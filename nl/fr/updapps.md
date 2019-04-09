---

copyright:
  years: 2015, 2018
lastupdated: "2018-02-15"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Mise à jour d'applications
{: #updatingapps}

Vous pouvez utiliser la ligne de commande ou {{site.data.keyword.Bluemix}} Continous Delivery pour mettre à jour les applications dans {{site.data.keyword.Bluemix_notm}}. Dans de nombreux cas, même pour les packs de construction intégrés tels que Node.js, vous devez également fournir un paramètre -c afin de spécifier la
commande à utiliser pour démarrer votre application.
{:shortdesc}

## Création et utilisation d'un domaine personnalisé
{: #domain}

Pour les applications Cloud Foundry et les groupes de conteneurs, vous pouvez utiliser un domaine personnalisé dans l'adresse URL de votre application au lieu du domaine de système {{site.data.keyword.Bluemix_notm}} par défaut, à savoir mybluemix.net.

Les domaines fournissent la route d'URL allouée à votre organisation dans {{site.data.keyword.Bluemix_notm}}. Pour utiliser un domaine personnalisé, vous devez enregistrer le domaine personnalisé sur un serveur DNS public, configurer ce domaine dans {{site.data.keyword.Bluemix_notm}}, puis mapper ce domaine au domaine de système {{site.data.keyword.Bluemix_notm}} sur le serveur DNS public. Une fois que votre domaine personnalisé est mappé au domaine de système {{site.data.keyword.Bluemix_notm}}, les requêtes de votre domaine personnalisé sont acheminées à votre application
dans {{site.data.keyword.Bluemix_notm}}.

Vous pouvez créer et utiliser un domaine personnalisé dans {{site.data.keyword.Bluemix_notm}} en utilisant l'interface utilisateur {{site.data.keyword.Bluemix_notm}} ou l'interface de ligne de commande bluemix.

### Utilisation de la console {{site.data.keyword.Bluemix_notm}}

  1. Créez un domaine personnalisé pour votre organisation.

	1. Accédez à **Gérer** &gt; **Compte** &gt; **Organisations Cloud Foundry** &gt; **Afficher les détails** pour votre organisation, puis cliquez sur **Editer une organisation Cloud Foundry** &gt; **Domaines**.

	2. Sur l'onglet **Domaines**, cliquez sur **Ajouter un domaine**, entrez votre nom de domaine personnalisé, puis cliquez sur **Sauvegarder**.

	**Remarque** : Par exemple, vous pouvez utiliser `mon_entreprise.com` pour associer la route `www.mon_entreprise.com` à votre application.
Vous pouvez aussi utiliser `exemple.mon_entreprise.com` pour associer la route `www.exemple.mon_entreprise.com` à votre application.

  2. Ajoutez la route avec le domaine personnalisé à une application.

    1. Cliquez sur l'icône **Menu** ![Icône de menu](../icons/icon_hamburger.svg) &gt; **Tableau de bord**, puis sur la ligne de l'application à laquelle ajouter la route. La page **Vue d'ensemble** s'affiche.

	2. Dans le menu **Routes**, sélectionnez **Editer les routes**.

	3. Cliquez sur **Ajouter une route** et spécifiez la route à utiliser pour l'application.
	4. Cliquez sur **Sauvegarder**.

### Utilisation de l'interface de ligne de commande Bluemix 

  1. Créez un domaine personnalisé pour votre organisation en lançant la commande suivante :

    ```
    bluemix app domain-create <your org name> mydomain
    ```

    *organization_name* : Nom de votre organisation.

    *mydomain* : Nom de domaine personnalisé à utiliser.

  2. Ajoutez la route avec le domaine personnalisé à une application. Pour les applications CF, entrez la commande suivante :

    ```
    bluemix app route-map myapp mydomain -n host_name
    ```

    Pour les groupes de conteneurs, entrez la commande suivante :
     ```
     cf ic route map -n host_name -d mydomain mycontainergroup
     ```

    *myapp* : Pour les applications CF, nom de votre application.

    *mydomain* : Nom de votre domaine personnalisé, par exemple `www.mydomain.mybluemix.net`.

    *host_name* : Nom d'hôte dans le chemin à utiliser pour votre application.

    *mycontainergroup* : Pour les groupes de conteneurs, nom du groupe de conteneurs.

Une fois le domaine personnalisé configuré dans {{site.data.keyword.Bluemix_notm}}, vous devez le mapper au domaine de système
{{site.data.keyword.Bluemix_notm}} sur votre serveur DNS enregistré :

  1. Configurez un enregistrement 'CNAME' pour le nom de domaine personnalisé sur votre serveur DNS. Les étapes de configuration de l'enregistrement
CNAME varient selon votre fournisseur DNS. Par exemple, si vous utilisez GoDaddy, vous suivez la procédure de la page [Domains Help ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://www.godaddy.com/help/add-a-cname-record-19236){: new_window} de GoDaddy.
  2. Mappez le nom de domaine personnalisé au noeud final sécurisé pour la région {{site.data.keyword.Bluemix_notm}} dans laquelle s'exécute
votre application. Utilisez les noeuds finaux de région suivants pour fournir la route d'URL allouée à votre organisation dans
{{site.data.keyword.Bluemix_notm}} :

    * SUD DES ETATS-UNIS : `secure.us-south.bluemix.net`
    * EST DES ETATS-UNIS : `secure.us-east.bluemix.net`
    * EUROPE-ALLEMAGNE : `secure.eu-de.bluemix.net`
    * EUROPE-ROYAUME-UNI : `secure.eu-gb.bluemix.net`
    * AUSTRALIE-SYDNEY : `secure.au-syd.bluemix.net`

Depuis un navigateur ou l'interface de ligne de commande, entrez l'adresse URL suivante pour accéder à l'application mon_app :

```
http://host_name.mydomain
```

**Remarque :** pour supprimer une route orpheline, utilisez la commande suivante :

```
bluemix app route-delete domain -n hostname -f
```

*domain* est le nom de votre domaine et *hostname* le nom d'hôte de la route pour votre application. Pour plus d'informations sur la commande **bluemix app route-delete**, entrez `bluemix app route-delete -h`.

##Déploiements Blue-Green
{: #blue_green}

{{site.data.keyword.Bluemix_notm}} prend en charge la technique de déploiement Blue-Green pour
permettre une distribution continue et limiter les événements d'indisponibilité.

Le *déploiement Blue-Green* est une technique de déploiement à indisponibilité zéro qui compte deux environnements de
production identiques appelés Blue et Green. Leur différence tient aux artefacts que le développeur a délibérément modifiés, généralement selon la version de l'application. A tout moment, au moins l'un des environnements est actif. La technique de déploiement Blue-Green procure les avantages suivants :

* Passage rapide du logiciel de sa phase de test final vers l'environnement opérationnel de production.
* Déploiement d'une nouvelle version d'une application sans perturbation du trafic vers l'application.
* Basculement rapide. Si l'un de vos environnements connaît un problème, vous pouvez basculer rapidement vers l'autre environnement.

Si vous
avez déjà déployé une application dans {{site.data.keyword.Bluemix_notm}} et que vous souhaitez la mettre à niveau
vers une
nouvelle version, vous pouvez utiliser l'une des méthodes ci-dessous pour effectuer un déploiement Blue-Green.

###Exemple : Utilisation de la commande bluemix app rename

Dans cet exemple, le nom de l'application est Blue. Cet exemple illustre la mise à jour de la version de *Blue* à l'aide de la commande **bluemix app rename** sans perturbation du trafic vers l'application. Vous pouvez, si vous le désirez, supprimer l'ancienne version de *Blue* une fois la nouvelle version en place.

1. Envoyez l'application *Blue* à {{site.data.keyword.Bluemix_notm}}.

  ```
  bluemix app push Blue
  ```

  Résultat :L'application *Blue* s'exécute et répond à l'adresse URL `Blue.mybluemix.net`.

2. Utilisez la commande **bluemix app rename** pour renommer l'application *Blue* en *Green* :

  ```
  bluemix app rename Blue Green
  ```

  Répertoriez les applications qui se trouvent dans l'espace en cours avec la commande **bluemix app list** :

  ```
  ...
  name             requested state   instances   memory   disk   urls
  Green            started           1/1         1G       1G	 Blue.mybluemix.net
  ...
  ```

  Résultat : L'application *Green* s'exécute et répond à l'adresse URL `Blue.mybluemix.net`.

3. Apportez les modifications nécessaires et préparez la version *Blue* mise à jour. Envoyez l'application *Blue*
mise à jour à {{site.data.keyword.Bluemix_notm}} :

  ```
  bluemix app push Blue
  ```

  Répertoriez les applications qui se trouvent dans l'espace en cours avec la commande **bluemix app list** :

  ```
  ...
  name             requested state   instances   memory   disk   urls
  Green            started           1/1         1G       1G	 Blue.mybluemix.net
  Blue             started           1/1         1G       1G	 Blue.mybluemix.net
  ...
  ```

  Résultats :
    * Deux instances de l'application sont déployées, l'instance *Blue* et l'instance *Green*.
	* L'application *Green* s'exécute et répond à l'adresse URL `Blue.mybluemix.net`.

4. Facultatif : si vous voulez supprimer l'ancienne version (*Green*) de l'application, utilisez la commande **bluemix app delete**.

  ```
  bluemix app delete Green -f
  ```

  Répertoriez les routes qui se trouvent dans votre espace avec la commande **bluemix app route-map** :

  ```
  ...
  host             domain           apps
  Blue             mybluemix.net    Blue
  ...
  ```

  Résultat : L'application *Blue* répond à l'adresse URL `Blue.mybluemix.net`.

###Exemple : Utilisation de la commande bluemix app route-map

Dans cet exemple, *Blue* est l'ancienne version déployée et
*Green* la version mise à jour. Cet exemple illustre la mise à jour de la version de *Blue* à l'aide de la commande **bluemix app route-map** sans perturbation du trafic vers l'application. Vous pouvez, si vous le désirez, supprimer l'ancienne version de *Blue* une fois la nouvelle version en place.

1. Envoyez l'application *Blue* à {{site.data.keyword.Bluemix_notm}}.

  ```
  bluemix app push Blue
  ```

  Résultat :L'application *Blue* s'exécute et répond à l'adresse URL `Blue.mybluemix.net`.

2. Apportez les modifications nécessaires et préparez la version *Green*. Envoyez l'application *Green* à
{{site.data.keyword.Bluemix_notm}} :

  ```
  bluemix app push Green
  ```

  Répertoriez les applications qui se trouvent dans l'espace en cours avec la commande **bluemix app route-map** :

  ```
  ...
  host             domain           apps
  Blue             mybluemix.net    Blue
  Green            mybluemix.net    Green
  ...
  ```

  Résultats :

    * Deux instances de l'application sont déployées, l'instance *Blue* et l'instance *Green*.
	* L'application *Blue* répond à l'adresse URL `Blue.mybluemix.net`. De plus, l'application *Green*
répond à l'adresse URL `Green.mybluemix.net`.

3. Mappez l'application *Blue* à l'application *Green* pour que tout le trafic vers `Blue.mybluemix.net`
soit routé vers l'application *Blue* et vers l'application *Green*.

  ```
  bluemix app route-map Green mybluemix.net -n Blue
  ```

  Répertoriez les routes qui se trouvent dans votre espace avec la commande bluemix app route-map :

  ```
  ...
  host             domain           apps
  Blue             mybluemix.net    Blue, Green
  Green            mybluemix.net    Green
  ...
  ```

  Résultat :

    * Le routeur CF envoie désormais le trafic pour Blue.mybluemix.net. à l'application Blue et à l'application Green.
	* Le routeur CF continue à envoyer le trafic pour Green.mybluemix.net. à l'application Green.

4. Lorsque vous vérifiez que *Green* est en cours d'exécution comme prévu, supprimez la route `Blue.mybluemix.net` de
l'application *Blue* :

  ```
  bluemix app route-unmap Blue mybluemix.net -n Blue
  ```

  Répertoriez les routes qui se trouvent dans votre espace avec la commande bluemix app route-map :

  ```
  ...
  host             domain           apps
  Blue             mybluemix.net    Green
  Green            mybluemix.net    Green
  ...
  ```

  Résultat : Le routeur CF arrête d'envoyer le trafic à l'application *Blue*. L'application *Green*
répond aux deux adresses URL : `Green.mybluemix.net` et `Blue.mybluemix.net`.

5. Supprimez la route `Green.mybluemix.net` vers l'application *Green*.

  ```
  bluemix app route-unmap Green mybluemix.net -n Green
  ```

  Résultat : Le routeur CF arrête d'envoyer le trafic à l'application *Blue*. L'application *Green* répond à l'adresse URL `Blue.mybluemix.net`.

6. Facultatif : si vous voulez supprimer l'ancienne version (*Blue*) de l'application, utilisez la commande `bluemix app delete`.

  ```
  bluemix app delete Blue -f
  ```

  Répertoriez les routes qui se trouvent dans votre espace avec la commande bluemix app route-map :

  ```
  ...
  host             domain           apps
  Blue             mybluemix.net    Green
  ...
  ```

  Résultat : L'application *Green* répond à l'adresse URL `Blue.mybluemix.net`.


# Liens connexes
{: #rellinks notoc}

## Liens connexes
{: #general}

[Déploiements Blue-Green ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](http://martinfowler.com/bliki/BlueGreenDeployment.html){:new_window}

