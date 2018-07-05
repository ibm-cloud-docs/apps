---
copyright:

  years: 2018

lastupdated: "2018-06-25"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Implementando apps
{: #deploy}

É possível implementar seus apps com uma cadeia de ferramentas ou uma interface da linha de comandos. Uma cadeia de ferramentas é um conjunto de integrações de ferramentas. A interface da linha de comandos é uma maneira simples de implementar seus apps e instâncias de serviço.
{: shortdesc}

## Implementando apps com cadeias de ferramentas
{: #toolchains_getting_started}

As cadeias de ferramentas abertas estão disponíveis nos ambientes Public e Dedicated no {{site.data.keyword.Bluemix}}. É possível criar uma cadeia de ferramentas de duas formas: usar um modelo para criar uma cadeia de ferramentas ou criar uma cadeia de
ferramentas a partir de um app. Para saber mais sobre cadeias de ferramentas, veja [Criando cadeias de ferramentas](../services/ContinuousDelivery/toolchains_working.html#toolchains_getting_started)

Com uma cadeia de ferramentas configurada adequadamente, a implementação de seu app é trivial: um ciclo de construção/implementação será iniciado automaticamente com cada mesclagem para a ramificação principal em seu repositório.

Todas as cadeias de ferramentas criadas por meio de um painel do desenvolvedor do {{site.data.keyword.Bluemix}} são configuradas para implementação automática.
{: tip}

## Implementando aplicativos com a interface da linha de comandos
{: #cli}

O IBM Cloud fornece uma CLI robusta, bem como plug-ins e extensões de ferramentas do desenvolvedor que se integram com a CLI.

Use a interface da linha de comandos do {{site.data.keyword.Bluemix_notm}} para implementar seus aplicativos e instâncias de serviço.
{:shortdesc}

Antes de iniciar, faça download e instale a interface da linha de comandos do {{site.data.keyword.Bluemix_notm}}.

<p>
<a class="xref" href="https://console.bluemix.net/docs/cli/index.html#overview" target="_blank" title="(Abre em uma nova guia ou janela)"><img class="image" src="images/btn_bx_commandline.svg" alt="Fazer download do IBM Cloud Developer Tools" /></a>
</p>

**Restrição:** a ferramenta de linha de comandos não é suportada por Cygwin. Use a ferramenta em uma janela de linha de comandos diferente da janela de linha de comandos do Cygwin.
{:prereq}

Após a instalação da interface da linha de comandos, é possível iniciar:

  1. {: download} Faça download do código do app em um novo diretório para configurar seu ambiente de desenvolvimento.

    <a class="xref" href="http://bluemix.net" target="_blank" img class=“image” src=“images/btn_starter-code.svg” alt=“Download application code” title="(Abre em uma nova guia ou janela)"></a>

  2. Mude para o diretório no qual o seu código está localizado.

  <pre class="pre"><code class="hljs">cd <var class="keyword varname">your_new_directory</var></code></pre>

  3.  Faça mudanças em seu código de app. Por exemplo, se você estiver usando um aplicativo de amostra do {{site.data.keyword.Bluemix_notm}} e seu app contiver o arquivo `src/main/webapp/index.html`, será possível modificá-lo e editar "Obrigado por criar..." para dizer algo novo. Assegure-se de que o app seja executado localmente antes de implementá-lo de volta no {{site.data.keyword.Bluemix_notm}}.

    Anote o arquivo `manifest.yml`. Ao implementar seu app de volta no {{site.data.keyword.Bluemix_notm}}, esse arquivo será usado para determinar a URL de seu aplicativo, a alocação de memória, o número de instâncias e outros parâmetros essenciais.

    Preste atenção também no arquivo `README.md`, que contém detalhes como instruções de construção, se aplicável.

    Nota: caso seu aplicativo seja um app Liberty, deve-se construí-lo antes da reimplementação.

  4. Conecte e efetue login no {{site.data.keyword.Bluemix_notm}}.

  <pre class="pre"><code class="hljs">ibmcloud api https://api.<span class="keyword" data-hd-keyref="DomainName">DomainName</span></code></pre>

  <pre class="pre"><code class="hljs">ibmcloud login -u <var class="keyword varname" data-hd-keyref="user_ID">username</var> -o <var class="keyword varname" data-hd-keyref="org_name">org_name</var> -s <var class="keyword varname" data-hd-keyref="space_name">space_name</var></code></pre>

  Se você usar um ID federado, inclua a opção `-sso`.

  <pre class="pre"><code class="hljs">ibmcloud login -o <var class="keyword varname" data-hd-keyref="org_name">org_name</var> -s <var class="keyword varname" data-hd-keyref="space_name">space_name</var> -sso</code></pre>

  **Nota**: quando o valor contém um espaço, deve-se incluir aspas simples ou duplas ao redor de `username`, `org_name` e `space_name`, por exemplo, `-o "my org"`.

  5. Por meio do <var class="keyword varname">your_new_directory</var>, reimplemente o seu app no {{site.data.keyword.Bluemix_notm}} usando o comando `ibmcloud app push`. Para obter mais informações sobre o comando `ibmcloud app push`, veja [Fazendo upload de seu aplicativo](/docs/starters/upload_app.html).

  <pre class="pre"><code class="hljs">ibmcloud app push <var class="keyword varname" data-hd-keyref="app_name">app_name</var></code></pre>

  6. Acesse seu app procurando https://<var class="keyword varname" data-hd-keyref="app_url">app_url</var>.<span class="keyword" data-hd-keyref="APPDomain">AppDomainName</span>.
