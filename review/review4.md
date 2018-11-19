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
* select * 
* from 
* (select *,row number()
* over(partition by gender order by age desc)as row_num from topn)as res
* where row_num<=2;
* row_number() over()总共做了对数据根据partition by 的属性进行分区，
* 通过order by 对每个分区单独排序并生成一列行号
