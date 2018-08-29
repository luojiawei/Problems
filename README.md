# 记录平时遇到的问题

## 目录

[1、环境配置问题](#enviroment)

[2、网络开发问题](#network)

[3、对apk进行系统签名](https://github.com/luojiawei/Problems/blob/master/Problem/%E7%AC%AC%E4%B8%89%E6%96%B9apk%E8%BF%9B%E8%A1%8C%E7%B3%BB%E7%BB%9F%E7%AD%BE%E5%90%8D.md)

[4、宏定义控制APP是否编译到源码](https://github.com/luojiawei/Problems/blob/master/Problem/宏定义控制APP是否编译到源码.md)

[5、NDK开发总结(捕获异常)](https://www.cnblogs.com/zhangyan-2015/p/5865536.html)

[6、Android 编译命令 make j8 2>&1 | tee build.log 解释](https://www.cnblogs.com/ifzy/p/3854560.html)

[7、反编译操作步骤和工具](https://github.com/luojiawei/Problems/blob/master/Problem/反编译操作步骤和工具/反编译操作步骤和工具.md)

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

#### 1.4 which is not in the whitelist

Android6.0在frameworks/base/core/java/com 增加代码编译报错 ==unknown package name of class file==

Android8.1在frameworks/base/core/java/com 增加代码编译报错 ==which is not in the whitelist==


在build/core/tasks/check_boot_jars/check_boot_jars.py的python脚本会对包进行校验。

解决措施：
在build\core\tasks\check_boot_jars\package_whitelist.txt增加对应的包名


```
# framework.jar
javax\.microedition\.khronos\.opengles
javax\.microedition\.khronos\.egl
```


[参考链接](https://blog.csdn.net/pq5357/article/details/80660699/)




<span id = "network"></span>
## 2、网络开发问题

### 2.1 socket开发 InputStream，BufferedReader的readline收不到数据

原因：

发送的数据没有换行符，readline读取不到结束符

解决方法：

发送的数据后面加上 "\r\n"