# 只修改17行代码，分分钟将alexa音箱转换成dumi音箱




### 安装alexa

 1. 点击[链接](https://github.com/alexa/alexa-avs-sample-app/wiki)，按照文档中的流程安装alexa-avs-sample-app到你的机器上，支持Raspberry Pi, Mac, Linux，Windows.
 2. 如果你觉得申请amazon的应用app很麻烦，可以使用如下测试app的信息：
			
		ProductID=cyluo_device
		ClientID=amzn1.application-oa2-client.844ac72014f14f939dc117eb38dfb6e1
		ClientSecret=362d959a12b413e74bd88329fd19a5fb05d49c5491345e46f5c5d9326bcad855

 3. samples/companionService/ 目录下 运行npm start,  samples/javaclient/目录下运行 mvn exec:exec，待alexa启动并跳转到amazon的登录页面，登录成功后，尝试和alexa说上几句话: 

		 what's your name ?   what's the weather today? 。（建议在翻墙后的网络环境下使用)


### 只修改17行代码，分分钟将alexa变成dumi

 - 修改samples/companionService/config.js中的帐号登录信息（4行)：
```html
var config = {
-    clientId: "amzn1.application-oa2-client.844ac72014f14f939dc117eb38dfb6e1",
-    clientSecret: "362d959a12b413e74bd88329fd19a5fb05d49c5491345e46f5c5d9326bcad855",
+    clientId: '5M7GhhTnfh7AjVTq37yxD3Cy',
+    clientSecret: 'YvRy2VHmnSzBCEQqc3fi3jIfKrZktSa6',
     redirectUrl: 'https://localhost:3000/authresponse',
-    lwaRedirectHost: "amazon.com",
-    lwaApiHost: "api.amazon.com",
+    lwaRedirectHost: 'openapi.baidu.com',
+    lwaApiHost: 'openapi.baidu.com',
```
 - 修改samples/javaclient/config.json （2行)
```html
-    "avsHost":"https://avs-alexa-na.amazon.com",
+    "avsHost":"https://dueros-h2.baidu.com",
     "companionApp":{
         "localPort":8443,
-        "lwaUrl":"https://api.amazon.com",
+        "lwaUrl":"https://openapi.baidu.com",
```

- 下载[patch](https://github.com/cyluo/dumi/blob/master/patch)文件，在alexa的根目录下运行git apply patch。（10行）
- 建议参照[amazon链接](https://github.com/alexa/alexa-avs-sample-app/wiki/Sample-App-Log-Out-Instructions)清除amazon的登录信息。
- 在samples/javaclient/ 目录下，运行mvn install 重新编译app。samples/companionService/ 目录下 运行npm start,  samples/javaclient/目录下运行 mvn exec:exec，启动并跳转到baidu登录页面，登录成功后，尝试和dumi说上几句话吧:  
		
		你叫什么名字？  今天天气如何？ 我想听一首歌。
### 参考链接
1，alexa-avs-sample-app：https://github.com/alexa/alexa-avs-sample-app/wiki

2,  Sample App Log Out Instructions:  https://github.com/alexa/alexa-avs-sample-app/wiki/Sample-App-Log-Out-Instructions
