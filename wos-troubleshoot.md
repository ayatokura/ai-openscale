---

copyright:
  years: 2018, 2019
lastupdated: "2019-11-22"


keywords: troubleshooting, bias

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

# Troubleshooting
{: #ts-trouble}

## Common issues for {{site.data.keyword.aios_short}}
{: #ts-trouble-common}

The following issues are common for both {{site.data.keyword.aios_full}} on Cloud and {{site.data.keyword.wos4d_full}}.

### AutoAI automatically sets the data type of the prediction to binary
{: #ts-trouble-common-autoai-binary}

For binary classification type, AutoAI automatically sets the data type of the prediction column to boolean. You can troubleshoot this situation by implementing one of the following solutions:

- Change the label column values in the training data to integer values, such as `0` or `1` depending on the outcome.
- Change the label column values in the training data to string value, such as `A` and `B`.

### Issues configuring model details
{: #ts-trouble-common-xgboost-wml-model-details}

The following messages while completing the **Model details** section during configuration indicate a mismatch between the model input schema and the model training data schema:

- Field `feature_fields` references column `<name>`, which is missing in `input_schema` of the model.
- Feature not found in input schema

To fix the issue, you must determine which of the following conditions is causing the error and take corrective action:

- If you use {{site.data.keyword.pm_full}} as your machine learning provider and the model type is XGBoost/scikit-learn refer to the {{site.data.keyword.pm_short}} [Python SDK documentation](http://wml-api-pyclient-dev.mybluemix.net/#repository){: external} for important information about how to store the model. To generate the drift detection model, you must use scikit-learn version 0.20.2 in notebooks. 

- For all other cases, you must ensure that the training data column names match with the input schema column names.

### Native XGBoost multiclass classification does not return class labels
{: #ts-trouble-common-xgboost-multiclass}

For XGBoost binary and multiple class models, you must update the model to return class labels.

### Payload analytics does not display properly
{: #ts-trouble-common-payloadfileformat}

- Situation: The following error message displays:
  - error code: AIQDT0044E
  - error text: Forbidden character `"` in column name `<column name>`

- Situation: For proper processing of payload analytics, {{site.data.keyword.aios_short}} does not support column names with double quotation marks (") in the payload. This affects both scoring payload and feedback data in CSV and JSON formats.
- Solution: Remove double quotation marks (") from the column names of the payload file.

### Active debias records do not reach the payload logging table
{: #ts-trouble-common-payloadlogging-1000k-limit}

When you use the active debias API, there is a limit of 1000 records that can be sent at one time for payload logging.

To avoid loss of data, you must use the active debias API to score in chunks of 1000 records or fewer.

