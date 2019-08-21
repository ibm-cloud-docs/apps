---

copyright:
  years: 2019
lastupdated: "2019-06-03"

keywords: apps, custom, domain, kubernetes, cloud foundry, add, subdomain, custom domain, dns, domainname, domain name, endpoint, update, migrate

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Eigene Domänen verwalten
{: #update-domain}

Mithilfe von Domänen wird die URL-Route angegeben, die Ihrer Organisation in {{site.data.keyword.cloud}} zugeordnet ist. Angepasste Domänen leiten Anforderungen für Ihre Anwendungen an eine Ihnen gehörende URL. Eine angepasste Domäne kann eine gemeinsame Domäne, eine gemeinsame Unterdomäne oder eine gemeinsame Domäne und ein gemeinsamer Host sein. Wenn keine angepasste Domäne angegeben ist, verwendet {{site.data.keyword.cloud_notm}} eine gemeinsam genutzte Standarddomäne in der Route für Ihre App. Der Prozess zur Verwaltung Ihrer Domänen ist von Ihrem Bereitstellungsziel abhängig, z. B. {{site.data.keyword.containershort}}, Cloud Foundry oder andere.
{:shortdesc}

Um eine angepasste Domäne zu verwenden, müssen Sie die angepasste Domäne auf einem öffentlichen DNS-Server registrieren und dann die angepasste Domäne in {{site.data.keyword.cloud_notm}} konfigurieren. Dann müssen Sie die angepasste Domäne der {{site.data.keyword.cloud_notm}}-Systemdomäne auf dem öffentlichen DNS-Server zuordnen. Nachdem Ihre angepasste Domäne der Systemdomäne zugeordnet wurde, werden Anforderungen für Ihre angepasste Domäne an Ihre App in {{site.data.keyword.cloud_notm}} weitergeleitet.

## Domäne für Kubernetes-Apps ändern
{: #update-domain-kube}

Die Unterdomäne für {{site.data.keyword.containershort_notm}}-Hostnamen ist `containers.appdomain.cloud`. Der von IBM bereitgestellte Ingress-Unterdomänenplatzhalter `*.<cluster_name>.<region>.containers.appdomain.cloud` ist standardmäßig für Ihren Cluster registriert. Das von IBM bereitgestellte TLS-Zertifikat ist ein Platzhalterzertifikat und kann für die Platzhalterunterdomäne verwendet werden. Weitere Informationen finden Sie unter [Mehrere Domänen in einem Namensbereich](/docs/containers?topic=containers-ingress#multi-domains).

## Angepasste Domäne für Kubernetes-Apps verwenden
{: #custom-domain-kube}

Zur Verwendung einer angepassten Domäne müssen Sie diese als Platzhalter-Domäne, z. B. `*.custom_domain.net`, registrieren. Um TLS verwenden zu können, müssen Sie ein Platzhalterzertifikat abrufen. Weitere Informationen finden Sie unter [Mehrere Domänen in einem Namensbereich](/docs/containers?topic=containers-ingress#multi-domains).

Beschäftigen Sie sich mit [diesem Lernprogramm](/docs/tutorials?topic=solution-tutorials-scalable-webapp-kubernetes), das Sie beim Erstellen eines Gerüsts für eine Web-App, beim lokalen Ausführen der Anwendung in einem Container und beim anschließenden Bereitstellen in einem Kubernetes-Cluster begleitet, der mit IBM Kubernetes Service erstellt wurde. Darüber hinaus zeigt Ihnen das Lernprogramm, wie Sie eine angepasste Domäne binden, den Zustand der Umgebung überwachen und die App skalieren.

## Domäne für Cloud Foundry-Apps ändern
{: #update-domain-cf}

Bei Cloud Foundry-Apps können Sie Ihre Domäne von `mybluemix.net` in `appdomain.cloud` ändern, indem Sie entweder die {{site.data.keyword.cloud_notm}}-Konsole oder die Befehlszeilenschnittstelle verwenden. Weitere Informationen zum Ändern Ihrer Domäne in `appdomain.cloud` finden Sie unter [Aktualisieren Ihrer Domäne](/docs/cloud-foundry-public?topic=cloud-foundry-public-update-domain).

Die gemeinsam genutzte Standarddomäne ist `mybluemix.net`, aber `appdomain.cloud` ist eine weitere Domänenoption, die Sie verwenden können.
{: tip}

## Angepasste Domäne für Cloud Foundry-Apps verwenden
{: #custom-domain-cf}

Bei Cloud Foundry-Apps können Sie eine angepasste Domäne erstellen und verwenden, indem Sie entweder die {{site.data.keyword.cloud_notm}}-Konsole oder die Befehlszeilenschnittstelle verwenden. Weitere Informationen finden Sie unter [Angepasste Domäne hinzufügen und verwenden](/docs/cloud-foundry-public?topic=cloud-foundry-public-custom-domains).
