# wiki

#### 介绍
* 采用前后端分离的模式，微服务版本前端(基于 [vue-element-admin](https://github.com/PanJiaChen/vue-element-admin));
* 后端采用Spring Boot、Spring Cloud & Alibaba;
* 注册中心+配置中心选型Nacos;
* 权限认证使用spring security + Jwt token;
#### 软件架构
<img src="./images/ch-cloud.jpg" alt="软件架构"/>

####微服务说明

[ch-admin3](https://gitee.com/ch-cloud/ch-admin3)  
说明：静态页面（基于Vue + element-ui） 
~~~
基本功能：
——系统管理
————用户管理
————角色管理
————权限管理
————组织管理
————职位管理
————数据字据
——日志管理
————登录日志
————操作日志
扩展功能：
——Canal管理
————集群管理
————服务管理
————实例管理
————告警管理
——Kafka管理
————群集管理
————主题管理
————消息搜索
————RPC泛化调用
~~~
[ch-upms](https://gitee.com/ch-cloud/ch-upms)  
说明：用户权限管理服务  
提供用户、角色、权限、组织、职位、数据字典、日志等管理RestFul接口

[ch-sso](https://gitee.com/ch-cloud/ch-sso)  
说明：用户登录认证服务  
提供用户登录、用户信息、Token刷新、网关权限认证RestFul接口

[ch-gateway](https://gitee.com/ch-cloud/ch-gateway)  
说明：网关服务  
提供Token鉴权、请求拦截与分发、日志记录

**由于资源不足，未能提供演示环境，请参考以下安装教程**

#### 安装教程
准备一台4核8G服务器  
基于Docker安装开发环境  

>基础服务
1.  安装数据库Mysql
2.  安装缓存Redis
3.  安装Nacos
4.  安装prometheus(监控中间件，非必要安装)
5.  安装grafana(监控面板，非必要安装)  

复制docker/base目录到服务器
使用docker/base/docker-compose.yaml一键部署
```shell script
docker-compose -f docker-compose.yml up -d
```
>中间服务
1.  安装RocketMQ
```shell script

```
>应用服务
1.  静态页面服务（请点击[ch-admin3](https://gitee.com/ch-cloud/ch-admin3)）
2.  用户权限服务（请点击[ch-upms](https://gitee.com/ch-cloud/ch-upms)）
3.  用户登录认证服务（请点击[ch-sso](https://gitee.com/ch-cloud/ch-sso)）
4.  网关鉴权请求服务（请点击[ch-gateway](https://gitee.com/ch-cloud/ch-gateway)）
>扩展服务(非必要安装)
1.  Canal管理服务（请点击[canal-admin]()）
2.  Kafka管理服务（请点击[ch-kafka]()）

#### 使用说明
<table>
    <tr>
        <td>登录</td>
        <td>首页</td>
    </tr>
    <tr>
        <td><img src="https://oscimg.oschina.net/oscnet/cd1f90be5f2684f4560c9519c0f2a232ee8.jpg"/></td>
        <td><img src="https://oscimg.oschina.net/oscnet/1cbcf0e6f257c7d3a063c0e3f2ff989e4b3.jpg"/></td>
    </tr>
    <tr>
        <td>用户管理</td>
        <td>角色管理</td>
    </tr>
    <tr>
        <td><img src="https://oscimg.oschina.net/oscnet/707825ad3f29de74a8d6d02fbd73ad631ea.jpg"/></td>
        <td><img src="https://oscimg.oschina.net/oscnet/46be40cc6f01aa300eed53a19b5012bf484.jpg"/></td>
    </tr>
    <tr>
        <td>权限管理</td>
        <td>组织管理</td>
    </tr>
    <tr>
        <td><img src="https://oscimg.oschina.net/oscnet/4284796d4cea240d181b8f2201813dda710.jpg"/></td>
        <td><img src="https://oscimg.oschina.net/oscnet/3ecfac87a049f7fe36abbcaafb2c40d36cf.jpg"/></td>
    </tr>
    <tr>
        <td>职位管理</td>
        <td>数据字典</td>
    </tr>
	<tr>
        <td><img src="https://oscimg.oschina.net/oscnet/71c2d48905221a09a728df4aff4160b8607.jpg"/></td>
        <td><img src="https://oscimg.oschina.net/oscnet/c14c1ee9a64a6a9c2c22f67d43198767dbe.jpg"/></td>
    </tr>	
    <tr>
        <td>登录日志</td>
        <td>操作日志</td>
    </tr> 
    <tr>
        <td><img src="https://oscimg.oschina.net/oscnet/5e8c387724954459291aafd5eb52b456f53.jpg"/></td>
        <td><img src="https://oscimg.oschina.net/oscnet/644e78da53c2e92a95dfda4f76e6d117c4b.jpg"/></td>
    </tr>
    <tr>
        <td>集群管理</td>
        <td>服务管理</td>
    </tr>
	<tr>
        <td><img src="https://oscimg.oschina.net/oscnet/fdea1d8bb8625c27bf964176a2c8ebc6945.jpg"/></td>
        <td><img src="https://oscimg.oschina.net/oscnet/509d2708cfd762b6e6339364cac1cc1970c.jpg"/></td>
    </tr>
    <tr>
        <td>实例管理</td>
        <td>告警管理</td>
    </tr>
	<tr>
        <td><img src="https://oscimg.oschina.net/oscnet/up-f1fd681cc9d295db74e85ad6d2fe4389454.png"/></td>
        <td><img src="https://oscimg.oschina.net/oscnet/up-c195234bbcd30be6927f037a6755e6ab69c.png"/></td>
    </tr>
</table>
1.  登录

2.  xxxx
3.  xxxx

#### 参与贡献

1.  Fork 本仓库
2.  新建 Feat_xxx 分支
3.  提交代码
4.  新建 Pull Request


#### 码云特技

1.  使用 Readme\_XXX.md 来支持不同的语言，例如 Readme\_en.md, Readme\_zh.md
2.  码云官方博客 [blog.gitee.com](https://blog.gitee.com)
3.  你可以 [https://gitee.com/explore](https://gitee.com/explore) 这个地址来了解码云上的优秀开源项目
4.  [GVP](https://gitee.com/gvp) 全称是码云最有价值开源项目，是码云综合评定出的优秀开源项目
5.  码云官方提供的使用手册 [https://gitee.com/help](https://gitee.com/help)
6.  码云封面人物是一档用来展示码云会员风采的栏目 [https://gitee.com/gitee-stars/](https://gitee.com/gitee-stars/)
