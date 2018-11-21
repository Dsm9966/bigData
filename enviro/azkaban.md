## azkaban工作流调度器

* 三个压缩包：
  * azkaban-sql-script-2.5.0.tar.gz   存放了azkaban运行需要的sql（sql导入完文件就没用了）
  * azkaban-executor-server-2.5.0.tar.gz 存放执行器
  * azkaban-web-server-2.5.0.tar.gz 存放了web服务器

* 步骤：
* 1.解压: tar -zxf 
   * azkaban-2.5.0
   * azkaban-executor-2.5.0
   * azkaban-web-2.5.0
* 2.将三个文件放到一个文件夹下

![image.png](https://upload-images.jianshu.io/upload_images/14466577-393430c49e1f3a09.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 3.mysql下执行语句：
   * 3.1: source /home/hadoop/azkaban/azkaban-2.5.0/create-all-sql-2.5.0.sql(数据库为azkaban)

![1.png](https://upload-images.jianshu.io/upload_images/14465950-147874b28ef63e80.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
  
   * 3.2 数据库里生成表：
  
![2.png](https://upload-images.jianshu.io/upload_images/14465950-e858e16797a25f42.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 4.ssl 配置: keytool -keystore keystore -alias jetty -genkey -keyalg RSA
  * ssl的秘钥=jerry的密码（123456）
 
![1.png](https://upload-images.jianshu.io/upload_images/14465950-0f326339302f4333.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 5.配置 web下的文件:/azkaban-web-2.5.0/conf/
   * 5.1 vim azkaban.properties
    * 时区：Asia/Shanghai
    * mysql:root-123-azkaban
    * jerry:123456
 
![image.png](https://upload-images.jianshu.io/upload_images/14466577-a98c1a0c59bae5c8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

  * 5.2 vim azkaban-users.xml
      * '<`user username="admin" password="admin" roles="admin,metrics" /`>'
 
![image.png](https://upload-images.jianshu.io/upload_images/14466577-b868f85d39739c9e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
  
* 6.配置executor:azkaban-executor-2.5.0/conf
 * 6.1 vim azkaban.properties
      * 配置内容同5.1
 
![image.png](https://upload-images.jianshu.io/upload_images/14466577-bd6a068b5b03814f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 7.启动服务（start/shutdown）
 * 注意：运行路径问题
      * azkaban/azkaban-executor-2.5.0路径下：bin/azkaban-executor-start.sh
 
![image.png](https://upload-images.jianshu.io/upload_images/14466577-a4819c13c27b1f52.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
  
![image.png](https://upload-images.jianshu.io/upload_images/14466577-8c72e32fceda9bc8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
  
 * azkaban/azkaban-web-2.5.0路径下：bin/azkaban-web-start.sh
  
![image.png](https://upload-images.jianshu.io/upload_images/14466577-104790922d686c78.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
  
![image.png](https://upload-images.jianshu.io/upload_images/14466577-fdc4f5d7e81bc87b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


* 8 登录

![image.png](https://upload-images.jianshu.io/upload_images/14466577-98edbbf1ab966998.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
 

 

 

 



 
 
