# 前言
主要看书为主,书本的话错误相对较少,但是得考虑书本的年代,比如go,版本太低的话很多东西太旧了

其次考虑看文章,博客园的文章质量相对于CSDN较高,可以通过博客园进行名词搜索;也可以考虑掘金社区的文章,CSDN的文章抄袭居多,因为量太大了,感觉质量差的文章很多,但是也有好的文章
# GO
## 公众号
刘丹冰 小徐先生的编程世界 go语言中文网 微服务实践 架构师尼恩(八股内容一般般,关于三高架构的文章质量比较高),[go梦工厂](https://mp.weixin.qq.com/mp/appmsgalbum?__biz=MzkyNzI1NzM5NQ==&action=getalbum&album_id=1932319304830517254&scene=173&from_msgid=2247484781&from_itemidx=1&count=3&nolastread=1#wechat_redirect)

## 无分类

[入门视频,用户入门和查漏补缺](https://www.bilibili.com/video/BV1EB4y1D7WW/?spm_id_from=333.788&vd_source=1063dec5ba093fbbf0591f3c9003cee8)

[Go语言底层原理剖析，必看且多看几遍,全且深,类似于Java里的Java核心卷1+深入理解JVM]()

[B站视频,涉及到汇编和指针,不适合0基础直接看,等有一定基础后再看](https://www.bilibili.com/video/BV1hv411x7we?p=1&vd_source=1063dec5ba093fbbf0591f3c9003cee8)

[Go语言设计与实现，涉及到汇编和机器码的知识点太多了,不适合0基础和面试食用](https://draveness.me/golang/docs/part2-foundation/ch05-keyword/golang-panic-recover/)

[for range的坑](https://mp.weixin.qq.com/s?__biz=MzkyNzI1NzM5NQ==&mid=2247484755&idx=1&sn=5e3f8405dc8244875614cc936fbfd601&source=41#wechat_redirect)

[sync.once的底层,互斥锁+aotomic包实现,主要是后者的三道面试题](https://mp.weixin.qq.com/s?__biz=MzkyNzI1NzM5NQ==&mid=2247484782&idx=1&sn=472e7ecef81a11f83abda18172ec53f5&chksm=c22b8332f55c0a2488a7e2e1dcd9d2bf3afb764b29e0733d6307e6f6d5d4fde8b550a4cc4e18&scene=178&cur_album_id=1932319304830517254#rd)

[go的伪汇编,cgo知识点等等介绍,感觉挺有意思的,可以看看](https://chai2010.cn/advanced-go-programming-book/index.html)

[《go学习笔记》,涉及到汇编,go版本有点老,很多知识点比较旧,无在线地址,存在网盘里,不是特别推荐看]()

[工具书,感觉内容有点老,可能会用到吧](https://github.com/astaxie/build-web-application-with-golang/blob/master/zh/preface.md)

[go栈扩容](https://www.cnblogs.com/davygeek/p/9871256.html)

## unsafe

[unsafe包主要是unsafe.Pointer是一种万能指针,它能将安全的指针转化Pointer直接进行内存管理,也可以转为安全类型且别的类型的指针,同时可以转为uintptr进行偏移量的计算,最经典的应用是StringBuilder实现零拷贝](https://blog.csdn.net/Mazi1994/article/details/124864996)

[unsafe包的应用,零拷贝实现[]byte和string的转换](https://mp.weixin.qq.com/s?__biz=MzkyNzI1NzM5NQ==&mid=2247484941&idx=1&sn=326abc6706a092e36af32a5b682e6e3c&chksm=c22b8051f55c0947df20327d7993878f1086c5391ec5890ae78e17df2c7627bd4bf345010f9b&scene=178&cur_album_id=1932319304830517254#rd)

[atomic包的cas,乐观锁(无锁),通过unsafe包实现,同时go的cas是没有aba问题的](https://mp.weixin.qq.com/s?__biz=MzkyNzI1NzM5NQ==&mid=2247484781&idx=1&sn=dcd593f3fe1fa8fe75a18dbd53802dc8&source=41#wechat_redirect)
## Runtime
[只用看垃圾回收,内存管理,内存分配部分,其他部分太简略了没必要看,初级八股,面小厂够用了,面大厂可能会叼你说只知道八股](https://www.yuque.com/aceld/golang)

[GMP,主要是协程的7个状态以及它的小结,讲GMP先介绍它们的数据结构,比如g的结构体和Gfree,p是调度器以及最大并发数和plist,m是内核线程,gmp三个结构体的映射关系,然后讲调度,从三个角度来讲,调度循环,调度策略和调度时机,调度循环是先讲g0是什么,再说g0->g->g的过程中间调用了schedule（调度策略）,exec(GP之间的绑定和解绑),gogo(操作系统里寄存器的指令),然后讲schedule是调度策略,p先看runext,如果没有则去看runq,如果还没有再去看全局队列,如果再没有再去看网络通信里,还没有则去stealing,stealing不到则自旋,自选后还没有就handoff;对于全局队列,为了防止饥饿,g执行一定次数后会去全局队列里调度;然后讲调度时机,和exec有关,分为主动调度,被动调度和抢占调度,主动调度是自己执行runtime.schedul,将runq和nextq放到全局队列里;被动调度指的是gc,M阻塞等等调用gopark,注意并不会把g放入全局队列,而是调用exec进行解绑;最后是抢占式调度,1.14版本之后解决gc的时候没有抢占的问题](https://zhuanlan.zhihu.com/p/502740833?utm_id=0)

[触发gc的时机](https://mp.weixin.qq.com/s/e2-NXWCS0bd2BPWzdeiS_A)

[协程和线程主要从内存空间,上下文切换以及创建和销毁]()

## map,chan,slice
[slice考点比较少,讲一讲底层复用,讲一讲深拷贝和浅拷贝,讲一讲扩容机制](https://mp.weixin.qq.com/s/uNajVcWr4mZpof1eNemfmQ)

[map,主要的回答点在扩容机制,range无序和为何无序以及如何无序,key如何定位到一个value,就是整个hash映射方式(高8lowB)+结构体的记忆](https://mp.weixin.qq.com/s?__biz=MzkxMjQzMjA0OQ==&mid=2247483868&idx=1&sn=6e954af8e5e98ec0a9d9fc5c8ceb9072&chksm=c10c4f02f67bc614ff40a152a848508aa1631008eb5a600006c7552915d187179c08d4adf8d7&scene=178&cur_album_id=2709593649634033668#rd)

[chan主要讲它实现了go的csp,然后讲一讲csp的优点解耦,缺点是容易写出死锁,再讲一讲它的结构体,讲一讲它通过结构体里的互斥锁实现同步,讲一讲带缓冲的之间的区别,讲一讲阻塞请求/接受队列,讲一讲不同状态下进行请求,发送和关闭](https://mp.weixin.qq.com/s/QgNndPgN1kqxWh-ijSofkw)

## socket编程

[socket编程基础知识](https://www.cnblogs.com/twoheads/p/10712094.html)

[net包](https://mp.weixin.qq.com/s/xt0Elppc_OaDFnTI_tW3hg)

[http包](https://mp.weixin.qq.com/s?__biz=MzkxMjQzMjA0OQ==&mid=2247484040&idx=1&sn=b710f4429188ea5f49f6a9155381b67f&chksm=c10c4c56f67bc540971550d92b4d9339fce806c9daf94e971fd71a1cca823f2bbcea863b3cc8&scene=178&cur_album_id=2709593649634033668#rd)

[gin框架](https://mp.weixin.qq.com/s/x8i9HvAzIHNbHCryLw5icg)

# Linux

[epoll的缺陷主要在多核消费fd,tl可能有惊群效应,所有的线程(因为多CPU所以一个cpu一个线程)都被唤醒有惊群效应,el可能有不必要的唤醒问题,因此用标志位+tl](https://www.zhihu.com/question/26101751)

[查看最近访问的ip的次数,通过ngnix日志进行统计](https://blog.csdn.net/xu710263124/article/details/119875291)

[chomd权限的计算,二进制100是读,010是写,001是可执行,后续三个数字代表文件拥有者,同一组群和其他访问者,如777代表三者都有最高权限,754代表文件拥有者有最高权限,同一组群下有读和执行的权限,其他访问者只有读权限](https://blog.csdn.net/weixin_44979073/article/details/119907849)

# 计算机网络

[小林coding的计算机网络部分比较好,不太需要别的书了,别的内容质量次一级但是也能看](https://www.xiaolincoding.com/)

[断点上传,http1.1以上,在header-range里确定上传范围,返回码是206](https://www.cnblogs.com/OIMM/p/9144798.html)

# 数据库

## mysql

[小林coding,主要没找到更好的,别的书不适合八股学习,可以看尚硅谷的mysql补充一些没有的知识点](https://www.xiaolincoding.com/mysql/)

## mongo

## es

## redis

基础知识比如AOF和RDB,内存淘汰策略,主从问题等等看《redis设计与实现》这本书

### 大Key

[大Key发现](https://www.cnblogs.com/yqzc/p/12425533.html)

[大Key拆分](https://www.cnblogs.com/-wenli/p/13612364.html)

### 热Key

热key问题基本上是**本地缓存**+**热点发现**

### 其他

[bitmap原理,精准的低内存统计,了解下原理](https://www.cnblogs.com/cjsblog/p/11613708.html)

[hyperloglog,一种数据结构,可能存在误差率,但是内存消耗更低](https://www.cnblogs.com/yangmingxianshen/p/8180369.html)

[有赞日活UV统计的方式,使用了bitmap和hyperloglog](https://blog.csdn.net/crazymakercircle/article/details/130648646?spm=1001.2014.3001.5501)


## 时序数据库

[时序数据库,了解下即可](https://www.cnblogs.com/tianqing/p/7152940.html)

[时序数据库常用于互联网级的监控,tps特别高](https://www.cnblogs.com/badboy200800/p/10981052.html)

# 数据一致性

[redis和mysql的数据一致性,主要是后几种生产者消费模式,消息队列和订阅binlog的方式](https://blog.csdn.net/crazymakercircle/article/details/129295341?spm=1001.2014.3001.5501)

# 消息队列

消息队列主要使用的是kafka和rocketmq,kfk的吞吐率很高,所以比较适用于日志系统的吞吐;而rocketmq的消息类型更加丰富,并且可靠性更高,java写的支持二开,因此业务上的mq一般是rocketmq

[黑马的RocketMQ,先看第一章和第三章了解下RocketMQ的相关概念](https://www.bilibili.com/video/BV1L4411y7mn/?p=112&spm_id_from=333.999.top_right_bar_window_history.content.click&vd_source=1063dec5ba093fbbf0591f3c9003cee8)

[阿里云RocketMQ官方视频,先看前三章，后几章好像偏实际,暂时用不到](https://edu.aliyun.com/course/317045/lesson/18400)

[尚硅谷的kafka,看这个入门了解基本概念](https://www.bilibili.com/video/BV1a4411B7V9/?spm_id_from=333.999.0.0)

[解决消息积压的问题,并且阐述消息积压产生原因,但是这种采集应该使用时序数据库,解决方案并不完美](https://www.bilibili.com/video/BV1SS4y137ta/?spm_id_from=333.999.0.0)

[rocketMQ的文章,挺齐全的,没事看看查漏补缺](https://www.cnblogs.com/weifeng1463/p/12889300.html)

[rocketMq官方文档,不适合八股学习,适合实战的时候看看](https://rocketmq.apache.org/zh/docs/)


# 分布式

[基于消息服务的最终一致性,常用于订单等服务](https://www.bilibili.com/video/BV1TZ4y1B745?buvid=YE4559E184927B0E4BD6B8A33F52A67E195B&is_story_h5=false&mid=%2BNz3o2orolOxzz8cJezV0A%3D%3D&p=1&plat_id=114&share_from=ugc&share_medium=iphone&share_plat=ios&share_session_id=9AF25BB2-4021-4070-90C9-BBE1C3E35802&share_source=WEIXIN&share_tag=s_i&timestamp=1684240430&unique_k=nZutly7&up_id=386555201)

[raft和etcd]()

# 系统设计题

[B站的高并发点赞,无论是熟悉架构设计还是配合项目食用都挺好的](https://blog.csdn.net/crazymakercircle/article/details/129281202?spm=1001.2014.3001.5501)

## 短链系统

[设计一个高并发短链系统,比较侧重于QPS分析,采用离线密钥的方式来应对高并发](https://www.cnblogs.com/xxuuzz/p/16426250.html)

[采用本地生成的分布式ID,如雪花算法来应对高并发发号;重点掌握发号,储存,映射这三块问题](https://blog.csdn.net/crazymakercircle/article/details/128820168?ops_request_misc=&request_id=8ffd6256137e42bfaf3da9f4b5912cb0&biz_id=&utm_medium=distribute.pc_search_result.none-task-blog-2~blog~koosearch~default-1-128820168-null-null.268^v1^control&utm_term=%E7%9F%AD%E9%93%BE&spm=1018.2226.3001.4450)

# 三高架构设计

[基本回答的角度都在这里](https://blog.csdn.net/niulu90/article/details/117380378)

## 高可用

高可用架构从如下四点回答：
  
  ### 灾容
   
  需要知道的概念:
   
     1.同城双活(热备)
     
     2.两地三中心(热备+冷备)
     
     3.异地机房需要注意什么？
     
       3.1 业务尽量在同一个单元内(通信速度和业务需求),单元划分(根据地理和业务,体会下得物,高德,饿了么案例在机房单元划分的依据)
       
       3.2 异地多活切流过程
       
       3.3 智能DNS来选择机房,并且Api层检测是不是打到正确的机房,如果错误则切流
  
  [redis同城双活,比较偏向于实战](https://blog.csdn.net/u012171444/article/details/127525169)
  
  [得物异地多活,主要偏重于概念的理解,具体的mysql异地多活没怎么仔细看](https://www.cnblogs.com/crazymakercircle/p/17227789.html#autoid-h3-8-0-3)
  
  ### 缓存降级服务(多级缓存,保证服务一定可用)
  
  ### 副本数据延迟优化架构
  
  ### 降级服务,限流,熔断

# 云原生

[docker和k8s看阿里云公开课](https://edu.aliyun.com/course/314164/lesson/7781)
