
## Hive

* 数据查询
    
    ![image.png](https://upload-images.jianshu.io/upload_images/14466577-afbb6b13348402b1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
    
* where、having、group by:
    *  1 使用分组就不再逐行执行模式了，会根据我们的分组key以分组模式执行，
    *  所以我们数据都是一组一组的，没法调用除了分组key和聚合函数(属性)之外的单独属性
    *  2 使用聚合函数得到的结果默认的字段名不好使，我们要进行调用可以给它取一个别名，就可以在条件中使用了，
    *  同一层给having使用，作为子查询时可以给外层where用
    *  3 where 执行时间在聚合之前进行数据筛选，而having是在聚合结束之后继续条件处理
* 排序区别：
    * order by: 全局排序，一个reduce
    * sort  by: 不是全局，进入reducer之前排序完成；设置mapred.reduce.tasks>1
    *  distribute by：开启的reducer数量=桶数
    *  cluster by:当分桶和sort by 字段是同一个时，相当于distribute by+sort  by;不是同一个的话，不适用
* join:
    *  内连接：inner join
    *  右外连接：right join
    *  左外连接：left join
    *  全连接：full join
    *  左半连接：left semi join(左连接结果基础上取左表相关数据)
* 数据类型
    *  1 原子数据类型：
        *  数值型
        *  时间类型：timestamp时间戳；date日期，年月日组成
        *  布尔型
        *  字符串型
    *  2 复杂数据类型：
        *  数组（Array)：相同数据类型的元素组成，可以通过下标访问，从0开始
        *  create table t_movie(moive_name string,actors array<string>,first_show date)
        *  row format delimited fields terminated by ','
        *  collection items terminated by ':';
*  映射（Map）:通过key来访问元素，eg:userlist['username']-->password

   ![image.png](https://upload-images.jianshu.io/upload_images/14466577-912fcc4414cb51a0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

   ![image.png](https://upload-images.jianshu.io/upload_images/14466577-3c3013a30344a6c9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240) 

*  结构体（struct）:可以包含不同类型的元素，获取元素方式‘.’,eg：user.name
