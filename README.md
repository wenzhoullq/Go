# 前言
主要看书为主,书本的话错误相对较少,但是得考虑书本的年代,比如go,版本太低的话很多东西太旧了

其次考虑看文章,博客园的文章质量相对于CSDN较高,可以通过博客园进行名词搜索;也可以考虑掘金社区的文章,CSDN的文章抄袭居多,因为量太大了,感觉质量差的文章很多,但是也有好的文章
# GO
## 公众号
刘丹冰 小徐先生的编程世界 go语言中文网 微服务实践 架构师尼恩(八股内容一般般,关于三高架构的文章质量比较高),[go梦工厂](https://mp.weixin.qq.com/mp/appmsgalbum?__biz=MzkyNzI1NzM5NQ==&action=getalbum&album_id=1932319304830517254&scene=173&from_msgid=2247484781&from_itemidx=1&count=3&nolastread=1#wechat_redirect)

[陈皓网站，质量挺高的](https://coolshell.cn/articles/21128.html)
## 无分类

[入门视频,用户入门和查漏补缺](https://www.bilibili.com/video/BV1EB4y1D7WW/?spm_id_from=333.788&vd_source=1063dec5ba093fbbf0591f3c9003cee8)

[Go语言底层原理剖析，必看且多看几遍,全且深,类似于Java里的Java核心卷1+深入理解JVM]()

[B站视频,涉及到汇编和指针,不适合0基础直接看,等有一定基础后再看](https://www.bilibili.com/video/BV1hv411x7we?p=1&vd_source=1063dec5ba093fbbf0591f3c9003cee8)

[Go语言设计与实现，涉及到汇编和机器码的知识点太多了,不适合0基础和面试食用](https://draveness.me/golang/docs/part2-foundation/ch05-keyword/golang-panic-recover/)

[for range的坑](https://mp.weixin.qq.com/s?__biz=MzkyNzI1NzM5NQ==&mid=2247484755&idx=1&sn=5e3f8405dc8244875614cc936fbfd601&source=41#wechat_redirect)

[sync.once的底层,互斥锁+aotomic包实现,主要是后者的三道面试题](https://mp.weixin.qq.com/s?__biz=MzkyNzI1NzM5NQ==&mid=2247484782&idx=1&sn=472e7ecef81a11f83abda18172ec53f5&chksm=c22b8332f55c0a2488a7e2e1dcd9d2bf3afb764b29e0733d6307e6f6d5d4fde8b550a4cc4e18&scene=178&cur_album_id=1932319304830517254#rd)

[go的伪汇编,cgo知识点等等介绍,感觉挺有意思的,可以看看](https://chai2010.cn/advanced-go-programming-book/index.html)

[go栈扩容](https://www.cnblogs.com/davygeek/p/9871256.html)

## unsafe

[unsafe包主要是unsafe.Pointer是一种万能指针,它能将安全的指针转化Pointer直接进行内存管理,也可以转为安全类型且别的类型的指针,同时可以转为uintptr进行偏移量的计算,最经典的应用是StringBuilder实现零拷贝](https://blog.csdn.net/Mazi1994/article/details/124864996)

[unsafe包的应用,零拷贝实现[]byte和string的转换](https://mp.weixin.qq.com/s?__biz=MzkyNzI1NzM5NQ==&mid=2247484941&idx=1&sn=326abc6706a092e36af32a5b682e6e3c&chksm=c22b8051f55c0947df20327d7993878f1086c5391ec5890ae78e17df2c7627bd4bf345010f9b&scene=178&cur_album_id=1932319304830517254#rd)

[atomic包的cas,乐观锁(无锁),通过unsafe包实现,同时go的cas是没有aba问题的](https://mp.weixin.qq.com/s?__biz=MzkyNzI1NzM5NQ==&mid=2247484781&idx=1&sn=dcd593f3fe1fa8fe75a18dbd53802dc8&source=41#wechat_redirect)
## Runtime
[只用看垃圾回收,内存管理,内存分配部分,其他部分太简略了没必要看,初级八股,面小厂够用了,面大厂可能会叼你说只知道八股](https://www.yuque.com/aceld/golang)

[GMP,主要是协程的7个状态以及它的小结,讲GMP先介绍它们的数据结构,比如g的结构体和Gfree,p是调度器以及最大并发数和plist(强调它是无锁队列,以前的方式是从全局队列里调用的时候是加锁的),m是内核线程,gmp三个结构体的映射关系,然后讲调度,从三个角度来讲,调度循环,调度策略和调度时机,调度循环是先讲g0是什么,再说g0->g->g的过程中间调用了schedule（调度策略）,exec(GP之间的绑定和解绑),gogo(操作系统里寄存器的指令),然后讲schedule是调度策略,p先看runext,如果没有则去看runq,如果还没有再去看全局队列,如果再没有再去看网络通信里,还没有则去stealing,stealing不到则自旋,自选后还没有就handoff;对于全局队列,为了防止饥饿,g执行一定次数后会去全局队列里调度;然后讲调度时机,和exec有关,分为主动调度,被动调度和抢占调度,主动调度是自己执行runtime.schedul,将runq和nextq放到全局队列里;被动调度指的是gc,M阻塞等等调用gopark,注意并不会把g放入全局队列,而是调用exec进行解绑;最后是抢占式调度,1.14版本之后解决gc的时候没有抢占的问题](https://zhuanlan.zhihu.com/p/502740833?utm_id=0)

[触发gc的时机](https://mp.weixin.qq.com/s/e2-NXWCS0bd2BPWzdeiS_A)

[协程和线程主要从内存空间,上下文切换以及创建和销毁]()

## map,chan,slice

### slice

切片的考点主要在于:切片的结构体,切片的扩容机制,切片底层共用数组,切片的值传递与函数

而go中的数组,如果声明了长度则是数组,如 s:=[3]int{1,2,3},作为函数的参数的时候需要声明数组的长度

```go
package main

import "fmt"

func deal(s []int) {//会报错
	//s = append(s, []int{1, 2}...)
	s[0] = 2
}

func main() {
	//s := make([]int, 10, 12)
	s := [3]int{1, 2, 3}
	deal(s)
	fmt.Println(s)
}

```

#### 切片的结构体

切片的结构体共有三个对象:分别是len,cap和slicehead;len是实际容量,cap是理论容量,如果不超过这个范围则不发生扩容,slicehead是指针,指向物理地址

#### 扩容机制

在切片的大小小于256的时候,是通过翻倍扩容

在切片的大小在256以上,通过容量的1/4不断进行扩容
 
#### 共用数组

对于s1 := s[2:] 之后,slicehead改变了,但是仍然共用数组

``` go
package main

import "fmt"

func main() {
	s := make([]int, 10, 12)

	//非共用数组
	s1 := s[8:]
	s1 = append(s1, []int{10, 11, 12}...)
	s1[1] = 1
	fmt.Println("非共用数组了")
	fmt.Println(s, s1)

	s2 := s[8:]
	s2 = append(s2, []int{10, 11}...)
	s2[1] = 1
	fmt.Println("共用数组了")
	fmt.Println(s, s2)
}
//执行结果

非共用数组了
[0 0 0 0 0 0 0 0 0 0] [0 1 10 11 12]
共用数组了
[0 0 0 0 0 0 0 0 0 1] [0 1 10 11]

```

#### 切片的值传递与函数

由于slicehead是指针,因此在传递的时候虽然是值传递（复制）,但是由于传递了指针,对于函数内的修改会影响函数外,但是对于函数内的扩容成一个新的slicehead则不影响函数外

``` go

package main

import "fmt"

func deal(s []int) {
	s[0] = 1
}

func main() {
	s := make([]int, 10, 12)
	deal(s)
	fmt.Println(s)
}
//[1 0 0 0 0 0 0 0 0 0]

```

参考资料:
[你真的了解go语言中的切片吗？](https://mp.weixin.qq.com/s/uNajVcWr4mZpof1eNemfmQ)

### map

map的主要考点在于map的数据结构,map中如何处理哈希碰撞以及它的哈希函数和map的扩容机制,map的无序和为何无序,

#### map的数据结构

map的对象是一个hmap指针,因此它也是引用类型的

其次它的桶数组,一共有B哥桶,取决于hash值的低B位

其余结构体成员看参考资料,感觉不是很重要

#### 扩容机制和哈希

在讲扩容机制前先讲map的哈希,处理hash碰撞的方式有两种:拉链法和开发寻址法,而map则将这两种都利用上了

开放寻址法体现在,如何函数映射到对应的B桶,则插入;如果此时发生哈希冲突,在该桶中临界下一个;如果在该桶的个数大于8的时候,则有溢出桶,即用拉链法的方式插入

map中分为等量扩容和增量扩容

等量扩容的原因取决溢出桶的个数大于map桶正常的个数,但是为什么会发生如此情况:在正常插入后,开放寻址法的个数满了,然后插入溢出桶,但是后续删除的时候将开放寻址法中的桶删除,因此正常的key的个数小于溢出桶的个数

增量扩容主要取决于键值对的个数/桶的个数 > 负载因子, 因此通过扩充桶的个数然后重hash实现的

#### map的无序

map的无序主要为了防止开发者在遍历的时候依赖于key的顺序,通过随机种子来决定从哪个桶开始

[Golang map 实现原理](https://mp.weixin.qq.com/s?__biz=MzkxMjQzMjA0OQ==&mid=2247483868&idx=1&sn=6e954af8e5e98ec0a9d9fc5c8ceb9072&chksm=c10c4f02f67bc614ff40a152a848508aa1631008eb5a600006c7552915d187179c08d4adf8d7&scene=178&cur_album_id=2709593649634033668#rd)



### chan

考点:1.csp 2.chan的数据结构 3.chan的不同状态的读和写

#### csp

在go中通过通信实现并发控制,即通过chan进行并发控制,这样容易解耦,但是通过chan编程容易写出死锁

#### 数据结构

chan的主要数据结构在于：

1.互斥锁,chan通过互斥锁实现并发

2.sendreq 发送队列,如果发送队列为空则阻塞

3.recvreq 接受队列,如果接受队列为空则阻塞

#### 不同状态的读写

思考逻辑在于,接收端是不会主动关闭队列的,因为它不知道chan还会不会被写入,所以在关闭状态下从chan获得值获得的时候都是默认值

对于发送端来说,因为你主动关闭的chan,因此你对一个关闭的队列写入会Panic

对于close来说,没有初始化过的chan和已经关闭的chan再次关闭会报错

[Golang Channel 实现原理](https://mp.weixin.qq.com/s/QgNndPgN1kqxWh-ijSofkw)

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


# 操作系统

## 虚拟内存/物理地址/虚拟地址

虚拟内存的考点:
	1.避免直接操作物理内存引发的错误,隔离不同的进程,保证安全性
        2.使程序无需考虑物理地址，直接操作虚拟地址
	3.程序的局部有限性,使得2G的物理内存可以有8G的虚拟内存(前提是操作系统支持swap)

## 进程的通信方式

1.管道 2.消息队列 3.信号量 4.信号 5.socket 6.共享内存

### 管道

管道分为匿名管道和命名管道, 即 | ,且单向

匿名管道只存在于父子进程之间的通信,命名管道可以在剩余的进程之间通信

### 消息队列

消息队列是以链表的形式进行传递,它无格式,因为涉及到队列的复制,因此速度比较慢

### 信号量

信号量是指PV操作

### 信号

信号是指比如 ctrl+c是退出,ctrl+z是挂起, kill -9 是指强制杀死等等

### socket

socket用于进程之间的通信,通过bind一系列进行绑定等等,最后指定IP+端口+协议

## 零拷贝

零拷贝关键点:1.DMA 和SG-DMA  2.sendfile 和 mmap  3. pagecatch  4.拷贝次数和上下文切换次数

### DMA/SG-DMA

DMA即内存直接访问技术,替代CPU进行从磁盘里读取数据至缓存区/将数据从socket缓冲区写入网卡,但是无法减少拷贝次数和上下文切换次数

SG-DMA 可以将内存直接拷贝至网卡

### MMAP和sendfile

MMAP内存映射技术,可以在用户态直接操作内存,减少一次上下文的切换

sendfile配合SG-DMA 可以不用将缓存区拷贝至socket缓冲区,直接将缓存区拷贝至网卡,减少一次拷贝

### pagecatch

因为程序局部性+内存的访问速度远大于磁盘IO,因此一次性多读取一些数据,这样可以减少一次拷贝

### 拷贝次数和上下文切换次数

原来的模式是 拷贝4次,上下文切换4次;零拷贝可以上下文切换2次,拷贝2次,极限情况可以只拷贝1次
 
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

[分布式协议与算法实战这本书很好,值得反复观看,资源在阿里云盘]()

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
