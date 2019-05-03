---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-14"

keywords: apps, credentials, virtual server instance, vsi, virtual machine, vm

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Ajout de données d'identification à votre environnement de docker local ou d'instance virtuelle
{: #add-credentials-vsi}

Découvrez comment ajouter des données d'identification de service à votre environnement de déploiement de docker local ou d'instance virtuelle.
{: shortdesc}

## Votre code + Instance de serveur virtuel ou docker local
{: #credentials-byoc-vsi}

Sous VSI ou votre docker local, l'environnement est entièrement à vous. Par exemple, vous pouvez créer un code similaire à l'exemple suivant et fournir la valeur d'environnement des données d'identification à votre application lors de son exécution.
```
password = getEnvironment('password');
```
{: codeblock}

Dans Bash, vous pouvez créer un code similaire à l'exemple suivant :
```bash
export password="someThingSensitive"
# run app locally.  If node, something like:
npm run start
```
{: codeblock}

Dans Docker, vous pouvez créer un code similaire à l'exemple suivant :
```
docker run -p 80:8080 -e password="someThingSensitive"
```
{: codeblock}

## Kit de démarrage + VSI (ou docker local)
{: #credentials-starterkit-vsi}

### Mode de préparation de l'instance de serveur virtuel

L'environnement est entièrement sous votre contrôle comme si vous exécutiez l'application depuis votre ordinateur portable (autrement dit, le docker local). Etant donné que VSI est réellement non virtualisé du point de vue de l'application en cours d'exécution, il n'existe aucun _secret_ (comme dans Kubernetes) ou _service_ (comme dans Cloud Foundry).

### Le kit de démarrage a généré du code
{: #starterkit-generated-code-vsi}

Le code généré à partir d'un kit de démarrage inclut la bibliothèque `IBMCloudEnv` native, qui agit sur l'extraction des valeurs d'environnement de façon à ce que le code d'application soit portable afin d'être exécuté sur plusieurs cibles de déploiement. Avec le docker virtuel ou local, cet environnement doit être préparé avec des valeurs qui répondent à la bibliothèque `IBMCloudEnv` et qui ne proviennent _pas nécessairement_ de variables d'environnement réelles.

Pour vous faciliter la tâche, les instructions `mappings.json` incluses avec la sortie générée par le kit de démarrage ont des références à un fichier local à partir duquel la bibliothèque `IBMCloudEnv` dérive les valeurs que l'application peut utiliser.

Par exemple, notez la dernière ligne dans la section suivante du fichier `mappings.json` :
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

Si vous utilisez la fonction "Configurer la distribution continue" quand vous créez une application, le fichier `/server/localdev-config.json` est retiré du référentiel GitLab. Pour des raisons de sécurité, il est préférable de ne pas placer vos données d'identification dans un référentiel de codes source.

Si vous utilisez `git clone` sur le référentiel GitLab créé pour démarrer le développement actif, notez que le fichier `.gitignore` ignore spécifiquement `server/localdev-config.json` pour empêcher un enregistrement accidentel d'un fichier incluant des données d'identification sensibles. Toutefois, VSI__ a besoin de ce fichier, tout comme le développeur qui utilise un ordinateur portable.

Vous pouvez extraire le fichier `server/localdev-config.json` en procédant comme suit :

1. Utilisez `git clone` sur le référentiel Gitlab qui a été automatiquement créé lors de l'utilisation de la fonction "Configurer la distribution continue".
2. Installez l'interface de ligne de commande [{{site.data.keyword.cloud_notm}}](/docs/cli?topic=cloud-cli-ibmcloud-cli), qui inclut le plug-in `dev`.
3. Utilisez la ligne de commande `ibmcloud` pour vous connecter à {{site.data.keyword.cloud_notm}}.
4. Exécutez `ibmcloud dev get-credentials`, qui fait référence au fichier `cli-config.yml`. Le fichier `cli-config.yml` inclut des informations décrivant quelle application ou quel travail de génération inclut les données d'identification.

Si un service est retiré de l'application entre l'utilisation de la fonction "Configurer la distribution continue" et `ibmcloud dev get-credentials`, le fichier téléchargé `/server/localdev-config.json` n'aura pas toutes les données d'identification pouvant être requises par votre codebase `git clone` d'origine.
{: tip}

Si vous exécutez votre application dans un conteneur Docker, vous pouvez choisir de retirer le fichier `/server/localdev-config.json` entièrement et de transmettre les variables d'environnement sur la ligne de commande Docker.

A partir de la section "cloudant_apikey" du fichier `mappings.json`, notez l'élément `env:cloudant_apikey` avant la ligne `file...`. Cela signifie qu'une variable d'environnement nommée `cloudant_apikey` est prioritaire par rapport au contenu du fichier. De plus, même si le fichier se trouve dans l'image Docker que vous avez générée (qui n'est pas requise), vous pouvez remplacer les valeurs en les transmettant à la ligne de commande Docker.

Par exemple :
```
docker run -p 80:8080 -e cloudant_apikey="someKeyValue"
```
{: codeblock}
