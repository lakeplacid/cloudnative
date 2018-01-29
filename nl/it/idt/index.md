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

{{site.data.keyword.dev_cli_long}} fornisce un approccio guidato al comando estensibile per la creazione, lo sviluppo e la distribuzione di un progetto web con il plugin `dev`. Ideale per gli sviluppatori che desiderano utilizzare il controllo della riga comandi per sviluppare le applicazioni del microservizio end-to-end. 

{: shortdesc}

{{site.data.keyword.dev_cli_notm}} utilizza due contenitori per facilitare la creazione e la verifica della tua applicazione. Il primo è il contenitore degli strumenti, che contiene i programmi di utilità necessari per creare e verificare la tua applicazione. Il Dockerfile per questo contenitore è definito dal parametro [`dockerfile-tools`](#command-parameters). Puoi pensare ad esso come a un contenitore di sviluppo poiché contiene gli strumenti normalmente utili per lo sviluppo di uno specifico runtime.

Il secondo contenitore è il contenitore di esecuzione. Questo contenitore è di un formato adeguato per essere distribuito per l'utilizzo, ad esempio, in {{site.data.keyword.Bluemix}}. Di conseguenza, viene definito un punto di ingresso che avvia la tua applicazione. Quando selezioni di eseguire la tua applicazione tramite {{site.data.keyword.dev_cli_short}}, utilizza questo contenitore. Il Dockerfile per questo contenitore è definito dal parametro [`dockerfile-run`](#run-parameters).


## Aggiunta di {{site.data.keyword.dev_cli_notm}}
{: #add-cli}


### Prerequisiti
{: #prereq}

Devi ottenere alcuni prerequisiti che ti consentono di esplorare a fondo e utilizzare correttamente la {{site.data.keyword.dev_cli_short}}, poiché è altamente estendibile per l'utilizzo di tecnologie complementari.

<!--1. Install the [Cloud Foundry CLI ![External link icon](../icons/launch-glyph.svg "External link icon")](https://github.com/cloudfoundry/cli#getting-started "External link icon").-->

1. Installa la CLI [{{site.data.keyword.Bluemix}} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](http://clis.ng.bluemix.net/ui/home.html "Icona link esterno").

2. Ottieni un ID [{{site.data.keyword.Bluemix_notm}}](https://www.bluemix.net).

3. Se prevedi di utilizzare ed eseguire il debug di applicazioni in locale, devi installare anche [Docker ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://www.docker.com/get-docker "Icona link esterno").


### Prima di iniziare
{: #before-install}

1. Connettiti a un endpoint API nella tua [regione {{site.data.keyword.Bluemix_notm}}](/docs/overview/whatisbluemix.html#ov_intro_reg). Ad esempio, immetti il seguente comando per connetterti alla regione Stati Uniti Sud {{site.data.keyword.Bluemix_notm}}:

	```
	bx api https://api.ng.bluemix.net
	```
	{: codeblock}
	
2. Accedi a {{site.data.keyword.Bluemix_notm}} fornendo il tuo ID IBM e password:

	```
	bx login
	```
	{: codeblock}
	
	**Nota:** se le tue credenziali vengono rifiutate, potresti utilizzare un ID federato. Segui questa procedura per effettuare l'autenticazione utilizzando un ID federato.
	
	<!-- 
	POINT TO IBM CLOUD CLI LOG IN DOCUMENTATION !!!
	
	This link does not work in production yet --> 
	
	1. Accedi a [{{site.data.keyword.iamshort}} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://www.bluemix.net/iam/#/apikeys "Icona link esterno"){: new_window}.
	2. Seleziona **Crea chiave API**.
		* Immetti un nome e una descrizione per apiKey
	3. Scarica la tua apiKey.
	4. Apri il file e copia il valore dal campo `apiKey`.
	5. Accedi utilizzando il seguente comando:
	 
		```
		bx login --apikey <value>
		```
		{: codeblock}


### installazione
{: #installation}

1. Installa la [{{site.data.keyword.dev_cli_short}} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](/docs/cli/reference/bluemix_cli/index.html#install_plug-in "Icona link esterno"){: new_window} eseguendo il seguente comando:
 
	```
	bx plugin install dev
	```
	{: codeblock}

2. 	Convalida la validità dell'installazione del plugin eseguendo il seguente comando:   
 
	```
	bx dev
	```
	{: codeblock}


