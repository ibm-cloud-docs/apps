---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-03-16"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Création d'une application mobile à l'aide d'un kit de démarrage
{: #tutorial}

Vous pouvez créer un projet mobile à partir d'un kit de démarrage de base. Vous verrez comment installer les outils dont vous avez besoin et vous découvrirez les étapes nécessaires à l'exécution du projet dans Xcode et Android Studio.
{: shortdesc}

## Installation des outils
{: #before-you-begin}

Installez les [outils de développement](/docs/cli/idt/index.html#add-cli){: new_window}.


## Choix du mode de création de votre projet
{: #choose_how}

Vous pouvez créer un projet en utilisant l'une des méthodes suivantes :
- En utilisant la console [{{site.data.keyword.dev_console}}](#create-devex) basée sur le Web
- En utilisant le plug-in [{{site.data.keyword.dev_cli_notm}}](#create-cli) piloté par des commandes


## Création d'un projet à l'aide de la console {{site.data.keyword.dev_console}}
{: #create-devex}

1. Créez un projet de console {{site.data.keyword.dev_console}} dans {{site.data.keyword.Bluemix}}.

    1. Sur la page [Kits de démarrage ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.ng.bluemix.net/developer/appservice/starter-kits/) de la console {{site.data.keyword.dev_console}}, sélectionnez un kit de démarrage en fonction des fonctions souhaitées. Par exemple, pour une application de langage Watson, accédez à **Watson Language** et cliquez sur **Sélectionner un kit de démarrage**.

    2. Entrez un nom de projet. Pour ce tutoriel, utilisez `WatsonProject`.   

    3. Sélectionnez votre plateforme de langage. Pour ce tutoriel, utilisez `Swift`.

    4. Cliquez sur **Créer un projet**.

### Facultatif : Ajouter des services
{: #add-services}

1. Sélectionnez votre projet sur la page **Projets**. 

2. Cliquez sur **Ajouter un service**.

3. Sélectionnez le type de service souhaité. Pour ce tutoriel, sélectionnez **Sécurité** > **Suivant** > **ID app** > **Suivant**.

4. Entrez le nom de votre service, puis cliquez sur **Créer**.

5. Pour plus d'informations sur la configuration de l'authentification, voir [Configuration des fournisseurs d'identité ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](/docs/services/appid/identity-providers.html){: new_window}.

6. Pour plus d'informations sur la configuration d'analyse, voir [Initiation à {{site.data.keyword.mobileanalytics_short}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](/docs/services/mobileanalytics/index.html){: new_window}.

7. Pour plus d'informations sur la configuration de {{site.data.keyword.cloudant_short_notm}}, voir [Initiation à {{site.data.keyword.cloudant_short_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](/docs/services/Cloudant/index.html){: new_window}.

8. Pour plus d'informations sur la configuration d'{{site.data.keyword.objectstorageshort}}, voir [Initiation à {{site.data.keyword.objectstorageshort}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](/docs/services/ObjectStorage/index.html){: new_window}.

9. Pour plus d'informations sur l'ajout de notifications push, voir la documentation sur les [notifications push](/docs/services/mobilepush/c_overview_push.html#overview-push).

### Générer le code de votre projet
{: #generate-code}

1. Sélectionnez votre projet sur la page **Projets**. 

2. Cliquez sur **Télécharger le code** pour télécharger l'archive de votre projet. 


### Commencer à utiliser votre application
{: #code}

Commencez à utiliser le projet que vous avez téléchargé :

1. Développez le fichier archivé.

2. Accédez au nouveau répertoire de projet.

3. Utilisez le {{site.data.keyword.dev_cli_notm}} pour poursuivre.


## Création d'un projet à l'aide du {{site.data.keyword.dev_cli_notm}}
{: #create-cli}

1. Prenez soin d'installer le plug-in [{{site.data.keyword.dev_cli_short}}](/docs/cli/idt/index.html).

2. Dans votre invite de terminal, accédez au répertoire local de votre choix et exécutez la commande suivante :

	```
	bx dev create
	```
	{: codeblock}

3. Fournissez les valeurs suivantes, quand vous y êtes invité :

	* Sélectionnez le type de projet "Mobile Client", option 2
	* Sélectionnez le langage d'implémentation "iOS Swift", option 3
	* Sélectionnez le kit de démarrage "Mobile App: Basic", option 1
	* Entrez le nom suivant pour votre projet : `MobileBasicProject`

    Remarque : les numéros de sélection pourront changer dans le cadre d'améliorations apportées aux outils. 

4. Si vous voulez ajouter des services à votre projet, répondez par l'affirmative à la question qui vous est posée, puis répondez aux questions suivantes.

5. Lorsque votre projet `MobileBasicProject` est créé et sauvegardé, accédez au dossier `MobileBasicProject/MobileBasicProject-Swift`. 

### Exécution de votre projet Swift dans Xcode
{: #run_swift}

1. Ouvrez le fichier `README.md` dans un visualiser Markdown pour passer en revue les étapes nécessaires pour configurer votre projet. 

2. Ouvrez votre terminal et accédez au dossier de votre projet, puis exécutez les commandes suivantes :
    1. Exécutez `pod setup` si vous devez configurer votre référentiel CocoaPods. 
    2. Exécutez `pod update` si vous devez mettre à jour vos pods existants. 
    3. Exécutez `pod install` afin d'installer les pods pour votre projet.

3. Ouvrez votre espace de travail Xcode `<projectname>.xcworkspace`. 

4. Exécutez votre application. 

### Exécution de votre projet Cordova dans Xcode
{: #run_cordova_xcode}

Si vous avez choisi d'utiliser Cordova comme langage d'implémentation, suivez les instructions ci-dessous :

1. Ouvrez le fichier `README.md` dans un visualiseur Markdown pour configurer votre projet. 

2. Ouvrez votre projet `platforms/ios` dans Xcode.

3. Exécutez votre application. 


### Exécution de votre projet Cordova dans Android Studio
{: #run_cordova_studio}

Utilisez cette section si vous avez choisi d'utiliser Cordova comme plateforme de votre application mobile. 

1. Décompressez le fichier `BasicProject-Cordova.zip`.

2. Ouvrez le fichier `README.md` dans un visualiseur Markdown pour configurer votre projet. 

3. Ouvrez votre projet `platforms/android` dans Android Studio.

4. Exécutez votre application. 


### Exécution de votre projet Android dans Android Studio
{: #run_android}

Utilisez cette section si vous avez choisi d'utiliser Android comme plateforme de votre application mobile. 

1. Ouvrez le fichier `README.md` dans un visualiseur Markdown pour configurer votre projet. 

2. Ouvrez votre projet `BasicProject-Android` dans Android Studio.

3. Exécutez votre application. 
