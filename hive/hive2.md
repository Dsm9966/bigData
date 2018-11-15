## Hive
#### jdbc
##### hiveserver2 将hive作为服务允许进行访问
##### beeline 进行连接 ！connect jdbc://hive2://ip:端口(10000)
#### DDL操作
* 创建表

 ![image.png](https://upload-images.jianshu.io/upload_images/14466577-8445a330d0d7667b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
 
* 内部表
 
  ![image.png](https://upload-images.jianshu.io/upload_images/14466577-b30a14347c8a122d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
 
* 外部表
  
  ![image.png](https://upload-images.jianshu.io/upload_images/14466577-6bf8431764493534.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

   ##### 注意：location后面跟的是文件路径
   
   ![1.png](https://upload-images.jianshu.io/upload_images/14466577-d83fd422019e415d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
  
* 内部表和外部表的区别：
   ##### 外部表用于引用外部数据，也不希望对原始数据继续破坏，配合location来指定外部表要读取数据；
   #####  删除内部表或者清空会将数据真正删除；外部表只是将表关联信息删除掉，对指定位置内容没有影响
* 分区表
   ##### 相当于表中又分了小表，减少查询量，提升查询效率
   ##### 分区不是只能有一层的，可以创建多层
   ##### 创建好分区后，将数据导入要指定好对应分区
   
  ![image.png](https://upload-images.jianshu.io/upload_images/14466577-efff8cbd91813464.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
  
* 桶表 

  ![image.png](https://upload-images.jianshu.io/upload_images/14466577-957466c0eb594400.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
  
#### DDL操作

* 查询分区
   ##### show partitions 表名；
* 增加分区
   ##### alter table 表名 add partition(列名=‘ ’);
* 删除分区
   ##### alter table 表名 drop  partition(列名=‘ ’)；
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
#### DML 插入数据   
*  插入一条数据
   ##### insert into table 表名 values( , );
*  导入数据：
   ##### 从hdfs上导入数据：load data inpath 'hdfs上的文件路径' into table 表名;
   ##### 从本地上导入数据：load data local inpath '文件路径' into table 表名;
   ##### load相当于剪切，把文件复制到表中，原文件路径下不再存在
*  导出数据：
   ##### insert overwrite [local] directory '路径'
   ##### select * from 表； 
#### 动态分区
##### 使用场景：当我们想要对数据分区的时候，拿到的数据未必是已经分好区的，并不能直接load进来，这个时候使用动态分区来结果
 
  ![image.png](https://upload-images.jianshu.io/upload_images/14466577-c8b50706f3e5276b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
  * 步骤：
  * 1 将混乱数据传入一个表
  * 2 创建对应分区表
  * 3 向分区表动态分区的插入数据 
  * 3.1 如果要进行动态分区，就不要在partition(month)给分区设置固定值
  * 3.2 默认是严格模式，不允许使用动态分区的
  
   ![image.png](https://upload-images.jianshu.io/upload_images/14466577-f79d30bf4a1cefdd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
 
  * 3.3 使用动态分区会将查询结构集最后一个作为分区条件
  
* CTAS
##### create table...as select...)将hive的查询结果直接存入到一个表中
  
  ![image.png](https://upload-images.jianshu.io/upload_images/14466577-689a1d97223d6bd0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
   

 
 

   
