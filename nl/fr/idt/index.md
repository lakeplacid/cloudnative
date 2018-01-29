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

Le plug-in {{site.data.keyword.dev_cli_long}} fournit une approche gérée par commande extensible pour créer, développer et déployer un projet Web avec le plug-in `dev`. 
Il est idéal pour les développeurs qui souhaitent utiliser la ligne de commande afin de contrôler le développement d'applications de microservice de bout en bout.

{: shortdesc}

Le plug-in {{site.data.keyword.dev_cli_notm}} utilise deux conteneurs pour faciliter la génération et le test de votre application. Le premier est le conteneur des outils, qui contient les utilitaires nécessaires pour générer et tester votre application. Le fichier Dockerfile pour ce conteneur est défini par le paramètre [`dockerfile-tools`](#command-parameters). Considérez-le
comme un conteneur de développement puisqu'il contient les outils généralement utiles pour le développement d'un environnement d'exécution particulier.

Le second conteneur est le conteneur d'exécution. Il peut être déployé pour être utilisé
dans {{site.data.keyword.Bluemix}}, par exemple. Par conséquent, un point
d'entrée démarrant votre application est défini. Lorsque vous choisissez d'exécuter
votre
application via le plug-in {{site.data.keyword.dev_cli_short}}, ce conteneur est utilisé. Le fichier Dockerfile pour ce conteneur est défini par le paramètre [`dockerfile-run`](#run-parameters).


## Ajout du plug-in {{site.data.keyword.dev_cli_notm}}
{: #add-cli}


### Prérequis
{: #prereq}

Vous devez satisfaire quelques exigences pour pouvoir explorer entièrement et
utiliser correctement le plug-in {{site.data.keyword.dev_cli_short}}, car celui-ci est
hautement extensible pour vous permettre de bénéficier de technologies complémentaires.


<!--1. Install the [Cloud Foundry CLI ![External link icon](../icons/launch-glyph.svg "External link icon")](https://github.com/cloudfoundry/cli#getting-started).-->

1. Installez
l'[interface
de ligne de commande {{site.data.keyword.Bluemix}}![External link icon](../icons/launch-glyph.svg "External link icon")](http://clis.ng.bluemix.net/ui/home.html).

2. Obtenez un ID [{{site.data.keyword.Bluemix_notm}}](https://www.bluemix.net).

3. Si vous prévoyez d'exécuter et de déboguer des applications localement, vous devez aussi installer [Docker ![External link icon](../icons/launch-glyph.svg "External link icon")](https://www.docker.com/get-docker).


### Avant de commencer
{: #before-install}

1. Connectez-vous à un noeud final d'API dans votre région [{{site.data.keyword.Bluemix_notm}}](/docs/overview/whatisbluemix.html#ov_intro_reg). Entrez, par exemple, la commande suivante pour vous connecter à la région {{site.data.keyword.Bluemix_notm}} Sud des Etats-Unis :

	```
	bx api https://api.ng.bluemix.net
	```
	{: codeblock}
	
2. Connectez-vous à {{site.data.keyword.Bluemix_notm}} en fournissant votre ID et votre mot de passe IBM :

	```
	bx login
	```
	{: codeblock}
	
	**Remarque :** si vos données d'identification sont rejetées, vous utilisez peut-être un ID fédéré. Procédez comme suit pour vous authentifier en utilisant un ID fédéré.
	
	<!-- 
	POINT TO IBM CLOUD CLI LOG IN DOCUMENTATION !!!
	
	This link does not work in production yet --> 
	
	1. Connectez-vous à [{{site.data.keyword.iamshort}} ![External link icon](../icons/launch-glyph.svg "External link icon")](https://www.bluemix.net/iam/#/apikeys){: new_window}.
	2. Sélectionnez **Créer une clé d'API**.
		* Entrez une description et un nom de clé d'API. 
	3. Téléchargez votre clé d'API. 
	4. Ouvrez le fichier et copiez la valeur depuis la zone `apiKey`.
	5. Connectez-vous avec la commande suivante :
	 
		```
		bx login --apikey <value>
		```
		{: codeblock}


### Installation
{: #installation}

1. Installez le plug-in [{{site.data.keyword.dev_cli_short}} ![External link icon](../icons/launch-glyph.svg "External link icon")](/docs/cli/reference/bluemix_cli/index.html#install_plug-in){: new_window} en exécutant la commande suivante :
 
	```
	bx plugin install dev
	```
	{: codeblock}

2. 	Vérifiez que l'installation du plug-in a abouti en exécutant la
commande suivante :
  
 
	```
	bx dev
	```
	{: codeblock}


