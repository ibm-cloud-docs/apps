---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-07"

keywords: apps, mendix, mendix app, deploy, cos, storage bucket, devops toolchain, deploy, kubernetes, kube

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Déploiement de votre application Mendix sur {{site.data.keyword.containerlong_notm}}
{: #deploy-mendix-kube}

Par défaut, les applications Mendix qui ciblent le déploiement sur {{site.data.keyword.containerlong}} sont configurées dans un mode d'évaluation. Ce mode permet de commencer rapidement à créer une application et à la déployer sur le cloud, mais il ne configure pas la persistance des données ou les configurations Kubernetes avancées. Ce tutoriel vous guide lors de la configuration d'un environnement de production en configurant un volume de stockage persistant dans Kubernetes avec le service {{site.data.keyword.cos_full_notm}}.
{: shortdesc}

## Avant de commencer
{: #prereqs-mendix-kube}

* Créez votre application Mendix. Pour plus d'informations, voir [Création d'applications Mendix](/docs/apps/tutorials?topic=creating-apps-create-mendix).
* Installez l'[interface de ligne de commande {{site.data.keyword.dev_cli_notm}}](/docs/cli?topic=cloud-cli-getting-started), qui inclut l'interface de ligne de commande {{site.data.keyword.containershort_notm}}.
* Connectez-vous à l'interface de ligne de commande `ibmcloud` et configurez `kubectl` pour [accéder au cluster Kubernetes](/docs/containers?topic=containers-cs_cluster_tutorial#cs_cluster_tutorial_lesson3).

## Création d'une instance de service Cloud Object Storage
{: #cos-mendix-kube}

Démarrez à partir de votre page **Détails de l'application** et procédez comme suit :
1. Cliquez sur **Ajouter un service**.
2. Sélectionnez **Stockage**, puis cliquez sur **Suivant**.
3. Ensuite, sélectionnez l'option **Cloud Object Storage**, puis cliquez sur **Suivant**.
4. Des plans de tarification pour votre instance {{site.data.keyword.cos_full_notm}} s'affichent. Sélectionnez le plan de tarification qui répond le mieux à vos besoins, puis cliquez sur **Créer** pour créer une instance du service {{site.data.keyword.cos_full_notm}} à utiliser avec votre application de Mendix.

  Si vous préférez utiliser une instance existante du service {{site.data.keyword.cos_full_notm}}, cliquez sur **Ajouter un service** puis sélectionnez l'instance existante qui sera utilisée par votre application.
  {: tip}

## Création d'un compartiment de stockage
{: #storage-bucket-mendix-kube}

Une fois qu'une instance du service {{site.data.keyword.cos_full_notm}} est associée à votre application Mendix, vous devez créer un compartiment de stockage dans lequel les données pourront être sauvegardées. Pour créer un compartiment, cliquez sur **...** pour l'instance {{site.data.keyword.cos_full_notm}}, puis sélectionnez **Ouvrir le tableau de bord**.  

La tableau de bord du service {{site.data.keyword.cos_full_notm}} s'ouvre dans une nouvelle fenêtre, sur l'onglet **Compartiments**. Cliquez sur **Créer un compartiment** et suivez les étapes permettant de créer un compartiment à l'aide d'un nom unique. Pour les besoins de ce tutoriel, créez un compartiment nommé `my-mendix-bucket`.

## Configuration du stockage persistant
{: #kube-storage-mendix}

Ensuite, servez-vous de la documentation concernant le [stockage des données sur {{site.data.keyword.cos_full_notm}}](/docs/containers?topic=containers-object_storage). Une réservation `PersistentVolumeClaim` et un volume `PersistentVolume` sont créés dans votre cluster Kubernetes et peuvent être utilisés par l'instance de base de données PostGres qui s'exécute au sein de votre cluster dans le cadre de l'application Mendix. Prenez soin de créer la réservation `PersistentVolumeClaim` à l'aide du compartiment `my-mendix-bucket` comme décrit à l'étape précédente, et vérifiez le nom `PersistentVolumeClaim` afin de l'utiliser lors de la prochaine étape.

## Edition du fichier `postgres-deployment.yaml`
{: #postgres-deploy-mendix}

Une fois qu'un volume persistant est configurée pour votre cluster Kubernetes, l'étape suivante consiste à modifier le déploiement de base de données PostgGres qui s'exécute dans votre cluster. Tout d'abord, vous devez éditer les fichiers dans le référentiel Git qui ont été créés dans le cadre de l'étape d'intégration de chaîne d'outils IBM DevOps. Pour trouver le référentiel Git, revenez sur la page **Détails de l'application** et cliquez sur le lien d'URL Git à partir de la vignette **Détails sur le déploiement**.

Vous pouvez cloner le référentiel Git vers votre ordinateur local ou apporter les modifications suivantes dans l'éditeur en ligne. Ouvrez le fichier `chart/{app name}/templates/postgres-deployment.yaml` (remplacez `{app name}` par le nom de votre application Mendix). Par défaut, le fichier ne comporte pas d'entrées `volumeMount` ou `volumes`, par conséquent, toutes les données sont stockées en mémoire au sein du pod de déploiement en cours d'exécution. Vous devez ajouter les entrées `volumeMount` `volumes` au fichier `deployment.yaml` de Kubernetes de sorte que les données soient sauvegardées dans le compartiment {{site.data.keyword.cos_full_notm}} et ne soient pas perdues si le pod redémarre. 

Consultez l'exemple de fichier `postgres-deployment.yaml` suivant qui comprend les entrées `volumeMount` et `volumes` :  
```yaml
apiVersion: apps/v1beta1
kind: Deployment
metadata:
  name: "{appname}-postgres"
spec:
  replicas: 1
  template:
    metadata:
      labels:
        service: "{appname}-postgres"
    spec:
      containers:
        - name: "{appname}-postgres"
          image: postgres:10.1
          ports:
            - containerPort: 5432
          env:
            - name: POSTGRES_DB
              value: db0
            - name: POSTGRES_USER
              value: mendix
            - name: POSTGRES_PASSWORD
              value: mendix
          volumeMounts:
            - mountPath: "/var/lib/postgresql/data"
              name: "mendix-data"
      volumes:
        - name: mendix-data
          persistentVolumeClaim:
            claimName: {pvc-name}
```

Prenez soin de remplacer `{pvc-name}` par le nom de votre réservation `PersistentVolumeClaim` issue de l'étape précédente et de ne pas écraser le nom de votre application, lequel est déjà défini dans le fichier au sein du référentiel Git. Ensuite, validez vos modifications dans le référentiel Git.

## Redéploiement
{: #redeploy-mendix-kube}

Après que les modifications de votre fichier `postgres-deployment.yaml` ont été validées dans le référentiel, une nouvelle exécution du pipeline DevOps se déclenche automatiquement. Or, elle redéploie l'application par défaut. Vous devez redéployer la toute dernière version de l'application Mendix pour que la toute dernière version de votre application soit déployée avec les dernières modifications de volume persistant.

Pour redéployer, accédez à la page **Détails de l'application** et cliquez sur **Configurer la distribution continue** dans la vignette **Déploiement de votre application**. Si le déploiement échoue dans la chaîne d'outils DevOps et génère une erreur indiquant que le fichier `.mda` de l'application est introuvable, vous devez l'exporter à nouveau depuis Mendix. Vous pouvez l'exporter à partir de l'application Mendix Modeler pour ordinateur de bureau ou en cliquant sur **Editer dans Mendix**. Ensuite, dans l'interface Web Mendix, accédez à la section **Environments** et suivez les étapes après avoir cliqué sur **Create package from teamserver**. Après que votre application a été exportée depuis Mendix, revenez sur la page **Détails de l'application** et cliquez de nouveau sur **Configurer la distribution continue**. La dernière application exportée est déployée sur votre cluster Kubernetes à l'aide de la chaîne d'outils {{site.data.keyword.cloud}} DevOps. Une fois le déploiement terminé, votre application est opérationnelle et prête à être utilisée en environnement de production.

## Vérification que votre application est en cours d'exécution
{: #verify-mendix-kube}

Une fois votre application déployée, Delivery Pipeline ou la ligne de commande indique l'URL de votre application.

1. Dans votre chaîne d'outils DevOps, cliquez sur **Delivery Pipeline** puis sélectionnez **Etape de déploiement**.
2. Cliquez sur **Afficher les journaux et l'historique**.
3. Dans le fichier journal, recherchez l'URL de l'application :

    A la fin du fichier journal, recherchez le mot `urls` ou `view`. Par exemple, une ligne similaire à `urls: my-app-devhost.mybluemix.net` ou à `View the application health at: http://<ipaddress>:<port>/health` peut être incluse dans le fichier journal.

4. Accédez à l'URL dans votre navigateur. Si l'application est en cours d'exécution, un message qui inclut `Congratulations` ou `{"status":"UP"}` s'affiche.

Si vous utilisez la ligne de commande, exécutez la commande [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) pour afficher l'URL de votre application. Accédez ensuite à l'URL dans votre navigateur.

## Informations supplémentaires
{: #more-info-mendix-kube}

Pour plus d'informations d'ordre architectural concernant l'exécution d'applications Mendix dans des environnements Kubernetes, voir la section [Run Mendix on Kubernetes](https://docs.mendix.com/developerportal/deploy/run-mendix-on-kubernetes){: new_window} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe") dans la documentation utilisateur Mendix.
