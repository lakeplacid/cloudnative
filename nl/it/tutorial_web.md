---

copyright:
  years: 2016, 2017
lastupdated: "2017-06-12"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Esercitazione end-to-end dello starter di base web
{: #tutorial}

La seguente esercitazione end-to-end ti guida attraverso i passaggi per creare un progetto dallo starter di base web. I passaggi includono l'installazione degli strumenti prerequisiti e come eseguire il codice del progetto. 


## Installazione degli strumenti per sviluppatori
{: #dev_tools}

Assicurati di installare gli [strumenti per sviluppatori prerequisiti ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](get_code.html#prereq-dev-tools "Icona link esterno"){: new_window}.


## Scegli come creare il tuo progetto
{: #choose_how}

Puoi creare un progetto utilizzando la [{{site.data.keyword.dev_console}}](#create-devex) basata su web o la [{{site.data.keyword.dev_cli_notm}}](#create-cli) controllata dai comandi. Dopo aver creato il progetto, puoi quindi [eseguire il progetto](#run).


## Creazione di un progetto utilizzando la {{site.data.keyword.dev_console}}
{: #create-devex}

1. Crea un progetto nella {{site.data.keyword.Bluemix}} {{site.data.keyword.dev_console}}:

	1. Dalla pagina [**Introduzione** ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://console.ng.bluemix.net/developer/getting-started/ "Icona link esterno") della {{site.data.keyword.dev_console}}, fai clic su **Crea progetto**.

		In alternativa puoi fare clic su **Crea progetto** dalla pagina **Progetti**.

	2. Seleziona **Applicazione web** e fai clic su **Avanti**.

	3. Seleziona **Web di base** e fai clic su **Avanti**.

	4. Immetti il nome del tuo progetto. Per questa esercitazione, utilizza `WebBasicProject`.   

	5. Immetti un nome host univoco, come le tue iniziali più `-devhost`. Ad
esempio:
	
	 ```
	 abc-devhost
	 ```

	6. Seleziona la tua piattaforma di linguaggio. Per questa esercitazione, utilizza `Swift`.
   
	7. Fai clic su **Crea**.

2. Facoltativo: aggiungi la funzionalità Data:

	1. Fai clic su **Visualizza** per **Data** nella pagina **Panoramica progetto**.

      In alternativa, puoi fare selezionare **Crea** o **Aggiungi esistente** nella pagina **Funzionalità > Data**.

   2. Immetti il nome del tuo servizio e fai clic su **Crea**.

3. Genera il tuo codice del progetto:

	1. Fai clic su **Richiama codice** nella pagina **Panoramica progetto** per selezionare il tuo linguaggio.
   
		In alternativa puoi fare clic sulla pagina **Codice**.
      
	2. Fai clic su **Genera codice**.
   
	3. Quando il codice del progetto ha terminato la generazione, fai clic su **Scarica codice** per scaricare il tuo archivio del progetto.

4. Inizia a lavorare con il tuo progetto scaricato:

	1. Espandi il file archiviato.
	
	2. Passa alla nuova directory del progetto.
	
	3. Utilizza la {{site.data.keyword.dev_cli_notm}} per continuare.

5. Facoltativo: [Aggiorna il tuo progetto](project_overview_page.html#update_language) per generare un nuovo linguaggio.


## Creazione di un progetto utilizzando la {{site.data.keyword.dev_cli_notm}}
{: #create-cli}

1. Assicurati di installare la [{{site.data.keyword.dev_cli_short}}](dev_cli.html).

2. Nella tua finestra del terminale, passa a una directory locale di tua scelta ed esegui il seguente comando.
  
	```
	bx dev create
	```
	{: codeblock}

3. Fornisci i seguenti valori quando richiesto:

	* Seleziona un modello: 1 (per Web)
	* Seleziona uno starter: 1 (per Web di base)
	* Seleziona un linguaggio: 2 (per Swift)
	* Immetti un nome per il tuo progetto: `WebBasicProjectCLI`
	* Immetti un nome host per il tuo progetto: `abc-devhost`
	  * Immetti un nome host univoco, come le tue iniziali più `-devhost`. Ad
esempio:
	
	     ```
	     abc-devhost
	     ```

4. Dopo aver salvato `WebBasicProjectCLI`, passa alla cartella `WebBasicProjectCLI`.

5. Aggiungi il tuo proprio codice, crea ed esegui il progetto. 
	
	1. Crea il progetto con il seguente comando: 
 
		```
		bx dev build
		```
		{: codeblock}
	 
	2. Esegui il progetto con il seguente comando:
 
		```
		bx dev run
		```
		{: codeblock}


## Esecuzione di un progetto web
{: #run}

Puoi eseguire l'applicazione localmente sul tuo sistema host se installi gli strumenti di build necessari o utilizzando il supporto del contenitore disponibile in {site.data.keyword.dev_cli_notm}}.


### Utilizzo della {{site.data.keyword.dev_cli_short}}
{: #dev notoc}

1. Installa le dipendenze del nodo:

  ```
  npm install
  ```
  {: codeblock}

2. Integra il tuo codice di frontend in un modulo:

  ```
  gulp
  ```
  {: codeblock}

3. Per creare il progetto nella tua directory del progetto corrente, immetti il seguente comando:

  ```
  bx dev build
  ```
  {: codeblock}

4. Per eseguire il progetto nella tua directory del progetto corrente, immetti il seguente comando: 

  ```
  bx dev run
  ```
  {: codeblock}

5. Apri il tuo browser in `http://localhost:8080`.


## Esecuzione del tuo progetto in Xcode
{: #Xcode}

1. Crea un progetto Xcode.

	Prima di poter sviluppare in Xcode, devi utilizzare il gestore del pacchetto Swift per creare un progetto Xcode.
	
	```
	swift project generate-xcodeproj
	```
	{: codeblock}

2. Modifica la tua destinazione attiva con l'eseguibile:

	Successivamente, apri il tuo progetto in Xcode e assicurati che la tua destinazione attiva sia l'eseguibile. Puoi tenere premuto il tasto di opzione e fai clic sul menu a discesa per selezionare l'eseguibile attivo desiderato. 

3. Premi **run**.

4. Apri il tuo browser in `http://localhost:8080`.

