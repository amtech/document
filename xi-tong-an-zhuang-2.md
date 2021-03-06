# 系统安装（开源版）

所需软件及版本：

> * MySQL5.5及以上版本；
> * JDK1.8及以上版本；
> * Tomcat8.0.44及以上版本;

睿思BI商业智能系统现已发布开源版，采用Apache2.0 授权协议，对商业友好。本文主要介绍如何从github下载源码并导入eclipse中，并创建数据，通过tomcat访问系统。

1.下载源码：

进入github下载源码，下载地址：[https://github.com/ruisibi/rsbi-pom](https://github.com/ruisibi/rsbi-pom)，点击 Download Zip 下载源码，并解压。

2.导入Eclipse：

在eclipse中点击导入菜单，选择Existing Maven Projects ，点击下一步，选择刚才下载的源码，导入源码到eclipse。

3.编译程序。

系统基于Maven开发，采用Maven编译项目。

4.还原数据\(采用mysql支撑库\)

在 mysql 中创建数据库 rs\_report, 并通过命令把  rs\_report\_data.bak 文件还原到  rs\_report 数据库中，命令如下：

```
mysql -u root -p rs_report<rs_report_data.bak
```

5.修改数据库连接\(采用mysql支持库\)。

数据库连接信息配置在 /rsbi/src/main/resources/application.properties 文件中，修改链接IP，账号密码等信息。

```java
jdbc.driver=com.mysql.jdbc.Driver  
jdbc.url=jdbc:mysql://localhost:3306/rs_report?useUnicode=true&characterEncoding=utf-8&allowMultiQueries=true  
jdbc.username=root  
jdbc.password=123456
```

6.发布到Tomcat并启动。

发布完成后启动tomcat, 在浏览器中输入地址： [http://localhost:8080/rsbi](http://localhost:8080/rsbi) , 如果出现登陆界面既系统配安装成功。

7.常见问题：

启动报错：java.lang.ClassNotFoundException: com.ruisi.ext.engine.control.ExtContextLoaderListener。

这个类在 ext3-1.4.jar 文件，由于启动jar未被发布到lib目录里，解决方法把ext3-1.4.jar添加到发布源，如下图：

![](http://www.ruisibi.cn/document/assets/import124.png)

8.系统目前支持用sqlite做支撑库，sqlite数据库在src/main/resources/rsreport.sqlite3文件中。需要修改src/main/resources/application.properties文件和src/main/webapp/WEB-INF/ext2/ext-config/ext-config.xml文件。

1）application.properties文件增加sqlite配置：

```java
#mysql 
#jdbc.driver=com.mysql.cj.jdbc.Driver
#jdbc.url=jdbc:mysql://localhost:3306/rs_report?useUnicode=true&characterEncoding=utf-8&allowMultiQueries=true&serverTimezone=GMT%2B8
#jdbc.username=root
#jdbc.password=12345678

#sqlite
jdbc.driver=org.sqlite.JDBC
jdbc.url=jdbc:sqlite::resource:rsreport.sqlite3
jdbc.username=
jdbc.password=
```

2）ext-config.xml文件修改dbName配置

```
<constant name="dbName" value="sqlite" />
```



