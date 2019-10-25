---

copyright:
  years: 2018, 2019
lastupdated: "2019-09-09"

keywords: accuracy, 

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

# Configuring the application monitor ![beta tag](images/beta.png)
{: #app-monitor}

In {{site.data.keyword.aios_short}} application refers to either the business application or business process that uses AI models. Applications that are configured in {{site.data.keyword.aios_short}} enable you to monitor business KPIs as well as to understand the impact of model metrics, such as model drift on an application's business key performance indicators (KPIs).
{: shortdesc}

{{site.data.keyword.aios_short}} gives you the ability to correlate business key performance indicators (KPIs) with the drift in model accuracy. In the next part of [the interactive setup tutorial](#wos-open-config-appmon), you will set up an application in {{site.data.keyword.aios_short}} to monitor your business KPIs and to find how deployed models influence these KPIs. The deployed models must be associated with the application; and, business KPIs must be defined based on the business events data. Business events data must be logged to {{site.data.keyword.aios_short}} either by manually uploading a file with events data or by using the REST API. 


## Steps
{: #app-monitor-steps}

1. To start the configuration process, from the **Insights** dashboard, on the Applications monitor tab, click Add to dashboard.
2. Follow the prompts and enter required information. 
3. Review the configuration. After you finish, a summary of your selections is presented. 
4. To make changes, click the **Edit** icon for that section, otherwise, save your work. 

## Requirements
{: #app-config-reqs}

On the successive pages of the **Applications monitor** tab, you must provide the following information:

### Associated models
{: #app-config-reqs}

Select models that are deployed and associated with {{site.data.keyword.aios_short}}.

Only models with a defined `transaction_id` column can be associated with the application. To configure the `transaction_id` column, from the **Model monitor** configuration window, click **Model details**.
{: note}

### Event details
{: #app-config-event-dts}

Events represent a business transaction. Event data must contain all the data that is required to calculate your business KPIs. Each event must also contain timestamp information,such as `2019-09-03T10:44:13.000Z` as well as a business transaction ID. The business transaction ID must be the same as the `transaction_id` value in the scoring payload.


### KPIs
{: #app-config-kpisss}

A key performance indicator is a measurable value that a business uses to determine operational effectiveness and profitability.

### Logging endpoint
{: #app-config-log-endpt}

After you configure associated models, event details, and KPIs, on the **Logging endpoint** window, you must activate the application monitor by clicking **Activate monitor**.

After you activate application monitoring is activated, you can log business events data either by uploading a .csv file or by using the REST API.

There is no possibility to edit activated monitor configuration in the current Beta version.
{: note}


## Continue with the tutorial by configuring the German Credit Risk Model application monitor
{: #wos-open-config-appmon}

For the following tutorial scenario, we provide a .csv file with a week's worth of KPI data for you to use to populate the monitor.

### Tutorial steps: Add a new application monitor for the German Credit Risk Model 
{: #wos-open-config-appmon-steps}

1. From the **Insights dashboard**, on the **Application monitors** tab, click the **Add to dashboard** button to create a new application.

   The application is represented by the tile on the dashboard and gathers together the information about the model that is associated with the KPIs that you will be adding.

1. In the **Application name** field, type **German Credit Risk Model Application**, and then click **Configure**.
1. In the **Associated models** section, click the **Add associated model** button.

   You associate a model for which you have tracked KPIs.
   
1. Select the **German Credit Risk model** deployment, and then click **Save**.




## Next steps
{: #app-next}

- To continue with the tutorial, see [Tutorial steps: Add KPIs for the German Credit Risk application monitor](/docs/services/ai-openscale?topic=ai-openscale-wos-open-config-appmon-steps-kpis)
- [Configure KPI metrics](/docs/services/ai-openscale?topic=ai-openscale-kpi-monitor)
- Get insights into how your KPIs correlate to model drift. For more information, see [Getting application insights](/docs/services/ai-openscale?topic=ai-openscale-io-app-ov).
- [View correlation charts](/docs/services/ai-openscale?topic=ai-openscale-app-perform-vdet).
- [View KPI performance](/docs/services/ai-openscale?topic=ai-openscale-it-appkpi-vdet).
