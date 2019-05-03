---

copyright:
  years: 2017, 2019
lastupdated: "2019-03-15"

keywords: apps, application, migrating apps, hosting apps, migrating, hosting

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Migrando e hospedando apps
{: #hosting}

Se você tiver um app existente, será possível hospedá-lo no {{site.data.keyword.cloud}} com todos os serviços de infraestrutura ou de plataforma necessários. Também é possível migrar seu app para o {{site.data.keyword.cloud_notm}} incrementalmente em vez de deslocar seu app para o ambiente de nuvem de uma só vez.

## Migrando aplicativos
{: #migrating}

Se você precisar que o app acesse seus dados ou serviços no local, use o [{{site.data.keyword.SecureGatewayfull}}](/docs/services/SecureGateway?topic=securegateway-getting-started-with-sg#getting-started-with-sg) para estabelecer um túnel seguro entre uma organização do {{site.data.keyword.cloud_notm}} e sua rede de backend corporativo. Para obter detalhes, consulte [Atingindo o back-end corporativo com o {{site.data.keyword.cloud_notm}} Secure Gateway por meio do console ](https://developer.ibm.com/bluemix/2015/04/01/reaching-enterprise-backend-bluemix-secure-gateway/){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo").

Se você precisar de ajuda com a sua migração, os [{{site.data.keyword.cloud_notm}} Serviços de migração ](https://www.ibm.com/cloud/migration-services){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo") estarão disponíveis.

## Hospedando aplicativos
{: #ht_hostapp}

No catálogo do {{site.data.keyword.cloud_notm}} [ ](https://{DomainName}/catalog/?taxonomyNavigation=apps){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo"), é possível escolher um ambiente gerenciado como o Kubernetes ou o Cloud Foundry, ou hospedar o app diretamente em um servidor bare metal ou virtual.

Em uma implementação virtual, a maioria das operações do seu app é gerenciada pelo {{site.data.keyword.cloud_notm}}. Uma implementação [virtual](/docs/vsi?topic=virtual-servers-about-virtual-servers#about-virtual-servers) é melhor se sua carga de trabalho está espalhada entre regiões geográficas e você deseja usar um hypervisor do {{site.data.keyword.cloud_notm}} para gerenciar suas implementações. Uma implementação [básica](/docs/bare-metal?topic=bare-metal-bm-getting-started#getting-started) é melhor quando você precisa de acesso direto a um servidor físico dedicado para maior desempenho.

Você também tem muitas opções para:
* Selecionar o tipo de [armazenamento](https://{DomainName}/catalog/?taxonomyNavigation=apps&category=slstorage){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo") que é o certo para você por meio de armazenamento de bloco, armazenamento de arquivo ou Object Storage.
* Selecionar o tipo de [rede](https://{DomainName}/catalog/?taxonomyNavigation=apps&category=slnetwork){: new_window}![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")} que é necessário.
* Selecionar um serviço de [conteinerização](https://{DomainName}/catalog/?taxonomyNavigation=apps&category=containers){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo") para aproveitar a tecnologia Kubernetes do {{site.data.keyword.cloud_notm}}.
