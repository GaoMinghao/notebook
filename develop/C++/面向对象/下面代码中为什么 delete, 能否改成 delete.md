1. 下面代码中为什么 delete[], 能否改成 delete

![Exported image](Exported%20image%2020260212172227-0.png)  

不能，delete[] 可以提示编译器需要删除的是数组，数组中的每个元素都会被调用析构函数，如果改成 delete，则只会调用一次析构函数