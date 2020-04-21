---

copyright:
  years: 2018, 2020
lastupdated: "2020-04-18"


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
{:faq: data-hd-content-type='faq'}
{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}

# Troubleshooting the {{site.data.keyword.aios_short}} service
{: #ts-trouble}

You can use the following techniques to work around problems with {{site.data.keyword.aios_full}}.
{: shortdesc}

## Common issues for {{site.data.keyword.aios_short}}
{: #ts-trouble-common}

The following issues are common for both {{site.data.keyword.aios_full}} on Cloud and {{site.data.keyword.wos4d_full}}.

## When I use AutoAI, why am I getting an error about mismatched data?
{: #ts-trouble-common-autoai-binary}
{: troubleshoot}
{: support}

You receive an error message about mismatched data when using AutoAI for binary classification. Note that AutoAI is only supported in {{site.data.keyword.wos4d_full}}. 
{: tsSymptoms} 

For binary classification type, AutoAI automatically sets the data type of the prediction column to boolean. 
{: tsCauses}

To fix this, implement one of the following solutions:
{: tsResolve}

- Change the label column values in the training data to integer values, such as `0` or `1` depending on the outcome.
- Change the label column values in the training data to string value, such as `A` and `B`.

## Why am I getting errors during model configuration?
{: #ts-trouble-common-xgboost-wml-model-details}
{: troubleshoot}
{: support}

The following error messages appear when you are configuring model details: **Field `feature_fields` references column `<name>`, which is missing in `input_schema` of the model. Feature not found in input schema.**
{: tsSymptoms} 

The preceding messages while completing the **Model details** section during configuration indicate a mismatch between the model input schema and the model training data schema:
{: tsCauses}

To fix the issue, you must determine which of the following conditions is causing the error and take corrective action: If you use {{site.data.keyword.pm_full}} as your machine learning provider and the model type is XGBoost/scikit-learn refer to the {{site.data.keyword.pm_short}} [Python SDK documentation](http://wml-api-pyclient-dev.mybluemix.net/#repository){: external} for important information about how to store the model. To generate the drift detection model, you must use scikit-learn version 0.20.2 in notebooks. For all other cases, you must ensure that the training data column names match with the input schema column names.
{: tsResolve}

## Why are my class labels missing when I use XGBoost?
{: #ts-trouble-common-xgboost-multiclass}
{: troubleshoot}
{: support}

Native XGBoost multiclass classification does not return class labels.
{: tsSymptoms} 

By default, for binary and multiple class models, the XGBoost framework does not return class labels.
{: tsCauses}

For XGBoost binary and multiple class models, you must update the model to return class labels.
{: tsResolve}

## Why are the payload analytics not displaying properly?
{: #ts-trouble-common-payloadfileformat}
{: troubleshoot}
{: support}

Payload analytics does not display properly and the following error message displays: **AIQDT0044E Forbidden character `"` in column name `<column name>`**
{: tsSymptoms} 

For proper processing of payload analytics, {{site.data.keyword.aios_short}} does not support column names with double quotation marks (") in the payload. This affects both scoring payload and feedback data in CSV and JSON formats.
{: tsCauses}

Remove double quotation marks (") from the column names of the payload file.
{: tsResolve}

## Why are some of my active debias records missing?
{: #ts-trouble-common-payloadlogging-1000k-limit}
{: troubleshoot}
{: support}

Active debias records do not reach the payload logging table.
{: tsSymptoms}

When you use the active debias API, there is a limit of 1000 records that can be sent at one time for payload logging.
{: tsCauses}

To avoid loss of data, you must use the active debias API to score in chunks of 1000 records or fewer.
{: tsResolve}

## Specific issues for {{site.data.keyword.wos4d_full}}
{: #ts-trouble-icp4d-only}

The following issues are specific to {{site.data.keyword.wos4d_full}}.

## When creating a subscription, why do I get an error?
{: #ts-trouble-icp4d-pod-restart}
{: troubleshoot}
{: support}

The following error applies to {{site.data.keyword.wos4d_full}} version 2.1.0.2 and version 2.5.0. You may see the following error display: **Action Create Payload Tables has failed: Invalid token**.
{: tsSymptoms}

In addition to that UI message, the dashboard service log might contain the following entry:

```
[ERROR] [aiops-dashboard] [configuration-routes] {"error":"Unexpected status code 500 from PUT API http://ai-open-scale-ibm-aios-nginx-internal/v1/data_marts/00000000-0000-0000-0000-000000000000/service_bindings/999/subscriptions/093ee84d-5a59-49fb-a367-1932ad3403df/configurations/payload_logging","statusCode":500,"globalTransactionId":"c3789a70-de41-46a2-979f-890c07eaad98","errors":[{"code":"AIQCS0046E","message":"Action Create Payload Tables has failed: Invalid token"}]}
```

The configuration service log might contain the following entry:

```
ApiRequestFailure: Failure during payload logging setup. (PUT https://icpd-aios-cluster1.cpolab.ibm.com:31843/v1/data_marts/00000000-0000-0000-0000-000000000000/service_bindings/999/subscriptions/093ee84d-5a59-49fb-a367-1932ad3403df/configurations/payload_logging) Status code: 500, body: {“errors”:[{“code”:“AIQCS0046E”,“message”:“Action Create Payload Tables has failed: Invalid token”}], “trace”:“N2RmNWViMTItMTc4Zi00MWM5LTkyMmUtZDEwYzg1NGJmZDA0”}
```

The access token used by the payload logging, configuration, and datamart processes has become invalid. Restarting these processes will generate a new, valid token.
{: tsCauses}


When this happens, it can be resolved by restarting the following pods:
{: tsResolve}

- aiopenscale-ibm-aios-payload-logging
- aiopenscale-ibm-aios-payload-logging-api
- aiopenscale-ibm-aios-configuration
- aiopenscale-ibm-aios-datamart

## Missing deployments
{: #ts-trouble-icp4d-missing-deployment}

A deployed model does not show up as a deployment that can be selected to create a subscription.
{: tsSymptoms}

There are different reasons that a deployment does not show up in the list of available deployed modes. If the model is not a supported type of model because it uses an unsupported algorithm or framework, it won't appear. Your machine learning provider might not be configured properly. It could also be that there are issues with permissions.
{: tsCauses}

Use the following steps to resolve this issue:
{: tsResolve}

1. Check that the model is a supported type. Not sure? For more information, see [Supported machine learning engines, frameworks, and models](/docs/ai-openscale-icp?topic=ai-openscale-icp-in-ov).
2. Check that a machine learning provider exists in the {{site.data.keyword.aios_short}} configuration for the specific deployment space. For more information, see [Deployment spaces](https://www.ibm.com/support/producthub/icpdata/docs/content/SSQNUZ_current/wsj/analyze-data/ml-spaces_local.html){: external}.
3. Check that the CP4D `admin` user has permission to access the deployment space. 

