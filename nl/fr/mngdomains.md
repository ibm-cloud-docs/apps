---

copyright:
  years: 2019
lastupdated: "2019-03-15"

keywords: apps, domain, Kubernetes, Cloud Foundry, cli

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Mise à jour de votre domaine
{: #update-domain}

Les domaines fournissent la route d'URL allouée à votre organisation dans {{site.data.keyword.cloud}}. Pour les applications Cloud Foundry, vous pouvez migrer votre domaine de `mybluemix.net` à `appdomain.cloud` en utilisant la console {{site.data.keyword.cloud_notm}} ou l'interface de ligne de commande.
{:shortdesc}

## Mise à jour des domaines depuis la console {{site.data.keyword.cloud_notm}}
{: #update-domain-console}

Le domaine partagé par défaut est `mybluemix.net` mais `appdomain.cloud` est une autre option de domaine que vous pouvez utiliser.
{: tip}

Procédez comme suit pour mettre à jour le domaine pour votre organisation Cloud Foundry en utilisant la console :

1. Depuis la console [{{site.data.keyword.cloud_notm}} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}){: new_window}, cliquez sur l'icône **Menu** ![Icône Menu](../icons/icon_hamburger.svg) et sélectionnez **Liste de ressources**.
2. Sur la page **Liste de ressources**, cliquez sur **Applications Cloud Foundry**.
3. Cliquez sur l'application pour laquelle vous voulez changer le domaine. La page **Présentation** de l'application s'affiche.
4. Sélectionnez le menu **Routes**, notez le domaine actuel, `<myapp.mybluemix.net>`, par exemple et cliquez sur **Editer les routes**.
5. Sélectionnez la liste des domaines puis cliquez sur le domaine que vous voulez utiliser, comme `us-south.cf.appdomain.cloud`.
6. Confirmez vos mises à jour en cliquant sur **Sauvegarder**.
7. Confirmez que vous voulez remplacer l'ancien domaine et cliquez sur **Retirer**.
8. Pour vérifier que la nouvelle route fonctionne, cliquez sur **Visite de l'URL de l'application**.

## Mise à jour des domaines depuis l'interface de ligne de commande {{site.data.keyword.cloud_notm}}
{: #update-domain-cli}

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

2. Ajoutez la route avec le nouveau domaine à une application en entrant la commande suivante :
   ```
   ibmcloud app route-map APP_NAME DOMAIN -n HOSTNAME
   ```

## Mise à jour de votre domaine pour des applications Kubernetes
{: #update-domain-kube}

Le sous-domaine pour les noms d'hôte {{site.data.keyword.containerlong}} est `containers.appdomain.cloud`. Le domaine générique de sous-domaine Ingress fourni par IBM, `*.<cluster_name>.<region>.containers.appdomain.cloud`, est enregistré par défaut pour votre cluster. Le certificat TLS fourni par IBM est un certificat générique pouvant être utilisé pour le sous-domaine générique. Pour plus d'informations, voir la rubrique traitant des [domaines multiples dans un espace de nom](/docs/containers?topic=containers-ingress#multi-domains).
