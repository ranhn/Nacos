# nacos
Alibaba nacos使用derby数据库存在sql注入


漏洞地址：
http://nacos.xxxxxxx.com.ph:8848/nacos/v1/cs/ops/derby?sql=select%20*%20from%20users

漏洞描述：
Alibaba nacos使用derby数据库存在sql注入,可直接执行sql查询相关敏感信息。

漏洞详情：


1，如果使用的是derby数据库，访问上述接口。
![image](https://github.com/ranhn/Nacos/assets/107679328/6a37ad79-d16e-4f35-bdb6-7277afcdf875)

2，执行sql语句，得到相关敏感数据。
![image](https://github.com/ranhn/Nacos/assets/107679328/30024d0c-6416-4403-9259-c010cc123dd3)

这个查询的数据输出表明了对 SQL 查询的直接执行，而没有对用户输入的 SQL 进行任何过滤或者防护。

3，如果不是使用的derby数据库，则提示 "The current storage mode is not Derby"
![image](https://github.com/ranhn/Nacos/assets/107679328/d32e5cc9-4843-4066-b8f7-ff8ab024779f)



漏洞版本：
nacos企业版 2.0.3以下
![image](https://github.com/ranhn/Nacos/assets/107679328/661ddf2c-efba-4231-be05-7e87b00cc30f)




修复建议：
为了防止 SQL 注入攻击，应该采取参数化查询等安全措施来处理用户输入的 SQL 查询。
