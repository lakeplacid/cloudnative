---

copyright:
  years: 2016, 2017
lastupdated: "2017-04-27"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}

# Netzanforderung erstellen
{: #sdk-network-request}

Sie können auch das `BMSCore`-SDK zum Erstellen von Netzanforderungen an beliebige Ressourcen verwenden.

## Android
{: #request-android}

1. Stellen Sie sicher, dass Sie in Ihrer Android-Anwendung [das Client-SDK importiert und initialisiert haben](/docs/mobile/sdk_BMSClient.html#init-BMSClient-android). 
	
2. Erstellen Sie eine Netzanforderung.

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

Die Klasse `Request` ist eine einfache Möglichkeit zum Erstellen einer HTTP-Anforderung und zum Erhalten der Antwort nach der Durchführung der Anforderung. Wenn Sie große Dateien oder Datenvolumen hoch- oder herunterladen, dann können Sie die Methode `Request` `download` oder `upload` verwenden. Zur Überwachung des Fortschritts des Up- oder Downloads erstellen Sie ein angepasstes Element `ProgressListener` und übergeben es an die Methode `download` oder `upload`. 

<!--For complete usage examples, see the `BMSCore` GitHub [README](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-android-core).-->


## iOS
{: #request-ios}

1. Stellen Sie sicher, dass Sie in Ihrer iOS-Anwendung [das Client-SDK importiert und initialisiert haben](/docs/mobile/sdk_BMSClient.html#init-BMSClient-ios).

2. Erstellen Sie eine Netzanforderung.

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

Die Klasse `Request` ist eine einfache Möglichkeit zum Erstellen einer HTTP-Anforderung und zum Erhalten der Antwort nach der Durchführung der Anforderung. Wenn Sie größere Flexibilität und mehr Steuerungsmöglichkeiten wünschen als mit der Klasse `Request`, können Sie die Klasse `BMSURLSession` verwenden. Funktionen der Klasse `BMSURLSession` sind unter anderem das Überwachen des Verarbeitungsfortschritts beim Hochladen und das Anhalten oder Abbrechen von Anforderungen. Um die Antworten zu erhalten, können Sie entweder Completion-Handler oder Delegierte (Delegates) auswählen.

Die Klasse `BMSURLSession` ist nur für iOS verfügbar.

Die Verwendungsbeispiele finden Sie alle in der [README](https://github.com/ibm-bluemix-mobile-services/bms-clientsdk-swift-core) für `BMSCore` GitHub.


## Cordova
{: #request-cordova}

1. Stellen Sie sicher, dass Sie in Ihrer Cordova-Anwendung [das Client-SDK importiert und initialisiert haben](/docs/mobile/sdk_BMSClient.html#init-BMSClient-cordova).

2. Erstellen Sie eine Netzanforderung.

	```Javascript
	var success = function(data) {
		console.log("success", data);
	}
	var failure = function(error)
		{console.log("failure", error);
	}
	var request = new BMSRequest("<Ihre_anwendungsroute>", BMSRequest.GET);
	request.send(success, failure);
	```
	{: codeblock}

