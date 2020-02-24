---

copyright:
  years: 2018, 2020
lastupdated: "2020-01-28"

keywords: risk, governance, model risk management, model risk governance

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
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}
{:faq: data-hd-content-type='faq'}

# Manage model risk ![beta tag](images/beta.png)
{: #mrm-risk-wos-only}

IBM offers a model risk management solution for financial services with IBM Watson OpenScale. IBM Watson OpenScale monitors and measures outcomes from AI Models across its lifecycle and performs model validations.
{: shortdesc}

## Perform analysis in Watson OpenScale

After you set up and activate the model risk management features, you can both see and compare the sample evaluations in Watson OpenScale. There is a downloadable report, the Model Summary Report, that includes all the quality measures, fairness measures, and drift magnitude.

1. From the Insights dashboard, click the model deployment tile
2. From the Actions drop-down box, click one of the following analysis options:
   
   1. Past evaluations: Lists all the previous versions of the evaluation. 
   2. Compare: Compare any of the models, but especially versions of the same model, for best performance.
   3. Download report PDF: Generates the model summary report, which gives you all of the metrics and the explanation for why they were scored the way they were. 

## Deploy a new model to production in Watson OpenScale

Push the best model to production. Create a production record by importing from a pre-production model. After the model is approved for deployment in IBM OpenPages, you can send the model to production in Watson OpenScale. 

1. Review the status of the model deployment:
2. Return to the sample beta notebook and run the cells to send the model to production.
3. You can now view the production model deployment tile. In a regular production environment, it initially appears empty until enough data is gathered and time has passed for metric calculation to be triggered. For the beta, the notebook adds data and runs the monitors so that you can see the results right away.

## Next steps
{: #mrm-risk-wos-only-next}

Use the analysis of fairness to redefine the model, possibly by using a different algorithm. 
Watson OpenScale enables you to compare models by looking at the key metrics in a side-by-side comparison. Use this feature to determine which version of a model is the best one to send to production or which model might need work:

