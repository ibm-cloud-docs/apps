---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-23"

keywords: apps, starter kit, create app starter kit, basic app, simple app

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Création d'une application à l'aide d'un kit de démarrage
{: #tutorial-starterkit}

Vous pouvez utiliser un kit de démarrage pour que votre application démarre rapidement et pour la préparer à des développements futurs. Choisissez un kit de démarrage et un langage de programmation, créez une application, puis configurez une chaîne d'outils DevOps pour déployer automatiquement votre application. Vous pouvez également télécharger le code pour un examen immédiat.
{: shortdesc}

Vous pouvez créer une application en utilisant des kits de démarrage, notamment un kit vide si vous voulez personnaliser vous-même les options de génération. Quoi qu'il en soit, une chaîne d'outils est automatiquement créée pour le déploiement de votre application. Vous pouvez également télécharger le code pour un examen immédiat.

{{site.data.keyword.cloud_notm}} propose des portails de développeur s'appliquant à différents domaines d'intérêt (par exemple, Watson, la sécurité ou la finance) ou un canal de vente numérique (par exemple, les applications mobiles ou Web). Vous pouvez accéder à ces portails à partir de l'icône **Menu** ![Icône Menu](../../icons/icon_hamburger.svg).

Chaque portail de développeur fournit des kits de démarrage adaptés au domaine d'intérêt du portail. Les portails incluent des flux de travaux cohérents et intuitifs pour la création d'une application fonctionnelle prête pour la production en quelques minutes.

Les kits de démarrage sont disponibles dans de nombreuses catégories, telles que les suivantes :
* [Watson ](https://{DomainName}/developer/watson/dashboard){: new_window} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")
* [Apple ](https://{DomainName}/developer/appledevelopment/dashboard){: new_window} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")
* [Mobile ](https://{DomainName}/developer/mobile/dashboard){: new_window} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")
* [Application Web ](https://{DomainName}/developer/appservice/dashboard){: new_window} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")
* [Sécurité ](https://{DomainName}/developer/security/dashboard){: new_window} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")
* [Finance ](https://{DomainName}/developer/finance/dashboard){: new_window} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")

[En savoir plus](/docs/apps?topic=creating-apps-starter-kits) sur les kits de démarrage.

## Etape 1. Créer une application
{: #create-starterkit}

1. A partir du tableau de bord [{{site.data.keyword.cloud}} ](https://{DomainName}){: new_window} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe"), cliquez sur l'icône **Menu** ![Icône Menu](../../icons/icon_hamburger.svg) > **Applications Web**.

2. Cliquez sur **Initiation** dans la section **Démarrer à partir du Web**.

3. Sélectionnez un kit de démarrage de votre choix, lisez les détails, puis cliquez sur **Créer**.
    
    Pour savoir ce qui est inclus dans le kit de démarrage, développez la vignette sur le tableau de bord des [kits de démarrage de service d'application ](https://{DomainName}/developer/appservice/starter-kits){: new_window} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe"). L'option de kit de démarrage "Créer une appli" peut être utilisée en tant qu'application Starter vide puis être personnalisée afin de répondre à vos besoins.
    {: tip}

4. Donnez un nom à votre application, sélectionnez un groupe de ressources, créez éventuellement des étiquettes, sélectionnez votre langage, puis cliquez sur **Créer**.
    
    C'est un bon début ! Vous venez de créer une application.

Pour inspecter votre code, cliquez sur **Télécharger le code** sur la page **Détails de l'application**. Consultez le fichier `README.md` se trouvant dans le fichier compressé téléchargé pour savoir si vous devez exécuter d'autres actions pour rendre votre application de démarrage opérationnelle.
{: tip}

Pour plus d'informations, consultez les rubriques suivantes :
 * [Création d'une application Web basique avec un kit de démarrage](/docs/apps/tutorials?topic=creating-apps-tutorial-webapp)
 * [Utilisation d'étiquettes](/docs/resources?topic=resources-tag)

## Etape 2. Ajouter des services
{: #resources-starterkit}

Vous pouvez ajouter des services qui améliorent votre application avec la puissance cognitive de Watson, ajoutent des services mobiles ou des services de sécurité. Pour ce tutoriel, ajoutez un emplacement pour gérer vos données.

1. Sur la page **Détails de l'application**, cliquez sur **Ajouter un service**.
2. Sélectionnez le type de service souhaité. Par exemple, sélectionnez **Données** > **Suivant** > **Cloudant** > **Suivant**.
3. Sélectionnez votre plan de tarification. Il existe une option gratuite que vous pouvez utiliser pour ce tutoriel.
4. Cliquez sur **Créer**.

## Etape 3. Déployer dans {{site.data.keyword.cloud_notm}}
{: #deploy-starterkit}

Cliquez sur **Configurer la distribution continue** sur la page **Détails de l'application**, sélectionnez une cible de déploiement et cliquez sur **Créer**. {{site.data.keyword.cloud_notm}} crée automatiquement une chaîne d'outils ouverte complétée par un référentiel Git et un pipeline de distribution continue.

L'activation d'une chaîne d'outils permet de créer un environnement de développement basé sur une équipe pour votre application. Lorsque vous créez une chaîne d'outils, le service d'application crée un référentiel Git dans lequel vous pouvez afficher le code source, cloner votre application, créer et gérer des problèmes. Vous avez également accès à un environnement de lab dédié Git et à un pipeline de distribution continue. Ces éléments sont personnalisés en fonction de l'environnement de déploiement choisi, [Kubernetes](/docs/containers?topic=containers-getting-started), [Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) ou [Virtual Server (VSI)](/docs/vsi?topic=virtual-servers-getting-started-with-virtual-servers).

Une fois que vous avez sélectionné votre cible de déploiement, ouvrez le composant Pipeline de votre nouvelle chaîne d'outils pour démarrer le processus de génération et de déploiement initial afin que vous puissiez voir votre application après quelques minutes.

Toutes les chaînes d'outils créées à partir d'un tableau de bord de développeur {{site.data.keyword.cloud_notm}} sont configurées pour un déploiement automatique.
{: note}

Pour déployer votre application avec la ligne de commande, utilisez `ibmcloud dev deploy`. Pour plus d'informations, voir [Création et déploiement d'applications à l'aide de l'interface de ligne de commande](/docs/apps?topic=creating-apps-create-deploy-app-cli).
