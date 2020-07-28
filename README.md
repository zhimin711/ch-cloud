# wiki

### 介绍
* 采用前后端分离的模式，微服务版本前端(基于 [vue-element-admin](https://github.com/PanJiaChen/vue-element-admin));
* 后端采用Spring Boot、Spring Cloud & Alibaba;
* 注册中心+配置中心选型Nacos;
* 权限认证使用spring security + Jwt token;
### 软件架构
<img src="./images/ch-cloud.jpg" alt="软件架构"/>

>服务注册与调用
基于Nacos来实现的服务注册与调用，在Spring Cloud中使用Feign, 我们可以做到使用HTTP请求远程服务时能与调用本地方法一样的编码体验，开发者完全感知不到这是远程方法，更感知不到这是个HTTP请求。

>服务鉴权  
通过JWT的方式来加强服务之间调度的权限验证，保证内部服务的安全性。

>负载均衡  
将服务保留的rest进行代理和网关控制，除了平常经常使用的node.js、nginx外，Spring Cloud系列的gateway和ribbon，可以帮我们进行正常的网关管控和负载均衡。  
其中扩展和借鉴国内Alibaba Sentinel组件，方面进行限流。

>熔断机制  
因为采取了服务的分布，为了避免服务之间的调用“雪崩”，采用了Hystrix的作为熔断器，避免了服务之间的“雪崩”。

### 微服务说明

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
提供Token鉴权、路由、请求日志记录

**由于资源不足，未能提供演示环境，请参考以下安装教程**

### 安装教程
准备一台4核8G服务器  
基于Docker安装开发环境  

>基础服务
1.  安装数据库Mysql
2.  安装缓存Redis
3.  安装Nacos
4.  安装prometheus(监控中间件，非必要安装)
5.  安装grafana(监控面板，非必要安装)  

    - 复制docker/base目录到服务器
    - 切换到该目录  
    - 使用docker/base/docker-compose.yaml一键部署
```shell script
docker-compose -f docker-compose.yml up -d
```
启动完成拓扑图如下：
<img src="./images/tp1.png" alt="基础服务拓扑"/>
>中间服务
1.  安装RocketMQ  
    - 复制docker/RocketMQ到服务器  
    - 切换到该目录  
    - 使用docker/RocketMQ /docker-compose.yaml一键部署
```shell script
docker-compose -f docker-compose.yml up -d
```
启动完成拓扑图如下：
<img src="./images/tp2.png" alt="中间服务拓扑"/>
>应用服务
1.  安装静态页面服务（[请点击打开ch-admin3](https://gitee.com/ch-cloud/ch-admin3)）
2.  安装用户权限服务（[请点击打开ch-upms](https://gitee.com/ch-cloud/ch-upms)）
3.  安装用户登录认证服务（[请点击打开ch-sso](https://gitee.com/ch-cloud/ch-sso)）
4.  安装网关(鉴权、路由)服务（[请点击打开ch-gateway](https://gitee.com/ch-cloud/ch-gateway)）
>扩展服务(非必要安装)
1.  Canal管理服务（[请点击打开canal-admin](https://gitee.com/ch-cloud/canal-admin)）
2.  Kafka管理服务（[请点击打开ch-kafka](https://gitee.com/ch-cloud/ch-kafka)）

### 使用说明
<table>
    <tr>
        <td>登录</td>
        <td>首页</td>
    </tr>
    <tr>
        <td><img src="./images/login.png"/></td>
        <td><img src="./images/home.png"/></td>
    </tr>
    <tr>
        <td>用户管理</td>
        <td>角色管理</td>
    </tr>
    <tr>
        <td><img src="./images/user.png"/></td>
        <td><img src="./images/role.png"/></td>
    </tr>
    <tr>
        <td>权限管理</td>
        <td>组织管理</td>
    </tr>
    <tr>
        <td><img src="./images/permission.png"/></td>
        <td><img src="./images/dept.png"/></td>
    </tr>
    <tr>
        <td>职位管理</td>
        <td>数据字典</td>
    </tr>
	<tr>
        <td><img src="./images/post.png"/></td>
        <td><img src="./images/dict.png"/></td>
    </tr>	
    <tr>
        <td>登录日志</td>
        <td>操作日志</td>
    </tr> 
    <tr>
        <td><img src="./images/login_logs.png"/></td>
        <td><img src="./images/operate_logs.png"/></td>
    </tr>
</table>


