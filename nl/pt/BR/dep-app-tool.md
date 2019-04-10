---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-15"

keywords: apps, deploy, deploying apps, toolchains, cli

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Implementando apps
{: #deploying-apps}

É possível implementar seus apps com uma cadeia de ferramentas ou com a interface da linha de comandos (CLI). Uma cadeia de ferramentas é um conjunto de integrações de ferramentas. A CLI é uma maneira simples de implementar seus apps e instâncias de serviço.
{: shortdesc}

## Implementando apps usando cadeias de ferramentas
{: #toolchain-deploy-apps}

As cadeias de ferramentas abertas estão disponíveis nos ambientes Public e Dedicated no {{site.data.keyword.Bluemix}}. Com uma cadeia de ferramentas configurada corretamente, a implementação do app é fácil. Um ciclo de implementação de construção é iniciado automaticamente com cada mesclagem na ramificação principal em seu repositório.

É possível criar uma cadeia de ferramentas destas maneiras:
* Use um modelo para criar uma cadeia de ferramentas.
* Crie uma cadeia de ferramentas por meio de um app.

Para saber mais sobre cadeias de ferramentas, consulte [Criando cadeias de ferramentas](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started).

## Implementando apps usando a CLI
{: #cli-deploy-apps}

O {{site.data.keyword.cloud_notm}} fornece uma CLI robusta, além de plug-ins e extensões de ferramentas do desenvolvedor que se integram à CLI.

Antes de iniciar, [faça download e instale a CLI do {{site.data.keyword.cloud_notm}}](/docs/cli?topic=cloud-cli-ibmcloud-cli).

A CLI não é suportada pelo Cygwin. Use a ferramenta em uma janela diferente da janela de linha de comandos do Cygwin.
{: important}

  1. {: download} Faça download do código do app em um novo diretório para configurar seu ambiente de desenvolvimento.

    <a class="xref" href="https://{DomainName}" target="_blank" img class=“image” src=“images/btn_starter-code.svg” alt=“Download application code” title="(Abre em uma nova guia ou janela)"></a>

  2. Mude para o diretório no qual o seu código está localizado.

  <pre class="pre"><code class="hljs">cd <var class="keyword varname">your_new_directory</var></code></pre>

  3.  Faça mudanças em seu código de app. Por exemplo, se você estiver usando um aplicativo de amostra do {{site.data.keyword.cloud_notm}} e seu app contiver o arquivo `src/main/webapp/index.html`, será possível modificá-lo e editar a linha `Thanks for creating ...`. Assegure-se de que o app seja executado localmente antes de implementá-lo de volta no {{site.data.keyword.cloud_notm}}.

    Anote o arquivo `manifest.yml`. Ao implementar seu app de volta no {{site.data.keyword.cloud_notm}}, esse arquivo será usado para determinar a URL de seu aplicativo, a alocação de memória, o número de instâncias e outros parâmetros essenciais.

    Revise também o arquivo `README.md`, que contém detalhes, como instruções de construção, se aplicável.

  Caso seja um app Liberty, deve-se construí-lo antes que seja novamente implementado.
  {: note}

  4. Conecte e efetue login no {{site.data.keyword.cloud_notm}}.

  <pre class="pre"><code class="hljs">ibmcloud api https://api.<span class="keyword" data-hd-keyref="DomainName">DomainName</span></code></pre>

  <pre class="pre"><code class="hljs">ibmcloud login -u <var class="keyword varname" data-hd-keyref="user_ID">username</var> -o <var class="keyword varname" data-hd-keyref="org_name">org_name</var> -s <var class="keyword varname" data-hd-keyref="space_name">space_name</var></code></pre>

  Se você usar um ID federado, inclua a opção `-sso`.

  <pre class="pre"><code class="hljs">ibmcloud login -o <var class="keyword varname" data-hd-keyref="org_name">org_name</var> -s <var class="keyword varname" data-hd-keyref="space_name">space_name</var> -sso</code></pre>

  Caso o valor contenha um espaço, deve-se incluir aspas simples ou duplas ao redor de `username`, `org_name` e `space_name`, por exemplo, `-o "my org"`.
  {: note}

  5. Em seu novo diretório, implemente seu app no {{site.data.keyword.cloud_notm}} usando o comando `ibmcloud dev deploy`. Para obter mais informações, consulte [a documentação da CLI](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy).

  <pre class="pre"><code class="hljs"> ibmcloud dev deploy  <var class="keyword varname" data-hd-keyref="app_name"> app_name </var> </code></pre>

  6. Acesse o app em https://<var class="keyword varname" data-hd-keyref="app_url">app_url</var>.<span class="keyword" data-hd-keyref="APPDomain">AppDomainName</span>.
