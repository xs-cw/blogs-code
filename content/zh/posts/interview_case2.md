---
title: "面试题2"
date: 2020-05-05T22:05:31+08:00
tags: [面试]
categories: [面试]
draft: false
---
## 单选题




1. 【2分】 在MySql中，如果要修改表的列名，下列语句的语法正确的是

```sql
AALTER TABLE 表名字 CHANGE 列名称 新列名称
BALTER TABLE 表名字 ALTER 列名称 新列名称
CALTER TABLE 表名字 MODIFY 列名称 新列名称
DALTER TABLE 表名字 列名称 新列名称
```

正确答案：A

2. 【2分】 数据库事务的特性不包括以下哪一项？

```
A原子性
B分区容错性
C一致性
D隔离性
```

正确答案：B

3. 【2分】 下列代码中三个变量x, y, z的内存位置分别是:

   ```c
      int <iostream>
      using namespace std;
      static int x = 0;
      void add(int e) { int y = 2 * e; x += y; }
      int main() {
         add(1);
         int *z = &x;
         cout << *z << endl;
         return 0;
      }
   ```

```
A数据段，栈，堆；
B栈，数据段，堆；
CBSS段，栈，栈；
D数据段，栈，栈;
```

正确答案：D

###### 参考答案：

x是被初始化的全局变量位于数据段，y位于栈中，z是指针变量，也位于栈中；

4. 【2分】 对任意实数c，从有N个无序元素的数组中寻找元素a、b，使得 a+b 的结果最接近c，最快的平均时间复杂度是

```
AO(N^2)
BO(log N)
CO(N)
DO(N^3)
EO(NLogN)
F不确定
```

正确答案：E

#### 参考答案：

2sum问题，稍微改了改让google直接搜不到

5. 【2分】 如果 22, 24, 26, 14, 16, 18, 46, 8, 10 是第二次排序后的结果，以下哪种排序算法可以满足？

```
A冒泡排序
B插入排序
C选择排序
D快速排序
```

正确答案：B

6. 【2分】以下情况对性能影响由大到小排列，最接近的选项是？
   A.分支预测失败 B.L1 Cache 失效
   C.IO等待 D.虚拟内存page miss



```
AA > B > C > D
BC > B > D > A
CD > A > C > B
DD > B > C > A
EA > C > D > B
FB > D > A > C
GC > D > B > A
```

正确答案：G

7. 【2分】 ctrl + c 会给前台进程组中的进程发送什么信号？

```
ASIGINT
BSIGTSTP
CSIGQUIT
DSIGTERM
```

正确答案：A

#### 参考答案：

Linux信号机制

8. 【2分】 在区间[-2, 2]里任取两个实数，它们的和>1的概率是：

```
A3/8
B3/16
C9/32
D9/64
```

正确答案：C

#### 参考答案：

作图可解

9. 【2分】 假设一共1000瓶酒，其中一瓶有毒。如果一只老鼠喝了有毒的酒，会在一天之后死亡，那么给你一天时间，需要你判定哪瓶酒有毒，至少需要几只老鼠？

```
A5
B10
C20
D100
E500
```

正确答案：B

10. 【2分】以下关于 linux 文件系统说法错误的是

```
A/proc是真实存在于磁盘上的目录
B/dev/null和/dev/zero是一个特殊的设备文件，并不会存在于磁盘上
C/sys是sysfs文件系统挂载的标准位置
Dcgroups系统通过读写文件与其交互
```

正确答案：A

11. 【2分】如果由于某些原因需要查看多进程运行时的所有系统调用，可以使用什么命令

```
Aptrace
Bstrace -f 
Cstrace 
Dptrace -f
```

正确答案：B

12. 【2分】已知字符串S为”abaabaabacacaabaabcc”，模式串t为”abaabc”。采用KMP算法进行匹配，第一次出现“失配”（s[i]!=t[j]）时，i=j=5，则下次开始匹配时，i和j的值分别是

```
Ai=1 j=0
Bi=5 j=0
Ci=5 j=2
Di=6 j=2
```

正确答案：C

13. 【2分】假设初始栈为空，在对中缀表达式 a/b+(c*d-e*f)/g 转化为后缀表达式的过程中，当扫描到 f 时，栈中元素依次是：

```
A+ ( * -    
B+ ( - *
C/ + ( * - *
D/ + - *
```

正确答案：B

14. 【2分】用哈希算法处理冲突时可能出现堆积现象，会受堆积直接影响的是：

```
A 储存效率
B散列函数
C装载因子
D平均查找长度
```

正确答案：D

15. 【2分】关于最小生成树的说法中，正确的是：

```
A最小生成树代价唯一
B所有权值最小的边一定会出现在所有最小生成树中
C使用Prim算法从不同顶点开始得到的最小生成树一定相同
D使用Prim算法与Kruskal算法得到的最小生成树总不相同
```

正确答案：A

16. 【2分】关于内存分配说法错误的是

```
A分页与分段都能达到地址隔离的效果
B硬件中的TLB，帮助操作系统快速从虚拟地址定位到物理地址
C如果TLB无法命中，则CPU或者操作系统会遍历分页表
D操作系统运行时，程序获取的变量的内存地址是真实的物理地址
```

正确答案：D

17. 【2分】关于 inode 以下说法错误的是

```
Ainode的数量是有限的
Binode信息中有一项叫做"链接数"，软链接会修改链接数
C不同名称的文件有可能对应相同的inode
D如果inode被使用完，则会导致无法创建文件
```

正确答案：B

18. 【2分】关于进程间通讯说法错误的是

```
A匿名管道只能用于父子进程间单向通讯
B 命名管道实际是创建了一个管道文件
C信号量只能用于父子进程间通讯与同步
Dsocket通讯可以跨主机通讯
```

正确答案：A

19. 【2分】关于 linux 中进程状态叙述错误的是

```
A处于D（TASK_UNINTERRUPTIBLE）状态的进程在状态改变前不能接受任何信号，也无法被强制退出
B处于Z（EXIT_ZOMBIE）状态的进程产生的原因是因为其父进程未收集其退出状态
C处于R（TASK_RUNNING）状态的进程不可能处于就绪状态
D处于S（TASK_INTERRUPTIBLE）状态的进程可能是正在等待IO事件
```

正确答案：C

20.【2分】linux 中如果希望让内核跟踪数据包在iptables内的处理过程，可以在哪个表中加入相关规则

```
Araw
Bnat
Cfilter
Dmangle 
```

正确答案：A

21. 【2分】关于 HTTP 协议说法中错误的是

```
AHTTP协议是无状态协议
BHTTP/1.0中已经支持KeepAlive
CHTTP/2协议支持多路复用与首部压缩
DHTTP/3将会使用UDP来传输数据
```

正确答案：B

22. 【2分】关于路由跟踪错误的是（请考虑任意平台中任意可用于做路由跟踪的软件）

```
ATCP与UDP协议也可用来做路由跟踪
B如果使用ICMP协议做路由跟踪，需要指定目目标端口
Clinux下做路由跟踪的软件包括traceroute和mtr 
D如果使用TCP协议做路由跟踪，目标主机不一定能有回应
```

正确答案：B

23. 【2分】关于 TCP 连接中拥塞控制中，正确的是

```
A拥塞窗口的大小，在首次出现丢包时一直是指数增长
B 快重传输算法中，如果发送方收到三个重复确认就应当立即重传对方尚未收到的报文段
C快重传算法触发后，快恢复不一定触发
D快重传算法触发后，慢启动阈值根据原慢启动阈值进行改变
```

正确答案：B

24. 【2分】下列关于 http 状态码描述正确的是（）

```
A404读取浏览器缓存，502错误网关
B404找不到资源，403服务器错误
C500服务器错误，304读取浏览器缓存
D304服务器错误，200请求成功
E500找不到资源，200请求成功
```

正确答案：C

25. 【2分】![img](https://uploadfiles.nowcoder.com/images/20161128/5918115_1480305264548_D7D3C8CC72BCD7C6F4E46095FAA5BD6D)

以上 javascript 代码，在浏览器中运行的结果是

```
A1 2 3
Bundefined 2 1
C报错
D1 2 1
```

正确答案：A



## 不定项选择题

1. 【3分】一台动态获取IP的服务器，开机后联网完成自动检查系统更新的过程中，可能用到的协议是？

```
A
DHCP
B
DNS
C
NTP
D
ARP
E
ICMP
F
BGP
G
TCP
```

正确答案：A、B、C、D、G

2. 【3分】 下列关于网络编程正确的是

```
A
TCP主动关闭的一端会出现 TIME_WAIT状态
B服务端编程会调用 listen(),客户端也可以调用 bind()
C
TCP 建立和关闭连接都只需要1.5个RTT
DLinux 通过提供提供 socket 接口来进行网络编程
E长连接相对短连接可以节省建立连接的时间
F
UDP传输有简单的流控制
```

正确答案：A、B、D、E

3. 【3分】 下列正则表达式不能匹配”[www.innotechx.com](http://www.innotechx.com/)”的是：

```
A^w+.w+.w+$
B[w]{0,3}.[a-z]*.[a-z]+
C^w.*com$
D[w]{3}.[a-z]{11}.[a-z]
```

正确答案：A、D

4. 【3分】 以下有关Http协议的描述中，正确的有？

```
Apost请求一般用于修改服务器上的资源，对发送的消息数据量没有限制，通过表单方式提交
BHTTP返回码302表示永久重定向，需要重新URI
C可以通过206返回码实现断点续传
DHTTP1.1实现了持久连接和管线化操作以及主动通知功能，相比http1.0有大福性能提升
```

正确答案：A、C、D

5. 【3分】在掩码为 255.255.224.0 条件下，下面哪些 ip 地址属于同一网段（）

```
A192.168.235.25
B192.168.188.99
C192.168.246.187
D192.168.67.28
```

正确答案：A、C

## 问答题

1. 【5分】以下这段代码是否存在问题？如有请纠正，并指出问题如没有，则程序的输出是？
```go
func main() {
	var wg sync.WaitGroup
	wg.Add(5)
	for i := 0; i < 5; i++ {
		go func() { fmt.Print(i)
			wg.Done() }()
	}
	wg.Wait()
	fmt.Println()
}
```

2. 【20分】
设计一个工具，可以监控任意长度的网站列表的存活状态，并输出相关信息。
要求：
    1.使用golang实现。
    2.数据每次刷新后控制台都必须输出新数据数据刷新时间间隔、监控网站列表必须可以热重载
    3.如有关字段数据无法获取，可直接返回nil或显示"nil"访问监控站点时，status code为20x即可判断为存活，其他为死亡。（遇到跳转需要跟随跳转）
    4.IP不要求能获取到源站IP，CDN IP也符合要求
    5.相关API示例:
    1.IP Geolocation: https://ipwhois.io/documentation, https://ipapi.co/#api
    2.Weather: https://www.metaweather.com/api/
运行：`./m <configuration file>`

控制台输出:

```
Data refresh interval: 60s 

Website          IP            Country   Region    City  Temperature WeatherState Request Cost Time Status
www.youtube.com 172.217.160.78 Singapore Singapore Singapore 29.71   Heavy Rain      1.5s     (Alive/Dead)


Data refresh at: 1970-01-01 00:00:00
Data refresh cost time: 0.001s
============================================================
http请求输出：curl http://xx:yy/zz | python -m json.tool
{
    "data": [
        {
            "website": "www.youtube.com",
            "ip": "172.217.160.78",
            "country": "Singapore",
            "region": "Central Singapore",
            "city": "Singapore",
            "temperature": 29.71,
            "weatherState": "Heavy Rain",
            "requestCostTime": 1.5,
            "alive": true
        }
    ],
    "dataRefreshInterval": 60,
    "lastRefreshAt": "1970-01-01 00:00:00"
}
```

## 编程题

1. ACM编程题 【10分】 标题：整数与IP地址间的转换 | 时间限制：1秒 | 内存限制：32768K原理：ip地址的每段可以看成是一个0-255的整数，把每段拆分成一个二进制形式组合起来，然后把这个二进制数转变成一个长整数。
   举例：一个ip地址为10.0.3.193
   每段数字       相对应的二进制数
   10          00001010
   0          00000000
   3          00000011
   193         11000001
   组合起来即为：00001010 00000000 00000011 11000001,转换为10进制数就是：167773121，即该IP地址转换后的数字就是它了。 每段可以看成是一个0-255的整数，需要对IP地址进行校验  

   **输入描述:**

   > 输入 
   >
   > 1 输入IP地址
   >
   > 2 输入10进制型的IP地址
   

**输出描述:**
   > 输出
   > 1 输出转换成10进制的IP地址
   > 2 输出转换后的IP地址
    **示例1**
   > 输入10.0.3.193 167969729 
   > 输出167773121 10.3.3.193
