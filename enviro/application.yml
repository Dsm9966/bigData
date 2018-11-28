
spring:
  datasource:
    driver-class-name: com.mysql.jdbc.Driver
    url: jdbc:mysql://192.168.197.148:3306/dsm?characterEncoding=utf-8
    username: root
    password: 123

#mybatis
mybatis:
   type-aliases-package: com.lanou.secondboot.model
   mapper-locations: classpath:mapper/*.xml

#mapper
#mappers
mapper:
  mappers: com.lanou.secondboot.util.MyMapper
  not-empty: false
  identity: MYSQL

#pagehelper
pagehelper:
  helperDialect: mysql
  reasonable: true
  supportMethodsArguments: true
  params: count=countSql
#logging
logging:
  path: D:\logger
  level:
    ## warn 级别才打印
    root: warn
    com.lanou.secondboot: info
