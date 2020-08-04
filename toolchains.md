---

copyright:
  years: 2019, 2020
lastupdated: "2020-08-03"

keywords: developer tools, building apps, developer entry point, get started coding, DevOps, toolchain, continuous delivery, cluster

subcollection: apps

---

{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# DevOps toolchains
{: #devops-toolchains}

A DevOps toolchain is a set of tools that automates the tasks of developing and deploying your app. You can perform DevOps manually with simple apps, but the need for automation increases quickly as app complexity increases, and toolchain automation is a must-have for continuous delivery.
{: shortdesc}

The core component of a DevOps toolchain is a version control repository like GitHub. More tools might include backlog tracking, delivery pipelines, an integrated development environment (IDE), and monitoring like {{site.data.keyword.DRA_full}}.

When you [create an app](/docs/apps?topic=apps-getting-started) by using a starter kit, and then click **Deploy my app** on the App details page, a DevOps toolchain is created. The toolchain has a code repository, delivery pipeline, and web IDE. You can then build on this toolchain to collaboratively manage and deploy your app to separate environments for development, test, and production.

For more information, see the [{{site.data.keyword.contdelivery_full}} Getting started tutorial](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-getting-started).

For more information about managing DevOps toolchains and delivery pipelines by using the {{site.data.keyword.cloud_notm}} Command Line Interface (CLI), see [Viewing a toolchain with the CLI](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started#viewing-toolchain-cli) and [Viewing a pipeline by using the CLI](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-pipeline-working#viewing-pipeline-cli).

For information about improved integration between DevOps continuous delivery and {{site.data.keyword.containerlong_notm}}, see [Connecting {{site.data.keyword.containerlong_notm}} and {{site.data.keyword.contdelivery_full}}](https://www.ibm.com/cloud/blog/announcements/connecting-ibm-cloud-kubernetes-service-and-ibm-continuous-delivery){: external}.
