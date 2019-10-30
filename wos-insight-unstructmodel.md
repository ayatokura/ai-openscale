---

copyright:
  years: 2018, 2019
lastupdated: "2019-09-09"

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
{:download: .download}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}
{:faq: data-hd-content-type='faq'}

# Explaining unstructured text models
{: #ie-unstruct}

{{site.data.keyword.aios_short}} supports explainability for unstructured text data.
{: shortdesc}

If you are using a Keras model that takes the input as byte array, you must create a deployable function in {{site.data.keyword.pm_full}} that accepts text as input. Creating a deployable function is part of the functionality that {{site.data.keyword.pm_full}} support. For more information, see [Passing payload data to model deployments](https://dataplatform.cloud.ibm.com/docs/content/wsj/analyze-data/ml-deploy-functions.html?linkInPage=true#models){: external}

## Working with unstructured text models
{: #ie-unstruct-steps}

1. Set up your environment.
   2. Install the {{site.data.keyword.aios_short}} and {{site.data.keyword.pm_full}} packages.
   3. Configure your credentials.
   4. Install the libraries that are needed for creating the models and doing analysis. These include the following libraries:
      - `pandas`
      - `pyspark` (if not using {{site.data.keyword.DSX}})

1. Create and deploy your image-based model.
   2. Load training data into a pandas frame.
   2. Train the model on the data.
   3. Publish the model.
   4. Deploy and score the model.

7. Configure {{site.data.keyword.aios_short}} by assigning the `APIClient`, sbuscribing the asset and scoring the model.
8. Configure explainability.
   9. Enable the explainability.
   10. Get explanations for the transactions.

## Explaining unstructured text transactions
{: #ie-unstruct-xplan}

The following example of explainability shows a classification model that evaluates unstructured text. The explanation shows the keywords that had a positive as well as a negative impact on the model prediction. We also show the position of the identified keywords in the original text which was fed as input to the model.

![Explainability image classification chart is displayed. it shows confidence levels for the unstructured text](images/insight-explain-text.png)

## Unstructured text model example
{: #ie-unstruct-ntbkssample}

Use the following notebook to see detailed code samples and develop your own {{site.data.keyword.aios_short}} deployments:

- [Tutorial on generating an explanation for a text-based model](https://github.com/pmservice/ai-openscale-tutorials/blob/master/notebooks/Watson%20OpenScale%20Explanation%20for%20Text%20Model.ipynb){: external}

