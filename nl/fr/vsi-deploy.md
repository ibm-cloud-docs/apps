---
copyright:

  years: 2018

lastupdated: "2018-07-05"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Déploiement sur un serveur virtuel
{: #vsi-deploy}

Déployez les applications {{site.data.keyword.cloud}} [App Service ![Icône de lien externe](../icons/launch-glyph.svg)](https://console.bluemix.net/developer/appservice/starter-kits){: new_window} dans les instances de serveur virtuel afin de permettre aux activités développeur d'infrastructure et de plateforme d'être utilisées ensemble et d'augmenter la flexibilité et le contrôle des applications.
{: shortdesc}

Par rapport aux autres configurations, une instance de serveur virtuel offre une meilleure transparence, un meilleur caractère prévisionnel et une meilleure automatisation pour tous les types de charge de travail. Associez-la à un serveur Bare metal pour créer des combinaisons de charge de travail uniques. Par exemple, vous pouvez créer une logique de base de données à hautes performances ou un système d'apprentissage automatique avec des configurations Bare metal ou GPU exécutant un système d'exploitation de type Debian Linux.

## Avant de commencer
Pour utiliser les instances virtuelles, votre compte {{site.data.keyword.cloud_notm}} doit être activé pour l'infrastructure. Pour plus d'informations, voir [Upgrade to Infrastructure ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/dashboard/ibm-iaas-g1){: new_window}.

**Important** : les services ne sont pas liés à l'instance de serveur virtuel. Vous ne pouvez pas ajouter de services dans un serveur virtuel.

## Déploiement via Terraform
Les kits de démarrage App Service peuvent être déployés dans une instance virtuelle créée dynamiquement via [Terraform ![Icône de lien externe](../icons/launch-glyph.svg)](https://ibm-cloud.github.io/tf-ibm-docs/v0.10.0/){: new_window}, infrastructure open source utilisée comme infrastructure de code. Pour plus d'informations, voir la [documentation Terraform![Icône de lien externe](../icons/launch-glyph.svg)](https://www.terraform.io/docs/index.html){: new_window}.

## Activation de votre déploiement de pipeline

Lorsque vous créez un kit de démarrage qui utilise {{site.data.keyword.cloud_notm}} [App Service ![Icône de lien externe](../icons/launch-glyph.svg)](https://console.bluemix.net/developer/appservice/starter-kits){: new_window}, l'instance de serveur virtuel est activée. Une fois l'application créée, vous pouvez alors choisir l'emplacement de déploiement de l'application. Les kits de démarrage permettent de prendre en charge le déploiement en utilisant une chaîne d'outils Continuous Delivery. Les kits de démarrage peuvent cibler les instances Kubernetes, Cloud Foundry et de serveur virtuel. La chaîne d'outils inclut un référentiel de code source et un pipeline de déploiement.

L'option de serveur virtuel inclut plusieurs phases. Tout d'abord, le code d'application est préparé et stocké dans un référentiel Git GITLab et le code source crée une chaîne d'outils avec un pipeline. Ce dernier est conçu pour générer le code et regrouper ce dernier en utilisant le format du gestionnaire de package Debian. Terraform met ensuite à disposition une instance virtuelle. Pour finir, l'application est déployée, installée et démarrée dans l'image virtuelle en cours d'exécution et son intégrité est validée.

Une erreur survient lors de la première utilisation du pipeline car un ensemble de propriétés de compte utilisateur doit être manuellement configuré. Pour des raisons de sécurité, il n'est pas possible de transmettre ces propriétés dans la chaîne d'outils qui utilise le code source GIT. Vous devez configurer ces valeurs manuellement pour que la chaîne d'outils puisse être exécutée.

Pour accéder à la vue des propriétés d'environnement et activer votre pipeline avec vos propriétés de compte utilisateur, procédez comme suit.

1. Sur la page Détails de l'application, cliquez sur **Afficher la chaîne d'outils**.
2. Cliquez sur la vignette **Delivery Pipeline**.
3. Cliquez sur l'icône **Configurer l'étape** puis cliquez sur **Configurer l'étape** lors de l'étape de génération.
4. Cliquez sur l'onglet **Propriétés d'environnement** pour afficher les propriétés.
5. Modifiez ces propriétés dans l'onglet Propriétés d'environnement pour que l'exécution de la chaîne d'outils s'effectue correctement.

| Propriété   | Description   |
|---|---|
| `TF_VAR_ibm_sl_api_key` | La [clé d'API de l'infrastructure](#iaas-key) provient de la console d'infrastructure. |
| `TF_VAR_ibm_sl_username` | [Nom d'utilisateur de l'infrastructure](#user-key) identifiant le compte d'infrastructure |
| `TF_VAR_ibm_cloud_api_key` | La [clé d'API de plateforme](#platform-key) {{site.data.keyword.cloud_notm}} permet d'activer la création de service. |
| `PUBLIC_KEY` | [Clé publique](#public-key) définie pour activer l'accès à l'instance de serveur virtuel. |
| `PRIVATE_KEY` | [Clé privée](#public-key) définie pour activer l'accès à l'instance de serveur virtuel. **Remarque** : vous devez utiliser le formatage de style de nouvelle ligne `\n`. |
| `VI_INSTANCE_NAME` | Nom généré automatiquement pour l'instance de serveur virtuel |
| `GIT_USER` | Si vous définissez l'[état Terraform](#tform-state) afin de stocker l'état de la commande apply, le nom d'utilisateur GITLab est requis. |
| `GIT_PASSWORD` | Si vous définissez l'[état Terraform](#tform-state) afin de stocker l'état de la commande apply, le mot de passe GITLab est requis. |
{: caption="Tableau 1. Variables d'environnement à changer pour l'activation" caption-side="top"}

### Extraction de la clé d'API d'infrastructure
{: #iaas-key}

Terraform requiert une clé d'API d'infrastructure pour pouvoir créer des ressources d'infrastructure. Procédez comme suit pour extraire une clé d'infrastructure.

1. Accédez à la [liste d'utilisateurs ![Icône de lien externe](../icons/launch-glyph.svg)](https://control.bluemix.net/account/users){: new_window} de l'infrastructure. Vous pouvez également cliquer sur **Menu** > **Infrastructure** > **Compte** > **Liste d'utilisateurs**.
2. Recherchez les détails utilisateur qui créent la chaîne d'outils puis cliquez sur `Afficher` dans la colonne de clé d'API ou cliquez sur `Générer`. Quelle que soit la méthode choisie, la clé d'API s'affiche dans une fenêtre.
3. Copiez la clé d'API et remplacez la valeur dans la configuration de chaîne d'outils `TF_VAR_ibm_sl_api_key`.

### Extraction du nom d'utilisateur de l'infrastructure
{: #user-key}

Pour extraire le nom d'utilisateur de l'infrastructure, procédez comme suit.

1. Accédez à la [liste d'utilisateurs ![Icône de lien externe](../icons/launch-glyph.svg)](https://control.bluemix.net/account/users){: new_window} de l'infrastructure. Vous pouvez également cliquer sur **Menu** > **Infrastructure** > **Compte** > **Liste d'utilisateurs**.
2. Cliquez sur l'utilisateur devant créer la chaîne d'outils.
3. Faites défiler jusqu'à la propriété de nom d'utilisateur VPN****.
4. Coupez et collez cette valeur et remplacez la configuration de chaîne d'outils `TF_VAR_ibm_sl_username`.

### Extraction de la clé d'API de plateforme
{: #platform-key}

Pour créer des services de niveau de plateforme dans Terraform (bases de données et services Compose, par exemple), la clé d'API de plateforme est requise. Procédez comme suit pour extraire une clé de plateforme.

1. Sur la page [Clés d'API ![Icône de lien externe](../icons/launch-glyph.svg)](https://console.bluemix.net/iam/#/apikeys), cliquez sur **Gérer** > **Sécurité** > **Clés d'API de la plateforme**.
2. Cliquez sur **Créer**.
3. Entrez un nom et une description puis cliquez sur **Créer**.
4. Lorsque la fenêtre s'affiche, cliquez sur **Afficher** pour consulter la clé.
5. Copiez et remplacez la clé dans le tableau de bord ou téléchargez-la.
6. Remplacez la valeur de la configuration de la chaîne d'outils `TF_VAR_ibm_cloud_api_key` par la valeur générée.

### Génération de la clé publique et de la clé privée
{: #public-key}

Pour que la chaîne d'outils puisse installer le package Debian dans l'instance de serveur virtuel, procédez comme suit.

1. Sur votre client, suivez les instructions présentées ci-dessous pour créer une [paire clé publique/clé privée ![Icône de lien externe](../icons/launch-glyph.svg)](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/){: new_window}.
2. Accédez à la [vue des clés SSH de l'infrastructure ![Icône de lien externe](../icons/launch-glyph.svg)](https://control.bluemix.net/devices/sshkeys){: new_window}. Vous pouvez également cliquer sur **Menu** > **Infrastructure** > **Périphériques** > **Gérer** > **Clés SSH**.
3. Cliquez sur **Ajouter**.
4. Copiez le contenu de la clé publique précédemment créée et collez-le dans le contenu de la clé.
5. Donnez un nom à la clé puis cliquez sur **Ajouter**.

La clé privée doit se trouver sur une seule ligne. Remplacez les nouvelles lignes par `\n`. Voir l'exemple suivant.
{: tip}

```
---------BEGIN RSA KEY----------\nasdfasdfeqwtqf13rf1eqwfwe\netq3efaewf23fa23f23f\n.....\n----------END RSA KEY-------------
```
{: screen}

### Activation de l'état Terraform
{: #tform-state}

Terraform prend en charge le stockage de l'état de la commande `apply` Terraform. Ce fichier d'état exécute une deuxième fois la commande `apply` afin de déterminer si un des fichiers de configuration Terraform a été modifié. Vous pouvez stocker l'état dans le référentiel GIT où l'application et la configuration sont gérées.

Pour permettre le stockage d'état, configurez les propriétés `GIT_USER` et `GIT_PASSWORD` dans les variables d'environnement de la chaîne d'outils. Pour extraire les valeurs, procédez comme suit :

1. Dans la vue Chaînes d'outils, accédez au référentiel GIT à partir de l'outil de code.
2. Dans GIT Lab, cliquez sur l'icône **Profil** puis sur **Paramètres**.
3. Cliquez sur **Compte**, copiez le nom d'utilisateur puis remplacez la valeur `GIT_USER`.
4. Cliquez sur **Jetons d'accès**.
5. Définissez un nom pour votre jeton, sélectionnez une portée puis cliquez sur **Créer un jeton d'accès personnel**.
6. Cliquez sur l'icône de copie dans la zone `Votre nouveau jeton d’accès personnel` et remplacez la valeur de l'élément `GIT_PASSWORD` dans les propriétés de la chaîne d'outils.

L'état Terraform est stocké dans une branche appelée `terraform` et ne déclenche pas l'exécution du pipeline en cas de modification.

### Activation des opérations GIT
{: #git-repo}

Lorsque l'application est déployée dans {{site.data.keyword.cloud_notm}}, un référentiel GIT Lab est créé en vue d'héberger le code pour la gestion du code source. Vous pouvez utiliser les opérations GIT pour permettre à vos équipe de travailler et de modifier votre application. Vous pouvez consulter les dossiers inclus dans ce référentiel ainsi qu'une description de leur contenu.

#### Dossier Debian
{: #debian-folder}

Le dossier `debian` inclut la configuration requise pour pouvoir placer l'application dans un [package Debian. ![Icône de lien externe](../icons/launch-glyph.svg)](https://www.debian.org/doc/manuals/debian-faq/ch-pkgtools.en.html){: new_window}

#### Dossier Terraform
{: #terraform-folder}

Le dossier `terraform` inclut la configuration de l'infrastructure, sous forme de code pouvant être utilisé pour mettre à disposition des ressources d'infrastructure. Le fichier `main.tf` constitue la principale source pour la modification des options de votre configuration Terraform.

```
resource "ibm_compute_vm_instance" "vm1" {
    hostname = "${var.vi_instance_name}"
    domain = "example.com"
    os_reference_code = "DEBIAN_8_64"
    datacenter = "${var.datacenter}"
    network_speed = 100
    hourly_billing = true
    private_network_only = false
    cores = 1
    memory = 1024
    disks = [25]
    local_disk = false
    ssh_key_ids = [
        "${ibm_compute_ssh_key.ssh_key_gip.id}"
    ]
}
```

Vous pouvez également mettre à disposition des serveurs Bare Metal avec Terraform. Pour plus d'informations, voir la [documentation sur le fournisseur IBM Terraform ![Icône de lien externe](../icons/launch-glyph.svg)](https://ibm-cloud.github.io/tf-ibm-docs/v0.10.0/){: new_window} et [IBM Terraform Provider GIT Repo ![Icône de lien externe](../icons/launch-glyph.svg)](https://github.com/IBM-Cloud/terraform-provider-ibm){: new_window}.

Vous pouvez utiliser le fichier `variables.tf` afin de changer de centre de données à cibler pour la création de l'instance virtuelle. Pour accéder à la liste des centres de données définis sur la plateforme, voir [Data Centers ![Icône de lien externe](../icons/launch-glyph.svg)](https://www.ibm.com/cloud-computing/bluemix/data-centers){: new_window}.

Par défaut, le fichier Terraform est configuré pour Washington et `wdc04`.

```
variable "datacenter" {
  description = "Washington"
  default = "wdc04"
}
```

### Présentation des étapes de la chaîne d'outils
{: #toolchain-stages}

La chaîne d'outils affiche l'infrastructure et le déploiement d'application dans un pipeline simple. Placez l'infrastructure sous forme de partie de code dans un pipeline et le déploiement d'application dans un autre.

La chaîne d'outils est composée de cinq étapes. 

1. L'étape de génération clone le référentiel GIT et place le code dans un package Debian.
2. L'étape de planification Terraform prépare un plan Terraform.

  ```
  terraform init -input=false
  terraform validate
  terraform plan -var "ssh_public_key=$PUBLIC_KEY" -input=false -out tfplan
  ```

3. L'étape d'application Terraform applique la configuration Terraform et attend que l'adresse IP du serveur virtuel soit disponible.

  ```
  terraform apply -auto-approve -input=false tfplan
  terraform output "host ip" > hostip.txt
  ```

4. L'étape de déploiement, d'installation et de démarrage déplace le package Debian généré lors de la première étape dans le serveur virtuel en cours d'exécution, l'installe puis le démarre.
5. L'étape de diagnostic d'intégrité valide le noeud final d'intégrité disponible dans l'application puis finalise le pipeline.

Pour accéder à l'application après son démarrage, consultez les journaux de l'étape de diagnostic d'intégrité. Cliquez sur les liens d'URL répertoriées dans les journaux qui incluent l'adresse IP et le port de l'application.
