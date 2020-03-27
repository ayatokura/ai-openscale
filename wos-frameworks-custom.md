---

copyright:
  years: 2018, 2020
lastupdated: "2020-01-28"

keywords: supported frameworks, models, model types, limitations, limits, custom machine learning engine, custom

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

# Custom ML frameworks
{: #frmwrks-custom}

You can use your custom machine learning framework to perform payload logging, feedback logging, and to measure performance accuracy, run-time bias detection, explainability, and auto-debias function in {{site.data.keyword.aios_full}}. The custom machine learning framework must have equivalency to {{site.data.keyword.pm_full}}.
{: shortdesc}

{{site.data.keyword.aios_full}} fully supports the following custom machine learning frameworks:

Table 1. Framework support details

| Framework | Problem type | Data type |
|:---|:---:|:---:|
| Equivalent to {{site.data.keyword.pm_full}} | Classification | Structured |
| Equivalent to {{site.data.keyword.pm_full}} | Regression | Structured |
{: caption="Framework support details" caption-side="top"}

For a model that is not equivalent to {{site.data.keyword.pm_full}}, you must create a wrapper for the custom model that exposes the required REST API endpoints and bridge the input/output between {{site.data.keyword.aios_short}} and the actual custom machine learning engine.

## How it works
{: #co-works}

The following image shows the custom environment support:

![How Custom works chart is displayed. It shows boxes for the custom environment with the client API and the {{site.data.keyword.aios_short}} API](images/wos-custom-how-works.png)

You can also reference the following links:

[{{site.data.keyword.aios_short}} payload logging API](https://cloud.ibm.com/apidocs/ai-openscale#publish-scoring-payload){: external}

[Custom deployment API](https://aiopenscale-custom-deployement-spec.mybluemix.net/){: external}

[Python client binding SDK](http://ai-openscale-python-client.mybluemix.net/#bindings){: external}

[Working with Custom machine Learning engine](https://github.com/pmservice/ai-openscale-tutorials/blob/master/notebooks/AI%20OpenScale%20and%20Custom%20ML%20Engine.ipynb){: external}

[Python SDK for {{site.data.keyword.aios_full}}](https://pypi.org/project/ibm-ai-openscale/){: external}

- **Input criteria for model to support monitors**

  Your model should take as input a feature vector, which is essentially a collection of named fields and their values (the fields being monitored for bias being one of those fields):

  ```bash
  {
    "fields": [
        "name",
        "age",
        "position"
    ],
    "values": [
        [
            "john",
            33,
            "engineer"
        ],
        [
            "mike",
            23,
            "student"
        ]
    ]
  }
  ```

  In this example, `“age”` could be a field someone is evaluating for fairness.

  If the input is a tensor/matrix, which is transformed from the input feature space (which is often the case in deep learning from text or images), that model cannot be handled by the {{site.data.keyword.aios_short}} platform in the current release. By extension, deep learning models with text or image inputs cannot be handled for bias detection and mitigation.

  Additionally, training data should be loaded to support Explainability.

  For explainability on text, the full text should be one of the features. Explainability on images for a Custom model is not supported in the current release.
  {: note}

- **Output criteria for model to support monitors**

  Your model should output the input feature vector alongside the prediction probabilities of various classes in that model.

  ```bash
  {
    "fields": [
        "name",
        "age",
        "position",
        "prediction",
        "probability"
    ],
    "labels": [
        "personal",
        "camping"
    ],
    "values": [
        [
            "john",
            33,
            "engineer",
            "personal",
            [
                0.6744664422398081,
                0.3255335577601919
            ]
        ],
        [
            "mike",
            23,
            "student"
            "camping",
            [
                0.2794765664946941,
                0.7205234335053059
            ]
        ]
    ]
  }
  ```

  In this example, `"personal”` and `“camping”` are the possible classes, and the scores in each scoring output are assigned to both classes. If the prediction probabilities are missing, bias detection will work, but auto-debias will not.

  The preceding scoring output should be accessible from a live scoring endpoint which {{site.data.keyword.aios_short}} could call over REST. For AzureML, SageMaker, and {{site.data.keyword.pm_full}}, {{site.data.keyword.aios_short}} directly connects to the native scoring endpoints, (so you don’t have to worry about implementing the scoring spec).

## Adding a custom machine learning engine to {{site.data.keyword.aios_short}}
{: #frmwrks-custom-add}

You can configure {{site.data.keyword.aios_short}} to work with a custom machine learning provider by using one of the following methods:

- If this is the first time that you are adding a custom machine learning provider to {{site.data.keyword.aios_short}}, you can use the configuration interface. For more information, see [Specifying a custom machine learning instance](/docs/services/ai-openscale?topic=ai-openscale-co-connect).
- You can also add your machine learning provider by using the Python SDK. You must use this method if you want to have more than one provider. For more information on performing this programmatically, see [Bind your custom machine learning engine](/docs/services/ai-openscale?topic=ai-openscale-cml-cusconfig#cml-cusbind).


## Sample notebooks
{: #frmwrks-custom-smpl-ntbks}

- [Creation of Custom Machine Learning engine using Kubernetes cluster](https://github.com/pmservice/ai-openscale-tutorials/tree/master/applications/custom-ml-engine-ibmcloud){: external}
- [Data mart creation, model deployment monitoring and data analysis](https://github.com/pmservice/ai-openscale-tutorials/blob/master/notebooks/AI%20OpenScale%20and%20Custom%20ML%20Engine.ipynb){: external}

## Explore further
{: #frmwrks-custom-mediumblogs}

[Monitor custom machine learning engine with {{site.data.keyword.aios_short}}](https://developer.ibm.com/patterns/monitor-custom-machine-learning-engine-with-ai-openscale/){: external}



## Custom machine learning engine examples
{: #fmrk-workaround-cstmmlsengex}

Use the following examples to set up your own custom machine learning engine.
{: shortdesc}

### Python and flask
{: #fmrk-workaround-pandflask}

The [Custom ML Engine example published on git](https://github.com/pmservice/ai-openscale-tutorials/tree/master/applications/custom-ml-engine-ibmcloud){: external} is using python and flask to serve scikit-learn model.

To generate the drift detection model, you must use scikit-learn version 0.20.2 in notebooks. 
{: note}


The [README file](https://github.com/pmservice/ai-openscale-tutorials/tree/master/applications/custom-ml-engine-ibmcloud){: external} describes how the app can be deployed locally for testing purposes as well as cf application on IBM Cloud. The implementation of REST API endpoints can be found in [app.py file](https://github.com/pmservice/ai-openscale-tutorials/blob/master/applications/custom-ml-engine-ibmcloud/app.py){: external}.

### Node.js
{: #fmrk-workaround-nodejs}

You can also find example of custom machine learning engine written in [Node.js here](https://github.com/pmservice/ai-openscale-tutorials/tree/master/applications/custom-ml-engine-nodejs){: external}.

### End2end code pattern
{: #fmrk-workaround-e2ecode}

[Code pattern](https://developer.ibm.com/patterns/monitor-custom-machine-learning-engine-with-ai-openscale){: external} showing end2end example of custom engine deployment and integration with {{site.data.keyword.aios_short}}.


## Next steps
{: #fmrk-workaround-nxt-steps-over}

{{site.data.keyword.aios_short}} is now ready for you to [configure monitors](/docs/services/ai-openscale?topic=ai-openscale-mo-config).

Implement your own solution by using one of these [Custom machine learning examples](/docs/services/ai-openscale?topic=ai-openscale-fmrk-workaround-cstmmlsengex).