1. List

环形双向链表

![Exported image](Exported%20image%2020260212171742-0.png)
 
1. Vector

连续空间，每次2倍增长，iterator指针

![Exported image](Exported%20image%2020260212171750-1.png)4. Array

中间包了一段类似 int[] 这样的结构体，就是  

![Exported image](Exported%20image%2020260212171754-2.png)  

类似这样，蛮神奇的写法

![Exported image](Exported%20image%2020260212171758-3.png)  
![Exported image](Exported%20image%2020260212171802-4.png)12. Forward list 线性单项链表
![Exported image](Exported%20image%2020260212171807-5.png)14. Deque

分段存储

![Exported image](Exported%20image%2020260212171809-6.png)17. Queue/Stack

Queue/Stack不算容器，算adapter，内部默认是dequeue，但是gnu4.9版本，stack的内部默认容器可以设置为vector
 20. Set/map

内部实现都是一个红黑树  
set不允许改key，是通过 iterator 是一个 ==const iterator==，map不允许改key，是通过==map====的====key==是 const

22. Hashmap

采用拉链法处理元素碰撞，当某一个bucket中链表的长度大于哈希表的长度时，则将哈希表拉长，长度变成x2之后附近的素数：例如：53x2 = 106 -\> 97
   

[https://mp.weixin.qq.com/s?__biz=MzkxNzQzNDM2Ng==&mid=2247493110&idx=1&sn=5d91da2eef3678c54a3cb7bcd6e4d67b&source=41#wechat_redirect](https://mp.weixin.qq.com/s?__biz=MzkxNzQzNDM2Ng==&mid=2247493110&idx=1&sn=5d91da2eef3678c54a3cb7bcd6e4d67b&source=41#wechat_redirect)
 
QA

29. Vector resize 和 reverse 的区别

**总结：**
 
• **reserve()**：只增加 vector 的容量，不改变元素数量，主要用于优化内存分配。  
• **resize()**：同时改变 vector 的容量和大小，增加或减少元素数量，并对新元素进行初始化或删除超出的元素。
 
两者的核心区别在于：
 
• reserve() 是关于**容量管理**，它不会影响元素数量，只是预留内存。  
• resize() 是关于**大小管理**，它改变了 vector 的大小，并且可能导致元素的增加或删除。

37. Emplace_back 和 push_back 有什么区别

Emplace_back 是在最末尾原地创建一个，接口的参数用于直接创建，中间不包含拷贝的操作，push_back 需要把原值拷贝