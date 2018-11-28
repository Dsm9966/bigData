## servlet/ajax
### 基础了解
* jsp 能执行java代码的html
* maven jar包管理工具
* SSM:Spring+SpringMVC+MyBatis

springboot-->SSM
* @RestController
* @RequestMapping()设置请求访问路径

### servlet同步请求
* 清除缓存四种方式：
	* tomat 右键clean
	* project-->clean
	* export-->war file 
	* servers界面右键 publish

* 为了减小缓存，运行速度快，设置好工程存储位置,
配置tomcat(当无法修改时，删除后重新安装但不要运行)

![image.png](https://upload-images.jianshu.io/upload_images/14466577-280db6e00f9d6d38.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 运行后,在D:\apache-tomcat-8.5.35\webapps\FirstServlet\WEB-INF\classes路径下发现java文件存成.class文件

![image.png](https://upload-images.jianshu.io/upload_images/14466577-e43baa47445f2e22.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 如果工程出现问题，在设定目录下也找不到对应的.class文件，点击markers内寻找错误(很大可能是jar包出现问题)


### 如何把本地写好的同步请求代码部署到服务器上？

* 1.工程--export-war file-选择存放路径
* 2.导入指定目录下：

![image.png](https://upload-images.jianshu.io/upload_images/14466577-6dbe7cd9423a7933.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 3.运行tomcat
* 4.服务器ip:8080/文件访问路径

![image.png](https://upload-images.jianshu.io/upload_images/14466577-3fbb929d12d306ba.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


### ajax异步请求

除了发请求，还有对页面进行一些操作

形式：
### function succ(data){
### }
### var obj={
### url:"",
### method:"",
### data:,
### success:succ 				
### }
### $.ajax(obj)
* url:发送请求的地址
* method:"",请求方式
* data:发送到服务器的数据。将自动转换为请求字符串格式
* success:succ 回调函数;由服务器返回，并根据 dataType 参数进行处理后的数据；描述状态的字符串				
* $.ajax(obj)用于配置 Ajax 请求的键值对集合

### json 校验格式化工具
* 使用fastjson-1.2.47.jar-->json
* toJSONString(Object object)-->转换化成json类型字符串
* parse()-->将字符串转化成对象（保存方式：键值对）
### ajax和json实例
* eg:注册用户时，检查用户是否存在，存在则显示存在;不存在则添加到数据库并显示注册成功
* 页面

![image.png](https://upload-images.jianshu.io/upload_images/14466577-e3fec278a0ed5ef3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 用ajax以异步请求方式向服务器发出请求

![image.png](https://upload-images.jianshu.io/upload_images/14466577-3f7395c521eab63f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 服务器
* (1)servlet层

![image.png](https://upload-images.jianshu.io/upload_images/14466577-7b2b919e37c8d8ed.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* (2)dao层
	* findUserByName(String name)返回List<User>
	* regUser(String name,String pwd)向数据库内添加数据
* ajax内的success回调函数
	
![image.png](https://upload-images.jianshu.io/upload_images/14466577-e8e0e8fe5c8d8030.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



