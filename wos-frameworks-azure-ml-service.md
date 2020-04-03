---

copyright:
  years: 2018, 2020
lastupdated: "2020-04-08"

keywords: supported frameworks, models, model types, limitations, limits, azure

subcollection: ai-openscale

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:pre: .pre}
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:note: .note}
{:swift: .ph data-hd-programlang='swift'}
{:faq: data-hd-content-type='faq'}

# Microsoft Azure ML Service frameworks
{: #frmwrks-azureservice}

You can use Microsoft Azure ML Service to perform payload logging, feedback logging, and to measure performance accuracy, run-time bias detection, explainability, and auto-debias function in {{site.data.keyword.aios_full}}.
{: shortdesc}

{{site.data.keyword.aios_full}} fully supports the following Microsoft Azure Machine Learning Service frameworks:

Table 1. Framework support details

| Framework | Problem type | Data type |
|:---|:---:|:---:|
| Native | Classification | Structured |
| scikit-learn | Classification | Structured |
| scikit-learn | Regression | Structured |
{: caption="Framework support details" caption-side="top"}

To generate the drift detection model, you must use scikit-learn version 0.20.2 in notebooks. 
{: note}

## Adding Microsoft Azure ML Service to {{site.data.keyword.aios_short}}
{: #frmwrks-azureservice-addsrvc}

You can configure {{site.data.keyword.aios_short}} to work with Microsoft Azure ML Service by using one of the following methods:

- If this is the first time that you are adding a machine learning provider to {{site.data.keyword.aios_short}}, you can use the configuration interface. For more information, see [Specifying a Microsoft Azure ML Service instance](#connect-azureservice).
- You can also add your machine learning provider by using the Python SDK. You must use this method if you want to have more than one provider. For more information on performing this programmatically, see [Bind your Microsoft Azure machine learning engine](#cml-azsrvbind).


{{site.data.keyword.aios_short}} calls various REST endpoints that are needed to interact with the Azure ML Service. To do this, you must bind the Azure Machine Learning Service {{site.data.keyword.aios_short}}.

1. Create an Azure Active Directory Service Principal.
2. Specify the credential details when adding the Azure ML Service service binding, either through the UI or the {{site.data.keyword.aios_short}} Python SDK.

## Requirements for JSON request and response files
{: #frmwrks-azureservice-JSON}

For {{site.data.keyword.aios_short}} to work with Azure ML Service, the web service deployments you create must meet certain requirements. The web service deployments you create must accept JSON requests and return JSON responses, according to the requirements described below.

### Required web service JSON request format
{: #frmwrks-azureservice-JSON-sample-request}

- The REST API request body must be a JSON document that contains one JSON array of JSON objects
- The JSON array must be named `"input"`.
- Each JSON object can only include simple key-value pairs, where the values can only be a string, a number, `true`, `false`, or `null`
- The values cannot be a JSON object or array
- Each JSON object in the array must have all have the same keys (and hence number of keys) specified, regardless of whether or not there is a non-`null` value available


The following sample JSON file meets the preceding requirements and can be used as a template for creating your own JSON request files:


```JSON
{
  "input": [
    {
      "field1": "value1",
      "field2": 31,
      "field3": true,
      "field4": 2.3
    },
    {
      "field1": "value2",
      "field2": 15,
      "field3": false,
      "field4": 0.1
    },
    {
      "field1": null,
      "field2": 5,
      "field3": true,
      "field4": 6.1
    }
  ]
}
```


### Required web service JSON response format
{: #frmwrks-azureservice-JSON-sample-response}

Make note of the following items when you create a JSON response file:

- The REST API response body must be a JSON document that contains one JSON array of JSON objects
- The JSON array must be named `"output"`.
- Each JSON object can only include key-value pairs, where the values can only be a string, a number, `true`, `false`, `null`, or an array that does not contain any other JSON objects or arrays
- The values cannot be a JSON object
- Each JSON object in the array must have all have the same keys (and number of keys) specified, regardless of whether or not there is a non-`null` value available
- For classification models: the web service must return an array of probabilities for each class and the ordering of the probabilities must be consistent for each JSON object in the array
  - Example: suppose you have a binary classification model that predicts credit risk, where the classes are `Risk` or `No Risk`
  - For every result returned back in the "output" array, the objects must contain a key-value pair that includes the probabilities in fixed order, in the form:
  
  <code>"output": [{"Scored Probabilities": [<i>"Risk" probability,"No Risk" probability</i>]}, {"Scored Probabilities": [<i>"Risk" probability,"No Risk" probability</i>]}]</code>

To be consistent with Azure ML visual tools used in both Azure ML Studio and Service, it is recommended, though not required to use the following key names:

- the key name `"Scored Labels"` for the output key that denotes the predicted value of the model
- the key name `"Scored Probabilities"` for the output key that denotes an array of probabilities for each class

The following sample JSON file meets the preceding requirements and can be used as a template for creating your own JSON response files:


```JSON
{
  "output": [
    {
      "Scored Labels": "No Risk",
      "Scored Probabilities": [
        0.8922524675865824,
        0.10774753241341757
      ]
    },
    {
      "Scored Labels": "No Risk",
      "Scored Probabilities": [
        0.8335192848546905,
        0.1664807151453095
      ]
    }
  ]
}
```

## Sample notebooks
{: #frmwrks-azureservice-smpl-ntbks}

The following notebooks show how to work with Microsoft Azure ML Service:

- [MS Azure Service model scoring examples](https://dataplatform.cloud.ibm.com/analytics/notebooks/v2/0d4ebd8d-87cb-4c38-8ba8-37f5623df131/view?access_token=fcb2c411aed913bf94f86f434184db67aef1a6b304824b86b4ad63686e4890be){: external}



## Specifying a Microsoft Azure ML Service instance
{: #connect-azureservice}

Your first step in the {{site.data.keyword.aios_short}} tool is to specify a Microsoft Azure ML Service instance. Your Azure ML Service instance is where you store your AI models and deployments.

{{site.data.keyword.aios_short}} connects to AI models and deployments in a Azure ML Service instance. To connect your service to {{site.data.keyword.aios_short}}, go to the **Configure** ![The configuration tab icon](/images/wos-config-tab.png) tab, add a machine learning provider, and click the **Edit** ![The edit icon](/images/wos-edit-icon.png) icon. In addition to a name and description and whether this is a **Pre-production** or **Production** environment type, you must provide the following information that is specific to this type of service instance:

- Client ID: The actual string value of your client ID, whichverifies who you are and authenticates and authorizes callsthat you make to Azure Service.
- Client Secret: The actual string value of the secret, whichverifies who you are and authenticates and authorizes callsthat you make to Azure Service.
- Tenant: Your tenant ID corresponds to your organization andis a dedicated instance of Azure AD. To find the tenant ID,hover over your account name to get the directory / tenant ID,or select Azure Active Directory > Properties > Directory ID inthe Azure portal.
- Subscription ID: Subscription credentials which uniquelyidentify your Microsoft Azure subscription. The subscription IDforms part of the URI for every service call.

See [How to: Use the portal to create an Azure AD applicationand service principal that can access resources](https://docsmicrosoft.com/en-us/azure/active-directory/develophowto-create-service-principal-portal){: external} for instructions about how to get your Microsoft Azure credentials.
{: note}

You are now ready to select deployed models and configure your monitors. {{site.data.keyword.aios_short}} lists your deployed models on the **Insights** dashboard where you can click the **Add to dashboard** button. Select the deployments you want to monitor and click **Configure**.

For more information, see [Configure monitors](/docs/services/ai-openscale?topic=ai-openscale-mo-config).


## Payload logging with the Microsoft Azure ML Service engine
{: #cml-azsrvconfig}

### Bind your Microsoft Azure ML Service engine
{: #cml-azsrvbind}

A non-{{site.data.keyword.pm_full}} engine is bound as Custom, meaning that this is just metadata; there is no direct integration with the non-{{site.data.keyword.pm_full}} service.
   
```
AZURE_ENGINE_CREDENTIALS = {
"client_id": "***",
"client_secret": "***",
"subscription_id": "***",
"tenant": "***"
}

binding_uid = client.data_mart.bindings.add('My Azure ML Service engine', AzureMachineLearningServiceInstance(AZURE_ENGINE_CREDENTIALS))


bindings_details = client.data_mart.bindings.get_details()
```
{: codeblock}

You can see your service binding with the following command:

```python
client.data_mart.bindings.list()
```
{: codeblock}

The sample output:

```python
uid	                                   name	                      service_type	                   created
410e730f-8462-45fe-8b41-a029d6d6043a	My Azure ML Service engine azure_machine_learning_service2019-06-10T22:10:29.398Z
```
{: codeblock}
    
    
### Add Microsoft Azure ML Service subscription
{: #cml-azsrvsub}

Add subscription

```python
client.data_mart.subscriptions.add(
   AzureMachineLearningAsset(source_uid=source_uid,
                                binding_uid=binding_uid,
                                input_data_type=InputDataType.STRUCTURED,
                                problem_type=ProblemType.MULTICLASS_CLASSIFICATION,
                                label_column='<my_label_column_name>',
                                prediction_column='Scored Labels'))
```
{: codeblock}

Get subscription list

```python
subscriptions = client.data_mart.subscriptions.get_details()

subscriptions_uids = client.data_mart.subscriptions.get_uids()
print(subscriptions_uids)
```
{: codeblock}

### Enable payload logging
{: #cml-azsrvenlog}

Enable payload logging in subscription

```python
subscription.payload_logging.enable()
```
{: codeblock}

Get logging details

```python
subscription.payload_logging.get_details()
```
{: codeblock}

### Scoring and payload logging
{: #cml-azsrvscore}

Score your model. For a full example, see the [Working with Azure Machine Learning Service Engine notebook](https://github.com/pmservice/ai-openscale-tutorials/blob/master/notebooks/AI%20OpenScale%20and%20Azure%20ML%20Studio%20Engine.ipynb){: external}.

Store the request and response in the payload logging table:

```python
records_list = [PayloadRecord(request=request_data, response=response_data, response_time=response_time),
                     PayloadRecord(request=request_data, response=response_data, response_time=response_time)]

for i in range(1, 10):
   records_list.append(PayloadRecord(request=request_data, response=response_data, response_time=response_time))

subscription.payload_logging.store(records=records_list)
```
{: codeblock}
   
For languages other than Python, you can also perform payload logging directly, using a REST API.
   
```
token_endpoint = "https://iam.cloud.ibm.com/identity/token"
headers = {
            "Content-Type": "application/x-www-form-urlencoded",
            "Accept": "application/json"
}

data = {
            "grant_type":"urn:ibm:params:oauth:grant-type:apikey",
            "apikey":aios_credentials["apikey"]
}
   
req = requests.post(token_endpoint, data=data, headers=headers)
token = req.json()['access_token']
```
{: codeblock}
{: json}


```python
import requests, uuid
   
PAYLOAD_STORING_HREF_PATTERN = '{}/v1/data_marts/{}/scoring_payloads'
endpoint = PAYLOAD_STORING_HREF_PATTERN.format(aios_credentials['url'], aios_credentials['data_mart_id'])
   
payload = [{
      'binding_id': binding_uid,
      'deployment_id': subscription.get_details()['entity']['deployments'][0]['deployment_id'],
      'subscription_id': subscription.uid,
      'scoring_id': str(uuid.uuid4()),
      'response': response_data,
      'request': request_data
}]

headers = {"Authorization": "Bearer " + token}
req_response = requests.post(endpoint, json=payload, headers = headers)
print("Request OK: " + str(req_response.ok))
```
{: codeblock}


## Next steps
{: #ca-next-azure-service}

-{{site.data.keyword.aios_short}} is now ready for you to [configure monitors](/docs/services/ai-openscale?topic=ai-openscale-mo-config).
- [How does Azure Machine Learning service differ from Studio?](https://docs.microsoft.com/en-us/azure/machine-learning/service/overview-what-is-azure-ml#how-does-azure-machine-learning-service-differ-from-studio){: external}

