---

copyright:

  years: 2019

lastupdated: "2019-05-22"

keywords: apps FAQs, apps frequently asked questions, applications FAQs, applications frequently asked questions

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:faq: data-hd-content-type='faq'}


# Foire aux questions
{: #apps-faq}

## Qu'est-il arrivé à mybluemix.net ?
{: #domain-change-faq}
{: faq}

Une nouvelle option de nom d'hôte `*.appdomain.cloud` est disponible sur cloud.ibm.com.

Auparavant, le domaine `mybluemix.net` était utilisé pour l'hébergement des applications dans différentes cibles de déploiement, comme {{site.data.keyword.containerlong_notm}} ou Cloud Foundry. Les applications hébergées sur `mybluemix.net` ne sont pas concernées.

Le sous-domaine des applications Cloud Foundry est `cf.appdomain.cloud`. Le sous-domaine des applications que vous déployez dans {{site.data.keyword.containerlong_notm}} est `containers.appdomain.cloud`.

Pour plus d'informations, voir [Gestion de vos domaines](/docs/apps?topic=creating-apps-update-domain).

## Où puis-je trouver la liste de mes applications ?
{: #cf-app}
{: faq}

La liste de vos ressources se trouvant dans la console [{{site.data.keyword.cloud_notm}}](https://{DomainName}){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe") fournit des informations récapitulatives sur les applications que vous avez créées. Dans la liste des ressources, la section **Applications** contient toutes les applications que vous avez créées mais *non* celles déployées dans Cloud Foundry. La section **Applications Cloud Foundry** contient toutes les applications créées et déployées dans Cloud Foundry.

## Pourquoi ne puis-je pas sélectionner d'espace Cloud Foundry lorsque je tente de déployer mon application ?
{: #cf-space}
{: faq}

Il est fort probable que vous ayez besoin de créer tout d'abord un espace Cloud Foundry. Si vous utilisez l'interface de ligne de commande Cloud Foundry, entrez `cf create-space <space_name> -o <organization_name>`. Sinon, procédez comme suit dans la console :

1. Dans la barre de menus de la console [{{site.data.keyword.cloud_notm}}](https://{DomainName}){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe"), sélectionnez **Gérer** > **Compte**.
2. Sélectionnez **Organisations Cloud Foundry**.
3. Cliquez sur le nom de l'organisation dans laquelle vous souhaitez créer un espace puis cliquez sur **Ajouter un espace**.

## Comment supprimer des applications ?
{: #delete-apps}
{: faq}

Pour supprimer une application que vous avez créée, procédez comme suit :

1. Dans la console [{{site.data.keyword.cloud_notm}}](https://{DomainName}){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe"), cliquez sur l'icône **Menu** ![Icône Menu](../icons/icon_hamburger.svg) puis sélectionnez **Liste de ressources**.
2. Cliquez sur l'icône **Actions** ![Icône Actions](../icons/action-menu-icon.svg) pour l'application que vous souhaitez supprimer puis cliquez sur **Supprimer**.

## Comment puis-je arrêter une application Cloud Foundry dans mon compte ?
{: #app-stop}
{: faq}

Si vous souhaitez arrêter une application Cloud Foundry, procédez comme suit :


1. A partir du tableau de bord, cliquez sur **Afficher les ressources** dans la section récapitulant les ressources. 
1. Dans liste des ressources, développez les sections et localisez l'instance de service que vous souhaitez arrêter. 
1. Sélectionnez l'icône **Actions** ![icône Liste d'actions](../icons/action-menu-icon.svg), puis cliquez sur **Arrêter**.

## Que sont les chaînes d'outils et comment sont-elles liées à mon application ?
{: #toolchains}
{: faq}

Une chaîne d'outils est un ensemble d'intégrations d'outils prenant en charge les tâches de développement, de déploiement et d'opérations. Vous pouvez créer une chaîne d'outils à partir de votre application. La chaîne d'outils peut prendre en charge le développement, le déploiement et la
surveillance en continu, entre autres, et est associée à votre application. Chaque application peut être associée à une chaîne d'outils. Une chaîne d'outils peut être configurée afin que les modifications apportées à la chaîne d'outils génèrent et déploient automatiquement l'application. Pour plus d'informations sur les chaînes d'outils, voir [Création de chaînes d'outils](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started).

## Comment changer de domaine pour mes applications Cloud Foundry ?
{: #cf-domains-faq}
{: faq}

Pour les applications Cloud Foundry, vous pouvez changer de domaine et utiliser `appdomain.cloud` et non plus `mybluemix.net` via la console {{site.data.keyword.cloud_notm}} ou l'interface de ligne de commande. Pour plus d'informations sur le passage au domaine `appdomain.cloud`, voir [Mise à jour de votre domaine](/docs/cloud-foundry-public?topic=cloud-foundry-public-update-domain).

Lorsque vous créez de nouvelles applications, le domaine partagé par défaut est `mybluemix.net` mais vous pouvez également utiliser le domaine `appdomain.cloud`.
