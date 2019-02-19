---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-01"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Usando contêineres com Kubernetes
{: #containers-kube}

Inicie o {{site.data.keyword.containershort}} implementando apps altamente disponíveis nos contêineres do Docker que são executados nos clusters do Kubernetes. Gerencie o desenvolvimento de sua equipe com Git e, em seguida, use a Cadeia de ferramentas do DevOps para gerenciar a implementação de seu app para o Kubernetes.
{: shortdesc}

Os contêineres são uma maneira padrão de empacotar apps e todas as suas dependências para que seja possível mover perfeitamente os apps entre ambientes. Ao contrário de máquinas virtuais, os contêineres não empacotam o sistema operacional. Apenas o código do app, o tempo de execução, as ferramentas do sistema, as bibliotecas e as configurações são compactados dentro dos contêineres. Os contêineres são mais leves, móveis e eficientes do que máquinas virtuais.

Consulte [Introdução ao {{site.data.keyword.containershort_notm}}](/docs/containers/container_index.html#container_index) para saber mais sobre o serviço.

## Configurando implementações
{: #config-deploy}

Ao criar apps de backend ou de serviço da web, é possível implementá-los no serviço {{site.data.keyword.containershort_notm}}, que usa o ambiente do Kubernetes.

1. Implemente seu app na nuvem configurando um pipeline de nuvem automatizado.
2. Clique em **Implementar na nuvem**.
3. Selecione Kubernetes como o destino. Será necessário [criar um cluster ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/containers-kubernetes/catalog/cluster/create){:new_window} se você ainda não tiver um.
4. Após a conclusão da implementação, efetue check-out do app em tempo real na nuvem, obtendo a URL nos logs do estágio de implementação do pipeline de entrega. O último endereço IP com uma porta é o novo início de seu app, por exemplo, 169.60.133.124:32355.

## Ligando serviços
{: #bind-services}

À medida que a cadeia de ferramentas é criada, os serviços associados a seu app são ligados ao cluster do Kubernetes usando segredos do Kubernetes. Os segredos são usados para gerenciar as credenciais de serviço fora do seu app em execução. O app lê os segredos e, em seguida, recupera os valores que ele precisa para iniciar a execução. Os serviços de ligação permitem implementar o app em outro ambiente do Kubernetes que pode estar usando as instâncias de serviço de nível de produção do {{site.data.keyword.cloud}}.

Se você excluir o serviço ou os segredos, será necessário ligá-los manualmente novamente ou excluir e recriar a cadeia de ferramentas.
{: tip}

Para obter mais informações, consulte [Segredos ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://kubernetes.io/docs/concepts/configuration/secret/){:new_window}.

## Iniciando o Desenvolvimento
{: #dev}

1. Efetue check-out do novo repositório Git on-line por meio da cadeia de ferramentas e comece a trabalhar com seu código. Para ver a cadeia de ferramentas, clique em **Visualizar cadeia de ferramentas**.
2. Acesse o repositório Git no qual o código foi criado clonando o repositório para seu ambiente local.
3. Abra o projeto com seu IDE favorito.

## Construindo e implementando com uma cadeia de ferramentas
{: #bulid-deploy-tc}

A cadeia de ferramentas contém o estágio de construção e o estágio de implementação.

### Estágio de construção
{: #build-stage}
O estágio de construção é acionado quando um `git push` é executado no repositório Git. O estágio no pipeline aciona uma construção de imagem do docker e coloca a imagem no registro de contêiner.

Para obter mais informações, consulte [Introdução ao IBM Cloud Container Registry](/docs/services/Registry/index.html#index).

### Estágio de implementação
{: #deploy-stage}

O estágio de implementação recupera a imagem mais recente do {{site.data.keyword.registryshort_notm}} e, em seguida, implementa-a no cluster do Kubernetes usando um gráfico de Helm. O gráfico de Helm foi incluído no app durante a implementação na nuvem. Os gráficos de Helm facilitam o gerenciamento das etapas de implementação da imagem de contêiner compactada.

Para obter mais informações, consulte [Gráficos ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://docs.helm.sh/developing_charts/){:new_window}.

O {{site.data.keyword.cloud_notm}} suporta vários [Gráficos de Helm pré-configurados ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/containers-kubernetes/solutions/helm-charts){:new_window}.

## Verificando a segurança do app
{: #sec}

O {{site.data.keyword.containershort_notm}} suporta varrer as imagens de contêiner compactadas para vulnerabilidades de segurança. A varredura de segurança é essencial para o suporte de aplicativos de nível corporativo.

Visualize o [repositório de imagem de
contêineres ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/containers-kubernetes/registry/private){:new_window} para verificar potenciais vulnerabilidades de segurança.
