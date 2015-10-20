---
layout: post
title:  "在线移动支付"
date:   2015-09-28 14:27:54
categories: random
---

## 支付宝移动支付

SDK下载地址：[LINK](https://b.alipay.com/order/productDetail.htm?productId=2014110308141993)

### 下载相关文件

```
WS_MOBILE_PAY_SDK_BASE.zip
|--即时到账批量退款有密接口-refund_fastpay_by_platform_pwd(20150825)
|--商户接入支付宝收银台界面展示标准-无线
`--支付宝钱包支付接口开发包2.0标准版(20150917)
```

### 具体步骤

1. 拷贝`alipaySDK-20150818.jar`到自己的libs目录
1. res资源拷贝，`string.xml`因为就一个app_name的字符串，所以不用拷贝
1. java源码拷贝自己包名下
1. AndroidManifest.xml添加需要的Activity，`H5PayActivity`
1. 混淆文件中的内容添加`proguard-project.txt`
1. 填上去支付的几个静态常量，`PARTNER、SELLER、RSA_PRIVATE、RSA_PUBLIC`
1. 自己定制其他内容

## 微信支付

资源中心：[LINK](https://open.weixin.qq.com/cgi-bin/showdocument?action=dir_list&t=resource/res_list&verify=1&lang=zh_CN)

```
新版本DEMO，使用AS编写，最后替换新版本的libammsdk.jar
Android2_SDK238f8d.zip
|--doc
`--libs
    `--libammsdk.jar

wechat_sdk_sample_android_v3_pay.zip
`--wx_pay
```

```
老版本DEMO，提供的不交完整，但是都是14年写好的老DEMO
app_wx_pay_tool_android1d902c.zip
|--【微信APP支付】Sample_For_Android
|--【微信APP支付】SDK_For_Android
|--【微信APP支付】服务端demo
|--【微信支付】退款及对账demo
|--【微信APP支付】接口文档V1.2_For_Android.pdf
`--【微信支付】退款及对账开发指南.pdf
```

### 具体步骤

拷贝java源代码到自己项目目录，假设自己程序的包名为`com.ianonymous.weixin`

1. WXPayEntryActivity必须在wxapi目录下，可以这样子放，例：`com.ianonymous.weixin.wxapi`目录
1. Demo页面PayActivity也可以先拷贝过来到com.ianonymous.weixin
1. net.sourceforge.simcpux直接全部拷贝到java目录
1. res目录资源拷贝过来，为了避免合并问题，values目录下的文件可以都加一下前缀`wxpay_`
1. AndroidManifest.xml添加需要的Activity，`PayActivity、WXPayEntryActivity、AppRegister`
1. 最后注意如果你使用6.0以上Android的SDK的话，因为android6.0 SDK中删除HttpClient的相关类，解决方法是在项目主build.gradle的android标签下添加useLibrary 'org.apache.http.legacy'

```
android {
    useLibrary 'org.apache.http.legacy'
}
```
之后都可以定制了
