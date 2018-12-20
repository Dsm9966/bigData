
### hadoop完全分布式

* namenode:伪分布环境
* 将namenode的/etc/profile,hadoop-2.7.3/etc/hadoop传递到三台基础datanode上
  * scp -r(递归) 要传递的内容 电脑用户名@ip:放置路径
  
  ![image.png](https://upload-images.jianshu.io/upload_images/14466577-06905a1cf11f2ed9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
  
  * namenode的/etc/profile粘贴到datanode中
 * vim hadoop-2.7.3/etc/hadoop/slaves --只放置datanode的ip,让namenode知道datanode
 
   ![image.png](https://upload-images.jianshu.io/upload_images/14466577-f923792a17599a05.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
  
* 可以用namenode启动datanode...........
* 问题：datanode无法注册到namenode中：
  * vim /etc/hosts 
  
  ![image.png](https://upload-images.jianshu.io/upload_images/14466577-d6edd49b1fba3ecd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 启动namenode
  * namenode:   
  
   ![image.png](https://upload-images.jianshu.io/upload_images/14466577-504d572807ddc083.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
 
 * datanode:   
  
    ![image.png](https://upload-images.jianshu.io/upload_images/14466577-5ee15f56ca427626.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 成功标志
  * 第一种：namenode的ip:50070
  
  ![image.png](https://upload-images.jianshu.io/upload_images/14466577-0c3702977705c378.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
  
  * 第二种：hdfs dfsadmin -report
  
* 免密    
    
  * ssh-keygen 生成秘钥
  * ssh-copy-id 用户名@ip 选择免密的用户
  * .ssh/id_rsa_pub >> .ssh/authorized_keys 将秘钥保存到本地
   
* 遇到问题
 * 安全问题
   解决方法：hdfs dfsadmin -safemode leave
 * namenode和datanode的clusterID不统一问题  
    原因：
   ![1111.png](https://upload-images.jianshu.io/upload_images/14466577-843e6b0626095d0a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
   
    解决方法：
    
    ![image.png](https://upload-images.jianshu.io/upload_images/14466577-4283a1fd41cb8ded.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

    
   ![image.png](https://upload-images.jianshu.io/upload_images/14466577-07ea84ac1c01619f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
  
  如果再次查询VERSION，需要退出所在的current目录下，因为该目录已经删除
   
   最后，重新启动就好~~~
   
   
   
   
  

