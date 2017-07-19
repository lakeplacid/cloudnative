---

copyright:
  years: 2016, 2017
lastupdated: "2017-07-19"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}

# Nouveautés de la console {{site.data.keyword.dev_console}} de {{site.data.keyword.Bluemix_notm}}
{: #what-is-new}


## Mise à jour de juin 2017 
{: #june-2017}

La mise à jour de juin 2017 de la console {{site.data.keyword.dev_console}}
de {{site.data.keyword.Bluemix}} comprend les modifications suivantes :


   * Désormais, les modules de démarrage Mobile gèrent la création des services {{site.data.keyword.ibmwatson}} requis et l'injection de vos données d'identification auprès des services dans le projet.

   * Le plug-in {{site.data.keyword.dev_cli_long}} a été mis à jour avec de nouvelles fonctions. Pour plus d'informations, voir [What's included in the {{site.data.keyword.Bluemix_notm}} CLI {{site.data.keyword.dev_cli_short}} version 0.1.12 ![External link icon](../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/blogs/bluemix/2017/06/whats-included-bluemix-cli-developer-plug-version-0-1-12/).

## Mise à jour de mars 2017
{: #mar-2017}

La mise à jour de mars 2017 de la console {{site.data.keyword.dev_console}} de {{site.data.keyword.Bluemix}} comprend les modifications suivantes :

   * Le tableau de bord {{site.data.keyword.Bluemix_notm}} Mobile est devenu la console {{site.data.keyword.dev_console}} de {{site.data.keyword.Bluemix}}.
   * La procédure de création de projets est modifiée pour inclure les types de modèle de serveur Application Web, BFF et Microservice avec prise en charge de Node.js, Java et Swift.
   * L'intégration au nouveau service optimisé {{site.data.keyword.appid_full}} fournit une authentification pour les projets Web et mobiles.
   * Désormais, vous pouvez générer des SDK pour vos projets en utilisant le [plug-in de générateur de SDK](sdk_cli.html). La génération de SDK dans la console {{site.data.keyword.dev_console}} n'est disponible que pour les projets mobiles.
   * Désormais, vous pouvez créer des projets en utilisant le plug-in [{{site.data.keyword.dev_cli_short}}](dev_cli.html).


## Mise à jour de janvier 2017
{: #jan-2017}

La mise à jour de janvier 2017 du tableau de bord {{site.data.keyword.Bluemix_notm}} Mobile comprend les modifications suivantes :

   * Au 31 janvier, les modules de démarrage pour l'interface utilisateur deviennent obsolètes. Les projets existants qui ont été crées depuis un module de démarrage pour l'interface utilisateur peuvent être utilisés jusqu'au 30 avril 2017. Pour plus d'informations sur les étapes de migration et les dates de retrait, voir l'[article de blogue annonçant la dépréciation ![External link icon](../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/blogs/bluemix/2017/01/bluemix-mobile-dashboard-update/). 
{: deprecated}
   * Vous pouvez maintenant mettre à jour votre type de module de démarrage de projet au lieu de supprimer votre projet et d'en créer un nouveau.
   * Vous pouvez désormais créer votre projet avec un module de démarrage pour le code [Watson Conversation](tutorial_conversation.html).
   * Là où il est pris en charge, vous pouvez maintenant générer un SDK pour votre projet.
   * Vous pouvez désormais ajouter vos instances de [calcul](sdk_compute.html) et générer des SDK client à ajouter à votre projet.


## Mise à jour de décembre 2016
{: #dec-2016}

La mise à jour de novembre 2016 du tableau de bord {{site.data.keyword.Bluemix_notm}} Mobile comprend les modifications suivantes :

   * Vous pouvez maintenant retirer d'un projet un service connecté de façon à pouvoir le supprimer ou le réutiliser avec un autre projet. 
   * Vous pouvez désormais ajouter un service existant à un projet.
   * Vous pouvez maintenant créer ou connecter un service CloudantNoSQL existant en tant que source de données quand vous utilisez un module de démarrage pour le code.
   * Là où il est pris en charge, vous pouvez désormais créer ou connecter un service Object Storage existant comme source de données pour votre projet.
   * Vous pouvez maintenant personnaliser la conception de la navigation de l'application que vous créez avec un module de démarrage pour l'interface utilisateur. 
   

## Mise à jour de novembre 2016
{: #nov-2016}

La mise à jour de novembre 2016 du tableau de bord {{site.data.keyword.Bluemix_notm}} Mobile comprend les modifications suivantes :

   * Vous pouvez à présent générer des artefacts SDK pour vos projets depuis la page **Code**.
   * Cordova est à présent pris en charge pour le module de démarrage Basic.
   * Désormais, vous pouvez [signaler des événements de réseau ![External link icon](../icons/launch-glyph.svg "External link icon")](/docs/services/mobileanalytics/sdk.html#network-requests){: new_window} et [surveiller les demandes de réseau ![External link icon](../icons/launch-glyph.svg "External link icon")](/docs/services/mobileanalytics/app-monitoring.html#monitor-network-requests){: new_window} dans la page **Demandes de réseau** de la console {{site.data.keyword.mobileanalytics_short}}. 
   * Vous pouvez désormais [exporter des données dans dashDB ![External link icon](../icons/launch-glyph.svg "External link icon")](/docs/services/mobileanalytics/app-monitoring.html#dashdb){: new_window} dans la console {{site.data.keyword.mobileanalytics_short}}.


## Mise à jour de novembre 2016
{: #oct-2016}

La mise à jour d'octobre 2016 du tableau de bord {{site.data.keyword.Bluemix_notm}} Mobile comprend les modifications suivantes :

   * Vous pouvez désormais ajouter directement des fonctionnalités {{site.data.keyword.mobilepushshort}} et Analytics à votre projet depuis le tableau de bord.
   * Désormais, des modules de démarrage pour le code sont disponibles. 
   * Vous pouvez ajouter l'authentification aux projets que vous avez créés à partir d'un module de démarrage de code.
   * Swift est désormais pris en charge.


### L'analyse
{: #analytics notoc}

   * Le mode démonstration est activé par défaut lorsque vous ajoutez la
fonction Analyse. Vous pouvez désactiver le mode démonstration pour visualiser
l'analyse après l'exécution de votre application.


### Générateur d'interface graphique
{: #ui_builder notoc}

   * La fonctionnalité **{{site.data.keyword.mobilepushshort}}** est désormais accessible depuis le projet.
   * L'onglet **Paramètres du projet** est renommé en **Paramètres**.
   * L'onglet **Authentification** est renommé en **Accès utilisateur**.


### Code
{: #code notoc}

   * Désormais, le code Objective-C et Swift généré pour iOS utilise CocoaPods pour la gestion des dépendances ; par conséquent, vous devez l'installer. Pour installer CocoaPods, exécutez `sudo gem install cocoapods`. Une fois CocoaPods installé, exécutez `pod setup` pour le configurer (si ne l'est pas déjà). Exécutez ensuite `pod install` pour télécharger et installer les dépendances de projet avant d'ouvrir votre fichier `.xcworkspace` dans Xcode. D'autres détails sont disponibles dans le fichier `README.md` de l'archive du code téléchargé. Pour plus d'informations, voir [Outils de développement prérequis](get_code.html#prereq-dev-tools).

Revenez fréquemment pour être tenu au courant des nouvelles mises à jour.
