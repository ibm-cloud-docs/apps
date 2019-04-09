---

copyright:
  years: 2017, 2018
lastupdated: "2018-01-18"

---

# O que torna um aplicativo bom?

Construir seu aplicativo no {{site.data.keyword.Bluemix_notm}} pode ser diferente de um aplicativo que você pode construir de outra forma. Essas melhores práticas podem ajudá-lo a construir o melhor aplicativo para a plataforma de nuvem.

## Arquitetura multiregion
{: #multiregion}

A execução de várias instâncias é recomendada para evitar o tempo de inatividade em uma única região, mas para entregar um aplicativo ainda mais robusto, considere uma arquitetura multiregion.

## Opções de monitoramento
{: #monitoring}

O {{site.data.keyword.Bluemix_notm}} torna mais fácil monitorar o seu aplicativo com serviços como [Monitoramento e Analytics](/docs/services/monana/index.html) e [New Relic ![Ícone de link externo](../icons/launch-glyph.svg)](http://newrelic.com/){: new_window}. Consulte [monitoramento e criação de log](../monitor_log/monitoringandlogging.html#monitoring_logging_bluemix_apps) para obter informações adicionais.

## Opções de suporte
{: #support}

O plano de precificação pago do {{site.data.keyword.Bluemix_notm}} oferece uma série de tipos de conta diferentes com suporte pago *opcional*. Não importa o tipo de sua conta, se você planeja trazer um aplicativo para produção no {{site.data.keyword.Bluemix_notm}}, considere a inscrição nesta opção.

Com ou sem suporte pago, é possível obter ajuda conforme descrito em [suporte](../get-support/howtogetsupport.html), oferece seguro contra problemas imprevistos.

## Desenvolvendo aplicativos prontos para nuvem
{: #cloud-ready-apps}

Se todos os princípios a seguir forem observados em seu app, o app estará pronto para nuvem e poderá ser migrado para o {{site.data.keyword.Bluemix_notm}}. Se um princípio for violado em seu aplicativo, geralmente será possível modificar seu aplicativo para aderir aos princípios.
{:shortdesc}

### Não codifique seu app diretamente para uma topologia específica.

Em um ambiente não de nuvem, o app pode usar uma topologia de implementação específica. No entanto, a topologia do app pode ser mudada nos apps em nuvem, pois os apps e serviços prontos para nuvem permitem mudanças imediatas de escalabilidade. As mudanças de escalabilidade incluem ajuste de escala dinâmica e redimensionamento manual do número de instâncias de um app.

Construa seu app para ser o mais genérico e stateless possível para evitar que seu app seja afetado pelas mudanças de escalabilidade.

### Não assuma que o sistema de arquivos local seja permanente.

Como uma instância do app pode ser movida, excluída ou duplicada a qualquer momento na nuvem, não confie nos arquivos que são gravados no sistema de arquivos. Se um app usa o sistema de arquivos local como um cache de informações usadas frequentemente, incluindo logs do app, as informações são perdidas quando a instância é encerrada e reiniciada em um local diferente ou uma VM diferente.

É possível armazenar informações em um serviço, como um banco de dados SQL ou NoSQL em vez do sistema de arquivos local. Em um ambiente de nuvem dinâmica, também é crítico que seus logs estejam disponíveis em um serviço que prolongue as instâncias do app nas quais os logs são gerados.

### Não armazene o estado de sessão em seu app.

O estado de seu sistema é definido pelos seus bancos de dados e pelo armazenamento compartilhado e não por instância do app individual em execução. O stateful de qualquer classificação limita a escalabilidade de um app. Tente minimizar o impacto do estado da sessão armazenando-a em um local centralizado no servidor.

Se não for possível eliminar o estado de sessão completamente, envie-o por push para um armazenamento altamente disponível que seja externo ao seu servidor de aplicativos. Os armazenamentos incluem IBM WebSphere Extreme Scale, Redis ou Memcached ou um banco de dados externo.

### Não use dependência de infraestrutura específica.

Esse é um princípio geral que possui diversas manifestações. Por exemplo, não presuma que os serviços que seu app usa sejam nomes de hosts ou endereços IP específicos alocados. Os serviços podem ser realocados ou regenerados em seu ambiente de nuvem e os nomes de hosts e endereços IP também podem mudar.

A extração de dependências específicas do ambiente para um conjunto de arquivos de propriedade é uma melhoria, mas ainda é inadequada. A melhor prática é usar um registro de serviço externo para resolver terminais em serviço ou delegar a função de roteamento inteira para um barramento de serviço ou um balanceador de carga com um nome virtual.

### Não use APIs de infraestrutura em seu app.

Se você conta com uma API de infraestrutura específica em seu app, mudar a infraestrutura é mais desafiador porque uma API de infraestrutura pode referir-se a muitas camadas diferentes em sua pilha de software.

É possível contar com produtos comerciais ou de software livre existentes e deixar as soluções PaaS na camada PaaS para mantê-las fora do seu código de app.

### Não use protocolos obscuros.

Não use protocolos obscuros que requeiram configuração extra para resiliência.

Os apps baseados em protocolos padrão são mais resilientes com os itens de configuração delegados para a plataforma. Os protocolos padrão incluem HTTP, SSL, banco de dados padrão, enfileiramento e conexões de serviço da web.

### Não conte com recursos específicos do S.O.

Se você já usou recursos específicos do sistema operacional, será possível corrigir esse problema usando bibliotecas de compatibilidade, por exemplo, Cygwin e Mono. Cygwin é uma biblioteca de compatibilidade que fornece um conjunto de ferramentas Linux em um ambiente do Windows. Mono é uma biblioteca de compatibilidade que fornece recursos .NET do Windows no Linux.

Evite as dependências específicas do sistema operacional; em vez disso, use serviços que sejam fornecidos pela infraestrutura de middleware ou por provedores de serviços.

### Não instale manualmente seu app.

Seu app pode ser instalado frequentemente sob demanda no ambiente de nuvem dinâmica. O processo de instalação deve ser por script e confiável, e os dados da configuração devem ser exteriorizados a partir dos scripts.

Capture sua instalação do aplicativo como um conjunto uniforme de scripts que são independentes do sistema operacional. Mantenha a instalação do app pequena e móvel para adaptar-se a diferentes técnicas de automação. Além disso, minimize as dependências que são requeridas pela instalação do app.

Para obter mais informações sobre apps prontos para nuvem, veja [O app de 12 fatores ![Ícone de link externo](../icons/launch-glyph.svg)](http://12factor.net/){: new_window}.

