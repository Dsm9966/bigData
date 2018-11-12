## Mysql配置

#### sudo yum -y install wget
#### wget http://repo.mysql.com/mysql-community-release-el7-5.noarch.rpm
#### sudo rpm -ivh mysql-community-release-el7-5.noarch.rpm
#### sudo yum -y install mysql-server
#### sudo yum -y install mysql
#### systemctl start mysqld
#### mysql -u root -p(没密码)

## Hive
#### tar -zxf apache-hive-1.2.1-bin.tar.gz
####  mv apache-hive-1.2.1-bin hive
####  cd hive/
####  pwd ：/home/hadoop/hive
####  vim /etc/profile:配置环境变量(同JAVA_HOME;HADOOP_HOME)
####  . /etc/profile

      ![image.png](https://upload-images.jianshu.io/upload_images/14466577-f7084238c6d71a88.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

####  cd conf(pwd:/home/hadoop/hive/conf)
#### touch hive-site.xml
####  vim hive-site.xml

      ![image.png](https://upload-images.jianshu.io/upload_images/14466577-c2b9a8de43e1ac37.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
      
#### hive 

      ![image.png](https://upload-images.jianshu.io/upload_images/14466577-8c3b4c2cb04ef4f3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### 运行Navicat 
    
    ![image.png](https://upload-images.jianshu.io/upload_images/14466577-253f8e5148f19364.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

    ![image.png](https://upload-images.jianshu.io/upload_images/14466577-82033c0e9af35d6d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)




