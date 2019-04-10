---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-15"

keywords: apps, custom domain, Kubernetes

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Ajout et utilisation d'un domaine personnalisé
{: #updatingapps}

Les domaines fournissent la route d'URL allouée à votre organisation dans {{site.data.keyword.cloud}}. Ils dirigent  les demandes pour vos applications vers une URL dont vous êtes propriétaire. Il peut s'agir d'un domaine partagé, d'un sous-domaine partagé ou d'un domaine et d'un hôte partagés. A moins qu'un domaine personnalisé ne soit spécifié, {{site.data.keyword.cloud_notm}} utilise un domaine partagé par défaut dans la route vers votre application. Vous pouvez créer et utiliser un domaine personnalisé en utilisant la console ou l'interface de ligne de commande {{site.data.keyword.cloud_notm}}.
{:shortdesc}

Le domaine partagé par défaut est `mybluemix.net` mais `appdomain.cloud` est une autre option de domaine que vous pouvez utiliser. Pour plus d'informations sur la migration vers `appdomain.cloud`, voir [Mise à jour de votre domaine](/docs/apps/tutorials?topic=creating-apps-update-domain).
{: tip}

Pour utiliser un domaine personnalisé, vous devez enregistrer ce dernier sur un serveur DNS public puis le configurer dans {{site.data.keyword.cloud_notm}}. Ensuite, vous devez mapper le domaine personnalisé au domaine de système {{site.data.keyword.cloud_notm}} sur le serveur DNS public. Une fois que votre domaine personnalisé est mappé au domaine de système, les demandes de votre domaine personnalisé sont acheminées vers votre application
dans {{site.data.keyword.cloud_notm}}.

## Ajout d'un domaine personnalisé depuis la console {{site.data.keyword.cloud_notm}}
{: #custom-domain-console}

Procédez comme suit pour ajouter un domaine personnalisé pour votre organisation en utilisant la console :

1. Accédez à **Gérer > Compte** puis sélectionnez **Organisations Cloud Foundry**.
2. Cliquez sur le nom de l'organisation pour laquelle vous créez un domaine personnalisé.
3. Cliquez sur l'onglet **Domaines** pour afficher une liste des domaines disponibles.
4. Cliquez sur **Ajouter un domaine**, entrez le nom de votre domaine et sélectionnez la région.
5. Confirmez vos mises à jour et cliquez sur **Ajouter**.

## Ajout d'une route avec un domaine personnalisé vers une application

1. Depuis la console [{{site.data.keyword.cloud_notm}}](https://{DomainName}){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe"), cliquez sur l'icône **Menu** ![Icône Menu](../../icons/icon_hamburger.svg) et sélectionnez **Liste de ressources**.
2. Sur la page **Liste de ressources**, cliquez sur **Applications Cloud Foundry**.
3. Cliquez sur l'application à laquelle vous voulez ajouter la route. La page **Présentation** de l'application s'affiche.
4. Sélectionnez le menu **Routes** et sélectionnez **Editer les routes**.
5. Cliquez sur **Ajouter une route** et spécifiez la route à utiliser pour l'application.
6. Confirmez vos mises à jour en cliquant sur **Sauvegarder**.

Ainsi, vous pouvez utiliser `*.mycompany.com` pour associer la route `www.mybluemix.net` à votre application, ou vous servir d'`example.mycompany.com` pour associer la route `www.example.bluemix.net` à votre application.
{: tip}

## Ajout d'un domaine personnalisé depuis l'interface de ligne de commande {{site.data.keyword.cloud_notm}}
{: #custom-domain-cli}

1. Pour les applications Cloud Foundry, connectez-vous à votre noeud final d'API ciblé en entrant la commande suivante :
   ```
   ibmcloud target --cf-api <CF_ENDPOINT>
   ```
   
   **Noeuds finaux d'API Cloud Foundry :**
   * SUD DES ETATS-UNIS - `api.us-south.cf.cloud.ibm.com`
   * EST DES ETATS-UNIS - `api.us-east.cf.cloud.ibm.com`
   * EUROPE-ALLEMAGNE - `api.eu-de.cf.cloud.ibm.com`
   * EUROPE-ROYAUME-UNI - `api.eu-gb.cf.cloud.ibm.com`
   * AUSTRALIE-SYDNEY - `api.au-syd.cf.cloud.ibm.com`
   
2. Créez un domaine personnalisé pour votre organisation en lançant la commande suivante :
   ```
   ibmcloud app domain-create <MY_ORGNAME> <MY_DOMAIN>
   ```

3. Ajoutez la route avec le domaine personnalisé à une application.

   Pour les applications Cloud Foundry, entrez la commande suivante :
   ```
   ibmcloud app route-map <MY_APPNAME> <MY_DOMAIN> -n <MY_HOSTNAME>
   ```
   
## Mappage du domaine personnalisé au domaine de système
{: #mapcustomdomain}

Une fois le domaine personnalisé configuré dans {{site.data.keyword.cloud_notm}}, mappez-le au domaine de système
{{site.data.keyword.cloud_notm}} sur votre serveur DNS enregistré :

1. Configurez un enregistrement 'CNAME' pour le nom de domaine personnalisé sur votre serveur DNS. Les étapes de configuration de l'enregistrement
CNAME varient selon votre fournisseur DNS. Par exemple, si vous utilisez GoDaddy, suivez la procédure décrite sur la page [Domains Help ](https://www.godaddy.com/help/add-a-cname-record-19236){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe") de GoDaddy.
2. Mappez le nom de domaine personnalisé au noeud final sécurisé pour la région {{site.data.keyword.cloud_notm}} dans laquelle s'exécute
votre application. Utilisez les noeuds finaux de région suivants pour fournir la route d'URL allouée à votre organisation dans {{site.data.keyword.cloud_notm}}. Ainsi, pointez votre nom CNAME sur `<custom-domain>.us-east.cf.cloud.ibm.com.`

  **Noeuds finaux Cloud Foundry :**
  * SUD DES ETATS-UNIS - `custom-domain.us-south.cf.cloud.ibm.com`
  * EST DES ETATS-UNIS - `custom-domain.us-east.cf.cloud.ibm.com`
  * EUROPE (ALLEMAGNE) - `custom-domain.eu-de.cf.cloud.ibm.com`
  * EUROPE (ROYAUME-UNI) - `custom-domain.eu-gb.cf.cloud.ibm.com`
  * AUSTRALIE (SYDNEY) - `custom-domain.au-syd.cf.cloud.ibm.com`

## Accès à votre application
{: #access-app}

Dans un navigateur, entrez l'URL suivante pour accéder à votre application, où `hostname` est votre nom d'hôte et `mydomain`, votre nom de domaine :
```
http://hostname.mydomain
```

## Retrait d'une route orpheline
{: #remove-orphaned-route}

Pour retirer une route orpheline, exécutez la commande suivante :
```
ibmcloud app route-delete <MY_DOMAIN> -n <MY_HOSTNAME> -f
```
{: tip}

Dans cet exemple, `domain` correspond au nom de votre domaine et `hostname` au nom d'hôte de la route de votre application. Pour plus d'informations sur la commande `ibmcloud app route-delete`, entrez la commande `ibmcloud app route-delete -h`.

## Utilisation d'un domaine personnalisé pour des applications Kubernetes
{: #kube-custom-domain}

Le sous-domaine pour les noms d'hôte IBM Cloud Kubernetes Service est `containers.appdomain.cloud`. Le domaine générique de sous-domaine Ingress fourni par IBM, `*.<cluster_name>.<region>.containers.mybluemix.net`, est enregistré par défaut pour votre cluster. Le certificat TLS fourni par IBM est un certificat générique pouvant être utilisé pour le sous-domaine générique. Si vous voulez utiliser un domaine personnalisé, vous devez enregistrer le domaine personnalisé en tant que domaine générique, `*.custom_domain.net`, par exemple. Pour utiliser TLS, vous devez obtenir un certificat générique. Pour plus d'informations, voir la rubrique traitant des [domaines multiples dans un espace de nom](/docs/containers?topic=containers-ingress#multi-domains).

Consultez [ce tutoriel](/docs/tutorials?topic=solution-tutorials-scalable-webapp-kubernetes) qui vous montre comment mettre au point une application Web, en l'exécutant localement dans un conteneur puis en la déployant dans un cluster Kubernetes qui a été créé avec IBM Kubernetes Service. Vous apprendrez également comment lier un domaine personnalisé, surveiller la santé de votre environnement et dimensionner l'application.
