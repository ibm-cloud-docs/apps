---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-22"

keywords: apps, credentials, kubernetes, kube, add, custom, deployment.yml, cluster, deployment, environment, kubectl, secret

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}

# Ajout de données d'identification de service à votre environnement Kubernetes
{: #add-credentials-kube}

Découvrez comment ajouter des données d'identification de service à votre environnement de déploiement Kubernetes.
{: shortdesc}

Vous devez ajouter manuellement des données d'identification de service à votre environnement de déploiement dans les situations suivantes :
 * Lorsque vous utilisez votre propre code.
 * Lorsque vous utilisez un modèle de kit de démarrage vide.
 * Lorsque vous ajoutez un service à une application reposant sur un kit de démarrage _après_ son déploiement.

## Votre code + Kubernetes
{: #credentials-byoc-kube}

<!-- (Refer to the ["Code it Right"](https://github.ibm.com/arf/planning-codegen/wiki/TEMP:-BYOC-UX-Docs#code-it-right) and ["Prepare the Environment"](https://github.ibm.com/arf/planning-codegen/wiki/TEMP:-BYOC-UX-Docs#prepare-the-environment) sections.  But translate a bit so we're only mentioning editing a `deployment.yml` file, not the "deployment.yml section of the script in the Deploy pipeline stage configuration".) -->

### Codage approprié

Par principe de précaution, vous pouvez coder votre application afin de confirmer que son environnement est terminé dans le point d'entrée principal de votre application. Vous ne souhaitez pas promouvoir une application dans un cluster dont l'environnement n'est pas terminé, ce qui provoquerait une interruption de votre produit. Le démarrage de l'application peut ne pas aboutir et votre configuration Kubernetes peut empêcher automatiquement de telles interruptions.

Supposons que vous disposiez des deux variables d'environnement suivantes :
* `SECRET`
* `NOT_SECRET`

Pour une base de données, vos variables peuvent être `APIKEY` et `DB_URL`, la première étant sensible contrairement à la seconde.

Dans Java, vous pouvez utiliser un code similaire à l'exemple suivant dans le point d'entrée principal de l'application :
```java
if (System.getenv("SECRET") == null) {
    throw new RuntimeException("Environment variable 'SECRET' is not set!");
}
// and many more checks...
```
{: codeblock}

Dans Node, vous pouvez utiliser un code similaire à l'exemple suivant :
```js
if (!process.env.SECRET) {
    console.error('ENVIRONMENT variable "SECRET" is not set!');
    process.exit(1);
}
// and many more checks...
```
{: codeblock}

### Préparation de l'environnement

Dans le fichier `deployment.yml` de Kubernetes, il est possible de définir les variables d'environnement ou une _référence à un secret dans le cluster_.

#### Définition du déploiement afin d'obtenir des données d'identification provenant de l'environnement

Dans la section incluant `kind: Deployment`, ajoutez le code exemple suivant à un niveau de mise en retrait après `spec.template.spec.containers` :
```yaml
env:
  - name: SECRET
    valueFrom:
      secretKeyRef:
          name: name-secret
          key: KEY_SECRET
  - name: NOT_SECRET
    value: "I'm not a secret"
```
{: codeblock}

* Cliquez sur **Enregistrer**.

Configurez le cluster de telle sorte que l'élément _secretKeyRef_ ayant le nom `name-secret` et la clé `KEY_SECRET` soit résolu en une valeur.

#### Installation des outils prérequis

Utilisez un terminal sur votre poste de travail pour installer les outils suivants :

1. Installez l'interface de ligne de commande [ {{site.data.keyword.dev_cli_long}}](/docs/cli?topic=cloud-cli-ibmcloud-cli).
2. Connectez-vous en utilisant la commande `ibmcloud login`.
3. Connectez-vous à votre cluster en exécutant `ibmcloud cs cluster-config {your_cluster_name}`.
4. Copiez et collez la commande `export` pour l'exécuter à partir d'un terminal.

#### Définition du secret dans le cluster

{{site.data.keyword.dev_cli_notm}} inclut `kubectl`, que vous pouvez exécuter car vous êtes connecté à votre cluster Kubernetes.

Pour définir le secret pouvant être résolu, utilisez les commandes `kubectl` suivantes :
```console
echo -n 'This is the secret.  Shhhhh!' > ./KEY_SECRET
```
{: codeblock}

```console
kubectl create secret generic name-secret --from-file=./KEY_SECRET
```
{: codeblock}

Maintenant que le cluster Kubernetes est préparé avec un secret pouvant être résolu, vous pouvez mettre à jour votre application pour utiliser les variables d'environnement définies dans le fichier `deployment.yml`.

## Application de kit de démarrage et Kubernetes
{: #credentials-starterkit-kube}

1. Accédez à la page **Détails de l'application** de votre application.

2. Pour créer une instance de Cloud Object Storage, sélectionnez **Ajouter un service** > **Stockage** > **Cloud Object Storage** > **Lite plan (Free)** > **Créer**.

3. Cliquez sur **Télécharger le code** pour regénérer votre application avec les fragments de code injectés.

4. Pour accéder aux données d'identification localement, copiez et remplacez les fichiers suivants à partir du fichier `.zip` nouvellement généré dans votre clone Git local pour accéder aux données d'identification. Vous devez toujours créer un secret Kubernetes dans votre cluster afin d'héberger les données d'identification.

   - `chart/{appName}/bindings.yaml` - Génère une variable d'environnement dans votre cluster Kubernetes qui désigne votre secret.
   - `src/main/resources/localdev-config.json` - Accédez aux données d'identification tout en exécutant votre application localement.
   - `src/main/resources/mappings.json` - Mappage fournissant l'accès à la méthode [`env.getProperty()`](/docs/java-spring?topic=java-spring-configuration#accessing-credentials) pour accéder à vos variables d'environnement à partir du code.
   - `manifest.yml` - Ce fichier lie votre service à votre application Cloud Foundry.

  Si vous choisissez ultérieurement d'effectuer un déploiement dans une application Cloud Foundry avec une ressource de contrôleur de ressources (se trouvant dans un groupe de ressources et non dans une organisation ou un espace), vous devez alors copier un fichier supplémentaire.
  {: note}

5. [Affichez votre cluster Kubernetes](https://{DomainName}/kubernetes/clusters){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe") avec la région correspondante (US-South si cette région est disponible gratuitement).

6. Cliquez dans votre cluster et sélectionnez **Tableau de bord Kubernetes** dans la partie supérieure droite pour afficher votre tableau de bord de cluster.

7. Faites défiler l'écran jusqu'à ce que vous voyez une section nommée **Secrets**. Vous pouvez voir un secret pour votre instance de service {{site.data.keyword.cloudant_short_notm}} qui utilise la convention `binding-{appName}-{serviceName}-{timestamp}`. Dans le fichier `chart/{appName}/bindings.yaml`, vous pouvez trouver le secret {{site.data.keyword.cloudant_short_notm}} correspondant.

8. Vous pouvez désormais créer un élément correspondant pour votre instance Cloud Object Storage avec le nom secret déjà généré dans le fichier `chart/{appName}/bindings.yaml`, qui est similaire à `binding-create-app-ktibr-cloudobjectstor-1538170732311`.

9. Accédez à la page **Détails de l'application** dans le tableau de bord et copiez les données d'identification pour l'instance Cloud Object Storage. Voir l'exemple de sortie de données d'identification suivant :
  ```yaml
  {
    "apikey": "hVi9lXHeMwvDCv7k8mOcl8h0JgqBujv8h9qHGuNl9bNg",
    "endpoints": "https://control.cloud-object-storage.cloud.ibm.com/v2/endpoints",
    "resource_instance_id": "crn:v1:staging:public:cloud-object-storage:global:a/144a947078143141bf66d9e93a2c257e:36467673-5cf2-4299-81ee-fc22ec04743a::"
  }    
  ```
  {: codeblock}

10. Assurez-vous que votre cluster est configuré en utilisant `ibmcloud cs cluster-config {your_cluster_name}` et en exportant la commande dans les instructions qui suivent.

11. Utilisez la commande `echo` pour placer les données d'identification dans un fichier `binding`.
  ```console
  echo -n '{"name":"create-app-ktibr-cloudobjectstor-1538170732311","credentials":{"apikey":"hVi9lXHeMwvDCv7k8mOcl8h0JgqBujv8h9qHGuNl9bNg","endpoints":"https://control.cloud-object-storage.cloud.ibm.com/v2/endpoints","resource_instance_id":"crn:v1:staging:public:cloud-object-storage:global:a/144a947078143141bf66d9e93a2c257e:36467673-5cf2-4299-81ee-fc22ec04743a::"}}' > ./binding

  ```
  {: codeblock}

12. Créez le secret avec `kubectl create secret generic binding-create-app-ktibr-cloudobjectstor-15381707323113 --from-file=./binding`. Si vous retournez dans votre tableau de bord de cluster Kubernetes, vous pouvez voir le secret que vous avez créé.

  Si vous effectuez le déploiement dans une application Cloud Foundry, vous devez créer un service fourni par l'utilisateur si vous utilisez une instance de contrôleur de ressources (si la ressource se trouve dans un groupe de ressources et non dans une organisation ou un espace). 
  {: note}
  
  ```console
  ibmcloud cf create-user-provided-service create-app-ktibr-cloudobjectstor-1538170732311 -p `{"name":"create-app-ktibr-cloudobjectstor-1538170732311","credentials":{"apikey":"hVi9lXHeMwvDCv7k8mOcl8h0JgqBujv8h9qHGuNl9bNg","endpoints":"https://control.cloud-object-storage.cloud.ibm.com/v2/endpoints","resource_instance_id":"ccrn:v1:staging:public:cloud-object-storage:global::a/144a947078143141bf66d9e93a2c257e:36467673-5cf2-4299-81ee-fc22ec04743a::"}}`
  ```
  {: codeblock}

  Le nom de votre service fourni par l'utilisateur est disponible dans le fichier `manifest.yml` avec le nom d'instance correspondant.

13. Vous pouvez désormais accéder à votre secret via les variables d'environnement de la méthode `env.getProperty` lorsque votre application s'exécute dans votre cluster Kubernetes.

### Préparation du cluster Kubernetes

Utilisez la fonction **Configurer la distribution continue** pour déployer votre application dans votre espace IBM Kubernetes. La fonction prépare votre cluster Kubernetes avec des secrets pour les données d'identification des ressources associées à votre application. Vous pouvez observer les résultats de la préparation du cluster en procédant comme suit :

1. Pour afficher les résultats, exécutez la commande suivante :

  ```
  kubectl get secrets
  ```
  {: codeblock}

  Vous pouvez afficher [plus d'informations sur les secrets](https://kubernetes.io/docs/concepts/configuration/secret/).
  {: tip}

2. Notez que le nom du secret est le nom de la ressource.
3. Affichez les informations prolixes sur le secret en utilisant `kubectl get secret binding-blarg-cloudant-1538408663553 -o=yaml`:

  ```
  apiVersion: v1
  data:
    binding: eyJhcGlrZXkiOiI4RFprT3VMVnduVkExWW1HODFnazNQMjZOeThlNWFWbjVhaFpZLVVEOHQ1NCIsImhvc3QiOiI1OWFhN2IxYS01YWFiLTRmMmQtOWE3My04YzNiMjk0MDhmOTYtYmx1ZW1peC5jbG91ZGFudC5jb20iLCJpYW1fYXBpa2V5X2Rlc2NyaXB0aW9uIjoiQXV0byBnZW5lcmF0ZWQgYXBpa2V5IGR1cmluZyByZXNvdXJjZS1rZXkgb3BlcmF0aW9uIGZvciBJbnN0YW5jZSAtIGNybjp2MTpibHVlbWl4OnB1YmxpYzpjbG91ZGFudG5vc3FsZGI6dXMtc291dGg6YS80ODBmZDFlYzE0YWM1NDBjNWJjMzdkYTc5OWE2MzQzNzpiZmEzNDJkZC00YjZmLTRkZmUtYTM1YS05MTA4ZmIwZWM1NzE6OiIsImlhbV9hcGlrZXlfbmFtZSI6ImF1dG8tZ2VuZXJhdGVkLWFwaWtleS01MzI3ZWMxZC0wOWE1LTQyMzctOTczNS03ZTAxZmU3NDFiYzciLCJpYW1fcm9sZV9jcm4iOiJjcm46djE6Ymx1ZW1peDpwdWJsaWM6aWFtOjo6OnNlcnZpY2VSb2xlOldyaXRlciIsImlhbV9zZXJ2aWNlaWRfY3JuIjoiY3JuOnYxOmJsdWVtaXg6cHVibGljOmlhbS1pZGVudGl0eTo6YS80ODBmZDFlYzE0YWM1NDBjNWJjMzdkYTc5OWE2MzQzNzo6c2VydmljZWlkOlNlcnZpY2VJZC1mNWRhMjMwYy1kNDE0LTQ4NTQtYjE1Yi00MmJmZmRhYWVmNWIiLCJwYXNzd29yZCI6ImY4MjU2ZDJhODYyMjI5NzViZDI3Mjc1MjEzMTY4YTQyNzBhNDZmMmEyOGQ5NDkyMjRhYzFjOTc3NjMwMWNlZTYiLCJwb3J0Ijo0NDMsInVybCI6Imh0dHBzOi8vNTlhYTdiMWEtNWFhYi00ZjJkLTlhNzMtOGMzYjI5NDA4Zjk2LWJsdWVtaXg6ZjgyNTZkMmE4NjIyMjk3NWJkMjcyNzUyMTMxNjhhNDI3MGE0NmYyYTI4ZDk0OTIyNGFjMWM5Nzc2MzAxY2VlNkA1OWFhN2IxYS01YWFiLTRmMmQtOWE3My04YzNiMjk0MDhmOTYtYmx1ZW1peC5jbG91ZGFudC5jb20iLCJ1c2VybmFtZSI6IjU5YWE3YjFhLTVhYWItNGYyZC05YTczLThjM2IyOTQwOGY5Ni1ibHVlbWl4In0=
  kind: Secret
  metadata:
    annotations:
      service-instance-id: 'crn:v1:bluemix:public:cloudantnosqldb:us-south:a/480fd1ec14ac540c5bc37da799a63437:bfa342dd-4b6f-4dfe-a35a-9108fb0ec571::'
      service-key-id: 5327ec1d-09a5-4237-9735-7e01fe741bc7
    creationTimestamp: 2018-10-01T15:45:02Z
    name: binding-blarg-cloudant-1538408663553
    namespace: default
    resourceVersion: "155591"
    selfLink: /api/v1/namespaces/default/secrets/binding-blarg-cloudant-1538408663553
    uid: f5e7885c-c590-11e8-ad83-8e37f3f3216f
  type: Opaque
  ```
  {: screen}

  La `liaison` est la valeur codée en Base64 du secret. Son décodage permet de découvrir qu'il s'agit uniquement de l'élément JSON brut provenant des `données d'identification` de l'instance de service, plus certaines valeurs `iam_...` :
  ```
  {
    "apikey": "8DZkOuLVwnVA1YmG81gk3P26Ny8e5aVn5ahZY-UD8t54",
    "host": "59aa7b1a-5aab-4f2d-9a73-8c3b29408f96-bluemix.cloudant.com",
    "iam_apikey_description": "Auto generated apikey during resource-key operation for Instance - crn:v1:bluemix:public:cloudantnosqldb:us-south:a/480fd1ec14ac540c5bc37da799a63437:bfa342dd-4b6f-4dfe-a35a-9108fb0ec571::",
    "iam_apikey_name": "auto-generated-apikey-5327ec1d-09a5-4237-9735-7e01fe741bc7",
    "iam_role_crn": "crn:v1:bluemix:public:iam::::serviceRole:Writer",
    "iam_serviceid_crn": "crn:v1:bluemix:public:iam-identity::a/480fd1ec14ac540c5bc37da799a63437::serviceid:ServiceId-f5da230c-d414-4854-b15b-42bffdaaef5b",
    "password": "f8256d2a86222975bd27275213168a4270a46f2a28d949224ac1c9776301cee6",
    "port": 443,
    "url": "https://59aa7b1a-5aab-4f2d-9a73-8c3b29408f96-bluemix:f8256d2a86222975bd27275213168a4270a46f2a28d949224ac1c9776301cee6@59aa7b1a-5aab-4f2d-9a73-8c3b29408f96-bluemix.cloudant.com",
    "username": "59aa7b1a-5aab-4f2d-9a73-8c3b29408f96-bluemix"
  }
  ```
  {: screen}

Le secret Kubernetes ne peut pas être extrait par votre code d'application sauf si le fichier `deployment.yml` déclare une valeur `env` qui référence le secret. Lorsque vous utilisez un kit de démarrage, un code de ce type est généré automatiquement.

### Le kit de démarrage a généré du code
{: #credentials-starterkit-kube-gencode}

Dans ce cas, vous avez créé cette application à partir d'un kit de démarrage. Le code généré à partir d'un kit de démarrage est conçu pour être portable et pour s'exécuter localement, dans Cloud Foundry ou dans Kubernetes. La bibliothèque, `IBMCloudEnv`, permet de fournir une couche d'abstraction entre le code d'application et l'extraction des variables d'environnement contenant les données d'identification pour les instances de service.

Le code créé à partir du kit de démarrage a une dépendance par rapport à la bibliothèque `IBMCloudEnv` et génère la sortie suivante.

* Un fichier `bindings.yml`, qui est inclus en ligne dans le fichier `deployment.yml`, avec ce contenu :
  ```yaml
   - name: service_cloudant
     valueFrom:
     secretKeyRef:
        name: binding-blarg-cloudant-1538408663553
        key: binding
        optional: true
  ```
  {: codeblock}

  L'élément `secretKeyRef.name` expose le secret Kubernetes défini afin qu'il puisse être extrait par l'application en tant que variable d'environnement simple dans le code d'application.

* Les instructions de la bibliothèque `IBMCloudEnv` sont encapsulées dans un fichier `mappings.json`, qui se trouve dans la base de code générée par le kit de démarrage. Le fichier `mappings.json` inclut des définitions individuelles pour chaque donnée d'identification :
  ```json
  "cloudant_apikey": {
    "searchPatterns": [
      "user-provided:blarg-cloudant-1538408663553:apikey",
      "cloudfoundry:$['cloudant'][0].credentials.apikey",
      "env:service_cloudant:$.apikey",
      "env:cloudant_apikey",
      "file:/server/localdev-config.json:$.cloudant_apikey"
    ]
  },
  ```
  {: codeblock}

  Le fichier `mappings.json` utilise la syntaxe `jsonpath` et l'ordre du tableau `searchPatterns` pour guider la logique `IBMCloudEnv`.

* Utilisez le code suivant pour extraire la clé d'API Cloudant (pseudocode) :
  ```java
  cloudantApiKey = IBMCloudEnv.getValue('cloudant_apikey');
  ```
  {: codeblock}

La bibliothèque `IBMCloudEnv` détecte automatiquement si votre application s'exécute dans Kubernetes, Cloud Foundry ou une instance de serveur virtuel (traitement identique à celui du docker local) et applique l'élément `searchPattern` correct pour trouver la valeur à renvoyer.

C'est pourquoi, le fichier `mappings.json` doit être considéré comme _liste définitive_ des valeurs préconfigurées et immédiatement disponibles provenant de l'environnement dans lequel votre application doit s'exécuter. Les valeurs sont chargées dans l'environnement pour le cluster ciblé lors de l'utilisation de la fonction **Configurer la distribution continue**.
