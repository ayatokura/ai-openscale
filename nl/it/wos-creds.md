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

# Creazione di credenziali per {{site.data.keyword.aios_short}}
{: #cred-create}

Per accedere alle API REST di {{site.data.keyword.aios_full}}, sono richiesti una chiave API della piattaforma e un ID data mart, anche detta istanza del servizio. La chiave API della piattaforma fornisce a un singolo utente la possibilità di accedere alle risorse in {{site.data.keyword.cloud_notm}}.
{: shortdesc}

Per gli account enterprise, un amministratore può creare il data mart, invitare gli utenti nell'account e fornire a tali utenti l'accesso a un data mart {{site.data.keyword.aios_short}} specifico. Quindi, un utente può creare la propria chiave API della piattaforma e accedere allo stesso data mart {{site.data.keyword.aios_short}}. Non c'è alcun rischio di conflitto o di sicurezza.

## Creazione della chiave API della piattaforma
{: #cred-create-apikey}

Per creare una chiave API della piattaforma, completare la seguente procedura:

1. Accedere a [{{site.data.keyword.cloud_notm}}](https://{DomainName}){: external}.

2. Selezionare **Gestisci** --> **Sicurezza** --> **Chiavi API della piattaforma**

    ![Chiavi API della piattaforma](images/cred-api-key.png)

3. Creare e salvare una chiave API della piattaforma.

Per trovare l'ID (o l'istanza del servizio) del data mart dell'utente:

1. Fare clic sul riquadro della distribuzione del modello.
2. Fare clic sull'icona **Configura** ![icona di configurazione](images/configure-deployment-button.png).
3. Fare clic su **Visualizza endpoint di registrazione payload**.
4. Nella pagina {{site.data.keyword.aios_short}} **Registrazione payload**, trovare il campo **ID datamart**.

    ![ID data mart](images/data-mart-id.png)

## Creazione delle credenziali dell'istanza del servizio utilizzando la console dei comandi
{: #cred-creds}

Per creare le credenziali per {{site.data.keyword.aios_short}}, completare i seguenti passi utilizzando la [console dei comandi](/docs/cli?topic=cloud-cli-ibmcloud-cli) di {{site.data.keyword.cloud_notm}}:

1. Richiamare la chiave API eseguendo il seguente comando:

    ```curl
    ibmcloud login --sso
    ibmcloud iam api-key-create 'my_key'
    ```

    Sono visualizzate le seguenti informazioni:

    ```bash
    Name         my_key
    Created At   2018-10-09T14:04+0000
    API Key      Tg4Gxxxxxxxxxxxxxxxxx_xxxxxxxxxxxxxxxxxQU-nE
    Locked       false
    UUID         ApiKey-xxxxxxxxx-afd7-xxxxx-b0e1-xxxxxxxxxxx
    ```
2. Verificare il gruppo di risorse che si sta utilizzando nell'account {{site.data.keyword.cloud_notm}}.

  ![Gruppo di risorse nel cloud](images/cloud-resource.png)

  Se non si utilizza il gruppo di risorse `Predefinito`, quindi eseguire il seguente comando per ottenere la credenziale per {{site.data.keyword.aios_short}}:

   ```curl
   ibmcloud target -g myResourceGroup
   ```

  dove `myResourceGroup` è il nome del gruppo di risorse associato all'istanza {{site.data.keyword.aios_short}}.

3. Richiamare l'ID istanza {{site.data.keyword.aios_short}} eseguendo il seguente comando:

    ```curl
    ibmcloud resource service-instance '<nome_istanza_Watson_OpenScale>'
    ```
    **Nota**: se si utilizza la console dei comandi {{site.data.keyword.cloud_notm}} su Windows, sostituire gli apici (') nei comandi sopra riportati con le virgolette (").

    Sono visualizzate le seguenti informazioni:

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

    Il valore `GUID` è l'ID istanza {{site.data.keyword.aios_short}}.
        
## Passi successivi
{: #cred-create-next-steps}

Specificare il provider di machine learning:

- [Specifica di un'istanza del servizio IBM Watson Machine Learning](https://test.cloud.ibm.com/docs/services/ai-openscale?topic=ai-openscale-wml-connect)
- [Specifica di un'istanza di Microsoft Azure ML Studio](https://test.cloud.ibm.com/docs/services/ai-openscale?topic=ai-openscale-connect-azure)
- [Specifica di un'istanza di Microsoft Azure ML Service](https://test.cloud.ibm.com/docs/services/ai-openscale?topic=ai-openscale-connect-azureservice)
- [Specifica di un'istanza del servizio Amazon SageMaker ML](https://test.cloud.ibm.com/docs/services/ai-openscale?topic=ai-openscale-csm-connect)
- [Specifica di un'istanza del servizio ML personalizzata](https://test.cloud.ibm.com/docs/services/ai-openscale?topic=ai-openscale-co-connect)