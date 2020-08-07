---

copyright:
  years: 2018, 2020
lastupdated: "2020-05-18"

keywords: accuracy, text, unstructured, unstructured text, pandas, explainability

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

# Working with unstructured text models
{: #ie-unstruct-steps}

{{site.data.keyword.aios_short}} supports explainability for unstructured text data. You must complete the following steps to set up your environment. For information about configuring support for non-space-delimited languages, such as Japanese, Chinese, and Korean, see [Enabling non-space-delimited language support](/docs/ai-openscale?topic=ai-openscale-explainability-monitor#ie-unstruct-xplan-langsupport)

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

7. Configure {{site.data.keyword.aios_short}} by assigning the `APIClient`, subscribing the asset and scoring the model.
8. Configure explainability.
   9. Enable the explainability.
   10. Get explanations for the transactions.

Fairness and drift metrics are not supported for unstructured (image or text) data types.
{: note}

## Next steps
{: #ie-unstruct-text-next}

[Explaining unstructured text models](/docs/ai-openscale?topic=ai-openscale-ie-ov#ie-unstruct)