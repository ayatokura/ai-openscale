---

copyright:
  years: 2018, 2020
lastupdated: "2020-01-28"

keywords: Watson Studio, Watson Machine Learning, wml, machine learning, services

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

# Specifying an {{site.data.keyword.ibmwatson_notm}} {{site.data.keyword.pm_short}} service instance
{: #wml-connect}

Your first step in the {{site.data.keyword.aios_short}} tool is to specify an {{site.data.keyword.pm_full}} instance. Your {{site.data.keyword.pm_short}} instance is where you store your AI models and deployments.
{: shortdesc}

## Prerequisites
{: #wml-prereq}

You should have provisioned an {{site.data.keyword.pm_full}} instance in the same {{site.data.keyword.Bluemix_notm}} account where the {{site.data.keyword.aios_short}} service instance is present. If you have provisioned a {{site.data.keyword.pm_full}} instance in some other account, then you will not be able to configure that instance with automatic payload logging with {{site.data.keyword.aios_short}}.

## Connect your {{site.data.keyword.pm_short}} service instance
{: #wml-config}

{{site.data.keyword.aios_short}} connects to AI models and deployments in an {{site.data.keyword.pm_full}} instance. To connect your service to {{site.data.keyword.aios_short}}, go to the **Configure** ![The configuration tab icon](/images/wos-config-tab.png) tab, add a machine learning provider, and click the **Edit** ![The configuration tab icon](/images/wos-edit-icon.png) icon. In addition to a name and description and whether this is a **Pre-production** or **Production** environment type, you must provide the following information that is specific to this type of service instance:

- If you have an instance of {{site.data.keyword.pm_full}}, {{site.data.keyword.aios_short}} detects it, along with the configuration information.
- To specify a machine learning location outside of your {{site.data.keyword.Bluemix_notm}} account, choose the **Other** option. Provide credentials for your location by pasting valid JSON credentials.


### Next steps
{: #wml-next}

You are now ready to select deployed models and configure your monitors. {{site.data.keyword.aios_short}} lists your deployed models on the **Insights** dashboard where you can click the **Add to dashboard** button. Select the deployments you want to monitor and click **Configure**.

For more information, see [Configure monitors](/docs/services/ai-openscale?topic=ai-openscale-mo-config).
