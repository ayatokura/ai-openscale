---

copyright:
  years: 2018, 2020
lastupdated: "2020-01-28"

keywords: machine learning, services, ml, custom 

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

# Specifying a Custom ML service instance
{: #co-connect}

Your first step in the {{site.data.keyword.aios_short}} tool is to specify a service instance. Your service instance is where you store your AI models and deployments.
{: shortdesc}

## Connect your Custom service instance
{: #co-config}

{{site.data.keyword.aios_short}} connects to AI models and deployments in a service instance. You can connect a custom service. To connect your service to {{site.data.keyword.aios_short}}, go to the **Configure** ![The configuration tab icon](/images/wos-config-tab.png) tab, add a machine learning provider, and click the **Edit** ![The configuration tab icon](/images/wos-edit-icon.png) icon. In addition to a name and description and whether this is a **Pre-production** or **Production** environment type, you must provide the following information that is specific to this type of service instance:

- Username
- Password
- API endpoint

Choose whether to connect to your deployments [by requesting a list](/docs/services/ai-openscale?topic=ai-openscale-co-connect#co-config-request-list) or [by entering individual scoring endpoints](/docs/services/ai-openscale?topic=ai-openscale-co-connect#co-config-scoring-endpoints).


### Requesting the list of deployments
{: #co-config-request-list}

If you selected the **Request the list of deployments** tile, enter your credentials and API Endpoint, then save your configuration.

### Providing individual scoring endpoints
{: #co-config-scoring-endpoints}

If you selected the **Enter individual scoring endpoints** tile, enter your credentials for the API Endpoint, then save your configuration.


### Next steps
{: #co-next}

You are now ready to select deployed models and configure your monitors. {{site.data.keyword.aios_short}} lists your deployed models on the **Insights** dashboard where you can click the **Add to dashboard** button. Select the deployments you want to monitor and click **Configure**.

For more information, see [Configure monitors](/docs/services/ai-openscale?topic=ai-openscale-mo-config).
