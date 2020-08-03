---

copyright:
  years: 2018, 2020
lastupdated: "2020-05-18"

keywords: fairness, monitoring, charts, debiasing, bias, accuracy, tabular model, table

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

# Working with tabular models
{: #ie-tabular}

{{site.data.keyword.aios_short}} supports explainability for tabular data. You must complete the following steps to set up you environment:
{: shortdesc}

## Steps
{: #ie-tabular-steps}

1. Set up your environment.
   2. Install the {{site.data.keyword.aios_short}} and {{site.data.keyword.pm_full}} packages.
   3. Configure your credentials.
   4. Install the libraries that are needed for creating the models and doing analysis. These include the following libraries:
      - `pandas`
      - `pyspark` (if not using {{site.data.keyword.DSX}})

1. Create and deploy your tabular model.
   2. Load training data into a pandas frame.
   2. Train the model on the data.
   3. Publish the model.
   4. Deploy and score the model.

7. Configure {{site.data.keyword.aios_short}} by assigning the `APIClient`, subscribing the asset and scoring the model.
8. Configure explainability.
   9. Enable the explainability.
   10. Get explanations for the transactions.

## Next steps
{: #ie-tabular-nextsteps}


