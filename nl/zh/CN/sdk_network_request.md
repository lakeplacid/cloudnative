---

copyright:
  years: 2016, 2017
lastupdated: "2017-04-27"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 发起网络请求
{: #sdk-network-request}

您还可以使用 `BMSCore` SDK 向任何资源发起网络请求。

## Android
{: #request-android}

1. 确保您在 Android 应用程序中已[导入客户机 SDK 并对其进行初始化](/docs/mobile/sdk_BMSClient.html#init-BMSClient-android)。 
	
2. 发起网络请求。

	```Java
	String customResourceURL = "<your resource URL>";
	Request request = new Request(customResourceURL, "GET");

	ResponseListener listener = new ResponseListener() {
		@Override
		public void onSuccess(Response response) {
			Log.i("MyApp", "Response: " + response.getResponseText());
		}

		@Override
		public void onFailure(Response response, Throwable t, JSONObject extendedInfo) {
			Log.i("MyApp", "Request failed. Response: " + response.getResponseText() + ". Error: " + t.getLocalizedMessage());
		}
	};
        
	request.send(getApplicationContext(), listener);
	```
	{: codeblock}

`Request` 类是发起 HTTP 请求的简单方法，在请求完成之后可获得响应。如果您在下载或上传大型文件或数据的大型主体，那么您可以使用 `Request` `download` 或 `upload` 方法。要监视下载或上传的进度，请创建定制 `ProgressListener` 并将其传递给 `download` 或 `upload` 方法。

<!--For complete usage examples, see the `BMSCore` GitHub [README](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-core).-->


## iOS
{: #request-ios}

1. 确保您在 iOS 应用程序中已[导入客户机 SDK 并对其进行初始化](/docs/mobile/sdk_BMSClient.html#init-BMSClient-ios)。

2. 创建网络请求。

	### Swift 3.0
	{: #ios-swift3 notoc}
	
	```Swift
	let customResourceURL = "<your resource URL>"
	let request = Request(url: customResourceURL, method: HttpMethod.GET)
	
	let callBack:BMSCompletionHandler = {(response: Response?, error: Error?) in
		if error == nil {
			print ("Response: \(response?.responseText), no error")
		} else {
			print ("Error: \(error)")
		}
	}
		request.send(completionHandler: callBack)
	```
	{: codeblock}
 
	### Swift 2.2
	{: #ios-swift22 notoc}
	
	```Swift
	let customResourceURL = "<your resource URL>"
	let request = Request(url: customResourceURL, method: HttpMethod.GET)
	
	let callBack:BMSCompletionHandler = {(response: Response?, error: NSError?) in
		if error == nil {
			print ("Response: \(response?.responseText), no error")
		} else {
			print ("Error: \(error)")
		}
	}
		request.send(completionHandler: callBack)
	```
	{: codeblock}

`Request` 类是发起 HTTP 请求的简单方法，在请求完成之后可获得响应。如果想要采用比 `Request` 类更灵活且更具有控制性的方法，您可以使用 `BMSURLSession` 类。`BMSURLSession` 类的部分功能包括监视上传进度以及暂停或取消请求。要获得响应，您可以选择使用完成处理程序或代理。

`BMSURLSession` 类仅可用于 iOS。

有关完整用法示例，请参阅 `BMSCore` GitHub [自述文件](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-core)。


## Cordova
{: #request-cordova}

1. 确保您在 Cordova 应用程序中已[导入客户机 SDK 并对其进行初始化](/docs/mobile/sdk_BMSClient.html#init-BMSClient-cordova)。

2. 创建网络请求。

	```Javascript
	var success = function(data) {
		console.log("success", data);
	}
	var failure = function(error)
		{console.log("failure", error);
	}
	var request = new BMSRequest("<your application route>", BMSRequest.GET);
	request.send(success, failure);
	```
	{: codeblock}

