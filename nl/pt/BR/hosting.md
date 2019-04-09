---

copyright:
  years: 2017, 2018
lastupdated: "2018-12-04"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Migrando e hospedando apps
{: #hosting}

Se você tiver um app existente, será possível hospedá-lo no {{site.data.keyword.cloud}} com todos os serviços de infraestrutura ou de plataforma necessários. Também é possível migrar seu app para o {{site.data.keyword.cloud_notm}} incrementalmente em vez de deslocar seu app para o ambiente de nuvem de uma só vez.

## Migrando aplicativos
{: #migrating}

Se você precisar que o app acesse seus dados ou serviços no local, use o [{{site.data.keyword.SecureGatewayfull}}](/docs/services/SecureGateway/index.html) para estabelecer um túnel seguro entre uma organização do {{site.data.keyword.cloud_notm}} e sua rede de backend corporativo. Para obter detalhes, consulte [Atingindo o back-end corporativo com o {{site.data.keyword.cloud_notm}} Secure Gateway por meio do console ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://developer.ibm.com/bluemix/2015/04/01/reaching-enterprise-backend-bluemix-secure-gateway/){: new_window}.

Se você precisar de ajuda com a sua migração, os [{{site.data.keyword.cloud_notm}} Serviços de migração ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud/migration-services){: new_window} estarão disponíveis.

## Hospedando aplicativos
{: #ht_hostapp}

No catálogo do {{site.data.keyword.cloud_notm}} [ ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/catalog/?taxonomyNavigation=apps){: new_window}, é possível escolher um ambiente gerenciado como o Kubernetes ou o Cloud Foundry, ou hospedar o app diretamente em um servidor bare metal ou virtual.

Em uma implementação virtual, a maioria das operações do seu app é gerenciada pelo {{site.data.keyword.cloud_notm}}. Uma implementação [virtual](/docs/vsi/vsi_about.html) é melhor se sua carga de trabalho está espalhada entre regiões geográficas e você deseja usar um hypervisor do {{site.data.keyword.cloud_notm}} para gerenciar suas implementações. Uma implementação [básica](/docs/bare-metal/index.html#getting-started) é melhor quando você precisa de acesso direto a um servidor físico dedicado para maior desempenho.

Você também tem muitas opções para:
* Selecionar o tipo de [armazenamento![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/catalog/?taxonomyNavigation=apps&category=slstorage){: new_window} que é o certo para você por meio de armazenamento de bloco, armazenamento de arquivo ou Object Storage.
* Selecionar o tipo de [rede![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/catalog/?taxonomyNavigation=apps&category=slnetwork){: new_window} de que você precisa.
* Selecionar um serviço de [conteinerização![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/catalog/?taxonomyNavigation=apps&category=containers){: new_window} para aproveitar a tecnologia Kubernetes do {{site.data.keyword.cloud_notm}}.
