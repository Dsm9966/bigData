## SpringBoot搭建

## SpringBoot
### spingboot-SSM搭建
* 1.创建springboot项目

![image.png](https://upload-images.jianshu.io/upload_images/14466577-043fe9ee8455b0e3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![image.png](https://upload-images.jianshu.io/upload_images/14466577-7017cb8c7fd9c109.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![image.png](https://upload-images.jianshu.io/upload_images/14466577-0144260c8ab7a209.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


* 2.修改pom.xml把需要的dependence加入dependencies下,plugin也加入(这样才有逆向工程插件mybatis-generator)
[]()
![image.png](https://upload-images.jianshu.io/upload_images/14466577-0051bc01e3e244d7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


* 3.逆向工程 generatorConfig.xml->告诉他要逆向工程的表有哪些，要生成实体类放哪里，生成dao接口放在哪里，要生成的xml放在哪里;
* 配置完后运行mybatis-generator,会出现对应的文件夹结构
	
* 4.接口MyMapper进行创建，继承Mapper<T>,MysqlMapper<T>接口，才能使用公共方法
* 5.application.yml设置数据库配置以及mybatis的配置
`spring:
    datasource:
        driver-class-name: com.mysql.jdbc.Driver
        url: jdbc:mysql://192.168.197.148:3306/dsm?characterEncoding=utf-8
        username: root
        password: 123`
`#mybatis 框架需要进行的设置
mybatis:
    type-aliases-package: com.lanou.firstboot.model
    mapper-locations: classpath:mappers/*.xml`
`#mapper 
#mappers 通用mapper设置，可以使用很多通用方法
mapper:
    mappers: com.lanou.firstboot.util.MyMapper
    not-empty: false
    identity: MYSQL`
`#pagehelper 分页插件的配置
pagehelper:
    helperDialect: mysql
    reasonable: true
    supportMethodsArguments: true
    params: count=countSql` 
* 6.SecondbootApplication在自己的boot项目的主入口设置
	* @MapperScan选择tk包下的(basePackages="dao层接口所在的包名")
	* eg:@MapperScan(basePackages = "com.lanou.secondboot.dao")
* 7.把要使用的dao层接口定义成对应的controller属性，并且加上@Autowired注解，就可以在请求方法中使用

![image.png](https://upload-images.jianshu.io/upload_images/14466577-9514dbac66c1bc9b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 8.运行成功

![image.png](https://upload-images.jianshu.io/upload_images/14466577-774ca5f89bcf2bff.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)




