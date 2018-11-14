## Hive
#### jdbc
##### hiveserver2 将hive作为服务允许进行访问
##### beeline 进行连接 ！connect jdbc://hive2://ip:端口(10000)
#### DDL操作
*  导入数据：
   ##### 从hdfs上导入数据：load data inpath 'hdfs上的文件路径' into table 表名;
   ##### 从本地上导入数据：load data local inpath '文件路径' into table 表名;
   ##### load相当于剪切，把文件复制到表中，原文件路径下不再存在
* 创建表

 ![image.png](https://upload-images.jianshu.io/upload_images/14466577-8445a330d0d7667b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
 
* 内部表
   ##### create table 表名（列名 类型，..）
   ##### row format delimited fields terminated by '区分每一列的依据';
* 外部表
   ##### create external table 表名（列名 类型，..）
   ##### row format delimited fields terminated by '区分每一列的依据';
   #####  location  '文件夹路径';
* 内部表和外部表的区别：

* 分区表
   ##### create table 表名（列名 类型，..）
   ##### partitioned by (列名 类型，..)列名为分区依据
   ##### row format delimited fields terminated by '区分每一列的依据';
#### DDL操作
* 查询分区
   ##### show partitions 表名；
* 修改表名
   ##### alter table 表名 rename to 新名字；
* 增加修改/替换列
   ##### alter table 表名 add/replace columns(列名 类型)；
* 修改列名
   ##### alter table 表名 change 原列名 现列名 类型；  
* 删除表数据，保留结构
   ##### truncate table 表名；
* 删除表
   ##### drop table 表名；
   
