//有信的和温州的能占其一吧，有信的优先（看来周日当真要多去哦，不过话说回来，过于积极了我也头疼）；讲道理，我和她的缘分早该尽了，一直偶尔还会问候一下纯粹是因为没有遇到合适的，再者于我来说也不曾因为她而有任何的损失；如果有遇到合适的因为她而错过了，说实话，于自己就是犯傻，于这段关系来说也是不好的。  

哪个合适、追哪个的事情再说，眼前这个肯定是要了解一下的，差不多是今年新标准中top级别的了。我不是什么完美主义者，和她也没有什么特别的羁绊，如果真的是符合我的标准的，我肯定要试试。



#### ==近期想学的内容==

- 设计模式
- 找一个大型的项目学习下，经典的数字化转型，银行、金融业最好；
- F5负载均衡
- 编码规范
- docker  k8s
- 源码，elastic job    // 防重，自己梳理一个工具类呀







//新年的目标：带回来的书看完；https研究下，nginx温习下；docker;oatuh2;

https、ssl证书的原理？？openssl用法？

- 在家里有一个好处，没有车水马龙的喧嚣，有着真正的、绝对的宁静，对于普通人来说令人窒息。对于一个真正能承受孤独的人，却是一种享受。希望自己35-40的时候，作选择时可以更少考虑物质层面的东西，更贴近自己的灵魂追求一些。毕竟，先要活着，然后才能追寻自己的灵魂。   两者的区别不在于肉体的劳累与舒适，而在于做事情的初衷与目标。每个人活着都是希望能解决问题的，我这一辈子希望解决什么问题？ 要站在巨人的肩膀上，而后能看到自己这辈子可能能解决的问题；追求此生的成就的话，则直接试着去解决这个时代最大的问题与矛盾。
- 慢慢去习惯脱离网络和影视吧，最初可能会稍有不适。   但是我相信坚持下去于己一定是大有裨益的。   垃圾食品吃多了容易营养不良，我在学校的时候何曾吃过垃圾食品，充其量就是看看综艺罢了。
- 正是研究生的经历，尤其是最后一年，让我深刻意识到，如果不是先立命，我的职业生涯甚至人生是绝对走不远的。
- 在我这里，人生的底色就是悲伤却伴随着宁静与平安的。

- 人的第一大罪是骄傲（唯有信仰能教会人绝对的谦卑）；第二大罪是攀比（这是一种精神上的懒惰，不曾去认真思考自己真正追求的是什么？）

正向代理的nignx可以直接安装在客户端？反向代理的nginx需要单独一台服务器  ？其实也可以用一个端口替代吧？

`正向代理和反向代理中，代理做的事情相同吗？`

正向代理中，客户端经过配置，所有的请求[目的ip是服务器]会转到Nginx； Nginx会获取请求的ip 端口 uri，然后自己转发请求到服务端；

反向代理，客户端直接访问代理[目的ip是代理]，代理从服务器获取资源

==//epoll？？？==

http  https仔细学习下！！！！很实用啊；



大富大贵，我早不留恋，既然命定无此，也便坦然接纳了。唯有男女一事，久久不能释怀。近来，年岁增长，渐渐悟到一点修身的功夫，也便放开了。美人如同豪车豪宅，既然命中没有，便不必强求，且于人生并非必需品。人生在世，终究是活得明白才能不枉此生。无欲无求，方渐明其志。

凡在某个领域有高深造诣者，大多博学。首先要培养学习的兴趣，顺应人的本性，而后能坚持，能有所专。

可以适当自学金融学！！！！！！

#### 面试角度的问题梳理

- 常用命令  ./nginx -t     ./nginx -s reload   //reload之后work进程的pid会变；重启之后master进程的pid会变；
- nginx速度快、并发高的原因是什么？epoll的底层原理是什么？为什么sendfile配置打开能提升从磁盘读取文件并返回的性能？
  - 使用了epoll，I/O多路复用。
- 简单介绍你对nginx的了解？nginx相比其它web服务器有什么优缺点？
  - nginx是具有高性能  HTTP 和 反向代理 功能的WEB服务器，也是一个 POP3/SMTP/IMAP代理服务器；
  - nginx主要具有：速度快，并发高[多进程和I/O多路复用]，高可靠，轻量级别 等优点 //[配置简单，扩展性好；热部署；成本低 BSD许可]
    - tomcat对态文件和高并发处理能力弱【200-300并发量】；
    - Apache：重量级、不支持高并发
    - Lighttpd：轻量级、高性能，欧美青睐
- ==什么是正向代理，什么是反向代理？==
  - 架设位置不同[客户端  服务端]；
  - 隐藏对象不同【正向隐藏了客户端---即客户端访问的目的地址是服务器[即客户端需要知道服务器的ip，因为代理在客户端]，访问服务端的是代理 ;  反向隐藏了服务端---即客户端访问的目的地址是代理服务器[即服务端需要知道客户端的ip，因为代理在服务端]；
  - 目的不同【正向 解决访问限制问题； 反向 负载均衡和安全防护】
- nginx的核心文件？核心路径？
  - nginx二进制可执行文件、nginx.conf配置文件、error.log、access.log
  - /nginx/sbin 二进制启动文件； /nginx/logs [内含nginx主进程id];  /nginx/html [访问成功、失败的页面]
- nginx启动、重启和停止nginx服务？
  - 信号控制（向master发送信号）：ps -ef | grep nginx获取master的PID； kill -signal PID
  - 命令行控制：/sbin/nginx -h查看支持参数；-c指定nginx配置文件路径；//还有-tc等；
    - 日常使用，直接可以用重启命令  ./nginx  -s quit ;  ./nginx -c  .....;   ./nginx -s reload
- nginx架构（高可靠的原理、平滑升级的原理）
  - 一个master进程和多个worker进程；master接收外界信息，发送给worker，监控worker状态，worker异常退出后，master会重新启用鑫的worker，由worker处理用户请求。
  - 先发送USR2信号，启动新的master和worker；如何发送QUIT给旧的master处理完请求关闭；
- nginx配置文件组成？
  - 默认三大块：全局块、events块、http块
    - http块可以配置多个server块，每个server块可以配置多个location块；
  - 全局块指令
    - user  user1：配置运行work进程的用户及用户组；例如：按照前面的配置只能访问/home/user1目录的权限 //有点迷糊，例子只配置了用户吧？没有用户组？
    - master process ; worker process (建议和cpu核心数保持一致)
    - 其它：daemon、pid、error_log、include
- nginx匹配规则，server   location root/alias
  - nginx如何没有匹配的server，返回结果是什么？
    - ==default_server==:访问的地址没配置对应的server时会跳转到default server，默认第一个配置的server为default_server；
  - server_name的匹配规则？
    - server_name：配置监听的ip/域名，支持==精确匹配>通配符匹配==（通配符在开始时匹配>通配符在结束时匹配；*使用注意，不能在中间；不能前面有字符）==>表达式匹配==（～后面不能加空格；结合（）可以在后面获取正则表达式匹配的内容；），==前三个优先级均大于 默认的default server==；
  - location的匹配规则？
    - location //==不带符号==（以指定模式开始，后面可以跟任意字符；匹配上还会向后搜索，搜索到匹配的会使用后面的） =(严格匹配)  ~（正则区分大小写） ~*(正则不区分大小写)  ^~（以指定模式开始，且一旦模式匹配会忽略后面匹配的正则）
  - root/alias匹配规则？
    - 可以指定资源路径；root的处理结果是 root路径+location路径  +url中的资源位置；alias的处理结果是alias路径(也可以理解为alias替换了url中 location对应的内容)  +url中的资源位置（所以location后面的路径末尾带/的话，alias末尾也要加/，root无此要求）
- nginx种sendfile的实现原理？
  - sendfile：是否开启高效的文件传输模式。       未使用sendfile时访问静态资源流程：nginx应用程序发送read指令给内核区；磁盘拷贝文件--->内核缓冲区---->应用程序缓冲区；nginx应用程序发送write指令给内核区；应用程序缓冲区拷贝文件--->socket缓冲区--->网卡---->发送到浏览器。     使用sendfile时访问静态资源流程：sendfile可以指定最终要交给的socket；可以直接走磁盘-->内核缓冲区-->socket缓冲区--->网卡-->浏览器；少了两次拷贝和  内核态/用户态的切换；//简单来说就是不用再经过应用程序了
  - 相关指令：==tcp_nopush==：服务端要发送的数据填满缓冲区才发（send file开启时才生效）；   ==tcp_nodelay==：如果有数据就发，实时性好，其中可能大多数是寻址用的数据，有效数据的占比很低，即所谓的效率低（keep alive开启时才生效） 
    - 2.5.9以后两者可以同时开启，tcp_nopush保证发送数据前缓冲区已填满，提升效率；tcp_nodelay保证最后一个包发送时，即使数据未填满缓冲区也会立刻发送
  - gzip与sendile的结合：
    - 使用sendfile之后，静态资源获取就不会经过应用程序（见前文，直接走磁盘-->内核缓冲区-->socket缓冲区-->浏览器）；但是==压缩这个操作是要应用程序进行的==。==为了保证senfile和Gzip共存，一般是提前手动把静态资源压缩好（.gz文件）==，保存在磁盘，当gzip生效时就可以直接去找.gz文件
- gzip相关内容：略；
  - 涉及指令：gzip  gzip_tyeps  gzip_comp_level  gzip_vary  gzip_buffers   gzip_disable  gzip_http_version gzip_min_length   gzip_proxied  gzip_static
  - 小番外：nginx编译增加新的模块
- web缓存有哪几种方式？各有什么有优缺点？
  - web缓存是指web资源在web服务器和客户端之间的副本。大致可以分为两类：客户端缓存 和  服务端缓存。   客户端缓存主要包括浏览器缓存，服务端缓存则包括 Nginx  Redis  Memcached 等
  - 浏览器缓存
    - 浏览器在用户磁盘上存储最新的请求结果，再次请求时从本次磁盘获取文件
    - 优点：缓存成本低 减少网络带宽、服务器压力等
    - 分为强缓存、弱缓存。强缓存指==缓存未过期==直接取浏览器缓存； 弱缓存指==缓存过期==，还需要发请求到服务端确认ETag [请求变量的属性，如md5值等] Last-Modified没有变化，服务端返回一个304[意思时文件没有变化]后才能取浏览器缓存。
      - F5或者刷新都会使强缓存失效（即有效期会过期），验证强缓存需要新开一个tab（并输入同样的网址），disable cache注意关闭；
  - //HTTP请求头缓存相关字段：Expires  Cache-Control  Last-Modified ETag
  - //nginx的add_header指令可以添加指定的响应头和响应值；
- 什么是跨域问题？nginx如何解决跨域问题？
  - 两台服务器A、B，如果来自A服务器的前端页面发送请求到B获取数据，且A和B不满足同源策略，则会出现跨域问题。协议  ip  端口都相同即为同源
  - 解决方案：add_header指令添加相关的头，如Access-Control-Allow-Origin, Access-Control-Allow-Method
- 什么是资源盗链？如何实现防盗链？
  - 资源盗链就是静态资源不在自己服务器上，通过技术手段，把别人的资源放到自己的页面上展示给用户。如在自己的页面上引入京东/百度的图片。
  - 防盗链实现原理：http的头信息referer，告诉浏览器该网页从哪个页面链接跳转过来，后台服务器判断referer是否为自己信任的网站地址，是则继续访问，不是则返回403（服务器拒绝访问）。 相关nginx指令：valid_refers (referer的限制比较粗粒度（一类文件或者是一个目录），比如随意加一个Referer，上面的方式无法限制。需要使用三方模块： ngx_http_accesskey_module)
- nginx的rewrite指令一般用于什么场景？
  - 域名跳转：例如让www.360buy.com也重定向到www.jd.com
  - 域名镜像：和镜像网站类似，完全相同的网站放置到几台服务器上，实现 高可用、分布不同地区以提高响应速度、流量负载、==不同镜像不同域名防止域名限制==。上述的www.itheima.com  www.itheima.cn 都跳转www.itcast.cn，则www.ticast.cn就是主域名，另外两个就是镜像域名。也可以只对一个子目录资源做镜像，可以在location配置rewrite功能。
  - 独立域名：为每一个功能模块设置独立的域名
  - 目录自动添加  ”/“：nginx 0.8.48以前server_name_in_redirect的默认开关都是on，==访问url不加斜杆==，Nginx服务器内部会自动做一个301的重定向，目的地址（如果是nginx服务器）会被替换为server_name(nginx监听配置种的server_name)。
  - 合并目录（搜索引擎优化的常见策略之一）：访问的时候通过名字添加 - 的方式降低目录层级，真正保存的时候一个 - 就是一个目录层级
  - //涉及的指令：set  if  break  return  rewrite  rewrite_log
- 实际操作流程：正向代理 反向代理
  - 正向代理：客户端配置代理服务器；代理服务器监听指定端口；服务器仅打印日志即可；
  - 反向代理：代理配置监听的端口、服务器域名/ip，转发地址；服务器配置相应的资源；
    - 语法说明：proxy_pass设置代理服务器地址，可以是主机名称、ip附加端口号形式（还要指定传输协议）； proxy_set_header 更改服务器收到的请求头中某个属性的信息； proxy_redirect:适用场景：重定向时依旧能隐藏服务器的ip
  - ==注意区分，地址后面自动加/的事情==：nginx配置中  proxy_pass后面的地址没有/的话，会自动把location后面的uri添加到后面(加了则不会)；  rewrite提到客户访问网址时  末尾不加/，server_name_in_redirect的默认开关都是on，Nginx服务器内部会自动做一个301的重定向
- nginx反向代理有哪些调优策略？
  - 缓冲与缓存。    缓冲（proxy_buffering）：客户端不和服务器直接交互，中间多一层缓冲区，缓冲区依次和服务器A（例如A处理快，B处理慢，缓冲区可以再对A B的返回结果做一次重新排序，A就不用一直等） 、B交互。              缓存（proxy_cache_path等）：代理服务器保存一份缓存数据，客户端再次发系统请求时只需要返回代理服务器上的缓存数据接口。
  - 缓冲相关指令：proxy_buffering     proxy_buffers   proxy_buffer_size    proxy_busy_buffer_size   proxy_temp_path    proxy_temp_file_write_size
- nginx缓存集成？？
- nginx是符合提升web服务器的安全的？
  - 安全隔离：通过代理分开了客户端到应用程序服务端的连接，实现了安全隔离。可以在代理之前设置防火墙，仅留一个入口供代理服务器访问（也就是行里的DMZ区，内网只留了一个DMZ区的入口）。
  - nginx支持https(需要http_ssl_module)，http是明文传输数据，存在安全问题，https是加密传输，相当于http+ssl
  - //ssl相关指令：ssl_sessin_cache  ssl  ssl_certificate ssl_certificate_key  ssl_session_timeout  ssl_ciphers  ssl_prefer_server_ciphers； 证书可以三方服务购买或者openssl生成；

- 常见的负载均衡策略有哪些？详细说说如何实现Nginx  四层、七层负载均衡指令？
  - 用户手动选择（如网页上多个下载地址）、 DNS轮询（一个域名映射多个ip，请求轮询访问多个ip）、四层负载均衡（ip+port实现负载均衡，硬件：F5 BIG-IP  Radware等；软件：LVS Nginx[==keepalivied，或stream + upstream使用时只配置到server层，涉及stream模块==] Hayproxy等）、七层负载均衡（基于虚拟的URL或主机IP，软件：Nginx[==upstream使用时只配置到location层==]、Hayproxy等 ）
  - 常用模式：四层负载lvs + 七层负载Nginx
  - //==行内支持负载均衡的本质上是四层负载均衡，采用的是F5（在开发人员看来就是 申请虚地址+ 负载均衡策略的配置）， 其实没有F5的话keepalived应该也看i实现类似的效果；  七层负载则自己在nginx中使用upstream配置即可==
  - //ssl相关指令：upstream  server;  tips: firewall-cmd是Linux提供的专门操作防火墙的工具
  - nginx七层负载均衡支持的均衡那个策略：轮询（默认，但不同服务器性能不同）、wegiht（但登录学习缓存无法命中）   ip_hash(将某个客户端ip的请求通过哈希算法定位到同一台后端服务器上 )   least_conn(请求转发给连接数较少的服务器)  url_hash（按访问url的hash结果分配请求） fair (依据页面大小、加载时间长短智能进行负载均衡)
  - 四层和七层负载均衡的区别：四层负载均衡依据ip+端口+设定的规则，要请求转发到对应的ip+端口上，七层则在四层基础上考虑了应用层特征，如七层的URL 浏览器类别等； 


### Nginx简介

#### 背景介绍

![image-20220529224517009](Nginx课程学习-photos/image-20220529224517009.png)

![image-20220529224612503](Nginx课程学习-photos/image-20220529224612503.png)

//协议：标准、规范；

![image-20220529224914471](Nginx课程学习-photos/image-20220529224914471.png)

![image-20220529224956642](Nginx课程学习-photos/image-20220529224956642.png)

//服务端禁掉某一类客户端的访问；客户端请求（指定了服务端?????）-->代理-->服务端； 服务端响应-->代理-->客户端；



![image-20220529225139571](Nginx课程学习-photos/image-20220529225139571.png)

//请求发给代理（请求未指定服务端????），代理分发给不同服务端；

#### 常见服务器对比

![image-20220529225707091](Nginx课程学习-photos/image-20220529225707091.png)

//web服务开发商市场份额占有率；

![image-20220529230830181](Nginx课程学习-photos/image-20220529230830181.png)

![image-20220529231023234](Nginx课程学习-photos/image-20220529231023234.png)

//tomcat并发量大概在200-300; 

![image-20220529231259410](Nginx课程学习-photos/image-20220529231259410.png)

![image-20220529231312913](Nginx课程学习-photos/image-20220529231312913.png)

![image-20220529231329271](Nginx课程学习-photos/image-20220529231329271.png)

#### Nginx的优点

//epoll？？？

![image-20220605223000950](Nginx课程学习-photos/image-20220605223000950.png)

![image-20220605223335130](Nginx课程学习-photos/image-20220605223335130.png)

![image-20220605223459750](Nginx课程学习-photos/image-20220605223459750.png)

![image-20220605223656871](Nginx课程学习-photos/image-20220605223656871.png)

![image-20220605223720660](Nginx课程学习-photos/image-20220605223720660.png)

#### Nginx的功能特性及常用功能

![image-20220605223840153](Nginx课程学习-photos/image-20220605223840153.png)

![image-20220605223856598](Nginx课程学习-photos/image-20220605223856598.png)

![image-20220605223935721](Nginx课程学习-photos/image-20220605223935721.png)

![image-20220605223957581](Nginx课程学习-photos/image-20220605223957581.png)

![image-20220605225049324](Nginx课程学习-photos/image-20220605225049324.png)

![image-20220605225209392](Nginx课程学习-photos/image-20220605225209392.png)

#### Nginx的官方简介

![image-20220605230129034](Nginx课程学习-photos/image-20220605230129034.png)

![image-20220605230204752](Nginx课程学习-photos/image-20220605230204752.png)

![image-20220605230219200](Nginx课程学习-photos/image-20220605230219200.png)

### Nginx系统环境准备

//用到时再参考视频即可；

### nginx.conf文件结构及其中的指令

//user work_process  daemon pid error_log等指令直接见思维导图

#### Events

- accept_mutex：对多个nginx进程接收连接进行序列化，即当一个请求到达时只唤醒一个work进程；设置为on只唤醒一个
  - 解决惊群问题，即一个请求到达时是唤醒多个work进程(性能低)还是一个
  - ![image-20240214145707059](Nginx课程学习.assets/image-20240214145707059.png)
- Multi_accept：worker进程是否同时接收多个网络了解
  - ![image-20240214145807456](Nginx课程学习.assets/image-20240214145807456.png)
- Worker connections：设置单个worker进程的最大连接数(指的是所有连接数且不大于操作系统支持打开的最大文件句柄数量)
  - ![image-20240214150045713](Nginx课程学习.assets/image-20240214150045713.png)
- use:nginx服务器选择那种事件驱动处理网络消息，可选select/poll/epoll/kqueue
  - ![image-20240214150214120](Nginx课程学习.assets/image-20240214150214120.png)

#### http块

- include 引入外部的配置信息；   default_type 设置返回的结果类型
  - 支持的资源的类型   //mime.types保存了不同的资源和文件后缀的对应关系; application/octet-stream是二进制流的意思；
  - ![image-20240214151434395](Nginx课程学习.assets/image-20240214151434395.png)
  - ![image-20240214151927052](Nginx课程学习.assets/image-20240214151927052.png)
- Access_log（设置nginx日志相关配置） + log_format（设置nginx日志的格式） 
  - Access_log用到的format需要用log_format提前声明
  - ![image-20240214153544620](Nginx课程学习.assets/image-20240214153544620.png)
  - ![image-20240214153623458](Nginx课程学习.assets/image-20240214153623458.png)
- sendfile(是否使用sendfile 传输文件)   Keepalive_timeout（设置长连接的超时时间，避免一个请求建立一个连接）    keepalive_request（一个keep-alive链接的使用次数）
  - ![image-20240214154251200](Nginx课程学习.assets/image-20240214154251200.png) 
  - ![image-20240214154216630](Nginx课程学习.assets/image-20240214154216630.png)

#### server块和location块概览

- listen  监听的端口；server_name  监听的端口/域名； local 监听的uri路径；
- root 资源所在的目录
- index默认访问/时候对应的首页；资源要放在root指定的目录下；
- error_page   设置错误包含的状态码  跳转的错误页面

#### nginx基础配置示例需求分析

- ![image-20240214155721558](Nginx课程学习.assets/image-20240214155721558.png)
- ![image-20240214221732663](Nginx课程学习.assets/image-20240214221732663.png)
- server1.conf
  - ![image-20240214221205484](Nginx课程学习.assets/image-20240214221205484.png)
- server2.conf
  - ![image-20240214221239986](Nginx课程学习.assets/image-20240214221239986.png)

#### Nginx配置成系统服务，Nginx命令配置到系统环境

- centOS配置系统服务
  - ![image-20240214223147566](Nginx课程学习.assets/image-20240214223147566.png)
  - ![image-20240214223205479](Nginx课程学习.assets/image-20240214223205479.png)

- 系统环境
  - ![image-20240214224927267](Nginx课程学习.assets/image-20240214224927267.png)

### Nginx静态资源部署及可能用到的指令

- #### Nginx静态资源的配置指令
  
  - listen    //nginx.org/en/docs 有语法等信息
    - ![image-20240215113735954](Nginx课程学习.assets/image-20240215113735954.png)
  - default server //访问的地址没配置对应的server时会跳转到default server；没有配置default server的时候，默认第一个配置的server为default_server
    - ![image-20240215120128301](Nginx课程学习.assets/image-20240215120128301.png)
  - server_name //域名解析及host配置的内容略，参考自己的笔记
    - ![image-20240215120645045](Nginx课程学习.assets/image-20240215120645045.png)
    - 精确匹配
      - ![image-20240215121030140](Nginx课程学习.assets/image-20240215121030140.png)
    - 通配符匹配
      - *使用注意，不能在中间；不能前面有字幕
      - ![image-20240215122604609](Nginx课程学习.assets/image-20240215122604609.png)
    - 使用正则表达式配置//～后面不能加空格；结合（）可以在后面获取正则表达式匹配的内容；
      - ![image-20240215195522158](Nginx课程学习.assets/image-20240215195522158.png)
      - ![image-20240215200055226](Nginx课程学习.assets/image-20240215200055226.png)
      - ![image-20240215201009945](Nginx课程学习.assets/image-20240215201009945.png)
    - 匹配优先级
      - 精确匹配 > 通配符在开始时匹配>通配符在结束时匹配>正则表达式匹配 > 默认的default_server，没有指定默认找第一个server
      - ![image-20240215203108958](Nginx课程学习.assets/image-20240215203108958.png)
  - location //不带符号（以指定模式开始，后面可以跟任意字符；匹配上还会向后搜索，搜索到匹配的会使用后面的） =(严格匹配)  ~（正则区分大小写） ~*(正则不区分大小写)  ^~（以指定模式开始，且一旦模式匹配会忽略后面匹配的正则）
    - ![image-20240215205231164](Nginx课程学习.assets/image-20240215205231164.png)
    - ![image-20240215211049399](Nginx课程学习.assets/image-20240215211049399.png)
    - ![image-20240215211102831](Nginx课程学习.assets/image-20240215211102831.png)
    - ![image-20240215211121188](Nginx课程学习.assets/image-20240215211121188.png)
    - ![image-20240215210957037](Nginx课程学习.assets/image-20240215210957037.png)
- #### 设置请求资源的目录
  
  - root / alias :都可以指定资源路径；root的处理结果是 root路径+location路径  +url中的资源位置；alias的处理结果是alias路径(也可以理解为alias替换了url中 location对应的内容)  +url中的资源位置（所以==location后面的路径末尾带/的话，alias末尾也要加/，root无此要求==）
    - 同样监听/image，  root  /usr/local/nginx/html ;   alias  /usr/local/nginx/html/image
    - ![image-20240216170929587](Nginx课程学习-photos/image-20240216170929587.png)
    - ![image-20240324150407563](Nginx课程学习-photos/image-20240324150407563.png)
  - index : 设置location的默认主页
    - ![image-20240217195332059](Nginx课程学习-photos/image-20240217195332059.png)
  - error_page： 设置错误页面，可以跟域名、重定向地址、自定义展示错误信息、自定义返回的状态码 + 错误页面；
    - ![image-20240217200008415](Nginx课程学习-photos/image-20240217200008415.png)
    - ![image-20240217200149194](Nginx课程学习-photos/image-20240217200149194.png)
    - ![image-20240217200238229](Nginx课程学习-photos/image-20240217200238229.png)
- #### 静态资源优化配置指令
  
  - sendfile
    - 是否开启高效的文件传输模式
      - 未使用sendfile时访问静态资源流程：nginx应用程序发送read指令；磁盘拷贝文件--->内核缓冲区---->应用程序缓冲区；nginx应用程序发送write指令；应用程序缓冲区拷贝文件--->socket缓冲区--->网卡---->发送到浏览器；
      - 使用sendfile时访问静态资源流程：sendfile可以指定最终要交给的socket；可以直接走磁盘-->内核缓冲区-->socket缓冲区--->网卡-->浏览器；少了两次拷贝和  内核态/用户态的切换；//==简单来说就是不用再结果应用程序了==
    - http底层是tcp, tcp底层是socket;  sendfile是操作系统底层的一个函数；一般操作系统不允许应用程序直接读磁盘，认为不安全；
    - ![image-20240217231139494](Nginx课程学习-photos/image-20240217231139494.png)
    - ![image-20240217230548319](Nginx课程学习-photos/image-20240217230548319.png)
    - ![image-20240217231121164](Nginx课程学习-photos/image-20240217231121164.png)
  - tcp_nopush：服务端要发送的数据填满缓冲区才发（send file开启时才生效）；   tcp_nodelay：如果有数据就发，实时性好，其中可能大多数是寻址用的数据，有效数据的占比很低，即所谓的效率低（keep alive开启时才生效）
    - 2.5.9以后两者可以同时开启，tcp_nopush保证发送数据前缓冲区已填满，提升效率；tcp_nodelay保证最后一个包发送时，即使数据未填满缓冲区也会立刻发送
    - ![image-20240217232612885](Nginx课程学习-photos/image-20240217232612885.png)
    - ![image-20240217232527734](Nginx课程学习-photos/image-20240217232527734.png)
    - 如果有数据就发，实时性好，其中可能大多数是寻址用的数据，有效数据的占比很低，即所谓的效率低；
    - ![image-20240217232326576](Nginx课程学习-photos/image-20240217232326576.png)
- 静态资源压缩
  - ![image-20240218202838463](Nginx课程学习-photos/image-20240218202838463.png)
  - //浏览器缓存开启时，走缓存的话大小可能会显示很小；
  - gzip开启gzip功能； gzip_types指定要压缩的文件类型；gzip_comp_level指定压缩程度；gzip_vary 是否通过添加返回头中字段的形式告诉前端资源经过了压缩；gzip_buffers设置压缩缓冲区的数量和每个缓冲区的大小，和操作系统相关，一般采用默认即可；gzip_disable 针对不同种类客户端发起的请求，选择性地关闭Gzip功能；gzip_http_version 开启Gzip功能所需的最低版本http协议，一般默认；gzip_min_length 开启压缩最小的文件大小 bytes/kb/M（一般1k以上），和请求头的content-type比较；gzip_proxied 反向代理的过程中，是否对服务器返回的资源进行压缩
    - ![image-20240218204132970](Nginx课程学习-photos/image-20240218204132970.png)
    - ![image-20240218204155048](Nginx课程学习-photos/image-20240218204155048.png)
    - ![image-20240218204401167](Nginx课程学习-photos/image-20240218204401167.png)
    - ![image-20240218204734840](Nginx课程学习-photos/image-20240218204734840.png)
    - ![image-20240218204827162](Nginx课程学习-photos/image-20240218204827162.png)
    - ![image-20240218205155451](Nginx课程学习-photos/image-20240218205155451.png)
    - ![image-20240218205743022](Nginx课程学习-photos/image-20240218205743022.png)
    - ![image-20240218205946845](Nginx课程学习-photos/image-20240218205946845.png)
    - ![image-20240218210335038](Nginx课程学习-photos/image-20240218210335038.png)
  - gzip使用示例
    - ![image-20240229183623532](Nginx课程学习-photos/image-20240229183623532.png)
  - gzip_static
    - 是否已经提前压缩好静态文件，即去检测资源同名的.gz文件；on则符合gzip_http_version配置生效，always则永远生效
    - 解决Gzip和senfile共存的问题，使用sendfile之后，静态资源获取就不会经过应用程序（见前文，直接走磁盘-->内核缓冲区-->socket缓冲区-->浏览器）；但是压缩这个操作是要应用程序进行的。为了保证senfile和Gzip共存，一般是提前手动把静态资源压缩好（.gz文件），保存在磁盘，当gzip生效时就可以直接去找.gz文件
    - ![image-20240229184851933](Nginx课程学习-photos/image-20240229184851933.png)
- 番外：nginx重新编译 增加新的模块
  - 注：第六步还需要补充第一步查询得到的参数；第8步需要在安装目录下执行；
  - ![image-20240229185518428](Nginx课程学习-photos/image-20240229185518428.png)
  - ![image-20240229185544884](Nginx课程学习-photos/image-20240229185544884.png)

### web缓存

- 缓存概念

  - ![image-20240229191209130](Nginx课程学习-photos/image-20240229191209130.png)
  - ![image-20240229191323792](Nginx课程学习-photos/image-20240229191323792.png)

- 缓存种类

  - ![image-20240229191359430](Nginx课程学习-photos/image-20240229191359430.png)

- 浏览器缓存

  - ![image-20240229191531153](Nginx课程学习-photos/image-20240229191531153.png)

  - ![image-20240229192800899](Nginx课程学习-photos/image-20240229192800899.png)

  - ![image-20240229192724945](Nginx课程学习-photos/image-20240229192724945.png)

  - 强缓存：缓存未过期直接取浏览器缓存；弱缓存，缓存过期，还需要发请求到服务端确认ETag  Last-Modified没有变化，服务端返回一个304然后才能取浏览器缓存

    - F5或者刷新都会使得强缓存失效；验证强缓存需要新开一个tab   //验证缓存时，disable cahce注意配置；

  - expires指令

    - //time默认时服务端时间而且时格林尼治时间；max-age  expire都标志超时时间，但是expire在客户端  服务端时针不一致的时候会有问题，两者同时存在时max-age优先生效；
    - ![image-20240229195431960](Nginx课程学习-photos/image-20240229195431960.png)
    - ![image-20240229195936647](Nginx课程学习-photos/image-20240229195936647.png)

  - add header指令

    - ![image-20240229200548426](Nginx课程学习-photos/image-20240229200548426.png)
    - ![image-20240229200628833](Nginx课程学习-photos/image-20240229200628833.png)
    - ![image-20240229200433735](Nginx课程学习-photos/image-20240229200433735.png)
    - ![image-20240229200501963](Nginx课程学习-photos/image-20240229200501963.png)

    

### 跨域问题及解决方案

- 同源：协议  ip  端口都相同即为同源
- 跨域问题：两台服务器A、B，如果从A服务器的业务发送异步请求到B获取数据，且A和B不满足同源策略，则会出现跨域问题
- 解决方案：添加相关的头，add_header
  - ![image-20240302223916620](Nginx课程学习-photos/image-20240302223916620.png)
- 案例
  - ![image-20240302220303244](Nginx课程学习-photos/image-20240302220303244.png)
  - ![image-20240302220430488](Nginx课程学习-photos/image-20240302220430488.png)
  - ![image-20240302220507057](Nginx课程学习-photos/image-20240302220507057.png)
  - ![image-20240302221137694](Nginx课程学习-photos/image-20240302221137694.png)
  - ![image-20240302224006719](Nginx课程学习-photos/image-20240302224006719.png)

### 防盗链及实现

- 什么是资源盗链？
  - 就是静态资源不在自己服务器上，通过技术手段，把别人的资源放到自己的页面上展示给用户。如在自己的页面上引入京东/百度的图片。

-   实现原理
  - http的头信息referer，告诉浏览器该网页从哪个页面链接跳转过来，后台服务器判断referer是否为自己信任的网站地址，是则继续访问，不是则返回403（服务器拒绝访问）
  - 指令：vilid_referers    可选值：none(Header中Refer为空时允许访问)   blocked（部位空，结果防火墙伪装的不带http://，https://）   server_names（具体的域名或IP）   string（~开头的正则表达式或带*的字符串） 
    - ![image-20240305235725463](Nginx课程学习-photos/image-20240305235725463.png)
    - ![image-20240305235736213](Nginx课程学习-photos/image-20240305235736213.png)
    - 扩展：可以结合后面的rewrite指令提升用户体验，403时给提示信息
      - ![image-20240317105517016](Nginx课程学习-photos/image-20240317105517016.png)
- 案例
  - html 引入nginx服务器资源
    - ![image-20240305235445069](Nginx课程学习-photos/image-20240305235445069.png)
  - ![image-20240306000209644](Nginx课程学习-photos/image-20240306000209644.png)
- 不足：referer的限制比较粗粒度（一类文件或者是一个目录），比如随意加一个Referer，上面的方式无法限制。需要使用三方模块： ngx_http_accesskey_module。

### Rewrite功能配置

- 一般用于URL重写，依赖PCRE库，Nginx使用的是ngx_http_rewrite_module模块来解析和处理Rewrite功能的相关配置
  - ![image-20240312223201493](Nginx课程学习-photos/image-20240312223201493.png)
- set指令
  - ![image-20240309194950297](Nginx课程学习-photos/image-20240309194950297.png)
  - rewrite常用全局变量
  - ![image-20240309210606469](Nginx课程学习-photos/image-20240309210606469.png)
  - ![image-20240309211432392](Nginx课程学习-photos/image-20240309211432392.png)
  - 使用示例
    - ![image-20240312223430350](Nginx课程学习-photos/image-20240312223430350.png)
    - ![image-20240309211635340](Nginx课程学习-photos/image-20240309211635340.png)
- if 指令
  - if 和 ( 之间一定要有一个空格；字符串不需要加引号，并且等号和不等号前后都要加空格；
  - ![image-20240312233038904](Nginx课程学习-photos/image-20240312233038904.png)
  - ![image-20240312233425593](Nginx课程学习-photos/image-20240312233425593.png)
  - ![image-20240312233618600](Nginx课程学习-photos/image-20240312233618600.png)
  - 示例
    - ![image-20240312233151423](Nginx课程学习-photos/image-20240312233151423.png)
    - ![image-20240312233926603](Nginx课程学习-photos/image-20240312233926603.png)
- break
  - break：同一个作用域内，break前的配置指令生效，break后的不生效；同时，终止当前的匹配并进行一次重定向（后面的return等不会去执行），即（默认从当前安装目录的html）去本地location对应目录下的静态资源（文件名默认是index.html）。
  - ![image-20240313181953981](Nginx课程学习-photos/image-20240313181953981.png)
  - ![image-20240313183741868](Nginx课程学习-photos/image-20240313183741868.png)
- return：向客户端返回，在return后的所有Nginx配置都是无效的
  - ![image-20240313194544634](Nginx课程学习-photos/image-20240313194544634.png)
  - ![image-20240313194851020](Nginx课程学习-photos/image-20240313194851020.png)
- rewrite指令
  - rewrite：通过正则表达式改变URI，如果字符串是http://或https://开头的，会直接返回重写后的uri。可以同时存在多个rewrite指令。    //rewrite后面的正则表达式中包含（），后面编写重写目的地址的时候可以用 $1、 $2等引用
  - ![image-20240313195346831](Nginx课程学习-photos/image-20240313195346831.png)
  - ![image-20240313200110465](Nginx课程学习-photos/image-20240313200110465.png)
  - flag: 设置rewrite对URI的处理行为，分 last(用新URI在当前server中匹配) 、 break（用新URI在当前location中匹配，找的就是静态资源文件了！）、  redirect（用新URI在当前server中匹配+301重定向)、  permanent（用新URI在当前server中匹配+302重定向）
    - ![image-20240313201411531](Nginx课程学习-photos/image-20240313201411531.png)
    - ![image-20240313201429779](Nginx课程学习-photos/image-20240313201429779.png)
    - ![image-20240313201454615](Nginx课程学习-photos/image-20240313201454615.png)
    - ![image-20240313201517413](Nginx课程学习-photos/image-20240313201517413.png)
- rewrite_log：是否开启URL重写日志的输出功能
  - ![image-20240313202746590](Nginx课程学习-photos/image-20240313202746590.png)
- rewrite的案例
  - 域名跳转：例如让www.360buy.com也重定向到www.jd.com
    - rewrite ^后面不跟任何就代表对server_name后面的内容没有任何限制，(.*)是为了重定向的时候把后面的uri一起带过来
    - ![image-20240313204404229](Nginx课程学习-photos/image-20240313204404229.png)
  - 域名镜像：和镜像网站类似，完全相同的网站放置到几台服务器上，实现 高可用、分布不同地区以提高响应速度、流量负载、不同镜像不同域名防止域名限制。上述的www.itheima.com  www.itheima.cn 都跳转www.itcast.cn，则www.ticast.cn就是主域名，另外两个就是镜像域名。也可以只对一个子目录资源做镜像，可以在location配置rewrite功能。
    - ![image-20240313205539654](Nginx课程学习-photos/image-20240313205539654.png)
  - 独立域名：为每一个功能模块设置独立的域名
    - ![image-20240316203612266](Nginx课程学习-photos/image-20240316203612266.png)
  - 目录自动添加  ”/“
    - nginx 0.8.48以前server_name_in_redirect的默认开关都是on，访问url不加斜杆，Nginx服务器内部会自动做一个301的重定向，目的地址（如果是nginx服务器）会被替换为server_name。
    - ![image-20240316215945986](Nginx课程学习-photos/image-20240316215945986.png)
    - ![image-20240316220003452](Nginx课程学习-photos/image-20240316220003452.png)
    - \$request_filename   \$host  \$server等都是全局变量； 下面的\[^/] 表示    去匹配最后一个字符不是/且最后一个字符不能为空； permanent保证了永久重定向；
    - ![image-20240316222108022](Nginx课程学习-photos/image-20240316222108022.png)
  - 合并目录
    - 搜索引擎优化（SEO）是一种利用搜索引擎的搜索规则提高目的网站在搜索引擎内排名的方式（简单举例就是 提升你在百度搜索结果的排名），其中一项就是URL目录层级不超过三级（过低 [即大量文件放一个目录] 的话有会有文件资源管理混乱+访问文件速度下降）。
    - 访问的时候通过名字添加 - 的方式降低目录层级，真正保存的时候一个 - 就是一个目录层级；
    - ![image-20240316224740173](Nginx课程学习-photos/image-20240316224740173.png)
    - ![image-20240316224803131](Nginx课程学习-photos/image-20240316224803131.png)
- vim小技巧
  - set nu;显示行号       31,36d；删除31-36行；
  - Control  v+选中多行+i+ #/d +esc，
  - gzip jquery.js  //压缩文件
  - chrome清楚浏览器缓存：ctrl +shift +del;   
- 其它小技巧
  - tree展示文件目录
  - cmd发送post请求： curl -X POST http://192.168.200.133:8081/testif
  - chmod 777的含义：http://www.mobiletrain.org/about/BBS/256716.html
  - 查看用户分组信息：cat /etc/group  http://www.mobiletrain.org/about/BBS/150835.html
  - break是301永久重定向；return是302临时重定向（重写地址是临时过渡的，和搜索引擎优化 su? 相关）  ;重定向跳转地址会变；





### Nginx实现代理（正向+反向）

#### Nginx代理概述及环境准备

 正向代理在客户端配置（隐藏客户端），反向代理在服务端配置。![image-20220717161933824](Nginx课程学习-photos/image-20220717161933824.png)

![image-20220717162045781](Nginx课程学习-photos/image-20220717162045781.png)

![image-20220717162607170](Nginx课程学习-photos/image-20220717162607170.png)



133

![image-20220717162848504](Nginx课程学习-photos/image-20220717162848504.png)

146

![image-20220717165247364](Nginx课程学习-photos/image-20220717165247364.png)

//uri:端口后面的所有内容

客户端经过配置，所有的请求会转到Nginx

![image-20220717165746326](Nginx课程学习-photos/image-20220717165746326.png)

![image-20220717170305004](Nginx课程学习-photos/image-20220717170305004.png)

#### Nginx反向代理的配置语法

![image-20220717170501197](Nginx课程学习-photos/image-20220717170501197.png)

 

![image-20220717170651584](Nginx课程学习-photos/image-20220717170651584.png)

//133代理上配置，服务器为146

![image-20220717170943552](Nginx课程学习-photos/image-20220717170943552.png)

![image-20220717171047105](Nginx课程学习-photos/image-20220717171047105.png)



![image-20220717182524881](Nginx课程学习-photos/image-20220717182524881.png)

//没有/的话，会自动把location添加到后面；

![image-20220717184612005](Nginx课程学习-photos/image-20220717184612005.png)

 





//不设置请求头的值的话，服务端只能活得代理的ip和端口；





146配置：

![image-20220717190551801](Nginx课程学习-photos/image-20220717190551801.png)

133配置

![image-20220717190445678](Nginx课程学习-photos/image-20220717190445678.png)



![image-20220717190909325](Nginx课程学习-photos/image-20220717190909325.png)

![image-20220814142729336](Nginx课程学习-photos/image-20220814142729336.png)

//133

![image-20220717191425815](Nginx课程学习-photos/image-20220717191425815.png)

//如下，133代理时地址不存在的时候重定向 到146主页，这时ip会跳转为146而不是133；仍然希望隐藏服务端的ip，返回代理服务器的地址；

//146

![image-20220717191830415](Nginx课程学习-photos/image-20220717191830415.png)

 ![image-20220717191849846](Nginx课程学习-photos/image-20220717191849846.png)



//133 对于146服务器上找不到资源的，先跳转到133的默认端口，然后在133的默认端口配置代理146；返回的信息就是133了，而index.html是146服务器上的，服务器的ip被隐藏

![image-20220717192253339](Nginx课程学习-photos/image-20220717192253339.png)

![image-20220717192727094](Nginx课程学习-photos/image-20220717192833169.png)

#### Nginx反向代理实战

服务器1 2 3的内容相同，则需要使用负载均衡；

![image-20220717193903925](Nginx课程学习-photos/image-20220717193903925.png)

![image-20220717193801840](Nginx课程学习-photos/image-20220717193801840.png)

//机器准备，机器有限，用146的不同端口模拟不同的服务器；

![image-20220717194010686](Nginx课程学习-photos/image-20220717194010686.png)

![image-20220717194133875](Nginx课程学习-photos/image-20220717194133875.png)

### Nginx安全相关

#### Nginx的安全控制

![image-20220717194650418](Nginx课程学习-photos/image-20220717194650418.png)

![image-20220717194702024](Nginx课程学习-photos/image-20220717194702024.png)

  ![image-20220717195105182](Nginx课程学习-photos/image-20220717195105182.png)

![image-20220717195120803](Nginx课程学习-photos/image-20220717195120803.png)

流量劫持的示例：中间人劫持你的请求，发送给下面的三方服务器；

![image-20220717195330365](Nginx课程学习-photos/image-20220717195330365.png)

#### Nginx添加ssl的支持（支持https请求）

nginx默认不支持https访问 

./nginx -V查看版本信息；

第三步的位置  ~/nignx/core/nginx-版本；//具体看你自己的nginx安装包位置；

第四步： 配置在原来配置的基础上添加http_ssl_module

![image-20220717195737577](Nginx课程学习-photos/image-20220717195737577.png)

#### ssl相关指令

![image-20220717203217943](Nginx课程学习-photos/image-20220717203217943.png)

http默认端口80，https默认端口443

![image-20220717203308153](Nginx课程学习-photos/image-20220717203308153.png)

//缓存较为常用；用于提升效率；

![image-2022071720381170](Nginx课程学习-photos/image-20220717203811170.png)

![image-20220717204032389](Nginx课程学习-photos/image-20220717204032389.png)

![](Nginx课程学习-photos/image-20220717203957662.png)

一般会设为on

![image-20220717204126404](Nginx课程学习-photos/image-20220717204126404.png)

#### 生成证书

![image-20220724103221773](Nginx课程学习-photos/image-20220724103221773.png)

![image-20220724103246146](Nginx课程学习-photos/image-20220724103246146.png)

![image-20220724103418342](Nginx课程学习-photos/image-20220724103418342.png)

![image-20220724103342820](Nginx课程学习-photos/image-20220724103342820.png)

证书控制台，证书申请，输入基本信息、域名（提前购买好），   验证 审批 签发后可用；

//第一种生产环境使用较多，学习期间相对麻烦；

![image-20220724104519232](Nginx课程学习-photos/image-20220724104519232.png)

#### 开启SSL实例

![image-20220724105346207](Nginx课程学习-photos/image-20220724105346207.png)

//nginx解压缩包下的conf/nginx.conf有对应的配置；

ctrl  v ,选中，delete;

![image-20220724105900985](Nginx课程学习-photos/image-20220724105900985.png)

![image-20220724105936863](Nginx课程学习-photos/image-20220724105936863.png)

//不安全是因为证书没经过三方验证； 用阿里云的方式生成key  pom文件，则没有这个问题；

![image-20220724110301735](Nginx课程学习-photos/image-20220724110301735.png)



用rewrite命令实现默认的访问方式是https：如www.baidu.com ，不需要加https前缀

![image-20220724110540932](Nginx课程学习-photos/image-20220724110540932.png)

#### 反向代理系统调优 

缓冲：如客户端不和服务器直接交互，中间多一层缓冲区，缓冲区依次和服务器A（例如A处理快，B处理慢，缓冲区可以再对A B的返回结果做一次重新排序，A就不用一直等） 、B交互。

缓存：代理服务器保存一份缓存数据，客户端再次发系统请求时只需要返回代理服务器上的缓存数据接口

![image-20220724111740947](Nginx课程学习-photos/image-20220724111740947.png)



![image-20220724111905757](Nginx课程学习-photos/image-20220724111905757.png)

![image-20220724112040895](Nginx课程学习-photos/image-20220724112040895.png)

![image-20220724112049304](Nginx课程学习-photos/image-20220724112049304.png)

![image-20220724112455907](Nginx课程学习-photos/image-20220724112455907.png)

![image-20220724112618634](Nginx课程学习-photos/image-20220724112618634.png)

![image-20220724112644951](Nginx课程学习-photos/image-20220724112644951.png)

### Niginx负载均衡

![image-20220724124744346](Nginx课程学习-photos/image-20220724124744346.png)

![image-20220724124514756](Nginx课程学习-photos/image-20220724124514756.png)

//反向代理重点在服务端的内容不一样的情况，负载均衡重点在服务端的内容一样的情况；

#### 负载均衡的原理及处理流程

![image-20220724124914627](Nginx课程学习-photos/image-20220724124914627.png)

![image-20220724125218578](Nginx课程学习-photos/image-20220724125218578.png)

![image-20220724125243598](Nginx课程学习-photos/image-20220724125243598.png)

#### 负载均衡常用的处理方式

![image-20220724125453417](Nginx课程学习-photos/image-20220724125453417.png)

 ![image-20220724125729165](Nginx课程学习-photos/image-20220724125729165.png)

![image-20220724130842505](Nginx课程学习-photos/image-20220724130842505.png)

![image-20220724130907390](Nginx课程学习-photos/image-20220724130907390.png)

tips

- ping命令可以查看域名对应的ip地址；一个域名可以绑定多个ip以实现负载均衡；
- DNS有本地缓存； ipconfig/flushdns；

![image-20220724131312607](Nginx课程学习-photos/image-20220724131312607.png)

![image-20220724131226756](Nginx课程学习-photos/image-20220724131226756.png)

![image-20220731133852156](Nginx课程学习-photos/image-20220731133852156.png)

![image-20220731134156047](Nginx课程学习-photos/image-20220731134156047.png)

![image-20220731134226770](Nginx课程学习-photos/image-20220731134226770.png)

硬件：贵；不易扩展；但是效率高

![image-20220731134524194](Nginx课程学习-photos/image-20220731134524194.png)

![image-20220731134600178](Nginx课程学习-photos/image-20220731134600178.png)

  

#### Nginx七层负载均衡

![image-20220731134731358](Nginx课程学习-photos/image-20220731134731358.png)

![image-20220731134935290](Nginx课程学习-photos/image-20220731134935290.png)

 ![image-20220731135018531](Nginx课程学习-photos/image-20220731135018531.png)

![image-20220731135220066](Nginx课程学习-photos/image-20220731135220066.png)

![image-20220731144926101](Nginx课程学习-photos/image-20220731144926101.png)

![image-20220731144955657](Nginx课程学习-photos/image-20220731144955657.png)

![image-20220731145232607](Nginx课程学习-photos/image-20220731145232607.png)

![image-20220731145426792](Nginx课程学习-photos/image-20220731145426792.png)

![image-20220731145524557](Nginx课程学习-photos/image-20220731145524557.png)

除了浏览器也可以用curl命令测试端口；

![image-20220731150100701](Nginx课程学习-photos/image-20220731150100701.png)

![image-20220731150903697](Nginx课程学习-photos/image-20220731150903697.png)

![image-20220731151926250](Nginx课程学习-photos/image-20220731151926250.png)

//systemctl start firewalld 开启防火墙

  ![image-20220731151640905](Nginx课程学习-photos/image-20220731151640905.png)

![image-20220731151748350](Nginx课程学习-photos/image-20220731151748350.png)

![image-20220731152040246](Nginx课程学习-photos/image-20220731152040246.png)

![image-20220731152110962](Nginx课程学习-photos/image-20220731152110962.png)

![image-20220731153043548](Nginx课程学习-photos/image-20220731153043548.png)

![image-20220731153326463](Nginx课程学习-photos/image-20220731153326463.png)

//问题：服务器性能可能不同；

![image-20220731153357324](Nginx课程学习-photos/image-20220731153357324.png)

![image-20220731154024222](Nginx课程学习-photos/image-20220731154024222.png)

//问题：web需要登录的场景，通过session保存登录信息，不同服务器之间的session不共享，则需要登录多次；故需要把单台服务器的请求固定到单台web服务器上；

![image-20220731155133510](Nginx课程学习-photos/image-20220731155133510.png)

![image-20220731155258331](Nginx课程学习-photos/image-20220731155258331.png)

//ip_hash考虑的是登录 信息缓存不命中的问题；但是可能造成负载不均衡，可以把session信息都保存到redis中；

![image-20220731155427470](Nginx课程学习-photos/image-20220731155427470.png)



![image-20220731160125050](Nginx课程学习-photos/image-20220731160125050.png)

![image-20220731160156070](Nginx课程学习-photos/image-20220731160156070.png)

![image-20220731160454393](Nginx课程学习-photos/image-20220731160454393.png)

url_hash针对的是文件缓存命中的问题； 

![image-20220731161344737](Nginx课程学习-photos/image-20220731161344737.png)

![image-20220731161510225](Nginx课程学习-photos/image-20220731161510225.png)

 ![image-20220731162315814](Nginx课程学习-photos/image-20220731162315814.png)

![image-20220731162533585](Nginx课程学习-photos/image-20220731162533585.png)

![image-20220731162855130](Nginx课程学习-photos/image-20220731162855130.png)

vim:  /表示搜索；

![image-20220731163042211](Nginx课程学习-photos/image-20220731163042211.png)

  //注意：有两个nginx文件夹，一个是nginx的源码，make的时候在源码；另一个是安装目录，存放可执行文件；？？？？

![image-20240405225356782](Nginx课程学习-photos/image-20240405225356782.png)

![image-20240405225410987](Nginx课程学习-photos/image-20240405225410987.png)

![image-20220731165114558](Nginx课程学习-photos/image-20220731165114558.png)

![image-20220731165557074](Nginx课程学习-photos/image-20220731165557074.png)

![image-20220731165937431](Nginx课程学习-photos/image-20220731165937431.png)

#### Nginx四层负载均衡

![image-20220731171123511](Nginx课程学习-photos/image-20220731171123511.png)

![image-20220731172041265](Nginx课程学习-photos/image-20220731172041265.png)

![image-20220731172050405](Nginx课程学习-photos/image-20220731172050405.png)

  ![image-20220731172245794](Nginx课程学习-photos/image-20220731172245794.png)

![image-20220731172316547](Nginx课程学习-photos/image-20220731172316547.png)

![image-20220731172803918](Nginx课程学习-photos/image-20220731172803918.png)

//允许所有服务器访问reids

![image-20220731173210851](Nginx课程学习-photos/image-20220731173210851.png)

启动reids:

![image-20220731173507877](Nginx课程学习-photos/image-20220731173507877.png)

再启动一个redis：

![image-20220731173528758](Nginx课程学习-photos/image-20220731173528758.png)

同样改配置，启动；



关闭redis:

![image-20220731173239647](Nginx课程学习-photos/image-20220731173239647.png)

连接redis，安装redis客户端，在cmd

![image-20220731173327211](Nginx课程学习-photos/image-20220731173327211.png)

四层和七层的负载均衡，在nginx的底层有什么不同吗？？？？？

![image-20220731231029401](Nginx课程学习-photos/image-20220731231029401.png)

https://blog.csdn.net/tongzidane/article/details/125443140

![image-20220731225426649](Nginx课程学习-photos/image-20220731225426649.png)

![image-20220731225651625](Nginx课程学习-photos/image-20220731225651625.png)

![image-20220731225838760](Nginx课程学习-photos/image-20220731225838760.png)

![image-20220731230120851](Nginx课程学习-photos/image-20220731230120851.png)

//四层和七层如果监听同一个端口，生效的应该是四层；



### Nginx缓存

#### 缓存集成

- 缓存维护及使用流程：缓存命中/不命中的情况
  - ![image-20240406182438356](Nginx课程学习-photos/image-20240406182438356.png)
- 缓存使用场景
  - ![image-20240406182804279](Nginx课程学习-photos/image-20240406182804279.png)
- 优缺点  //高可用，是指缓存也是临时的备份，给服务器更多维修时间
  - ![image-20240406182822831](Nginx课程学习-photos/image-20240406182822831.png)
- Nginx作为Web服务器缓存  生效流程
  - ![image-20240406183051368](Nginx课程学习-photos/image-20240406183051368.png)
- Nginx URL缓存、状态码缓存流程 
  - ![image-20240406190736856](Nginx课程学习-photos/image-20240406190736856.png)
- Nginx缓存相关指令
  - proxy_cache_path:设置缓存文件的存放路径 //注意：只能再http块中配置
  - ![image-20240406191735190](Nginx课程学习-photos/image-20240406191735190.png)
  - ![image-20240406192055900](Nginx课程学习-photos/image-20240406192055900.png)
  - ![image-20240406192214943](Nginx课程学习-photos/image-20240406192214943.png)
  - ![image-20240406192440332](Nginx课程学习-photos/image-20240406192440332.png)
  - proxy_cache：缓存区的名字要和proxy_cache_path中指定的缓存区名称一致
    - ![image-20240406192931297](Nginx课程学习-photos/image-20240406192931297.png)
  - proxy_cache_key: web缓存的key值，Nginx根据key值MD5哈希缓存
    - ![image-20240406193130924](Nginx课程学习-photos/image-20240406193130924.png)
  - proxy_cache_valid：对不同的状态码的URL设置不同的缓存时间//从上到下适配，第一个命中的生效
    - ![image-20240406193152903](Nginx课程学习-photos/image-20240406193152903.png)
    - ![image-20240406193600417](Nginx课程学习-photos/image-20240406193600417.png)
  - proxy_cache_min_uses：设置资源被访问多少次后被缓存
    - ![image-20240406200335347](Nginx课程学习-photos/image-20240406200335347.png)
  - proxy_cache_methods：设置缓存哪些HTTP方法
    - ![image-20240406200350156](Nginx课程学习-photos/image-20240406200350156.png)
- Nginx缓存案例
  - ![image-20240406200517088](Nginx课程学习-photos/image-20240406200517088.png)
  - 阶段一：可以正常133代理请求
    - ![image-20240407191311126](Nginx课程学习-photos/image-20240407191311126.png)
  - 阶段二：开启nginx缓存  //查看缓存是否命中的方法：查看nginx服务器是否生成目录或文件；添加发回头$upstream_cache_status；
    - ![image-20240407191147777](Nginx课程学习-photos/image-20240407191147777.png)
  - 阶段三：自定义缓存key、min_use等；
    - ![image-20240408185919471](Nginx课程学习-photos/image-20240408185919471.png)
- nginx缓存删除
  - 删除对应的缓存目录//适合批量删除缓存的场景
    - rm  -rf /usr/local/proxy_cache/  ....
  - 使用第三方扩展模块： 使用proxy_cache_purge模块 + nginx配置purge==（注意key带变量的话，要保证正常访问、和purge请求对应的变量值保持一致）== + 前端发请求删除
    - ![image-20240408193558719](Nginx课程学习-photos/image-20240408193558719.png)
    - ![image-20240408193654279](Nginx课程学习-photos/image-20240408193654279.png)
    - ![image-20240408193806235](Nginx课程学习-photos/image-20240408193806235.png)
- Nginx设置资源不缓存
  - 对于经常变化的数据，不进行缓存
  - proxy_no_cache：不将数据进行缓存
    - ![image-20240408194946193](Nginx课程学习-photos/image-20240408194946193.png)
  - proxy_cache_bypass：不从缓存中获取数据 
    - ![image-20240408195045457](Nginx课程学习-photos/image-20240408195045457.png)
    - ![image-20240408195935932](Nginx课程学习-photos/image-20240408195935932.png)
  -  案例一（proxy_no_cache/proxy_cache_bypass 在用法上都是一样的）：常用方式是设置上面三个条件，然后不缓存的资源在请求上添加参数nocache或comment即可
    -  ![image-20240408201100519](Nginx课程学习-photos/image-20240408201100519.png)
    - ![image-20240408201011230](Nginx课程学习-photos/image-20240408201011230.png)
  - 案例二：自定义if块第一过滤条件
    - ![image-20240408202024307](Nginx课程学习-photos/image-20240408202024307.png)

### Nginx实现服务集群搭建

- ![image-20240410165452950](Nginx课程学习-photos/image-20240410165452950.png)
- ![image-20240410165113599](Nginx课程学习-photos/image-20240410165113599.png)
- ![image-20240410165428745](Nginx课程学习-photos/image-20240410165428745.png)
- 为什么可以直接访问tomcat，还要多一层nginx，提高系统复杂度?
  - 使用nginx实现动静分离 //动即后台应用程序的业务处理；静即网站的静态资源（html, javaScript, css, image等）；动静分离即静态资源部署nginx/cdn等，动态资源部署tomcat/weblogic/websphere等服务器好处是nginx的==静态资源处理效率高+并发高，且实现了动态资源和静态资源的解耦；==     //nginx的并发在5W左右，tomcat在500左右；
  - ==Nginx搭建Tomcat的集群，避免后端的单点故障==
- ![image-20240410182607305](Nginx课程学习-photos/image-20240410182607305.png)
- 例：主页、js等资源放在nginx；后端接口的请求转发到146
  - ![image-20240411161156634](Nginx课程学习-photos/image-20240411161156634.png)
- nginx搭建tomcat集群，流量分发到多台服务器 //这里用不同的端口模拟不同的机器;  需要改tomcat/conf/server.xml，修改端口8005->8105 8080->8180
  - ![image-20240411164245327](Nginx课程学习-photos/image-20240411164245327.png)
  - ![image-20240411164855222](Nginx课程学习-photos/image-20240411164855222.png)

### Nginx高可用解决方案之keep alived

- c语言编写，为LVS负载均衡软件设计，通过VRRP协议实现高可用  //避免nginx单点故障

- VRRP

  - 简介：虚拟路由冗余协议，优先级高的是master节点，请求由master结点处理。master定时发送当前状态信息，backup接收状态信息（超时未收到则认为master出问题了）
  - 核心：选择协议和路由容错协议
    - ![image-20240418194720106](Nginx课程学习-photos/image-20240418194720106.png)
    - ![image-20240418200039508](Nginx课程学习-photos/image-20240418200039508.png)

- keep alived实践

  - 安装keep alived

    - ![image-20240418195758918](Nginx课程学习-photos/image-20240418195758918.png)

  - keep alived配置文件

    - global全局配置、vrrp相关配置、LVS相关配置，重要的配置 priority

    - ![image-20240418203445693](Nginx课程学习-photos/image-20240418203445693.png)

    - ![image-20240418203529873](Nginx课程学习-photos/image-20240418203529873.png)

    - ```
      VRRP部分，该部分可以包含以下四个子模块
      1. vrrp_script
      2. vrrp_sync_group
      3. garp_group
      4. vrrp_instance
      我们会用到第一个和第四个，
      #设置keepalived实例的相关信息，VI_1为VRRP实例名称
      vrrp_instance VI_1 {
          state MASTER  		#有两个值可选MASTER主 BACKUP备
          interface ens33		#vrrp实例绑定的接口，用于发送VRRP包[当前服务器使用的网卡名称]
          virtual_router_id 51#指定VRRP实例ID，范围是0-255
          priority 100		#指定优先级，优先级高的将成为MASTER
          advert_int 1		#指定发送VRRP通告的间隔，单位是秒
          authentication {	#vrrp之间通信的认证信息
              auth_type PASS	#指定认证方式。PASS简单密码认证(推荐)
              auth_pass 1111	#指定认证使用的密码，最多8位
          }
          virtual_ipaddress { #虚拟IP地址设置虚拟IP地址，供用户访问使用，可设置多个，一行一个
              192.168.200.222
          }
      }
      ```

  - 访问测试

    - ![image-20240418203812434](Nginx课程学习-photos/image-20240418203812434.png)
    - ![image-20240418203827214](Nginx课程学习-photos/image-20240418203827214.png)
    - ![image-20240418205121562](Nginx课程学习-photos/image-20240418205121562.png)

  - 如何让keepalived自动判断nginx是否启动并自动启动/停止 keepalived？  说明：正常情况下keepalived不能检测到nginx是否正常的（只能监控网络故障和keepalived自身），如果nginx挂了，keppalived，也是无法正常漂移的。可以编写vrrp_script脚本检测服务器的nginx是否正常，异常则切换

    - ![image-20240421154202542](Nginx课程学习-photos/image-20240421154202542.png)
    - ![image-20240421154456966](Nginx课程学习-photos/image-20240421154456966.png)
    - ![image-20240616165937425](Nginx课程学习-photos/image-20240616165937425.png)
    - ![image-20240616170440727](Nginx课程学习-photos/image-20240616170440727.png)
      - //当前机器的实例下要添加新增的脚本
      - ![](Nginx课程学习-photos/image-20240421155835472.png)

    - 实验：脚本只保留最后一个if；配置好keppalived相关内容；重启keepalived；nginx -s stop模拟nginx，(ip -a)会发现keepalived漂移到其它的机器了; 重启nginx和keepalived，(ip -a)会发现keepalived漂移回来了；

      - ![image-20240421160159263](Nginx课程学习-photos/image-20240421160159263.png)

    - 问题

      - ![image-20240421161201541](Nginx课程学习-photos/image-20240421161201541.png)
      - （master/高优先级的实例宕机后，backup会成为主节点；但是master/高优先级恢复时，因为竞争机制 master/高优先级 会二次切换为主节点    但是二次切换其实是非必要的）
        - 上面  weight -20意思是如果脚本成功停止了keepalived服务，则优先级-20。
        - 所以这里的解决方案是：所有的实例设置的都是 backup+ nopreempt，通过priority来竞争 (nopreempt的使用还没有验证过 )

### Nginx制作下载站点

- 可以使用nginx的ngx_http_autoindex_module模块来实现，该模块处理以“/”结尾的请求，并生成目录列表。
  - ![image-20240421162247481](Nginx课程学习-photos/image-20240421162247481.png)
  - ![image-20240421163535169](Nginx课程学习-photos/image-20240421163535169.png)
  - autoindex-format设置的值为html时才能生效
  - ![image-20240421163629338](Nginx课程学习-photos/image-20240421163629338.png)
  - ![image-20240421163642931](Nginx课程学习-photos/image-20240421163642931.png)
  - ![image-20240421165646613](Nginx课程学习-photos/image-20240421165646613.png)
- 实验
  - 资源都放到一个文件夹；添加nginx配置

### Ngixn用户认证模块的使用

- 可以用ngx_http_auth_basic_module实现，允许通过HTTP基本身份验证 协议验证用户名和密码来限制对资源的访问，默认安装（可以用--without-http_auth_basic_module取消） 
- ![image-20240421190637174](Nginx课程学习-photos/image-20240421190637174.png)
- ![image-20240421190740803](Nginx课程学习-photos/image-20240421190740803.png)
- 实验：
  - ![image-20240421191014477](Nginx课程学习-photos/image-20240421191014477.png)
  - ![image-20240421191026629](Nginx课程学习-photos/image-20240421191026629.png)
  - ![image-20240421192435676](Nginx课程学习-photos/image-20240421192435676.png)

### lua的概念介绍//==语法不是重点，关注Nginx与脚本语言的配合方式==

- 轻量、小巧的脚本语言，c语言编写，可嵌入其它应用程序，为其它应用程序提供扩展和定制功能。
- 优点：轻量级、可扩展、支持面向过程编程和函数式编程
  - ![image-20240421202059288](Nginx课程学习-photos/image-20240421202059288.png)
- 应用场景：
  - 游戏开发、独立应用脚本、web应用脚本、扩展和数据库插件、系统安全

### Lua的安装

- 下载源码包并在终端解压、编译即可使用
- ![image-20240421202347294](Nginx课程学习-photos/image-20240421202347294.png)
- ![image-20240421202724262](Nginx课程学习-photos/image-20240421202724262.png)

### Lua语法

- 交互方式：交互式和脚本式（可以用lua命令执行；如果要用./执行，需要在脚本第一行指定lua解释器）；语句末尾 是否加分号、是否换行都是等价的；
  - ![image-20240421203557996](Nginx课程学习-photos/image-20240421203557996.png)
  - ![image-20240421203808752](Nginx课程学习-photos/image-20240421203808752.png)
  - ![image-20240421203924732](Nginx课程学习-photos/image-20240421203924732.png)
  - ![image-20240421204021062](Nginx课程学习-photos/image-20240421204021062.png)
  - ![image-20240421204248260](Nginx课程学习-photos/image-20240421204248260.png)
- Lua常见运算符
  - 注释：单行注释  -- 、多行注释 --[[       --]]、取消多行注释  ---[[       ---]]
  - 标识符：
    - 大小写字母/下划线开头后加上0个或多个字母/下划线/数字‘
  - ![image-20240425231756082](Nginx课程学习-photos/image-20240425231756082.png)
  - ![image-20240425231812335](Nginx课程学习-photos/image-20240425231812335.png)
  - ![image-20240425231858331](Nginx课程学习-photos/image-20240425231858331.png)
  - ![image-20240425231906945](Nginx课程学习-photos/image-20240425231906945.png)
  - ![image-20240425232003209](Nginx课程学习-photos/image-20240425232003209.png)
  - ![image-20240425234953864](Nginx课程学习-photos/image-20240425234953864.png)

### Lua数据类型

- ![image-20240427221234130](Nginx课程学习-photos/image-20240427221234130.png)
- ![image-20240427221341329](Nginx课程学习-photos/image-20240427221341329.png)
- ![image-20240427221515476](Nginx课程学习-photos/image-20240427221515476.png)
- ![image-20240427222033655](Nginx课程学习-photos/image-20240427222033655.png)
- ![image-20240427222514510](Nginx课程学习-photos/image-20240427222514510.png)
- ![image-20240427223001774](Nginx课程学习-photos/image-20240427223001774.png)
- ![image-20240427223202042](Nginx课程学习-photos/image-20240427223202042.png)
- ![image-20240427223231772](Nginx课程学习-photos/image-20240427223231772.png)
- ![image-20240427223255158](Nginx课程学习-photos/image-20240427223255158.png)
- ![image-20240502115154135](Nginx课程学习.assets/image-20240502115154135.png)
- ![image-20240502115226443](Nginx课程学习.assets/image-20240502115226443.png)
- ![image-20240502115245614](Nginx课程学习.assets/image-20240502115245614.png)

### Lua控制语句

- ![image-20240502120111229](Nginx课程学习.assets/image-20240502120111229.png)
- ![image-20240502120402472](Nginx课程学习.assets/image-20240502120402472.png)
- ![image-20240502132646233](Nginx课程学习.assets/image-20240502132646233.png)
- ![image-20240502132808521](Nginx课程学习.assets/image-20240502132808521.png)
- ![image-20240502133955934](Nginx课程学习.assets/image-20240502133955934.png)
- ![image-20240502134906821](Nginx课程学习.assets/image-20240502134906821.png)
- ![image-20240502134952794](Nginx课程学习.assets/image-20240502134952794.png)

### Ngx_lua模块

- Lua解释器集成进nginx，以实现业务逻辑；Lua内建协程，保证高并发服务能力的同时降低了业务逻辑实现成本

- 模块环境准备
  - lua-nginx-module模块
    - ![image-20240502140351260](Nginx课程学习.assets/image-20240502140351260-4629832.png)
    - ![image-20240502140433948](Nginx课程学习.assets/image-20240502140433948.png)
    - ![image-20240502140524186](Nginx课程学习.assets/image-20240502140524186.png)
    - ![image-20240502140549352](Nginx课程学习.assets/image-20240502140549352.png)
    - ![image-20240502140610711](Nginx课程学习.assets/image-20240502140610711.png)
  - OpenRestry
    - http://openrestry.org    基于Nginx于Lua的高性能web平台，能够搭建高并发、扩展性好的 Web应用、Web服务和动态网关
    - ![image-20240502141055596](Nginx课程学习.assets/image-20240502141055596.png)
  
- nginx_lua指令
  - 用lua编写nginx脚本以指令为单位，指定指定lua代码的运行时机和结果的使用方法
  - ![image-20240502160807862](Nginx课程学习.assets/image-20240502160807862.png)
  - ![image-20240502161036489](Nginx课程学习.assets/image-20240502161036489.png)
  - ![image-20240502161105272](Nginx课程学习.assets/image-20240502161105272.png)
  - ![image-20240502161122756](Nginx课程学习.assets/image-20240502161122756.png)
  
- Ngx_lua使用set_by_lua指令
  - ![image-20240502161207744](Nginx课程学习.assets/image-20240502161207744.png)
  - ![image-20240502161848209](Nginx课程学习.assets/image-20240502161848209.png)
  - ![image-20240502163742025](Nginx课程学习.assets/image-20240502163742025.png)
  
-  Ngx_lua操作Redis
  - Nginx支持3中方法访问Redis，分别是HttpRedis模块(适合做简单缓存)、HttpRedis2Module(功能比前一个稍强)、lua-resty-redis（推荐，适合复杂的业务逻辑）
  - ![image-20240502165049574](Nginx课程学习.assets/image-20240502165049574.png)
  - ![image-20240502165548039](Nginx课程学习.assets/image-20240502165548039.png)
  - 下面的lcoation少了个/，/testRedis
  - ![image-20240502180245539](Nginx课程学习.assets/image-20240502180245539.png)
  - ![image-20240502180424885](Nginx课程学习.assets/image-20240502180424885.png)
  
- ngx_lua操作Mysql
  - 两种访问模式
    - Ngx_lua模块和lua-regsty-mysql模块：这两个模块是安装OpenResty时默认安装的 //适合复杂的业务场景，同时支持存储过程的访问
    - Drizzle_nginx_module(HttpDrizzleModule)模块：需要单独安装，这个库不在OpenResty中
  - ![image-20240502181228279](Nginx课程学习.assets/image-20240502181228279.png)
    - ![image-20240502181329364](Nginx课程学习.assets/image-20240502181329364.png)
    - ![image-20240502181432053](Nginx课程学习.assets/image-20240502181432053.png)
    - ![image-20240502181512617](Nginx课程学习.assets/image-20240502181512617.png)
    - ![image-20240504111458958](Nginx课程学习.assets/image-20240504111458958.png)
    - ![image-20240504111539697](Nginx课程学习.assets/image-20240504111539697.png)
    - ![image-20240504112217560](Nginx课程学习.assets/image-20240504112217560.png)
    - ![image-20240504111955670](Nginx课程学习.assets/image-20240504111955670.png)
  
  - #### lua-resty-mysql查询多条数据 + lua-cjson处理查询结果（适用于不知道表结构的情况）+init_by_lua_block
  
    - //lua中 ..是字符串的连接符
    -  ![image-20240602204503329](Nginx课程学习-photos/image-20240602204503329.png)
    - ![image-20240602204545732](Nginx课程学习-photos/image-20240602204545732.png)
    - ![image-20240602204707674](Nginx课程学习-photos/image-20240602204707674.png)
    - init_by_lua_block ： 每次启动的时候都会执行一次，适合放require这种引入语句
  
  - db:query
  
    - 是send_query 和 read_result功能的组合
      - ![image-20240602205648909](Nginx课程学习-photos/image-20240602205648909.png)
  
  - 增删改查
  
    - ![image-20240602210355623](Nginx课程学习-photos/image-20240602210355623.png)
  
- 综合案例：ngx_lua模块完成Redis缓存预热
  
  - ![image-20240602211120769](Nginx课程学习-photos/image-20240602211120769.png)
  - ![image-20240602211253542](Nginx课程学习-photos/image-20240602211253542.png)
  - ![image-20240602211319218](Nginx课程学习-photos/image-20240602211319218.png)
  - ![image-20240602211435862](Nginx课程学习-photos/image-20240602211435862.png)
  - ![image-20240602211649340](Nginx课程学习-photos/image-20240602211649340.png)
  
- Tips:
  
  - tar -zxf ....  -C  targetDirectory  
  - redis连接工具：redis desktop manager
  - 问：redis和lua的结合是如何实现的？？redis的解释器结合了lua的解释器，识别到lua的指令时，使用Lua的解释器。
