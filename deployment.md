---

copyright:

  years: 2014, 2017, 2018

lastupdated: "2017-01-16"

---

{:shortdesc: .shortdesc}

# {{site.data.keyword.Bluemix_notm}} security deployment
{: #security-deployment}

{{site.data.keyword.Bluemix_notm}} security deployment architecture includes different information flows for app users and developers to ensure secure access.

![{{site.data.keyword.Bluemix_notm}} security deployment architecture](images/sec_deployment.svg)

Figure 1. {{site.data.keyword.Bluemix_notm}} security deployment architecture

## User login flow
{: #user-login}

For {{site.data.keyword.Bluemix_notm}} *app users*, the **app user flow** is as follows:
 1. Through a firewall, with intrusion prevention and network security in place.
 2. Through the IBM DataPower Gateway with reverse proxy and SSL termination proxy.
 3. Through the network router.
 4. Reaches the application runtime in the droplet execution agent (DEA).

The {{site.data.keyword.Bluemix_notm}} *developer* follows two main flows: for login and for development and deployment.

## Developer login flow
{: #dev-login}

For developers who are logging in to {{site.data.keyword.Bluemix_notm}} Public, the flow is as follows:
      1. Through the IBM Single Sign On service.
      2. Through IBM web identity.
    * For developers who are logging in to {{site.data.keyword.Bluemix_notm}} Dedicated or Local, the flow is through the enterprise LDAP.

### Development and deployment flow
{: #dev-dep-login}

1. Through a firewall, with intrusion prevention and network security in place. This applies to {{site.data.keyword.Bluemix_notm}} Dedicated only.
2. Through the IBM DataPower Gateway with reverse proxy and SSL termination proxy.
3. Through the network router.
4. Through authorization by using Cloud Foundry cloud controller, to ensure access to only apps and service instances that are created by the developer.

### Dedicated and local flow
{: #dedicate-loc-login}

For {{site.data.keyword.Bluemix_notm}} Dedicated and {{site.data.keyword.Bluemix_notm}} Local *administrators*, the **administrator flow** is as follows:
1. Through a firewall, with intrusion prevention and network security in place.
2. Through the IBM DataPower Gateway with reverse proxy and SSL termination proxy.
3. Through the network router.
4. Reaches the Administration page in the {{site.data.keyword.Bluemix_notm}} user interface.

In addition to users described in these paths, an authorized IBM security operations team performs various operational security tasks, such as the following:
 * Vulnerability scans. For {{site.data.keyword.Bluemix_notm}} Local, you own the physical security and any scans within your firewall.
 * User access management.
 * Operating system hardening by periodically applying fixes with IBM Endpoint Manager.
 * Management of risks with intrusion protection.
 * Security monitoring with QRadar.
 * Security reports available on the Administration page.
