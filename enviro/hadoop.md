
## 伪分布式

* 单节点环境基础：$JAVA_HOME;$HADOOP_HOME
* 关闭防火墙：
   systemctl stop firewalld
   service firewalld status
* 配置hadoop文件：目标路径--hadoop2.7.3/etc/profile
  * 1.hadoop-env.sh
   * $JAVA_HOME=文件中/etc/profile中的$JAVA_HOME
  * 2.core-site.xml
   * fs.defaultFS:默认本地文件系统
   * hadoop.tmp.dir 存放临时文件的目录
 
    ![image.png](https://upload-images.jianshu.io/upload_images/14466577-792cdf10fc2c914e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
 
  * 3.hdfs-site.xml
   * dfs.namenode.name.dir:namenode的路径
   * dfs.datenode.data.dir:datenode的路径
   
    ![image.png](https://upload-images.jianshu.io/upload_images/14466577-df77b6b7c3dab298.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
   
  * 4.yarn-site.xml
   * yarn.nodemanager.aux.services:使用mapreduce_shuffle机制
    
    ![image.png](https://upload-images.jianshu.io/upload_images/14466577-d27c1e8e7ac31cfb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
    
  * 5 mapred-site.xml
   * cp mapred-site.xml.templete mapred-site.xml
      
     ![image.png](https://upload-images.jianshu.io/upload_images/14466577-eb9caa091384d8fb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 格式化hdfs
  * hadoop namenode -format(注意是n)
 
     ![image.png](https://upload-images.jianshu.io/upload_images/14466577-d6826393a6f9de77.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 启动hadoop服务
   * start-all.sh 全部开启
 
     ![image.png](https://upload-images.jianshu.io/upload_images/14466577-85e27514bf2e3193.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
 
   * start-yarn.sh 开启ResourceManager,NodeManager
   * start-dfs.sh  开启SecondaryNameNode, NameNode,DataNode
* 关闭hadoop服务
   * stop-all.sh 关闭全部
   * hadoop-daemon.sh start 启动单个节点进程

* 若出现关闭后仍有除jsp进程存在，或者进程号被占用：
   * netstat -tunlp`|`grep 端口号 查看端口是否被占用
   * kill -9 端口号 杀死进程
 


 
