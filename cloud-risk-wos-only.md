---

copyright:
  years: 2018, 2020
lastupdated: "2020-05-18"

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
{:faq: data-hd-content-type='faq'}

# Manage model risk
{: #mrm-risk-wos-only}

IBM offers a model risk management solution with {{site.data.keyword.aios_full}}. {{site.data.keyword.aios_full}} monitors and measures outcomes from AI Models across its lifecycle and performs model validations.
{: shortdesc}

## Perform analysis in {{site.data.keyword.aios_short}}
{: #mrm-risk-wos-only-perform-analysis}

After you set up and activate the model risk management features, you can both see and compare the sample evaluations in {{site.data.keyword.aios_short}}. There is a downloadable report, the Model Summary Report, that includes all the quality measures, fairness measures, and drift magnitude.

![MRM summary dashboard](/images/wos-mrm-preprod.png)


1. From the Insights dashboard, click the model deployment tile
2. From the Actions drop-down box, click one of the following analysis options:
   
   1. Past evaluations: Lists all the previous versions of the evaluation. 
   2. Compare: Compare any of the models, but especially versions of the same model, for best performance.
   3. Download report PDF: Generates the model summary report, which gives you all of the metrics and the explanation for why they were scored the way they were. 

## Deploy a new model to production in {{site.data.keyword.aios_short}}
{: #mrm-risk-wos-only-deploy-to-prod}

Push the best model to production. Create a production record by importing from a pre-production model. After the model is approved for deployment in IBM OpenPages, you can send the model to production in {{site.data.keyword.aios_short}}. 

1. Review the status of the model deployment:
2. Return to the sample notebook and run the cells to send the model to production.
3. You can now view the production model deployment tile. In a regular production environment, it initially appears empty until enough data is gathered and time has passed for metric calculation to be triggered. For the tutorial, the notebook adds data and runs the monitors so that you can see the results right away.

## Compare models
{: #mrm-risk-wos-only-compare-between}

{{site.data.keyword.aios_short}} enables you to compare models by looking at the key metrics in a side-by-side comparison. Use this feature to determine which version of a model is the best one to send to production or which model might need work.

From the **Actions** menu, select a model to compare to the currently displayed in the MRM Summary dashboard.

## Evaluate Now 
{: #mrm-risk-wos-only-evaluate-now-opt}

In the pre-production environment, you can upload test data in the form of a CSV file, a database table, or a cloud object storage file. To use the CSV option, drag the CSV file to the drop box. To use the Db2 or cloud storage options, you must supply credentials. After you upload the data, you can immediately see results by evaluating the new data against the model.

Connections to the database options are transient. To perform the evaluation a subsequent time, you must reenter the connection information.
{: note}

## Copy configuration from a pre-production subscription to a production subscription
{: #mrm-risk-wos-only-copy-configuration}

To save time, you can copy configuration and model metadata from a pre-production subscription to a production subscription. To do this, the model must be an identical match to the source model, but deployed to the production space.


## Next steps
{: #mrm-risk-wos-only-next}

Use the analysis of fairness to redefine the model, possibly by using a different algorithm. 
