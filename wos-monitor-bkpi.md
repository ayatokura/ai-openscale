---

copyright:
  years: 2018, 2020
lastupdated: "2020-04-08"

keywords: KPIs, applications, monitor, configuration 

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
{:note: .note}
{:note: .note}
{:note: .note}
{:note: .note}
{:faq: data-hd-content-type='faq'}

# Configuring KPI metrics in {{site.data.keyword.aios_short}}
{: #kpi-monitor}

After you configure the application monitor, you must add key performance indicators to your monitor. 
{: shortdesc}

## Requirements
{: #kpi-config-reqs}

On the successive pages of the **Application** tab, you must provide the following information:

### Event detail
{: #kpi-config-reqs-eventdets}

You must select one of the event details.

### KPI name and description
{: #kpi-config-reqs-name}

You must give your KPI a name and, optionally, a description. 

### Calculation
{: #kpi-config-reqs-num-ev-dets}

In the **Numeric evaluation details** pane you must select the type of numeric evaluation that is performed on the KPI. You can choose from several mathematcial operators, such as summation or average.

### Numeric operation
{: #kpi-config-reqs-sumtocalc}

Depending on the mathematical operator you choose, you must select the details of the operation.

### Upper or Lower Threshold
{: #kpi-config-reqs-threshold}

Choose either an upper or lower threshold for the alert. Then enter a numeric value for the threshold that {{site.data.keyword.aios_short}} uses for alerting user to data drift.

### Logging endpoint activation
{: #kpi-config-reqs-logging-activation}

To activate the application, along with any of the KPIs that you created, you must upload the business payload file, which is in the form of a .csv file.

## Steps
{: #kpi-config}

1. To start the configuration process, from the **Add monitor** screen, click **KPIs** > **Add KPI**.
2. Follow the prompts and enter required information. When you finish, a summary of your selections is presented for review. If you want to change anything, click the **Edit** link for that section, otherwise, save your work.
3. A summary of your selections is presented for review. If you want to change anything, click the **Edit** icon for that section. Otherwise, click **Save** to complete your configuration.


### Continue with the interactive tutorial: Add KPIs for the German Credit Risk application monitor
{: #wos-open-config-appmon-steps-kpis}

After you configure the application monitor, you must add key performance indicators to your monitor. 

1. In the **Event details** section, click **Load event data from file**.

   The event data corresponds to actual business transactions that represent the fluctuations of your key performance indicators. For example, the accepted credits and sums for the credit applicants. An important part of this file is the `transaction_id` field and the `timestamp` field. These two fields are necessary to make sure that the KPIs line up with the correct transactions in the model data.

1. Download the [history_business_payloads_week.csv](https://raw.githubusercontent.com/pmservice/ai-openscale-tutorials/master/assets/historical_data/german_credit_risk/wos/history_business_payloads_week.csv) file.
1. Select the downloaded file, and then click **Save**.
1. In the **KPIs** section, click **Add KPI**.
1. In the **KPI name** field, type **Accepted Credits**, and then click **Next**.
1. On the **Configure the KPI** window, click the **Accepted** tile, and then click **Next**.
1. Make the following selections:

   - In the **Calculation** drop-down box, select **Sum**.
   - In the **Sum to calculate** drop-down box, select **Daily Sum**.
   - Click the **Lower Threshold** radio button and type **500** in the field and click **Save**.

1. Use the preceding steps to add another KPI with the following values:

   - Credit Amount Granted
   - Amount Granted
   - Sum/DailySum/Lower Threshold = 1 000 000

1. In the **Logging endpoint** section, click the **Activate the application** button and then upload the `history_business_payloads_week.csv` file by dragging it to the drop location.

To see KPI transactions right away, you must click **Evaluate now**.
{: note}

## Next steps
{: #kpi-next}

- [Configure event details](/docs/ai-openscale?topic=ai-openscale-event-dets-monitor)
- Get insights into how your KPIs correlate to model drift. See [Getting application insights](/docs/ai-openscale?topic=ai-openscale-io-app-ov).
- [View correlation charts](/docs/ai-openscale?topic=ai-openscale-app-perform-vdet).
- [View KPI performance](/docs/ai-openscale?topic=ai-openscale-it-appkpi-vdet).
