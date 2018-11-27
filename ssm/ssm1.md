
jsp 能执行java代码的html
maven jar包管理工具

SpingBoot
@RestController
@RequestMapping

servlet同步请求
ajax   异步请求

清除缓存四种方式：
tomat 右键clean
project-->clean
export-->war file 
servers界面右键 publish

为了减小缓存，运行速度快，设置好工程存储位置,
配置tomcat(当无法修改时，删除后重新安装但不要运行)

![image.png](https://upload-images.jianshu.io/upload_images/14466577-280db6e00f9d6d38.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

运行后,在D:\apache-tomcat-8.5.35\webapps\FirstServlet\WEB-INF\classes路径下发现java文件存成.class文件

如果工程出现问题，在设定目录下也找不到对应的.class文件，点击markers内寻找错误


如何把本地写好的代码部署到服务器上？

1.工程--export-war file-选择存放路径
2.导入指定目录下：
![image.png](https://upload-images.jianshu.io/upload_images/14466577-6dbe7cd9423a7933.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
3.运行tomcat
4.服务器ip:8080/文件访问路径
![image.png](https://upload-images.jianshu.io/upload_images/14466577-3fbb929d12d306ba.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


ajax 除了发请求，还有对页面进行一些操作

形式：
	function succ(data){回调函数
	
	}
	var obj={
			url:"",发送请求的地址
			method:"",请求方式
			data:,发送到服务器的数据。将自动转换为请求字符串格式
			success:succ 由服务器返回，并根据 dataType 参数进行处理后的数据；描述状态的字符串				
		}
		$.ajax(obj)用于配置 Ajax 请求的键值对集合




