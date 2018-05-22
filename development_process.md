---

copyright:
  years: 2018
lastupdated: "2018-05-21"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Recommended phases of cloud development
{: #development_process}

Cloud app developers pass through four fundamental phases in the development process: get started, code, deliver, and manage. The goal is to quickly produce a minimum viable app, and then use feedback from the production app to continuously iterate the code or deliver cycle until your app resonates with users.
{: shortdesc}

![Development flow](images/dev_flow_overview.png "Development flow") Figure 1. Phases of the development process

In some cases, `run` is called out as a separate phase but is combined here with the Deliver and Manage phases.

Let's take a closer look at the best way to use {{site.data.keyword.cloud_notm}} in your development flow.

##Get started
{: #get_started}

Build your app from the {{site.data.keyword.cloud_notm}} developer dashboards, where you can select a starter kit that is related to your use case and choose a programming language. {{site.data.keyword.cloud_notm}} uses instructions from the starter kit to automatically provision the resources you need and to create a language-specific, runtime-agnostic app that is the basis for your production app. To complete the getting started phase, click **Deploy to Cloud** from the developer dashboard. One click creates a DevOps toolchain complete with a code repository that is populated with your app source code and deployment pipeline.

![Get started](images/dev_get_started.png "Get started") Figure 2. Getting started flow

When you use the **Deploy to Cloud** button to set up your DevOps toolchain, select your runtime platform, for example Kubernetes or Cloud Foundry. The starter app that is produced from {{site.data.keyword.cloud_notm}} is runtime-agnositic and doesn’t need to be modified.
{: tip}

##Develop locally
{: #develop_locally}

After you create your starter app and toolchain, you start your development locally. Clone the code from your repository to a local workstation and import into your IDE. Use the {{site.data.keyword.dev_cli_notm}} to build, run, and test your cloud app on your local machine. The {{site.data.keyword.dev_cli_notm}} creates and manages a local container for you. When you’re ready to see your app running on the cloud, push to your cloud repository and merge your changes.

![Develop locally](images/dev_code_locally.png "Develop locally") Figure 3. Developing locally flow

The basic functions for {{site.data.keyword.dev_cli_notm}} are `bx dev build` and `bx dev run`, but the CLI offers much more. See [{{site.data.keyword.dev_cli_notm}}](../cli/idt/index.html) for more details.
{: tip}

##Deliver and manage in {{site.data.keyword.cloud_notm}}
{: #deliver_and_manage}

Merging changes to your cloud repository starts a build and deployment cycle in the DevOps toolchain that you created previously. Your app is running in the cloud after a few minutes.

To check status of your DevOps pipeline, use your Delivery Pipeline dashboard. To check the overall status of your app, see the {{site.data.keyword.cloud_notm}} dashboard for your account.
{: tip}

The toolchain that is produced by your getting started experience has the basic components that you need for collaborative, team-based continuous delivery. However, {{site.data.keyword.cloud_notm}} offers an extensive set of DevOps services that you can add into your toolchain to enhance delivery, monitoring, logging, alerting.

![Deliver and manage](images/dev_deliver_and_manage.png "Deliver and manage") Figure 4. Delivering and managing flow

Learn more about [continuous development on {{site.data.keyword.cloud_notm}}](../services/ContinuousDelivery/index.html#cd_getting_started).

## Putting it all together

![Process detail](images/dev_process_detail.png "Process details") Figure 5. End-to-end development process
