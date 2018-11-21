## azkaban工作流调度器

* 三个压缩包：
azkaban-sql-script-2.5.0.tar.gz   存放了azkaban运行需要的sql（sql导入完文件就没用了）
azkaban-executor-server-2.5.0.tar.gz 存放执行器
azkaban-web-server-2.5.0.tar.gz 存放了web服务器

* 步骤：
* 1.解压
#### tar -zxf 
  * azkaban-2.5.0
  * azkaban-executor-2.5.0
  * azkaban-web-2.5.0
* 2.将三个文件放到一个文件夹下

  ![image.png](https://upload-images.jianshu.io/upload_images/14466577-393430c49e1f3a09.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 3.mysql下执行语句：
  * 3.1 
  #### source /home/hadoop/azkaban/azkaban-2.5.0/create-all-sql-2.5.0.sql

  ![1.png](https://upload-images.jianshu.io/upload_images/14465950-147874b28ef63e80.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
  
  * 3.2 数据库里生成表：
  
  ![2.png](https://upload-images.jianshu.io/upload_images/14465950-e858e16797a25f42.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* ssl 配置

#### keytool -keystore keystore -alias jetty -genkey -keyalg RSA
