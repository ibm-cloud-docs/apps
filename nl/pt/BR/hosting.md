---

copyright:
  years: 2017, 2018
lastupdated: "2018-01-18"

---

{:shortdesc: .shortdesc}

# Hospedando aplicativos
{: #hosting}

Se você tiver um aplicativo existente, será possível hospedá-lo no IBM Cloud com todos os serviços de infraestrutura ou de plataforma necessários. Também é possível tirar proveito da infraestrutura do {{site.data.keyword.Bluemix_notm}} para hospedar aplicativos que você desenvolveu especificamente para o {{site.data.keyword.Bluemix_notm}}.
{:shortdesc}

## Migrando aplicativos
{: #ht_hostapp}

É possível migrar os seus apps para {{site.data.keyword.Bluemix_notm}} incrementalmente, em vez de deslocar o app completamente para o ambiente de nuvem. É possível migrar uma parte de seu app primeiro e conectar-se aos dados existentes ou sistema de registros usando o serviço Cloud Integration.

Para seus aplicativos {{site.data.keyword.Bluemix_notm}}, pode ser necessário acessar os dados de backend ou serviços, como um sistema de registro. No {{site.data.keyword.Bluemix_notm}}, é possível usar o serviço Secure Gateway para estabelecer um túnel seguro entre uma organização do {{site.data.keyword.Bluemix_notm}} e a rede de backend corporativa. O serviço permite que os apps no {{site.data.keyword.Bluemix_notm}} acessem os dados e serviços da rede de backend. Para obter detalhes, veja [Atingindo o backend corporativo com o Bluemix Secure Gateway por meio do console ![Ícone de link externo](../icons/launch-glyph.svg)](https://developer.ibm.com/bluemix/2015/04/01/reaching-enterprise-backend-bluemix-secure-gateway/){: new_window}.

O {{site.data.keyword.Bluemix_notm}} pode hospedar seu aplicativo existente e fornecer toda a infraestrutura no {{site.data.keyword.Bluemix_notm}}. No [catálogo](https://console.bluemix.net/catalog/?taxonomyNavigation=apps), é possível escolher se você hospedará seu aplicativo na nuvem em um servidor bare metal ou em um servidor virtual.

É possível migrar partes do aplicativo para o {{site.data.keyword.Bluemix_notm}} todas de uma vez ou componente por componente. Dê uma olhada em alguns dos serviços que oferecemos à medida que você migra seu aplicativo.

* Selecione o tipo de [armazenamento](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slstorage) que serve para você dentre armazenamento de bloco, armazenamento de arquivo ou armazenamento de objeto.
* Selecione o tipo de [rede](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slnetwork) que você precisa.
* Selecione um serviço de [conteinerização](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=containers) para aproveitar a tecnologia Kubernetes do {{site.data.keyword.Bluemix_notm}}.

## Próximas Etapas
{: #next-steps}

Se seu serviço puder ser hospedado em mais de uma região, será possível selecionar onde seu aplicativo será hospedado. Em [Atualizando aplicativos](updapps.html), é possível selecionar as regiões em que seu aplicativo está hospedado e editar sua URL customizada.
