---

copyright:
   years: 2020, 2023
lastupdated: "2023-03-09"

keywords: apps, scalable web apps, web apps, liberty apps, java liberty, tutorial, java liberty tutorial, liberty tutorial, java tutorial, schematics tutorial, terraform tutorial, schematics workspace, kubernetes cluster, openshift cluster, deploy to ibm cloud, cluster deployment, devops toolchain, delivery pipeline, reference architecture, gitsecure, terraform, schematics, tekton ci-pipeline, pipelinerun, pipeline run, terraform

subcollection: apps
content-type: tutorial
services: schematics, terraform, openshift, containers, ContinuousDelivery, apps
account-plan: paid
deployable: quickstart
completion-time: 45m

---

{{site.data.keyword.attribute-definition-list}}

# Deploy a Java Liberty app by using {{site.data.keyword.bplong_notm}}
{: #tutorial-liberty-webapp}
{: toc-content-type="tutorial"}
{: toc-services="schematics, terraform, openshift, containers, ContinuousDelivery, apps"}
{: toc-completion-time="45m"}

In this tutorial, you learn how to create and deploy a scalable Java Liberty application. This scalable web app offers a one-click option to create an {{site.data.keyword.bplong}} workspace with your choice of preconfigured Terraform templates. The Terraform templates deploy your app to {{site.data.keyword.cloud_notm}} with options for the deployment target (Kubernetes or Red Hat&reg; OpenShift&reg;) and the DevOps toolchain pipeline structure.
{: shortdesc}

{{site.data.keyword.bplong_notm}} delivers Terraform-as-a-Service so that you can use a high-level scripting language to model the resources that you want in your {{site.data.keyword.cloud_notm}} environment, and enable Infrastructure as Code (IaC). [Terraform](https://www.terraform.io/){: external} is an open source software that is developed by HashiCorp that enables predictable and consistent resource provisioning to rapidly build complex, multitier cloud environments.

In this tutorial, you follow two easy steps to create a {{site.data.keyword.bpshort}} workspace and apply a Terraform execution plan. When you apply the plan, a Kubernetes or OpenShift cluster is created, and a Java Liberty application is deployed to it by using an {{site.data.keyword.cloud_notm}} DevOps toolchain.

Two types of DevOps toolchain pipeline structures are available with this app:
* Classic pipeline structure
* Tekton "GitSecure" pipeline structure

Both toolchain template options offer a code repository, delivery pipelines, and web IDE.

## Before you begin
{: #liberty-prereqs}

* Set up an [{{site.data.keyword.cloud_notm}} account](/registration){: external}. Depending on your {{site.data.keyword.cloud_notm}} account type, access to certain resources might be limited. Depending on your account plan limits, certain capabilities that are required by some DevOps toolchains might not be available. For more information, see [Setting up your {{site.data.keyword.cloud_notm}} account](/docs/account?topic=account-account-getting-started) and [Upgrading your account](/docs/account?topic=account-upgrading-account).

## Create a {{site.data.keyword.bpshort}} workspace
{: #liberty-schematics-workspace}
{: step}

1. Click one of the following options for the cluster deployment target and toolchain pipeline type. This action takes you to the Deploy to {{site.data.keyword.cloud_notm}} page where you create a {{site.data.keyword.bpshort}} workspace. Complete the required fields on that page, and then click **Next**.

   The following options use the [simple-helm-toolchain template](https://github.com/open-toolchain/simple-helm-toolchain){: external}, which uses a Classic pipeline structure.

   [![Deploy to Kubernetes on {{site.data.keyword.cloud_notm}}](../images/Deploy_to_kube.svg "Deploy to Kubernetes on {{site.data.keyword.cloud_notm}}")](https://cloud.ibm.com/schematics/workspaces/create?repository=https://github.com/IBM-Cloud/Scalable-web-app-liberty/tree/master/terraform/simple-kube&terraform_version=terraform_v1.3)
   [![Deploy to OpenShift on {{site.data.keyword.cloud_notm}}](../images/Deploy_to_Openshift.svg "Deploy to OpenShift on {{site.data.keyword.cloud_notm}}")](https://cloud.ibm.com/schematics/workspaces/create?repository=https://github.com/IBM-Cloud/Scalable-web-app-liberty/tree/master/terraform/simple-openshift&terraform_version=terraform_v1.3)

   The following options use the [secure-kube-toolchain template](https://github.com/open-toolchain/secure-kube-toolchain){: external}, which uses a Tekton pipeline structure.

   [![Deploy to Kubernetes on {{site.data.keyword.cloud_notm}} (secured)](../images/Deploy_to_kube_Secured.svg "Deploy to Kubernetes on {{site.data.keyword.cloud_notm}}")](https://cloud.ibm.com/schematics/workspaces/create?repository=https://github.com/IBM-Cloud/Scalable-web-app-liberty/tree/master/terraform/secure-kube&terraform_version=terraform_v1.3)
   [![Deploy to OpenShift on {{site.data.keyword.cloud_notm}} (secured)](../images/Deploy_to_Openshift_Secured.svg "Deploy to OpenShift on {{site.data.keyword.cloud_notm}}")](https://cloud.ibm.com/schematics/workspaces/create?repository=https://github.com/IBM-Cloud/Scalable-web-app-liberty/tree/master/terraform/secure-openshift&terraform_version=terraform_v1.3)

   Based on which option you select, the corresponding Terraform template from this repository is automatically imported into the new {{site.data.keyword.bpshort}} workspace. The Terraform engine version is v1.3.
   {: note}

1. Verify the information, and then click **Create**. The {{site.data.keyword.bpshort}} workspace is created, and the Settings page for the {{site.data.keyword.bpshort}} workspace is displayed.

## Apply the Terraform execution plan
{: #liberty-apply-plan}
{: step}

1. In the **Variables** section of the {{site.data.keyword.bpshort}} Settings page, enter the values for each variable. Required fields are the fields without default values. However, default values can be overridden.
1. Optional. Click **Generate plan**. This action creates a Terraform execution plan and checks your configuration for syntax errors. On the {{site.data.keyword.bpshort}} Activity page, you can review log files for errors and {{site.data.keyword.cloud_notm}} resources that must be created, modified, or deleted to achieve the state of the Terraform template.
1. After you enter all the values for the variables and are satisfied with the changes, click **Apply plan**. This step takes some time to complete (usually 20 - 30 minutes, but it can take longer), due to the creation of a new Kubernetes or OpenShift cluster.
1. Follow the progress of this step by clicking the **View log** link next to the corresponding step.
1. After the plan is successfully applied, view the URL to the generated {{site.data.keyword.cloud_notm}} DevOps toolchain. The URL is located near the end of the log file on a line that begins with `View the toolchain at:`.
1. Copy and paste the URL into a browser search bar to view the newly created toolchain.
1. On the toolchain's Overview page, click **ci-pipeline** in the **Delivery pipelines** card.
1. Check the status of your application by choosing one of the following options, depending on whether you ran a Classic or a Tekton pipeline:
   1. Classic pipelines: On the Delivery Pipeline page, check the status of the Deploy stage.
      - If the status is **Stage Passed**, click the "Passed" link that is next to the deploy job to open the log file. In the log file, locate the string `VIEW THE APPLICATION AT:`, and then click the URL.
      - If the status is **Stage Failed**, click the Play icon ![Play icon](../../icons/play.svg) to run the stage again.
   1. Tekton pipelines: On the ci-pipeline Dashboard page, check the Status column in the table.
      - If the status is **Succeeded**, click the name of the pipeline run, and then click the **execute** step in the **deploy-to-kubernetes** task. The task deploys the app into the Kubernetes cluster. In the log file, locate the string `VIEW THE APPLICATION AT:`, and then click the URL.
      - If the status is **Failed**, click the Action menu ![Action menu](../../icons/action-menu-icon.svg) for the pipeline run, and select **Rerun**. Alternatively, click **Run pipeline**, and then click **Rerun** on the Run Pipeline page.

If you apply your plan a second time, the previously created Kubernetes or OpenShift cluster and any applications that are deployed to it are deleted, and a new cluster is created.
{: note}

## Related information
{: #liberty-related}

- [Getting started with {{site.data.keyword.bplong_notm}}](/docs/schematics?topic=schematics-getting-started)
- [Using Terraform to configure Schematics](/docs/schematics?topic=schematics-terraform-setup)
- [Use the "Develop a Kubernetes app" toolchain with Tekton pipelines](https://www.ibm.com/cloud/architecture/tutorials/use-develop-kubernetes-app-toolchain-with-tekton-pipelines){: external}
- [Classic pipeline overview](/docs/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_about)
- [Working with Tekton pipelines](/docs/ContinuousDelivery?topic=ContinuousDelivery-tekton-pipelines)
