# 腾讯CSIG事业群后台开发 3+1hr面经【已offer】

https://blog.csdn.net/weixin_40992982/article/details/105205367?%3E

3.19 一面【将近2h】
1.自我介绍

2.判断链表是否有环，说思路

3.怎么找到环的入口，说完方法再说推导思路，给了5min让写推导公式。

4.说说怎么找链表的倒数第k个节点，要说最优解。

5.只用2GB内存在一个装有20亿个整数的文件中找到出现次数最多的数

6.只用2GB内存在一个装有20亿个整数的文件中找到出现次数topK的数

7.只用2GB内存在一个装有20亿个整数的文件中找到出现次数第topK的数

8.在40亿个非负整数中找到所有数的中位数

4-8具体的问题记不清了，反正不是让找中位数、就是和topk有关系的。

9.说说三次握手和四次挥手。

10.ping的原理

11.TCP的端口有多少个？为什么是65535？

12.一个场景题，简化一下就是在问请求一个万维网文档的所需的时间是多少？

2*RTT

13.为什么是2*RTT？请结合三次握手说一下。

一个RTT用于连接TCP连接，另一个RTT用于请求和接收万维网文档。要说出TCP建立连接的第三个报文段是可以携带数据的。

14.如果第三次握手没有携带数据的话，那么三次握手是多久？

1.5*RTT

15.索引的数据结构？为什么是B+树？

16.那来做三个题吧，

两个栈实现一个队列
机器人的最大运动范围
两个矩阵求交集
17.说说项目…

18.闲聊

3.24 二面【1h10min】
自我介绍

说说你熟悉的技术栈

说说ArrayList？自己叭叭了十分钟。

ArrayList的扩容为什么是1.5？为什么不能是2.5和3.5？这个1.5是怎么得来的？

ArrayList插入一个元素，平均复杂度是多少？为什么是O(1)?如果扩容的话复杂度是O(1)吗？为什么ArrayList随机访问速度快，你能说说嘛？

扩容的话应该是O(n)。
两个栈实现一个队列，那么push和pop的复杂度是多少？

入队的复杂度为O(1)，出队的复杂度则变为O(n)
ArrayList扩容机制是什么？扩容用到的什么方法？这个方法具体是怎么扩容的呢？你说它创建了一个新数组，在进行复制的时候复制的是引用还是值，深拷贝还是浅拷贝？

复制的地址，也就是引用，属于浅拷贝。
对象在JVM里怎么进行存储的？

从实例、引用和类型信息三个方面去回答。
三次握手和四次挥手？为什么四次？三次握手改成四次行不行呢，为什么？

说说拥塞控制和流量控制？拥塞控制的算法是啥，具体讲讲过程是怎样的呢？

ssthresh是动态变化的吗？你说是动态变化的，那具体怎么变化的，可以举个例子说一下吗？慢开始门限的初始值怎么计算？

ssthresh=max{size/2，2*SMSS}，size指的是已经发送但是还没有被确认的数据的字节数来设置，SMSS是发送方的最大报文段。
四次挥手的时候为什么要客户端先关闭连接啊？从状态转换上结合性能分析分析。

如果服务端主动关闭连接，那么服务端就会先发送fin，最后要有个2MSL的TIME-WAIT。如果服务端在一段时间内主动关闭的连接比较多，则服务端会有大量的TIME-WAIT状态的连接要等2MSL时间，在Windows下默认为4分钟。

当时回答的时候，面试官说你不要假设服务器端先关闭怎么怎么样，你就结合状态去分析就好。

后来我看TCP/IP协议卷1，发现服务器端先关闭的话，在2MSL阶段会占用熟知端口号，下一次在建立连接的时候，会报错，但是客户端的话，每次端口都是动态的。

服务器先关闭，客户端不关闭，继续发送数据，会出现什么情况？

触发四次挥手机制：

服务器：发出FIN,客户端回复ACK，进入TIME_WAIT状态
客户端：没有close(),处于close_wait()状态，
接着向服务器继续发送数据，会出现什么情况？

客户端：因为对方关闭（相当于管道中对方的读端关闭写端写满缓冲区就会触发SIGPIPE信号，操作系统会强制关闭写端），客户端继续写的话，会触发SIGPIPE信号，操作系统会强制关闭客户端。

进程内存结构，画个图给我看看？栈和堆是怎么增长的？低地址->高地址是从上到下还是从下到上？

栈是向下增长，堆是向上增长，上面是高地址，下面是低地址。 

大端小端？

股票的最大利润，说思路，然后写伪代码。

说说自认为做的最好的一个项目

面试官：建议你看看深入理解操作系统这本书，操作系统这方面还是有点薄弱的。下一面的面试官会更加严格哦，你要好好准备！

3.26 三面【40-50min】
自我介绍

看你熟悉Java，说一下单例模式吧，单例是安全的吗？说说安全和不安全的？

我：啊，这个单例模式是…

面试官：我的意思是你说说咋实现的…

我：它是主要是这样这样实现的…

面试官：那我问你单例是安全的吗？

我：当…时，它是安全的，当…时，它是不安全的。

面试官：那如果我想让他在懒加载的时候，保证安全，你说行不行？要是行，怎么做呢？

我：比如说我们加个锁，或者改造一下doublecheck模式，用volatile修饰instance。

知道Java中的注解吗？怎么实现的？注解底层是怎么工作的？

我只知道它们上面还有个Annotation接口，还知道怎么去自定义一个注解，具体的实现没怎么了解。

看你还会点数据库的知识，那么MySQL和MyISAM的区别？

什么情况下要考虑主从库呢？

主从复制的过程？主从复制涉及到的日志？你觉得是单线程还是多线程，为什么呢？

说说项目

围绕分布式、高可用的实际场景，出题考察
这里是一个个项目介绍一个个问的，特点就是刨根问底，回答完了问题，会问你为什么呢？
自闭了…
cap理论和base理论是个啥？你给我讲讲你对CAP的理解，顺便举举例子。

项目基本部署到哪个平台上？Linux是吧？那你说说常用的命令吧。

top命令显示400%啥意思呢？

2PC和3PC知道吗？

https的握手过程？啥时候是非对称加密，啥时候是对称加密？

一组数，排序，实现时间复杂度是O（n）？

提示你一下，你可以考虑我要给学生的成绩排序。我：（您这提示了我咋也不大会…），我想了一会说，那肯定普通的排序是不行的了，那我们可以开个数组，然后一趟遍历，出现的位置就+1，没出现就算了【这里我想起来之前看过的一道大数题，借鉴了一下思路】。这样到最后就知道了。面试官：那空间复杂度呢？我：O（n）。上网查了下好像说错了。。。空间复杂度应该是O（1）。

有一天风和日丽，你发现你们学校门口有几个报亭，你怎么推断一个城市有多少个报亭呢（面试官偷笑，欸嘿嘿，你们学校旁边有报亭嘛嘿嘿嘿我也不知道哈哈）？那你怎么快速知道有多少个报亭呢，比如说我要马上知道，你怎么做呢？

说说你的建模比赛，简单说说。怎么分工的呢？

职业规划？

你的老师和同学是怎么评价你的？

好啦，如果你没有什么问题的话，那我们到此结束吧…好吧，面试官再见。

3.27 hr面
hr：喂，是xx同学吗？我是tx的hr，之前有跟你约面试的，还记得吗？现在方便吗？
当然方便啦。【是个小哥哥哈哈哈哈

哎，我们约的几点来着？噢！不好意思，我给你打早了，哎呀我忘了其他同学了，我晚点再给你打过来…
？？？哈哈哈好的。

1.自我介绍
2.长期在深圳发展，家里人的看法？自己可以接受吗？
3.怎么去学一个新技术？
4.说说自己在项目/比赛当中的角色？
5.说说自己的经历？
6.手上的offer情况？
7.那我问你，如果阿里和腾讯都给你offer，你会选择谁呀？
8.实习的时间？
9.有没有考虑过毕业之后的发展方向呀？说说自己的职业规划？
10.对于实习之后是期望转正还是仅仅是实习呢？
11.平时怎么保证自己写代码的量呢？
12.目前对我们部门了解多少呢？说说你的看法吧~
13.offer肯定是会给你的，耐心等待1-2周。你有没有啥要问我的呢？