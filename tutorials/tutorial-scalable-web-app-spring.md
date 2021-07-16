---

copyright:
   years: 2020, 2021
lastupdated: "2021-07-06"

keywords: apps, scalable web apps, web apps, spring apps, java spring, tutorial, java spring tutorial, spring tutorial, java tutorial, schematics tutorial, terraform tutorial, schematics workspace, kubernetes cluster, openshift cluster, deploy to ibm cloud, cluster deployment, devops toolchain, delivery pipeline, reference architecture, gitsecure, terraform, schematics

subcollection: apps

content-type: tutorial
services: schematics, terraform, openshift, containers
account-plan: paid
completion-time: 45m

---

{:shortdesc: .shortdesc}
{:screen: .screen}  
{:codeblock: .codeblock}  
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:external: target="_blank" .external}
{:step: data-tutorial-type='step'}

# Deploy a Java Spring app by using {{site.data.keyword.bplong_notm}}
{: #tutorial-spring-webapp}
{: toc-content-type="tutorial"}
{: toc-completion-time="45m"}

In this tutorial, you learn how to create and deploy a scalable Java Spring application. This scalable web app offers a one-click option to create an {{site.data.keyword.bplong}} workspace with your choice of preconfigured Terraform templates. The Terraform templates deploy your app to {{site.data.keyword.cloud_notm}} with options for the deployment target (Kubernetes or Red Hat&reg; OpenShift&reg;) and the DevOps toolchain pipeline structure.
{: shortdesc}

{{site.data.keyword.bplong_notm}} delivers Terraform-as-a-Service so that you can use a high-level scripting language to model the resources that you want in your {{site.data.keyword.cloud_notm}} environment, and enable Infrastructure as Code (IaC). [Terraform](https://www.terraform.io/){: external} is an open source software that is developed by HashiCorp that enables predictable and consistent resource provisioning to rapidly build complex, multitier cloud environments.

In this tutorial, you follow two easy steps to create a {{site.data.keyword.bpshort}} workspace and apply a Terraform execution plan. When you apply the plan, a Kubernetes or OpenShift cluster is created, and a Java Spring application is deployed to it by using an {{site.data.keyword.cloud_notm}} DevOps toolchain.

Two types of DevOps toolchain pipeline structures are available with this app:
* Classic pipeline structure
* GitSecure pipeline structure

Both toolchain template options offer a code repository, delivery pipelines, and web IDE.

## Before you begin
{: #spring-prereqs}

* Set up an [{{site.data.keyword.cloud_notm}} account](https://{DomainName}/registration). Depending on your {{site.data.keyword.cloud_notm}} account type, access to certain resources might be limited. Depending on your account plan limits, certain capabilities that are required by some DevOps toolchains might not be available. For more information, see [Setting up your {{site.data.keyword.cloud_notm}} account](/docs/account?topic=account-account-getting-started) and [Upgrading your account](/docs/account?topic=account-upgrading-account).

## Create a {{site.data.keyword.bpshort}} workspace
{: #spring-schematics-workspace}
{: step}

Click one of the following options for the cluster deployment target and toolchain pipeline type. This action takes you to the "Deploy to {{site.data.keyword.cloud_notm}}" page where you create a {{site.data.keyword.bpshort}} workspace. Complete the required fields on that page, and then click **Create**.

The following options use the [simple-helm-toolchain template](https://github.com/open-toolchain/simple-helm-toolchain){: external}, which uses a classic pipeline structure.

[![Deploy to Kubernetes on {{site.data.keyword.cloud_notm}}](../images/Deploy_to_kube.svg "Deploy to Kubernetes on {{site.data.keyword.cloud_notm}}")](https://cloud.ibm.com/schematics/workspaces/create?repository=https://github.com/IBM-Cloud/Scalable-web-app-java/tree/master/terraform/simple-kube&terraform_version=terraform_v0.12){: external}
[![Deploy to OpenShift on {{site.data.keyword.cloud_notm}}](../images/Deploy_to_Openshift.svg "Deploy to OpenShift on {{site.data.keyword.cloud_notm}}")](https://cloud.ibm.com/schematics/workspaces/create?repository=https://github.com/IBM-Cloud/Scalable-web-app-java/tree/master/terraform/simple-openshift&terraform_version=terraform_v0.12){: external}

The following options use the [secure-kube-toolchain template](https://github.com/open-toolchain/secure-kube-toolchain){: external}, which uses a "GitSecure" pipeline structure.

[![Deploy to Kubernetes on {{site.data.keyword.cloud_notm}} (secured)](../images/Deploy_to_kube_Secured.svg "Deploy to Kubernetes on {{site.data.keyword.cloud_notm}}")](https://cloud.ibm.com/schematics/workspaces/create?repository=https://github.com/IBM-Cloud/Scalable-web-app-java/tree/master/terraform/secure-kube&terraform_version=terraform_v0.12){: external}
[![Deploy to OpenShift on {{site.data.keyword.cloud_notm}} (secured)](../images/Deploy_to_Openshift_Secured.svg "Deploy to OpenShift on {{site.data.keyword.cloud_notm}}")](https://cloud.ibm.com/schematics/workspaces/create?repository=https://github.com/IBM-Cloud/Scalable-web-app-java/tree/master/terraform/secure-openshift&terraform_version=terraform_v0.12){: external}

Based on which option you select, the corresponding Terraform template from this repository is automatically imported into the new {{site.data.keyword.bpshort}} workspace. The Terraform engine version is v0.12.
{: note}

## Apply the Terraform execution plan
{: #spring-apply-plan}
{: step}

1. In the **Variables** section of the {{site.data.keyword.bpshort}} Settings page, enter the values for each variable. Required fields are the fields without default values. However, default values can be overridden.
1. Optional. Click **Generate plan**. This action creates a Terraform execution plan and checks your configuration for syntax errors. On the {{site.data.keyword.bpshort}} Activity page, you can review log files for errors and {{site.data.keyword.cloud_notm}} resources that must be created, modified, or deleted to achieve the state of the Terraform template.
1. After you enter all the values for the variables and are satisfied with the changes, click **Apply plan**. This step takes some time to complete (usually 20 - 30 minutes, but it can take longer), due to the creation of a new Kubernetes or OpenShift cluster.
1. Follow the progress of this step by clicking the **View log** link next to the corresponding step.
1. After the plan is applied, view the URL to the generated {{site.data.keyword.cloud_notm}} DevOps toolchain. The URL is located near the end of the log file on a line that begins with "View the toolchain at:."

If you apply your plan a second time, the previously created Kubernetes or OpenShift cluster and any applications that are deployed to it are deleted, and a new cluster is created.
{: note}

## Related information
{: #spring-related}

For more information about this workflow, see [Getting started with {{site.data.keyword.bplong_notm}} and Terraform](/docs/schematics?topic=schematics-getting-started).

## Next steps
{: #spring-next-steps}

* View your app. For information about viewing your app, see [Monitor application health](/docs/solution-tutorials?topic=solution-tutorials-scalable-webapp-kubernetes#scalable-webapp-kubernetes-monitor_application).
* Scale your app. For information about scaling your app, see [Scale Kubernetes pods](/docs/solution-tutorials?topic=solution-tutorials-scalable-webapp-kubernetes#scalable-webapp-kubernetes-scale_cluster).
