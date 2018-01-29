---

copyright:
  years: 2017
lastupdated: "2017-11-02"

---
{:new_window: target="_blank"}  
{:shortdesc: .shortdesc}  
{:screen: .screen}  
{:codeblock: .codeblock}  
{:pre: .pre}  

# {{site.data.keyword.dev_cli_short}}
{: #developercli}	

Das {{site.data.keyword.dev_cli_long}} bietet ein erweiterbares befehlsgesteuertes Konzept zum Erstellen, Entwickeln und Bereitstellen eines Webprojekts im Plug-in `dev`. Es ist ideal für Entwickler, die für die Entwicklung von End-to-End-Microservice-Anwendungen die Befehlszeilensteuerung verwenden möchten.

{: shortdesc}

Vom {{site.data.keyword.dev_cli_notm}} werden zwei Container zum leichteren Erstellen und Testen der Anwendung verwendet. Der erste ist der Container mit den Tools, in dem die erforderlichen Dienstprogramme zum Erstellen und Testen der Anwendung enthalten sind. Die Dockerfile für diesen Container wird durch den Parameter [`dockerfile-tools`](#command-parameters) definiert. Er kann als Entwicklungscontainer angesehen werden, da er die Tools enthält, die normalerweise für Entwicklung einer bestimmten Laufzeit nützlich sind.

Der zweite Container ist der Ausführungscontainer. Dieser Container ist so konzipiert, dass er sich zur Bereitstellung für die Verwendung eignet, zum Beispiel in {{site.data.keyword.Bluemix}}. Aus diesem Grund wird ein Einstiegspunkt definiert, über den die Anwendung gestartet wird. Wenn Sie auswählen, dass die Anwendung über die {{site.data.keyword.dev_cli_short}} gestartet werden soll, wird hierfür dieser Container verwendet. Die Dockerfile für diesen Container wird durch den Parameter [`dockerfile-run`](#run-parameters) definiert.


## Ein {{site.data.keyword.dev_cli_notm}} hinzufügen
{: #add-cli}


### Voraussetzungen
{: #prereq}

Sie müssen bestimmte Voraussetzungen erfüllen, um das gesamte Funktionsspektrum des {{site.data.keyword.dev_cli_short}}s kennenzulernen und optimal nutzen zu können, da es in hohem Maße erweiterbar ist und die Nutzung weiterer ergänzender Technologien ermöglicht. 

<!--1. Install the [Cloud Foundry CLI ![External link icon](../icons/launch-glyph.svg "External link icon")](https://github.com/cloudfoundry/cli#getting-started "External link icon").-->

1. Installieren Sie die [{{site.data.keyword.Bluemix}} CLI ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](http://clis.ng.bluemix.net/ui/home.html "Symbol für externen Link").

2. Rufen Sie eine [{{site.data.keyword.Bluemix_notm}}](https://www.bluemix.net)-ID ab.

3. Wenn Sie beabsichtigen, Anwendungen lokal auszuführen und lokal für sie eine Fehlerbehebung auszuführen, müssen Sie auch [Docker ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](https://www.docker.com/get-docker "Symbol für externen Link") installieren.


### Vorbereitende Schritte
{: #before-install}

1. Stellen Sie eine Verbindung zu einem API-Endpunkt in Ihrer [{{site.data.keyword.Bluemix_notm}}-Region her](/docs/overview/whatisbluemix.html#ov_intro_reg). Beispiel: Geben sie den folgenden Befehl ein, um eine Verbindung zu der {{site.data.keyword.Bluemix_notm}}-Region 'USA - Süden' herzustellen:

	```
	bx api https://api.ng.bluemix.net
	```
	{: codeblock}
	
2. Melden Sie sich bei {{site.data.keyword.Bluemix_notm}} an und geben Sie Ihre IBMid und das entsprechende Kennwort an:

	```
	bx login
	```
	{: codeblock}
	
	**Hinweis:** Wenn Ihre Berechtigungsnachweise abgelehnt werden, kann es sein, dass Sie eine föderierte ID verwenden. Führen Sie die folgenden Schritte aus, um sich mit einer föderierten ID zu authentifizieren.
	
	<!-- 
	POINT TO IBM Cloud CLI LOG IN DOCUMENTATION !!!
	
	This link does not work in production yet --> 
	
	1. Melden Sie sich an [{{site.data.keyword.iamshort}} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](https://www.bluemix.net/iam/#/apikeys "Symbol für externen Link"){: new_window} an.
	2. Wählen Sie **API-Schlüssel erstellen** aus.
		* Geben Sie einen Namen und eine Beschreibung für den API-Schlüssel ein.
	3. Laden Sie den API-Schlüssel herunter.
	4. Öffnen Sie die Datei und kopieren Sie den Wert aus dem Feld `apiKey`.
	5. Melden Sie sich unter Verwendung des folgenden Befehls an:
	 
		```
		bx login --apikey <value>
		```
		{: codeblock}


### Installieren
{: #installation}

1. Installieren Sie die [{{site.data.keyword.dev_cli_short}} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](/docs/cli/reference/bluemix_cli/index.html#install_plug-in "Symbol für externen Link"){: new_window} durch Ausführen des folgenden Befehls:
 
	```
	bx plugin install dev
	```
	{: codeblock}

2. 	Überprüfen Sie durch die Ausführung des folgenden Befehls, ob die Installation des Plug-ins erfolgreich war:   
 
	```
	bx dev
	```
	{: codeblock}


