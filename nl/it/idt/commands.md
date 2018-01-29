---
copyright:
  years: 2017, 2018
lastupdated: "2018-01-19"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:screen: .screen}  
{:codeblock: .codeblock}  
{:pre: .pre}  

# {{site.data.keyword.dev_cli_notm}} (bx dev) commands
{: #idt-cli}

Version: 1.1.0
Released: Dec 11, 2017

Use the following {{site.data.keyword.dev_cli_notm}} (bx dev) commands to create a project, deploy, debug, and test it.

- [build](#build): Build the project in a local container
- [code](#code): Download the code from a project
- [console](#console): Opens the IBM Cloud console for a project
- [create](#create): Creates a new project and gives you the option to add services
- [debug](#debug): Debug your application in a local container
- [delete](#delete): Deletes a project from your space
- [deploy](#deploy): Deploy an application to IBM Cloud
- [enable](#enable): Add IBM Cloud files to an existing project
- [get-credentials](get-credentials]): Gets credentials required by the project to enable use of bound services
- [help](#help): Help on IDT syntax and arguments
- [list](#list): List all IBM Cloud projects in a space
- [run](#run): Run your application in a local container
- [shell](#shell): Open a shell into a local container
- [status](#status): Check the status of the containers used by the CLI
- [stop](#stop): Stop a container
- [test](#test): Test your application in a local container
- [view](#view): View the app's deployed URL for testing and viewing



## Comandi
{: #commands}

Utilizzare i seguenti comandi per creare un progetto, distribuirlo, eseguirne il debug, e verificarlo.

### Creazione
{: #build}

Puoi creare la tua applicazione utilizzando il comando `build`. L'elemento di configurazione `build-cmd-run` viene utilizzato per creare l'applicazione. I comandi `test`, `debug` e `run` prevedono di trovare un progetto compilato in modo che puoi prima eseguire un'operazione di build almeno una volta.

Esegui il seguente comando nella tua directory del progetto corrente per creare la tua applicazione:  

```
bx dev build
```
{: codeblock}


[Crea parametri del comando](#command-parameters)


### Codice
{: #code}

Utilizza il comando `code` per scaricare il codice dell'applicazione dopo la distribuzione, in modo da poterlo riesaminare localmente o modificare.

Esegui il seguente comando per scaricare il codice da un progetto specificato.

```
bx dev code <projectName>
```
{: codeblock}


### Creazione
{: #create}

Crea un progetto richiedendo tutte le informazioni, tra cui il linguaggio, il nome progetto e il tipo di modello applicazione. Il progetto viene creato nella directory corrente. 

Per creare un progetto nella directory corrente e associare dei servizi ad esso, esegui il seguente comando: 

```
bx dev create
```
{: codeblock}


### Debug
{: #debug}

Puoi eseguire il debug della tua applicazione tramite il comando `debug`. Deve prima essere completata una build nel progetto utilizzando il comando di build. Quando richiami il comando `debug`, viene avviato un contenitore che fornisce una o più porte di debug come definito dal valore `container-port-map-debug`. Collegando il tuo strumento di debug preferito alla porta o alle porte puoi eseguire il debug della tua applicazione come normale.

**Limitazione**: i progetti Swift non sono disponibili per il debug.

Per prima cosa, compila il tuo progetto:

```
bx dev build
```
{: codeblock}

Esegui il seguente comando nella tua directory del progetto corrente per eseguire il debug della tua applicazione:

```
bx dev debug
```
{: codeblock}	

Per uscire dalla sessione di debug utilizza `CTRL-C`.


#### Debug dei parametri del comando
{: #debug-parameters}

I seguenti parametri sono esclusivi del comando `debug` e forniscono supporto
con il debug di un'applicazione.

##### `container-port-map-debug`
{: #port-map-debug}

* Le associazioni di porta per la porta di debug. Il primo valore è la porta da utilizzare nel sistema operativo host, il secondo è la porta nel contenitore [host-port:container-port].
* Utilizzo: `bx dev debug --container-port-map-debug [7777:7777]`

##### `build-cmd-debug`
{: #build-cmd-debug}

* Il parametro che viene utilizzato per creare il codice per DEBUG. 
* Utilizzo: `bx dev debug --build-cmd-debug build.command.sh`

##### `debug-cmd`
{: #debug-cmd}

* Il parametro che viene utilizzato per specificare un comando per richiamare il debug nel contenitore degli strumenti. Utilizzare questo parametro se `build-cmd-debug` avvia la tua applicazione in debug.
* Utilizzo: `bx dev debug --debug-cmd /the/debug/command`

#### Debug dell'applicazione locale:
{: #local-app-dev}

Per ulteriori informazioni sul debug dell'applicazione locale, vedi [Debug dell'applicazione locale](docs/cloudnative/dev_cli_local_debug.html#local-debug).


### Eliminazione
{: #delete}

Utilizza il comando `delete` per rimuovere i progetti dal tuo spazio {{site.data.keyword.Bluemix}}. Puoi eseguire il comando senza i parametri per elencare i progetti disponibili da eliminare. Il codice e le directory del progetto non vengono rimossi dallo spazio del disco locale.

Esegui il seguente comando per eliminare il tuo progetto da {{site.data.keyword.Bluemix}}:

```
bx dev delete <projectName>
```
{: codeblock}
 

**Nota:** i servizi {{site.data.keyword.Bluemix}} **non** vengono rimossi.


### Distribuzione 
{: #deploy}

Puoi distribuire un'applicazione a {{site.data.keyword.Bluemix}} tramite il comando `deploy` quando è presente un file `manifest.yml` nella directory root del tuo progetto.

Esegui il seguente comando nella tua directory del progetto corrente per creare la tua applicazione:  

```
bx dev build
```
{: codeblock}

Esegui il seguente comando per distribuire il tuo progetto a {{site.data.keyword.Bluemix}}:

```
bx dev deploy
```
{: codeblock}


### Guida
{: #help}

Per impostazione predefinita, se non viene passato alcun argomento o azione, o se viene fornita l'azione 'help', questo comando mostra un testo della "Guida" generale. La guida generale visualizzata include una descrizione degli argomenti di base così come un elenco di azioni disponibili.  

Esegui il seguente comando per visualizzare le informazioni sulla guida generali:

```
bx dev help
```
{: codeblock}


### Elenco
{: #list}

Puoi elencare tutti i progetti {{site.data.keyword.Bluemix_notm}} in uno spazio.

Esegui il seguente comando per elencare i tuoi progetti:

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


### Esecuzione
{: #run}

Puoi eseguire la tua applicazione tramite il comando `run`. Deve prima essere completata una build nel progetto utilizzando il comando `build`. Quando richiami il comando run, viene avviato il contenitore di esecuzione che espone le porte come definito dal parametro `container-port-map`. Il parametro `run-cmd` può essere utilizzato per richiamare l'applicazione se il contenitore di esecuzione Dockerfile non contiene un punto di ingresso per completare questa fase. 

Per prima cosa, compila il tuo progetto:

```
bx dev build
```
{: codeblock}

Esegui il seguente comando nella tua directory del progetto corrente per avviare la tua applicazione:

```
bx dev run
```
{: codeblock}

Per uscire dalla sessione utilizza `CTRL-C`.


#### Eseguire i parametri
{: #run-parameters}

I seguenti parametri sono esclusivi del comando `run` e forniscono supporto
nella gestione della tua applicazione nel contenitore di esecuzione.

##### `container-name-run`
{: #container-name-run}
	
* Il nome del contenitore per il tuo contenitore di esecuzione.
* Utilizzo: `bx dev run --container-name-run [<projectName>]`

##### `container-path-run`
{: #container-path-run}

* L'ubicazione nel contenitore da condividere nell'esecuzione.
* Utilizzo: `bx dev run --container-path-run [/path/to/app]`

##### `host-path-run`
{: #host-path-run}

* L'ubicazione del sistema host da condividere nel contenitore nell'esecuzione. 
* Utilizzo: `bx dev run --host-path-run [/path/to/app/bin]`

##### `dockerfile-run`
{: #dockerfile-run}

* Il Dockerfile per il contenitore di esecuzione. 
* Utilizzo: `bx dev run --dockerfile-run [/path/to/Dockerfile.yml]`

##### `image-name-run`
{: #image-name-run}

* L'immagine da creare da `dockerfile-run`.
* Utilizzo: `bx dev run --image-name-run [/path/to/image-name]`

##### `run-cmd`
{: #run-cmd}

* Parametro utilizzato per eseguire il codice nel contenitore di esecuzione. Utilizza questo parametro se la tua immagine avvia la tua applicazione.
* Utilizzo: `bx dev run --run-cmd [/the/run/command]`
	
### Stato
{: #status}

Puoi eseguire una query dello stato dei contenitori utilizzati dalla {{site.data.keyword.dev_cli_short}} come definito da `container-name-run` e `container-name-tools`. 

Esegui il seguente comando nella tua directory del progetto corrente per controllare lo stato del contenitore:

```
bx dev status
```
{: codeblock}


[Stato dei parametri del comando](#command-parameters)


### Arresto
{: #stop}

Puoi arrestare i tuoi contenitori tramite il comando `stop`. 

Per arrestare gli strumenti ed eseguire i contenitori come definito nel tuo file `cli-config.yml`, esegui:

```
bx dev stop
```
{: codeblock}

Per arrestare un contenitore non definito nel file `cli-config.yml`, puoi specificare un ulteriore parametro della riga di comando per sovrascriverlo. Per il contenitore degli strumenti, utilizza il parametro [`--container-name-tools`](#container-name-tools) e per il contenitore in esecuzione utilizza [`--container-name-run`](#container-name-run). Se non viene specificato alcun contenitore nel file `cli-config.yml` e nella riga di comando, il comando stop viene semplicemente restituito.


### Verifica
{: #test}

Puoi verificare la tua applicazione tramite il comando `test`. Deve prima essere completata una build nel progetto utilizzando il comando `build`. Il contenitore degli strumenti viene quindi utilizzato per richiamare `test-cmd` per l'applicazione.

Per prima cosa, compila il tuo progetto:

```
bx dev build
```
{: codeblock}

Esegui il seguente comando per verificare la tua applicazione: 

```
bx dev test
```
{: codeblock}


[Verifica dei parametri del comando](#command-parameters)


## I parametri per la creazione, il debug, l'esecuzione e la verifica
{: #command-parameters}

I seguenti parametri possono essere utilizzati con i comandi `build|debug|run|test` oppure aggiornando direttamente il file `cli-config.yml` del progetto. Sono disponibili ulteriori parametri per i comandi [`debug`](#debug-parameters) e [`run`](#run-parameters). 

**Nota**: i parametri di comando immessi sulla riga comandi hanno la precedenza sulla configurazione `cli-config.yml`.

### `container-name-tools`  
{: #container-name-tools}

* Il nome del contenitore per il tuo contenitore degli strumenti.
* Utilizzo: `bx dev <build|debug|run|stop|test> --container-name-tools [<projectName>]`

### `host-path-tools`
{: #host-path-tools}

* L'ubicazione sull'host da condividere per la creazione, il debug e la verifica.
* Utilizzo: `bx dev <build|debug|run|test> --host-path-tools [/path/to/build/tools]`

### `container-path-tools`
{: #container-path-tools}

* L'ubicazione nel contenitore da condividere per la creazione, il debug e la verifica.
* Utilizzo: `bx dev <build|debug|run|test> --container-path-tools [/path/for/build]`

### `container-port-map`
{: #container-port-map}

* Le associazioni di porta per il contenitore. Il primo valore è la porta da utilizzare nel sistema operativo host, il secondo è la porta nel contenitore [host-port:container-port].
* Utilizzo: `bx dev <build|debug|run|test> --container-port-map [8090:8090,9090,9090]`

### `dockerfile-tools`
{: #dockerfile-tools}

* Il Dockerfile per il contenitore degli strumenti. 
* Utilizzo: `bx dev <build|debug|run|test> --dockerfile-tools [path/to/dockerfile]`

### `image-name-tools`
{: #image-name-tools}

* L'immagine da creare da `dockerfile-tools`.
* Utilizzo: `bx dev <build|debug|run|test> --image-name-tools [path/to/image-name]`

### `build-cmd-run`
{: #build-cmd-run}

* Il parametro che viene utilizzato per specificare un comando per creare il codice per tutti gli utilizzi di DEBUG.
* Utilizzo: `bx dev <build|debug|run|test> --build-cmd-run [some.build.command]`

### `test-cmd`
{: #test-cmd}

* Il parametro che viene utilizzato per specificare un comando per verificare il codice nel contenitore degli strumenti. 
* Utilizzo: `bx dev <build|debug|run|test> --test-cmd [/the/test/command]`

### `trace`
{: #trace}

* Utilizzare questo parametro per fornire l'output dettagliato. 
* Utilizzo: `bx dev <build|debug|run|test> --trace`


