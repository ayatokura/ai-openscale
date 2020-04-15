---

copyright:
  years: 2018, 2020
lastupdated: "2020-04-18"

keywords: accuracy, drift, configuration, monitors

subcollection: ai-openscale

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:pre: .pre}
{:codeblock: .codeblock}
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}
{:screen: .screen}
{:note: .note}
{:note: .note}
{:note: .note}
{:note: .note}
{:faq: data-hd-content-type='faq'}

# Configuring the drift detection monitor
{: #behavior-drift-config}

You must configure the {{site.data.keyword.aios_full}} drift monitor before it can analyze your model. You can train your drift detection model online by using the {{site.data.keyword.aios_full}} user interface or by using a notebook.
{: shortdesc}

You can train your model online by using {{site.data.keyword.aios_short}}
if you use {{site.data.keyword.pm_full}} and your data does not exceed 500 MB. Otherwise, you must use a notebook to train the model.

## Requirements
{: #behavior-drift-config-steps-wos-reqs}

Throughout this process, {{site.data.keyword.aios_full}} analyzes your model and makes recommendations based on the most logical outcome. For the drift monitor to work properly, the data type of your prediction column in the training data must match the data type of the same column in the payload data. Assign matching string or numeric types to the prediction and label columns. To confirm data types, click **Model details** > **Model output details** > **Edit**. These selections ensure that you have accurate information for the following configuration steps. If for some reason you must change data types, you must redeploy the monitor to effect the changes.

On the successive pages of the **Drift** tab, you must provide the following information:

### Alert threshold
{: #behavior-drift-config-steps-wos-reqs-alert}

(Required only for classification type models.) {{site.data.keyword.aios_full}} tracks the degree of change in model accuracy when compared to accuracy at training time. The alert threshold, which must be at least 5%, indicates the degree of tolerance for change over time.

### Sample size
{: #behavior-drift-config-steps-wos-reqs-sample}

By setting a minimum sample size, you prevent measuring drift until a minimum number of records are available in the evaluation data set. This setting ensures that the sample size is not too small to skew results. Every time drift checking runs, it uses the minimum sample size to decide the number of records on which it does the computation.

## Steps to configure drift in {{site.data.keyword.aios_short}}
{: #behavior-drift-config-steps-wos}
{: help} 
{: support}

If you use {{site.data.keyword.pm_full}}, you have the option of using the {{site.data.keyword.aios_short}} user interface to configure drift detection.

To start the configuration process, from the **Drift** tab, in the **Drift model** box, click the **Edit** ![The edit icon](images/wos-edit-icon.png) icon. Use the **Train in {{site.data.keyword.aios_short}}** option.

Follow the prompts and enter required information. When you finish, a summary of your selections is presented for review. If you want to change anything, click the **Edit** icon for that section, otherwise, save your work.



## Steps to configure drift without retraining
{: #behavior-drift-config-steps-no-training}

Reconfigure the drift monitor without retraining the drift model to update parameters without more processing. You update the minimum sample size and threshold to produce more data on the currently trained model without incurring more processing costs. It is one way to avoid intensive CPU usage when the underlying data is stable and you want to view drift magnitude with different thresholds. Your drift model requires retraining only when training data or schema changes.


To start the configuration process, from the **Drift** tab, in the **Drift threshold** box or **Sample size** box, click the **Edit** ![The edit icon](images/wos-edit-icon.png) icon. Update the current setting and save it.

## Steps to configure drift by using a notebook
{: #behavior-drift-config-steps-ntbk}

Use a notebook to configure drift in the following circumstances:

- You do not want to share the training data with {{site.data.keyword.aios_short}}.
- You do not have a means to share the training data on Db2 or {{site.data.keyword.cos_full}}, which are the only two training data locations that are supported by {{site.data.keyword.aios_short}}. 

This option is useful if the training data is not stored in Db2 or {{site.data.keyword.cos_full}}. Using a notebook, you must read the training data into a dataframe. The specialized notebook that you can download from {{site.data.keyword.aios_short}} then creates a specialized output that you can upload to {{site.data.keyword.aios_short}}.

To generate the drift detection model, you must use scikit-learn version 0.20.2 in notebooks. 
{: note}

Create a notebook to generate the drift detection model. Use [the sample notebook](https://github.com/IBM-Watson/aios-data-distribution/blob/master/training_statistics_notebook.ipynb){: external} that is available from the {{site.data.keyword.aios_short}} UI. The drift detection model is converted into a .tar.gz file for you.

To start the configuration process, from the **Drift** tab, in the **Drift model** box, click the **Edit** ![The edit icon](images/wos-edit-icon.png) icon. Use the **Train in a data science notebook** option. You can drag your compressed drift detection model to the drop zone.

Follow the prompts and enter required information. When you finish, a summary of your selections is presented for review. If you want to change anything, click the **Edit** icon for that section, otherwise, save your work.



## Next steps
{: #behavior-drift-config-next-steps}

- Continue with configuration by [configuring the endpoint monitor](/docs/ai-openscale?topic=ai-openscale-mf-endpoints).
- For more information about interpreting drift, see [Drift](/docs/ai-openscale?topic=ai-openscale-behavior-drift-ovr)