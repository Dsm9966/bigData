## flume日志采集系统
* 特征：分布式、可靠性、可拓展性、可管理性
### flume架构
* 数据流
  * Flume的核心是把数据从数据源收集过来，在送到目的地，为了保证输送一定成功，在送到目的地之前，会先缓存数据，待数据真正到达目的地后，删除自己缓存的数据
  * flume传输的基本单位-->event,代表数据流最小的完整单位，本身为byte数组，从外部数据源来，到外部目的地去
  * flume运行核心-->agent,数据收集工具，包含三个部件：
     * source:接受外部源发送的数据
     * channel:存储地，接受source的输出，直到sink消费掉channel中的数据
     * sink:消费channel中的数据，然后送给外部源或者其他source
  
    ![image.png](https://upload-images.jianshu.io/upload_images/14466577-f11d51aa4c56cccb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)   
  
    * 允许多个agent连在一起
    
    ![image.png](https://upload-images.jianshu.io/upload_images/14466577-8d4e2058e97ef423.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
* 组件
  * source
  
