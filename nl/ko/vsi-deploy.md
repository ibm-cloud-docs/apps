---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-29"

keywords: apps, deploy, virtual server, App Service, vsi, virtual machine, delivery pipeline, virtual deployment

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
{:table: .aria-labeledby="caption"}

# 가상 서버에 배치
{: #vsi-deploy}

종량과금제 계정이 있으면 {{site.data.keyword.cloud}} [앱 서비스](https://{DomainName}/developer/appservice/starter-kits){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")를 사용하여 가상 서버 인스턴스를 포함하여 여러 유형의 환경에 앱을 배치할 수 있습니다. 가상 서버 인스턴스는 온프레미스 워크로드를 클라우드로 이동할 때의 일반적인 배치 선택사항이며 베어메탈 머신을 에뮬레이트합니다.
{: shortdesc}

가상 서버 인스턴스는 다른 구성과 비교할 때 모든 워크로드 유형에 대해 더 나은 투명성, 예측 가능성 및 자동화를 제공합니다. 고유 워크로드 조합을 작성하려면 이를 베어메탈 서버와 결합하십시오. 예를 들어, Debian Linux 기반 운영 체제를 실행하는 베어메탈 및 GPU 구성을 사용하여 고성능 데이터베이스 로직 또는 기계 학습을 작성할 수 있습니다.

가상 서버 인스턴스를 프로비저닝하고 배치하는 작업은 복잡하고 시간이 많이 걸리는 프로세스지만 {{site.data.keyword.cloud_notm}} 앱 서비스를 사용하면 이를 신속하게 시작하고 실행할 수 있습니다.

서비스는 가상 서버 인스턴스에 바인드되지 않습니다. 가상 서버의 애플리케이션에는 서비스를 추가할 수 없습니다.
{: important}

## 앱 작성 및 배치
{: #create-deploy-vsi}

앱 서비스는 가상 서버를 사용자에 맞게 프로비저닝하고 앱이 포함된 이미지를 로드하며 Devops 도구 체인을 작성하고 첫 번째 배치 사이클을 시작합니다.

1. [앱을 작성](/docs/apps?topic=creating-apps-tutorial-scratch#tutorial-scratch)하십시오. 
2. **앱 세부사항** 페이지에서 **지속적 딜리버리 구성**을 클릭하십시오.
3. 서버를 실행할 지역과 함께 **가상 서버에 배치**를 선택하십시오.

## 배치 프로세스 작동 방식

가상 서버 배치 프로세스는 Terraform, 파이프라인 인에이블먼트, API 키 관리(Git 오퍼레이션) 및 도구 체인 프로세스에 대한 이해 등이 포함된 몇 가지 주요 기술로 구성됩니다. 

### Terraform을 통해 배치

오픈 소스 IaC(Infrastructure as Code) 프레임워크인 [Terraform](https://ibm-cloud.github.io/tf-ibm-docs/v0.10.0/){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")을 통해 앱 서비스 스타터 킷을 동적으로 작성된 가상 인스턴스에 배치할 수 있습니다. 

### 파이프라인 배치 사용

{{site.data.keyword.cloud_notm}} [앱 서비스](https://{DomainName}/developer/appservice/starter-kits){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")를 사용하는 스타터 킷을 작성할 때 가상 서버 인스턴스가 사용으로 설정됩니다. 앱이 작성된 후 앱을 배치할 위치를 선택할 수 있습니다. 스타터 킷은 Continuous Delivery 도구 체인을 사용하여 배치를 지원할 수 있습니다. 스타터 킷은 Kubernetes, Cloud Foundry 및 가상 서버 인스턴스를 대상으로 할 수 있습니다. 이 도구 체인에는 소스 코드 저장소 및 배치 파이프라인이 포함되어 있습니다.

가상 서버 옵션은 단계적으로 작동합니다. 먼저, 앱 코드가 준비되어 GitLab Git 저장소에 저장되며 소스 코드가 파이프라인을 사용하여 도구 체인을 작성합니다. 코드를 빌드하여 Debian 패키지 관리자 형식으로 패키징하기 위한 파이프라인이 정의됩니다. 그런 다음, Terraform이 가상 인스턴스를 프로비저닝합니다. 마지막으로, 실행 중인 가상 이미지 내부에 앱이 배치, 설치 및 시작되고 해당 상태의 유효성이 검증됩니다.

파이프라인에서는 사용자 계정 특성 세트 및 신규 SSH 키 쌍을 사용하여 인프라를 배치합니다. 이러한 특성이 자동으로 도구 체인에 전달되지만 보안을 위해 Git 소스 코드에 저장되지는 않습니다.

이러한 환경 특성을 보려면 다음 단계를 완료하십시오. 

1. 앱 세부사항 페이지에서 **도구 체인 보기**를 클릭하십시오.
2. **Delivery Pipeline** 타일을 클릭하십시오.
3. **단계 구성** 아이콘을 클릭한 다음 빌드 단계에서 **단계 구성**을 클릭하십시오.
4. **환경 특성** 탭을 클릭하여 특성을 확인하십시오. 사용 가능한 특성에 대해 알아보려면 다음 표를 참조하십시오.

|특성  |설명  |
|-----------|--------------|
| `TF_VAR_ibm_sl_api_key` | [인프라 API 키](/docs/apps?topic=creating-apps-vsi-deploy#iaas-key)는 클래식 인프라 콘솔에서 가져옵니다. |
| `TF_VAR_ibm_sl_username` |클래식 인프라 계정을 식별하는 [인프라 사용자 이름](/docs/apps?topic=creating-apps-vsi-deploy#user-key)입니다. |
| `TF_VAR_ibm_cloud_api_key` | {{site.data.keyword.cloud_notm}} [API 키](/docs/apps?topic=creating-apps-vsi-deploy#platform-key)는 서비스 작성을 사용으로 설정하는 데 사용됩니다. |
| `PUBLIC_KEY` |가상 서버 인스턴스에 액세스할 수 있도록 정의된 [공개 키](/docs/apps?topic=creating-apps-vsi-deploy#public-key)입니다. |
| `PRIVATE_KEY` |가상 서버 인스턴스에 액세스할 수 있도록 정의된 [개인 키](/docs/apps?topic=creating-apps-vsi-deploy#public-key)입니다. `\n` 줄 바꾸기 스타일 형식을 사용해야 합니다. |
| `VI_INSTANCE_NAME` | 가상 서버 인스턴스에 대한 자동 생성 이름입니다. |
| `GIT_USER` |apply 명령의 상태를 저장하도록 [Terraform 상태](/docs/apps?topic=creating-apps-vsi-deploy#tform-state)를 설정한 경우 GitLab 사용자 이름이 필요합니다. |
| `GIT_PASSWORD` |apply 명령의 상태를 저장하도록 [Terraform 상태](/docs/apps?topic=creating-apps-vsi-deploy#tform-state)를 설정한 경우 GitLab 비밀번호가 필요합니다. |
{: caption="표 1. 사용을 위해 변경할 환경 변수" caption-side="top"}


#### 클래식 인프라 API 키
{: #iaas-key}

Terraform은 인프라 리소스를 작성하는 데 클래식 인프라 API 키를 필요로 합니다. API 키는 배치 중에 자동으로 확보됩니다. 키를 수동으로 검색하려면 다음 단계를 완료하십시오.

1. [사용자 목록](https://{DomainName}/iam#/users){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")으로 이동하십시오. **관리** > **액세스(IAM)**를 클릭하고 **사용자**를 선택할 수도 있습니다.
2. 사용자 이름을 클릭한 후 **사용자 세부사항**을 클릭하십시오.
3. API 키 섹션에서 **클래식 인프라 키 추가**를 클릭하십시오.
4. API 키 `TF_VAR_ibm_sl_api_key`를 복사하거나 다운로드하고 이를 안전한 곳에 저장하십시오. **조치** ![조치 목록 아이콘](../icons/action-menu-icon.svg) 메뉴에서 **세부사항 보기** 옵션을 사용하여 나중에 API 키의 세부사항을 검색할 수 있습니다.
5. 복사된 API 사본 값을 도구 체인 구성에 붙여넣어 `TF_VAR_ibm_sl_api_key`를 대체하십시오.

자세한 정보는 [클래식 인프라 API 키 관리](/docs/iam?topic=iam-classic_keys#classic_keys) 및 [클래식 인프라 권한](/docs/iam?topic=iam-infrapermission#infrapermission)을 참조하십시오.

#### 클래식 인프라 사용자 이름
{: #user-key}

클래식 인프라 사용자 이름도 배치 중에 자동으로 확보되어 사용됩니다. 사용자 이름을 수동으로 확보하려면 다음 단계를 완료하십시오.

1. [사용자 목록](https://{DomainName}/iam#/users){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")으로 이동하십시오. **관리** > **액세스(IAM)**를 클릭하고 **사용자**를 선택할 수도 있습니다.
2. 사용자 이름을 클릭한 후 **사용자 세부사항**을 클릭하십시오.
3. **VPN 사용자 이름** 특성을 찾으십시오.
4. 이 값을 잘라내어 붙여넣고 도구 체인 구성 `TF_VAR_ibm_sl_username`을 대체하십시오.

#### {{site.data.keyword.cloud_notm}} API 키
{: #platform-key}

Terraform에서 데이터베이스 및 Compose 서비스와 같은 플랫폼 레벨 서비스를 작성하려는 경우 {{site.data.keyword.cloud_notm}} API 키는 자동으로 확보되어 파이프라인에 환경 변수로서 저장됩니다. {{site.data.keyword.cloud_notm}} API 키를 수동으로 검색하려면 다음 단계를 완료하십시오.

1. [사용자 목록](https://{DomainName}/iam#/users){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")으로 이동하십시오. **관리** > **액세스(IAM)**를 클릭하고 **사용자**를 선택할 수도 있습니다.
2. 사용자 이름을 클릭한 후 **사용자 세부사항**을 클릭하십시오.
3. API 키 섹션을 찾고 **IBM Cloud API 키 작성**을 클릭하십시오.
4. 이름과 설명을 입력하고 **작성**을 클릭하십시오.
5. 창이 열리면 **표시**를 클릭하여 키를 검토하십시오.
6. 키를 복사하여 클립보드에 붙여넣거나 키를 다운로드하십시오.
7. 도구 체인 구성 `TF_VAR_ibm_cloud_api_key`의 값을 생성된 값으로 대체하십시오.

#### 공개 키와 개인 키
{: #public-key}

도구 체인이 Debian 패키징을 가상 서버 인스턴스에 설치할 수 있도록 배치 인프라가 자동으로 개인 및 공개 SSH 키 쌍을 생성하여 Git 컨텐츠를 인스턴스에 전송합니다.

이를 수동으로 수행하려면 다음을 수행하십시오.
1. 클라이언트에서 다음 지시사항을 사용하여 [공개 및 개인 키 쌍](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")을 작성하십시오.
2. [인프라 SSH 키 보기](https://{DomainName}/iam/#/users){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")로 이동하십시오. **메뉴** > **클래식 인프라** > **디바이스** > **관리** > **SSH 키**를 클릭할 수도 있습니다.
3. **추가**를 클릭하십시오.
4. 이전에 작성한 공개 키의 컨텐츠를 복사하여 키 컨텐츠에 붙여넣으십시오.
5. 키 이름을 지정하고 **추가**를 클릭하십시오.

개인 키는 한 줄로 되어 있어야 합니다. 새 줄은 `\n`로 대체하십시오. 다음 예제를 참조하십시오.
{: tip}

```
---------BEGIN RSA KEY----------\nasdfasdfeqwtqf13rf1eqwfwe\netq3efaewf23fa23f23f\n.....\n----------END RSA KEY-------------
```
{: screen}

#### Terraform 상태 사용
{: #tform-state}

Terraform은 Terraform `apply` 명령의 상태를 저장하도록 지원합니다. 이 상태 파일은 `apply` 명령을 두 번 실행하여 Terraform 구성 파일이 변경되었는지 여부를 판별합니다. 앱 및 구성이 자동으로 설정된 Git 저장소에 상태가 저장됩니다.

상태 스토리지를 사용으로 설정하기 위해 `GIT_USER` 및 `GIT_PASSWORD`가 자동으로 도구 체인 환경 변수에 특성으로 구성됩니다. 이러한 값에 액세스해야 하는 경우 다음 단계를 따르십시오.

1. 도구 체인 보기의 코드 도구에서 Git 저장소에 액세스하십시오.
2. GIT Lab에서 **프로파일 아이콘**을 클릭한 후 **설정**을 클릭하십시오.
3. **계정**을 클릭하고 사용자 이름을 복사한 후 `GIT_USER` 값을 대체하십시오.
4. **액세스 토큰**을 클릭하십시오.
5. 토큰의 이름을 정의한 후 범위를 선택하고 **개인 액세스 토큰 작성**을 클릭하십시오.
6. `새 개인 액세스 토큰` 필드에서 **복사**를 클릭하고 도구 체인 특성의 `GIT_PASSWORD` 값을 대체하십시오.

Terraform 상태가 `terraform`이라는 분기에 저장되며, 변경된 경우 파이프라인이 실행되도록 트리거하지 않습니다.

### Git 오퍼레이션 사용
{: #git-repo-vsi}

앱이 {{site.data.keyword.cloud_notm}}에 배치될 때 소스 코드 관리용 코드를 호스팅하기 위한 GitLab 저장소가 작성됩니다. Git 오퍼레이션을 사용하여 팀에서 작업하고 앱에 변경사항을 전달하도록 할 수 있습니다. 다음은 이 저장소에 포함된 폴더와 해당 컨텐츠에 대한 설명입니다.

#### Debian 폴더
{: #debian-folder}

`debian` 폴더에는 앱을 [Debian 패키지](https://www.debian.org/doc/manuals/debian-faq/ch-pkgtools.en.html){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")로 패키징할 수 있도록 하는 데 필요한 구성이 포함되어 있습니다.

#### Terraform 폴더
{: #terraform-folder}

`terraform` 폴더에는 인프라에 대한 구성이 인프라 리소스를 프로비저닝하는 데 사용될 수 있는 코드로 포함되어 있습니다. `main.tf` 파일은 Terraform 구성에 대한 옵션을 변경하기 위한 기본 소스입니다.

```json
resource "ibm_compute_vm_instance" "vm1" {
    hostname = "${var.vi_instance_name}"
    domain = "example.com"
    os_reference_code = "DEBIAN_8_64"
    datacenter = "${var.datacenter}"
    network_speed = 100
    hourly_billing = true
    private_network_only = false
    cores = 1
    memory = 1024
    disks = [25]
    local_disk = false
    ssh_key_ids = [
        "${ibm_compute_ssh_key.ssh_key_gip.id}"
    ]
}
```

Terraform으로 베어메탈 서버를 프로비저닝할 수도 있습니다. 자세한 정보는 [IBM Terraform 제공자 문서](https://ibm-cloud.github.io/tf-ibm-docs/v0.10.0/){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘") 및 [IBM Terraform 제공자 GIT 저장소](https://github.com/IBM-Cloud/terraform-provider-ibm){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")를 참조하십시오.

`variables.tf`를 사용하여 가상 인스턴스를 작성하기 위한 대상으로 지정할 데이터 센터를 변경할 수 있습니다. 플랫폼에 대해 정의된 데이터 센터의 목록을 보려면 [데이터 센터](https://www.ibm.com/cloud-computing/bluemix/data-centers){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")를 참조하십시오.

기본적으로 워싱턴 및 `wdc04`에 대한 Terraform 파일이 구성됩니다.
```json
variable "datacenter" {
  description = "Washington"
  default = "wdc04"
}
```

### 도구 체인 단계 이해
{: #toolchain-stages-vsi}

도구 체인은 인프라 및 앱 배치를 하나의 단순 파이프라인에 표시합니다. IaC(Infrastructure as Code) 파트를 하나의 파이프라인으로 구분하고 앱 배치를 다른 파이프라인으로 구분하십시오.

도구 체인 프로세스는 5단계로 구성됩니다.

1. 빌드 단계는 Git 저장소를 복제하고 코드를 Debian 패키지로 패키징합니다.
2. Terraform 플랜 단계는 Terraform 플랜을 준비합니다.
  ```console
  terraform init -input=false
  terraform validate
  terraform plan -var "ssh_public_key=$PUBLIC_KEY" -input=false -out tfplan
  ```

3. Terraform 적용 단계에서는 Terraform 구성을 적용하고 가상 서버의 IP 주소가 사용 가능하게 될 때까지 대기합니다.

  ```console
  terraform apply -auto-approve -input=false tfplan
  terraform output "host ip" > hostip.txt
  ```

4. 배치, 설치 및 시작 단계에서는 첫 번째 단계에서 빌드된 Debian 패키지를 실행 중인 가상 서버로 이동하여 해당 패키지를 설치한 후 시작합니다.
5. 상태 검사 단계에서는 상태 엔드포인트가 앱에서 사용 가능한지 유효성 검사한 후 파이프라인을 완료합니다.

앱이 시작된 후 앱에 액세스하려면 상태 검사 단계의 로그를 확인하십시오. 로그에 나열된 URL 링크를 클릭하십시오. URL 링크는 앱의 IP 주소 및 포트를 표시합니다.
