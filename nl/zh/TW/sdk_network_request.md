---

copyright:
  years: 2016, 2017
lastupdated: "2017-04-27"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# 提出網路要求
{: #sdk-network-request}

您也可以使用 `BMSCore` SDK 對任何資源提出網路要求。

## Android
{: #request-android}

1. 確定您已在 Android 應用程式中[匯入用戶端 SDK 並起始設定它](/docs/mobile/sdk_BMSClient.html#init-BMSClient-android)。 
	
2. 提出網路要求。

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

`Request` 類別是提出 HTTP 要求並在要求完成後取得回應的簡單方法。如果您正在下載或上傳大型檔案，或大量的資料，可以使用 `Request` `download` 或 `upload` 方法。若要監視下載或上傳的進度，請建立自訂的 `ProgressListener`，並將它傳遞給 `download` 或 `upload` 方法。

<!--For complete usage examples, see the `BMSCore` GitHub [README](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-core).-->


## iOS
{: #request-ios}

1. 確定您已在 iOS 應用程式中[匯入用戶端 SDK 並起始設定它](/docs/mobile/sdk_BMSClient.html#init-BMSClient-ios)。

2. 建立網路要求。

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

`Request` 類別是提出 HTTP 要求並在要求完成後取得回應的簡單方法。如果您想要得到比 `Request` 類別更多的彈性與控制，可以使用 `BMSURLSession` 類別。`BMSURLSession` 類別部分特性包括監視上傳的進度，以及暫停或取消要求。若要取得回應，您可以選擇完成處理程式或委派。

`BMSURLSession` 類別僅適用於 iOS。

如需完整的使用範例，請參閱 `BMSCore` GitHub [README](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-core)。


## Cordova
{: #request-cordova}

1. 確定您已在 Cordova 應用程式中[匯入用戶端 SDK 並起始設定它](/docs/mobile/sdk_BMSClient.html#init-BMSClient-cordova)。

2. 建立網路要求。

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

