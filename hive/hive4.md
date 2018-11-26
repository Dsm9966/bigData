### 自定义jar包
* 创建自定义函数UDF:
  * 1.需求分析
  * 2 写java类，继承UDF类，实现evaluate方法，返回值和参数列表根据需求来定义
  * 3 对写好的代码进行单元测试
  * 4 将代码打成jar包 
  * 5 在hive 命令行界面通过 add jar 自己jar包位置来将jar包真正加入到hive的运行时classpath中去，这样才能找到类
  * 6 创建临时函数 create temporary function 方法名 as '全类名'；

#### eg:求三个数最大值，并且返回下标
#### 类继承UDF类，需要导入jar包，jar包路径：

  ![1.png](https://upload-images.jianshu.io/upload_images/14466577-8ba54f50bae40f3f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### 类：

  ![image.png](https://upload-images.jianshu.io/upload_images/14466577-c2f2bb33f1c54467.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
  

#### add jar /home/hadoop/hive/lib/hive.jar;

#### create temporary function dsm_maxindex as 'com.lanou.util.MyUDF';

#### select dsm_maxindex(1,2,3);

  ![image.png](https://upload-images.jianshu.io/upload_images/14466577-e5c4893c0a4a09a7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
