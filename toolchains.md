---

copyright:
  years: 2019, 2023
lastupdated: "2023-01-20"

keywords: developer tools, building apps, developer entry point, get started coding, DevOps, toolchain, continuous delivery, cluster

subcollection: apps

---

{{site.data.keyword.attribute-definition-list}}

# DevOps toolchains
{: #devops-toolchains}

The {{site.data.keyword.cloud}} starter kits are deprecated. As of 18 February 2023, new applications cannot be created, and the starter kits will be removed from the catalog. For current users, existing apps will continue to operate and will be supported until the End of Support date on 31 March 2023. On this date, the Applications Details page will no longer be accessible, but you will still be able to access your application code and toolchains through your [{{site.data.keyword.cloud_notm}} Resource List](https://cloud.ibm.com/resources). For more information, see the [deprecation announcement](https://www.ibm.com/cloud/blog/announcements/deprecation-of-ibm-cloud-starter-kits){: external}.
{: deprecated}

A DevOps toolchain is a set of tools that automates the tasks of developing and deploying your app. You can perform DevOps manually with simple apps, but the need for automation increases as app complexity increases, and toolchain automation is a must-have for continuous delivery.
{: shortdesc}

The core component of a DevOps toolchain is a version control repository like GitHub. More tools might include backlog tracking, delivery pipelines, an integrated development environment (IDE), and monitoring like {{site.data.keyword.DRA_full}}.

When you [create an app](/docs/apps?topic=apps-getting-started) by using a starter kit, and then click **Deploy my app** on the App details page, a DevOps toolchain is created. The toolchain has a code repository, delivery pipeline, and web IDE. You can then build on this toolchain to collaboratively manage and deploy your app to separate environments for development, test, and production.

For more information, see the [{{site.data.keyword.contdelivery_full}} Getting started tutorial](/docs/ContinuousDelivery?topic=ContinuousDelivery-getting-started) and [Toolchain availability, templates, and tutorials](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd_about).

For more information about managing DevOps toolchains and delivery pipelines by using the {{site.data.keyword.cloud_notm}} Command Line Interface (CLI), see [Viewing a toolchain with the CLI](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started#viewing-toolchain-cli) and [Viewing a pipeline by using the CLI](/docs/ContinuousDelivery?topic=ContinuousDelivery-pipeline-working#viewing-pipeline-cli).
