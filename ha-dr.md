---

copyright:
  years: 2020, 2023
lastupdated: "2023-03-10"

keywords: high availability, disaster recovery, SLA

subcollection: apps


---

{{site.data.keyword.attribute-definition-list}}

# High availability and disaster recovery
{: #ha-dr}

The {{site.data.keyword.cloud}} starter kits are deprecated. As of 18 February 2023, new applications cannot be created, and the starter kits will be removed from the catalog. For current users, existing apps will continue to operate and will be supported until the End of Support date on 31 March 2023. On this date, the Applications Details page will no longer be accessible, but you will still be able to access your application code and toolchains through your [{{site.data.keyword.cloud_notm}} Resource List](https://cloud.ibm.com/resources). For more information, see the [deprecation announcement](https://www.ibm.com/cloud/blog/announcements/deprecation-of-ibm-cloud-starter-kits){: external}.
{: deprecated}

All {{site.data.keyword.cloud}} general availability (GA) services have a Service Level Agreement of 99.99% availability. The services that provide the {{site.data.keyword.cloud_notm}} getting started experience are GA services that are offered in these regions: Dallas, London, Frankfurt, Sydney, Tokyo, and Washington, DC. Each region has multiple different data centers for redundancy. The data for each location is kept in the data centers near that location. If all the data centers in a location fail, the services for that location become unavailable.

The services are available only on the public cloud, but the tools that are used with {{site.data.keyword.contdelivery_full}}, which the services use, can run in dedicated or public cloud environments and in on-premises environments.

You can add resources manually before you create your app. If the resource stores data, you must ensure that the resource meets all business continuity, disaster recovery, and regulatory compliance standards and policies for your organization. For more information, see [resource-specific documentation](/docs?tab=all-docs).

See [ensure zero downtime](/docs/overview?topic=overview-zero-downtime) to learn more about the high availability and disaster recovery standards in {{site.data.keyword.cloud_notm}}. For more information about high availability and disaster recovery for {{site.data.keyword.contdelivery_short}}, see [{{site.data.keyword.contdelivery_short}} high availability and disaster recovery](/docs/ContinuousDelivery?topic=ContinuousDelivery-ha-dr). You can also find information about [Service Level Agreements](/docs/overview?topic=overview-slas).  
