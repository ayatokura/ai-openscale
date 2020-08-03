---

copyright:
  years: 2018, 2020
lastupdated: "2020-05-18"

keywords: fairness, monitoring, charts, debiasing, bias, accuracy,

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

# Explaining a categorical model
{: #ie-class}

A categorical model, such as a binary classification model categorizes data into distinct groups. Unlike regression, image, and unstructured text models, {{site.data.keyword.aios_short}} generates advanced explanations for binary classification models. You can use the **Inspect** tab to experiment with features by changing the values to see whether the outcome changes.
{: shortdesc}

While the charts are useful in showing the most significant factors in determining the outcome of a transaction, classification models can also include advanced explanations on the `Explain` and `Inspect` tabs.

- The `Explain` tab, in addition to basic information about the transaction and model, displays the following information:
  
  - Predicted outcome: The outcomes are set in the model.
  - How this prediction was determined: 
  - Confidence level: 
  - Features influencing this prediction: 
  
- The `Inspect` tab displays the following information:
  
  - Feature: The feature from the model. If the model was created with additional meta fields that were not used in training, you have the option of viewing only those features by selecting the **Analyze controllable features only** option.
  - Original value: The original value used in training the model.
  - New value: You can enter a new value for one or more features to see how it might change the outcome.
  - Value for a different outcome: After you run an analysis, you can see what are the mostly likely settings to change the outcome.
  - Importance: After you run an analsysis, you can see what the relative importance is for each changed feature value.



## Next steps
{: #ie-class-next}

For more information, see [Contrastive explanations](/docs/ai-openscale?topic=ai-openscale-ie-pp-pn).
