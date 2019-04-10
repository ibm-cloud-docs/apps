---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-18"

keywords: apps, Mendix, starter kit, developer tools, Mendix app

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Création d'applications à l'aide de Mendix
{: #create-mendix}

Mendix est un environnement et un ensemble d'outils de développement qui utilise peu de code et vous permet de distribuer plus rapidement des applications multi-dispositif, avec moins de ressources de développement, qui s'exécutent sur {{site.data.keyword.cloud}}. Si vous sélectionnez un kit de démarrage Mendix qui utilise peu de code, vous êtes guidé pour configurer votre compte sur la plateforme Mendix, démarrer votre projet et sélectionner votre cible de déploiement dans Cloud Foundry ou sur votre cluster Kubernetes.
{: shortdesc}

## Sélection d'un kit de démarrage
{: #starterkit-mendix}

1. Sur le tableau de bord [{{site.data.keyword.cloud_notm}} App Service ](https://{DomainName}/developer/appservice/dashboard){: new_window} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe"), cliquez sur **Initiation**.
2. Sélectionnez un kit de démarrage Mendix qui utilise peu de code à partir de l'une des catégories suivantes :
  * [Mobile ](https://{DomainName}/developer/appservice/starter-kits/mendix-mobile-app){: new_window} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")
  * [Application Web Watson ou mobile ](https://{DomainName}/developer/appservice/starter-kits/mendix-web-or-mobile-app-with-watson){: new_window} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")
  * [Application Web ](https://{DomainName}/developer/appservice/starter-kits/mendix-web-app){: new_window} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")
3. Cliquez sur **Créer une application**.
4. Sur la page **Détails de l'application**, nommez votre application et créez éventuellement des étiquettes pour classer votre application. Pour plus d'informations, voir [Utilisation d'étiquettes](/docs/resources?topic=resources-tag).
5. Cliquez sur **Créer**.


## Autoriser IBM à créer votre projet sur Mendix et des comptes liés
{: #link-mendix-account}

Si vous n'utilisez pas encore Mendix avec {{site.data.keyword.cloud_notm}}, vous êtes dirigé vers la plateforme Mendix pour vous connecter et autoriser {{site.data.keyword.cloud_notm}} à créer un nouveau projet sur la plateforme Mendix en votre nom. Ce projet est lié à {{site.data.keyword.cloud_notm}}, ainsi, les déploiements sont automatiquement dirigés vers {{site.data.keyword.cloud_notm}}.

1. Si le message suivant s'affiche : "Pour créer une application, un compte utilisateur Mendix est requis. Voulez-vous lier votre compte maintenant ?", cliquez sur **Lier le compte**.
2. Sur la page de confirmation Mendix, sélectionnez **J'accepte les règles de confidentialité et les termes de Mendix**, puis cliquez sur **Confirmer**.
3. Lorsque vous y êtes invité, indiquez votre adresse électronique, votre mot de passe et votre pays, puis cliquez sur **Créer**.
4. Sur la page **Autoriser l'accès à votre compte Mendix**, cliquez sur **Autoriser**.

Une fois l'autorisation effectuée, votre navigateur revient sur l'application Mendix que vous êtes en train de créer. La page **Sélectionner une cible de déploiement** s'affiche.

## Sélection d'une cible de déploiement pour votre application Mendix
{: #select-deployment}

1. Sur la page **Sélectionner une cible de déploiement**, sélectionnez Cloud Foundry ou l'un de vos clusters Kubernetes qui s'exécutent sur {{site.data.keyword.cloud_notm}}. Si votre compte a accès à {{site.data.keyword.cfee_full_notm}}, vous pouvez sélectionner un déployeur Cloud Foundry de type **[Public Cloud](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf)** ou **[Enterprise Environment](/docs/cloud-foundry-public?topic=cloud-foundry-public-cfee)**, que vous pouvez utiliser pour créer et gérer des environnements isolés pour l'hébergement de vos applications Cloud Foundry exclusivement pour votre entreprise.
2. Facultatif. Si vous ne possédez pas de cluster Kubernetes, vous pouvez en créer un maintenant.
3. Sur la page **Configurer la chaîne d'outils**, sélectionnez votre région et votre groupe de ressources, puis cliquez sur **Créer**.

Une chaîne d'outils DevOps est créée. La chaîne d'outils intègre votre projet Mendix au sein de la plateforme Mendix dans votre environnement {{site.data.keyword.cloud_notm}}. Une application par défaut est déployée sur votre cible de déploiement afin de vous permettre de vérifier que l'application a bien été déployée lors de l'achèvement de la chaîne d'outils DevOps.

Les déploiements Mendix Cloud Foundry requièrent le service de base de données PostGRES, qui ne dispose pas d'un niveau simplifié. Si vous souhaitez évaluer les kits de démarrage Mendix en utilisant un compte simplifié, vous pouvez cibler un cluster kubernetes d'essai.
{: tip}

Si vous avez sélectionné un cluster kubernetes pour déploiement, consultez le [tutoriel Mendix kubernetes](/docs/apps/tutorials?topic=creating-apps-deploy-mendix-kube) pour savoir comment configurer votre cluster pour une utilisation en production.


## Poursuite du cycle de vie de développement et de déploiement de Mendix
{: #dev-lifecycle-mendix}

Mendix est un environnement de création qui utilise peu de code. Dans le cadre du cycle de vie de développement, vous devez ouvrir votre projet dans l'application pour ordinateur de bureau Mendix Modeler.

1. A partir de votre application {{site.data.keyword.cloud_notm}}, cliquez sur **Editer dans Mendix**.
2. Dans le portail Web Mendix, cliquez sur **Edit in Desktop Modeler**.
  L'application Mendix s'ouvre dans le modélisateur pour ordinateur de bureau.
3. Editez votre application Mendix, puis sauvegardez vos modifications.
4. Utilisez le menu **Run** de l'application Mendix Desktop Modeler et sélectionnez l'option **Run**.
  Le package de déploiement est créé et téléchargé dans Mendix. Une fois le package de déploiement créé, vous pouvez déployer votre application sur {{site.data.keyword.cloud_notm}}.
5. Pour déployer votre application Mendix, revenez sur la page **Détails de l'application** dans {{site.data.keyword.cloud_notm}} et cliquez sur **Déployer**.
  Cette action démarre la chaîne d'outils DevOps de votre application, ce qui envoie le dernier déploiement depuis Mendix et le déploie sur votre environnement cible. Une fois le déploiement terminé, la version la plus récente de votre application démarre automatiquement et devient disponible.

Toutes les applications Mendix seront déployées sur {{site.data.keyword.cloud_notm}} en cliquant sur **Configurer la distribution continue** sur la page **Détails de l'application** dans {{site.data.keyword.cloud_notm}}. Vous ne devez pas appeler manuellement les chaînes d'outils Mendix via l'interface IBM DevOps. Le fait de lancer des chaînes d'outils manuellement via l'interface DevOps peut entraîner un échec du déploiement en raison du manque de métadonnées requises pour les déploiements Mendix. Selon l'état de votre application, un échec peut se produire durant le lancement de la chaîne d'outils DevOps ou une erreur peut survenir dans l'application déployée. Si vous lancez manuellement une chaîne d'outils et qu'un échec se produit, vous pouvez restaurer le déploiement de votre application en cliquant sur **Configurer la distribution continue** sur la page **Détails de l'application** dans {{site.data.keyword.cloud_notm}}. Cette action déclenche un DevOps complet pour l'application Mendix, qui inclut les métadonnées requises.
{: tip}

## Etapes suivantes 
{: #next-steps-mendix}

Pour déployer votre application sur {{site.data.keyword.containerlong_notm}}, configurez-la pour déploiement en production. Pour plus d'informations, voir le [tutoriel Mendix Kubernetes](/docs/apps/tutorials?topic=creating-apps-deploy-mendix-kube). 
