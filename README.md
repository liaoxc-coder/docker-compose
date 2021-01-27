# docker-compose
使用docker-compose 1.27.4版本实现MySQL读写分离
启动服务，使用指令 docker-compose up -d 启动服务并使服务在后台运行。

通过访问宿主机的 8066 端口使用数据库服务，查询数据，并插入一条数据。由于
mycat 假定在生产环境中均处于内网，因此不支持 mysql 8 客户端默认加密登录方
式，需要添加参数--default-auth=mysql_native_password，方可登录，访问宿主机的9066端口也是一样。

mysql --default-auth=mysql_native_password -uroot -p123456 -P8066 -h127.0.0.1
mysql --default-auth=mysql_native_password -uroot -p123456 -P9066 -h127.0.0.1 -e "show @@datasource" 
