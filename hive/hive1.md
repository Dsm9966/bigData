## Hive
#### 1.具有SQl数据库外表，只适合用来做批量海量数据统计分析
#### 2.基于hadoop的一个数据仓库工具，实质上就是基于HDFS的MapReduce计算框架

  ![image.png](https://upload-images.jianshu.io/upload_images/14466577-4445e2009304087a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 特点：

  ![image.png](https://upload-images.jianshu.io/upload_images/14466577-3f2ad10cae9c5562.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

  * cli:终端命令行
  * JDBC:基于JDBC操作提供的客户端，用户通过这连接至 Hive Server Web UI，通过浏览器访问Hive
  * 元数据：存储在hive中的数据描述信息
  * 数据存储:
  * (1)db:在hdfs中表现为${hive.metastore.warehouse.dir}目录下一个文件夹
  * (2)table：内表，在hdfs中表现所属db目录下一个文件夹
  * (3)external table:外表，其数据存放位置可以在任意指定路径
  * (4)partition:分区，在hdfs中表现为table目录下的子目录
  * (5)bucket:桶，同一个表目录下根据hash散列之后的多个文件
* 基本使用
* 1 同mysql
* 2 导入数据：
