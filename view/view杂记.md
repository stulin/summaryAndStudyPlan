- spring的事务是如何回滚的？    或者说  spring的事务管理是如何实现的？
  - 总：spring事务是由AOP实现的，首先生成代理对象，然后按照AOP整套流程执行具体的操作逻辑；正常情况下需要通过通知完成核心功能，但是spring中事务通过TransactionInterceptor实现的，调用invoke实现具体的逻辑；
    - 分：1.做准备工作（解析各个方法上事务相关的属性，如隔离性、传播特性等）；2.依据具体的事务判断是否开启新事务，确定需要开启，则 获取数据库连接 关闭自动提交 开启事务；3. 执行具体的sql逻辑操作；4.操作过程中，如果执行失败了，那么会通过CompleteTransactionAfterThrowing来完成事务的回滚操作，回滚的具体逻辑是通过doRollBack方法来实现的，实现的时候也是要先获取连接对象，通过连接对象来回滚；5.执行的过程中，如果没有任何意外情况的发生，那么通过CommitTransactionAfterReturning来完成事务的提交操作，提交的具体逻辑是通过doCommit方法来实现的，实现的时候也是要先获取连接对象，通过连接对象来提交；6. 当事务执行完毕之后需清除相关的事务信息，cleanUpTransactionInfo；
    - 如果要聊更细致的话，需要知道TransactionInfo、TransactionStatus等类；
  -  题外话：事务的回滚最后都是数据库的回滚，多个事务由多个连接 connectHolder，开启事务 关闭自动提交都是连接维度的；(事务分 声明式事务、编程式事务) ；spring五种类型通知：before after around  afterThrowing afterReturning
- spring如何实现递归回滚事务？（或者说同步提交）//这个问题很巧，融合了 spring、 数据库、  threadLocal、事务
  - 如果我自己实现的话：
    - 事务的回滚最后都是数据库的回滚，
  - 要保证方法递归回滚，只需要保证多个方法中的sql语句都在==一个事务==里，
    - 故需要保证多个方法==共用一个   数据库连接(需要了解下jdbc是如何获取数据库连接的)== ，可以把 数据库连接作为参数传递给子方法；或者把数据库连接保存到ThreadLocal中；再或者改写数据库驱动的getConnectioin方法，使得同一个线程获取到的总是同一个数据库连接即可；
    - 最终的目标就一个：同一个线程的不同方法便可以共用这个数据库连接(spring应该是先从dataSource获取，然后保存在ThreadLocal变量中)；
  - spring是不是这么做的只需要看下源码，回滚的时候数据库连接 是不是从threadlocal中获取的；
  - ==todo:  扩展：spring结合jdbc如何获取数据库连接？==
- ==看看自己的笔记，把ThreadLocal的内容也梳理出来？==



https的原理？仔细说说五次握手的过程？



如何自己实现一个spring框架？



