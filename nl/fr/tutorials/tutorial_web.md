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

# Tutoriel de bout en bout du module de démarrage Web Basic 
{: #tutorial}

Le tutoriel de bout en bout ci-dessous vous guide tout au long des étapes de création d'un projet depuis le module de démarrage Web Basic. Il présente l'installation des outils prérequis et la procédure d'exécution du code du projet. 


## Installation des outils de développement
{: #dev_tools}

Prenez soin d'installer les [outils de développement prérequis![External link icon](../icons/launch-glyph.svg "External link icon")](get_code.html#prereq-dev-tools){: new_window}.


## Choisissez la façon dont vous allez créer votre projet 
{: #choose_how}

Vous pouvez créer un projet en utilisant la console [{{site.data.keyword.dev_console}}](#create-devex) reposant sur le Web ou le plug-in [{{site.data.keyword.dev_cli_notm}}](#create-cli) géré par commande. Une fois le projet créé, vous pouvez l'[exécuter](#run).


## Création d'un projet en utilisant la console {{site.data.keyword.dev_console}}
{: #create-devex}

1. Créez un projet dans la console {{site.data.keyword.dev_console}} de {{site.data.keyword.Bluemix}} :

	1. Depuis la page [**Initiation** ![External link icon](../icons/launch-glyph.svg "External link icon")](https://console.ng.bluemix.net/developer/getting-started/) dans la console {{site.data.keyword.dev_console}}, cliquez sur **Créer un projet**.

		Vous pouvez également cliquer sur **Créer un projet** dans la page **Projets**. 

	2. Sélectionnez **Appli Web**, puis cliquez sur **Suivant**.

	3. Sélectionnez **Basic Web**, puis cliquez sur **Suivant**.

	4. Entrez le nom de votre projet. Pour ce tutoriel, utilisez `WebBasicProject`.   

	5. Entrez un nom d'hôte unique, par exemple vos initiales, plus `-devhost`. Exemple :
	
	 ```
	 abc-devhost
 	     ```

	6. Sélectionnez votre plateforme de langage. Pour ce tutoriel, utilisez `Swift`.
   
	7. Cliquez sur **Créer**.

2. Facultatif : ajoutez la fonctionnalité Données :

	1. Cliquez sur **Afficher** pour **Données** sur la page **Présentation du projet**.

      Vous pouvez aussi sélectionner **Créer** ou **Ajouter des instances existantes** dans la page **Fonctions > Données**. 

   2. Entrez le nom de votre service et cliquez sur **Créer**.

3. Générez votre code de projet :

	1. Cliquez sur **Obtenir le code** dans la page **Présentation du projet** pour sélectionner votre langue. 
   
		Vous pouvez également cliquer sur la page **Code**.
      
	2. Cliquez sur **Générer le code**.
   
	3. Lorsque la génération du code du projet est terminée, cliquez sur **Télécharger le code** pour télécharger l'archive du projet.

4. Commencez à utiliser le projet que vous avez téléchargé :

	1. Développez le fichier archivé.
	
	2. Accédez au nouveau répertoire de projet.
	
	3. Utilisez le plug-in {{site.data.keyword.dev_cli_notm}} pour poursuivre.

5. Facultatif : [mettez à jour votre projet](project_overview_page.html#update_language) pour générer un nouveau langage.


## Création d'un projet en utilisant le plug-in {{site.data.keyword.dev_cli_notm}}
{: #create-cli}

1. Prenez soin d'installer le plug-in [{{site.data.keyword.dev_cli_short}}](dev_cli.html).

2. Dans votre invite de terminal, accédez au répertoire local de votre choix et exécutez la commande suivante :
  
	```
	bx dev create
	```
	{: codeblock}

3. Fournissez les valeurs suivantes, quand vous y êtes invité :

	* Sélectionnez un modèle : 1 (pour Web)
	* Sélectionnez un module de démarrage : 1 (pour Basic Web)
	* Sélectionnez un langage : 2 (pour Swift)
	* Entrez le nom de votre projet : `WebBasicProjectCLI`
	* Entrez un nom d'hôte pour votre projet : `abc-devhost`
	  * Entrez un nom d'hôte unique, par exemple vos initiales, plus `-devhost`. Exemple :
	
	     ```
	     abc-devhost
 	     ```

4. Une fois votre projet `WebBasicProjectCLI` sauvegardé, accédez au dossier `WebBasicProjectCLI`.

5. Ajoutez votre propre code, puis générez et exécutez le projet.

	
	1. Générez le projet avec la commande suivante : 
 
		```
		bx dev build
		```
		{: codeblock}
	 
	2. Exécutez le projet avec la commande suivante :
 
		```
		bx dev run
		```
		{: codeblock}


## Exécution d'un projet Web
{: #run}

Vous pouvez exécuter l'application localement sur votre système hôte si vous installez les outils de génération nécessaires ou en utilisant le support de conteneur disponible dans le plug-in {site.data.keyword.dev_cli_notm}}.



### Utilisation du plug-in {{site.data.keyword.dev_cli_short}}
{: #dev notoc}

1. Installez les dépendances de noeud :

  ```
  npm install
  ```
  {: codeblock}

2. Incluez votre code frontend dans un module :

  ```
  gulp
  ```
  {: codeblock}

3. Pour générer le projet dans votre répertoire de projet en cours, entrez la commande suivante :

  ```
  bx dev build
  ```
  {: codeblock}

4. Pour exécuter le projet dans votre répertoire de projet en cours, entrez la commande suivante :


  ```
  bx dev run
  ```
  {: codeblock}

5. Dans votre navigateur, ouvrez l'URL `http://localhost:8080`.


## Exécution de votre projet dans Xcode
{: #Xcode}

1. Créez un projet Xcode.

	Avant de pouvoir développer dans Xcode, vous devez utiliser le gestionnaire de package Swift pour générer un projet Xcode.
	
	```
	swift project generate-xcodeproj
	```
	{: codeblock}

2. Rendez exécutable votre cible active :

	Ouvrez votre projet sous Xcode et assurez-vous que votre cible active est exécutable. Vous pouvez maintenir la touche d'option enfoncée et cliquer sur le menu déroulant pour sélectionner l'exécutable actif de votre choix. 

3. Cliquez sur **run**.

4. Dans votre navigateur, ouvrez l'URL `http://localhost:8080`.

