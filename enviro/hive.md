## Hive
#### 启动mysql基础上，在mysql内的操作：
#### 1 mysql -u root -p(刚开始没有密码就登陆成功)
#### 2 MySQL> UPDATE mysql.user SET Password=PASSWORD('新密码') where USER='root';
#### 3 MySQL> flush privileges;
#### 4 MySQL> exit
#### 5 mysql -u root -p(再次登录，输入密码登陆成功)
#### 1 tar -zxf apache-hive-1.2.1-bin.tar.gz
#### 2 mv apache-hive-1.2.1-bin hive
#### 3 cd hive/
#### 4 pwd ：/home/hadoop/hive
#### 5 vim /etc/profile:配置环境变量(同JAVA_HOME;HADOOP_HOME)
#### 6 . /etc/profile

   ![image.png](https://upload-images.jianshu.io/upload_images/14466577-f7084238c6d71a88.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### 7 hive 

   ![image.png](https://upload-images.jianshu.io/upload_images/14466577-8c3b4c2cb04ef4f3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
   
#### 8 cd conf(pwd:/home/hadoop/hive/conf)
#### 9 touch hive-site.xml
#### 10 vim hive-site.xml

   ![image.png](https://upload-images.jianshu.io/upload_images/14466577-c2b9a8de43e1ac37.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
   
#### 11 hive 检查是否存在错误
#### 运行Navicat 
    
  ![image.png](https://upload-images.jianshu.io/upload_images/14466577-253f8e5148f19364.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

  ![image.png](https://upload-images.jianshu.io/upload_images/14466577-82033c0e9af35d6d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)




