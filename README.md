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


#### 安装教程
基于Docker安装开发环境
1.  安装数据库Mysql
2.  安装缓存Redis
3.  安装Nacos
4.  安装prometheus(监控中间件，非必要的)
5.  安装grafana(监控面板，非必要的)  
基于docker-compose.yaml一键部署
```yaml
version: "3.5"
services:
  nacos:
    image: nacos/nacos-server:latest
    container_name: ch-nacos-2
    env_file:
      - ./env/nacos-standlone-mysql.env
    volumes:
      - ./nacos/logs/:/home/nacos/logs
      - ./init.d/custom.properties:/home/nacos/init.d/custom.properties
    ports:
      - "8848:8848"
      - "9555:9555"
    depends_on:
      - mysql
    restart: on-failure
  mysql:
    container_name: ch-mysql-2
    image: nacos/nacos-mysql:5.7
    env_file:
      - ./env/mysql.env
    volumes:
      - ./mysql/data:/var/lib/mysql
      - ./mysql/conf:/etc/mysql/conf.d
    ports:
      - "3306:3306"
  prometheus:
    container_name: ch-prometheus-2
    image: prom/prometheus:latest
    volumes:
      - ./prometheus/prometheus-standalone.yaml:/etc/prometheus/prometheus.yml
    ports:
      - "9090:9090"
    depends_on:
      - nacos
    restart: on-failure
  grafana:
    container_name: ch-grafana-2
    image: grafana/grafana:latest
    ports:
      - 3000:3000
    restart: on-failure
  redis:
    container_name: ch-redis-2
    image: docker.io/redis:latest
    volumes:
      - ./redis/data:/data
    ports:
      - 6379:6379
    restart: on-failure
```
6.  安装RocketMQ

由于资源不足，不能提供演示环境
#### 使用说明

1.  xxxx
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
