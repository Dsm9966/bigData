

### jdk

java环境配置：
* 解压jdk
* jdk文件夹所在的目录 pwd
* 配置 /etc/profile
* export JAVA_HOME=$(pwd)
* export CLASSPATH=$:CLASSPATH:$JAVA_HOME/lib/
* export PATH=$PATH:$JAVA_HOME/bin

### hadoop

* java环境配置基础上
* tar -zxvf hadoop压缩包
* 找到hadoop文件夹根目录$(pwd)
* 配置 .bash_profile 
* 添加 HAOOP_HOME=$(pwd)
       * PATH=原来内容:$HAOOP_HOME/bin:$ HAOOP_HOME/sbin 
* 或者 /etc/profile
       * PATH=$PATH:$JAVA_HOME/bin:$HAOOP_HOME/bin:$ HAOOP_HOME/sbin 
* 测试

![image.png](https://upload-images.jianshu.io/upload_images/14498135-1e858515d16ed507.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![image.png](https://upload-images.jianshu.io/upload_images/14498135-97da3f98dbf48206.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
