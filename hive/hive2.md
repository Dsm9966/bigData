## Hive
#### jdbc
* hiveserver2 将hive作为服务允许进行访问
* beeline 进行连接 ！connect jdbc://hive2://ip:端口(10000)
#### DDL操作
* 创建表

 ![image.png](https://upload-images.jianshu.io/upload_images/14466577-8445a330d0d7667b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
 * 内部表
 * ##### create table 表名（列名 类型，..）
 * ##### row format delimited fields terminated by '区分每一列的依据';
*  导入数据：
  * 从hdfs上导入数据：load data inpath 'hdfs上的文件路径' into table 表名;
  * 从本地上导入数据：load data local inpath '文件路径' into table 表名;
