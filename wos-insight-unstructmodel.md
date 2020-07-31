---

copyright:
  years: 2018, 2020
lastupdated: "2020-05-18"

keywords: fairness, monitoring, charts, debiasing, bias, accuracy

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

# Explaining unstructured text models
{: #ie-unstruct}

{{site.data.keyword.aios_short}} supports explainability for unstructured text data.
{: shortdesc}

If you are using a Keras model that takes the input as byte array, you must create a deployable function in {{site.data.keyword.pm_full}} that accepts the entire text as a single feature in input (as opposed to text which is vectorised and represented as a tensor or split across multiple features). Creating a deployable function is part of the functionality that {{site.data.keyword.pm_full}} support. For more information, see [Passing payload data to model deployments](https://dataplatform.cloud.ibm.com/docs/content/wsj/analyze-data/ml-deploy-functions.html?linkInPage=true#models){: external}

For information about setting up your unstructured text models, see [Working with unstructured text models](/docs/ai-openscale?topic=ai-openscale-ie-unstruct-steps).

For information about configuring support for non-space-delimited languages, such as Japanese, Chinese, and Korean, see [Enabling non-space-delimited language support](/docs/ai-openscale?topic=ai-openscale-explainability-monitor#ie-unstruct-xplan-langsupport)

## Explaining unstructured text transactions
{: #ie-unstruct-xplan}

The following example of explainability shows a classification model that evaluates unstructured text. The explanation shows the keywords that had a positive as well as a negative impact on the model prediction. We also show the position of the identified keywords in the original text which was fed as input to the model.  

![Explainability image classification chart is displayed. it shows confidence levels for the unstructured text](images/wos-insight-explain-text.png)

Unstructured text models present the importance of words or tokens. To change the language, select a different language from the drop-down menu. The explanation runs again by using a different tokenizer.


## Unstructured text model example
{: #ie-unstruct-ntbkssample}

Use the following notebook to see detailed code samples and develop your own {{site.data.keyword.aios_short}} deployments:

- [Tutorial on generating an explanation for a text-based model](https://github.com/pmservice/ai-openscale-tutorials/blob/master/notebooks/Watson%20OpenScale%20Explanation%20for%20Text%20Model.ipynb){: external}

