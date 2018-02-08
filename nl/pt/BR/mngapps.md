---

copyright:
  years: 2015, 2017, 2018
lastupdated: "2018-01-18"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Verificando o status de seu app
{: #manageapps}

Seu painel no console do {{site.data.keyword.Bluemix}} fornece informações de resumo para os aplicativos que você criou. As informações de resumo incluem o nome, ícone, URL, tempo de execução, status de execução e instâncias de serviço que estão ligadas ao app.
{:shortdesc}

## Entendendo o status de seu app
{: #status}

Em seu painel, é possível visualizar o status de cada aplicativo:

<dl>
<dt>
<strong>
Interrompido ou desconhecido (cinza)
</strong>
</dt>
<dd>
Seu app está interrompido ou o status é desconhecido. O ícone cinza indica que o app está interrompido ou o status é desconhecido.
</dd>
<dt>
<strong>
Em execução (verde)
</strong>
</dt>
<dd>
Seu app está em execução. O ícone verde indica que o app está iniciado e todas as instâncias estão em execução.
</dd>
<dt>
<strong>
_Número_ em execução (amarelo)
</strong>
</dt>
<dd>
O app está iniciado, mas nem todas as instâncias estão em execução. O ícone amarelo indica que menos de 100% das instâncias estão em execução. O número de instâncias que estão em execução e o número de instâncias que
falharam são exibidos.
</dd>
<dt>
<strong>
Não em execução (vermelho)
</strong>
</dt>
<dd>
Seu app não está em execução. O ícone vermelho indica que o app está iniciado, mas nenhuma instância está em execução.
</dd>
</dl>

## Visualizando seu painel de detalhes do app
{: #viewingapps}

É possível visualizar mais informações sobre um app clicando no nome dele em seu painel. Em seguida, é possível ver a página Visão geral do app.

Na página Visão geral de apps, depois que um app é implementado, é possível iniciar, parar, reiniciar ou, no caso de aplicativos da web, modificar o número de instâncias e a quantia de memória que é usada pelo app. Para aplicativos da web, o {{site.data.keyword.Bluemix_notm}} não escala automaticamente seus apps com base em sua carga, então deve-se gerenciar isso sozinho.

Os apps poderão ser reimplementados se uma atualização for feita. O mecanismo para atualizar o app é o mesmo mecanismo que é usado para implementá-lo originalmente. {{site.data.keyword.Bluemix_notm}} para todas as instâncias em execução
e as substitui por novas instâncias automaticamente.
