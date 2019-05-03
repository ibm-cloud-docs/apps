---

copyright:
  years: 2019
lastupdated: "2019-04-02"

keywords: apps, custom, domain, kubernetes, cloud foundry, add, subdomain, custom domain, dns, domainname, domain name, endpoint, update, migrate

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Gestion de vos domaines
{: #update-domain}

Les domaines fournissent la route d'URL allouée à votre organisation dans {{site.data.keyword.cloud}}. Ils dirigent  les demandes pour vos applications vers une URL dont vous êtes propriétaire. Il peut s'agir d'un domaine partagé, d'un sous-domaine partagé ou d'un domaine et d'un hôte partagés. A moins qu'un domaine personnalisé ne soit spécifié, {{site.data.keyword.cloud_notm}} utilise un domaine partagé par défaut dans la route vers votre application. Le processus de gestion de vos domaines dépend de votre cible de déploiement ({{site.data.keyword.containershort}}, Cloud Foundry, etc.).
{:shortdesc}

Pour utiliser un domaine personnalisé, vous devez enregistrer ce dernier sur un serveur DNS public puis le configurer dans {{site.data.keyword.cloud_notm}}. Ensuite, vous devez mapper le domaine personnalisé au domaine de système {{site.data.keyword.cloud_notm}} sur le serveur DNS public. Une fois que votre domaine personnalisé est mappé au domaine de système, les demandes de votre domaine personnalisé sont acheminées vers votre application
dans {{site.data.keyword.cloud_notm}}.

## Changement de domaine pour des applications Kubernetes
{: #update-domain-kube}

Le sous-domaine pour les noms d'hôte {{site.data.keyword.containershort_notm}} est `containers.appdomain.cloud`. Le domaine générique de sous-domaine Ingress fourni par IBM, `*.<cluster_name>.<region>.containers.appdomain.cloud`, est enregistré par défaut pour votre cluster. Le certificat TLS fourni par IBM est un certificat générique pouvant être utilisé pour le sous-domaine générique. Pour plus d'informations, voir la rubrique traitant des [domaines multiples dans un espace de nom](/docs/containers?topic=containers-ingress#multi-domains).

## Utilisation d'un domaine personnalisé pour des applications Kubernetes
{: #custom-domain-kube}

Si vous souhaitez utiliser un domaine personnalisé, vous devez en enregistrer un en tant que domaine générique (`*.custom_domain.net`, par exemple). Pour utiliser TLS, vous devez obtenir un certificat générique. Pour plus d'informations, voir la rubrique traitant des [domaines multiples dans un espace de nom](/docs/containers?topic=containers-ingress#multi-domains).

Consultez [ce tutoriel](/docs/tutorials?topic=solution-tutorials-scalable-webapp-kubernetes) qui vous montre comment mettre au point une application Web, en l'exécutant localement dans un conteneur puis en la déployant dans un cluster Kubernetes qui a été créé avec IBM Kubernetes Service. De plus, le tutoriel présente comment lier un domaine personnalisé, surveiller la santé de votre environnement et dimensionner l'application.

## Changement de domaine pour des applications Cloud Foundry 
{: #update-domain-cf}

Pour les applications Cloud Foundry, vous pouvez changer de domaine et utiliser `appdomain.cloud` et non plus `mybluemix.net` via la console {{site.data.keyword.cloud_notm}} ou l'interface de ligne de commande. Pour plus d'informations sur le passage au domaine `appdomain.cloud`, voir [Mise à jour de votre domaine](/docs/cloud-foundry-public?topic=cloud-foundry-public-update-domain).

Le domaine partagé par défaut est `mybluemix.net` mais `appdomain.cloud` est une autre option de domaine que vous pouvez utiliser.
{: tip}

## Utilisation d'un domaine personnalisé pour des applications Cloud Foundry
{: #custom-domain-cf}

Pour les applications Cloud Foundry, vous pouvez créer et utiliser un domaine personnalisé dans la console {{site.data.keyword.cloud_notm}} ou l'interface de ligne de commande. Pour plus d'informations, voir [Ajout et utilisation d'un domaine personnalisé](/docs/cloud-foundry-public?topic=cloud-foundry-public-custom-domains).
