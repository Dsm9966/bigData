## zookeeper

## zookeeper配置

### --单机模式----------------------------------
* tar -zxf zookeeper-3.4.6.tar.gz
* cd zookeeper-3.4.6/conf
* cp zoo_sample.cfg zoo.cfg
* vim zoo.cfg 修改datadir="/home/hadoop/zookeeper-3.4.6/zkData"
* ./zkServer.sh start

* ./zkServer.sh status

* jps
* ./zkServer.sh stop
### --伪分布式-----------------------------------
* 一台电脑
* cd ~
* mkdir zk
* mv zookeeper-3.4.6 zk
* cd zk
	* cp -r zookeeper-3.4.6 zk2
	* cp -r  zookeeper-3.4.6 zk3
	* mv  zookeeper-3.4.6/ zk1
* 对三个文件夹下的conf/zoo.cfg下进行修改：
 	* zk1中的dataDir=/home/hadoop/zk/zk1/zkData
	* zk2中的dataDir=/home/hadoop/zk/zk2/zkData;clientPort=2182
	* zk3中的dataDir=/home/hadoop/zk/zk3/zkData;clientPort=2183

* 添加id			
	* echo "1"`>` /home/hadoop/zk/zk1/zkData/myid
	* echo "2"`>` /home/hadoop/zk/zk2/zkData/myid
	* echo "3"`>` /home/hadoop/zk/zk3/zkData/myid

* 对三个文件夹下的每个conf/zoo.cfg下进行添加（防止其中一个出现错误）：
	* server.1=192.168.197.148:2888:3888
	* server.2=192.168.197.148:2889:3889
	* server.3=192.168.197.148:2890:3890
* 开启
	* zk1/bin/zkServer.sh start-------follower（第一个开启没有参照物）
	* zk2/bin/zkServer.sh start-------leader(即使leader关闭，其他两个仍会选举出一个leader)
	* zk3/bin/zkServer.sh start-------follower
### --完全分布-------在伪分布基础上------------------------------------
第一台电脑
* vim zoo.cfg 中
	* dataDir=/home/hadoop/zookeeper-3.4.6/zkData
	* server.1=192.168.197.148:2888:3888
	* server.2=192.168.197.137:2888:3888
	* server.3=192.168.197.138:2888:3888
	* (选举需要进行通信，通信需要端口，同步需要端口)
* cd ~/zookeeper-3.4.6
* mkdir zkData
* echo "1" `>` zkData/myid
第二台
* 同1;echo "2" `>` zkData/myid
 第三台
* 同1;echo "3" `>` zkData/myid
* 同时启动：bin/zkServer.sh start

![image.png](https://upload-images.jianshu.io/upload_images/14466577-5a1963a95e84f9fd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

bin/zkServer.sh status

![image.png](https://upload-images.jianshu.io/upload_images/14466577-5345996191a38ece.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![image.png](https://upload-images.jianshu.io/upload_images/14466577-c1a26f8e3d6768d4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![image.png](https://upload-images.jianshu.io/upload_images/14466577-5d9473b1c49e6416.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 如果存在问题，可以查看日志：

![image.png](https://upload-images.jianshu.io/upload_images/14466577-e52a281135442b6d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### --客户端操作-----------------------------------------------
* bin/zkCli.sh 
* 基本语法
	* 添加子节点和value：create /name dsm（创建时一定要加value）
	* 获取key的value:get /name[watch]只监测一次
	* 更改子节点的value:set /name wukong
	* 展示子数据的变化： ls /user[watch]
	* 删除节点： rmr /name

	![image.png](https://upload-images.jianshu.io/upload_images/14466577-350fa47ebec5a705.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


### --java api客户端-----------------------------------------------
* 1.创建maven项目

* 2.选择

	![image.png](https://upload-images.jianshu.io/upload_images/14466577-4ccb3f315a3ca948.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 3.创建后等待下载，成功后向pom.xml文件添加
    	<dependency>
		<groupId>org.apache.zookeeper</groupId>
		<artifactId>zookeeper</artifactId>
		<version>3.4.6</version>
	</dependency>






















