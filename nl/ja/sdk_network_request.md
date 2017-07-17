---

copyright:
  years: 2016, 2017
lastupdated: "2017-04-27"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# ネットワーク要求を行う
{: #sdk-network-request}

`BMSCore` SDK を使用して、任意のリソースにネットワーク要求を行うこともできます。

## Android
{: #request-android}

1. Android アプリケーションに [Client SDK をインポートして初期化](/docs/mobile/sdk_BMSClient.html#init-BMSClient-android)しておくようにしてください。 
	
2. ネットワーク要求を行います。

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

`Request` クラスは、HTTP 要求を行い、要求が完了した後に応答を取得するためのシンプルな方法です。サイズの大きいファイルまたは大規模なデータをダウンロードまたはアップロードする場合、`Request` `download` または `upload` メソッドを使用できます。ダウンロードまたはアップロードの進行をモニターするには、カスタム `ProgressListener` を作成し、それを `download` メソッドまたは `upload` メソッドに渡します。

<!--For complete usage examples, see the `BMSCore` GitHub [README](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-core).-->


## iOS
{: #request-ios}

1. iOS アプリケーションに [Client SDK をインポートして初期化](/docs/mobile/sdk_BMSClient.html#init-BMSClient-ios)しておくようにしてください。

2. ネットワーク要求を作成します。

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

`Request` クラスは、HTTP 要求を行い、要求が完了した後に応答を取得するためのシンプルな方法です。`Request` クラスよりも高い柔軟性と制御性が必要な場合は、`BMSURLSession` クラスを使用できます。`BMSURLSession` クラスのフィーチャーとしては、アップロードの進行状態のモニター、および要求の一時停止やキャンセルなどがあります。応答を取得するには、完了ハンドラーか代行のいずれかを選択するというオプションがあります。

`BMSURLSession` クラスは iOS でのみ使用可能です。

使用法の完全な例については、`BMSCore` GitHub [README](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-core) を参照してください。


## Cordova
{: #request-cordova}

1. Cordova アプリケーションに [Client SDK をインポートして初期化](/docs/mobile/sdk_BMSClient.html#init-BMSClient-cordova)しておくようにしてください。

2. ネットワーク要求を作成します。

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

