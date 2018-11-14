## Hive
#### cli
#### jdbc
* hiveserver2 将hive作为服务允许进行访问
* beeline 进行连接 ！connect jdbc://hive2://ip:端口（10000）
*  导入数据：
  * 从hdfs上导入数据：load data inpath 'hdfs上的文件路径' into table 表名;
  * 从本地上导入数据：load data local inpath '文件路径' into table 表名;
