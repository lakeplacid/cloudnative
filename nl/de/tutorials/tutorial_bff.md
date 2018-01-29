---

copyright:
  years: 2016, 2017
lastupdated: "2017-11-02"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Umfassendes Lernprogramm zu BFF Basic Starter
{: #tutorial}

Das folgende umfassende Lernprogramm führt Sie durch die Schritte zur Erstellung eines Projekts mit dem BFF Basic Starter. In diesen Schritten wird das Installieren erforderlicher Tools sowie das Ausführen des Projektcodes erläutert. 


## Entwicklertools installieren
{: #dev_tools}

Stellen Sie sicher, dass die [vorausgesetzten Entwicklertools ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](get_code.html#prereq-dev-tools "Symbol für externen Link"){: new_window} installiert sind.


## Vorgehensweise zur Projekterstellung auswählen
{: #choose_how}

Sie können ein Projekt entweder mithilfe der webbasierten [{{site.data.keyword.dev_console}}](#create-devex) oder über das befehlsgesteuerte [{{site.data.keyword.dev_cli_notm}}](#create-cli) erstellen. Nachdem das Projekt erstellt wurde, können Sie das [Projekt ausführen](#running-bff). 


## Projekt mit der {{site.data.keyword.dev_console}} erstellen
{: #create-devex}

1. Erstellen Sie ein Projekt in der {{site.data.keyword.Bluemix}} {{site.data.keyword.dev_console}}.

	1. Klicken Sie auf der Seite [**Einführung** ![Symbol für externen Link](../icons/launch-glyph.svg " Symbol für externen Link")](https://console.ng.bluemix.net/developer/getting-started/ " Symbol für externen Link") in der {{site.data.keyword.dev_console}} auf **Projekt erstellen**.

		Alternativ können Sie auf der Seite **Projekte** auf **Projekt erstellen** klicken.

	2. Wählen Sie **Backend for Frontend** aus und klicken Sie auf **Weiter**.

	3. Wählen Sie die Auswahlmöglichkeit für ein Basis-Backend**** aus und klicken Sie auf **Weiter**.

	4. Geben Sie Ihren Projektnamen ein. Verwenden Sie für dieses Lernprogramm `BFFProject`.   

	5. Geben Sie einen eindeutigen Hostnamen, z. B. Ihre Initialen und `-devhost` ein. Beispiel: 
	
	 ```
	 abc-devhost
	 ``` 

	6. Wählen Sie Ihre Sprachplattform aus. Verwenden Sie für dieses Lernprogramm `Node`.
   
	7. Klicken Sie auf **Erstellen**.

2. Optional: Fügen Sie die Data-Funktion hinzu.

	1. Klicken Sie auf der Seite **Projektübersicht** für **Data** auf **Anzeigen**.

      Alternativ können Sie **Erstellen** oder **Vorhandenen hinzufügen** auf der Seite **Funktionen > Data** aus.

   2. Geben Sie Ihren Servicenamen ein und klicken Sie auf **Erstellen**.

3. Generieren Sie den Projektcode:

	1. Klicken Sie auf der Seite **Projektübersicht** auf **Code abrufen**, um Ihre Sprache auszuwählen.
   
		Alternativ können Sie auf die Seite **Code** klicken.
      
	2. Klicken Sie auf **Code generieren**.
   
	3. Wenn die Projektcodegenerierung fertig ist, klicken Sie auf **Code herunterladen**, um Ihr Projektarchiv herunterzuladen.

4. Beginnen Sie mit Ihrem heruntergeladenen Projekt zu arbeiten:

	1. Dekomprimieren Sie die archivierte Datei.
	
	2. Navigieren Sie zum neuen Projektverzeichnis.
	
	3. Verwenden Sie den {{site.data.keyword.dev_cli_notm}}, um fortzufahren.

5. Optional: [Aktualisieren Sie das Projekt](project_overview_page.html#update_language), um eine neue Sprache zu generieren.


## Projekt mit dem {{site.data.keyword.dev_cli_notm}} erstellen
{: #create-cli}

1. Stellen Sie sicher, dass das [{{site.data.keyword.dev_cli_short}}](dev_cli.html) installiert ist.

2. Navigieren Sie in der Eingabeaufforderung des Terminals zu einem lokalen Verzeichnis Ihrer Wahl und führen Sie den folgenden Befehl aus.
  
	```
	bx dev create
	```
	{: codeblock}
	
3. Geben Sie bei Aufforderung die folgenden Werte an:

	* Wählen Sie ein Muster aus: 3 (für Backend for Frontend)
	* Wählen Sie einen Starter aus: 1 (für Basis-Backend)
	* Wählen Sie eine Sprache aus: 1 (für Node)
	* Geben Sie einen Namen für Ihr Projekt ein: `BFFProjectCLI`
	* Geben Sie einen Hostnamen für Ihr Projekt ein: `abc-devhost`
	  * Geben Sie einen eindeutigen Hostnamen, z. B. Ihre Initialen und `-devhost` ein. Beispiel: 
	
	     ```
	     abc-devhost
	     ```
	  
4. Navigieren Sie nach dem erfolgreichen Speichern des Projekts `BFFProjectCLI` zum Ordner `BFFProjectCLI`.

5. Fügen Sie eigenen Code hinzu, erstellen Sie das Projekt und führen Sie es aus.
 
	1. Erstellen Sie das Projekt mit dem folgenden Befehl: 

		```
		bx dev build
		```
		{: codeblock}
		 
	2. Führen Sie das Projekt mit dem folgenden Befehl aus:

 		```
		bx dev run
		```
		{: codeblock}


## Running a BFF project
{: #running-bff}

Sie können die Anwendung lokal auf Ihrem Hostsystem ausführen, wenn Sie die dazu erforderlichen Erstellungstools installieren. Alternativ hierzu können Sie die verfügbare Containerunterstützung in {{site.data.keyword.dev_cli_notm}} verwenden.

### Using the IBM Cloud Plugin
{: #using-blumix}

1. Geben Sie zum Erstellen des Projekts im aktuellen Projektverzeichnis den folgenden Befehl ein:

   ```
   bx dev build
   ```
   {: codeblock}

2. Geben Sie zum Ausführen des Projekts im aktuellen Projektverzeichnis den folgenden Befehl ein:

   ```
   bx dev run
   ```
   {: codeblock}

3. Sie können curl auf dem Server mit dem folgenden Befehl ausführen:

   ```
   curl http://localhost:8080
   ```
   {: codeblock}

4. Sie können das API-Dokument auf Ihrem Server unter der folgenden Adresse anzeigen:

   ```
   http://localhost:8080/swagger/api
   ```
   {: codeblock}

5. Sie können sich mit der API auf Ihrem Server unter der folgenden Adresse vertraut machen:

   ```
   http://localhost:8080/explorer
   ```
   {: codeblock}
