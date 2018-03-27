---

copyright:
  years: 2017, 2018
lastupdated: "2018-03-16"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Migrando e hospedando apps
{: #hosting}

Se você tiver um app existente, será possível hospedá-lo no {{site.data.keyword.Bluemix}} com todos os serviços de infraestrutura ou de plataforma necessários. Também é possível migrar seu app para o {{site.data.keyword.Bluemix_notm}} incrementalmente em vez de deslocar seu app para o ambiente de nuvem de uma só vez.

## Migrando aplicativos
{: #migrating}

Se você precisar que o app acesse seus dados ou serviços no local, use o [{{site.data.keyword.SecureGatewayfull}}](../services/SecureGateway/secure_gateway.html) para estabelecer um túnel seguro entre uma organização do {{site.data.keyword.Bluemix_notm}} e sua rede de backend corporativo. Para obter detalhes, consulte [Atingindo o backend corporativo com o {{site.data.keyword.Bluemix_notm}} Secure Gateway por meio do console ](https://developer.ibm.com/bluemix/2015/04/01/reaching-enterprise-backend-bluemix-secure-gateway/){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg).

Se você precisar de ajuda com sua migração, o [IBM Cloud Migration Services](https://www.ibm.com/cloud/migration-services){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo") estará disponível.

## Hospedando aplicativos
{: #ht_hostapp}

No [catálogo](https://console.bluemix.net/catalog/?taxonomyNavigation=apps){: new_window} do {{site.data.keyword.Bluemix_notm}} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo"), é possível escolher um ambiente gerenciado como o Kubernetes ou Cloud Foundry ou hospedar seu app diretamente em um servidor bare metal ou virtual.

Em uma implementação virtual, a maioria das operações do seu app é gerenciada pelo {{site.data.keyword.Bluemix_notm}}. Uma implementação [virtual](../vsi/vsi_about.html) é melhor se sua carga de trabalho está espalhada entre regiões geográficas e você deseja usar um hypervisor do {{site.data.keyword.Bluemix_notm}} para gerenciar suas implementações. Uma implementação [básica](../bare-metal/index.html) é melhor quando você precisa de acesso direto a um servidor físico dedicado para maior desempenho.

Você também tem muitas opções para:
* Selecionar o tipo de [armazenamento](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slstorage){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo") que é o certo para você por meio de armazenamento de bloco, armazenamento de arquivo ou armazenamento de objeto.
* Selecionar o tipo de [rede](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slnetwork){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo") de que você precisa.
* Selecionar um serviço de [conteinerização](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=containers){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo") para aproveitar a tecnologia Kubernetes do {{site.data.keyword.Bluemix_notm}}.
