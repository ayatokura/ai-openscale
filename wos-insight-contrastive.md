---

copyright:
  years: 2018, 2020
lastupdated: "2020-05-18"

keywords: accuracy, LIME, contrastive, explainability, pertinent positives, pertinent negatives

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

# Contrastive explanations
{: #ie-pp-pn}

For contrastive explanations, {{site.data.keyword.aios_short}} displays the maximum changes for the same outcome and the minimum changes for a changed outcome. These categories are also known as pertinent positive and pertinent negative values. These values help explain the behavior of the model in the vicinity of the data point for which an explanation is generated. You can use the **Explain** tab to see how the model made the prediction and you can use the **Inspect** tab to experiment with features by changing the values to see how you can change the outcome.
{: shortdesc}

While the charts are useful in showing the most significant factors in determining the outcome of a transaction, classification models can also include advanced explanations on the **Explain** and **Inspect** tabs.

- The **Explain** tab, in addition to basic information about the transaction and model, displays the following information:
  
  - Predicted outcome: The outcomes are set in the model.
  - How this prediction was determined: 
  - Confidence level: 
  - Features influencing this prediction: 
  
- The **Inspect** tab displays the following information:
  
  - Feature: The feature from the model. If the model was created with additional meta fields that were not used in training, you have the option of viewing only those features by selecting the **Analyze controllable features only** option.
  - Original value: The original value used in training the model.
  - New value: You can enter a new value for one or more features to see how it might change the outcome. Change a value and click the **Score new values** button.
  - Value for a different outcome: After you run an analysis, you can see what are the mostly likely settings to change the outcome.
  - Importance: After you run an analsysis, you can see what the relative importance is for each changed feature value.


Consider an example of a model used for loan processing. It can have the following predictions: **Loan Approved**, **Loan Partially Approved**, and **Loan Denied**. For the sake of simplicity, assume that the model takes only one feature in input: salary. Consider a data point where the salary=150000 and the model predicts Loan Partially Approved. Assume that the median value of salary is 90000. A pertinent positive might be: Even if the salary of the person was 100000, the model still predicts Loan Partially Approved. Alternatively, the pertinent negative is: If the salary of the person was 200000, the model prediction would change to Loan Approved. Thus pertinent positive and pertinent negative together explain the behavior of the model in the vicinity of the data point for which the explanation is generated.
 
{{site.data.keyword.aios_short}} always displays a pertinent positive sometimes there are no pertinent negatives to be displayed. When {{site.data.keyword.aios_short}} calculates the pertinent negative value, it changes the values of all the features away from their median value. If the value changes away from median, the prediction does not change, then there are no pertinent negatives to display. For pertinent positives, {{site.data.keyword.aios_short}} finds the maximum change in the feature values towards the median such that the prediction does not change. Practically, there is almost always a pertinent positive to explain a transaction (and it might be the feature value of the input data point itself).

