---

copyright:
  years: 2017, 2018
lastupdated: "2017-01-16"

---

{:shortdesc: .shortdesc}

# Hosting apps
{: #hosting}

If you have an existing app, you can host it on IBM Cloud with all the infrastructure or platform services you need. You can also take advantage of the {{site.data.keyword.Bluemix_notm}} infrastructure to host apps that you've developed specifically for {{site.data.keyword.Bluemix_notm}}.
{:shortdesc}

## Migrating apps
{: #ht_hostapp}

You can migrate your apps to {{site.data.keyword.Bluemix_notm}} incrementally, instead of shifting the app completely to the cloud environment. You can migrate a portion of your app first and connect to the existing data or system of records by using the Cloud Integration service.

For your {{site.data.keyword.Bluemix_notm}} apps, you might need to access the back-end data or services, such as a system of record. In {{site.data.keyword.Bluemix_notm}}, you can use the Secure Gateway service to establish a secured tunnel between a {{site.data.keyword.Bluemix_notm}} organization and the enterprise backend network. The service enables the apps on {{site.data.keyword.Bluemix_notm}} to access the backend network’s data and services. For details, see [Reaching enterprise backend with Bluemix Secure Gateway via console ![External link icon](../icons/launch-glyph.svg)](https://developer.ibm.com/bluemix/2015/04/01/reaching-enterprise-backend-bluemix-secure-gateway/){: new_window}.

{{site.data.keyword.Bluemix_notm}} can host your existing app and provide all the infrastructure in the {{site.data.keyword.Bluemix_notm}}. In the [catalog](https://console.bluemix.net/catalog/?taxonomyNavigation=apps), you can choose whether you host your app on the cloud on a  bare metal server, or a virtual server.

You can migrate parts of the app to {{site.data.keyword.Bluemix_notm}} all at once or component by component. Take a look at a few of the services we offer as you migrate your app.

* Select the type of [storage](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slstorage) that's right for you from block storage, file storage, or object storage.
* Select the type of [network](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slnetwork) you need.
* Select a [containerization](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=containers) service to take advantage of {{site.data.keyword.Bluemix_notm}} Kubernetes technology.

## Next steps
{: #next-steps}

If your service can be hosted in more than one region, you can select where your app is hosted. In [Updating apps](updapps.html), you can select the regions where your app is hosted and edit your custom URL.
