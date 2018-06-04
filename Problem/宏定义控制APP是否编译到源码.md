
## 宏定义控制APP是否编译到源码

1、将app源码添加到/package/apps/下，Android.mk

![image](https://github.com/luojiawei/Problems/blob/master/image/Android.mk.png)

2、device目录下对应的mk文件中加入这个属性 
BUILD_APP := false

3、在build\target\product目录下mk里面加入PRODUCT_PACKAGES += \ 模块


通过BUILD_APP来控制是否编译app模块，ture为编译，false为不编译