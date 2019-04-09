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

# 在 {{site.data.keyword.containerlong_notm}} 上部署 Mendix 應用程式
{: #deploy-mendix-kube}

依預設，將部署目標設為 {{site.data.keyword.containerlong}} 的 Mendix 應用程式會以評估模式設定。此模式容許您快速開始建置應用程式並部署至雲端，但不會配置資料持續性或進階 Kubernetes 配置。本指導教學會引導您配置正式作業環境，方法是在 Kubernetes 使用 {{site.data.keyword.cos_full_notm}} 服務設定持續性儲存空間磁區。
{: shortdesc}

## 開始之前
{: #prereqs-mendix-kube}

- 建立 Mendix 應用程式。如需相關資訊，請參閱[建立 Mendix 應用程式](/docs/apps/tutorials/tutorial_mendix_getting_started.html#create-mendix)。
- 安裝 [{{site.data.keyword.dev_cli_notm}} 指令行介面 (CLI)](/docs/cli/index.html#overview)，這包含了 {{site.data.keyword.containershort_notm}} CLI。
- 登入 `ibmcloud` CLI 並配置 `kubectl` 以便[存取 Kubernetes 叢集](/docs/containers/cs_tutorials.html#cs_cluster_tutorial_lesson3)。

## 建立 Cloud Object Storage 服務實例
{: #cos-mendix-kube}

從應用程式詳細資料頁面開始，使用下列步驟：
1. 按一下**新增資源**。
2. 選取**儲存空間**，然後按**下一步**。
3. 接下來，選取 **Cloud Object Storage** 選項，然後按**下一步**。
4. 您會看到 {{site.data.keyword.cos_full_notm}} 實例的定價方案。請選取最符合您需要的定價方案，然後按一下**建立**，建立 {{site.data.keyword.cos_full_notm}} 服務的實例以便搭配 Mendix 應用程式使用。

  如果您喜好使用現有的 {{site.data.keyword.cos_full_notm}} 服務實例，請按一下**新增資源**，然後選取現有實例供您的應用程式使用。
  {: tip}

## 建立儲存空間儲存區
{: #storage-bucket-mendix-kube}

{{site.data.keyword.cos_full_notm}} 服務的實例與 Mendix 應用程式相關聯之後，您必須在可以建立儲存空間儲存區，然後便可以在其中儲存資料。若要建立儲存區，請按一下 {{site.data.keyword.cos_full_notm}} 實例的 **...**，然後選取**開啟儀表板**。  

{{site.data.keyword.cos_full_notm}} 服務儀表板會在新的視窗中開啟。在**儲存區**標籤上，按一下**建立儲存區**，然後遵循步驟以使用唯一名稱建立儲存區。針對本指導教學的目的，請建立稱為 `my-mendix-bucket` 的儲存區。

## 配置持續性儲存空間
{: #kube-storage-mendix}

接下來，遵循[在 {{site.data.keyword.cos_full_notm}} 上儲存資料](/docs/containers/cs_storage_cos.html#object_storage)的文件。會在您的 Kubernetes 叢集內建立 `PersistentVolumeClaim` 及 `PersistentVolume`，且可以供您叢集內執行的 PostGres 資料庫實例用於 Mendix 應用程式的一部分。請務必使用 `my-mendix-bucket` 儲存區建立 `PersistentVolumeClaim`，如前一步驟中所述，然後檢閱 `PersistentVolumeClaim` 名稱以便用於下一個步驟。

## 編輯 `postgres-deployment.yaml` 檔案
{: #postgres-deploy-mendix}

為您的 Kubernetes 叢集配置持續性磁區之後，下一步是修改您叢集內執行的 PostGres 資料庫部署。首先，您必須在 Git 儲存庫中編輯 IBM DevOps 工具鏈整合步驟中建立的檔案。若要尋找 Git 儲存庫，請回到應用程式詳細資料頁面，然後從**部署詳細資料**磚按一下 Git URL 鏈結。  

您可以將 Git 儲存庫複製到您的本端機器，或是在線上編輯器中進行下列變更。開啟 `chart/{app name}/templates/postgres-deployment.yaml` 檔案（請將 `{app name}` 取代為您的 Mendix 應用程式名稱）。依預設，檔案沒有任何現有 `volumeMount` 或 `volumes` 項目，因此所有資料會儲存在執行中部署 Pod 的記憶體內。您必須將 `volumeMount` 及 `volumes` 項目都新增至 Kubernetes `deployment.yaml` 檔，以便資料儲存至 {{site.data.keyword.cos_full_notm}} 儲存區，而且不會在 Pod 重新啟動時遺失。 

請參閱下列範例 `postgres-deployment.yaml`，它包含了 `volumeMount` 及 `volumes` 項目。  
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

請務必將 `{pvc-name}` 取代為上個步驟的 `PersistentVolumeClaim` 名稱，並且小心不要改寫應用程式名稱，應用程式名稱已經在 Git 儲存庫內的檔案中設定。然後，將您的變更確定回 Git 儲存庫。

## 重新部署
{: #redeploy-mendix-kube}

您的 `postgres-deployment.yaml` 檔案變更確定回儲存庫之後，會自動觸發新的 DevOps 管線執行。不過，它會再次部署預設應用程式。您必須重新部署最新版的 Mendix 應用程式，才能讓最新版的應用程式與最新的持續性磁區變更一起部署。

若要重新部署，請移至您的應用程式詳細資料頁面，然後在**部署詳細資料**磚內按一下**部署應用程式**。如果 DevOps 工具鏈內的部署失敗，並且發生指出找不到應用程式 `.mda` 檔的錯誤，則您必須重新從 Mendix 匯出。您可以從 Mendix Modeler 桌面應用程式匯出，或是按一下**在 Mendix 上編輯**來匯出。然後，在 Mendix Web 介面內，移至 **Environments** 區段並遵循您按一下 **Create package from teamserver** 之後的步驟。從 Mendix 匯出應用程式之後，請回到應用程式詳細資料頁面，然後重新按一次**部署應用程式**。最後一次匯出的應用程式會使用 {{site.data.keyword.cloud}} DevOps 工具鏈匯出到您的 Kubernetes 叢集。部署順利完成之後，您的應用程式便已執行並準備好供正式作業使用。

## 驗證應用程式正在執行
{: #verify-mendix-kube}

部署應用程式之後，Delivery Pipeline 或指令行會將您指向應用程式的 URL。

1. 從 DevOps 工具鏈中，按一下 **Delivery Pipeline**，然後選取**部署階段**。
2. 按一下**檢視日誌和歷程**。
3. 在日誌檔中，尋找應用程式 URL：

    在日誌檔結尾，搜尋單字 `urls` 或 `view`。例如，您可能會看到日誌檔中有一行類似 `urls: my-app-devhost.cloud.ibm.com` 或 `View the application health at: http://<ipaddress>:<port>/health`。

4. 在瀏覽器中移至 URL。如果應用程式正在執行，則會顯示包含 `Congratulations` 或 `{"status":"UP"}` 的訊息。

如果您要使用指令行，請執行 [`ibmcloud dev view`](/docs/cli/idt/commands.html#view) 指令來檢視應用程式的 URL。然後，在瀏覽器中移至 URL。

## 其他資訊
{: #more-info-mendix-kube}

如需在 Kubernetes 環境中執行 Mendix 應用程式的架構詳細資料，請檢閱 Mendix 使用者文件的 [Run Mendix on Kubernetes](https://docs.mendix.com/developerportal/deploy/run-mendix-on-kubernetes) 小節。
