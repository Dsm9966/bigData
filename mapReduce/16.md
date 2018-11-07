## 本地创建hdfs

#### hadoop2.7.3/bin替换hadooponwindows-master/bin 

![image.png](https://upload-images.jianshu.io/upload_images/14466577-2dffe8e117c0f26f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### hadoop2.7.3/bin/hadoop.dll,winutils复制到c:/Windows/System32中

![image.png](https://upload-images.jianshu.io/upload_images/14466577-9645e3543de8a453.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![image.png](https://upload-images.jianshu.io/upload_images/14466577-53b15b0fc5337fc0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### 配置环境变量 JAVA_HOME;HADOOP_HOME ;PATH----hadoop命令提示JAVA_HOME存在问题

![image.png](https://upload-images.jianshu.io/upload_images/14466577-2e09abb3309685da.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### hadoop2.7.3/etc/hadoop/hadoop-env.cmd:JAVA_HOME

![image.png](https://upload-images.jianshu.io/upload_images/14466577-551c7d4c8727082b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### ----/core-site.xml 更改与否都可以

![image.png](https://upload-images.jianshu.io/upload_images/14466577-e9c3d96f2879c2e8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### ----/hdfs-site.xml 在本地磁盘创建目录存放datanode,namenode

![image.png](https://upload-images.jianshu.io/upload_images/14466577-fbc89257b52576b7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### start-all.cmd

#### jps 或者 localhost:50070(ip与core-site.cml的ip相同)

![image.png](https://upload-images.jianshu.io/upload_images/14466577-c3b2d91469dda0f7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![image.png](https://upload-images.jianshu.io/upload_images/14466577-3b08d9f5f30ccfa3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
