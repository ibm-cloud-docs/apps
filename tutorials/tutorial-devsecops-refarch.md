---

copyright:
   years: 2021
lastupdated: "2021-07-13"

keywords: tekton, pipeline, toolchain, CD, CI, Terraform, template, automate, automation, compliance, secure, compliant, shift-left, shift left, quick start, devsecops tutorial, devsecops

subcollection: apps

content-type: tutorial
services: schematics, terraform, openshift, containers, ContinuousDelivery, apps
account-plan: paid
completion-time: 1h

---

{:shortdesc: .shortdesc}
{:screen: .screen}  
{:codeblock: .codeblock}  
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:external: target="_blank" .external}
{:step: data-tutorial-type='step'}

# Set up your DevSecOps infrastructure and CI toolchain for deploying a secure app
{: #tutorial-apps-devsecops}
{: toc-content-type="tutorial"}
{: toc-services="schematics, terraform, openshift, containers, ContinuousDelivery, apps"}
{: toc-completion-time="1h"}

Use this tutorial for automated setup of the infrastructure for your CI and CD toolchains by using a Terraform-based quick start template. The template uses DevSecOps best practices of compliance and security. The template uses an [{{site.data.keyword.bplong}} workspace](/docs/schematics?topic=schematics-about-schematics), which automates the creation of the required infrastructure for securely deploying your app to either Kubernetes or Red Hat&reg; OpenShift&reg;. The template uses the DevSecOps {{site.data.keyword.contdelivery_full}} toolchain pipeline structure. The toolchain is preconfigured for continuous delivery with inventory integration, change management, evidence collection, and deployment.
{: shortdesc}

{{site.data.keyword.bplong_notm}} delivers Terraform-as-a-Service so that you can use a high-level scripting language to model the resources that you want in your {{site.data.keyword.cloud_notm}} environment, and enable Infrastructure as Code (IaC). [Terraform](https://www.terraform.io/){: external} is an open source software that is developed by HashiCorp that enables predictable and consistent resource provisioning to rapidly build complex, multitier cloud environments.

In this tutorial, you follow two easy steps to create a {{site.data.keyword.bpshort}} workspace and apply a Terraform execution plan. When you apply the plan, the {{site.data.keyword.bpshort}} workspace provides you with a setup of your secure infrastructure. This infrastructure is shareable with your team, and it works for the DevSecOps CI and CD toolchain templates.

The automated infrastructure setup includes the creation of the following resources:

  * A cluster in [{{site.data.keyword.containerlong}}](/docs/containers?topic=containers-clusters) or [Red Hat OpenShift on {{site.data.keyword.cloud_notm}}](/docs/openshift?topic=openshift-getting-started)
  * [{{site.data.keyword.cos_full_notm}} instance and bucket](/docs/cloud-object-storage?topic=cloud-object-storage-about-cloud-object-storage)
  * [{{site.data.keyword.secrets-manager_full}}](/docs/secrets-manager?topic=secrets-manager-getting-started)
  * [GPG image signing key](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd-devsecops-image-signing)
  * A fully functional [DevSecOps CI toolchain](/docs/ContinuousDelivery?topic=ContinuousDelivery-tutorial-cd-devsecops#devsecops-ci-toolchain-intro) that builds, tests, and deploys a sample Node.js application using DevSecOps best practices of compliance and security.

These resources are automatically provisioned for you by using the default values from the DevSecOps CI and CD templates. You can find the default values in the “Variables” section of the {{site.data.keyword.bpshort}} workspace.

## Before you begin
{: #apps-devsecops-prereqs}

* Set up an [{{site.data.keyword.cloud_notm}} account](https://{DomainName}/registration){: external}. Depending on your {{site.data.keyword.cloud_notm}} account type, access to certain resources might be limited. Depending on your account plan limits, certain capabilities that are required by some DevSecOps toolchains might not be available. For more information, see [Setting up your {{site.data.keyword.cloud_notm}} account](/docs/account?topic=account-account-getting-started) and [Upgrading your account](/docs/account?topic=account-upgrading-account).
* [Install the {{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-getting-started) if you want to interact with elements of the toolchain or infrastructure after they are created.
* Obtain a [GitLab Personal Access Token](https://us-south.git.cloud.ibm.com/-/profile/personal_access_tokens){: external}. Enter a name for your personal access token. Create your token in the same region as your CI toolchain. Be sure to copy and save the token because you need it later, and you cannot access it again.
* Create an [{{site.data.keyword.cloud_notm}} API key](https://cloud.ibm.com/iam/apikeys){: external}. Be sure to copy and save or download the API key value because you need it later, and you cannot access it again.

## Create a {{site.data.keyword.bpshort}} workspace
{: #devsecops-schematics-workspace}
{: step}

1. Click one of the following options for the cluster deployment target. This action takes you to the "Deploy to {{site.data.keyword.cloud_notm}}" page where you create a {{site.data.keyword.bpshort}} workspace. Complete the required fields on that page, and then click **Create**. The {{site.data.keyword.bpshort}} workspace is created, and the Settings page is displayed.

  [![Deploy to Kubernetes on {{site.data.keyword.cloud_notm}}](../images/Deploy_to_kube_Secured.svg "Deploy to Kubernetes on {{site.data.keyword.cloud_notm}}")](https://cloud.ibm.com/schematics/workspaces/create?repository=https://github.com/IBM-Cloud/shift-left-compliance-module/tree/master/terraform/secure-kube){: external}
  [![Deploy to OpenShift on {{site.data.keyword.cloud_notm}}](../images/Deploy_to_Openshift_Secured.svg "Deploy to OpenShift on {{site.data.keyword.cloud_notm}}")](https://cloud.ibm.com/schematics/workspaces/create?repository=https://github.com/IBM-Cloud/shift-left-compliance-module/tree/master/terraform/secure-openshift){: external}

  Based on which option you select, the corresponding Terraform template from this repository is automatically imported into the new {{site.data.keyword.bpshort}} workspace.
  {: note}

## Apply the Terraform execution plan
{: #devsecops-apply-plan}
{: step}

1. In the **Variables** section of the {{site.data.keyword.bpshort}} Settings page, enter the values for each variable. Required fields are the fields without default values. You can override default values.

   If you override any of the following values, the corresponding resource is not created: `cluster_name`, `cos_instance_name`, `cos_bucket_name`, or `sm_service_name`.
   {: important}

1. For the `gitlab_token` variable, enter the personal access token that you obtained previously.
1. Optional. Click **Generate plan**. This action creates a Terraform execution plan and checks your configuration for syntax errors. On the {{site.data.keyword.bpshort}} Activity page, you can review log files for errors and {{site.data.keyword.cloud_notm}} resources that must be created, modified, or deleted to achieve the state of the Terraform template.
1. After you enter all the values for the variables and are satisfied with the changes, click **Apply plan**. 
   This step takes some time to complete (usually 20 - 30 minutes, but it can take longer), due to the creation of a new Kubernetes or OpenShift cluster.
   {: note}
1. Follow the progress of this step by clicking the **View log** link next to the corresponding step.
1. After the plan is applied, view the URL to the generated {{site.data.keyword.cloud_notm}} DevSecOps CI toolchain. The URL is located near the end of the log file on a line that begins with "View the toolchain at:."

If you apply your plan a second time, the previously created Kubernetes or OpenShift cluster and any applications that are deployed to it are deleted, and a new cluster is created.
{: note}

For more information about this workflow, see [Getting started with {{site.data.keyword.bplong_notm}} and Terraform](/docs/schematics?topic=schematics-getting-started).

## Next steps
{: #devsecops-next-steps}

You can now [Explore your CI toolchain](/docs/apps?topic=ContinuousDelivery-tutorial-cd-devsecops#devsecops-ci-toolchain-explore) and run the CI-PR and CI pipelines. Then continue through the remainder of the steps to continue the process of deploying a secure app by using DevSecOps best practices.
