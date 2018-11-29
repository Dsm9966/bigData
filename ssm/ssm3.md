## SpringBoot项目
### 1.springboot搭建环境
### 2.springboot参数接受 String User,接受参数名称匹配，自定义类型，传过来的key与自定义类型匹配
### 3.分页:PageInfo PageHelper.startPage(页码，一页展示数量)，new PageInfo(查询到的集合)
### 4.ajax请求到数据继续页面渲染
### $(找到要操作的标签)根据需求决定要追加还是清空，执行不同的方法，html();append(要添加进去的元素)
### 5.logback日志级别error>warn>info>debug
### logging path,logging.level root=warn com.lanou=info---->spring.log文件,flume tail -F(追加一个带走一个)
### 6.echarts可视化展示
* 6.1 引js `<script src="https://unpkg.com/echarts@4.2.0-rc.2/dist/echarts.min.js"></script>`
* 6.2 创建一个div作为容器	`<div id="main" style="width: 600px;height:400px;"></div>`
* 6.3 初始化	`var myChart = echarts.init(document.getElementById('main'));	`
* 6.4 设置需要的属性 http://echarts.baidu.com/examples/
* 6.5 使用指定的配置	`myChart.setOption(option);`	
### 7.servlet-->war包;springboot-->jar包 
* 直接启动springboot项目，但是只要一停掉进程，或者关闭回话项目也会跟着停掉（前台运行模式）
* spring-boot后台运行:`nohup java -jar ~/jar/secondboot-0.0.1-SNAPSHOT.jar  & ` 关闭:`kill -9`
### 8.跨域请求（域名=ip+port），ajax默认不允许跨域请求
### 如果希望实现跨域请求，找到对应的请求方法，设置上`@CrollOrigin(origins="*",maxAge=3600)`，这样这个方法就允许跨域请求了
## springboot启动方式：
### 1.执行main()方法
### 2.maven插件-->spring-boot-->spring-boot:run

  ![image.png](https://upload-images.jianshu.io/upload_images/14466577-83f41fbe78d57070.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 3.执行本项目的jar包 

* 3.1用插件打出来该项目jar包，项目停止状态
	
	![image.png](https://upload-images.jianshu.io/upload_images/14466577-b591735799293304.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
	
* 3.2 执行jar包 `java -jar secondboot-0.0.1-SNAPSHOT.jar``  
	
	![image.png](https://upload-images.jianshu.io/upload_images/14466577-4599bb0e8290c806.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
	
## 为了区分在本地还是远端（开发环境/生产环境）方便改配置：
### 1.application.yml总配置(去掉path) 
### 2.创建application-dev.yml  
`logging:`
	`path: D:\logger\logs`
				
### 3.application-prod.yml 开发环境
`logging:`
		`path: /home/hadoop/bootlogs`
			
### 4.application.yml在spring下添加		
`profiles:`
	`active: dev/prod(上面两个文件)`
	
### 注意：改配置文件后需要重新package一遍	

	
	
	
	
	
	
	
	
