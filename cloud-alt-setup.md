---

copyright:
  years: 2018, 2020
lastupdated: "2020-08-08"

keywords: Python, install, python module, setup, set up, insights, explainability

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

# Installing a Python module to set up {{site.data.keyword.aios_short}}
{: #as-module}

To automate the provisioning and configuration of the required {{site.data.keyword.cloud_notm}} services and see an {{site.data.keyword.aios_full}} application, including sample data, you can install a Python module.
{: shortdesc}

## About this module
{: #as-about}

- The module provides an alternate way for technical users to see an instance of {{site.data.keyword.aios_short}} running without needing to provision and configure the services yourself, as described in the [Getting started](/docs/ai-openscale?topic=ai-openscale-getting-started) tutorial.
- The Python module runs through the process of checking the services that you have and creating the ones that are necessary, including {{site.data.keyword.aios_short}}. After the module runs successfully, from the {{site.data.keyword.cloud_notm}} dashboard you can launch {{site.data.keyword.aios_short}} to see how it monitors a model.

### {{site.data.keyword.aios_short}} Python Client
{: #abt-python}

The [{{site.data.keyword.aios_short}} Python Client](http://ai-openscale-python-client.mybluemix.net/){: external} is a Python library that works directly with the {{site.data.keyword.aios_short}} service. For development and automation purposes, you can optionally use the Python client to directly configure the datamart database, bind your machine learning engine, and select and monitor deployments. For examples using the Python client in this way, see the [{{site.data.keyword.aios_short}} sample notebooks](https://github.com/pmservice/ai-openscale-tutorials/tree/master/notebooks){: external}.

<p>&nbsp;</p>

## Before you begin
{: #as-prereqs}

1. [Create an {{site.data.keyword.cloud_notm}} API key and download it](/docs/iam?topic=iam-userapikey#create_user_key){: external}. You will need to enter the API key in a later step.

2. [Install any release of Python 3](https://www.python.org/downloads/){: external}.

  Python 3 includes the required pip package management system.
  {: note}

3. Install the `ibm-ai-openscale-cli` package by running the following command:

    ```python
    pip install -U ibm-ai-openscale-cli
    ```
    {: codeblock}

    If more than one version of pip is installed on your system, you might need to run `pip3` instead of `pip`, as in, `pip3 install -U ibm-ai-openscale-cli`.
    {: tip}

4. If you have an existing {{site.data.keyword.pm_short}} service instance, check the [{{site.data.keyword.cloud_notm}} dashboard](https://{DomainName}){: external} to ensure that the service is managed by {{site.data.keyword.iamshort}} (IAM), not Cloud Foundry.

  **Important**: The module checks for an instance of {{site.data.keyword.pm_short}}. If you have an instance, the module uses it. But if your instance is managed by Cloud Foundry, you must first [migrate it to an IAM resource group before running the module](/docs/resources?topic=resources-migrate#migrate).

## Running the module
{: #as-run}

Run the following command:

```python
ibm-ai-openscale-cli -a <Your API key>
```
{: codeblock}

## Viewing results in the {{site.data.keyword.aios_short}} model monitor
{: #as-open}

To view insights into the fairness and accuracy of the model, details of data that is monitored, and explainability for an individual transaction, open the [{{site.data.keyword.aios_short}} dashboard](https://aiopenscale.cloud.ibm.com/aiopenscale/){: external}.

- To understand the scenario for the sample data, read [Use case and the value of {{site.data.keyword.aios_short}}](/docs/ai-openscale?topic=ai-openscale-getting-started#gs-use).

### View insights
{: #as-insights}

From the [{{site.data.keyword.aios_short}} dashboard](https://aiopenscale.cloud.ibm.com/aiopenscale/){: external}, click the **Insights** tab, which shows an overview of metrics for deployed models: ![Insights](images/wos_insight-dash-tab.png)

- At a glance, the Insights page shows any issues with fairness and accuracy, as determined by the thresholds that are configured.

- Each deployment is shown as a tile. If you are following any one of the tutorials, in your dashboard, you see a deployment called `GermanCreditRiskModel`. The following sample shows a dashboard with many deployed and monitored models:

    ![Insight dashboard with many deployments, each shown as a tile](images/wos-insight-dashboard.png)


### View monitoring data
{: #as-monitoring}

1. From the Insights page, click the `GermanCreditRiskModel` tile to view details about the monitored data.
2. Slide the marker across the chart to view a day and time period that show data and then click the **View details** link.

   - For example, the following screen shows data for a specific date and time. The dates and times vary, depending on when you run the module.

   - For information about interpreting the time series chart, see [Getting insights](/docs/ai-openscale?topic=ai-openscale-io-ov).

    ![Monitor data is shown](images/wos-fairness-age-payload-perturbed.png)

3. To see details about `AGE` data monitoring, ensure that `AGE` is selected from the drop-down menu.

  - Notice that in the following screen capture, no bias exists.

  - For information about interpreting the chart of the data points at a specific hour, see [Visualizing data for a specific hour](/docs/ai-openscale?topic=ai-openscale-it-vdet).

    ![View details are shown](images/wos-fairness-age-debiased.png)

### View explainability
{: #as-explain}

To understand the factors that contribute when bias is present for a given time period, from the visualization screen shown in the previous section, select the **View transactions** button.

Transaction IDs for the past hour are listed for those transactions that have bias. For the model used in this module, no bias exists for requests that are available. Therefore, no transactions are shown for the time period in the following screen capture.

  ![Transaction list with no transactions](images/cloud-setup06-0206.png)

For information about finding and explaining transactions, see [Explaining transactions](/docs/ai-openscale?topic=ai-openscale-ie-ov#ie-view).

## Related information
{: #as-info}

- To learn about biases, see [Fairness](/docs/ai-openscale?topic=ai-openscale-mf-monitor).
- To learn about how well your model predicts outcomes, see [Accuracy](/docs/ai-openscale?topic=ai-openscale-acc-monitor).
- To learn about interpreting charts and data, see [Getting insights](/docs/ai-openscale?topic=ai-openscale-io-ov).
- To learn how underlying factors influence outcomes, see [Monitoring explainability](/docs/ai-openscale?topic=ai-openscale-ie-ov).
