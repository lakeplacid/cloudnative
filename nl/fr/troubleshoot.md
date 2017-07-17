---

copyright:
  years: 2017
lastupdated: "2017-06-12"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}

# Traitement des incidents
{: #ts}

Certains problèmes connus rencontrés avec le plug-in {{site.data.keyword.dev_cli_notm}} sont documentés, et des solutions sont proposées.
{:shortdesc}

<!-- Add a headings and paragraphs about troubleshooting for your service, or a list of known issues and workarounds. -->

## Problèmes connus
{: #knownissues}

Les sections ci-dessous décrivent les problèmes connus et la façon dont ils peuvent être résolus.


### Erreur indiquant que le nom d'hôte est pris lorsque vous créez un projet avec un modèle non mobile
{: #hostname}

L'erreur suivante peut s'afficher si vous utilisez le plug-in {{site.data.keyword.dev_cli_short}} pour créer un projet depuis les modèles Application Web, BFF ou Microservice :

```
Le nom d'hôte <mon_nom_hôte> est déjà utilisé.
```
{: codeblock}


#### Cause
{: #hostname-cause}
   
Cette erreur est due à un jeton de connexion arrivé à expiration. 


#### Résolution
{: #hostname-resolution}

Connectez-vous à nouveau.

```
bx login
```
{: codeblock}


### Défaillances générales au niveau du plug-in {{site.data.keyword.dev_cli_short}}
{: #general}

L'erreur suivante peut s'afficher si vous utilisez les commandes create, delete, list ou code du plug-in {{site.data.keyword.dev_cli_short}} :

```
Echec de <commande> du projet.
```
{: codeblock}


#### Cause
{: #general-cause}
   
Cette erreur est due à un jeton de connexion arrivé à expiration. 


#### Résolution
{: #general-resolution}

Connectez-vous à nouveau.

```
bx login
```
{: codeblock}


### Erreur : aucune image de ce type lorsque vous exécutez un nouveau projet 
{: #nosuchimage}

L'erreur suivante peut s'afficher lorsque vous exécutez un projet alors que vous ne l'avez pas généré :

```
$ bx dev run testProject
L'option run-cmd n'a pas été spécifiée
Arrêt du conteneur 'testProject' en cours...
Le conteneur 'testProject' est introuvable
Création de l'image bx-dev-testProject basée sur Dockerfile en cours...
OK
Création d'un conteneur nommé 'testProject' à partir de cette image en cours...
ECHEC
Le conteneur 'testProject' n'a pas pu être créé :
Erreur : Pas d'image de ce type : bx-dev-testProject
```


#### Cause
{: #nosuchimage-cause}

Vous devez générer un projet avant de l'exécuter.  


#### Résolution
{: #nosuchimage-resolution}

Exécutez la commande suivante dans votre répertoire de projet en cours pour générer votre application :

```
bx dev build
```
{: codeblock}

Exécutez la commande suivante dans votre répertoire de projet en cours pour démarrer votre application :

```
bx dev run
```


### Erreur du courtier de services lorsque vous ajoutez la fonction {{site.data.keyword.objectstorageshort}} 
{: #os}

L'erreur suivante peut s'afficher si vous utilisez le plug-in {{site.data.keyword.dev_cli_short}} pour créer deux projets avec la fonction {{site.data.keyword.objectstorageshort}} :

```
FAILED
Service broker error: {"description"=>"You can not create this Object Storage instance. Each organization using the Object Storage service is limited to one instance of the Free plan."}
```
{: codeblock}


#### Cause
{: #os-cause}
   
Cette erreur est due au fait que le service {{site.data.keyword.objectstorageshort}} ne fournit qu'une instance du plan {{site.data.keyword.objectstorageshort}} gratuit.


#### Résolution
{: #os-resolution}

Choisissez un autre plan pour éviter cette erreur.


### Echec lors de l'obtention du code lors de la création d'un projet
{: #code}

L'erreur suivante peut s'afficher si vous utilisez le plug-in {{site.data.keyword.dev_cli_short}} pour créer un projet :
	
```
ECHEC
Le projet a été créé mais impossible d'obtenir le code
https://console.ng.bluemix.net/developer/projects/b22165f3-cbc6-4f73-876f-e33cbec199d4/code
```
{: codeblock}
	

#### Cause
{: #code-cause}

Cette erreur est due à un dépassement de délai interne.
	

#### Résolution
{: #code-resolution}

Vous pouvez obtenir le code de l'une des façons suivantes :

* Exécutez la commande suivante en utilisant l'interface de ligne de commande :

   ```
   bx dev code <your-project-name>
   ```
   {: codeblock}

   Remplacez `<your-project-name>` par le nom de projet que vous avez spécifié au cours de la création du projet. 

* Utilisez la console {{site.data.keyword.dev_console}}.

	1. Sélectionnez votre [projet ![External link icon](../icons/launch-glyph.svg "External link icon")](https://console.{DomainName}/developer/projects) dans la console {{site.data.keyword.dev_console}} et cliquez sur **Obtenir le code**.

	2. Cliquez sur la commande de génération de code.

	3. Une fois le code généré, cliquez sur la commande de téléchargement du code.


### Erreur lors de l'exécution de `bx dev run` pour les projets Node.js
{: #node}

L'erreur suivante peut s'afficher si vous exécutez `bx dev run` avec le plug-in {{site.data.keyword.dev_cli_short}} pour des projets Web ou BFF Node.js :

```
module.js:597
  return process.dlopen(module, path._makeLong(filename));
                 ^

Error: /app/node_modules/bluemix-autoscaling-agent/node_modules/appmetrics/appmetrics.node: invalid ELF header
    at Error (native)
    at Object.Module._extensions..node (module.js:597:18)
    at Module.load (module.js:487:32)
    at tryModuleLoad (module.js:446:12)

    at Function.Module._load (module.js:438:3)
    at Module.require (module.js:497:17)
    at require (internal/module.js:20:19)
    at Object.<anonymous> (/app/node_modules/bluemix-autoscaling-agent/node_modules/appmetrics/index.js:25:13)
    at Module._compile (module.js:570:32)
    at Object.Module._extensions..js (module.js:579:10)
```
{: codeblock}


#### Cause
{: #node-cause}
   
Cette erreur survient lorsque le module `appmetrics` est installé dans une architecture différente. Les modules npm natifs qui sont installés sur une architecture ne fonctionnent pas sur une autre architecture. Les images Docker incluses sont basées sur le noyau Linux.


#### Résolution
{: #node-resolution}

Supprimez le dossier `node_modules` et exécutez à nouveau `bx dev run`.


<!--
## Troubleshooting techniques
{: #tstechniques}
-->

<!-- Add a heading and content for how to get help and support. Use this template for beta and GA services:  -->


## Aide et support
{: #gettinghelp}

Si vous rencontrez des problèmes ou avez des questions au sujet de la console {{site.data.keyword.dev_console}} de {{site.data.keyword.Bluemix_notm}} ou du plug-in {{site.data.keyword.dev_cli_notm}}, vous pouvez obtenir de l'aide en recherchant des informations ou en posant des questions sur un forum. Vous pouvez aussi ouvrir un ticket de demande de service.

Lorsque vous publiez des questions sur les forums, vous pouvez les étiqueter de sorte que les équipes de développement {{site.data.keyword.Bluemix_notm}} soient notifiées. 

<!--Insert the appropriate Stack Overflow tag for your service for <service_keyword> in URL and text below:  -->

Si vous avez des questions techniques sur le développement ou le déploiement d'une application avec la console {{site.data.keyword.dev_console}} ou le plug-in {{site.data.keyword.dev_cli_notm}} :

* Postez votre question sur [stackoverflow![External link icon](../icons/launch-glyph.svg "External link icon")](http://stackoverflow.com/search?q=bluemix-dev-services+ibm-bluemix) et marquez votre question avec les étiquettes `bluemix-dev-services` et `ibm-bluemix`.
* Postez votre question sur [Slack ![External link icon](../icons/launch-glyph.svg "External link icon")](http://ibm-cloud-tech.slack.com/) sur le canal `bluemix-dev-services`. [Inscrivez-vous ![External link icon](../icons/launch-glyph.svg "External link icon")](http://ibm.biz/IBMCloudNativeSlack) maintenant.


<!--Insert the appropriate dW Answers tag for your service for <service_keyword> in URL below:  -->
<!--
* For questions about the service and getting started instructions, use the [IBM developerWorks dW Answers ![External link icon](../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/answers/topics/bluemix-dev-services/?smartspace=bluemix) forum. Include the  "bluemix-dev-services" and "bluemix" tags.
* -->

Pour plus d'informations sur l'utilisation des forums, voir la rubrique expliquant [comment obtenir de l'aide ![External link icon](../icons/launch-glyph.svg "External link icon")](/docs/support/index.html#getting-help).

Pour plus d'informations sur l'ouverture d'un ticket de demande de service {{site.data.keyword.IBM}}, sur les niveaux de support disponibles ou les niveaux de gravité des tickets, voir la rubrique expliquant [comment contacter le support![External link icon](../icons/launch-glyph.svg "External link icon")](/docs/support/index.html#contacting-support).

<!--Add a heading and content for how to get help. (Support not available for experimental.) Use this template for experimental services:  -->

