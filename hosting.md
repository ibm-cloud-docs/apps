---

copyright:
  years: 2017, 2019
lastupdated: "2019-06-25"

keywords: apps, application, migrating apps, hosting apps, migrating, hosting, migration

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Choosing your hosting environment
{: #hosting}

If you have an existing application, you can host it on {{site.data.keyword.cloud}} with all the infrastructure or platform services you need.
{:shortdesc}

With {{site.data.keyword.cloud_notm}}, you no longer need to make large investments in hardware to test out or run a new app. Instead, we manage it all for you and only charge for what you use. Your cloud server environment is the base of your infrastructure layer. You can choose a single option or a combination for more complex environments. 

You have various options for hosting your apps, giving you as much control over the infrastructure as you want or need. You can run your app in any of the following ways:

  * As a Docker container on a Kubernetes cluster
  * As a Cloud Foundry app
  * As a serverless function
  * As VMware
  * As a virtual machine
  * On high-performance {{site.data.keyword.baremetal_short}} 
  
<!--
{{site.data.keyword.baremetal_short}} are single-tenant, physical servers that are dedicated to a single customer. You control almost everything from the server host to the RAM and storage devices. These servers are used with workloads that require compute power over a sustained time, for example, several months.

Some example workloads include e-commerce, ERP, CRM, SCM, and financial services and regulatory applications.

{{site.data.keyword.BluVirtServers_short}} can be deployed as either as public or dedicated instances. With public instances, the resources of the server are shared with other customers, also known as a multi-tenant environment. Private instances dedicate the resources of the physical server to one customer who can have one or more virtual machines on the same server. These servers are ideal for workloads that run for a limited time, for example, a couple of weeks. Some workload examples are development and testing, backup and recovery, and disaster recovery. For more information about server options, see [Bare metal servers versus virtual servers: Choosing the best option for you](https://www.ibm.com/cloud/blog/bare-metal-virtual-servers-works){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon").
-->

Check out the following table for a summary of your compute options.

| Option | Description | 
|--------|---------------|
| [{{site.data.keyword.containerlong_notm}}](/docs/containers?topic=containers-getting-started) | Combines Docker containers, the Kubernetes technology, an intuitive user experience, and built-in security and isolation to automate the deployment, operation, scaling, and monitoring of containerized apps in a cluster of compute hosts. |
| [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) | Instantiate multiple, isolated, enterprise-grade Cloud Foundry platforms on demand. |
| [{{site.data.keyword.openwhisk_short}}](/docs/openwhisk?topic=cloud-functions-getting_started) | A Functions-as-a-Service (FaaS) programming platform based on Apache OpenWhisk. |
| [{{site.data.keyword.vmwaresolutions_short}}](/docs/services/vmwaresolutions?topic=vmware-solutions-getting-started) | Quickly and seamlessly integrate or migrate on-premises VMware workloads by using scalable, secure, and high-performance infrastructure and the industry-leading VMware hybrid virtualization technology. |
| [{{site.data.keyword.BluVirtServers_short}}](/docs/vsi?topic=virtual-servers-about-public-virtual-servers) | Scalable virtual servers that are purchased with dedicated cores and memory allocations. |
| [{{site.data.keyword.baremetal_short}}](/docs/bare-metal?topic=bare-metal-about-bm)  | Hourly or monthly, single-tenant servers that are dedicated to you and not shared in any part, including server resources, with other customers. |
{: caption="Table 1. Compute options" caption-side="top"}

