---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-28"

keywords: credentials, REST API, data mart

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

# {{site.data.keyword.aios_short}} の資格情報の作成
{: #cred-create}

{{site.data.keyword.aios_full}} REST API にアクセスするには、プラットフォーム API キーとデータマート (サービス・インスタンスとも呼ばれる) ID が必要です。 プラットフォーム API キーによって、各ユーザーは {{site.data.keyword.cloud_notm}} 内のリソースにアクセスできるようになります。
{: shortdesc}

エンタープライズ・アカウントの場合、管理者がデータマートを作成し、ユーザーをそのアカウントに招待し、それらのユーザーに特定の {{site.data.keyword.aios_short}} データマートへのアクセス権を付与できます。 その後、ユーザーは自身のプラットフォーム API キーを作成し、同じ {{site.data.keyword.aios_short}} データマートにアクセスできます。 そのため、競合やセキュリティー・リスクは生じません。

## プラットフォーム API キーの作成
{: #cred-create-apikey}

プラットフォーム API キーを作成するには、以下の手順を実行します。

1. [{{site.data.keyword.cloud_notm}}](https://{DomainName}){: external} にログインします。

2. **「管理」**-->**「セキュリティー」**-->**「プラットフォーム API キー」**の順に選択します

    ![プラットフォーム API キー](images/cred-api-key.png)

3. プラットフォーム API キーを作成して保存します。

データマート (またはサービス・インスタンス) ID を検出するには、次のようにします。

1. モデル・デプロイメント・タイルをクリックします。
2. **「構成」**![構成アイコン](images/configure-deployment-button.png) アイコンをクリックします。
3. **「ペイロード・ロギング・エンドポイントの表示」**をクリックします。
4. {{site.data.keyword.aios_short}}の**「ペイロード・ロギング (Payload logging)」**ページで、**「データマート ID」**フィールドを見つけます。

    ![データマート ID](images/data-mart-id.png)

## コマンド・コンソールを使用したサービス・インスタンス資格情報の作成
{: #cred-creds}

{{site.data.keyword.aios_short}} の資格情報を作成するには、{{site.data.keyword.cloud_notm}} [コマンド・コンソール](/docs/cli?topic=cloud-cli-ibmcloud-cli)を使用して、以下の手順を実行します。

1. 以下のコマンドを実行して、API キーを取得します。

    ```curl
    ibmcloud login --sso
    ibmcloud iam api-key-create 'my_key'
    ```

    次の情報が表示されます。

    ```bash
    Name         my_key
    Created At   2018-10-09T14:04+0000
    API Key      Tg4Gxxxxxxxxxxxxxxxxx_xxxxxxxxxxxxxxxxxQU-nE
    Locked       false
    UUID         ApiKey-xxxxxxxxx-afd7-xxxxx-b0e1-xxxxxxxxxxx
    ```
2. 自分の {{site.data.keyword.cloud_notm}} アカウントで使用しているリソース・グループを確認します。

  ![Cloud での リソース・グループ](images/cloud-resource.png)

  `デフォルト`のリソース・グループを使用していない場合は、次のコマンドを実行して、{{site.data.keyword.aios_short}} の資格情報を取得します。

   ```curl
   ibmcloud target -g myResourceGroup
   ```

  ここで、`myResourceGroup` は、{{site.data.keyword.aios_short}} インスタンスに関連付けられているリソース・グループの名前です。

3. 以下のコマンドを実行して、{{site.data.keyword.aios_short}} インスタンス ID を取得します。

    ```curl
    ibmcloud resource service-instance '<Your_Watson_OpenScale_instance_name>'
    ```
    **注:** Windows で {{site.data.keyword.cloud_notm}} コマンド・コンソールを使用している場合は、上記のコマンドの単一引用符 (') を二重引用符 (") に置き換えてください。

    次の情報が表示されます。

    ```bash
    Name:                  AI OpenScale-my_instance
    ID:                    crn:v1:ibmcloud:public:aiopenscale:us-south:a/c2f2xxxxxxxxxxxx867::
    GUID:                  03daxxxx-xxxx-xxxx-xxxx-xxxxxxxx38a7
    Location:              us-south
    Service Name:          aiopenscale
    Service Plan Name:     lite
    Resource Group Name:   Default
    State:                 active
    Type:                  service_instance
    Sub Type:
    Tags:
    Created at:            2018-09-17T13:58:43Z
    Updated at:
    ```

    `GUID` の値は、ご使用の {{site.data.keyword.aios_short}} インスタンス ID です。
        
## 次のステップ
{: #cred-create-next-steps}

機械学習プロバイダーを指定します。

- [IBM Watson Machine Learning サービス・インスタンスの指定](https://test.cloud.ibm.com/docs/services/ai-openscale?topic=ai-openscale-wml-connect)
- [Microsoft Azure ML Studio インスタンスの指定](https://test.cloud.ibm.com/docs/services/ai-openscale?topic=ai-openscale-connect-azure)
- [Microsoft Azure ML Service インスタンスの指定](https://test.cloud.ibm.com/docs/services/ai-openscale?topic=ai-openscale-connect-azureservice)
- [Amazon SageMaker ML サービス・インスタンスの指定](https://test.cloud.ibm.com/docs/services/ai-openscale?topic=ai-openscale-csm-connect)
- [カスタム ML サービス・インスタンスの指定](https://test.cloud.ibm.com/docs/services/ai-openscale?topic=ai-openscale-co-connect)