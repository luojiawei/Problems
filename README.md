# 记录平时遇到的问题

## 目录

[1、环境配置问题](#enviroment)

[2、网络开发问题](#network)

[3、对apk进行系统签名](https://github.com/luojiawei/Problems/第三方apk进行系统签名.md)

<span id = "enviroment"></span>
## 1、环境配置问题
#### 1.1  提交的commit没有被统计到contributions

原因：本地配置的邮箱与github配置的不一样。
    
    1.1 怎么看github邮箱：
    
    github->settings->Emails
    
    1.2 怎么看本地配置邮箱：
    
    git log查看提交记录
    
    1.3 怎么将之前的由于提交的是本地配置的邮箱而未显示的contribution显示出来
    
    github->settings->Emails->Add email address增加本地邮箱
    
    1.4 怎么保持本地配置邮箱与github邮箱一致？
    
    git config --global user.name "用户名"
    
    git config --global user.email "邮箱"
    
    
    

#### 1.2 通过github下载的jar

如下载leakcanary jar包：

Getting started

In your build.gradle:

 
```
dependencies {
   compile "org.java-websocket:Java-WebSocket:1.3.6"
 }
```

通过AndroidStudio运行后，jar下载在如下目录：


```
C:\Users\用户名\.gradle\caches\modules-2\files-2.1\org.java-websocket\Java-WebSocket\1.3.6
```

#### 1.3 AS导入工程报错


```
SDK location not found. Define location with sdk.dir in the local.properties file or with an ANDROID_HOME environment variable
```

在环境变量-->系统变量-->新建

变量名：ANDROID_HOME

变量值：E:\AndroidStudio_SDK\sdk

然后在path中添加%ANDROID_HOME%\tools，重启AS即可。


<span id = "network"></span>
## 2、网络开发问题

### 2.1 socket开发 InputStream，BufferedReader的readline收不到数据

原因：

发送的数据没有换行符，readline读取不到结束符

解决方法：

发送的数据后面加上 "\r\n"