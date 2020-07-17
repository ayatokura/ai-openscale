---

copyright:
  years: 2018, 2020
lastupdated: "2020-05-18"

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
{:faq: data-hd-content-type='faq'}

# Explaining a categorical model
{: #ie-class}

A categorical model, such as a binary classification model categorizes data into distinct groups. Unlike regression, image, and unstructured text models, {{site.data.keyword.aios_short}} generates advanced explanations for binary classification models.
{: shortdesc}

While the charts are useful in showing the most significant factors in determining the outcome of a transaction, classification models can also include advanced explanations in the `Minimum changes for [a different] outcome` and `Maximum changes for [the same] outcome` sections.

- The `Minimum changes for [a different] outcome` section indicates that if the values of the features change to the listed values, then the prediction of the model changes.

- The `Maximum changes allowed for the same outcome` section indicates that if the values of the features change to the listed values, the prediction of the model does not change.

These two values indicate the behavior of the model in the vicinity of the data point for which the explanation is generated.

## Next steps
{: #ie-class-next}

For more information, see [Contrastive explanations](/docs/ai-openscale?topic=ai-openscale-ie-pp-pn).
