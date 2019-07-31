---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-28"

keywords: databases, connections, scoring, requests

subcollection: ai-openscale

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:pre: .pre}
{:codeblock: .codeblock}
{:download: .download}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}
{:faq: data-hd-content-type='faq'}

# 데이터베이스 지정
{: #connect-db}

사용할 {{site.data.keyword.aios_short}} 인스턴스에 대한 데이터베이스를 지정하십시오.
{: shortdesc}

## 데이터베이스에 연결
{: #cdb-connect}

{{site.data.keyword.aios_short}}은 데이터베이스를 사용하여 페이로드, 피드백 및 측정치 데이터를 저장합니다. 데이터베이스 선택 외에 데이터베이스에 대한 스키마도 선택할 수 있습니다. 스키마란 데이터베이스 내에 있는 테이블의 이름 지정된 콜렉션입니다.

1.  데이터베이스를 선택하십시오. 무료 데이터베이스 또는 기존/신규 데이터베이스의 두 가지 옵션이 있습니다.

    ![데이터베이스 선택](images/gs-config-database.png)

    유료 {{site.data.keyword.cloud_notm}} 계정이 있는 경우, `Databases for PostgreSQL` 또는 `Db2 Warehouse` 서비스를 프로비저닝하여 Watson Studio 및 연속 학습 서비스와의 통합을 활용할 수 있습니다. 유료 서비스를 프로비저닝하지 않기로 선택하는 경우 무료 내부 PostgreSQL 스토리지를 {{site.data.keyword.aios_short}}과 함께 사용할 수 있으나 모델에 대한 연속 학습을 구성할 수 없습니다.
    {: note}

### 무료 Lite 플랜 데이터베이스
{: #cdb-lite}

**참고**: 무료 데이터베이스에는 몇 가지 중요한 제한사항이 있습니다.

- 무료 데이터베이스가 호스팅되며 사용자에 직접 액세스할 수 없습니다.
- {{site.data.keyword.aios_full}}은 데이터베이스에 대한 전체 액세스 권한을 갖고 있으므로 데이터에 대한 전체 액세스 권한을 가집니다.
- 무료 데이터베이스는 GDPR을 준수하지 않습니다. 모델이 PII(Personally-Identifiable Information)를 처리하는 경우 무료 데이터베이스를 사용할 수 없습니다. 새 데이터베이스를 구매하거나 GDPR 규칙을 준수하는 기존 데이터베이스를 사용해야 합니다. 자세한 내용은 [정보 보안](/docs/services/ai-openscale?topic=ai-openscale-is-ov)을 참조하십시오.

무료 데이터베이스를 계속 사용하려면 **무료 Lite 플랜 데이터베이스 사용** 타일을 클릭한 후 **저장**을 클릭하십시오. 

  ![데이터베이스 선택](images/gs-config-database2.png)
  
무료 데이터베이스에서 다른 데이터베이스로 업그레이드할 수 있지만 Compose for Postgres, Database for Postgres 또는 Db2 인스턴스를 무료 데이터베이스에 대해 재구성할 수는 없습니다. 업그레이드한 후에는 무료 데이터베이스를 사용하도록 돌아갈 수 없습니다. 구성, 스코어링 결과 및 설명과 같은 모든 최신 데이터를 재사용할 수 없습니다. 다른 스키마 또는 데이터베이스를 선택하면 {{site.data.keyword.aios_short}} 환경이 전체 다시 설정됩니다.



### 기존 또는 신규 데이터베이스
{: #cdb-exn}

1.  **기존 데이터베이스 사용 또는 신규 데이터베이스 구매** 옵션을 선택하면 {{site.data.keyword.aios_short}}은 사용자의 {{site.data.keyword.Bluemix_notm}} 계정을 확인하여 기존 데이터베이스를 찾습니다. 

1.  기존 데이터베이스 유형(Compose for Postgres, Database for Postgres 또는 Db2)을 선택한 다음 **데이터베이스** 드롭 다운 메뉴에서 데이터베이스를 선택하고 **스키마**를 선택하십시오.

    {{site.data.keyword.aios_short}}은 PostgreSQL 또는 Db2 데이터베이스를 사용하여 모델 관련 데이터(피드백 데이터, 스코어링 페이로드) 및 계산된 메트릭을 저장합니다. Lite Db2 플랜은 현재 지원되지 않습니다. 훈련 데이터에 대한 자세한 정보는 [{{site.data.keyword.aios_short}}에서 내 훈련 데이터에 액세스해야 하는 이유는 무엇입니까?](/docs/services/ai-openscale?topic=ai-openscale-trainingdata#trainingdata)를 참조하십시오.
    {: note}

    ![데이터베이스 선택](images/gs-config-database3.png)

1.  또한 **다른 위치 선택**을 클릭하여 {{site.data.keyword.Bluemix_notm}} 계정 외부의 데이터베이스 위치를 지정할 수 있습니다.

    {{site.data.keyword.aios_short}}은 PostgreSQL 또는 Db2 데이터베이스를 사용하여 모델 관련 데이터(피드백 데이터, 스코어링 페이로드) 및 계산된 메트릭을 저장합니다. Lite Db2 플랜은 현재 지원되지 않습니다.
    {: note}

    - **데이터베이스 유형**(`Compose for PostgreSQL`, `Database for PostgreSQL` 또는 `Db2`)를 선택한 다음 연결 정보를 제공하십시오.

        - `Compose for PostgreSQL` 데이터베이스의 경우, 다음을 완료하십시오.

            - 호스트 이름 또는 IP 주소
            - 포트
            - 데이터베이스(이름)
            - 사용자 이름
            - 비밀번호

        - `Database for PostgreSQL` 데이터베이스의 경우, 다음을 완료하십시오.

            - 호스트 이름 또는 IP 주소
            - SSL 포트
            - Base-64 인코딩 인증서
            - 데이터베이스(이름)
            - 사용자 이름
            - 비밀번호

        - `Db2` 데이터베이스의 경우, 다음을 완료하십시오.

            - 호스트 이름 또는 IP 주소
            - SSL 포트
            - 데이터베이스(이름)
            - 사용자 이름
            - 비밀번호

    - 연결되고 나면 스키마를 선택하고 작업을 저장할 수 있습니다. 

      액세스가 제한된 Db2 인스턴스를 제공하는 경우 스키마 이름이 명시적으로 제공되어야 하며 이로 인해 스키마 이름을 자동으로 생성하도록 허용되지 않습니다. 이는 Entry Db2 Warehouse 플랜에 적용됩니다.
      {: important}

## 다음 단계
{: #cdb-next}

이제 {{site.data.keyword.aios_short}}에서 [스코어링 페이로드를 전송](/docs/services/ai-openscale?topic=ai-openscale-connect-db#cdb-score)하고 [배치에 대한 모니터를 구성](/docs/services/ai-openscale?topic=ai-openscale-mo-config)할 준비가 되었습니다.