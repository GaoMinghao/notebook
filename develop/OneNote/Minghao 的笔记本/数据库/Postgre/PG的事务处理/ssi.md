**串行化隔离（****Serializable Isolation****）**: 这是最高的隔离级别，要求事务的执行结果必须等同于某种顺序的串行执行。传统上，串行化通过加锁来实现，但 PostgreSQL 使用了基于 MVCC 的 **SSI****（****Serializable Snapshot Isolation****）** 来实现更高效的串行化隔离。
 
严格的S2PL可以解决写偏序的问题，这是因为读写互斥，保证两个事务无法同时操作同一个对象，但是存在死锁的可能，如下图

![Exported image](Exported%20image%2020260212171533-0.png)

两个事务分别先读到 x,y 并各自添加读锁，然后再去【处理】另外一个对象时会进入锁等待
   

从概念上讲，存在三种类型的冲突：**写-读冲突（wr-conflicts）**（脏读），**写-写冲突（ww-conflicts）**（丢失更新），以及**读写冲突（rw-conflicts）**。 但是这里无需考虑写-读冲突与写-写冲突，因为如前所述，PostgreSQL可以防止此类冲突。 因此PostgreSQL中的SSI实现只需要考虑读-写冲突。