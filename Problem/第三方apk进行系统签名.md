## 第三方apk进行系统签名

 解决方法：使用自己的Android签名工具给apk重新签名。

    (1) Android的签名文件存放于系统源码的 build/target/product/security/目录下

    
    该目录下有 media.pk8、media.x509.pem、platform.pk8、platform.x509.pem、shared.pk8、shared.x509.pem、testkey.pk8、testkey.x509.pem等签名文件，不同的签名文件，对应不同的权限。Android默认的签名文件为testkey.pk8、testkey.x509.pem。

    (2) Android自带的签名工具为 signapk.jar， 可以在源码编译目录out中找到，具体路径为：out/host/linux-x86/framework/signapk.jar    以上APK具有系统权限，重新签名应该使用platform签名文件进行签名。

    签名方法：将对应权限的签名文件platform.pk8、platform.x509.pem， 签名工具 signapk.jar， 以及需要签名的apk（假设 old.apk） 放到同一目录下，打开linux终端（windows cmd也可以），进入该目录，进行重新签名：

    java -jar signapk.jar platform.x509.pem platform.pk8 old.apk new.apk

    重新生成的new.apk就可以安装在我们的Android设备上了。