# 前言

博客园的文章质量相对于CSDN较高,可以通过博客园进行名词搜索;也可以考虑掘金社区的文章,CSDN的文章抄袭居多,因为量太大了,感觉质量差的文章很多,但是也有好的文章
# GO
## 公众号
刘丹冰 小徐先生的编程世界 go语言中文网 微服务实践 架构师尼恩(八股内容一般般,关于三高架构的文章质量高)
## Runtime
[只用看垃圾回收,内存管理,内存分配部分,其他部分太简略了](https://www.yuque.com/aceld/golang)

## map,chan,slice
[slice](https://mp.weixin.qq.com/s/uNajVcWr4mZpof1eNemfmQ)

## socket编程
[socket编程基础知识](https://www.cnblogs.com/twoheads/p/10712094.html)

[net包](https://mp.weixin.qq.com/s/xt0Elppc_OaDFnTI_tW3hg)

[http包]()
# 计算机网络
[小林coding的计算机网络部分比较好,别的内容次一级但是也能看](https://www.xiaolincoding.com/)

# 数据库

## redis

[bitmap原理,精准的低内存统计,了解下原理](https://www.cnblogs.com/cjsblog/p/11613708.html)

[hyperloglog,一种数据结构,可能存在误差率,但是内存消耗更低](https://www.cnblogs.com/yangmingxianshen/p/8180369.html)

[有赞日活UV统计的方式](https://blog.csdn.net/crazymakercircle/article/details/130648646?spm=1001.2014.3001.5501)


## 时序数据库

[时序数据库,了解下即可](https://www.cnblogs.com/tianqing/p/7152940.html)

[时序数据库常用于互联网级的监控,tps特别高](https://www.cnblogs.com/badboy200800/p/10981052.html)

# 数据一致性

[redis和mysql的数据一致性,主要是后几种生产者消费模式,消息队列和订阅binlog的方式](https://blog.csdn.net/crazymakercircle/article/details/129295341?spm=1001.2014.3001.5501)

[基于消息服务的最终一致性,常用于订单等服务](https://www.bilibili.com/video/BV1TZ4y1B745?buvid=YE4559E184927B0E4BD6B8A33F52A67E195B&is_story_h5=false&mid=%2BNz3o2orolOxzz8cJezV0A%3D%3D&p=1&plat_id=114&share_from=ugc&share_medium=iphone&share_plat=ios&share_session_id=9AF25BB2-4021-4070-90C9-BBE1C3E35802&share_source=WEIXIN&share_tag=s_i&timestamp=1684240430&unique_k=nZutly7&up_id=386555201)

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


