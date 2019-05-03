---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-15"

keywords: apps, credentials, Cloud Foundry

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Ajout de données d'identification à votre environnement Cloud Foundry
{: #add-credentials-cf}

Découvrez comment ajouter des données d'identification de service à votre environnement de déploiement Cloud Foundry. Ces instructions s'appliquent à [Cloud Foundry Public](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf) et à [Cloud Foundry Enterprise Environment](/docs/cloud-foundry-public?topic=cloud-foundry-public-cfee).
{: shortdesc}

## Votre code + Cloud Foundry
{: #credentials-byoc-cf}

Dans l'espace Cloud Foundry où se trouve votre application, vous pouvez définir quel élément Cloud Foundry appelle un service fourni par un utilisateur. Un service fourni par l'utilisateur est un élément JSON sous forme de chaîne stocké comme s'il s'agissait d'un service reliable dans l'espace Cloud Foundry. Une fois que vous vous connectez à l'espace et à l'organisation Cloud Foundry, procédez comme suit pour créer et lier un service.

1. Créez un service fourni par l'utilisateur en exécutant la commande suivante :
  ```console
  cf cups customcreds -p '{"username":"Leeroy","password":"Jenkins"}'
  ```
  {: codeblock}

2. Configurez votre application Cloud Foundry afin de l'associer au service fourni par l'utilisateur en ajoutant la section services :
  ```yaml
  ---
  applications:
  - instances: 1
    timeout: 180
    name: Blarg3
    buildpack: sdk-for-nodejs
    command: npm start
    memory: 256MB
    domain: mybluemix.net
    host: blarg3
    services:
      - customcreds
  ```

3. Codez votre application afin de lire l'environnement pour une variable d'environnement `VCAP_SERVICES`, analysez-la dans JSON et recherchez les données d'identification dont vous avez besoin (pseudocode de type node.js) :
  ```
  // get the 'password' from "customcreds" user-provided service
  vcapServices = getEnvironment('VCAP_SERVICES');
  vcapServicesAsJSON = JSON.parse(vcapServices);
  upsArray = vcapServicesAsJSON['user-provided'];
  if (upsArray) {
      for (var i = 0, len = upsArray.length; i < len; i++) {
          if (upsArray[i].name === 'customcreds') {
              return upsArray[i].credentials.password
          }
      }
  }
  ```
{: codeblock}


## Application de kit de démarrage + Cloud Foundry
{: #credentials-starterkit-cf}

### Préparation de l'espace Cloud Foundry

Utilisez la fonction **Configurer la distribution continue** pour déployer votre application dans votre espace Cloud Foundry.

Si l'instance de service reposant sur Cloud Foundry se trouve dans le même espace Cloud Foundry que l'application Cloud Foundry déployée, voir cette [section](/docs/apps?topic=creating-apps-add-credentials-cf).

Si l'instance de service reposant sur Cloud Foundry se trouve dans un autre espace que l'espace cible pour l'application Cloud Foundry, voir cette [section](/docs/apps?topic=creating-apps-add-credentials-cf#cf_resource_different).

Si le service associé à votre application repose sur le contrôleur de ressources, voir [Contrôleur de ressources](/docs/apps?topic=creating-apps-add-credentials-cf#cf_resource_controller).

#### Le service reposant sur Cloud Foundry se trouve dans le même espace que l'application déployée
{: #cf_resource_same}

Si le service qui est associé à votre application repose sur Cloud Foundry, le service est "reliable" dans Cloud Foundry. Vous pouvez voir le service dans votre espace Cloud Foundry en connectant votre ligne de commande `cf` à la région, l'organisation et l'espace corrects. Vous pouvez indiquer si le service repose sur Cloud Foundry lors de la création du service, s'il vous est demandé dans quelle organisation et dans quel espace Cloud Foundry créer le service.

Vous pouvez afficher les applications liées en exécutant la commande suivante :
```console
cf services
```
{: codeblock}

Exemple de sortie :
```
Getting services in org test_user@us.ibm.com / space dev as test_user@us.ibm.com...

name                                   service             plan              bound apps   last operation
blarg3-alertnotificati-1538417831070   alertnotification   authorizedusers                create succeeded
```
{: screen}

#### Le service reposant sur Cloud Foundry se trouve dans un autre espace que l'application déployée
{: #cf_resource_different}

Cloud Foundry ne prend pas en charge la "liaison" d'une application Cloud Foundry à un service Cloud Foundry lorsque l'application et le service ne se trouvent pas dans le même espace Cloud Foundry. L'espace Cloud Foundry doit être préparé avec des services "fournis par l'utilisateur" et la section suivante est applicable.

#### Le service du contrôleur de ressources est associé à votre application
{: #cf_resource_controller}

Si le service que vous avez associé à votre application repose sur le contrôleur de ressources, le service n'est _pas_ "reliable" dans Cloud Foundry. Vous pouvez indiquer qu'il repose sur le contrôleur de ressources au moment de la création du service s'il vous est demandé dans quel groupe de ressources créer le service. L'espace Cloud Foundry doit être préparé avec des données d'identification de service afin que l'application puisse les référencer dans le code. La préparation est effectuée pour vous automatiquement et vous pouvez observer les résultats de la préparation de l'espace en connectant la ligne de commande `cf` à votre espace en exécutant :
```console
cf services
```
{: codeblock}

Exemple de sortie :
```
Getting services in org test_user@us.ibm.com / space dev as test_user@us.ibm.com...

name                                   service             plan              bound apps   last operation
blarg-cloudant-1538408663553           user-provided
```
{: screen}

Cloud Foundry ne permet pas de voir la valeur des données d'identification de service, codées ou non, sur la ligne de commande `cf service` ou `cf services`. Fonctionnellement, un service fourni par l'utilisateur est un élément JSON sous forme de chaîne défini comme "instance de service" nommée dans votre espace Cloud Foundry. Pour voir les valeurs, vous devez tout d'abord lier une application au service Cloud Foundry en indiquant le nom de l'instance de service dans le fichier `manifest.yml` de l'application sous l'en-tête `services`. Exécutez ensuite l'application dans l'espace Cloud Foundry et obtenez l'environnement de cette application en exécutant `cf env $APP_NAME`.

Le code généré à partir d'un kit de démarrage est automatiquement chargé avec les liaisons correctes afin d'extraire et d'utiliser les valeurs de l'environnement défini pour ce code dans l'espace Cloud Foundry où l'application s'exécute.

### Le kit de démarrage a généré le code
{: #starterkit-generated-code-cf}

Avant de continuer, voir [Application de kit de démarrage + Kubernetes](/docs/apps?topic=creating-apps-add-credentials-kube#credentials-starterkit-kube-gencode). Appliquez ensuite la modification suivante :

* Bien que le code fournisse le fichier `deployment.yml`, il ne s'applique pas aux applications déployées dans Cloud Foundry. En revanche, le fichier `manifest.yml` _est_ applicable et son contenu s'affiche afin d'être _lié_ aux deux services créés dans l'espace Cloud Foundry :
  ```yaml
  ---
  applications:
  - instances: 1
    timeout: 180
    name: Blarg3
    buildpack: sdk-for-nodejs
    command: npm start
    memory: 256MB
    domain: mybluemix.net
    host: blarg3
    services:
      - blarg3-alertnotificati-1538417831070
      - blarg-cloudant-1538408663553
  ```
  {: codeblock}

Le reste de la documentation de la sous-section précédente s'applique à nouveau. La bibliothèque `IBMCloudEnv` abstrait l'extraction des valeurs de l'environnement dans lequel l'application s'exécute.

La bibliothèque simplifie les choses en extrayant des valeurs d'environnement de Cloud Foundry. Dans Cloud Foundry, une application en cours d'exécution est fournie avec une variable d'environnement nommée `VCAP_SERVICES` dont la valeur est un élément JSON sous forme de chaîne qui inclut les valeurs des données d'identification du service lié, que le service soit une instance de service _dans_ l'espace Cloud Foundry ou une valeur de service définie par l'utilisateur. Les clés de niveau supérieur dans l'élément JSON analysé de la variable d'environnement `VCAP_SERVICES` sont composées du `libellé` Cloud Foundry associé aux services reposant sur Cloud Foundry et de la clé `fournie par l'utilisateur` dont la valeur inclut un tableau des données d'identification de tous les services "fournis par l'utilisateur".
