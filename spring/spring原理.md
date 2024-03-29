=//想学代理的玩法==

//内嵌的tomcat，神策上的代码是否 配置个WebConfig registrationBean能运行web？

//Bean工厂相关的后处理器，4个；Bean生命周期相关的后处理器，讲了2个？

课程地址：

https://www.bilibili.com/video/BV1P44y1N7QG/?vd_source=8bd5ab544d4cb8d9821752b68ce53b11

梳理的时候多思考？面试的话哪些问题可以提取？   学的内容在自己日常该做中是不是可以有应用？

#### 问题小结：

- jdk代理的原理？如何自己实现代理？Cglib?? 代理的模拟实现自己手写下？？
- 想体验下微软的面试？看下人家和我之间的差距？

看源码技巧

![image-20230130195909028](spring原理-photos/image-20230130195909028.png)

![image-20230130200213405](spring原理-photos/image-20230130200213405.png)

![image-20230130200315981](spring原理-photos/image-20230130200315981.png)

![image-20230130200432114](spring原理-photos/image-20230130200432114.png)

### BeanFactory和ApplicationContext

#### 1.什么是BeanFactory//看类图ctrl alt u; 查看实现：ctrl alt 单击；

![image-20230205170555379](spring原理-photos/image-20230205170555379.png)

启动类的run方法返回值就是spring容器，

ApplicationContext继承了BeanFactory; BeanFactory[里面有SingletonObjects]才是Spring的核心，ApplicationContext的部分功能是组合了BeanFactory的内容实现的[beanFactory是applicationContext的成员变量，可以断点看属性验证]；





![image-20230202201258253](spring原理-photos/image-20230202201258253.png)

#### 2.BeanFactory的功能(要看有哪些方法和实现哪些接口、还有成员变量可以有很多方法)//ctrl+F12看方法？ uml :选中+F4

默认实现类  DefaultListableBeanFactory，可以管理所有Bean; 实现类中的DefaultSignletomBeanRegistry管理单例对象，可以反射查看所有单例；//下面的singletonObjects.get()里面的入参是什么情况？?也是个对象 说明beanFactory也是个单例对象，且保存在singletonObject中；看看 反射查看私有属性的示例代码？？

![image-20230205165940508](spring原理-photos/image-20230205165940508.png)

//只想看某个bean 话还可以过滤；

![image-20230205170207500](spring原理-photos/image-20230205170207500.png)

#### 3.ApplicationContext相对BeanFactory多了四种能力：//log输出日志会给出类名？@Autowired注入环境变量；

![image-20230205164002835](spring原理-photos/image-20230205164002835.png)

处理国际化资源的能力：MessageSource: context.getMessage() ； 依据key找到不同版本翻译结果，一般在messages打头的文件(不同语言的资源信息)；浏览器的请求头提供请求的语言类型；

![image-20230202204706856](spring原理-photos/image-20230202204706856.png)



​	通配符  获取资源（磁盘路径对应的资源）的能力：getResources()   //在jar包里面也查找：calsspath*:....

![image-20230205172101764](spring原理-photos/image-20230205172101764.png)



getEvironment: 获取环境信息（系统环境变量等）

发布事件对象 (本质上是一种解耦方式，如用户注册后 发短信、发邮件等；可以对标下AOP看哪个更优雅？)：pushlishEvent ，入参 事件源要继承ApplicationEcent； 接收时间  参数和入参一直，@EventListener

![image-20230205225338111](spring原理-photos/image-20230205225338111.png)

//单例+发送事件；

![image-20230205230310058](spring原理-photos/image-20230205230310058.png)

![image-20230205230425861](spring原理-photos/image-20230205230425861.png)

### 容器实现

#### BeanFactory实现 //默认实现DefaultListableBeanFactroy 是一个核心的spring容器？  bean的定义，BeanFactory会依据定义创建对象

//容器默认为空，往容器添加也给bean定义(先设置BeanDefinitin--类名、生命周期；然后注册bean--设置bean名字)；

![image-20230205232232567](spring原理-photos/image-20230205232232567.png)

原始的beanFactory并不会去解析注解，添加了后处理器[register扩展功能]并执行[postProcess/addBean....，或者称为建立联系]之后，会去解析注解，

![image-20230205233200331](spring原理-photos/image-20230205233200331.png)

BeanFactory后处理的主要功能，补充了一些bean定义，如@Bean @Configuration注解；



Bean后处理器，针对ean生命周期的各个阶段提供扩展，解析例如@Autowired注解；@Resource注解//javaee的注解

![image-20230206230400978](spring原理-photos/image-20230206230400978.png)



bean创建对象的时机：初始化的时候只会保存bean的定义、描述信息到beanFactory，当第一次用的时候，才会真正创建实例； 单例对象如果希望初始化时创建所有的单例对象，可以使用preInstantiateSingletons()：

![image-20230206231511602](spring原理-photos/image-20230206231511602.png)

applicationContext会把上面这些常用的初始化操作都直接封装好；



beanFactory的排序：

@autowired，bean容器中找实现类；有多个的时候[可以用qualifier指定？]会匹配成员变量名字和类名，匹配上优先；@Resource可以用name属性指定； 



![image-20230206232613301](spring原理-photos/image-20230206232613301.png)

![image-20230206232848214](spring原理-photos/image-20230206232848214.png)

优先级[优先级高的生效]@Autowired > @Resource，可以用比较器控制先后顺序，排序依据实现order接口的getOrder方法的返回值，数字小的排前面//同时使用两个注解时;

![image-20230206234006952](spring原理-photos/image-20230206234006952.png)

为什么sorted之后顺序会变？？和register一样的比较器啊？除非register只是进行了比较器的初始化，并没有把它用于排序，即执行；

#### ApplicationContext的常见实现和用法

- ClassPathXmlApplicationContext  基于xml路径读取配置；通常使用    <context:annotation-config>   标签就会自动加入一些有用的后处理器；
  -  ![image-20230208215603262](spring原理-photos/image-20230208215603262.png)
- FileSystemXmlApplicationContext : 基于文件路径读取配置；//绝对路径、相对路径均可
  - ![image-20230208215718274](spring原理-photos/image-20230208215718274.png)
- ApplicationContext是如何把beanDefination信息加载到beanFactory中的：用的XmlBeanDefinitonReader的 loadBeanDefinitions方法，入参也可以是ClassPathResource()对象；
  - ![image-20230208220500569](spring原理-photos/image-20230208220500569.png)
- AnnotationConfigApplicationContext : 基于配置类的applicationContext    
  - ![image-20230212110308969](spring原理-photos/image-20230212110308969.png)

#### 内嵌容器、注册DispatcherServletAnnotationConfigServletWebServerApplicationContext：既支持配置类，又支持内嵌servlet的Web容器---tomcat

- - spring的web服务器的核心是DispatcherServlet； DispatcherServlet要运行在tomcat服务器中；
  - 路径一般配置/，所有请求都经过dispatcherServlet，再到controller
  - ![image-20230212113647701](spring原理-photos/image-20230212113647701.png)
  - ![image-20230212113533870](spring原理-photos/image-20230212113533870.png)
  - 前3步必须的[构建内置tomcat，构建dispatcherServlet，建立dipatcherServlet和tomcat容器之间的关联]，controller1可选，bean名字/开头并实现Controller就可以作为控制器；
  - ![image-20230212113738417](spring原理-photos/image-20230212113738417.png)

#### 

### Spring Bean的生命周期

#### Spring Bean生命周期的各个阶段

![image-20230212223508800](spring原理-photos/image-20230212223508800.png)

 //@Autowired的参数  也会自动注入[值、变量]；

![image-20230212213754091](spring原理-photos/image-20230212213754091.png)



![image-20230212225551281](spring原理-photos/image-20230212225551281.png)

![image-20230212225605205](spring原理-photos/image-20230212225605205.png)

![image-20230212225841324](spring原理-photos/image-20230212225841324.png)



#### 模板设计模式：固定不变的内容+接口调用称为了模板[变化的内容单独封装为接口]；模板方法不需修改，改业务代码即可；

![image-20230212232225441](spring原理-photos/image-20230212232225441.png)

![image-20230212232233475](spring原理-photos/image-20230212232233475.png)

![image-20230212232156415](spring原理-photos/image-20230212232156415.png)

### 第四讲 Bean后处理器

#### 常见的Bean后处理器

- GenericApplicationContext相比AnnotationConfigApplicationContext  ，很干净，没添加bean后处理器等；refresh()方法会执行工厂后处理器 初始化单例等；

- 常见后处理器相关注解：@Autowired @Value；@Resource @PostConstruct @PreDestroy;@ConfigurationProperties注解

  - registerBean方法默认名称：包名、类名；设置AutowiredCandiateResoulver才能获取@Value注解内部的值注入；

- tips

  - ==@Autowired结合方法进行注入，可以打印信息查看是否注入成功；== 
  - Spring注解积累，@ConfigrationProperties  SpringBoot的bean的属性和配置文件的键值对 做绑定；

  - ![image-20230907190211419](spring原理-photos/image-20230907190211419.png)
  - //将后处理器加入到容器中
  - ![image-20230213230017296](spring原理-photos/image-20230213230017296.png)

- 示例代码
  - ![image-20230212234621913](spring原理-photos/image-20230212234621913.png)
  - ![image-20230213224839835](spring原理-photos/image-20230213224839835.png)
  - ![image-20230212234601021](spring原理-photos/image-20230212234601021.png)
  - ![image-20230213224732050](spring原理-photos/image-20230213224732050.png)
  - @ConfigurationProperties注解：前缀+属性名去配置文件中找环境变量
  - ![image-20230213225036305](spring原理-photos/image-20230213225036305.png)



#### @Autowired bean后处理器执行分析

- 准备工作
  - registerSingleton方法使用相对简单[不需要常见BeanDefinition]；但是要提供成品bean，即不再走bean工厂创建流程；
  - bean后处理器的依赖注入等阶段需要用到beanFactory，所以需要设置；
- 真正执行@Autowired @Value解析的是postProcessProperties
  - //直接调用Autowired相关方法的方式，理解Autowired的原理；  第一个参数传null，没有自己手工指定bean中的属性的值==
  - 找到添加了@autowired注解的方法和属性；inject方法反射赋值；
    - inject内部实现：
      -  属性和方法胡被封装为DependencyDescriptor对象  入参：成员变量名，是否必须；////方法的注入，类似，但是多一个参数 表明要注入的是方法的哪一个参数，然后一个一个注入；
      - beanFactory.doResolveDependency   入参：DependencyDescripor，依据成员变量信息找到类型，进一步找到bean；
- 示例代码：
  - ![image-20230213232635463](spring原理-photos/image-20230213232635463.png)
  - ![image-20230213231938822](spring原理-photos/image-20230213231938822.png)
  - ![image-20230213232711589](spring原理-photos/image-20230213232711589.png)
  - ![image-20230219144839839](spring原理-photos/image-20230219144839839.png)
  - ![image-20230219145953099](spring原理-photos/image-20230219145953099.png)

### 第五讲 BeanFactory后处理器

**BeanFactory后处理器**

- ConfigurationClassPostProcessor.class: 解析@Bean、@Component 、@Import 、@ImportResource
-  MapperScannerConfigurer[springboot自动配置]：扫描mybatis的mapper接口；
  - 一般spring boot自动配置，SSM架构用的@MapperScanner底层也是MapperScannerConfigurer.class ；
  - 入参：要指定扫描的包  //bd为beanDefinition；
- 代码示例：
  - ![image-20230219153011136](spring原理-photos/image-20230219153011136.png)

**模拟@ComponentScan注解的解析：** //==getResources是要获取二进制文件，难怪spring bean对象得是动态代理？？==；

- 获取ComponentScan注解中声明的包名，获取包下所有的类；
  - AnnotationUtils.findAnnotation用于判断某个类上是不是有加注解并获取注解对象  参数----Config.class, 注解对象类型；  //==如何做到判断类上是否有注解底层原理？==
  - 获取basePackages 包名，报名格式转换，   getResources获取所有类资源 ；
- 判断每一个类是否加了@Component注解 ;  如果加了则生成对应的BeanDefinition，并注册到bean工厂

  - CachingMetadataReaderFactory：获取类的元数据信息、注解信息等；用到的方法：getMeradataReader  getAnnotationMetadata().hasAnnotation()  getAnnotationMetadata().hasMetaAnnotation 
- AnnotationBeanNameGenerator解析@Component获取bean的名字；
  -  registerBeanDefinition将bean注册到工厂中；
  - getResources是在class目录下扫描到的，扫的是字节码？
- 将自定义的类抽取成独立的beanFactory后处理器，ComponentScanPostPostProcessor实现的BeanFactoryPostProcessor的postProcessBeanFactory方法会在refresh的时候回调 //可能要吧ConfigurableListableBeanFactory类型需要转换一下；getResource换一个类去调用；
- 示例代码：
  - ![image-20230219155926088](spring原理-photos/image-20230219155926088.png)
  - ![image-20230219160528207](spring原理-photos/image-20230219160528207.png)
  - ![image-20230226133516051](spring原理-photos/image-20230226133516051.png)
  - ![image-20230226143006514](spring原理-photos/image-20230226143006514.png)
  - ![image-20230226143107701](spring原理-photos/image-20230226143107701.png)
  - ![image-20230226143033100](spring原理-photos/image-20230226143033100.png)
  - ![image-20230226143213740](spring原理-photos/image-20230226143213740.png)

**模拟@Bean注解的解析**

- CacheingMeradataReaderFactory.getMetadataReader 加载Config类信息，进一步获取类中被@Bean注解标注的方法；
- 遍历  方法： BeanDefinitionBuilder.genericBeanDefiniton().setFactoryMethodOnBean 生成 对应BeanDefiniton 入参----方法名、工厂类名
  - 注意区别，这里生成BeanDefinition的不是config类[是个工厂类]，而是config类中@Bean注解标注的方法；
- 将BeanDefiniton注册到Bean工厂 入参----bean的名字、beanDefiniton对象（一般就用工厂方法名作为bean的名字）；
- 补充
  - //Bean定义方法有入参的话，需要指定自动装配模式 builder.setAutowiredMode  
  - Bean中有属性的话， getAnnotationAttributes().get获取@Bean中的属性；如果属性有值，则进行对应的操作(如有initMehtod属性则调用setInitMethodName)

- ==tips: 捕捉异常，ctrl+alt+T==
- 示例代码：目前配置类路径和类名还是写死，其实要找@Configuration标注的所有类；
  - ![image-20230226170127667](spring原理-photos/image-20230226170127667.png)
  - ![image-20230226170218062](spring原理-photos/image-20230226170218062.png)

**模拟@MapperScanner注解的解析**

- 前置说明：
  - beanFactory只能管理对象，要添加接口则需要接口转对象； 用MapperFactoryBean<T>封装，并指定sqlSessionFactory即可；
    - 
- @MapperScanner实现    实现接口BeanDefinitionRegistry(也是DefaultListableBeanFactory的父接口，直接就有registerBeanDefiniton方法)
  - 之前的后处理器实现的接口不好，用了一个强转，建议使用：BeanDefinitionRegistryPostProcessor，直接有registBeanDefiniton方法；
  - 

- 实现流程：
  - getResources加载class路径下所有文件，
  - for  resource :getMetadataReader 获取文件元数据信息，getClassMetadata进一步获取类信息
    - if 为接口， 
      - BeanDefinitionBuilder.genericBeanDefinition()获取BeanDefinition，并设置构造方法参数值[addConstructorArgValue]，设置装配模式，注册对应的bean；
        - setAutowiredMode 设置了自动装配模式后，factory会自动去工厂中找sqlSessionFactory并装配；这里的生成bean名字时generateBeanName的入参不再是类而是金额口，因为所有接口的封装类都是MapperFactoryBean；
  - 代码示例：
    - ![image-20230909141720183](spring原理-photos/image-20230909141720183.png)
    - ![image-20230226172036075](spring原理-photos/image-20230226172036075.png)
    - ![image-20230226204740122](spring原理-photos/image-20230226204740122.png)
    - ![image-20230226205207986](spring原理-photos/image-20230226205207986.png)

### 第六讲

#### Aware接口、InitializingBean接口简介

- 功能

  - aware接口：bean名字注入、BeanFactory容器注入、ApplicationContext容器注入、解析${}等
  - InitializingBean接口：为bean添加初始化方法
  - ![image-20230226205819279](spring原理-photos/image-20230226205819279.png)

- 核心亮点：在配置类中存在BeanFactoryPostProcessor的情况，@Aturowired @PostConstuct等扩展功能会失效，此时可以使用Aware接口、InitializingBean接口替代实现bean名字注入、bean初始化方法设置等操作；

- 用法

  - /注入时会回调，可以获取自己需要的信息，先回调Aware，再回调InitializingBean；两个接口内置功能[不加后处理器也能生效，且不会失效]不同于@Aturowired @PostConstuct扩展功能；
  - ![image-20230226211611809](spring原理-photos/image-20230226211611809.png)
  - ![image-20230226212034237](spring原理-photos/image-20230226212034237.png)

- **加了后处理器@Autowired等注解依然失效的情形**：配置类内部添加了BeanFactoryPostProcessor的Bean，使得@Atrowired @PostConstruct失效 

  - context.refresh()执行顺序：1.beanFactory后初期，2.添加bean后处理器，3.初始化单例

  - 失效原因分析：Java配置类包含BeanFactoryPostProcessor，故提前创建并初始化[为了执行BeanFactoryPostProcessor]，而此时BeanFactoryPostProcessor  BeanPostProcessor都没准备好，故配置类中的@Autowired等注解都无法解析
  - 解决方法1：
    - 使用IntializingBean、Aware接口替代@Autowired   @PostConstruct；
    - ![image-20230226213130208](spring原理-photos/image-20230226213130208.png)
    - ![image-20230226214249847](spring原理-photos/image-20230226214249847.png)
    - ![image-20230226214225873](spring原理-photos/image-20230226214225873.png)

### 第七讲  初始化和销毁

- 初始化的三种方法
  - @PostConstruct     后处理器，扩展功能，第一位执行；//aware在1 2之间执行；
  - 实现initializingBean接口     第二位执行；//上一讲提到的aware接口则是1.5位执行
  - @Bean(initMethod = "init3")    第三位执行

- 销毁的三种方法，优先级也是按顺序
  - @PreDestroy
  - 实现disposableBean接口
  - @Bean(destroyMethod = "destroy3")
- 代码示例：
  - ![image-20230910225408139](spring原理-photos/image-20230910225408139.png)
  - ![image-20230910225417959](spring原理-photos/image-20230910225417959.png)
  - ![image-20230910230041801](spring原理-photos/image-20230910230041801.png)

### 第八讲  Scope

- spring中scope的种类//spring5  默认single
  - singleton(容器关闭时销毁),  prototype（自行调用销毁）,  request（存在web的request域中，生命周期同request，重发请求会销毁）,  session(会话域，长时间不发/重新打开浏览器/调用session的invalid方法 请求会销毁),  application（应用程序域  启动时入servlet context，似乎spring不会自动销毁 即使你关闭应用）

- 单例的bean使用其它域的类，必须用@Lazy [否则 注入的类scope会失效，见下文，本质上是创建代理对象，打印时最后反射调用Object的toString] ，jdk9以后的版本，反射调用jdk中的类，会抛IllegalAccessException异常；

- 解决方案：改JDK版本；自己重写 javaBean的toString 方法；运行时添加指定的配置  --add-opens；

- 测试案例参考配制 session超时时间10s：但是实际的超时时间是max(超时时间配置，检测session超时的频率)
- 示例代码
  - ![image-20230304155219903](spring原理-photos/image-20230304155219903.png)
  - ![image-20230304155137529](spring原理-photos/image-20230304155137529.png)
  - ![image-20230304155559884](spring原理-photos/image-20230304155559884.png)
  - ![image-20230304160017798](spring原理-photos/image-20230304160017798.png)



- 单例注入多例，scope会失效（解决方案本质上都是获取多例的时候多一层） E（单例）有属性发（多例）；
  - 原因：对于单例对象只执行了一次初始化，所以内部属性的注入也只发生了一次
    - 
  - 解决方法
    - 四种解决方法思想上都是一样的：推迟其它scope bean的获取，代理  工厂  applicatioinContext
    - 1.添加@Lazy解决  
      - 加了@Lazy之后注入的是代理对象，代理类虽然不变，但是使用代理对象的方法时会创建新的多例代理对象；
    - 2.使用@Scope中的属性proxyMode解决 ，底层原理也是生成代理
    - 3.(推荐)使用工厂类解决，由工厂创建多例对象
    - 4.(推荐)注入一个ApplicationContext，调用getBean方法解决；

- 示例代码
  - ![image-20230305135529245](spring原理-photos/image-20230305135529245.png)
  - ![image-20230305135609810](spring原理-photos/image-20230305135609810.png)
  - ![image-20230911122859580](spring原理-photos/image-20230911122859580.png)
  - ![image-20230305140022017](spring原理-photos/image-20230305140022017.png)
  - ![image-20230305140156490](spring原理-photos/image-20230305140156490.png)
  - ![image-20230911124100586](spring原理-photos/image-20230911124100586.png)

#### aop之ajc增强

切面的实现方式不止代理，MyAspect监听MyService，拿到的MyService对象名字还是MyService; 编译的时候改写了原有的类  增加了前置增强；

编译结果的位置，==拖拉文件到idea可以反编译！！==

![image-20230305141334462](spring原理-photos/image-20230305141334462.png)

本质上，切面是由ajc编译器管理的，所以MyAspect不需要添加@Component注解；

pom.xml中添加插件：

![image-20230305141714908](spring原理-photos/image-20230305141714908.png)

![image-20230305141736924](spring原理-photos/image-20230305141736924.png)

有时候，idea默认是javac编译器，不使用aspect插件，可以使用maven的compiler强制使用；



相比spring的代理方式实现 aop，使用ajc编译器（修改class文件）可以增强static方法；

#### Aop实现之agent类加载

类加载阶段实现修改字节码 实现增强

![image-20230305145656423](spring原理-photos/image-20230305145656423.png)

![image-20230305145721931](spring原理-photos/image-20230305145721931.png)

可以突破代理实现aop的限制：一个方法调用另一个方法，被调用的方法无法增强；

![image-20230305145922238](spring原理-photos/image-20230305145922238.png)

阿里巴巴的arthas工具：可以实现运行时的反编译（类加载才实现的增强，直接看target中编译结果还是没有增强）

![image-20230305150119707](spring原理-photos/image-20230305150119707.png)

![image-20230305150228904](spring原理-photos/image-20230305150228904.png)

#### AOP实现之proxy//==简写为lamda快捷键？？==

代理类没有源码，运行时直接生成字节码；

##### jdk只能针对接口代理

- 参数一：classLoader；
- 参数二：要实现的接口可以一次实现多个接口；
- 参数三：invocationHandler，规定被代理方法具体的行为；

- invocationHandler的三个参数：
  - 代理对象
  - 真正执行的方法
  - 方法的参数

- 示例：
  - ![image-20230305152125580](spring原理-photos/image-20230305152125580.png)
- 特点：被代理类和代理类是兄弟关系，不能互相强转，且被代理类可以是final;

##### cglib实现代理

- 参数一：被代理类
- 参数二：Callback的子接口，MethodInterceptor
- MethodInterceptor的四个参数：代理对象，当前代理对象中执行的方法，方法的参数，MethodProxy
- 示例
  - ![image-20230305153521286](spring原理-photos/image-20230305153521286.png)
  - 使用methodProxy可以避免反射调用，invoke传被代理对象[spring使用这种]，厚着invokeSuper传代理对象
  - ![image-20230305153957518](spring原理-photos/image-20230305153957518.png)

- 特点：被代理类和代理类是父子关系，可以相互强转，且被代理类不能是final；父类方法加了final也不能被增强，代理类会重写被代理方法；

#### jdk代理原理

//代理的场景：日志；权限；事务的增强？

- 模拟实现代理，代理对象 增加一个私有成员Invocationhandler，代理方法的具体执行逻辑，放在Invocationhandler的invoke方法中； 在声明代理对象的时候再指定具体的invoke方法的执行内容；

- ![image-20230305155311339](spring原理-photos/image-20230305155311339.png)
- 对象有多个方法时，上述代码的invoke方法都调用的是被代理的foo方法，需要改进 所有的方法都调invoke， invoke具体反射调用哪个被代理方法 参数化；
- ![image-20230305155917375](spring原理-photos/image-20230305155917375.png)
- 还需要增加返回值处理（invoke是Object），增加代理对象参数，异常处理（检查异常、throwable异常不能直接抛，需要转换下再抛）；
- ![image-20230305161229366](spring原理-photos/image-20230305161229366.png)
- 方法对象的获取不需要每次调用都获取一次
- ![image-20230305161510415](spring原理-photos/image-20230305161510415.png)
- jdk的代理会继承Proxy类，内含一个InvocationHandler接口，所以可以直接用
- ![image-20230305163339477](spring原理-photos/image-20230305163339477.png)
- arthas工具[powershell]需要知道类名才能反编译；程序要保持运行状态，可以System.in.read()；//直接看jdk代理源码基本看不懂，因为用的asm动态生成代理类的字节码；

- ![image-20230305164327370](spring原理-photos/image-20230305164327370.png)
- ![image-20230305164452865](spring原理-photos/image-20230305164452865.png)
- ![image-20230305164535950](spring原理-photos/image-20230305164535950.png)
- ![image-20230305164609432](spring原理-photos/image-20230305164609432.png)

#### jdk代理字节码生成

- jdk代理没有源码，直接生成字节码，用的asm[spring jdk使用很多]
- 安装idea插件 java源码转换为asm代码，然后可以转换为字节码；但不能很好地在高版本的jdk里面工作；
  - ![image-20230305165206211](spring原理-photos/image-20230305165206211.png)
- 编写一个代理类的代码
  - ![image-20230305165934972](spring原理-photos/image-20230305165934972.png)
  - 编译， 右键-- show Bytecode outline，会转换为ASMified  即asm代码；需要导下包，spring的包即可；



