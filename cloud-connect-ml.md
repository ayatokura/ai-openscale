---

copyright:
  years: 2018, 2020
lastupdated: "2020-05-18"

keywords: payload, non-Watson, machine learning, services, subscription

subcollection: ai-openscale

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:pre: .pre}
{:codeblock: .codeblock}

{:screen: .screen}
{:faq: data-hd-content-type='faq'}

# Payload logging for non-{{site.data.keyword.ibmwatson_notm}} {{site.data.keyword.pm_short}} service instances
{: #cml-connect}

If your AI model is deployed in a machine learning engine other than {{site.data.keyword.pm_full}}, you must enable payload logging for the external machine learning engine with a Python client.
{: shortdesc}

See additional information in the [{{site.data.keyword.aios_short}} Python client documentation](http://ai-openscale-python-client.mybluemix.net/){: external}, and in the sample {{site.data.keyword.aios_short}} Python client notebooks that are part of the [{{site.data.keyword.aios_short}} tutorials](https://github.com/pmservice/ai-openscale-tutorials/blob/master/README.md){: external}.

## Before you begin
{: #cml-prereq}

You need to have the training data of your model available in Db2 or {{site.data.keyword.cos_full}} to monitor bias for your model. Explainability and accuracy are not supported for Python functions. For more information about training data, see. Why does {{site.data.keyword.aios_short}} need access to training data?](/docs/ai-openscale?topic=ai-openscale-fmt-upld-training_data_schema-ovr)

- Import and initiate {{site.data.keyword.aios_short}}

    ```python
    from ibm_ai_openscale import APIClient

    aios_credentials = {
      "instance_guid": "***",
      "url": "https://api.aiopenscale.cloud.ibm.com",
      "apikey": "***"
    }

    client = APIClient(service_credentials)
    ```
    {: codeblock}

  Credentials can be found by following the steps that are shown in the "[Creating credentials](/docs/ai-openscale?topic=ai-openscale-cred-create)" topic.

- Create a schema name in your PostgreSQL database

- Set up a data mart

    ```python
    client.data_mart.setup(db_credentials=postgres_credentials, schema=schemaName)

    client.data_mart.get_details()
    ```
    {: codeblock}

## Next steps
{: #cml-next}

- To continue with the {{site.data.keyword.aios_short}} client, see [Configuring the Accuracy or Quality monitor](/docs/ai-openscale?topic=ai-openscale-acc-monitor).
- To continue with the Python command library, refer to the [Python client documentation](http://ai-openscale-python-client.mybluemix.net/){: external}.
