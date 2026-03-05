![Exported image](Exported%20image%2020260212171715-0.png)  
![Exported image](Exported%20image%2020260212171718-1.png)  

1. sizeof 判断的是数据类型的大小， 编译期确定，所以sizeof(char*)实际上实在判断指针大小
2. strlen 判断的是具体数据的大小，运行期确定，但是最后的 '\0' 是不算的
3. struct 最后一个成员如果是不定长数组，不计算大小，同时不定长数组只能放在结构体最后，不然会报错
![Exported image](Exported%20image%2020260212171722-2.png)  
![Exported image](Exported%20image%2020260212171728-3.png)