* 一.mapreduce自定义输入输出
* inputFormat --> recordreader
* split job 
* outputFormat --> recordwriter
* 二.hive
* 1.hive的安装
	* 解压缩，bin/hive,未使用Mysql
	* 为了将元数据存放到mysql,
	* 安装配置mysql:rpm,yum;修改root密码;设置远程连接
	* 为了让hive使用mysql作为元数据存放仓库，配置hive-site.xml
* 2.create table
	* 2.1 内部表 外部表(location)
	* 2.2 分区表:减小查询范围 分桶表：减少join消耗资源，高效
	* eg:把订单做成多分区分桶表
* 3.load,insert,CTAS
* 4.select 	
* 5.type arr,map,struct
* 6.function date arr,explode,表生成函数lateral view，窗口分析函数
	* select * from 
	* (select *,row number()
	* over(partition by gender order by age desc)as row_num from topn)as res
	* where row_num<=2;
* row_number() over()总共做了对数据根据partition by 的属性进行分区，
* 通过order by 对每个分区单独排序并生成一列行号
#### 实际例子：
原表：

![image.png](https://upload-images.jianshu.io/upload_images/14466577-4dc8cc52dc6a961a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

获取：连续销售天数超过3天的店铺

1.根据店铺进行分区，根据时间进行升序排序，生成行号
	* select *,row_number() over(partition by name order by times) as row_num from shop

![image.png](https://upload-images.jianshu.io/upload_images/14466577-22434739c30914f2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

2.以上一步查询结果为基表，将得到的临时表中的times-row_num得到的差值相同表示是连续的
	* select name,times,count,date_sub(times,row_num) as diff
	* from
	* (select *,row_number() over(partition by name order by times) as row_num from shop)as res

![image.png](https://upload-images.jianshu.io/upload_images/14466577-ff8251ec457f23f3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

3.以上一步查询结果为基表，以店铺名和减出来的结果进行group by,从分组的结果中取出店铺名和分组的记录个数，也就知道了店铺连续销售天数
	* select name,count(*) as res_count
	* from
	* (select name,times,count,date_sub(times,row_num) as diff
	* from
	* (select *,row_number() over(partition by name order by times) as row_num from shop) as first) as res
	* group by diff,name
	* having res_count >= 3

![image.png](https://upload-images.jianshu.io/upload_images/14466577-583ccbe0fbc3f93a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
