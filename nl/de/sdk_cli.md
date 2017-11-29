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

# SDK Generator-Plug-in
{: #sdk-cli}

Das {{site.data.keyword.IBM}} SDK Generator-Plug-in kann in der [{{site.data.keyword.Bluemix_notm}}-CLI ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](/docs/cli/reference/bluemix_cli/index.html "Symbol für externen Link") installiert werden. 

Als Entwickler unter {{site.data.keyword.Bluemix_notm}} können Sie dieses Plug-in verwenden, um SDKs auf Basis der mit der [Open API-Spezifikation ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](https://www.openapis.org/ "Symbol für externen Link") konformen REST-API-Definition zu generieren. Wenn Sie Änderungen an der REST-API-Definition vornehmen, dann können Sie dieses Plug-in verwenden, um nur das SDK und nicht das gesamte Projekt neu zu generieren.

Außerdem können Sie ersehen, ob Ihre Cloud Foundry-Apps in einem bestimmten Bereich über REST-API-Definitionen verfügen, die für die SDK-Generierung gültig sind. Abschließend können Sie das {{site.data.keyword.IBM_notm}} SDK Generator-Plug-in verwenden, um alle REST-API-Definitionen zu überprüfen und um sicherzustellen, dass sie mit den SDK Generator-Anforderungen übereinstimmen.

Dieses {{site.data.keyword.IBM_notm}} SDK Generator-Plug-in ermöglicht Ihnen die einfache Integration der Back-End-Services für Ihre App mit einem generierten SDK. Wenn eine Änderung an einer REST-API auftritt, dann können Sie das SDK neu generieren und das alte SDK zur reibungslosen Durchführung des SDK-Upgrades ersetzen. Außerdem können Sie die CLI in eine DevOps-Pipeline integrieren und so sicherstellen, dass das SDK immer mit der API-Spezifikation übereinstimmt, wenn die App erstellt wird.

Die REST-API-Definition muss gültig sein und entweder auf einem Live-Serverendpunkt gehostet oder in einer lokalen Datei auf Ihrem System vorhanden sein. Wenn die REST-API-Definition gehostet wird, dann muss die relative URL in der Umgebungsvariablen `OPENAPI_SPEC` definiert sein.


## Voraussetzungen
{: #prereqs}

Vergewissern Sie sich, dass die folgenden Anforderungen erfüllt sind.

* Sie verfügen über ein [{{site.data.keyword.Bluemix_notm}}![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](http://bluemix.net "Symbol für externen Link")-Konto. 
* Sie verfügen über eine gültige API-Definition, die der [Open API![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](https://www.openapis.org/ "Symbol für externen Link")-Spezifikation entspricht. 


## Installation
{: #installation}

1. [Installieren Sie die {{site.data.keyword.Bluemix}}-CLI ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](http://clis.ng.bluemix.net/ui/home.html "Symbol für externen Link"). 

2. [Installieren Sie das Plug-in ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](/docs/cli/reference/bluemix_cli/index.html#install_plug-in "Symbol für externen Link"). 

	```
	bx plugin install sdk-gen
	```
	{: codeblock}


## Befehle
{: #commands}

Verwenden Sie die folgenden Befehle, um ein SDK zu generieren, die Open API-Definitionsdateien zu überprüfen oder die Cloud Foundry-Apps aufzulisten.


### SDK generieren
{: #gen}

Verwenden Sie `bx sdk generate [arguments...] [command options]`.


#### Argumente
{: #gen-args}

* `APP_NAME` - Der Name der Cloud Foundry-App in Ihrem aktuellen Bereich.
* `OPENAPI_DOC_LOCATION` - Eine URL oder ein relativer Dateipfad zur JSON- oder Yaml-Komponente der unaufbereiteten REST-API-Definition.
* `GENERATED_SDK_NAME` (optional) - Der Name des generierten SDK.


#### Optionen
{: #gen-options}

* `PLATFORM` (erforderlich)
   * `--android` - Generiert ein Android-SDK.
   * `--ios` - Generiert ein iOS Swift-SDK
   * `--swift` - Generiert ein Swift-Server-SDK
   * `--js` - Generiert ein JavaScript-SDK
* `LOCATION` (erforderlich) - Gibt den Typ für `OPENAPI_DOC_LOCATION` an
   * `-r` - Remote URL
   * `-f` - Datei
   * `-a` - App, die unter {{site.data.keyword.Bluemix_notm}} ausgeführt wird
   * `-l` - URL des lokalen Hosts (localhost)
* `--output "YOUR_RELATIVE_PATH"` (optional) - Platziert das generierte SDK in dem Verzeichnis, das in `YOUR_RELATIVE_PATH` angegeben wird (bereits vorhandene SDKs werden dabei überschrieben).
* `--unzip` (optional) - Extrahiert das generierte SDK (bereits vorhandene SDK-Artefakte werden dabei überschrieben).


#### Syntax
{: #gen-usage}

Zum Generieren eines SDK auf Basis einer Cloud Foundry-App, die unter {{site.data.keyword.Bluemix_notm}} ausgeführt wird, können Sie den Namen der App als Parameter für die CLI verwenden. Im folgenden Befehl wird der Name der App im Parameter `SDK_Name` benutzt.

```
bx sdk generate [APP_NAME] [LOCATION] [PLATFORM]
```
{: codeblock}

Zum Generieren eines SDK auf Basis einer URL zu einer Open API-Definitionsdatei oder einer lokalen JSON- oder Yaml-Datei verwenden Sie den folgenden Befehl.

```
bx sdk generate [OPENAPI_DOC_LOCATION] [SDK_Name] [LOCATION] [PLATFORM]
```
{: codeblock}


### Open API-Definitionen überprüfen
{: #validating}

Verwenden Sie `bx sdk validate [argument]`.


#### Argumente
{: #val-args}

* `APP_NAME` - Der Name der Cloud Foundry-App in Ihrem aktuellen Bereich.
* `OPENAPI_DOC_LOCATION` - Eine URL oder ein relativer Dateipfad zur JSON- oder Yaml-Komponente der unaufbereiteten REST-API-Definition.


#### Syntax
{: #val-usage}

Zum Überprüfen der API-Spezifikation einer Cloud Foundry-App, die unter {{site.data.keyword.Bluemix_notm}} ausgeführt wird, können Sie den Namen der App als Parameter für die CLI verwenden.

```
bx sdk validate [APP_NAME] [LOCATION]
```
{: codeblock}

Zum Überprüfen eines SDK auf Basis der URL zu einem Dokument mit API-Spezifikationen oder einer lokalen JSON- oder Yaml-Datei verwenden Sie den folgenden Befehl.

```
bx sdk validate [OPENAPI_DOC_LOCATION] [LOCATION]
```
{: codeblock}



### Apps (Cloud Foundry) auflisten
{: #list-apps}

Verwenden Sie `bx sdk list [argument] [option]`, um Apps aufzulisten und API-Spezifikationen zu überprüfen. In der Umgebungsvariablen `OPENAPI_SPEC` muss der relative URL-Pfad angegeben werden, über den Ihre Spezifikation gehostet wird.


#### Argumente
{: #list-args}

* `SPACE_NAME` (optional) - Der Name des Cloud Foundry-Bereichs in Ihrer aktuellen Organisation, der nach Apps durchsucht werden soll. Wird hier nichts angegeben, dann durchsucht das System den aktuellen Bereich.


#### Optionen
{: #list-options}

* `--url` (optional) - Zeigt eine vollständig formatierte URL zur Open API-Definition jeder App in der Liste an.


#### Syntax
{: #list-usage}

Verwenden Sie den folgenden Befehl, um Apps im aktuellen Bereich aufzulisten.

```
bx sdk list
```
{: codeblock}

Verwenden Sie den folgenden Befehl, um Apps im aktuellen Bereich aufzulisten und die URL zur API-Spezifikation anzuzeigen.

```
bx sdk list --url
```
{: codeblock}

Verwenden Sie den folgenden Befehl, um Apps in einem bestimmten Bereich aufzulisten.

```
bx sdk list [SPACE_NAME]
```
{: codeblock}

Verwenden Sie den folgenden Befehl, um Apps in einem bestimmten Bereich aufzulisten und die URL der API-Spezifikation anzuzeigen.

```
bx sdk list [SPACE_NAME] --url
```
{: codeblock}
