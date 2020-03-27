---

copyright:
  years: 2018, 2020
lastupdated: "2020-01-28"

keywords: Microsoft Azure ML service, ml, machine learning, services

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

# Specifying a Microsoft Azure ML Service instance
{: #connect-azureservice}

Your first step in the {{site.data.keyword.aios_short}} tool is to specify a Microsoft Azure ML Service instance. Your Azure ML Service instance is where you store your AI models and deployments.
{: shortdesc}

You can also add your machine learning provider by using the Python SDK. For more information on performing this programmatically, see [Bind your Microsoft Azure Service machine learning engine](/docs/services/ai-openscale?topic=ai-openscale-cml-azsrvconfig#cml-azsrvbind).

## Connect your Azure ML Service instance
{: #ca-connect-azureservice}

{{site.data.keyword.aios_short}} connects to AI models and deployments in a Azure ML Service instance. To connect your service to {{site.data.keyword.aios_short}}, go to the **Configure** ![The configuration tab icon](/images/wos-config-tab.png) tab, add a machine learning provider, and click the **Edit** ![The configuration tab icon](/images/wos-edit-icon.png) icon. In addition to a name and description and whether this is a **Pre-production** or **Production** environment type, you must provide the following information that is specific to this type of service instance:

- Client ID: The actual string value of your client ID, whichverifies who you are and authenticates and authorizes callsthat you make to Azure Service.
- Client Secret: The actual string value of the secret, whichverifies who you are and authenticates and authorizes callsthat you make to Azure Service.
- Tenant: Your tenant ID corresponds to your organization andis a dedicated instance of Azure AD. To find the tenant ID,hover over your account name to get the directory / tenant ID,or select Azure Active Directory > Properties > Directory ID inthe Azure portal.
- Subscription ID: Subscription credentials which uniquelyidentify your Microsoft Azure subscription. The subscription IDforms part of the URI for every service call.

See [How to: Use the portal to create an Azure AD applicationand service principal that can access resources](https://docsmicrosoft.com/en-us/azure/active-directory/develophowto-create-service-principal-portal){: external} forinstructions about how to get your Microsoft Azure credentials.
{: note}


### Next steps
{: #ca-next-azureservice}

You are now ready to select deployed models and configure your monitors. {{site.data.keyword.aios_short}} lists your deployed models on the **Insights** dashboard where you can click the **Add to dashboard** button. Select the deployments you want to monitor and click **Configure**.

For more information, see [Configure monitors](/docs/services/ai-openscale?topic=ai-openscale-mo-config).
