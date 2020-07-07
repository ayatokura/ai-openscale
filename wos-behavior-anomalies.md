---

copyright:
  years: 2018, 2020
lastupdated: "2020-05-18"

keywords: drift, anomalies, data, data drift, drift detection, transactions

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

# Drift in data
{: #behavior-anomalies}

In addition to checking for the drift in model accuracy, the drift monitor can detect the drift in data. This type of drift is defined as something that deviates from what is standard, normal, or expected. {{site.data.keyword.aios_short}} detects data drift so that you can make changes to the model.
{: shortdesc}

## Understanding drift detection
{: #behavior-anomalies-understand}

Drift is the degradation of predictive performance over time because of hidden context. As your data changes over time, the ability of your model to make accurate predictions may deteriorate. {{site.data.keyword.aios_short}} both detects and highlights drift so that you can take corrective action.

### How it works
{: #behavior-anomalies-works}

{{site.data.keyword.aios_short}} analyzes all transactions to find the ones that contribute to drift. It then groups the records based on the similarity of data inconsistency patterns that were significant in contributing to drift.

### Single feature constraints
distribution constraints

### Double feature constraints

situations where the expected constraint cannot be generated
how is clustering done?
transactions show clustered events
how are we calculating the effect size?
1hotencoding: wrapper technique, REST API, needs for explainability (generic, required for payload logging, etc) Check with DSE team for notebook sample 
Mike: email Manish

larger dataset, how to configure? dividing columns into smaller datasets
What is the technique for larger datasets? (more than 1K columns)
1012, see the GitHub issue
also needs columns to make its analysis
payload column issue 

### Working with large datasets

Example of 4K columns, divided into separate subscriptions of 1K columns each

Mention limits:
https://cloud.ibm.com/docs/ai-openscale?topic=ai-openscale-rn-12ki#wos-limitations-feat-col-size-limit

### Do the math
{: #behavior-anomalies-math}


{{site.data.keyword.aios_short}} analyzes each transaction for data inconsistency, by comparing the transaction content with the training data patterns. If a transaction violates one or more of the training data patterns, the transaction is marked as drifted. {{site.data.keyword.aios_short}} then estimates the magnitude of data inconsistency as the fraction of drifted transactions to the total number of transactions analyzed. Further, {{site.data.keyword.aios_short}} analyzes all the drifted transactions; and then, groups transactions that violate similar training data patterns into different clusters. In each cluster, {{site.data.keyword.aios_short}} also estimates the important features that played a major role in the data inconsistency and classifies their feature impact as large, some, and small.

## Next steps
{: #behavior-anomalies-ns}

- For information on how to set up drift detection, see [Configuring the drift detection monitor](/docs/ai-openscale?topic=ai-openscale-behavior-drift-config).
- To mitigate drift, after it has been detected by {{site.data.keyword.aios_short}}, you must build a new version of the model that fixes the problem. A good place to start is with the data points that are highlighted as reasons for the drift. Introduce the new data to the predictive model after you have manually labeled the drifted transactions and use them to re-train the model.
