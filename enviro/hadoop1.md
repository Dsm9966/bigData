
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
    
  * ssh -keygen
  * ssh-copy-id 用户名@ip
  * .ssh/id_rsa_pub >> .ssh/authorized_keys
   
   
   
  

