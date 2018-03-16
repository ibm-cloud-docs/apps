---

copyright:
  years: 2017, 2018
lastupdated: "2018-03-16"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Migrating and hosting apps
{: #hosting}

If you have an existing app, you can host it on {{site.data.keyword.Bluemix}} with all the infrastructure or platform services you need. You can also migrate your app to {{site.data.keyword.Bluemix_notm}} incrementally instead of shifting your app to the cloud environment all at once.

## Migrating apps
{: #migrating}

If you need your app to access your on-premises data or services, you can use [{{site.data.keyword.SecureGatewayfull}}](../services/SecureGateway/secure_gateway.html) to establish a secured tunnel between an {{site.data.keyword.Bluemix_notm}} organization and your enterprise backend network. For details, see [Reaching enterprise backend with {{site.data.keyword.Bluemix_notm}} Secure Gateway via console](https://developer.ibm.com/bluemix/2015/04/01/reaching-enterprise-backend-bluemix-secure-gateway/){: new_window} ![External link icon](../icons/launch-glyph.svg).

If you need help with your migration, [IBM Cloud Migration Services](https://www.ibm.com/cloud/migration-services){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon") are available.

## Hosting apps
{: #ht_hostapp}

In the {{site.data.keyword.Bluemix_notm}} [catalog](https://console.bluemix.net/catalog/?taxonomyNavigation=apps){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon"), you can choose a managed environment like Kubernetes or Cloud Foundry, or can you host your app directly on a bare metal or virtual server.

On a virtual deployment, most of your app's operations are managed by {{site.data.keyword.Bluemix_notm}}. A [virtual](../vsi/vsi_about.html) deployment is best if your workload is spread out across geographic regions and you want to use an {{site.data.keyword.Bluemix_notm}} hypervisor to manage your deployments. A [bare metal](../bare-metal/index.html) deployment is best if you need direct access to a dedicated physical server for higher performance.

You also have many options for:
* Selecting the type of [storage](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slstorage){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon") that's right for you from block storage, file storage, or Object Storage.
* Selecting the type of [network](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slnetwork){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon") you need.
* Selecting a [containerization](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=containers){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon") service to take advantage of {{site.data.keyword.Bluemix_notm}} Kubernetes technology.