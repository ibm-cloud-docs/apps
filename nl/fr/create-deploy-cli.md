---
copyright:

  years: 2018

lastupdated: "2018-10-02"

---

{:new_window: target="_blank"}  
{:shortdesc: .shortdesc}  
{:screen: .screen}  
{:codeblock: .codeblock}  
{:pre: .pre}
{:tip: .tip}

# Création et déploiement d'applications à l'aide de l'interface de ligne de commande
{: #developing}

Vous pouvez utiliser l'interface de ligne de commande {{site.data.keyword.Bluemix}} pour créer et déployer votre application. {:shortdesc}

## Avant de commencer
{: #prereqs}

Installez l'interface de ligne de commande {{site.data.keyword.Bluemix_notm}}, le plug-in d'interface de ligne de commande {{site.data.keyword.dev_cli_notm}} et d'autres plug-in et outils recommandés. Pour plus d'informations, voir [Initiation à l'interface de ligne de commande IBM Cloud](/docs/cli/index.html). 

## Création de votre application
{: #create}

Vous pouvez créer une toute nouvelle application ou créer une application compatible cloud en utilisant votre code existant.  

### Création d'une toute nouvelle application

1. Exécutez la commande [`ibmcloud dev create`](/docs/cli/idt/commands.html#create) dans le répertoire de votre choix. 
2. Sélectionnez **Service de back-end / Appli Web** comme type d'application. 
3. Sélectionnez **Noeud** comme type de langue. 
4. Sélectionnez **Base Express.js (appli Web)** comme kit de démarrage à utiliser. 
5. Entrez un nom pour votre application et sélectionnez le groupe de ressources que vous souhaitez utiliser (si nécessaire). N'ajoutez pas de services pour l'instant. 
6. Sélectionnez l'option **BM DevOps, en utilisant Cloud Foundry** pour créer une chaîne d'outils DevOps. Vous devrez peut-être configurer des clés SSH pour finaliser cette étape. 
7. Entrez un nom d'hôte unique, par exemple, `abc-devhost`. Ce nom d'hôte correspond à la route de votre application, `abc-devhost.mybluemix.net`.

La création de l'application et de la chaîne d'outils dure quelques secondes. Vous pouvez surveiller le statut de cette opération dans l'invite de commande. 

### Création d'une application à l'aide du code existant

1. Clonez l'application [Hello World sample app](https://github.com/IBM-Cloud/node-helloworld) en exécutant la commande suivante dans le répertoire de votre choix. 

  ```
  git clone https://github.com/IBM-Cloud/node-helloworld.git
  ```
  {: codeblock}

2. Accédez au répertoire dans lequel vous avez cloné le modèle d'application et exécutez la commande [`ibmcloud dev enable`](/docs/cli/idt/commands.html#enable). 
3. Choisissez de continuer sans valider pour l'instant les modifications apportées à GitHub. 
4. Choisissez de continuer lorsque vous êtes invité à poursuivre avec la langue de noeud qui est détectée. 
5. Sélectionnez le groupe de ressources que vous souhaitez utiliser (si nécessaire). N'ajoutez pas de services pour l'instant. 
6. L'application est créée au bout de quelques secondes.  
7. Vous pouvez choisir de fusionner manuellement les fichiers de déploiement et de configuration qui sont sauvegardés dans le répertoire de l'application lors de la création de l'application. Ou, vous pouvez ignorer cette étape pour le moment.

## Génération de votre application et exécution de celle-ci localement
{: #build-run}

Quelle que soit l'option que vous avez utilisée pour créer votre application, vous pouvez désormais la générer et l'exécuter localement. 

1. Accédez à votre répertoire d'application et assurez-vous que Docker est en cours d'exécution sur votre système. 
2. Exécutez la commande [`ibmcloud dev build`](/docs/cli/idt/commands.html#build) pour générer votre application. 
3. Exécutez la commande [`ibmcloud dev run`](/docs/cli/idt/commands.html#run) pour commencer à exécuter votre application localement.
4. Visualisez votre application qui s'exécute localement en vous connectant à l'URL `http://localhost:3000` ou à une URL similaire.
5. Appuyez sur les touches **Ctrl+C** pour arrêter votre application. 

Vous pouvez également utiliser des [commandes composées](/docs/cli/idt/commands.html#compound), par exemple, `ibmcloud dev build/run`, pour émettre de façon séquentielle une version suivie d'une exécution.
{: tip}

## Ajout d'un service et modification du code
{: #add-service}

Maintenant que votre application peut s'exécuter localement, vous pouvez ajouter un service et modifier du code. 

1. Exécutez la commande [`ibmcloud dev edit`](/docs/cli/idt/commands.html#edit). 
2. Suivez les invites pour créer et connecter à votre application un service lié aux données, par exemple, {{site.data.keyword.cloudant_short_notm}}. Il peut être nécessaire de sélectionner une région et un plan pour le service.
3. Vous pouvez choisir de fusionner manuellement les fichiers de déploiement et de configuration qui sont sauvegardés dans le répertoire de l'application lors de la création du service. Ou, vous pouvez ignorer cette étape pour le moment.
4. Modifiez votre code. Par exemple, modifiez le fichier `/public/index.html` ou un fichier similaire. Si vous utilisez le modèle d'application `ExpressJS`, vous pouvez remplacer la chaîne `Congratulations!` par `Hello World!`, par exemple.
5. Sauvegardez les fichiers que vous avez modifiés. 

## Déploiement d'{{site.data.keyword.Bluemix_notm}}
{: #deploy}

Il existe deux manières de déployer une application {{site.data.keyword.Bluemix_notm}}, en fonction de la manière dont cette application est configurée.  

### Déploiement de votre application à l'aide d'une chaîne d'outils DevOps

Si vous avez précédemment créé une chaîne d'outils DevOps pour votre application, déployer une nouvelle version revient tout simplement à valider et envoyer votre code vers le répertoire dans votre chaîne d'outils.  

1. Exécutez la commande `git add`. 
2. Exécutez la commande `git commit -m "made changes"` pour valider les modifications. 
3. Exécutez la commande `git push origin master` pour un envoi vers la branche maître.
4. Affichez la chaîne d'outils DevOps pour votre application à partir de la console {{site.data.keyword.Bluemix_notm}}. Vous pouvez afficher la chaîne d'outils dans un navigateur Web en exécutant la commande [`ibmcloud dev console`](/docs/cli/idt/commands.html#console) à partir du répertoire d'application et en cliquant sur **Afficher la chaîne d'outils**.
5. Affichez le pipeline au sein de la chaîne d'outils pour vérifier qu'une nouvelle version a démarré.

### Déploiement manuel de votre application

Vous pouvez déployer manuellement votre application à l'aide de la commande [`deploy`](/docs/cli/idt/commands.html#deploy). Par exemple, procédez comme suit pour déployer manuellement votre application dans Kubernetes.

1. Vérifiez qu'un [cluster Kubernetes a bien été créé](https://console.bluemix.net/containers-kubernetes/overview).
2. Exécutez la commande [`ibmcloud dev deploy -t container`](/docs/cli/idt/commands.html#deploy). 
3. Lorsque vous y êtes invité,confirmez le nom de l'image de conteneur et de cluster à utiliser. 
4. Le déploiement est effectué au bout de quelques minutes. 

## Affichage de votre application
{: #view}

1. Pour afficher l'URL de votre application qui s'exécute sur {{site.data.keyword.Bluemix_notm}}, exécutez la commande [`ibmcloud dev view`](/docs/cli/idt/commands.html#view). 
2. Pour afficher les détails relatifs aux données d'identification, aux services et à la chaîne d'outils de votre application à partir de la console {{site.data.keyword.Bluemix_notm}}, exécutez la commande [`ibmcloud dev console`](/docs/cli/idt/commands.html#console).  

