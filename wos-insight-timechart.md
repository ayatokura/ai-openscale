---

copyright:
  years: 2018, 2020
lastupdated: "2020-01-28"

keywords: fairness, monitoring, charts, de-biasing, bias, accuracy

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

# Viewing data for a deployment
{: #it-vdep}

Select a deployment from the dashboard to see monitoring data for that deployment. The heading displays information about the deployed model, such as the **Model ID** and **Created date** fields.
{: shortdesc}

![Time series chart is displayed with hours for one day and a fairness score](images/wos-insight-time-chart.png)

Because the algorithm checks are only run every hour, there are also links provided to check fairness and quality on-demand. From the **Schedule** panel, you can click the following links to make an immediate check of your data:

![check fairness button is shown](images/wos-fairness-button.png)


![check quality button is shown](images/wos-quality-button.png)

Next, click the chart and move the marker across the chart to see statistics for an individual hour:

![Time series chart detail is shown with a specific data point in the chart selected and a tooltip saying to click to view details](images/wos-insight-time-detail.png)

- ***Fairness***: Two Fairness features, Sex and Age, met their set thresholds for approval.
- ***Quality***: The **Area under ROC** metric displays an alert because it was not within the configured treshold.
- ***Avg. Reqs/Min***: Click the **Throughput** metric to see the number of records that were processed per minute between. The throughput is computed every minute, and its average value over the course of the hour is reported in the chart.


## View transactions
{: #it-tra}

This option allows you to view the individual transactions that contributed to bias when you click the **View transactions** button.

![View transactions button is displayed](images/wos-view_transactions.png)

A list of transactions where the deployment has acted in a biased manner is listed. Click the **Explain** link for any of the transaction IDs to get details about that transaction in the Explainability tab. For more information, see [Monitoring explainability](/docs/services/ai-openscale?topic=ai-openscale-ie-ov).

Select the **All transactions** view to see all transactions from the selected feature (in this example "AGE"), and the selected period (in this example "September 15, 2018 1:00 PM"):

![Transaction lists all transactions for a specific data point](images/wos-explain-all-transactions.png)

Select the **Biased transactions** view to see only the subset of transactions that received biased outcomes. Each biased transaction is compared to a similar-but-slightly-altered (perturbed) transaction that shows how changing the value of the monitored feature (AGE) will result in a favorable outcome for the biased transaction:

![Transaction lists only biased transactions](images/wos-explain-debias-transactions.png)


