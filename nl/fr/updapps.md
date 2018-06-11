---

copyright:
  years: 2015, 2018
lastupdated: "2018-05-22"

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Création et utilisation d'un domaine personnalisé
{: #updatingapps}

Vous pouvez utiliser la ligne de commande ou {{site.data.keyword.Bluemix}} Continuous Delivery pour mettre à jour les applications dans {{site.data.keyword.Bluemix_notm}}. Dans de nombreux cas, même pour les packs de construction tels que Node.js, vous devez également fournir un paramètre -c afin de spécifier la
commande à utiliser pour démarrer votre application.
{:shortdesc}

Les domaines fournissent la route d'URL allouée à votre organisation dans {{site.data.keyword.Bluemix_notm}}. Pour utiliser un domaine personnalisé, vous devez enregistrer le domaine personnalisé sur un serveur DNS public, configurer ce domaine dans {{site.data.keyword.Bluemix_notm}}, puis mapper ce domaine au domaine de système {{site.data.keyword.Bluemix_notm}} sur le serveur DNS public. Une fois que votre domaine personnalisé est mappé au domaine de système, les demandes de votre domaine personnalisé sont acheminées vers votre application
dans {{site.data.keyword.Bluemix_notm}}.

Vous pouvez créer et utiliser un domaine personnalisé en utilisant la console ou l'interface de ligne de commande {{site.data.keyword.Bluemix_notm}}.

## Utilisation de la console {{site.data.keyword.Bluemix_notm}}

Procédez comme suit pour créer un domaine personnalisé pour votre organisation à l'aide de la console :

1. Accédez à **Gérer** > **Compte** > **Organisations Cloud Foundry**.
2. Cliquez sur le nom de l'organisation pour laquelle vous créez un domaine personnalisé.
3. Cliquez sur l'onglet **Domaines**.
4. Cliquez sur **Ajouter un domaine**, entrez le nom de votre domaine et sélectionnez la région.
5. Confirmez vos mises à jour. Cliquez sur **Ajouter**. 

Par exemple, vous pouvez utiliser `*.mycompany.com` pour associer la route `www.mybluemix.com` à votre application. Vous pouvez également utiliser `example.mycompany.com` pour associer la route `www.example.mybluemix.com` à votre application.
{: tip}

Ajoutez la route avec le domaine personnalisé à une application.

1. Cliquez sur l'icône **Menu** ![Icône Menu](../icons/icon_hamburger.svg) > **Tableau de bord**, puis sur la ligne de l'application à laquelle ajouter la route. La page **Vue d'ensemble** s'affiche.
2. Dans le menu **Routes**, sélectionnez **Editer les routes**.
3. Cliquez sur **Ajouter une route** et spécifiez la route à utiliser pour l'application.
4. Confirmez vos mises à jour en cliquant sur **Sauvegarder**.

## Utilisation de l'interface de ligne de commande {{site.data.keyword.Bluemix_notm}}

1. Créez un domaine personnalisé pour votre organisation en lançant la commande suivante :

   ```
   ibmcloud app domain-create <nom_organisation> mydomain
   ```

2. Ajoutez la route avec le domaine personnalisé à une application. Pour les applications CF, entrez la commande suivante :

   ```
   ibmcloud app route-map myapp mydomain -n host_name

   ```

   Pour les groupes de conteneurs, entrez la commande suivante :

   ```
   cf ic route map -n host_name -d mydomain mycontainergroup

   ```

Une fois le domaine personnalisé configuré dans {{site.data.keyword.Bluemix_notm}}, mappez-le au domaine de système
{{site.data.keyword.Bluemix_notm}} sur votre serveur DNS enregistré :

1. Configurez un enregistrement 'CNAME' pour le nom de domaine personnalisé sur votre serveur DNS. Les étapes de configuration de l'enregistrement
CNAME varient selon votre fournisseur DNS. Par exemple, si vous utilisez GoDaddy, suivez la procédure décrite sur la page [Domains Help ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://www.godaddy.com/help/add-a-cname-record-19236){: new_window} de GoDaddy.
2. Mappez le nom de domaine personnalisé au noeud final sécurisé pour la région {{site.data.keyword.Bluemix_notm}} dans laquelle s'exécute
votre application. Utilisez les noeuds finaux de région suivants pour fournir la route d'URL allouée à votre organisation dans
{{site.data.keyword.Bluemix_notm}} :

  * SUD DES ETATS-UNIS : `secure.us-south.bluemix.net`
  * EST DES ETATS-UNIS : `secure.us-east.bluemix.net`
  * EUROPE-ALLEMAGNE : `secure.eu-de.bluemix.net`
  * EUROPE-ROYAUME-UNI : `secure.eu-gb.bluemix.net`
  * AUSTRALIE-SYDNEY : `secure.au-syd.bluemix.net`

Depuis un navigateur ou une interface de ligne de commande, entrez l'adresse URL suivante pour accéder à l'application myapp :

```
http://host_name.mydomain

```

Pour retirer une route orpheline, exécutez la commande suivante :

```
ibmcloud app route-delete domain -n hostname -f

```
{: tip}

`domain` est le nom de votre domaine et `hostname` le nom d'hôte de la route pour votre application. Pour plus d'informations sur la commande **ibmcloud app route-delete**, entrez `ibmcloud app route-delete -h`.

