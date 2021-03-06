---

copyright:
  years: 2018, 2020
lastupdated: "2020-08-08"

keywords: fairness, monitoring, charts, debiasing, bias, accuracy

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
{:faq: data-hd-content-type='faq'}

# Understanding how debiasing works
{: #mf-debias}

{{site.data.keyword.aios_short}} corrects for both direct and indirect bias by using a scoring endpoint.
{: shortdesc}

The debiased scoring endpoint can be used exactly as the normal scoring endpoint of your deployed model. In addition to returning the response of your deployed model, it also returns the `debiased_prediction` and `debiased_probability` columns.

- The `debiased_prediction` column contains the debiased prediction value. In {{site.data.keyword.pm_full}}, this column is an encoded representation of the prediction. For example, if the model prediction is either "Loan Granted" or "Loan Denied", {{site.data.keyword.pm_full}} can encode these two values to "0.0" and "1.0". The `debiased_prediction` column contains such an encoded representation of the debiased prediction. If you specify a string column as prediction column, `debiased_prediction` column can also contain a string value.

- The `debiased_probability` column represents the probability of the debiased prediction. This array of double values represents the probability of the debiased prediction that belongs to one of the prediction classes.

- The `debiased_decoded_target` column still exists in the response, but it contains the same value as the one in the `debiased_prediction` column. Because there is no mapping set in the **Model details** wizard, you can now directly specify the string column as a prediction column.

- The `debiased_decoded_target` column contains the string representation of the debiased prediction. In the previous example, where the prediction value was either "0.0" or "1.0", the `debiased_decoded_target` contains either "Loan Granted" or "Loan Denied".

## Steps to check the debias endpoint
{: #mf-debias-steps}

To check the debias endpoint, from the **Endpoint** box, select **Debiased transactions**. You can then view and copy the endpoint in different formats, such as cURL, Java, or Python. 

Ideally, you would directly call this endpoint from your production application, instead of directly calling the scoring endpoint of your model that is deployed in your machine learning provider. {{site.data.keyword.aios_short}} stores the `debiased` values in the payload logging table of your model deployment. Then, all scoring done through this endpoint is automatically debiased.

Because this endpoint deals with runtime bias, it continues to run background checks for the scoring data from the payload logging table. It keeps updating the bias mitigation model, which is used to debias the scoring requests sent. In this way, {{site.data.keyword.aios_short}} is always up to date with the incoming data, and with its behavior to detect and mitigate bias.

Finally, {{site.data.keyword.aios_short}} uses a threshold to decide that data is now acceptable and is deemed to be unbiased. That threshold is taken as the least value from the thresholds set in the Fairness monitor for all the fairness attributes configured.

## Indirect bias
{: #mf-debias-indirect}

Indirect bias occurs when one feature can be used to stand for another. For example, one feature in a model might approximate another feature that is a protected attribute. However, it would be illegal to discriminate based on race because race can sometimes track closely with postal code, it might be the cause of indirect bias. In like manner, if you had access to a person's music tastes you might be able to determine a person's age. Or, if you had access to purchase history, you might determine a person's sex. Even if your predictive model had none of the protected attributes, such as race, age, or sex by using proxies your model might produce biased results.

{{site.data.keyword.aios_short}} analyzes indirect bias when the following conditions are met:

- To find correlations, the data set must be sufficiently large (more than 4000 records).
- The training data must include the meta fields. You must train the model on a subset of data fields. These additional fields, the meta fields, are for determining indirect bias. (Include the meta fields, but don't use them in model training.)
- Payload logging must contain meta fields and be run before the fairness monitor is configured. You must use this method to upload the meta fields to the {{site.data.keyword.aios_short}} service. Payload logging for indirect bias requires two types of input: 1) training features with values and 2) meta fields with values.
- When you configure the fairness monitor, select the additional fields to monitor.

### Typical workflow for indirect bias
{: #mf-debias-indirect-workflow}

You can determine indirect bias for preproduction and production models, however, the models require different columns. The test data that is used to evaluate preproduction models and the feedback data that is used to evaluate either preproduction or production models differ on the use of meta columns. Meta columns are required for the test data for preproduction and cannot be included in the feedback data that is used for production models. A typical workflow, might include the following steps:

1. Create training data that contains both feature columns and meta columns. The meta columns contain data that is not used to train the model.
2. In {{site.data.keyword.aios_short}}, configure the fairness monitor with the meta columns.
3. During preproduction, upload test data that contains both the feature columns and the meta columns.
4. During pre-production, you might interate on different versions of the model while using the indirect bias measures to ensure that your final model will be free of bias.
4. After you send the model to production, the feedback data should not have any of the meta columns, only the feature columns that were used to train the model.



### Sample JSON payload file with meta fields
{: #mf-debias-indirect-sample-json}

The following sample file shows a JSON payload with the fields and values that are used to train the model. The meta fields and values that are used for the indirect bias analysis are also included. The meta fields are not used to train the model, instead they are reserved for a different kind of analysis that attempts to correlate them to bias in the model. Although the meta fields can be any type of data, they are usually protected attributes, such as sex, race, or age.

```
[{
	"request": {
		"fields": ["AGE", "BP", "CHOLESTEROL", "NA", "K"],
		"values": [
			[28, "LOW", "HIGH", 0.61, 0.026]
		],
		"meta": {
			"fields": ["SEX"],
			"values": [
				["F"]
			]
		}
	},
	"response": {
		"fields": ["AGE", "BP", "CHOLESTEROL", "NA", "K", "probability", "prediction", "DRUG"],
		"values": [
			[28, "LOW", "HIGH", 0.61, 0.026, [0.82, 0.07, 0.0, 0.05, 0.03], 0.0, "drugY"]
		]
	},
	"binding_id": "3cbede08-0626-4035-8a00-9546081a0a65",
	"subscription_id": "8be283de-cbce-40d6-888b-706f85795866",
	"deployment_id": "b799de0c-da58-4145-8532-97d04778ad33"
}]
```

Meta values must be in the format of an array of arrays:

```
"meta": {
"fields": ["age", "race", "sex"],
"values": [
[32, "Black", "Male"]
]
}

```

### Configuring the {{site.data.keyword.aios_short}} service for indirect bias
{: #mf-debias-indirect-steps}

When you set up the fairness monitor, select the fields to monitor. Include both training features and fields that are excluded from model training. If you select a field that is excluded from model training, {{site.data.keyword.aios_short}} finds correlations between values in that field and values in the training features. The correlated features are used as proxies for the fields that were excluded from model training.

![Indirect bias displays](images/wos-indirect-bias.png)

Some fields are training features. Others fields that are not training features are identified as meta fields. For the selected meta fields, {{site.data.keyword.aios_short}} checks for indirect bias.


## Next steps
{: #wos-debias-next-steps}

- For more information, see [Debiasing options](/docs/ai-openscale?topic=ai-openscale-it-dbo).
- For a Notebook for indirect bias, see [Mitigating Indirect Bias with Watson OpenScale](https://github.com/pmservice/ai-openscale-tutorials/blob/master/notebooks/Watson%20OpenScale%20indirect%20bias.ipynb){: external}.