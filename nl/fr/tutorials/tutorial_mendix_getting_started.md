---

copyright:
  years: 2018
lastupdated: "2018-11-28"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Création d'applications à l'aide de Mendix
{: #getting-started}

Mendix est un environnement et un ensemble d'outils de développement qui utilise peu de code et vous permet de distribuer plus rapidement des applications multi-dispositif, avec moins de ressources de développement, qui s'exécutent sur {{site.data.keyword.cloud}}. Si vous sélectionnez un kit de démarrage Mendix qui utilise peut de code, celui-ci vous aide à configurer votre compte sur la plateforme Mendix, à démarrer votre projet et à sélectionner votre environnement de déploiement dans Cloud Foundry ou sur votre cluster Kubernetes.
{: shortdesc}

## Sélection d'un kit de démarrage
{: #select-a-starter-kit}

1. Sur le tableau de bord [{{site.data.keyword.cloud_notm}} App Service ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/developer/appservice/dashboard){: new_window}, cliquez sur **Initiation**.
2. Sélectionnez un kit de démarrage Mendix qui utilise peu de code à partir de l'une des catégories suivantes :
  * [Mobile ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/developer/appservice/starter-kits/mendix-mobile-app)
  * [Application Web Watson ou mobile ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/developer/appservice/starter-kits/mendix-web-or-mobile-app-with-watson)
  * [Application Web ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/developer/appservice/starter-kits/mendix-web-app)
3. Cliquez sur **Créer une application**.
4. Donnez un nom à votre application.
5. Cliquez sur **Créer**.

<!-- 
####### Promote CLOUD.IBM.COM links to prod when approved.
1. From the [{{site.data.keyword.cloud_notm}} App Service dashboard ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/developer/appservice/dashboard){: new_window}, click **Get Started**.
2. Select a Mendix low-code starter kit from one of the following categories:
  * [Mobile ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/developer/appservice/starter-kits/mendix-mobile-app)
  * [Watson Web or Mobile App ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/developer/appservice/starter-kits/mendix-web-or-mobile-app-with-watson)
  * [Web App ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/developer/appservice/starter-kits/mendix-web-app)
3. Click **Create app**.
4. Name your app.
5. Click **Create**.
-->

## Autoriser IBM à créer votre projet sur Mendix et des comptes liés
{: #link-mendix-account}

Si vous n'utilisez pas encore Mendix avec {{site.data.keyword.cloud_notm}}, vous êtes dirigé vers la plateforme Mendix pour vous connecter et autoriser {{site.data.keyword.cloud_notm}} à créer un nouveau projet sur la plateforme Mendix en votre nom. Ce projet est lié à {{site.data.keyword.cloud_notm}}, ainsi, les déploiements sont automatiquement dirigés vers {{site.data.keyword.cloud_notm}}.

1. Si le message suivant s'affiche : "Pour créer une application, un compte utilisateur Mendix est requis. Voulez-vous lier votre compte maintenant ?", cliquez sur **Lier le compte**.
2. Sur la page de confirmation Mendix, sélectionnez **J'accepte les règles de confidentialité et les termes de Mendix**, puis cliquez sur **Confirmer**.
3. Lorsque vous y êtes invité, indiquez votre adresse électronique, votre mot de passe et votre pays, puis cliquez sur **Créer**.
4. Sur la page **Autoriser l'accès à votre compte Mendix**, cliquez sur **Autoriser**.

Une fois l'autorisation effectuée, votre navigateur revient sur l'application Mendix que vous êtes en train de créer. La page **Choisir un environnement de déploiement** s'affiche.

## Sélection d'une option de déploiement pour votre application Mendix
{: #select-deployment}

1. Sur la page **Choisir un environnement de déploiement**, sélectionnez Cloud Foundry ou l'un de vos clusters Kubernetes qui s'exécutent sur {{site.data.keyword.cloud_notm}}.
2. Facultatif. Si vous ne possédez pas de cluster Kubernetes, vous pouvez en créer un maintenant.
3. Sur la page **Configurer la chaîne d'outils**, sélectionnez votre région et votre groupe de ressources, puis cliquez sur **Créer**.

Une chaîne d'outils DevOps est créée. La chaîne d'outils intègre votre projet Mendix au sein de la plateforme Mendix dans votre environnement {{site.data.keyword.cloud_notm}}. Une application par défaut est déployée sur votre déploiement cible afin de vous permettre de vérifier que l'application a bien été déployée lors de l'achèvement de la chaîne d'outils DevOps.

Les déploiements Mendix Cloud Foundry requièrent le service de base de données PostGRES, qui ne dispose pas d'un niveau simplifié.   Si vous souhaitez évaluer les kits de démarrage Mendix en utilisant un compte simplifié, vous pouvez cibler un cluster kubernetes d'essai.
{: tip}

Si vous avez sélectionné un cluster kubernetes pour déploiement, consultez le [tutoriel Mendix kubernetes](/docs/apps/tutorials/tutorial_mendix_kubernetes.html) pour savoir comment configurer votre cluster pour une utilisation en production.


## Poursuite du cycle de vie de développement et de déploiement de Mendix
{: #development-lifecycle}

Mendix est un environnement de création qui utilise peu de code. Dans le cadre du cycle de vie de développement, vous devez ouvrir votre projet dans l'application pour ordinateur de bureau Mendix Modeler.

1. A partir de votre application {{site.data.keyword.cloud_notm}}, cliquez sur **Editer dans Mendix**.
2. Dans le portail Web Mendix, cliquez sur **Edit in Desktop Modeler**.
  L'application Mendix s'ouvre dans le modélisateur pour ordinateur de bureau.
3. Editez votre application Mendix, puis sauvegardez vos modifications.
4. Utilisez le menu **Run** de l'application Mendix Desktop Modeler et sélectionnez l'option **Run**.
  Le package de déploiement est créé et téléchargé dans Mendix. Une fois le package de déploiement créé, vous pouvez déployer votre application sur {{site.data.keyword.cloud_notm}}.
5. Pour déployer votre application Mendix, revenez sur la page **Détails d'application** dans {{site.data.keyword.cloud_notm}}, puis cliquez sur **Déployer l'application**.
  Cette action démarre la chaîne d'outils DevOps de votre application, ce qui envoie le dernier déploiement depuis Mendix et le déploie sur votre environnement cible. Une fois le déploiement terminé, la version la plus récente de votre application démarre automatiquement et devient disponible.

Toutes les applications Mendix seront déployées sur {{site.data.keyword.cloud_notm}} en cliquant sur **Déployer l'application** sur la page **Détails d'application** dans {{site.data.keyword.cloud_notm}}. Vous ne devez pas appeler manuellement les chaînes d'outils Mendix via l'interface IBM DevOps. Le fait de lancer des chaînes d'outils manuellement via l'interface DevOps peut entraîner un échec du déploiement en raison du manque de métadonnées requises pour les déploiements Mendix. Selon l'état de votre application, un échec peut se produire durant le lancement de la chaîne d'outils DevOps ou une erreur peut survenir dans l'application déployée. Si vous lancez manuellement une chaîne d'outils et qu'un échec se produit, vous pouvez restaurer le déploiement de votre application en cliquant sur **Déployer l'application** sur la page **Détails d'application** dans {{site.data.keyword.cloud_notm}}. Cette action déclenche un DevOps complet pour l'application Mendix, qui inclut les métadonnées requises.
{: tip}

## Etapes suivantes 
{: #next steps}

Pour déployer votre application sur {{site.data.keyword.containerlong_notm}}, configurez-la pour déploiement en production. Pour plus d'informations, voir [Tutoriel Mendix Kubernetes](/docs/apps/tutorials/tutorial_mendix_kubernetes.html). 
