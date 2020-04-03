---

copyright:
  years: 2018, 2020
lastupdated: "2020-04-08"

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
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}
{:screen: .screen}
{:note: .note}
{:note: .note}
{:note: .note}
{:note: .note}
{:faq: data-hd-content-type='faq'}

# Understanding how de-biasing works
{: #mf-debias}

To check the debias endpoint, from the **Endpoint** box, select **Debiased transactions**. You can then view and copy the endpoint in different formats, such as cURL, Java, or Python. 

The de-biased scoring endpoint can be used exactly as the normal scoring endpoint of your deployed model. In addition to returning the response of your deployed model, it also returns the `debiased_prediction` and `debiased_probability` columns.

- The `debiased_prediction` column contains the debiased prediction value. In {{site.data.keyword.pm_full}}, this column is an encoded representation of the prediction. For example, if the model prediction is either "Loan Granted" or "Loan Denied", {{site.data.keyword.pm_full}} can encode these two values to "0.0" and "1.0". The `debiased_prediction` column contains such an encoded representation of the debiased prediction. If you specify a string column as prediction column, `debiased_prediction` column can also contain a string value.

- The `debiased_probability` column represents the probability of the debiased prediction. This is an array of double value, where each value represents the probability of the de-biased prediction that belongs to one of the prediction classes.

- The `debiased_decoded_target` column still exists in the response, but it contains the same value as the one in the `debiased_prediction` column. Because there is no mapping set in the **Model details** wizard, you can now directly specify the string column as a prediction column.

- The `debiased_decoded_target` column contains the string representation of the debiased prediction. In the previous example, where the prediction value was either "0.0" or "1.0", the `debiased_decoded_target` contains either "Loan Granted" or "Loan Denied".

Ideally, you would directly call this endpoint from your production application, instead of directly calling the scoring endpoint of your model that is deployed in your machine learning provider ({{site.data.keyword.pm_full}}, Amazon Sagemaker, Microsoft Azure ML Studio, etc.) This way, {{site.data.keyword.aios_short}} also stores the `debiased` values in the payload logging table of your model deployment. Then, all scoring done via this endpoint would be automatically de-biased.

Because this endpoint deals with runtime bias, it continues to run background checks for the scoring data from the payload logging table. It keeps updating the bias mitigation model, which is used to debias the scoring requests sent. In this way, {{site.data.keyword.aios_short}} is always up to date with the incoming data, and with its behavior to detect and mitigate bias.

Finally, {{site.data.keyword.aios_short}} uses a threshold to decide that data is now acceptable and is deemed to be unbiased. That threshold is taken as the least value from the thresholds set in the Fairness monitor for all the fairness attributes configured.

## Next steps
{: #wos-debias-next-steps}

For more information, see [Debiasing options](/docs/ai-openscale?topic=ai-openscale-it-dbo)