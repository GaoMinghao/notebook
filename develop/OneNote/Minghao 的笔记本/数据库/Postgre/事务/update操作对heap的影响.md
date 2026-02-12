![Exported image](Exported%20image%2020260212171536-0.png)

可见，pg中更新时是直接在heap中加了一条新的tuple，老的tuple的xmax设为了非0，该tuple在未来的某一个时间会被vacuum机制回收