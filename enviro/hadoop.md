
#### 伪分布式

* 单节点环境基础：$JAVA_HOME;$HADOOP_HOME
* 关闭防火墙：
  * systemctl stop firewalld
  * service firewalld status
* 配置hadoop文件：目标路径--hadoop2.7.3/etc/profile
  * 1 hadoop-env.sh
  * $JAVA_HOME=文件中/etc/profile中的$JAVA_HOME
  * 2 core-site.xml
  * 
