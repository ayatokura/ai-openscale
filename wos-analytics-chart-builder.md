---

copyright:
  years: 2018, 2020
lastupdated: "2020-05-18"

keywords: fairness, fairness monitor, payload, perturbation, training data, debiased

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

# Chart builder
{: #chart_builder}

Use the {{site.data.keyword.aios_short}} chart builder to create custom visualizations, so you can better understand model predictions and inputs at run time. The chart builder displays the output of the model’s prediction against the features or data ranges that a business considers important. It helps uncover new trends in the data, which might prompt the business and data science teams to consider changes to the AI model. 
{: shortdesc}

For example, if you're familiar with the credit risk model from the tutorials, you can see the split in predicted classes for different ranges of the attribute Credit History. 

   ![A chart that shows feature prediction for gender by the feature age](images/wos_by_custom_chart.png)
      
   You can also see how confident the model predicts within this range of credit history. You can analyze the scoring payload that is sent to your deployment in the selected data range by custom chart (selecting between features, prediction classes, and confidence).

   ![A chart that shows feature prediction for gender by the feature age](images/wos_by_custom_chart002.png)
   
