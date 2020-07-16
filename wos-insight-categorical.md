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

This example of explainability is for a binary classification model that approves or denies insurance claims. You can see the factors that contributed positively or negatively to the outcome of `DENIED` in this case.
{: shortdesc}

The *POLICY AGE* feature, with a value of less than one, has the maximum impact in the model decision, which is a DENIED outcome. The other features that contributed to this outcome are *CLAIM FREQUENCY* (`High`) and *AGE* (`18`), with only a minor impact from *CAR VALUE* (`$50,000`).

![Explainability binary classification displays with details about denied and approved claims](images/wos-insight-explain-binary.png)

While the charts are useful in showing the most significant factors in determining the outcome of a transaction, classification models can also include advanced explanations, detailed in the `Minimum changes for Approved outcome` and `Minimum changes for this outcome` sections.

Advanced explanations are not available for regression, image, and unstructured text models.
{: note}

- The `Minimum changes for Approved outcome` indicates that if the values of the features change to the listed values, then the prediction of the model changes.

- The `Maximum changes allowed for the same outcome` indicates that if the values of the features change to the listed values, the prediction of the model does not change.

These two values indicate the behavior of the model in the vicinity of the data point for which the explanation is generated.

![Explainability binary classification details with minimum changes that would be needed to change outcomes](images/wos-insight-explain-binary2.png)