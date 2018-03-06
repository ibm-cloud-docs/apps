---

copyright:
  years: 2017, 2018
lastupdated: "2017-01-26"

---

{:shortdesc: .shortdesc}

# Hospedando aplicativos
{: #hosting}

Se você tiver um aplicativo existente, será possível hospedá-lo no IBM Cloud com todos os serviços de infraestrutura ou de plataforma necessários. Para apps existentes, você aproveita a infraestrutura do {{site.data.keyword.Bluemix_notm}} para hospedar apps que você desenvolveu especificamente para {{site.data.keyword.Bluemix_notm}}.
{:shortdesc}

## Migrando aplicativos
{: #ht_hostapp}

Para apps existentes, é possível migrar seus apps para o {{site.data.keyword.Bluemix_notm}} incrementalmente, em vez de deslocar o app completamente para o ambiente de nuvem. É possível migrar uma parte de seu app primeiro e conectar-se aos dados existentes ou sistema de registros usando o serviço Cloud Integration.

Para seus aplicativos {{site.data.keyword.Bluemix_notm}}, pode ser necessário acessar os dados de backend ou serviços, como um sistema de registro. No {{site.data.keyword.Bluemix_notm}}, é possível usar o serviço do Secure Gateway para estabelecer um túnel seguro entre uma organização do {{site.data.keyword.Bluemix_notm}} e a rede de backend corporativa. O serviço permite que os apps no {{site.data.keyword.Bluemix_notm}} acessem os dados e serviços da rede de backend. Para obter detalhes, veja [Atingindo o backend corporativo com o Bluemix Secure Gateway por meio do console ![Ícone de link externo](../icons/launch-glyph.svg)](https://developer.ibm.com/bluemix/2015/04/01/reaching-enterprise-backend-bluemix-secure-gateway/){: new_window}.

O {{site.data.keyword.Bluemix_notm}} pode hospedar seu app existente e fornecer toda a infraestrutura necessária. No [catálogo](https://console.bluemix.net/catalog/?taxonomyNavigation=apps), é possível escolher se você hospedará seu app em um servidor bare metal ou em um servidor virtual. Uma implementação [básica](../bare-metal/index.html#about-bare-metal-servers) é melhor se você precisa de um servidor físico dedicado para maior desempenho. Uma implementação [virtual](/vsi/vsi_index.html#provisioning-a-virtual-server) é melhor se sua carga de trabalho está espalhada entre regiões geográficas e você deseja usar um hypervisor do {{site.data.keyword.Bluemix_notm}} para gerenciar suas implementações.

É possível migrar partes do aplicativo para o {{site.data.keyword.Bluemix_notm}} todas de uma vez ou componente por componente. Dê uma olhada em alguns dos serviços que oferecemos à medida que você migra seu aplicativo.

* Selecione o tipo de [armazenamento](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slstorage) que serve para você dentre armazenamento de bloco, armazenamento de arquivo ou armazenamento de objeto.
* Selecione o tipo de [rede](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slnetwork) que você precisa.
* Selecione um serviço de [conteinerização](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=containers) para aproveitar a tecnologia Kubernetes do {{site.data.keyword.Bluemix_notm}}.

## Próximas Etapas
{: #next-steps}

Se seu serviço puder ser hospedado em mais de uma região, será possível selecionar onde seu aplicativo será hospedado. Para fazer isso, registre e inclua as informações da URL customizada em seu app no {{site.data.keyword.Bluemix_notm}}. Em seguida, selecione as regiões em que seu app está hospedado. Consulte [Atualizando apps](updapps.html) para obter mais informações sobre como implementar seu app.
