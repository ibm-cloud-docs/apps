---

copyright:
  years: 2018, 2023
lastupdated: "2023-04-28"

keywords: getting started apps, create app tutorial, add services, deploy apps, create app, app tutorial, toolchain, devops, schematics, devsecops

subcollection: apps
content-type: tutorial
account-plan: lite
completion-time: 30m

---

{{site.data.keyword.attribute-definition-list}}

# Getting started with apps
{: #getting-started}
{: toc-content-type="tutorial"}
{: toc-completion-time="30m"}

You can use a variety of ways to build and deploy enterprise-ready applications in {{site.data.keyword.cloud_notm}}. Possible deployment targets include {{site.data.keyword.cloud_notm}} Kubernetes Service, Red Hat OpenShift on {{site.data.keyword.cloud_notm}}, and {{site.data.keyword.codeenginefull}}.
{: shortdesc}

## Before you begin
{: #prereqs-getting-started}

Depending on your [{{site.data.keyword.cloud}} account type](/registration){: external}, access to certain resources might be limited or constrained. Depending on your plan limits, certain capabilities that are required by some toolchains might not be available. For more information, see [Setting up your IBM Cloud account](/docs/account?topic=account-account-getting-started).

For more information about requirements for specific deployment targets, see the following table.

| Deployment target | Prerequisites | 
|--------|---------------|
| {{site.data.keyword.cloud_notm}} Kubernetes Service / Helm | Create a free or paid cluster. One free Kubernetes cluster is available per account. For more information, see [Deploying apps to Kubernetes clusters](/docs/containers?topic=containers-app). Helm is a package manager for Kubernetes that allows you to package, configure, and deploy apps and services to {{site.data.keyword.cloud_notm}} Kubernetes Service. |
| Red Hat OpenShift on {{site.data.keyword.cloud_notm}} | OpenShift is available only through a standard cluster, which requires you to have a billable account. [Learn more](/docs/openshift?topic=openshift-openshift_apps) or [create an OpenShift cluster](/kubernetes/overview){: external}.|
| {{site.data.keyword.codeenginefull}} | Ensure that you have either a Pay-As-You-Go account or a Subscription account to use {{site.data.keyword.codeengineshort}} as your deployment target. If you are using a free Lite account, upgrade it before you use {{site.data.keyword.codeengineshort}}. [Learn more about accounts.](/docs/account) |
{: caption="Table 1. Requirements for deployment targets" caption-side="bottom"}

## View previously created apps
{: #view-getting-started}

You can view previously created apps from the [{{site.data.keyword.cloud_notm}} Resource List](/resources). From the {{site.data.keyword.cloud_notm}} console, select the ![Navigation Menu icon](../icons/icon_hamburger.svg "Menu") > **Resource list**. Then, expand the **Developer tools** category.

## Select an option for creating and deploying apps
{: #create-getting-started}

Several options are available for you to create and deploy apps on {{site.data.keyword.cloud_notm}}. You can use any of the following entry points to learn more.

* {{site.data.keyword.contdelivery_full}} uses DevOps toolchain templates to help you create and deploy apps. For more information, see [Toolchain availability, templates, and tutorials](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd_about). You can find several DevOps-based tutorials in the “Tutorials” section of the [{{site.data.keyword.contdelivery_short}} docs](/docs/ContinuousDelivery).
* [Set up continuous deployment with {{site.data.keyword.bpshort}} and DevOps toolchain](/schematics?topic=schematics-workspace-continuous-deployment).
* View the [tutorials for deploying a secure app with DevSecOps](/docs/devsecops).
* Browse or search the [{{site.data.keyword.cloud_notm}} catalog](/catalog){: external} for apps and services that you can create and use today.
* [IBM Developer code patterns](https://developer.ibm.com/patterns/){: external} help you quickly create your app and deploy it to {{site.data.keyword.cloud_notm}}.
* Use the following tutorials to use {{site.data.keyword.bplong_notm}} to create and deploy apps:
   * [Deploy a Node.js Express app by using {{site.data.keyword.bplong_notm}}](/docs/apps?topic=apps-tutorial-node-webapp)
   * [Deploy a Java Spring app by using {{site.data.keyword.bplong_notm}}](/docs/apps?topic=apps-tutorial-spring-webapp)
   * [Deploy a Java Liberty app by using {{site.data.keyword.bplong_notm}}](/docs/apps?topic=apps-tutorial-liberty-webapp)
* Check out the Tutorials section in the navigation menu to find more ways to create and deploy apps.
