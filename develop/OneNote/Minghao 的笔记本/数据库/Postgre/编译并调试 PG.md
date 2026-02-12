1. GitHub下载源码
2. 在顶层 ./configure CFLAGS="-O0" --prefix=/Users/mh/Develop/postgres/opt --with-pgport=5432 --enable-debug
3. Make
4. Make install
5. 初始DB：/Users/mh/Develop/postgres/opt/bin/initdb -D /Users/mh/Develop/postgres/opt/data/
6. 启动：/Users/mh/Develop/postgres/opt/bin/pg_ctl -D /Users/mh/Develop/postgres/opt/data/ -l logfile start
   

参考资料：https://blog.csdn.net/qq_34479012/article/details/123603729