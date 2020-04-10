---

copyright:
  years: 2018, 2020
lastupdated: "2020-04-08"

keywords: accuracy, 

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
{:note: .note}
{:note: .note}
{:note: .note}
{:note: .note}
{:faq: data-hd-content-type='faq'}

# Working with unstructured text models
{: #ie-unstruct-steps}

{{site.data.keyword.aios_short}} supports explainability for unstructured text data. You must complete the following steps to set up your environment.
{: shortdesc}

1. Set up your environment.
   2. Install the {{site.data.keyword.aios_short}} and {{site.data.keyword.pm_full}} packages.
   3. Configure your credentials.
   4. Install the libraries that are needed for creating the models and doing analysis. These include the following libraries:
      - `pandas`
      - `pyspark` (if not using {{site.data.keyword.DSX}})

1. Create and deploy your text-based model.
   2. Load training data into a pandas frame.
   2. Train the model on the data.
   3. Publish the model.
   4. Deploy and score the model.

7. Configure {{site.data.keyword.aios_short}} by assigning the `APIClient`, sbuscribing the asset and scoring the model.
8. Configure explainability.
   9. Enable the explainability.
   10. Get explanations for the transactions.

Fairness and drift metrics are not supported for unstructured (image or text) data types.
{: note}

## Next steps
{: #ie-unstruct-text-next}

[Explaining unstructured text models](/docs/services/ai-openscale?topic=ai-openscale-ie-unstruct)