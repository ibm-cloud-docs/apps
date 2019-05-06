---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-23"

keywords: apps, application, troubleshooting, debug apps, known issues, debug, help, configuration, app, troubleshoot, error, errors, failure, failed, fail, issues, applications

subcollection: creating-apps

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:troubleshoot: data-hd-content-type='troubleshoot'}

# Traitement des incidents liés à la création d'applications
{: #managingapps}

Des problèmes d'ordre général liés à la création d'applications peuvent survenir, par exemple, les applications ne peuvent pas être mises à jour ou les caractères codés sur deux octets ne sont pas affichés. Dans de nombreux cas, ces problèmes peuvent être résolus en quelques opérations simples.
{:shortdesc}

## Des modifications n'ont pas été sauvegardées
{: #ts_unsaved_changes}
{: troubleshoot}

Lorsque vous cliquez sur des éléments de la page des détails de l'application, il est possible que vous ne puissiez pas effectuer d'action. Vous pouvez également être invité à sauvegarder vos modifications avant de pouvoir continuer.

Lorsque vous essayez de vérifier votre application ou vos services sur la page des détails de l'application, le message d'erreur suivant s'affiche :
{: tsSymptoms}

`You have unsaved changes. Are you sure you want to leave this page?`

Lorsque vous survolez avec la souris les zones **INSTANCES** ou **QUOTA DE MEMOIRE** dans le panneau du contexte d'exécution, les valeurs changent. Ce comportement est normal. Toutefois, vous êtes invité à sauvegarder les paramètres de mémoire ou d'instance avant d'accéder à une autre page.
{: tsCauses}

Fermez la fenêtre de message puis cliquez sur **REINITIALISER** dans votre panneau d'exécution.
{: tsResolve}

## Le basculement automatique entre les régions {{site.data.keyword.cloud_notm}} n'est pas disponible
{: #ts_failover}
{: troubleshoot}

Vous ne pouvez pas utiliser le basculement automatique entre les régions {{site.data.keyword.cloud}}. Toutefois, vous pouvez utiliser un fournisseur DNS qui prend en charge le basculement entre plusieurs adresses IP comme solution de contournement.

Lorsqu'une région {{site.data.keyword.cloud_notm}} n'est plus disponible, les applications qui sont exécutées dans cette région ne sont plus disponibles non plus, même si les mêmes applications s'exécutent dans une autre région {{site.data.keyword.cloud_notm}}.
{: tsSymptoms}

{{site.data.keyword.cloud_notm}} ne fournit pas encore le basculement automatique d'une région vers une autre.
{: tsCauses}

Vous pouvez utiliser un fournisseur DNS qui prend en charge le basculement intelligent entre plusieurs adresses IP et configurer manuellement vos paramètres DNS pour activer le basculement automatique entre les régions {{site.data.keyword.cloud_notm}}. Les fournisseurs DNS avec cette fonction incluent NSONE, Akamai et Dyn.
{: tsResolve}

Lorsque vous configurez vos paramètres DNS, vous devez spécifier les adresses IP publiques des régions {{site.data.keyword.cloud_notm}} dans lesquelles vos applications s'exécutent. Pour obtenir l'adresse IP publique d'une région {{site.data.keyword.cloud_notm}}, utilisez la commande `nslookup`. Vous pouvez, par exemple, entrer la commande suivante dans une fenêtre de ligne de commande.
```
nslookup cloud.ibm.com
```
{: codeblock}

## Impossible d'accéder aux services {{site.data.keyword.cloud_notm}} en raison d'erreurs d'autorisation
{: #ts_vcap}
{: troubleshoot}

Des erreurs d'autorisation peuvent se produite lorsque votre application accède à un service {{site.data.keyword.cloud_notm}} si les données d'identification du service sont codées en dur dans votre application.

Une fois que vous avez configuré votre application pour qu'elle communique avec un service {{site.data.keyword.cloud_notm}}, vous la déployez dans {{site.data.keyword.cloud_notm}}. Toutefois, vous ne pouvez pas utiliser l'application pour accéder au service {{site.data.keyword.cloud_notm}} et recevez une erreur d'autorisation.
{: tsSymptoms}

Il se peut que les données d'identification codées en dur dans l'application soient incorrectes. A chaque fois que le service est recréé, les données d'identification permettant d'y accéder changent.
{: tsCauses}

Au lieu de coder en dur les données d'identification dans votre application, utilisez les paramètres de connexion de la variable d'environnement VCAP_SERVICES. Les méthodes d'utilisation des paramètres de connexion de la variable d'environnement VCAP_SERVICES varient selon les langages de programmation. Par exemple, pour les applications Node.js, vous pouvez utiliser la commande suivante :
{: tsResolve}

```
process.env.VCAP_SERVICES
```

Pour plus d'informations sur les commandes que vous pouvez utiliser dans d'autres langages de programmation, voir [Java](http://docs.run.pivotal.io/buildpacks/java/java-tips.html#env-var){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe") et[Ruby](http://docs.run.pivotal.io/buildpacks/ruby/ruby-tips.html#env-var){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe").

## Erreurs 502 Bad Gateway (passerelle incorrecte)
{: #ts_502_error}
{: troubleshoot}

Si des erreurs `502 Bad Gateway` (passerelle incorrecte) sont générées lors d'une interaction avec des applications dans {{site.data.keyword.cloud_notm}}, vérifiez la page de statut {{site.data.keyword.cloud_notm}} puis effectuez les actions appropriées.

Vous recevez des messages d'erreur commençant par 502 Bad Gateway. Par exemple, vous pourriez rencontrer le message `502 Bad Gateway: Registered endpoint failed to handle the request.`
{: tsSymptoms}

Une erreur de passerelle incorrecte se produit généralement lorsque vous accédez à un site Web qui utilise un serveur proxy pour stocker et relayer les données du serveur principal hébergeant le site. Il se peut que le serveur principal et le serveur proxy ne se connectent pas correctement. Le code d'état HTTP 502 s'affiche alors dans votre fenêtre de navigateur. Ce code d'état indique que le serveur principal du site n'a pas reçu l'implémentation HTTP attendue de la part du serveur proxy.
{: tsCauses}

Motifs moins fréquents d'une erreur de passerelle incorrecte : interruptions du fournisseur d'accès internet, configurations incorrectes du pare-feu et erreurs de cache du navigateur.

Si vous suspectez l'arrêt d'un service {{site.data.keyword.cloud_notm}}, consultez d'abord la page [{{site.data.keyword.cloud_notm}} Statut ](https://cloud.ibm.com/status){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe"). L'[utilisation du service dans une autre région {{site.data.keyword.cloud_notm}}](/docs/resources/connect_external_app?topic=resources-externalapp){: new_window} peut être une solution palliative. Si le statut du service est normal, essayez la procédure suivante pour résoudre le problème :
{: tsResolve}

  * Réessayez l'action :
    * Rechargez la page en appuyant sur la touche F5 de votre clavier ou en cliquant sur le bouton **Actualiser**. Si cette étape ne fonctionne pas, videz le cache de votre navigateur et supprimez les cookies, puis rechargez la page.
    * Utilisez un navigateur différent.
    * Redémarrez votre routeur, votre modem et votre ordinateur. Le réamorçage de ces unités peut éliminer diverses erreurs à l'origine de l'erreur 502.
  * Patientez et essayez à nouveau ultérieurement. Des problèmes temporaires peuvent se produire avec votre fournisseur d'accès Internet ou les services {{site.data.keyword.cloud_notm}}. Vous pouvez attendre jusqu'à ce que les problèmes temporaires soient résolus.
  * Si le problème persiste, contactez le support {{site.data.keyword.cloud_notm}}. Pour plus d'informations, voir [Contacter le support {{site.data.keyword.cloud_notm}}](/docs/get-support?topic=get-support-getting-customer-support){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe"). 

## Les applications Android ne peuvent pas recevoir de {{site.data.keyword.mobilepushshort}}
{: #ts_push}
{: troubleshoot}

Dans certaines régions où Google n'est pas accessible, les applications Android ne peuvent pas recevoir les notifications que vous envoyez via le service IBM {{site.data.keyword.mobilepushshort}}. Dans ce cas, une solution de contournement consiste à utiliser des services tiers.

Vous liez un service {{site.data.keyword.mobilepushshort}} pour votre application {{site.data.keyword.cloud_notm}} et envoyez un message aux unités enregistrées. Toutefois, les applications qui sont développées sous Android ne peuvent pas recevoir vos notifications dans certaines régions.
{: tsSymptoms}

Le service IBM {{site.data.keyword.mobilepushshort}} utilise le service GCM (Google Cloud Messaging) pour diffuser les notifications aux applications mobiles développées sur Android. Les applications mobiles doivent pouvoir accéder au service GCM pour que les applications Android puissent recevoir les notifications. Dans les régions où les applications Android ne peuvent pas accéder au service GCM, ces dernières ne peuvent pas recevoir de notifications {{site.data.keyword.mobilepushshort}}.
{: tsCauses}

Comme solution palliative, utilisez des services de tiers qui ne sont pas basés sur les services GCM, par exemple [Pushy ](https://pushy.me){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe"), [getui ](http://www.getui.com/){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe") et [jpush ](https://www.jpush.cn/){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe").
{: tsResolve}

## Les caractères codés sur deux octets ne s'affichent pas correctement lorsque des applications sont envoyées par commande push vers {{site.data.keyword.cloud_notm}}
{: #ts_doublebytes}
{: troubleshoot}

Il se peut que les caractères codés sur deux octets ne s'affichent pas correctement si la prise en charge Unicode n'est pas configurée correctement pour le servlet ou les fichiers JSP.

Lorsqu'une application est envoyée par commande push dans {{site.data.keyword.cloud_notm}}, les caractères codés sur deux octets spécifiés dans l'application ne s'affichent pas correctement.
{: tsSymptoms}

Le problème peut se produire si la prise en charge Unicode n'est pas configurée correctement pour le servlet ou les fichiers JSP.
{: tsCauses}

Utilisez le code suivant dans votre servlet ou votre fichier JSP :
{: tsResolve}

  * Dans le fichier source servlet
  ```java
	response.setContentType("text/html; charset=UTF-8");
	```
  {: codeblock}

  * Dans l'élément JSP
  ```jsp
	<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
	```
  {: codeblock}

## Les applications Node.js ne peuvent pas être déployées
{: #ts_nodejs_deploy}
{: troubleshoot}

Des problèmes peuvent survenir lorsque vous mettez à jour ou déployez une application Node.js dans {{site.data.keyword.cloud_notm}}.

Lorsque vous mettez à jour ou déployez votre application Node.js dans {{site.data.keyword.cloud_notm}}, l'un des messages d'erreur suivants peut s'afficher :
{: tsSymptoms}

`An app was not successfully detected by any available buildpack.`

`Instance (index 0) failed to start accepting connections.`

`Cannot get instances since staging failed.`

Causes possibles :
{: tsCauses}

  * La commande de démarrage n'a pas été spécifiée.
  * Des fichiers requis pour déployer une application Node.js sont manquants dans l'application ou résident dans un dossier autre que le répertoire racine.

Utilisez l'une des méthodes suivantes, selon la cause du problème :
{: tsResolve}

  * Spécifiez la commande de démarrage à l'aide d'une des méthodes suivantes :
     * Utilisez l'interface de ligne de commande Cloud Foundry. Exemple :
      ```
		  ibmcloud cf push MyUniqueNodejs01 -p app_path -c "node app.js"
		  ```
      {: codeblock}

    * Utilisez le fichier [package.json ](https://www.npmjs.com/package/jsonfile){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe"). Exemple :
	    ```json
		  {
        ...
  	    "scripts": {
	 		  "start": "node app.js"
 	   }
	    }
	    ```

    * Utilisez le fichier `manifest.yml`. Exemple :
	    ```
		  applications:
  name: MyUniqueNodejs01
  ...
      command: node app.js
  ...
      ```

  * Vérifiez qu'un fichier `package.json` existe dans votre application Node.js pour que le pack de construction Node.js puisse reconnaître l'application. Prenez soin de placer ce fichier dans le répertoire racine de votre application.
    L'exemple suivant représente un fichier `package.json` simple :
	```json
	{
        "name": "MyUniqueNodejs01",
        "version": "0.0.1",
        "description": "A sample package.json file",
        "dependencies": {
                "express": "3.4.x",
                "jade": "1.1.x"
        },
        "engines": {
                "node": "0.10.x"
        },
        "scripts": {
                  "start": "node app.js"
        }
 }
    ```

Pour obtenir des conseils supplémentaires relatifs aux applications Node.js, voir [Tips for Node.js Applications ](https://docs.cloudfoundry.org/buildpacks/node/node-tips.html){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe").

## Des erreurs de configuration figurent dans le fichier `server.xml` après avoir importé une application {{site.data.keyword.cloud_notm}} Liberty dans Eclipse
{: #ts_eclipse}
{: troubleshoot}

Si vous rencontrez des erreurs de configuration dans le fichier `server.xml` après avoir importé une application {{site.data.keyword.cloud_notm}} Liberty dans Eclipse, vous devrez peut-être supprimer du projet le fichier `server.xml`.

Après avoir importé une application {{site.data.keyword.cloud_notm}} Liberty dans Eclipse, vous rencontrez des erreurs de configuration dans le fichier `server.xml` dans la vue Erreurs d'Eclipse.
{: tsSymptoms}

Le pack de construction Liberty utilise le fichier `server.xml` pour configurer l'application et génère un fichier `runtime-vars.xml` lorsque l'application Liberty est envoyée par commande push dans {{site.data.keyword.cloud_notm}}. Lorsque vous importez l'application dans Eclipse, le fichier `runtime-vars.xml` n'existe pas dans votre environnement local.
{: tsCauses}

Pour résoudre ce problème, supprimez le fichier server.xml du projet. Le pack de construction crée le fichier `server.xml` de manière dynamique lorsque vous envoyez par commande push l'application sous forme d'application WAR. Pour plus d'informations, voir [Liberty for Java](/docs/runtimes/liberty?topic=liberty-liberty_runtime#liberty_runtime).
{: tsResolve}

## Les applications ne peuvent pas être transférées à l'aide de packs de construction personnalisés
{: #ts_bp_compilation}
{: troubleshoot}

Il se peut que vous ne puissiez pas déployer d'application dans {{site.data.keyword.cloud_notm}} à l'aide d'un pack de construction personnalisé si les scripts que ce dernier contient ne sont pas des fichiers exécutables.

Lorsque vous déployez une application dans {{site.data.keyword.cloud_notm}} à l'aide d'un pack de construction personnalisé, le message d'erreur `The application failed to stage, so there are no instances to display` s'affiche.
{: tsSymptoms}

Ce problème peut se produire si des scripts (tels que le script de détection, le script de compilation ou le script de publication) ne sont pas exécutables.
{: tsCauses}

Vous pouvez utiliser la commande [Git update ](http://git-scm.com/docs/git-update-index){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe") pour faire en sorte que chaque script soit exécutable. Par exemple, vous pouvez entrer `git update --chmod=+x script.sh`.
{: tsResolve}

## Impossible de déployer une application depuis Delivery Pipeline dans {{site.data.keyword.cloud_notm}} Continuous Delivery
{: #ts_devops_to_bm}
{: troubleshoot}

 Il se peut que vous ne puissiez pas déployer votre application à l'aide de {{site.data.keyword.deliverypipeline}} dans {{site.data.keyword.contdelivery_short}} si le fichier `manifest.yml` n'est pas présent dans votre application.

 Lorsque vous déployez une application à l'aide de {{site.data.keyword.deliverypipeline}} dans {{site.data.keyword.contdelivery_short}}, il se peut que le message d'erreur `Unable to detect a supported application type` s'affiche.
 {: tsSymptoms}

 Ce problème peut survenir car le pipeline requiert un fichier `manifest.yml` pour déployer une application dans {{site.data.keyword.cloud_notm}}.
 {: tsCauses}

 Pour remédier à ce problème, vous devez créer un fichier `manifest.yml`. Pour plus d'informations sur la création du fichier `manifest.yml`, voir [Manifeste d'application](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps#appmanifest).
 {: tsResolve}

## Dépassement de votre quota de stockage
{: #exceed_quota}

Si les travaux de génération ou de déploiement échouent et que le message suivant est généré, vous pouvez supprimer vos images en utilisant les commandes CLI suivantes.
`Status: unauthorized: You have exceeded your storage quota. Delete one or more images, or review your storage quota and pricing plan.`

* Installez [l'interface de ligne de commande {{site.data.keyword.cloud_notm}}](/docs/cli?topic=cloud-cli-ibmcloud-cli) si ce n'est aps déjà fait. 
* Connectez-vous à {{site.data.keyword.cloud_notm}} à l'aide de la commande `ibmcloud login` et faites en sorte qu'elle désigne l'espace dans lequel vous vous trouvez. 
* Répertoriez vos images en utilisant `ibmcloud cr images`.
* Supprimez toute image non utilisée en utilisant `ibmcloud cr image-rm <respository>:<tag>`.
* Exécutez à nouveau le travail de génération ou de déploiement ayant échoué.

## Accès aux journaux Kubernetes
{: #access_kube_logs}

Si l'application n'est pas en cours d'exécution et que vous ne pouvez pas accéder au noeud final de santé, consultez les journaux du cluster. 
* Installez [l'interface de ligne de commande {{site.data.keyword.cloud_notm}}](/docs/cli?topic=cloud-cli-ibmcloud-cli) si ce n'est aps déjà fait. 
* Connectez-vous à {{site.data.keyword.cloud_notm}} à l'aide de la commande `ibmcloud login` et faites en sorte qu'elle désigne l'espace dans lequel vous vous trouvez. 
* Répertoriez vos clusters en utilisant `ibmcloud cs clusters`. 
* Désignez votre cluster correspondant en utilisant `ibmcloud cs cluster-config <cluster-name>`.
* Exportez la variable d'environnement qui est répertoriée. 
* Affichez vos pods en utilisant `kubectl get pods`. Si vous devez installer `kubectl`, voir [Install and set up kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe").
* Vous pouvez afficher les journaux dans votre application en utilisant `kubectl logs <pod-name>.`

## Echec du démarrage de `docker` avec le message "file not found"
{: #docker_not_found}
{: troubleshoot}

Si vous tentez de démarrer Docker, le message d'erreur suivant s'affiche :
{: tsSymptoms}

```
An error exec: "docker": executable file not found in $PATH was encountered while building the Docker image.
```
{: screen}

Le client Docker n'est pas installé ou est installé mais n'est pas démarré.
{: tsCauses}

Assurez-vous que [Docker](https://docs.docker.com/install/){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe") est installé, puis démarrez-le.
{: tsResolve}

## Echec de la génération d'une application avec une erreur Docker
{: #build_error}
{: troubleshoot}

Lorsque vous tentez de générer une application à l'aide de la commande `ibmcloud dev build`, cette opération échoue uite à une erreur de nom d'utilisateur/mot de passe.
{: tsSymptoms}

Des données d'identification Docker Hub incorrectes ont été utilisées pour l'authentification.
{: tsCauses}

Déconnectez Docker Hub dans le client Docker.
{: tsResolve}


