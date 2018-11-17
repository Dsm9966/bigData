## Hive
#### jdbc
#### hiveserver2 将hive作为服务允许进行访问
#### beeline 进行连接 ！connect jdbc://hive2://ip:端口(10000)
#### DDL操作
* 创建表

 ![image.png](https://upload-images.jianshu.io/upload_images/14466577-8445a330d0d7667b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
 
* 内部表
 
  ![image.png](https://upload-images.jianshu.io/upload_images/14466577-b30a14347c8a122d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
 
* 外部表
  
  ![image.png](https://upload-images.jianshu.io/upload_images/14466577-6bf8431764493534.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

  * 注意：location后面跟的是文件路径
   
   ![1.png](https://upload-images.jianshu.io/upload_images/14466577-d83fd422019e415d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
  
* 内部表和外部表的区别：
  * 外部表用于引用外部数据，也不希望对原始数据继续破坏，配合location来指定外部表要读取数据；
  * 删除内部表或者清空会将数据真正删除；外部表只是将表关联信息删除掉，对指定位置内容没有影响
* 分区表
  * 相当于表中又分了小表，减少查询量，提升查询效率
  *  分区不是只能有一层的，可以创建多层
  * 创建好分区后，将数据导入要指定好对应分区
   
  ![image.png](https://upload-images.jianshu.io/upload_images/14466577-efff8cbd91813464.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
  
* 桶表 

  ![image.png](https://upload-images.jianshu.io/upload_images/14466577-957466c0eb594400.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
  
  *  当向桶表添加数据时，会出现的情况：
  
  ![1.png](https://upload-images.jianshu.io/upload_images/14466577-65aa3cd424724eed.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
  
  *  设置允许分桶（只对当前对话有效）
  *  set hive.enforce.bucketing=true;
  *  设置分区后：
  
  ![2.png](https://upload-images.jianshu.io/upload_images/14466577-b0df533c5dffdf08.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
   
####  DDL操作

 * 查询分区
 * show partitions;
 * 增加/删除分区
  
   ![image.png](https://upload-images.jianshu.io/upload_images/14466577-33ff9e58fd01f155.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
  
   ![image.png](https://upload-images.jianshu.io/upload_images/14466577-8800948b28fd028f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

 * 修改表名

   ![image.png](https://upload-images.jianshu.io/upload_images/14466577-d29a1673e998cfd0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

 * 增加/修改/替换列

   ![image.png](https://upload-images.jianshu.io/upload_images/14466577-abe9851a9ac0f5fd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
  
   ![image.png](https://upload-images.jianshu.io/upload_images/14466577-47f5a37a3fb9dbc0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
  
   ![image.png](https://upload-images.jianshu.io/upload_images/14466577-69958d109089758e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 删除表数据，保留结构

  * truncate table 表名；

* 删除表
 
  * drop table 表名；

####  DML操作 
 *  插入一条数据
   * insert into table 表名 values( , );
 *  导入数据：
   * 从hdfs上导入数据：load data inpath 'hdfs上的文件路径' into table 表名;
   * 从本地上导入数据：load data local inpath '文件路径' into table 表名;
   * load相当于剪切，把文件复制到表中，原文件路径下不再存在
 * 导出数据：
   * insert overwrite [local] directory '路径'
   * select * from 表； 
 * 动态分区
   * 使用场景：当我们想要对数据分区的时候，拿到的数据未必是已经分好区的，并不能直接load进来，这个时候使用动态分区来结果
 
  ![image.png](https://upload-images.jianshu.io/upload_images/14466577-c8b50706f3e5276b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
  
   * 步骤：
    * 1 将混乱数据传入一个表
    * 2 创建对应分区表
    * 3 向分区表动态分区的插入数据 
    * 3.1 如果要进行动态分区，就不要在partition(month)给分区设置固定值
    * 3.2 默认是严格模式，不允许使用动态分区的
    * 3.3 使用动态分区会将查询结构集最后一个作为分区条件
   ![image.png](https://upload-images.jianshu.io/upload_images/14466577-f79d30bf4a1cefdd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
 
   
  
* CTAS
 * create table...as select...)将hive的查询结果直接存入到一个表中
  
  ![image.png](https://upload-images.jianshu.io/upload_images/14466577-689a1d97223d6bd0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
   

 
 

   
