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

# Tutoriel de bout en bout du module de démarrage BFF Basic 
{: #tutorial}

Le tutoriel de bout en bout ci-après vous guide tout au long des étapes de
création d'un projet
depuis le module de démarrage BFF Basic. Il présente l'installation des
outils prérequis et la procédure d'exécution du code du projet.



## Installation des outils de développement
{: #dev_tools}

Prenez soin d'installer les [outils de développement prérequis![External link icon](../icons/launch-glyph.svg "External link icon")](get_code.html#prereq-dev-tools){: new_window}.


## Choisissez la façon dont vous allez créer votre projet 
{: #choose_how}

Vous pouvez créer un projet en utilisant la console [{{site.data.keyword.dev_console}}](#create-devex) reposant sur
le Web ou le plug-in [{{site.data.keyword.dev_cli_notm}}](#create-cli) géré par
commande. Une fois le projet créé, vous pouvez l'[exécuter](#running-bff).


## Création d'un projet en utilisant la consle {{site.data.keyword.dev_console}}
{: #create-devex}

1. Créez un projet dans la console {{site.data.keyword.dev_console}} de {{site.data.keyword.Bluemix}}.

	1. Depuis la page
[**Initiation** ![External link icon](../icons/launch-glyph.svg "External link icon")](https://console.ng.bluemix.net/developer/getting-started/) dans la console {{site.data.keyword.dev_console}}, cliquez sur **Créer un projet**.

		Vous pouvez également cliquer sur **Créer un projet** dans
la page **Projets**. 

	2. Sélectionnez **BFF (Backend for Frontend)**, puis cliquez
sur **Suivant**.

	3. Sélectionnez **Basic Backend**, puis cliquez sur
**Suivant**.

	4. Entrez le nom de votre projet. Pour ce tutoriel, utilisez `BFFProject`.   

	5. Entrez un nom d'hôte unique, par exemple vos initiales, plus `-devhost`. Exemple :
	
	 ```
	 abc-devhost
	 ``` 

	6. Sélectionnez votre plateforme de langage. Pour ce tutoriel, utilisez `Node`.
   
	7. Cliquez sur **Créer**.

2. Facultatif : ajoutez la fonctionnalité Données.

	1. Cliquez sur **Afficher** pour
**Données** dans la page **Présentation du projet**.

      Vous pouvez aussi sélectionner **Créer** ou
**Ajouter des instances existantes** dans la page
**Fonctions > Données**.


   2. Entrez le nom de votre service et cliquez sur
**Créer**.

3. Générez votre code de projet :

	1. Cliquez sur **Obtenir le code** dans la page
**Présentation du projet** pour sélectionner votre langue.

   
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

	* Sélectionnez un modèle : 3 (pour Backend for Frontend)
	* Sélectionnez un module de démarrage : 1 (pour Basic Backend)
	* Sélectionnez un langage : 1 (pour Node)
	* Entrez le nom de votre projet : `BFFProjectCLI`
	* Entrez un nom d'hôte pour votre projet : `abc-devhost`
	  * Entrez un nom d'hôte unique, par exemple vos initiales, plus
`-devhost`. Exemple :
	
	     ```
	     abc-devhost
	     ```
	  
4. Une fois votre projet `BFFProjectCLI` sauvegardé, vous pouvez
accéder au dossier `BFFProjectCLI`. 

5. Ajoutez votre propre code, puis générez et exécutez le projet.

 
	1. Générez votre projet avec la commande suivante : 

		```
		bx dev build
		```
		{: codeblock}
		 
	2. Exécutez votre projet avec la commande suivante :

 		```
		bx dev run
		```
		{: codeblock}


## Exécution d'un projet BFF
{: #running-bff}

Vous pouvez exécuter l'application localement sur votre système hôte si vous installez les outils de génération nécessaires ou en utilisant le support de conteneur disponible dans le plug-in {{site.data.keyword.dev_cli_notm}}.


### Utilisation du plug-in IBM Cloud
{: #using-blumix}

1. Pour générer le projet dans votre répertoire de projet en cours, entrez la commande suivante :
```
   bx dev build
   ```
   {: codeblock}

2. Pour exécuter le projet dans votre répertoire de projet en cours, entrez la commande suivante :
```
   bx dev run
   ```
   {: codeblock}

3. Vous pouvez exécuter curl sur votre serveur avec :
```
   curl http://localhost:8080
   ```
   {: codeblock}

4. Vous pouvez afficher le document d'API sur votre serveur à l'adresse suivante :
```
   http://localhost:8080/swagger/api
   ```
   {: codeblock}

5. Vous pouvez explorer l'API sur votre serveur à l'adresse suivante :
   ```
   http://localhost:8080/explorer
   ```
   {: codeblock}
