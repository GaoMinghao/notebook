1. Iterator++ 目的应该是跑到下一个 iterator，但是在 list 的实现中，不同的 iterator 之间是用 next 链表相连的，这种情况就需要重载 ++
2. ++ 存在前++与后++，比方说 i++/++i
![Exported image](Exported%20image%2020260212171846-0.png)

直接从定义上进行区分，重载时有无参数，有参数的就是后++，即i++
 
2.1 为什么postsfix的格式中，*this 没有调用操作符重载*  
因为编译器会先处理 self tmp = *this，其中的 = 会调用拷贝构造函数，所以 *this 会被解释为 const interator& x 类型，所以不会调用被重载的 *
 
2.2 观察上面代码，可以发现前++的返回值类型是reference，后++的返回值类型是对象，为什么？  
为了模仿integer对于后加加的操作  
i(++)(++) 这种写法 C++是不允许的  
(++)(++)i 这种写法 C++是允许的、  
integer 确实是这样的，但是如果是list iterator 其实是可以的

![Exported image](Exported%20image%2020260212171851-1.png)

这么写编译器会告警，但是并不会直接报 error  
我认为一个合适的解释是，pos++返回的是对原值的拷贝，

![Exported image](Exported%20image%2020260212171855-2.png)

看代码可知 __tmp 是个栈变量，如果返回对 __tmp 的引用的话，当这个函数出栈之后，这个指针（引用实际上是靠指针实现的）就会悬空了，这是fatal的error