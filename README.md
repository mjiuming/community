# 不挂高数社区（名字可以随便改的）

## 参考项目

[mawen 社区](http://www.mawen.co)

[community](https://github.com/codedrinker/community)

## 介绍

目前还是MVC模式，开发完成后可能会考虑前后端分离


已完成登陆注册,发帖，回复评论，点赞，markdown编辑，消息通知，图片上传,个人界信息编辑，热门话题，问题与用户的搜索，热门帖子与话题,以及后台管理（在主页输入url /admin 进入）设置首页置顶问题

部分权限验证

待完成文件上传，找回密码，删除未使用图片

后端使用 Spring boot 和  mybatis 开发

密码加密采用 Spring Security 的 Bcrypt 加密

页面模板使用 Thymeleaf

前端页面设计使用 BootStrap4 

热门话题与热门问题每一小时更新一次

每两小时处理一次离线用户

每六小时同步一次管理数据


## 快速运行

你可以选择到releases中下载直接运行或这自己打包。

不管怎样，你都需要先使用 database.sql 脚本创建数据库

与配置 application.yml

以下为打包方法

环境准备

Java版本： Java 8 及以上

maven: 3

数据库： MySQL 或者 MariaDB 或者 H2 （使用H2数据库需要在pom文件中添加H5依赖）

```xml
        <dependency>
            <groupId>com.h2database</groupId>
            <artifactId>h2</artifactId>
            <version>1.4.199</version>
        </dependency>
```
使用 database.sql 脚本创建数据库
配置 application.properties

运行打包命令
```bash
mvn clena package
```
运行项目
```bash
java -jar community-0.0.1-SNAPSHOT.jar
```
即可

**注意：第一个管理员账号需要在创建完数据库运行项目注册第一个账户后，手动将数据库的权限表power列数据该为0**

**第一次运行如果没有修改配置文件中上传图片保存路径与日志路径的化，系统会默认在程序运行的目录下创建file文件夹和log文件夹，分别保存图片文件和日志文件！**

也可以在 IDEA 中导入此项目，如果 getter 和 setter 飘红，则需要安装 IDEA 得到 Lombok 插件

## 页面展示

(ps：如果图片不显示，请到images文件夹下查看)

主页

![主页](https://github.com/PuZhiweizuishuai/community/blob/master/images/home.jpg "主页")

用户首页

![用户首页](https://github.com/PuZhiweizuishuai/community/blob/master/images/userHome.jpg "用户首页")

用户信息修改页

![用户信息修改页](https://github.com/PuZhiweizuishuai/community/blob/master/images/userchange.jpg "用户信息修改页")


问题展示页

![](https://github.com/PuZhiweizuishuai/community/blob/master/images/questionPage.jpg)

![](https://github.com/PuZhiweizuishuai/community/blob/master/images/questionPage2.jpg)

![](https://github.com/PuZhiweizuishuai/community/blob/master/images/questionPage3.jpg)

消息提醒页

![](https://github.com/PuZhiweizuishuai/community/blob/master/images/message.jpg)

管理员页面

![](https://github.com/PuZhiweizuishuai/community/blob/master/images/adminPage.jpg)

![](https://github.com/PuZhiweizuishuai/community/blob/master/images/adminPage%20(2).jpg)

![](https://github.com/PuZhiweizuishuai/community/blob/master/images/adminPage%20(3).jpg)


## 资料
[spring 入门指南](https://spring.io/guides)

[spring boot 日志](https://docs.spring.io/spring-boot/docs/current/reference/html/boot-features-logging.html)

[spring thymeleafk快速指南](https://spring.io/guides/gs/serving-web-content/)

[mybatis 文档](http://www.mybatis.org/mybatis-3/zh/index.html)

[mybatis-spring-boot-autoconfigure](http://www.mybatis.org/spring-boot-starter/mybatis-spring-boot-autoconfigure/)

[Java web开发基础](http://jinxuliang.com/course/CoursePortal/Details/5a9268a9a664d72f041e0a6a)

[BootStrap4 中文文档](http://bs4.ntp.org.cn/)

[spring-session-jdbc](https://docs.spring.io/spring-session/docs/current/reference/html5/guides/boot-jdbc.html)

## 工具
在线 markdown 编辑器 [markdown edit](https://pandao.github.io/editor.md/)

JavaScript剪裁图片工具 [cropperjs](https://github.com/fengyuanchen/cropperjs)

JavaScript定位引擎 [popper.js](https://github.com/FezVrasta/popper.js)

BootStrap 日历选择插件 [Tempus Dominus](https://tempusdominus.github.io/bootstrap-4/)

节省多余的Java代码 [Lombok](https://www.projectlombok.org)

后端生成验证码的工具包 [EasyCaptcha 验证码](https://github.com/whvcse/EasyCaptcha)
注意：此工具和kaptcha有一样的问题，使用的Random方法有不安全，[CVE-2018-18531](http://www.cnnvd.org.cn/web/xxk/ldxqById.tag?CNNVD=CNNVD-201810-1111)对安全性要求较高的，建议下载源码后将Random方法更改为SecureRandom

更新：最新版修复了这个问题

JWT验证工具 [JJWT Java JWT](https://github.com/jwtk/jjwt)

## 代码文件结构

cache 缓存

component 组件

config 自定义配置

controller 控制层

dto DAO层负责页面与后端程序的数据传输

enums 各种数据的类型

exception 异常处理

interceptor 过滤器

mapper 数据库映射

model 定义数据库和后端程序的数据交换类型

schedule 定时任务

service 服务层

util 各种工具

## 更新日志

#### 2019-09-25跟新

添加问题点赞功能，待完成评论点赞

暂时移除 spring-session-jdbc 等待修复添加 spring-session-jdbc 后造成的登陆序列化异常 BUG

#### 2019-09-22更新

添加 spring-session-jdbc，修改配置文件为 yml，删除不必要的包
