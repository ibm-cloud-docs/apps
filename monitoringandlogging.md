---

copyright:
  years: 2015, 2017, 2018

lastupdated: "2017-07-31"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:pre: .pre}

# Overview
{: #monitoringandlogging}

{{site.data.keyword.Bluemix}} offers logging and monitoring integrated capabilities across different services, such as Cloud Foundry and {{site.data.keyword.containershort}}. You can also use the {{site.data.keyword.loganalysisfull}} service and the {{site.data.keyword.monitoringlong}} service for extended logging and monitoring capabilities.
{:shortdesc}

## Logging in Bluemix
{: #logging}

{{site.data.keyword.Bluemix_notm}}, by default, collects and displays logs for your apps, apps runtimes, and compute runtimes where those apps run. {{site.data.keyword.Bluemix_notm}} logging capabilities are integrated in the platform, and collection of data is automatically enabled for cloud resources.

The {{site.data.keyword.loganalysisfull}} service provides log collection and log search services for the {{site.data.keyword.Bluemix_notm}} platform, automatically collecting application and {{site.data.keyword.Bluemix_notm}} services’ data from select {{site.data.keyword.Bluemix_notm}} services. Use the {{site.data.keyword.loganalysisshort}} service to expand your log collection, log retention, and log search abilities when working with logs:

* Spend less time instrumenting your application and more time enhancing its value

    {{site.data.keyword.loganalysislong_notm}} automatically collects data from selected {{site.data.keyword.IBM_notm}} cloud services, no instrumentation is necessary.

* Keep your log data near your application workloads and safe guarded on cloud class economical storage solutions

    Collect and store log data from traditional and micro-service driven applications running in the {{site.data.keyword.IBM_notm}} Cloud in a centralized log. Retain log data for as long as you need.

	Logs are stored on {{site.data.keyword.IBM_notm}} Cloud storage. You can download logs when you need them.

* Gain insights into your environment to quickly detect, diagnose, and identify issues

    Visualize, analyze and interact with your data through customizable dashboards. Built on the Elastic stack platform, log search features offer you the flexibility and familiarity of Kibana to quickly build your dashboard to your application needs.

* Robust integration with APIs

    Integrate your log data into your applications and operations through the service’s APIs. Use the {{site.data.keyword.loganalysisshort}} service API to manage your retained logs, and to send log data from outside the {{site.data.keyword.IBM_notm}} Cloud.

* Choose the service plan that fits your needs.

     You may choose the Lite service plan or the Premium service plan to match your usage needs.

	 Choose the amount of logs that you can search per day. Different plans are available that you can use to search up to 500MB,  2GB, 5GB, and 10GB of logs per day.

	 **Note:** The features that you get through the Lite plan are the same as the integrated logging capabilities offered by default in {{site.data.keyword.Bluemix_notm}}.

Empower your DevOps team with features such as aggregation of application and environment logs for consolidated application or environment insights, encryption of logs, retention of log data for as long as it is required, and quick detection and troubleshooting of issues.

For more information, see [Logging in Bluemix](/docs/services/CloudLogAnalysis/log_analysis_ov.html#log_analysis_ov).


## Monitoring in Bluemix
{: #monitoring}

{{site.data.keyword.Bluemix_notm}}, by default, collects and displays metrics for CPU usage, memory utilization, and network I/O for the {{site.data.keyword.containershort}}.

You can use the {{site.data.keyword.monitoringlong}} service in {{site.data.keyword.Bluemix_notm}} to automatically collect and measure key metrics from your environment and applications. No special instrumentation is required to collect metrics. For example, you can use information provided by performance metrics to monitor how a service is running in the cloud, detect resource bottlenecks, and keep an eye on the service level agreement (SLA). When you analyze performance data for a service, you can detect situations that can lead to a resource bottleneck and consequently affect your service SLA to your clients. By taking early action, you can prevent situations that can impact your business negatively.

Use the {{site.data.keyword.monitoringlong}} service to expand your collection, retention, and analysis capabilities in {{site.data.keyword.Bluemix_notm}} when working with metrics:

* Alert into action!

    {{site.data.keyword.monitoringlong}} offers an API that you can use to set performance thresholds, and to be notified when those thresholds are breached. Define alert rules for a single service instance or app instance, and alert rules that report on a set of instances. When an alert is triggered, get a notification through an e-mail, a PagerDuty event, a webhook notification, or any combination of the three.

* Add custom metrics.

    {{site.data.keyword.monitoringlong}} premium plan offers APIs that you can use to add relevant application and business metrics to your Cloud Monitoring data. You can also use them to send metric data from outside the {{site.data.keyword.IBM_notm}} Cloud into the {{site.data.keyword.monitoringlong}} service.

* Build reusable dashboards and make them interactive.

    {{site.data.keyword.monitoringlong}}’s hosted Grafana provides support for building custom dashboards with a large palate of visualization options.  Make your dashboards dynamic with templating by using metric queries with variables.

* Access your service through the {{site.data.keyword.Bluemix_notm}} catalog.

    {{site.data.keyword.monitoringlong}} is available as a service tile in the DevOps section of the {{site.data.keyword.Bluemix_notm}} catalog.  For the {{site.data.keyword.containershort}} service with single and group containers, you can access the service from the {{site.data.keyword.Bluemix_notm}} UI.

* Choose the service plan that fits your needs.

    You may choose the Lite service plan or the Premium service plan to match your usage needs. The Lite plan offers metric collection at once per minute, retention for 15 days, and complementary alerting. Alternatively, you can select the Premium plan to enable greater consumption, longer metrics retention, and to gain access to the service APIs, for example, to send or retrieve metrics from the {{site.data.keyword.monitoringlong}} service. {{site.data.keyword.monitoringlong}} offers metric collection at once per minute.  The Lite plan retains metrics at full resolution for 15 days. The Premium plan retains metrics at full resolution for 45 days.

    **Note:** The features that you get through the Lite plan are the same as the integrated monitoring capabilities offered by default in {{site.data.keyword.Bluemix_notm}}.

For more information, see [Monitoring in Bluemix](/docs/services/cloud-monitoring/monitoring_ov.html#monitoring_ov).

{{site.data.keyword.Bluemix_notm}} also offers infrastructure monitoring, that is available for every server, and easily readable reports. For more information, see [Infrastructure Monitoring & Reporting ![External link icon](../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/cloud-computing/bluemix/infrastructure-monitoring){: new_window}.
