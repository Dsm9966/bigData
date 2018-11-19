
date_sub()

原表：

![image.png](https://upload-images.jianshu.io/upload_images/14466577-4dc8cc52dc6a961a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

获取：连续销售天数超过3天的店铺

1.根据店铺进行分区，根据时间进行升序排序，生成行号
select *,row_number() over(partition by name order by times) as row_num from shop

![image.png](https://upload-images.jianshu.io/upload_images/14466577-22434739c30914f2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

2.以上一步查询结果为基表，将得到的临时表中的times-row_num得到的差值相同表示是连续的
select name,times,count,date_sub(times,row_num) as diff
from
(select *,row_number() over(partition by name order by times) as row_num from shop)as res

![image.png](https://upload-images.jianshu.io/upload_images/14466577-ff8251ec457f23f3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

3.以上一步查询结果为基表，以店铺名和减出来的结果进行group by,从分组的结果中取出店铺名和分组的记录个数，也就知道了店铺连续销售天数
select name,count(*) as res_count
from
(select name,times,count,date_sub(times,row_num) as diff
from
(select *,row_number() over(partition by name order by times) as row_num from shop) as first) as res
group by diff,name
having res_count >= 3

![image.png](https://upload-images.jianshu.io/upload_images/14466577-583ccbe0fbc3f93a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


创建自定义函数UDF:
1.需求分析
2 写java类，继承UDF类，实现evaluate方法，返回值和参数列表根据需求来定义
3 对写好的代码进行单元测试
4 将代码打成jar包 
5 在hive 命令行界面通过 add jar 自己jar包位置来将jar包真正加入到hive的运行时classpath中去，这样才能找到类
6 创建临时函数 create temporary function 方法名 as '全类名'；

eg:求三个数最大值，并且返回下标


#### add jar /home/hadoop/hive/lib/hive.jar;

#### create temporary function dsm_maxindex as 'com.lanou.util.MyUDF';

#### select dsm_maxindex(1,2,3);

![image.png](https://upload-images.jianshu.io/upload_images/14466577-e5c4893c0a4a09a7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
