---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-13"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Implementando o aplicativo Mendix no {{site.data.keyword.containerlong_notm}}
{: #deploy-mendix-kube}

Por padrão, os aplicativos Mendix que direcionam a implementação para o {{site.data.keyword.containerlong}} são configurados em um modo de avaliação. Esse
modo permite iniciar rapidamente a construção de um aplicativo e implementá-lo na nuvem, mas não configura a
persistência de dados ou as configurações avançadas do Kubernetes. Esse tutorial orienta a configuração de um
ambiente de produção, definindo um volume de armazenamento persistente no Kubernetes com o serviço do {{site.data.keyword.cos_full_notm}}.
{: shortdesc}

## Antes de começar
{: #prereqs-mendix-kube}

- Crie o aplicativo Mendix. Consulte
[Criando aplicativos Mendix](/docs/apps/tutorials/tutorial_mendix_getting_started.html#create-mendix) para obter
mais informações.
- Instale a [{{site.data.keyword.dev_cli_notm}}interface da linha de
comandos (CLI)](/docs/cli/index.html#overview), que inclui a CLI do {{site.data.keyword.containershort_notm}}.
- Efetue login na CLI do `ibmcloud` e configure `kubectl` para o
[ acesso ao cluster do Kubernetes](/docs/containers/cs_tutorials.html#cs_cluster_tutorial_lesson3).

## Criando uma instância de serviço do Cloud Object Storage
{: #cos-mendix-kube}

Inicie na página de detalhes do aplicativo e use as etapas a seguir:
1. Clique em **Incluir recurso**.
2. Selecione **Armazenamento** e clique em **Avançar**.
3. Em seguida, selecione a opção **Cloud Object Storage** e clique em **Avançar**.
4. Os planos de precificação para a instância do {{site.data.keyword.cos_full_notm}} são exibidos. Selecione o plano de precificação que melhor se ajuste às suas necessidades e, em seguida, clique em **Criar** para criar uma instância do serviço do {{site.data.keyword.cos_full_notm}} para usar com o aplicativo Mendix.

  Se você prefere usar uma instância existente do serviço do {{site.data.keyword.cos_full_notm}}, clique em **Incluir recurso** e selecione a instância existente para o uso do aplicativo.
  {: tip}

## Criando um depósito de armazenamento
{: #storage-bucket-mendix-kube}

Depois que uma instância do serviço do {{site.data.keyword.cos_full_notm}} estiver associada ao aplicativo Mendix, crie um depósito de armazenamento no qual os dados podem ser salvos. Para criar um depósito, clique em **...** para a instância do {{site.data.keyword.cos_full_notm}} e selecione **Abrir painel**.  

O painel de serviço do {{site.data.keyword.cos_full_notm}} se abre em uma nova janela, na guia **Depósitos**. Clique em **Criar depósito** e siga as etapas para criar um depósito usando um nome exclusivo. Para os propósitos deste tutorial, crie um depósito chamado `my-mendix-bucket`.

## Configurando o armazenamento persistente
{: #kube-storage-mendix}

Em seguida, siga a documentação para [Armazenando dados no {{site.data.keyword.cos_full_notm}}](/docs/containers/cs_storage_cos.html#object_storage). Um `PersistentVolumeClaim` e um `PersistentVolume` são criados dentro do cluster do Kubernetes e podem ser usados pela instância de banco de dados do PostGres que está em execução no cluster como parte do aplicativo Mendix. Certifique-se de criar o `PersistentVolumeClaim` usando o depósito `my-mendix-bucket`, conforme descrito na etapa anterior, e revisar o nome `PersistentVolumeClaim` para usar na próxima etapa.

## Editando o arquivo `postgres-deployment.yaml`
{: #postgres-deploy-mendix}

Após a configuração de um volume persistente para o cluster do Kubernetes, a próxima etapa é modificar a implementação do banco de dados do PostGres que está em execução no cluster. Primeiro, deve-se editar os arquivos no repositório Git que foi criado como parte da etapa de integração da cadeia de ferramentas do IBM DevOps. Para localizar o repositório Git, volte para a página de detalhes do aplicativo e clique no link da URL do Git por meio do bloco **Detalhes da implementação**.  

É possível clonar o repositório Git para a máquina local ou fazer as mudanças a seguir no editor on-line. Abra o
arquivo `chart/{app name}/templates/postgres-deployment.yaml` (substitua `{app
name}` pelo nome do aplicativo Mendix). O arquivo não tem nenhuma entrada `volumeMount` ou `volumes` existente por padrão, portanto, todos os dados são armazenados na memória dentro do
pod de implementação em execução. Deve-se incluir as entradas `volumeMount` e `volumes` no arquivo `deployment.yaml` do Kubernetes para que os dados sejam salvos no depósito
do {{site.data.keyword.cos_full_notm}} e não sejam perdidos se o pod reiniciar. 

Consulte o `postgres-deployment.yaml` de amostra a seguir que inclui as entradas
`volumeMount` e `volumes`.  
```yaml
apiVersion: apps/v1beta1
kind: Deployment
metadata:
  name: "{appname}-postgres"
spec:
  replicas: 1
  template:
    metadata:
      labels:
        service: "{appname}-postgres"
    spec:
      containers:
        - name: "{appname}-postgres"
          image: postgres:10.1
          ports:
            - containerPort: 5432
          env:
            - name: POSTGRES_DB
              value: db0
            - name: POSTGRES_USER
              value: mendix
            - name: POSTGRES_PASSWORD
              value: mendix
          volumeMounts:
            - mountPath: "/var/lib/postgresql/data"
              name: "mendix-data"
      volumes:
        - name: mendix-data
          persistentVolumeClaim:
            claimName: {pvc-name}
```

Certifique-se de substituir `{pvc-name}` pelo nome do `PersistentVolumeClaim` da
etapa anterior e tenha cuidado para não sobrescrever o nome do aplicativo, que já está configurado no arquivo dentro do repositório Git. Em seguida, confirme as mudanças de volta ao repositório Git.

## Reimplementando
{: #redeploy-mendix-kube}

Após a confirmação das mudanças do arquivo `postgres-deployment.yaml` de volta
ao repositório, uma nova execução do pipeline do DevOps será acionada automaticamente. No entanto, o
aplicativo padrão é implementado novamente. Deve-se reimplementar a versão mais recente do aplicativo Mendix para que
ela seja implementada com as mudanças de volume persistentes mais recentes.

Para reimplementar, acesse a página de detalhes do aplicativo e clique em **Implementar
aplicativo** dentro do bloco **Detalhes da implementação**. Se a implementação falhar
dentro da cadeia de ferramentas do DevOps com um erro que indica que o arquivo `.mda` do aplicativo
não pode ser localizado, então, ele deverá ser exportado do Mendix novamente. É possível exportar por meio do aplicativo
para desktop do Mendix Modeler ou clicando em **Editar no Mendix**. Em seguida, na interface
da web do Mendix, acesse a seção **Ambientes** e siga as etapas depois de clicar em **Criar
pacote por meio do servidor de equipe**. Depois que o aplicativo for exportado do Mendix, volte para a
página de detalhes do aplicativo e clique em **Implementar aplicativo** novamente. O último
aplicativo exportado é implementado para o cluster do Kubernetes usando a cadeia de ferramentas do DevOps
do {{site.data.keyword.cloud}}. Quando a implementação for concluída com êxito, o aplicativo estará ativo
e pronto para o uso de produção.

## Verificando se o seu app está em execução
{: #verify-mendix-kube}

Após você implementar o seu app, o Delivery Pipeline ou a linha de comandos apontará a você a URL para o seu app.

1. Na cadeia de ferramentas do seu DevOps, clique em **Delivery Pipeline** e, em seguida, selecione **Implementar estágio**.
2. Clique em **Visualizar logs e histórico**.
3. No arquivo de log, localize a URL do aplicativo:

    No término do arquivo de log, procure a palavra `urls` ou `view`. Por exemplo, você pode ver uma linha no arquivo de log que é semelhante a `urls: my-app-devhost.cloud.ibm.com` ou `View the application health at: http://<ipaddress>:<port>/health`.

4. Acesse a URL em seu navegador. Se o app estiver em execução, uma mensagem que incluirá `Parabéns` ou `{"status":"UP"}` será exibida.

Se você estiver usando a linha de comandos, execute o comando [`ibmcloud dev view`](/docs/cli/idt/commands.html#view) para visualizar a URL de seu app. Em seguida, acesse a URL em seu navegador.

## Informações adicionais
{: #more-info-mendix-kube}

Para obter mais detalhes arquiteturais sobre como executar os aplicativos Mendix em ambientes do Kubernetes,
revise a seção [Executar o Mendix no
Kubernetes](https://docs.mendix.com/developerportal/deploy/run-mendix-on-kubernetes) da documentação do usuário do Mendix.
