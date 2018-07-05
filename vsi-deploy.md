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

# Deploying to a virtual server
{: #vsi-deploy}

Deploy {{site.data.keyword.cloud}} [App Service ![External link icon](../icons/launch-glyph.svg)](https://console.bluemix.net/developer/appservice/starter-kits){: new_window} apps into virtual server instances to enable your platform and infrastructure developer activities to work together and increase app control and flexibility.
{: shortdesc}

A virtual server instance offers better transparency, predictability, and automation for all workload types when compared to other configurations. Combine it with a bare metal server to create unique workload combinations. For example, you can create high-performance database logic or machine learning with bare metal and GPU configurations that run a Debian Linux-based operating system.

## Before you begin
To use virtual instances, your {{site.data.keyword.cloud_notm}} account must be enabled for infrastructure. For more information, see [Upgrade to Infrastructure ![External link icon](../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/dashboard/ibm-iaas-g1){: new_window}.

**Important**: Services don't bind to the virtual server instance. You cannot add services to an application in a virtual server.

## Deploying through Terraform
Any of the App Service starter kits can be deployed in a dynamically created virtual instance through [Terraform ![External link icon](../icons/launch-glyph.svg)](https://ibm-cloud.github.io/tf-ibm-docs/v0.10.0/){: new_window}, an open source infrastructure as code framework. For more information, see [Terraform Documentation ![External link icon](../icons/launch-glyph.svg)](https://www.terraform.io/docs/index.html){: new_window}.

## Enabling your pipeline deployment

When you create a starter kit that uses the {{site.data.keyword.cloud_notm}} [App Service ![External link icon](../icons/launch-glyph.svg)](https://console.bluemix.net/developer/appservice/starter-kits){: new_window}, the virtual server instance is enabled. After the app is created, you can then choose where you want to deploy the app. The starter kits are enabled to support deployment by using a Continuous Delivery toolchain. Starter kits can target Kubernetes, Cloud Foundry, and Virtual Server Instances. The toolchain includes a source code repository and a deployment pipeline.

The virtual server option works in phases. First, the app code is prepared and stored into a GITLab Git repository and the source code creates a toolchain with a pipeline. The pipeline is defined to build the code and package it into a Debian Package manager format. Then, Terraform provisions a virtual instance. Finally, the app is deployed, installed, and started inside the running virtual image and its health is validated.

The pipeline fails on first use because it requires a set of user account properties to be manually configured. These properties can't be passed into the toolchain that uses GIT source code for security reasons. You must manually configure these values to enable the toolchain to complete successfully.

To access the environment properties view and enable your pipeline with your user account properties, follow these steps.

1. From the app details page, click **View Toolchain**.
2. Click the **Delivery Pipeline** tile.
3. Click the **Stage Configure** icon, then click **Configure Stage** on the build stage.
4. Click **Environment Properties** tab to view the properties.
5. Change these properties in the environment properties tab to enable the toolchain to run successfully.

| Property   | Description   |
|---|---|
| `TF_VAR_ibm_sl_api_key` | The [infrastructure API key](#iaas-key) is from the infrastructure console. |
| `TF_VAR_ibm_sl_username` | The [infrastructure user name](#user-key) that identifies the infrastructure account |
| `TF_VAR_ibm_cloud_api_key` | The {{site.data.keyword.cloud_notm}} [platform API key](#platform-key) is used to enable service creation. |
| `PUBLIC_KEY` | [Public key](#public-key) that is defined to enable access to the virtual server instance. |
| `PRIVATE_KEY` | [Private key](#public-key) that is defined to enable access to the virtual server instance. **Note**: You must use `\n` newline style formatting. |
| `VI_INSTANCE_NAME` | Auto-generated name for the virtual server instance |
| `GIT_USER` | If you set the [Terraform state](#tform-state) to store the state of the apply command, the GITLab user name is required. |
| `GIT_PASSWORD` | If you set the [Terraform state](#tform-state) to store the state of the apply command, the GITLab password is required. |
{: caption="Table 1. Environment Variables to change for enablement" caption-side="top"}

### Retrieving the infrastructure API key
{: #iaas-key}

Terraform requires an infrastructure API key to create infrastructure resources. Follow these steps to retrieve an infrastructure key.

1. Go to the infrastructure [user list ![External link icon](../icons/launch-glyph.svg)](https://control.bluemix.net/account/users){: new_window}. You can also click **Menu** > **Infrastructure** > **Account** > **User List**.
2. Find the user details that are creating the toolchain and either click `View` in the API Key column or click `Generate` both steps display the API key in a window.
3. Copy the API Key and replace the value in the Toolchain configuration `TF_VAR_ibm_sl_api_key`.

### Retrieving the infrastructure user name
{: #user-key}

To retrieve the infrastructure user name, follow these steps.

1. Go to the infrastructure [user list ![External link icon](../icons/launch-glyph.svg)](https://control.bluemix.net/account/users){: new_window}. You can also click **Menu** > **Infrastructure** > **Account** > **User List**.
2. Click the user who you want to create the toolchain.
3. Scroll down to the **VPN User Name** property.
4. Cut and paste this value and replace the Toolchain configuration `TF_VAR_ibm_sl_username`.

### Retrieving the platform API key
{: #platform-key}

To create platform level services in Terraform, like databases and compose services, the platform API key is required. Follow these steps to retrieve a platform key.

1. From the [API Keys ![External link icon](../icons/launch-glyph.svg)](https://console.bluemix.net/iam/#/apikeys) page, click **Manage** > **Security** > **Platform API Keys**.
2. Click **Create**.
3. Enter a name and description and click **Create**.
4. When the window opens, click **Show** to review the key.
5. Copy and paste the key into the clipboard or download the key.
6. Replace the value in the toolchain configuration `TF_VAR_ibm_cloud_api_key` with the value that was generated.

### Generating the public and private Key
{: #public-key}

For the toolchain to install the Debian packaging into the virtual server instance, follow these steps.

1. In your client, use the following instructions to create a [public and private key pair ![External link icon](../icons/launch-glyph.svg)](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/){: new_window}.
2. Go to the [Infrastructure SSH keys view ![External link icon](../icons/launch-glyph.svg)](https://control.bluemix.net/devices/sshkeys){: new_window}. You can also click **Menu** > **Infrastructure** > **Devices** > **Manage** > **SSH Keys**.
3. Click **Add**.
4. Copy the contents of the public key that you previously created and paste it into the key contents.
5. Give the key a name and click **Add**.

The private key must be on a single line. Replace new lines with `\n`. See the following example.
{: tip}

```
---------BEGIN RSA KEY----------\nasdfasdfeqwtqf13rf1eqwfwe\netq3efaewf23fa23f23f\n.....\n----------END RSA KEY-------------
```
{: screen}

### Enabling Terraform state
{: #tform-state}

Terraform supports storing the state of the Terraform `apply` command. This state file runs the `apply` command a second time to determine whether any of the Terraform configuration files changed. You can store the state in the GIT repo where the app and configuration are managed.

To enable the state storage, configure the `GIT_USER` and `GIT_PASSWORD` properties in the toolchain environment variables. To retrieve the values, follow these steps:

1. From the toolchains view, access the GIT repo from the code tool.
2. In GIT Lab, click the **Profile icon** and then click **Settings**.
3. Click **Account** and copy the user name and replace the `GIT_USER` value.
4. Click **Access Tokens**.
5. Define a name for your token, select a scope, and click **Create Personal Access Token**.
6. Click the copy icon from the `Your New Personal Access Token` field, and replace the value of the `GIT_PASSWORD` in the toolchain properties.

The Terraform state is stored in a branch that is called `terraform`, and doesn't trigger the pipeline to run if it was changed.

### Enabling GIT operations
{: #git-repo}

When the app is deployed to {{site.data.keyword.cloud_notm}}, a GIT Lab repository is created to host the code for source code management. You can use GIT operations to enable teams to work and deliver changes to your app. The folders included in this repository and an explanation of their contents.

#### Debian folder
{: #debian-folder}

The `debian` folder holds the configuration that is required to enable the packaging of the app into a [Debian package. ![External link icon](../icons/launch-glyph.svg)](https://www.debian.org/doc/manuals/debian-faq/ch-pkgtools.en.html){: new_window}

#### Terraform folder
{: #terraform-folder}

The `terraform` folder holds the configuration for the infrastructure as code that can be used to provision infrastructure resources. The file `main.tf` is the main source for changing the options for your Terraform configuration.

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

You can also provision bare metal servers with Terraform. For more information, see [IBM Terraform Provider Documentation ![External link icon](../icons/launch-glyph.svg)](https://ibm-cloud.github.io/tf-ibm-docs/v0.10.0/){: new_window} and [IBM Terraform Provider GIT Repo ![External link icon](../icons/launch-glyph.svg)](https://github.com/IBM-Cloud/terraform-provider-ibm){: new_window}.

The `variables.tf` can be used to change the data center you want to target to create the virtual instance. To see the list of defined data centers on the platform, see [Data Centers ![External link icon](../icons/launch-glyph.svg)](https://www.ibm.com/cloud-computing/bluemix/data-centers){: new_window}.

By default, the Terraform file is configured for Washington and `wdc04`.

```
variable "datacenter" {
  description = "Washington"
  default = "wdc04"
}
```

### Understanding the toolchain stages
{: #toolchain-stages}

The toolchain shows infrastructure and app deployment in one simple pipeline. Break the infrastructure as code part into one pipeline and the app deployment into another pipeline.

The toolchain process has five stages.

1. The build stage clones the GIT repo and packages the code into a Debian package.
2. The Terraform plan stage prepares a Terraform plan.

  ```
  terraform init -input=false
  terraform validate
  terraform plan -var "ssh_public_key=$PUBLIC_KEY" -input=false -out tfplan
  ```

3. The Terraform apply stage applies the Terraform configuration and waits until the IP address of the virtual server is available.

  ```
  terraform apply -auto-approve -input=false tfplan
  terraform output "host ip" > hostip.txt
  ```

4. The deploy, install, start stage moves the Debian package that is built in the first stage into the running virtual server, installs it and then starts it.
5. The health check stage validates the health endpoint is available on the app and then completes the pipeline.

To access the app after it starts, check the logs of the Health Check Stage. Click the URL links listed in the logs that show the IP address and port of the app.
