# 记录github遇到的问题
1.提交的commit没有被统计到contributions

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
    
    
    

2.通过github下载的jar

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

