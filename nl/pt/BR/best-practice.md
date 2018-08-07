---

copyright:
  years: 2017, 2018
lastupdated: "2018-07-25"

---

# O que torna um aplicativo bom?
{: #best-practice}

Construa seu app no {{site.data.keyword.Bluemix_notm}} para aproveitar todas as coisas que a nuvem oferece. Essas melhores práticas podem ajudá-lo a assegurar que seus apps estão prontos para a nuvem.
{:shortdesc}

## Construa seu app para ser independente de topologia

Em um ambiente não de nuvem, seu app pode usar uma topologia de implementação específica. No entanto, sua topologia de app pode mudar em apps em nuvem porque os apps e serviços prontos para a nuvem permitem mudanças de escalabilidade imediatas. As mudanças de escalabilidade incluem ajuste de escala dinâmica e redimensionamento manual do número de instâncias de um app.

Construa seu app para ser o mais genérico e stateless possível para evitar que seu app seja afetado pelas mudanças de escalabilidade.

## Suponha que o sistema de arquivos local não seja permanente

Não dependa dos arquivos gravados no sistema de arquivos porque uma instância do app pode ser movida, excluída ou duplicada na nuvem. Se um app usa o sistema de arquivos local como um cache de informações usadas frequentemente, incluindo logs do app, as informações são perdidas quando a instância é encerrada e reiniciada em um local diferente ou uma VM diferente.

É possível armazenar informações em um serviço, como um banco de dados SQL ou NoSQL em vez do sistema de arquivos local. Em um ambiente de nuvem dinâmica, também é crítico que seus logs estejam disponíveis em um serviço que prolongue as instâncias do app nas quais os logs são gerados.

## Estado de sessão do armazenamento fora de seu app

O estado de seu sistema é definido pelos seus bancos de dados e pelo armazenamento compartilhado e não por instância do app individual em execução. O stateful de qualquer classificação limita a escalabilidade de um app. Tente minimizar o impacto do estado da sessão armazenando-a em um local centralizado no servidor.

Se não for possível eliminar o estado de sessão completamente, envie-o por push para um armazenamento altamente disponível que seja externo ao seu servidor de aplicativos. Os armazenamentos incluem o IBM WebSphere eXtreme Scale, o Redis ou o Memcached ou um banco de dados externo.

## Use um registro de serviço externo para resolver terminais em serviço

Não presuma que os serviços que seu app usa sejam nomes de hosts ou endereços IP específicos alocados. Os serviços podem ser realocados ou regenerados em seu ambiente de nuvem e os nomes de hosts e endereços IP também podem mudar.

A extração de dependências específicas do ambiente em um conjunto de arquivos de propriedades é uma melhoria, mas ainda é inadequada. A melhor prática é usar um registro de serviço externo para resolver terminais em serviço ou delegar a função de roteamento inteira para um barramento de serviço ou um balanceador de carga com um nome virtual.

## Construa seu app usando uma arquitetura de várias regiões
{: #multiregion}

Execute múltiplas instâncias para evitar o tempo de inatividade em uma única região, mas para entregar um aplicativo ainda mais robusto, considere uma arquitetura multiregion.

## Assegure-se de que você esteja monitorando seus apps
{: #monitoring}

O {{site.data.keyword.Bluemix_notm}} torna mais fácil monitorar o seu aplicativo com serviços como [New Relic ![Ícone de link externo](../icons/launch-glyph.svg)](http://newrelic.com/){: new_window}. Veja [Monitoramento e criação de log](../monitor_log/logging.html#logging) para obter mais informações.

## Tire proveito de opções de suporte
{: #support}

O plano de precificação pago do {{site.data.keyword.Bluemix_notm}} oferece uma série de tipos de contas diferentes com suporte pago opcional. Não importa o tipo de sua conta, se você planeja trazer um aplicativo para produção no {{site.data.keyword.Bluemix_notm}}, considere a inscrição nesta opção.

Com ou sem suporte pago, é possível obter ajuda conforme descrito em [Suporte](../get-support/howtogetsupport.html), que oferece seguro contra problemas imprevistos.

## Evite APIs de infraestrutura em seu app

Se você conta com uma API de infraestrutura específica em seu app, mudar a infraestrutura é mais desafiador porque uma API de infraestrutura pode referir-se a muitas camadas diferentes em sua pilha de software.

É possível contar com produtos comerciais ou de software livre existentes e deixar as soluções PaaS na camada PaaS para mantê-las fora do seu código de app.

## Use protocolos padrão

Não use protocolos obscuros que requeiram configuração extra para resiliência.

Os apps baseados em protocolos padrão são mais resilientes com os itens de configuração delegados para a plataforma. Os protocolos padrão incluem HTTP, SSL, banco de dados padrão, enfileiramento e conexões de serviço da web.

## Use bibliotecas de compatibilidade em vez de recursos específicos do sistema operacional

Se você já usou recursos específicos do sistema operacional, será possível corrigir esse problema usando bibliotecas de compatibilidade, por exemplo, Cygwin e Mono. Cygwin é uma biblioteca de compatibilidade que fornece um conjunto de ferramentas Linux em um ambiente do Windows. Mono é uma biblioteca de compatibilidade que fornece recursos .NET do Windows no Linux.

Evite as dependências específicas do sistema operacional; em vez disso, use serviços que sejam fornecidos pela infraestrutura de middleware ou por provedores de serviços.

## Defina o script de seu processo de instalação

Seu app pode ser instalado frequentemente sob demanda no ambiente de nuvem dinâmica. O processo de instalação deve ser por script e confiável, e os dados da configuração devem ser exteriorizados a partir dos scripts.

Capture sua instalação do aplicativo como um conjunto uniforme de scripts que é independente do sistema operacional. Mantenha a instalação do app pequena e móvel para adaptar-se a diferentes técnicas de automação. Além disso, minimize as dependências que são requeridas pela instalação do app.

Para obter mais informações sobre apps prontos para nuvem, veja [O app de 12 fatores ![Ícone de link externo](../icons/launch-glyph.svg)](http://12factor.net/){: new_window}.


