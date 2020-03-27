---

copyright:
  years: 2018, 2020
lastupdated: "2020-01-28"

keywords: Amazon SageMaker, machine learning, services, AWS

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
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}
{:faq: data-hd-content-type='faq'}

# Specifying an Amazon SageMaker ML service instance
{: #csm-connect}

Your first step in the {{site.data.keyword.aios_short}} tool is to specify an Amazon SageMaker service instance. Your Amazon SageMaker service instance is where you store your AI models and deployments.
{: shortdesc}

You can also add your machine learning provider by using the Python SDK. For more information on performing this programmatically, see [Bind your Amazon SageMaker machine learning engine](/docs/services/ai-openscale?topic=ai-openscale-cml-smbind).

## Connect your Amazon SageMaker service instance
{: #csm-config}

{{site.data.keyword.aios_short}} connects to AI models and deployments in an Amazon SageMaker service instance. To connect your service to {{site.data.keyword.aios_short}}, go to the **Configure** ![The configuration tab icon](/images/wos-config-tab.png) tab, add a machine learning provider, and click the **Edit** ![The configuration tab icon](/images/wos-edit-icon.png) icon. In addition to a name and description and whether this is a **Pre-production** or **Production** environment type, you must provide the following information that is specific to this type of service instance:

- Access Key ID: Your AWS access key ID, `aws_access_key_id`, which verifies whoyou are and authenticates and authorizes calls that you make to AWS.
- Secret Access Key: Your AWS secret access key, `aws_secret_access_key`, whichis required to verify who you are and to authenticate and authorize calls thatyou make to AWS.
- Region: Enter the region where your Access Key ID was created. Keys are storedand used in the region in which they were created and cannot be transferred toanother region. 

### Next steps
{: #csm-next}

You are now ready to select deployed models and configure your monitors. {{site.data.keyword.aios_short}} lists your deployed models on the **Insights** dashboard where you can click the **Add to dashboard** button. Select the deployments you want to monitor and click **Configure**.

For more information, see [Configure monitors](/docs/services/ai-openscale?topic=ai-openscale-mo-config).
