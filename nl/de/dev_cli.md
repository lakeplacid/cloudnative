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


## Befehle
{: #commands}

Verwenden Sie die folgenden Befehle, um ein Projekt zu erstellen, es bereitzustellen, eine Fehlerbehebung dafür auszuführen und es zu testen.

### Erstellen
{: #build}

Sie können eine Anwendung mit dem Befehl `build` erstellen. Das Konfigurationselement `build-cmd-run` wird zum Erstellen der Anwendung verwendet. Bei den Befehlen `test`, `debug` und `run` wird erwartet, dass ein kompiliertes Projekt vorhanden ist. Aus diesem Grund müssen Sie zuerst mindestens eine Erstellungsoperation (Build) durchführen. 

Führen Sie den folgenden Befehl im aktuellen Projektverzeichnis aus, um die Anwendung zu erstellen:  

```
bx dev build
```
{: codeblock}


[Befehlsparameter erstellen](#command-parameters)


### Code
{: #code}

Mit dem Befehl `code` können Sie nach der Bereitstellung Anwendungscode herunterladen, sodass Sie ihn lokal überprüfen oder ändern können.

Führen Sie den folgenden Befehl aus, um den Code von einem angegebenen Projekt herunterzuladen.

```
bx dev code <projectName>
```
{: codeblock}


### Erstellen
{: #create}

Erstellen Sie ein Projekt mit der Aufforderung zur Angabe aller Informationen einschließlich Sprache, Projektname und Appmustertyp. Das Projekt wird im aktuellen Verzeichnis erstellt. 

Führen Sie den folgenden Befehl aus, um ein Projekt im aktuellen Projektverzeichnis zu erstellen und ihm Services zuzuordnen:

```
bx dev create
```
{: codeblock}


### Debuggen
{: #debug}

Sie können eine Anwendung mit dem Befehl `debug` debuggen. Zunächst muss für das Projekt jedoch mithilfe des Erstellungsbefehls eine Erstellung (Build) ausgeführt werden. Wird der Befehl `debug` aufgerufen, dann startet das System einen Container, der auf Basis des Werts für `container-port-map-debug` mindestens einen Debug-Port bereitstellt. Verbinden Sie Ihr bevorzugtes Debugging-Tool mit dem Port bzw. den Ports; danach können Sie wie gewohnt Debugging für die Anwendung ausführen.

**Einschränkung:** Für Swift-Projekte kann kein Debugging durchgeführt werden.

Zunächst müssen Sie Ihr Projekt kompilieren:

```
bx dev build
```
{: codeblock}

Führen Sie den folgenden Befehl im aktuellen Projektverzeichnis aus, um die Anwendung zu debuggen:

```
bx dev debug
```
{: codeblock}	

Verwenden Sie zum Beenden der Debugsitzung `CTRL-C`.


#### Debugbefehlsparameter
{: #debug-parameters}

Die folgenden Parameter werden ausschließlich mit dem Befehl `debug` verwendet und dienen als Unterstützung beim Debugging einer Anwendung.

##### `container-port-map-debug`
{: #port-map-debug}

* Portzuordnungen für den Debugging-Port. Der erste Wert ist der Port, der im Hostbetriebssystem verwendet werden soll, der zweite ist der Port im Container [host-port:container-port].
* Syntax: `bx dev debug --container-port-map-debug [7777:7777]`

##### `build-cmd-debug`
{: #build-cmd-debug}

* Parameter, der zum Erstellen des Codes für DEBUG verwendet wird. 
* Syntax: `bx dev debug --build-cmd-debug build.command.sh`

##### `debug-cmd`
{: #debug-cmd}

* Parameter, der zur Angabe eines Befehls verwendet wird, mit dem die Debugfunktion im Container mit den Tools aufgerufen wird. Verwenden Sie diesen Parameter, falls
`build-cmd-debug` Ihre Anwendung im Debugmodus startet. 
* Syntax: `bx dev debug --debug-cmd /the/debug/command`

#### Debuggen einer lokalen Anwendung:
{: #local-app-dev}

Weitere Informationen zum Debuggen einer lokalen Anwendung finden Sie unter [Debuggen einer lokalen Anwendung](docs/cloudnative/dev_cli_local_debug.html#local-debug).


### Löschen
{: #delete}

Verwenden Sie den Befehl `delete`, um Projekte aus dem {{site.data.keyword.Bluemix}}-Bereich zu löschen. Sie können den Befehl ohne Parameter ausführen, um zum Löschen verfügbare Projekte aufzulisten. Projektcode und Verzeichnisse werden nicht aus dem lokalen Festplattenspeicher entfernt.

Führen Sie den folgenden Befehl aus, um ein Projekt in {{site.data.keyword.Bluemix}} zu löschen:

```
bx dev delete <projectName>
```
{: codeblock}
 

**Hinweis:** {{site.data.keyword.Bluemix}}-Services werden **nicht** entfernt.


### Bereitstellen
{: #deploy}

Sie können eine Anwendung durch Eingabe des Befehls `deploy` mit einer Push-Operation an {{site.data.keyword.Bluemix}} übertragen, wenn im Projektstammverzeichnis die Datei `manifest.yml` vorhanden ist. 

Führen Sie den folgenden Befehl im aktuellen Projektverzeichnis aus, um die Anwendung zu erstellen:  

```
bx dev build
```
{: codeblock}

Führen Sie den folgenden Befehl aus, um Ihr Projekt in {{site.data.keyword.Bluemix}} bereitzustellen: 

```
bx dev deploy
```
{: codeblock}


### Hilfe
{: #help}

Wenn keine Aktionen bzw. Argumente übergeben werden oder wenn die Aktion "Hilfe" verfügbar ist, wird bei Verwendung dieses Befehls standardmäßig ein allgemeiner Hilfetext angezeigt. Die erweiterte Hilfe umfasst eine Beschreibung der Basisargumente sowie eine Liste der verfügbaren Aktionen.  

Führen Sie den folgenden Befehl aus, um die erweiterte Hilfeinformationen anzuzeigen:

```
bx dev help
```
{: codeblock}


### Auflisten
{: #list}

Sie können alle {{site.data.keyword.Bluemix_notm}}-Projekte in einem Bereich auflisten.

Führen Sie den folgenden Befehl aus, um die Projekte aufzulisten:

```
bx dev list
```
{: codeblock}


<!--
### Editing a project
{: #edit}

You can edit a project, such as changing the name, pattern or starter type, or adding services to your project. Run the following command:

```
bx dev edit
```
{: codeblock}
-->


### Ausführen
{: #run}

Sie können eine Anwendung mit dem Befehl `run` ausführen. Zunächst muss jedoch für das Projekt mithilfe des Befehls `build` eine Erstellung (Build) ausgeführt werden. Bei Aufruf des Ausführungsbefehls wird der Ausführungscontainer gestartet und die Ports, die im Parameter `container-port-map` definiert sind, werden verfügbar gemacht. Der Parameter `run-cmd` kann zum Aufrufen der Anwendung benutzt werden, wenn die Dockerfile des Ausführungscontainers keinen Einstiegspunkt zur Ausführung dieses Schritts enthält. 

Zunächst müssen Sie Ihr Projekt kompilieren:

```
bx dev build
```
{: codeblock}

Führen Sie den folgenden Befehl im aktuellen Projektverzeichnis aus, um die Anwendung zu starten:

```
bx dev run
```
{: codeblock}

Verwenden Sie zum Beenden der Sitzung `CTRL-C`.


#### Ausführungsparameter
{: #run-parameters}

Die folgenden Parameter werden ausschließlich mit dem Befehl `run` verwendet und dienen als Unterstützung beim Verwalten der Anwendung im Ausführungscontainer.

##### `container-name-run`
{: #container-name-run}
	
* Containername für den Ausführungscontainer.
* Syntax: `bx dev run --container-name-run [<projectName>]`

##### `container-path-run`
{: #container-path-run}

* Position im Container, die bei der Ausführung gemeinsam genutzt werden soll.
* Syntax: `bx dev run --container-path-run [/path/to/app]`

##### `host-path-run`
{: #host-path-run}

* Position auf dem Hostsystem, die im Container beim Ausführen gemeinsam genutzt werden soll.
* Syntax: `bx dev run --host-path-run [/path/to/app/bin]`

##### `dockerfile-run`
{: #dockerfile-run}

* Dockerfile für den Ausführungscontainer.
* Syntax: `bx dev run --dockerfile-run [/path/to/Dockerfile.yml]`

##### `image-name-run`
{: #image-name-run}

* Image, das durch die Ausführung von `dockerfile-run` erstellt werden soll.
* Syntax: `bx dev run --image-name-run [/path/to/image-name]`

##### `run-cmd`
{: #run-cmd}

* Parameter, der zum Ausführen des Codes im Ausführungscontainer verwendet wird. Verwenden Sie diesen Parameter, wenn Ihr Image Ihre Anwendung startet.
* Syntax: `bx dev run --run-cmd [/the/run/command]`
	
### Status
{: #status}

Sie können den Status der vom {{site.data.keyword.dev_cli_short}} verwendeten Container entsprechend der Definition in `container-name-run` und `container-name-tools` abfragen. 

Führen Sie den folgenden Befehl im aktuellen Projektverzeichnis aus, um den Containerstatus zu überprüfen:

```
bx dev status
```
{: codeblock}


[Statusbefehlsparameter](#command-parameters)


### Stoppen
{: #stop}

Sie können Ihre Container mit dem Befehl `stop` stoppen. 

Führen Sie zum Stoppen der Container mit den Tools und der Ausführungscontainer, die in der Datei `cli-config.yml` definiert sind, den folgenden Befehl aus: 

```
bx dev stop
```
{: codeblock}

Geben Sie zum Stoppen eines Containers, der in der Datei `cli-config.yml` nicht definiert ist, einen zusätzlichen Befehlszeilenparameter an, um die ursprüngliche Angabe zu überschreiben. Verwenden Sie für den Container mit den Tools  den Parameter [`--container-name-tools`](#container-name-tools) und für den Ausführungscontainer den Parameter [`--container-name-run`](#container-name-run). Wenn in der Datei `cli-config.yml` oder in der Befehlszeile keine Container angegeben wurden, dann bleibt der Stoppbefehl ohne Wirkung. 


### Testen
{: #test}

Sie können eine Anwendung mit dem Befehl `test` testen. Zunächst muss jedoch für das Projekt mithilfe des Befehls `build` eine Erstellung (Build) ausgeführt werden. Anschließend wird der Container mit den Tools zum Aufrufen von `test-cmd` für die Anwendung verwendet.

Zunächst müssen Sie Ihr Projekt kompilieren:

```
bx dev build
```
{: codeblock}

Führen Sie den folgenden Befehl aus, um die Anwendung zu testen: 

```
bx dev test
```
{: codeblock}


[Testbefehlsparameter](#command-parameters)


## Parameter zum Erstellen, Debuggen, Ausführen und Testen
{: #command-parameters}

Die folgenden Parameter können zusammen mit den Befehlen `build|debug|run|test` oder beim direkten Aktualisieren der Datei `cli-config.yml` des Projekts verwendet werden. Für die Befehle [`debug`](#debug-parameters) und [`run`](#run-parameters) stehen zusätzliche Parameter zur Verfügung.

**Hinweis:** In der Befehlszeile eingegebene Befehlsparameter haben Vorrang vor der Konfiguration in `cli-config.yml`.

### `container-name-tools`  
{: #container-name-tools}

* Containername für den Container mit den Tools.
* Syntax: `bx dev <build|debug|run|stop|test> --container-name-tools [<projectName>]`

### `host-path-tools`
{: #host-path-tools}

* Position auf dem Host, die zum Erstellen, Debuggen und Testen gemeinsam genutzt werden soll.
* Syntax: `bx dev <build|debug|run|test> --host-path-tools [/path/to/build/tools]`

### `container-path-tools`
{: #container-path-tools}

* Position im Container, die zum Erstellen, Debuggen und Testen gemeinsam genutzt werden soll.
* Syntax: `bx dev <build|debug|run|test> --container-path-tools [/path/for/build]`

### `container-port-map`
{: #container-port-map}

* Portzuordnungen für den Container. Der erste Wert ist der Port, der im Hostbetriebssystem verwendet werden soll, der zweite ist der Port im Container [host-port:container-port].
* Syntax: `bx dev <build|debug|run|test> --container-port-map [8090:8090,9090,9090]`

### `dockerfile-tools`
{: #dockerfile-tools}

* Dockerfile für den Container mit den Tools.
* Syntax: `bx dev <build|debug|run|test> --dockerfile-tools [path/to/dockerfile]`

### `image-name-tools`
{: #image-name-tools}

* Image, das auf Basis von `dockerfile-tools` erstellt werden soll.
* Syntax: `bx dev <build|debug|run|test> --image-name-tools [path/to/image-name]`

### `build-cmd-run`
{: #build-cmd-run}

* Parameter, der zur Angabe eines Befehls verwendet wird, mit dem Code für jede Verwendung außer für DEBUG erstellt wird. 
* Syntax: `bx dev <build|debug|run|test> --build-cmd-run [some.build.command]`

### `test-cmd`
{: #test-cmd}

* Parameter, der zur Angabe eines Befehls verwendet wird, mit dem der Code im Container mit den Tools getestet wird. 
* Syntax: `bx dev <build|debug|run|test> --test-cmd [/the/test/command]`

### `trace`
{: #trace}

* Verwenden Sie diesen Parameter, um die ausführliche Ausgabe bereitstellen.
* Syntax: `bx dev <build|debug|run|test> --trace`


