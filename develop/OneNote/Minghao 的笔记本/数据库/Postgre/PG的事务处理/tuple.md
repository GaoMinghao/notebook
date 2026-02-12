![HeapTupleHeaderData t xmin t xmax t cid 5.2 t_ctid...](Exported%20image%2020260212171517-0.png)   
t_xmin：插入此元组的事务 id  
t_xmax：删除或者更新此tuple 的事务 id，tuple有效时该值为0  
t_cid：(command id, cid)，cid 是指同一个事务中，执行当前命令前执行了多少条SQL命令  
t_ctid：指向自身或新元组的元组标识符，如果发生更新，该值指向新版本的元组，否则指向自己
 
一个实际的例子

![postgres begin postgres BEGIN 01 21 01 31 01 51 61...](Exported%20image%2020260212171519-1.png)  

删除：  
删除其实就是把 tuple 的 x_max 设置为删除事务的 id，此时 tuple 变成死元组，VACUMM 机制会负责将这个死元组清除掉。
 
更新：  
更新就是先删除旧的元组（处理流程与上面删除一致），再插入一条新的元组  
在同一个事务中，如果事务 commit，旧的元组就是死元组，如果事务 abort，新的元组就是死元组