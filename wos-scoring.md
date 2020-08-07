---

copyright:
  years: 2018, 2020
lastupdated: "2020-05-18"

keywords: databases, connections, scoring, requests

subcollection: ai-openscale

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}
{:screen: .screen}
{:faq: data-hd-content-type='faq'}

# Sending a scoring request
{: #cdb-score}

To configure monitors, you must send a scoring payload to log the data to be monitored.
{: shortdesc}

- For models deployed in {{site.data.keyword.pm_full}}, you must score your model by using {{site.data.keyword.pm_full}} API. The scoring payload is automatically sent to {{site.data.keyword.aios_short}} when you score the model.
- For other machine learning engines, such as Microsoft Azure, Amazon SageMaker, or a custom machine learning engine the scoring payload must be sent by using the Payload Logging API. For more information, see [Payload logging for non-{{site.data.keyword.pm_full}} service instances](/docs/ai-openscale?topic=ai-openscale-cml-connect).

## Steps for payload logging
{: #cdb-score-apisteps}
{: help} 
{: support}

1. From the {{site.data.keyword.aios_short}} dashboard, click a deployment tile.
2. Click **Configure monitors**. 
3. In the navigation pane, click **Payload logging**.
2. Choose whether to use the `cURL` or `Python` code by clicking the `cURL` or `Python` tab.
3. Click **Copy to clipboard** and paste it into to log model deployment request and response data. For more information, see [Payload logging for non-{{site.data.keyword.pm_full}} service instances](/docs/ai-openscale?topic=ai-openscale-cml-connect).

The fields and values in the code snippets need to be substituted with your real values, as the ones provided are only examples.
{: important}

![Select database](images/wos-config-send-scoring.png)

After you run your payload logging, a check mark appears in the **Ready to Monitor** column for the selected deployment. Click **Configure Monitors** to continue.

## Payload logging fields
{: #cdb-score-fields-values}

The following table describes the fields that make up a typical payload logging request.

| Field | Description |
|:----|:-----|
| scoring_id | ID of the scoring transaction. |
| response_time | The time (ms) taken to make prediction (for performance monitoring). |
| request | The `request` section specifies fields and values for both the training data and the meta data, which are features that you can use to measure indirect bias |
| fields |   |
| values |   |
| meta | The `meta` section specifies fields and values for the meta data. |
| fields | Lists the fields for the meta data. |
| values | Lists the values for the meta data. |
| response | The `response` section specifies the fields and values of the result. |
| fields |   |
| values |   |
| binding_id |   |
| subscription_id |   |
| deployment_id |   |
{: row-headers}
{: class="comparison-table"}
{: caption="Table 1. Payload logging fields" caption-side="top"}
{: summary="The table provides detailed descriptions of the fields that you find in a typical payload logging request."}
{: #payloadloggingfieldstable1}


```
# Generate an IAM access token by passing an API key as $APIKEY in the request below
# See: https://cloud.ibm.com/docs/iam?topic=iam-iamtoken_from_apikey

curl -k -X POST \
--header "Content-Type: application/x-www-form-urlencoded" \
--header "Accept: application/json" \
--data-urlencode "grant_type=urn:ibm:params:oauth:grant-type:apikey" \
--data-urlencode "apikey=$APIKEY" \
"https://iam.cloud.ibm.com/identity/token"

# the above CURL request will return an auth token that you will use as $IAM_TOKEN in the payload logging request below
# TODO: manually define and pass:
# request - input to scoring endpoint in supported by Watson OpenScale format - replace sample fields and values with proper ones
# response - output from scored model in supported by Watson OpenScale format - replace sample fields and values with proper ones
# - $SCORING_ID - ID of the scoring transaction
# - $SCORING_TIME - Time (ms) taken to make prediction (for performance monitoring)

SCORING_PAYLOAD='[{
  "scoring_id": "$SCORING_ID",
  "response_time": "$SCORING_TIME",
  "request": {
    "fields": ["AGE", "BP", "CHOLESTEROL", "NA", "K"],
    "values": [[28, "LOW", "HIGH", 0.61, 0.026]],
    "meta": {
      "fields": ["SEX"],
      "values": [["F"]]
    }
  },
  "response": {
    "fields": ["AGE", "BP", "CHOLESTEROL", "NA", "K", "probability", "prediction", "DRUG"],
    "values": [[28, "LOW", "HIGH", 0.61, 0.026, [0.82, 0.07, 0.0, 0.05, 0.03], 0.0, "drugY"]]
  },
  "binding_id": "60dcc83f-e0f3-4b97-86b3-53fcb3928be5",
  "subscription_id": "f6abbabb-ba6e-42c8-831c-00eaa57675de",
  "deployment_id": "7cba4363-3267-4ad6-adc8-fdbd1a5e6043"
}]'

curl -X POST https://aiopenscale-dev.us-south.containers.appdomain.cloud/v1/data_marts/5d2949f3-6ca1-44c8-940b-1609e29c80cc/scoring_payloads -d "$SCORING_PAYLOAD" \
--header 'Content-Type: application/json' --header 'Accept: application/json' --header "Authorization: Bearer $IAM_TOKEN"
```


```
from ibm_ai_openscale import APIClient
from ibm_ai_openscale.supporting_classes import PayloadRecord

# "apikey" is IBM Cloud API key
# It can be generated using following link https://cloud.ibm.com/iam#/apikeys

aios_credentials = {
                      "instance_guid": "5d2949f3-6ca1-44c8-940b-1609e29c80cc",
                      "apikey": "***",
                      "url": "https://aiopenscale-dev.us-south.containers.appdomain.cloud"
                   }

client = APIClient(aios_credentials)
subscription = client.data_mart.subscriptions.get(subscription_uid="f6abbabb-ba6e-42c8-831c-00eaa57675de")

"""
request_data - input to scoring endpoint in supported by Watson OpenScale format
response_data - output from scored model in supported by Watson OpenScale format
response_time - scoring request response time [ms] (integer type)

Example:

request_data = {
    "fields": ["AGE", "BP", "CHOLESTEROL", "NA", "K"],
    "values": [[28, "LOW", "HIGH", 0.61, 0.026]],
    "meta": {
      "fields": ["SEX"],
      "values": [["F"]]
    }
  }

response_data = {
    "fields": ["AGE", "BP", "CHOLESTEROL", "NA", "K", "probability", "prediction", "DRUG"],
    "values": [[28, "LOW", "HIGH", 0.61, 0.026, [0.82, 0.07, 0.0, 0.05, 0.03], 0.0, "drugY"]]
  }
"""

request_data = <put your data here>
response_data = <put your data here>

records = [PayloadRecord(request=request_data, response=response_data, response_time=18), 
                PayloadRecord(request=request_data, response=response_data, response_time=12)]

subscription.payload_logging.store(records=records)
```

## Understanding the number of scoring requests
{: #cdb-score-capacity}
{: help} 
{: support}

Scoring requests are a part of {{site.data.keyword.aios_short}} processing. Each transaction record that you send to the model to be scored generates extra processing so that the {{site.data.keyword.aios_short}} service perturbs data and creates explanations.

- For tabular, text, or image models the following baseline request generates data points:

   - 1 scheduling service scoring request generates 5000 data points.

- For tabular classification models only, there are more scoring requests that are made for contrastive explanation. The following requests are added to the preceding baseline request:

   - One hundred (100) scoring requests generate 51 additional data points per request.
   - One hundred one (101) scoring requests generate 1 additional data point per request.


## Next steps
{: #cdb-score-next-steps-scoringreq}

[Configure monitors](/docs/ai-openscale?topic=ai-openscale-mo-config).
