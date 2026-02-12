![Exported image](Exported%20image%2020260212172113-0.png)

Iterator traits是用来给algorithm提供iterator的属性的，其中共包含五种属性

1. iterator_category： 例如是否是只能单向移动的 iterator 等等
2. Value type：node的类型
3. Difference_type: 两个 iterator 之间的距离的类型
4. Pointer:
5. Reference:
 
但是如果是指针类型的，是没有 category 和 difference_type 等属性的，但是 algorithm 还是会问的  
所以要用泛化的偏特化来解决

![Exported image](Exported%20image%2020260212172115-1.png)