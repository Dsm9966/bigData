
## Hive

* 数据查询
    
    ![image.png](https://upload-images.jianshu.io/upload_images/14466577-afbb6b13348402b1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

##### 排序区别：
##### order by: 全局排序，一个reduce
##### sort  by: 不是全局，进入reducer之前排序完成；设置mapred.reduce.tasks>1
##### distribute by：开启的reducer数量=桶数
##### cluster by:当分桶和sort by 字段是同一个时，相当于distribute by+sort  by;不是同一个的话，不适用
##### join:
##### 内连接：inner join
##### 右外连接：right join
##### 左外连接：left join
##### 左半连接：left semi join(左连接结果基础上取左表相关数据)
