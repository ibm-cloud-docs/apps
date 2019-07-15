---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-20"

keywords: apps, mobile, mobile app, starter kit, developer tools, devops toolchain, toolchain, create mobile app, mobile starter kit, android, ios, swift, xcode

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Création d'une application mobile
{: #tutorial-mobile}

{{site.data.keyword.cloud}} inclut des kits de démarrage mobiles vous permettant de créer plus facilement et plus rapidement une application mobile. Sélectionnez un langage, une infrastructure et des outils dans les kits de démarrage mobiles afin de commencer à utiliser une application préconfigurée. Ou bien, vous pouvez utiliser un kit de démarrage de base pour créer une application mobile personnalisée.
{: shortdesc}

## Avant de commencer
{: #prereqs-mobile}

Installez l'[interface de ligne de commande {{site.data.keyword.dev_cli_long}}](/docs/cli?topic=cloud-cli-getting-started).

## Création d'une application mobile à l'aide d'un kit de démarrage préconfiguré
{: #create-mobile}

Pour créer une application mobile à l'aide d'un kit de démarrage préconfiguré, procédez comme suit :

1. Sur la page [Kits de démarrage mobiles](https://{DomainName}/developer/mobile/starter-kits){: new_window} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe") dans {{site.data.keyword.dev_console}}, sélectionnez un kit de démarrage correspondant aux fonctions dont vous avez besoin. Sélectionnez, par exemple, **Watson Visual Recognition**.
2. Entrez le nom de votre application. Pour ce tutoriel, utilisez `WatsonApp`.
3. Facultatif. Créez des étiquettes pour classer votre application. Pour plus d'informations, voir [Utilisation d'étiquettes](/docs/resources?topic=resources-tag).
4. Sélectionnez votre plateforme. Pour ce tutoriel, utilisez **Swift**. Certains kits de démarrage peuvent être disponibles dans un seul langage.
5. Sélectionnez votre plan de tarification. Utilisez l'option **Lite** pour ce tutoriel. Si des services sont requis, ils sont automatiquement définis dans le kit de démarrage. 
6. Cliquez sur **Créer**.

## Création d'une application mobile à l'aide d'un kit de démarrage de base
{: #create-mobile-basic}

Pour créer une application mobile à l'aide d'un kit de démarrage de base, procédez comme suit :

1. Sur la page [Kits de démarrage mobiles](https://{DomainName}/developer/mobile/starter-kits){: new_window} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe") dans {{site.data.keyword.dev_console}}, sélectionnez la vignette **Créer une appli**.
2. Entrez un nom pour votre application. Pour ce tutoriel, tapez `CustomMobile`.
3. Vous pouvez éventuellement créer des étiquettes pour classer votre application. Pour plus d'informations, voir [Utilisation d'étiquettes](/docs/resources?topic=resources-tag).
4. Sélectionnez **Créer une application** comme point de départ.
5. Sélectionnez **Mobile** comme type d'application.
6. Sélectionnez votre langage et votre infrastructure. Certains kits de démarrage peuvent être disponibles dans un seul langage.
7. Sélectionnez votre plan de tarification. Vous pouvez utiliser l'option gratuite pour ce tutoriel.
8. Cliquez sur **Créer**.

## Ajout de services (facultatif)
{: #resources-mobile}

En fonction du kit de démarrage sélectionné, il est possible que certains services soit déjà connectés à votre application. Vous pouvez ajouter des services qui améliorent votre application avec la puissance cognitive de Watson, ajoutent des services mobiles ou des services de sécurité. Pour ce tutoriel, ajoutez un emplacement pour gérer vos données.

Pour ajouter un service à votre application, procédez comme suit :

1. Sur la page **Détails de l'application**, cliquez sur **Créer un service**.
2. Sélectionnez le type de service souhaité. Sélectionnez, par exemple, **Bases de données** > **Suivant** > **Cloudant** > **Suivant**.
3. Sélectionnez votre plan de tarification. Utilisez l'option **Lite** pour ce tutoriel. 
4. Cliquez sur **Créer**.

## Téléchargement du code
{: #mobile-download-code}

Pour télécharger le code de votre application et l'utiliser en local, procédez comme suit :

1. Sur la page **Détails de l'application**, cliquez sur **Télécharger le code**.
2. Importez l'application dans votre environnement de développement intégré.
3. Modifiez puis sauvegardez le code.

## Exécution de votre application mobile
{: #run-mobile-app}

### Exécution de votre application Swift dans Xcode
{: #run_swift}

Si vous utilisez iOS Swift comme langage d'implémentation, procédez comme suit :

1. Ouvrez le fichier `README.md` dans un visualiseur Markdown afin de passer en revue les étapes nécessaires pour configurer votre application.
2. Ouvrez votre terminal et accédez au dossier de votre application, puis exécutez les commandes suivantes :
    1. Exécutez `pod setup` si vous devez configurer votre référentiel CocoaPods.
    2. Exécutez `pod update` si vous devez mettre à jour vos pods existants.
    3. Exécutez `pod install` pour installer les pods de votre application.
3. Ouvrez votre espace de travail Xcode `<appname>.xcworkspace`.
4. Exécutez votre application.

### Exécution de votre application Android dans Android Studio
{: #run_android}

Si vous utilisez Android comme plateforme de votre application mobile, procédez comme suit :

1. Ouvrez le fichier `README.md` dans un visualiseur Markdown pour configurer votre application.
2. Ouvrez votre application `BasicProject-Android` dans Android Studio.
3. Exécutez votre application.

### Exécution de votre application Cordova dans Xcode
{: #run_cordova_xcode}

Si vous utilisez Cordova comme langage d'implémentation, procédez comme suit :

1. Ouvrez le fichier `README.md` dans un visualiseur Markdown pour configurer votre application.
2. Ouvrez votre application `platforms/ios` dans Xcode.
3. Exécutez votre application.

### Exécution de votre application Cordova dans Android Studio
{: #run_cordova_studio}

Si vous utilisez Cordova comme plateforme de votre application mobile, procédez comme suit :

1. Décompressez le fichier `BasicProject-Cordova.zip`.
2. Ouvrez le fichier `README.md` dans un visualiseur Markdown pour configurer votre application.
3. Ouvrez votre application `platforms/android` dans Android Studio.
4. Exécutez votre application.

## Informations connexes
{: #related-mobile}

Pour en savoir plus sur les applications mobiles, explorez les tutoriels suivants :

 * [Développement d'une application mobile iOS avec Push Notifications](/docs/tutorials?topic=solution-tutorials-ios-mobile-push-analytics)
 * [Développement d'une application mobile native Android avec Push Notifications](/docs/tutorials?topic=solution-tutorials-android-mobile-push-analytics)
 * [Application mobile avec back-end sans serveur ](/docs/tutorials?topic=solution-tutorials-serverless-mobile-backend)
