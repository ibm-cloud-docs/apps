---

copyright:
  years: 2018
lastupdated: "2018-11-29"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:table: .aria-labeledby="caption"}

# Déploiement sur un serveur virtuel
{: #vsi-deploy}

Si vous avez un compte Paiement à la carte, vous pouvez utiliser {{site.data.keyword.cloud}} [App Service ![Icône de lien externe](../icons/launch-glyph.svg)](https://{DomainName}/developer/appservice/starter-kits){: new_window} pour déployer vos applications dans un grand nombre d'environnements, notamment des instances de serveur virtuel. Une instance de serveur virtuel émule une machine bare metal et est une option de déploiement couramment choisie lors du déplacement de charges de travail locales vers le cloud.
{: shortdesc}

Par rapport aux autres configurations, une instance de serveur virtuel offre une meilleure transparence, un meilleur caractère prévisionnel et une meilleure automatisation pour tous les types de charge de travail. Associez-la à un serveur Bare metal pour créer des combinaisons de charge de travail uniques. Par exemple, vous pouvez créer une logique de base de données à hautes performances ou un système d'apprentissage automatique avec des configurations Bare metal ou GPU exécutant un système d'exploitation de type Debian Linux.

La mise à disposition et le déploiement d'une instance de serveur virtuel peut être un processus long et complexe, mais vous pouvez être rapidement opérationnel si vous utilisez le service d'application {{site.data.keyword.cloud_notm}}.

Les services ne sont pas liés à l'instance de serveur virtuel. Vous ne pouvez pas ajouter de services dans un serveur virtuel.
{: important}

## Création et déploiement d'applications
{: #create-deploy}

Le service d'application met à disposition une instance de serveur virtuel, charge une image qui inclut votre application, crée une chaîne d'outils Devops et initie le premier cycle de déploiement pour vous.

1. [Créez une application](index.html#createapp). 
2. Cliquez sur **Déployer dans le cloud** sur la page des détails de l'application.
3. Sélectionnez **Déployer sur un serveur virtuel** en même temps que la région dans laquelle votre serveur doit s'exécuter.

## Fonctionnement du processus de déploiement

Le processus de déploiement de serveur virtuel est composé de plusieurs technologies essentielles, notamment Terraform, l'activation de pipeline, la gestion de clés d'API (opérations Git) et la compréhension du processus de chaîne d'outils. 

### Déploiement via Terraform

Les kits de démarrage de service d'application peuvent être déployés dans une instance virtuelle créée dynamiquement via [Terraform ![Icône de lien externe](../icons/launch-glyph.svg)](https://ibm-cloud.github.io/tf-ibm-docs/v0.10.0/){: new_window}, infrastructure open source utilisée comme infrastructure de code. 

### Activation de votre déploiement de pipeline

Lorsque vous créez un kit de démarrage qui utilise {{site.data.keyword.cloud_notm}} [App Service ![Icône de lien externe](../icons/launch-glyph.svg)](https://{DomainName}/developer/appservice/starter-kits){: new_window}, l'instance de serveur virtuel est activée. Une fois l'application créée, vous pouvez alors choisir l'emplacement de déploiement de l'application. Les kits de démarrage permettent de prendre en charge le déploiement en utilisant une chaîne d'outils Continuous Delivery. Les kits de démarrage peuvent cibler les instances Kubernetes, Cloud Foundry et de serveur virtuel. La chaîne d'outils inclut un référentiel de code source et un pipeline de déploiement.

L'option de serveur virtuel inclut plusieurs phases. Tout d'abord, le code d'application est préparé et stocké dans un référentiel Git GitLab et le code source crée une chaîne d'outils avec un pipeline. Ce dernier est conçu pour générer le code et regrouper ce dernier en utilisant le format du gestionnaire de package Debian. Terraform met ensuite à disposition une instance virtuelle. Pour finir, l'application est déployée, installée et démarrée dans l'image virtuelle en cours d'exécution et son intégrité est validée.

Le pipeline utilise un ensemble de propriétés de compte utilisateur et une nouvelle paire de clés SSH à déployer dans l'infrastructure. Ces propriétés sont automatiquement transmises à la chaîne d'outils, mais ne sont pas stockées dans le code source Git pour des raisons de sécurité.

Pour afficher ces propriétés d'environnement, procédez comme suit : 

1. Sur la page Détails de l'application, cliquez sur **Afficher la chaîne d'outils**.
2. Cliquez sur la vignette **Delivery Pipeline**.
3. Cliquez sur l'icône **Configurer l'étape** puis cliquez sur **Configurer l'étape** lors de l'étape de génération.
4. Cliquez sur l'onglet **Propriétés d'environnement** pour afficher les propriétés. Consultez le tableau suivant pour connaître les propriétés disponibles.

| Propriété  | Description  |
|-----------|--------------|
| `TF_VAR_ibm_sl_api_key` | La [clé d'API de l'infrastructure](#iaas-key) provient de la console d'infrastructure classique. |
| `TF_VAR_ibm_sl_username` | [Nom d'utilisateur de l'infrastructure](#user-key) identifiant le compte d'infrastructure classique. |
| `TF_VAR_ibm_cloud_api_key` | La [clé d'API de plateforme](#platform-key) {{site.data.keyword.cloud_notm}} permet d'activer la création de service. |
| `PUBLIC_KEY` | [Clé publique](#public-key) définie pour activer l'accès à l'instance de serveur virtuel. |
| `PRIVATE_KEY` | [Clé privée](#public-key) définie pour activer l'accès à l'instance de serveur virtuel. Vous devez utiliser le formatage de style de nouvelle ligne `\n`. |
| `VI_INSTANCE_NAME` | Nom généré automatiquement pour l'instance de serveur virtuel |
| `GIT_USER` | Si vous définissez l'[état Terraform](#tform-state) afin de stocker l'état de la commande apply, le nom d'utilisateur GitLab est requis. |
| `GIT_PASSWORD` | Si vous définissez l'[état Terraform](#tform-state) afin de stocker l'état de la commande apply, le mot de passe GitLab est requis. |
{: caption="Tableau 1. Variables d'environnement à changer pour l'activation" caption-side="top"}


#### Clé d'API de l'infrastructure
{: #iaas-key}
<!-- This section is incomplete. The UI doesn't have a button named classic instructure API key. -->
Pour pouvoir créer des ressources d'infrastructure, Terraform doit avoir une clé d'API d'infrastructure. La clé d'API est obtenue automatiquement lors du déploiement. Pour extraire manuellement une clé, procédez comme indiqué ci-après.

1. Accédez à la [liste d'utilisateurs ![Icône de lien externe](../icons/launch-glyph.svg)](https://{DomainName}/iam#/users){: new_window}. Vous pouvez également cliquer sur **Gérer** > **Accès (IAM)** et sélectionner **Utilisateurs**.
2. Cliquez sur un nom d'utilisateur puis sur **Détails de l'utilisateur**.
3. Cliquez sur **Ajouter une clé d’infrastructure classique** dans la section Clés d'API.
4. Copiez ou téléchargez la clé d'API `TF_VAR_ibm_sl_api_key` et sauvegardez-la à un emplacement sûr. Vous pouvez extraire ultérieurement les détails de la clé d'API en utilisant l'option **Afficher les détails** dans le menu **Actions** ![Icône Liste des actions](../icons/action-menu-icon.svg).
5. Collez la valeur de la clé d'API copiée dans la configuration de chaîne d'outils pour remplacer l'élément `TF_VAR_ibm_sl_api_key`.

Pour plus d'informations, voir [Gestion des clés d'API d'infrastructure classique](/docs/iam/classic_infra_keys.html) et [Droits d'infrastructure classique](/docs/iam/infrastructureaccess.html).

#### Nom d'utilisateur de l'infrastructure
{: #user-key}
<!-- This section is incomplete. The UI doesn't have a VPN User Name property. -->
Le nom d'utilisateur de l'infrastructure est également obtenu et utilisé automatiquement lors du déploiement. Pour obtenir manuellement le nom d'utilisateur, procédez comme indiqué ci-après.

1. Accédez à la [liste d'utilisateurs ![Icône de lien externe](../icons/launch-glyph.svg)](https://{DomainName}/iam#/users){: new_window}. Vous pouvez également cliquer sur **Gérer** > **Accès (IAM)** et sélectionner **Utilisateurs**.
2. Cliquez sur un nom d'utilisateur puis sur **Détails de l'utilisateur**.
3. Recherchez la propriété **Nom d'utilisateur VPN**.
4. Coupez et collez cette valeur et remplacez la configuration de chaîne d'outils `TF_VAR_ibm_sl_username`.

#### Clé d'API IBM Cloud
{: #platform-key}

Pour créer des services de niveau de plateforme dans Terraform (bases de données et services Compose, par exemple), la clé d'API de plateforme est automatiquement obtenue et stockée sous forme de variable d'environnement dans votre pipeline. Pour extraire manuellement une clé de plateforme, procédez comme indiqué ci-après.

1. Accédez à la [liste d'utilisateurs ![Icône de lien externe](../icons/launch-glyph.svg)](https://{DomainName}/iam#/users){: new_window}. Vous pouvez également cliquer sur **Gérer** > **Accès (IAM)** et sélectionner **Utilisateurs**.
2. Cliquez sur un nom d'utilisateur puis sur **Détails de l'utilisateur**.
3. Recherchez la section Clés d'API puis cliquez sur **Créer une clé d'API IBM Cloud**.
4. Entrez un nom et une description puis cliquez sur **Créer**.
5. Lorsque la fenêtre s'affiche, cliquez sur **Afficher** pour consulter la clé.
6. Copiez et collez la clé dans le presse-papiers ou téléchargez la clé.
7. Remplacez la valeur de la configuration de la chaîne d'outils `TF_VAR_ibm_cloud_api_key` par la valeur générée.

#### Clés publiques et privées
{: #public-key}
<!-- Cannot verify these steps until we get an infrastructure account. Step 2 is showing the incorrect UI steps, but we cannot see the correct UI. -->
Pour que la chaîne d'outils puisse installer le package Debian dans l'instance de serveur virtuel, l'infrastructure de déploiement génère automatiquement une paie de clés SSH privée et publique afin de transférer le contenu Git vers l'instance.

Pour exécuter cette opération manuellement :
1. Sur votre client, suivez les instructions présentées ci-dessous pour créer une [paire clé publique/clé privée ![Icône de lien externe](../icons/launch-glyph.svg)](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/){: new_window}.
2. Accédez à la [vue des clés SSH de l'infrastructure ![Icône de lien externe](../icons/launch-glyph.svg)](https://{DomainName}/devices/sshkeys){: new_window}. Vous pouvez également cliquer sur **Menu** > **Infrastructure classique** > **Périphériques** > **Gérer** > **Clés SSH**.
3. Cliquez sur **Ajouter**.
4. Copiez le contenu de la clé publique précédemment créée et collez-le dans le contenu de la clé.
5. Donnez un nom à la clé puis cliquez sur **Ajouter**.

La clé privée doit se trouver sur une seule ligne. Remplacez les nouvelles lignes par `\n`. Voir l'exemple suivant.
{: tip}

```
---------BEGIN RSA KEY----------\nasdfasdfeqwtqf13rf1eqwfwe\netq3efaewf23fa23f23f\n.....\n----------END RSA KEY-------------
```
{: screen}

#### Activation de l'état Terraform
{: #tform-state}

Terraform prend en charge le stockage de l'état de la commande `apply` Terraform. Ce fichier d'état exécute une deuxième fois la commande `apply` afin de déterminer si un des fichiers de configuration Terraform a été modifié. L'état est stocké dans le référentiel Git où l'application et la configuration sont automatiquement définies.

Pour permettre le stockage d'état, `GIT_USER` et `GIT_PASSWORD` sont automatiquement configurés en tant que propriétés dans les variables d'environnement de la chaîne d'outils. Si vous devez accéder à ces valeurs, procédez comme suit :

1. Dans la vue Chaînes d'outils, accédez au référentiel Git à partir de l'outil de code.
2. Dans GIT Lab, cliquez sur l'icône **Profil** puis sur **Paramètres**.
3. Cliquez sur **Compte**, copiez le nom d'utilisateur puis remplacez la valeur `GIT_USER`.
4. Cliquez sur **Jetons d'accès**.
5. Définissez un nom pour votre jeton, sélectionnez une portée puis cliquez sur **Créer un jeton d'accès personnel**.
6. Cliquez sur **Copier** dans la zone `Votre nouveau jeton d’accès personnel` et remplacez la valeur de l'élément `GIT_PASSWORD` dans les propriétés de la chaîne d'outils.

L'état Terraform est stocké dans une branche appelée `terraform` et ne déclenche pas l'exécution du pipeline en cas de modification.

### Activation des opérations Git
{: #git-repo}

Lorsque l'application est déployée dans {{site.data.keyword.cloud_notm}}, un référentiel GitLab est créé en vue d'héberger le code pour la gestion du code source. Vous pouvez utiliser les opérations Git pour permettre à vos équipes de travailler et de modifier votre application. Vous pouvez consulter les dossiers inclus dans ce référentiel ainsi qu'une description de leur contenu.

#### Dossier Debian
{: #debian-folder}

Le dossier `debian` inclut la configuration requise pour pouvoir placer l'application dans un [package Debian. ![Icône de lien externe](../icons/launch-glyph.svg)](https://www.debian.org/doc/manuals/debian-faq/ch-pkgtools.en.html){: new_window}

#### Dossier Terraform
{: #terraform-folder}

Le dossier `terraform` inclut la configuration de l'infrastructure, sous forme de code pouvant être utilisé pour mettre à disposition des ressources d'infrastructure. Le fichier `main.tf` constitue la principale source pour la modification des options de votre configuration Terraform.

```json
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
```json
variable "datacenter" {
  description = "Washington"
  default = "wdc04"
}
```

### Présentation des étapes de la chaîne d'outils
{: #toolchain-stages}

La chaîne d'outils affiche l'infrastructure et le déploiement d'application dans un pipeline simple. Placez l'infrastructure sous forme de partie de code dans un pipeline et le déploiement d'application dans un autre.

La chaîne d'outils est composée de cinq étapes.

1. L'étape de génération clone le référentiel Git et place le code dans un package Debian.
2. L'étape de planification Terraform prépare un plan Terraform.
  ```console
  terraform init -input=false
  terraform validate
  terraform plan -var "ssh_public_key=$PUBLIC_KEY" -input=false -out tfplan
  ```

3. L'étape d'application Terraform applique la configuration Terraform et attend que l'adresse IP du serveur virtuel soit disponible.

  ```console
  terraform apply -auto-approve -input=false tfplan
  terraform output "host ip" > hostip.txt
  ```

4. L'étape de déploiement, d'installation et de démarrage déplace le package Debian généré lors de la première étape dans le serveur virtuel en cours d'exécution, l'installe puis le démarre.
5. L'étape de diagnostic d'intégrité valide le noeud final d'intégrité disponible dans l'application puis finalise le pipeline.

Pour accéder à l'application après son démarrage, consultez les journaux de l'étape de diagnostic d'intégrité. Cliquez sur les liens d'URL répertoriées dans les journaux qui incluent l'adresse IP et le port de l'application.
