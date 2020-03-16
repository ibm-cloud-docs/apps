---

copyright:
  years: 2020
lastupdated: "2020-03-13"

keywords: high availability, disaster recovery, SLA

subcollection: creating-apps


---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}


# High availability and disaster recovery
{: #ha-dr}

All {{site.data.keyword.cloud}} general availability (GA) services have a Service Level Agreement of 99.99% availability. The services that provide the {{site.data.keyword.cloud_notm}} getting started and starter kit experiences are GA services that are offered in five regions: Dallas, London, Frankfurt, Tokyo, and Washington, DC. Each region has multiple different data centers for redundancy. The data for each location is kept in the data centers near that location. If all the data centers in a location fail, the services for that location become unavailable.

The services are available only on the public cloud, but the tools that are used with {{site.data.keyword.contdelivery_full}}, which the services use, can run in dedicated or public cloud environments and in on-premises environments.

Some starter kits automatically provision {{site.data.keyword.cloud_notm}} resources for you, and you can also add resources manually before you create your app. If the resource stores data, you must ensure that the resource meets all business continuity, disaster recovery, and regulatory compliance standards and policies for your organization. For more information, see [resource-specific documentation](/docs?tab=all-docs).

See [ensure zero downtime](/docs/overview?topic=overview-zero-downtime#zero-downtime) to learn more about the high availability and disaster recovery standards in {{site.data.keyword.cloud_notm}}. For more information about high availability and disaster recovery for {{site.data.keyword.contdelivery_short}}, see [{{site.data.keyword.contdelivery_short}} high availability and disaster recovery](/docs/ContinuousDelivery?topic=ContinuousDelivery-ha-dr). You can also find information about [Service Level Agreements](/docs/overview?topic=overview-zero-downtime#SLAs).  
