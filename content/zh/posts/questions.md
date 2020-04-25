---
title: "Questions"
date: 2020-04-07T10:42:49+08:00
tags: [question]
categories: [question]
draft: false
---

1. ### 乐观锁悲观锁

   - https://juejin.im/post/5b4977ae5188251b146b2fc8

2. ### docker相关

   - docker实现原理:linux namespace技术

   - https://blog.csdn.net/lixiao0320/article/details/94348042

3. ### redis数据结构

   - 数据结构有:
   
       | 类型常量     | 对象的名称 | 编码格式                                        |
       | ------------ | ---------- | ----------------------------------------------- |
       | REDIS_STRING | 字符串     | int、raw或者embstr                              |
       | REDIS_LIST   | 列表       | ziplist或者linkedlist                           |
       | REDIS_HASH   | 哈希       | ziplist或者hashtable(hashtable是由dict结构实现) |
       | REDIS_SET    | 集合       | intset或者hashtable                             |
       | REDIS_ZSET   | 有序集合   | ziplist，或者是skiplist与dict结合体             |
   - 底层实现
     https://blog.csdn.net/wcf373722432/article/details/78678504

4. ### redis为什么比mysql快

   - redis存储在内存中,mysql磁盘
   - redis使用K-V存储,mysql使用B+tree 

5. ### 消息队列

   

6. ### 微服务

   - 服务发现

     go-micro,consul工具; zookeeper,k8s

   - 负载均衡

   - https://blog.csdn.net/yang731227/article/details/90637535

7. ### 微服务有什么优点？
   - 解耦——系统中的服务在很大程度上是解耦的。因此，整个应用程序可以很容易地构建、修改和伸缩
   - 组件化——微服务被视为独立的组件，可以很容易地替换和升级
   - 业务功能——微服务非常简单，只关注一个功能
   - 自治——开发人员和团队可以彼此独立工作，从而提高速度
   - 持续交付——通过软件创建、测试和批准的系统自动化，允许频繁地发布软件
   - 责任——微服务不关注应用程序作为项目。相反，他们将应用程序视为自己负责的产品
   - 分散治理——重点是为正确的工作使用正确的工具。这意味着没有标准化的模式或任何技术模式。开发人员可以自由选择最有用的工具来解决他们的问题
   - 敏捷——微服务支持敏捷开发。任何新特性都可以快速开发并再次丢弃

8. ### redis缓存数据一致性

   - https://blog.csdn.net/koli6678/article/details/88202245

9. ### redis 缓存穿透

   - 不存在的结果也进行缓存,或者采用布隆过滤拦截不存在结果的请求

10. ### 缓存雪崩

   - 加锁或者使用队列约束请求
   - 过期时间设置一个随机偏量,避免同时失效

11. ### 缓存击穿
    | 方案                         | 优点                                                   | 缺点                                                         |
    | ---------------------------- | ------------------------------------------------------ | :----------------------------------------------------------- |
    | 简单分布式互斥锁（mutex key) | 1. 思路简单  2. 保证一致性                             | 1.代码复杂度增大  2.存在死锁的风险  3. 存在线程池阻塞的风险  |
    | “提前”使用互斥锁             | 1. 保证一致性                                          | 同上                                                         |
    | "永不过期"                   | 1. 异步构建缓存，不会阻塞线程池                        | 1. 不保证一致性。2. 代码复杂度增大(每个value都要维护一个timekey)。 3. 占用一定的内存空间(每个value都要维护一个timekey) |
    | netflix资源隔离组件hystrix   | 1. hystrix技术成熟，有效保证后端。2. hystrix监控强大。 | 1. 部分访问存在降级策略。                                    |

12. ### channel 底层实现线程安全

    - 加锁
    - 关闭通道时会广播到所有

13. ### sync map 区别

    - 加锁
    - 适合大量读,小量写
    - tips:第三方优化的 [concurrent-map](https://github.com/orcaman/concurrent-map)(想一想，mysql加锁，是不是有表级锁、行级锁，前文的sync.RWMutex加锁方式相当于表级锁。
    而sync.Map其实也是相当于表级锁，只不过多读写分了两个map，本质还是一样的。
    既然这样，那就自然知道优化方向了：就是把锁的粒度尽可能降低来提高运行速度。
    思路：对一个大map进行hash，其内部是n个小map，根据key来来hash确定在具体的那个小map中，这样加锁的粒度就变成1/n了。
    网上找了下，真有大佬实现了)

14. ### context 超时

    - 

15. ### 登录过程修改角色

    - session消息

16. ### token与jwt比较 

17. ### 登录持久化

    - 登录信息加密写入cookie
    - oatht2 验证

18. ### go的前期版本bug

19. ### go 相关问题

    - [go面试题](https://talkgo.org/interview/interview-golang-language/)

    - [nil的相关理解](https://studygolang.com/articles/11535) [PLAY](https://play.yeyuqiu.com/p/3UV3wfPWoim)

      ```go
      
      package main
      import (
          "fmt"
          "unsafe"
      )
      func main() {
      // nil的零值
      // nil没有默认的类型，尽管它是多个类型的零值，必须显式或隐式指定每个nil用法的明确类型
          // 明确.
          _ = (*struct{})(nil)
          _ = []int(nil)
          _ = map[int]bool(nil)
          _ = chan string(nil)
          _ = (func())(nil)
          _ = interface{}(nil)
      
          // 隐式.
          var _ *struct{} = nil
          var _ []int = nil
          var _ map[int]bool = nil
          var _ chan string = nil
          var _ func() = nil
          var _ interface{} = nil
          
      // nil的类型
      // nil类型的所有值的内存布局始终相同,换一句话说就是：不同类型nil的内存地址是一样的。
          var m map[int]string
          var ptr *int
          var sl []int
          fmt.Printf("%p\n", m)       //0x0
          fmt.Printf("%p\n", ptr )    //0x0
          fmt.Printf("%p\n", sl )     //0x0
      // nil值的大小始终与其类型与nil值相同的non-nil值大小相同。因此, 表示不同零值的nil标识符可能具有不同的大小。
          // 以下打印结果为64位体系
          var p *struct{} = nil
          fmt.Println( unsafe.Sizeof( p ) ) // 8
          var s []int = nil
          fmt.Println( unsafe.Sizeof( s ) ) // 24
          var m map[int]bool = nil
          fmt.Println( unsafe.Sizeof( m ) ) // 8
          var c chan string = nil
          fmt.Println( unsafe.Sizeof( c ) ) // 8
          var f func() = nil
          fmt.Println( unsafe.Sizeof( f ) ) // 8
          var i interface{} = nil
          fmt.Println( unsafe.Sizeof( i ) ) // 16
      // nil 值比较
          // 1.不同类型的nil是不能比较的
          var m map[int]string
          var ptr *int
          fmt.Printf(m == ptr) //invalid operation: m == ptr (mismatched types map[int]string and *int)
          // 2.有两个情形例外: 两个值之一的类型是另一个的基础类型。
                 //两个值之一的类型实现了另一个值的类型 (必须是接口类型)。
          type IntPtr *int
          fmt.Println(IntPtr(nil) == (*int)(nil))            //true
          fmt.Println((interface{})(nil) == (*int)(nil))    //false
          
      }
      ```

      

    - 

20. ### go框架 路由

21. ### 订单高并发  超卖

    - 超卖问题

       https://juejin.im/post/5dbeb66f51882524a33b9135
    - 超时实现

      轮询数据库,时间轮,redis ,消息队列

22. ### ws连接数过高

23. ### k8s

24. ### 最近项目

25. ### 常见排序时间复杂度


26. ### mysql 

    - 事务隔离

    - 慢查询

    - 索引优化 索引的数据结构

      https://cloud.tencent.com/developer/news/362898

    - filesort

      不能使用索引排序时,会使用文件排序,比较慢的外部查询,尽量避免

    - B+tree

      [为什么mysql使用B+树](https://www.cnblogs.com/tiancai/p/9024351.html)

27. ### Mongodb 

    - mongodb索引

      通常采用类似btree的结构持久化存储，以保证从索引里快速`O(logN)的时间复杂度`

      MongoDB支持多种类型的索引，包括单字段索引、复合索引、多key索引、文本索引等，每种类型的索引有不同的使用场合

28. ### 求数组中两数字之和为指定数字

    - 双循环遍历

    - 字典法: 将差值作为key,下标作为value,遍历数组查询

      ```go
      	for i, v := range nums {
      		if index, ok := m[v]; ok {
      			return index, i
      		}
      		m[N-v] = i
      	}
      ```

29. ### 踩过的坑

    - for range 数组长度固定,range到的值会有一次复制过程
    - sync.Pool 被gc会被直接回收掉，所以不适合存放有状态的内容，只适合状态无关的临时数据,gin框架中存储context对象

30. ### Linux
    - select、poll、epoll 的区别[详见Linux IO模式](https://segmentfault.com/a/1190000003063859)
       - **select** 有数量限制,可以通过宏修改,但是性能会更低
       
       - **poll** 没有数量限制,监控文件数过多也会性能变低
         
           > select和poll都需要在返回后，`通过遍历文件描述符来获取已经就绪的socket`。事实上，同时连 接的大量客户端在一时刻可能只有很少的处于就绪状态，因此随着监视的描述符数量的增长，其效率也会线性下降
           
       - **epoll** 增强版的select和poll,更灵活,使用一个文件描述符管理多个描述符，将用户关系的文件描述符的事件存放到内核的一个事件表中，这样在用户空间和内核空间的copy只需一次。
       
           操作过程需要如下三个接口:
       
           ```c
           int epoll_create(int size)；//创建一个epoll的句柄，size用来告诉内核这个监听的数目一共有多大,只是一个建议值
           int epoll_ctl(int epfd, int op, int fd, struct epoll_event *event)；
           int epoll_wait(int epfd, struct epoll_event *events, int maxevents, int timeout);
           ```
       
           epoll工作模式: **LT(level trigger)** ,**ET(edge trigger)**
       
           - **LT模式**(默认)：当epoll_wait检测到描述符事件发生并将此事件通知应用程序，`应用程序可以不立即处理该事件`。下次调用epoll_wait时，会再次响应应用程序并通知此事件。`同时支持block和no-block socket`
           - **ET模式**(高性能)：当epoll_wait检测到描述符事件发生并将此事件通知应用程序，`应用程序必须立即处理该事件`。如果不处理，下次调用epoll_wait时，不会再次响应应用程序并通知此事件。`只支持no-block socket`

31. ### 其他问题

    - mysql 隔离级别 

      https://www.cnblogs.com/jian-gao/p/10795407.html 

      **Mysql的四种隔离级别**

      - **Read Uncommitted（读取未提交内容）**

      - **Read Committed（读取提交内容）**

      - **Repeatable Read（可重读）**(数据库默认级别)

      - **Serializable（可串行化）**
      - ![img](https://img2018.cnblogs.com/blog/1646034/201904/1646034-20190430095830286-1397235000.png)

    - mvcc 聚集索引和非聚集索引的结构

    - redis 底层模型 多路复用  

    - tcp/ip
      
    - http2和http1的区别
      
    - 分布式事务 分布式锁
      
    - 一致性哈希
      
    - ConcurrentHashMap的看法
      
    - docker 网络模式 隔离级别
    
      - Bridge contauner 桥接式
      - Host(open) container 开放式
      - Container(join) container 联合挂载式，是host模式的延伸
      - None(Close) container 封闭式网络模式
