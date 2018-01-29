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



## Commandes
{: #commands}

Utilisez les commandes décrites ci-après pour créer un projet, le déployer, le déboguer et le tester.

### Build
{: #build}

Vous pouvez générer votre application en utilisant la commande `build`. L'élément de configuration `build-cmd-run` est utilisé pour générer l'application. Les
commandes `test`, `debug` et `run`
s'attendent à trouver un projet compilé ; par conséquent, vous devez d'abord
exécuter une opération de génération au moins une fois au préalable.


Exécutez la commande suivante dans votre répertoire de projet en cours pour
générer
votre application :  

```
bx dev build
```
{: codeblock}


[Paramètres de la commande build](#command-parameters)


### Code
{: #code}

Utilisez la commande `code` pour télécharger le code d'application après le déploiement, afin de pouvoir le réviser localement ou y apporter des modifications.

Exécutez la commande suivante pour télécharger le code à partir du projet spécifié :

```
bx dev code <projectName>
```
{: codeblock}


### Create
{: #create}

Cette commande crée un projet en vous invitant à entrer toutes les informations,
notamment la langue, le nom du projet et le type de modèle d'application. Le projet est
créé dans le répertoire de travail.  

Pour créer un projet dans le répertoire de projet en cours et lui associer des
services, exécutez la commande suivante :


```
bx dev create
```
{: codeblock}


### Debug
{: #debug}

Vous pouvez déboguer votre application avec la commande `debug`. Une
génération doit d'abord être effectuée pour le projet à l'aide de la commande build. Lorsque vous appelez la commande `debug`, un conteneur
qui fournit un ou des ports de débogage, tels que définis par la valeur
`container-port-map-debug`, est démarré. Connectez l'outil de
débogage de votre choix au(x) port(s),  puis déboguez votre application comme vous le
faites
normalement.

**Limitation** : les projets Swift ne sont pas disponibles pour le débogage.

D'abord, compilez votre projet : 

```
bx dev build
```
{: codeblock}

Exécutez la commande suivante dans votre répertoire de projet en cours pour
déboguer votre application : 

```
bx dev debug
```
{: codeblock}	

Pour quitter la session de débogage, utilisez `CTRL-C`.


#### Paramètres de la commande debug
{: #debug-parameters}

Les paramètres ci-dessous, qui sont réservés à la commande
`debug`, facilitent le débogage d'une application.

##### `container-port-map-debug`
{: #port-map-debug}

* Mappages de port pour le port de débogage. La première valeur est le port à
utiliser sur le système d'exploitation hôte et la seconde le port dans le conteneur
[host-port:container-port].
* Syntaxe : `bx dev debug --container-port-map-debug [7777:7777]`

##### `build-cmd-debug`
{: #build-cmd-debug}

* Paramètre utilisé afin de générer le code pour DEBUG.

* Syntaxe : `bx dev debug --build-cmd-debug build.command.sh`

##### `debug-cmd`
{: #debug-cmd}

* Paramètre utilisé pour spécifier une commande afin d'appeler la fonction
de débogage dans le conteneur des outils. Utilisez-le si
`build-cmd-debug` démarre votre application en mode débogage.

* Syntaxe : `bx dev debug --debug-cmd /the/debug/command`

#### Débogage d'une application locale : 
{: #local-app-dev}

Pour plus d'informations sur le débogage d'une application locale, voir [Débogage d'une application locale](docs/cloudnative/dev_cli_local_debug.html#local-debug).


### Delete
{: #delete}

Utilisez la commande `delete` pour supprimer des projets de votre espace {{site.data.keyword.Bluemix}}. Vous pouvez exécuter la commande sans paramètre pour répertorier les projets disponibles à supprimer. Le
code du projet et les répertoires ne sont pas retirés de votre espace disque local.

Exécutez la commande suivante pour supprimer votre projet depuis {{site.data.keyword.Bluemix}} :

```
bx dev delete <projectName>
```
{: codeblock}
 

**Remarque : **les services {{site.data.keyword.Bluemix}} ne sont **pas** retirés.


### Deploy
{: #deploy}

Vous pouvez envoyer une application à {{site.data.keyword.Bluemix}} avec la commande `deploy` si un fichier
`manifest.yml` existe dans le répertoire racine de votre projet.


Exécutez la commande suivante dans votre répertoire de projet en cours pour
générer votre application :  

```
bx dev build
```
{: codeblock}

Exécutez la commande suivante pour déployer votre projet dans
{{site.data.keyword.Bluemix}} :

```
bx dev deploy
```
{: codeblock}


### Help
{: #help}

Par défaut, si aucune action ou aucun argument n'est transmis, ou si
l'action help
est fournie, cette commande affiche un texte d'aide général. L'aide générale affichée
inclut une description des arguments de base ainsi que la liste des actions disponibles.  

Exécutez la commande suivante pour afficher des informations d'aide générales :

```
bx dev help
```
{: codeblock}


### List
{: #list}

Vous pouvez répertorier tous les projets {{site.data.keyword.Bluemix_notm}} d'un espace.

Exécutez la commande suivante pour répertorier vos projets :

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


### Run
{: #run}

Vous pouvez exécuter votre application avec la commande `run`. Une
génération doit d'abord être effectuée pour le projet à l'aide de la commande
`build`. Lorsque vous appelez la commande run, le conteneur d'exécution est
démarré et expose les ports tels que définis par le paramètre
`container-port-map`. Le paramètre `run-cmd` peut être
utilisé pour appeler l'application si le conteneur d'exécution Dockerfile ne contient pas de
point d'entrée pour effectuer cette étape.
 

D'abord, compilez votre projet : 

```
bx dev build
```
{: codeblock}

Exécutez la commande suivante dans votre répertoire de projet en cours pour
démarrer votre application :

```
bx dev run
```
{: codeblock}

Pour quitter la session, utilisez `CTRL-C`.


#### Paramètres de la commande run
{: #run-parameters}

Les paramètres ci-dessous, qui sont réservés à la commande
`run`, facilitent la gestion de votre application dans le conteneur
d'exécution.

##### `container-name-run`
{: #container-name-run}
	
* Nom de conteneur pour le conteneur d'exécution.
* Syntaxe : `bx dev run --container-name-run [<projectName>]`

##### `container-path-run`
{: #container-path-run}

* Emplacement dans le conteneur à partager à l'exécution.
* Syntaxe : `bx dev run --container-path-run [/path/to/app]`

##### `host-path-run`
{: #host-path-run}

* Emplacement de partage du conteneur sur le système hôte lors de
l'exécution.

* Syntaxe : `bx dev run --host-path-run [/path/to/app/bin]`

##### `dockerfile-run`
{: #dockerfile-run}

* Fichier Dockerfile pour le conteneur d'exécution. 
* Syntaxe : `bx dev run --dockerfile-run
[/path/to/Dockerfile.yml]`

##### `image-name-run`
{: #image-name-run}

* Image à créer depuis `dockerfile-run`.
* Syntaxe : `bx dev run --image-name-run [/path/to/image-name]`

##### `run-cmd`
{: #run-cmd}

* Paramètre utilisé pour exécuter le code dans le conteneur d'exécution. Utilisez ce
paramètre si votre image démarre votre application.

* Syntaxe : `bx dev run --run-cmd [/the/run/command]`
	
### Status
{: #status}

Vous pouvez effectuer une requête relative au statut des conteneurs qui sont
utilisés par le plug-in {{site.data.keyword.dev_cli_short}}, comme défini par `container-name-run` et `container-name-tools`. 

Exécutez la commande suivante dans votre répertoire de projet en cours pour
vérifier le statut d'un conteneur :

```
bx dev status
```
{: codeblock}


[Paramètres de la commande status](#command-parameters)


### Stop
{: #stop}

Vous pouvez arrêter vos conteneurs avec la commande `stop`.


Pour arrêter les outils et les conteneurs d'exécution tels que définis dans votre
fichier `cli-config.yml`, exécutez :

```
bx dev stop
```
{: codeblock}

Pour arrêter un conteneur qui n'est pas défini dans le fichier
`cli-config.yml`, vous pouvez spécifier un paramètre de ligne de
commande supplémentaire à la place du nom de conteneur.
Pour le conteneur des outils, utilisez le paramètre
[`--container-name-tools`](#container-name-tools) et
pour le conteneur d'exécution, utilisez le paramètre
[`--container-name-run`](#container-name-run). Si
aucun conteneur n'est spécifié dans le fichier `cli-config.yml` ou
sur la ligne de commande, la commande stop s'arrête.



### Test
{: #test}

Vous pouvez tester votre application avec la commande `test`. Une
génération doit d'abord être effectuée pour le projet à l'aide de la commande
`build`. Le conteneur des outils est ensuite utilisé afin d'appeler `test-cmd` pour l'application.

D'abord, compilez votre projet : 

```
bx dev build
```
{: codeblock}

Exécutez la commande suivante pour tester votre application : 

```
bx dev test
```
{: codeblock}


[Paramètres de la commande test](#command-parameters)


## Paramètres pour les commandes build, debug, run et test
{: #command-parameters}

Les paramètres ci-dessous peuvent être utilisés avec les commandes
`build|debug|run|test` ou en mettant à jour directement le fichier `cli-config.yml` du projet. 
Des paramètres supplémentaires sont disponibles pour les commandes
[`debug`](#debug-parameters) et
[`run`](#run-parameters).

**Remarque** : les paramètres de commande qui sont entrés sur la
ligne de commande sont prioritaires sur ceux du fichier de configuration `cli-config.yml`.

### `container-name-tools`  
{: #container-name-tools}

* Nom de conteneur pour le conteneur des outils.
* Syntaxe : `bx dev <build|debug|run|stop|test> --container-name-tools [<projectName>]`

### `host-path-tools`
{: #host-path-tools}

* Emplacement de partage sur l'hôte pour les commandes build, debug, test.
* Syntaxe : `bx dev <build|debug|run|test> --host-path-tools [/path/to/build/tools]`

### `container-path-tools`
{: #container-path-tools}

* Emplacement de partage dans le conteneur pour les commandes build, debug, test.
* Syntaxe : `bx dev <build|debug|run|test> --container-path-tools [/path/for/build]`

### `container-port-map`
{: #container-port-map}

* Mappages de port pour le conteneur. La première valeur est le port à utiliser sur
le système d'exploitation hôte et la seconde le port dans le conteneur [host-port:container-port].
* Syntaxe : `bx dev <build|debug|run|test> --container-port-map [8090:8090,9090,9090]`

### `dockerfile-tools`
{: #dockerfile-tools}

* Fichier Dockerfile pour le conteneur des outils. 
* Syntaxe : `bx dev <build|debug|run|test> --dockerfile-tools [path/to/dockerfile]`

### `image-name-tools`
{: #image-name-tools}

* Image à créer depuis `dockerfile-tools`.
* Syntaxe : `bx dev <build|debug|run|test> --image-name-tools [path/to/image-name]`

### `build-cmd-run`
{: #build-cmd-run}

* Paramètre utilisé afin de spécifier une commande pour générer le code
pour toutes les utilisations sauf DEBUG.

* Syntaxe : `bx dev <build|debug|run|test> --build-cmd-run [some.build.command]`

### `test-cmd`
{: #test-cmd}

* Paramètre utilisé afin de spécifier une commande pour tester le code dans
le conteneur des outils.

* Syntaxe : `bx dev <build|debug|run|test> --test-cmd [/the/test/command]`

### `trace`
{: #trace}

* Utilisez ce paramètre pour générer une sortie prolixe.

* Syntaxe : `bx dev <build|debug|run|test> --trace`


