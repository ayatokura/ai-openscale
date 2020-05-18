---

copyright:
  years: 2018, 2020
lastupdated: "2020-05-18"

keywords: supported frameworks, models, model types, limitations, limits, XGBoost, AutoAI, Keras, scikit-learn, Spark, Python

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
{:note: .note}
{:note: .note}
{:note: .note}
{:note: .note}
{:faq: data-hd-content-type='faq'}

# {{site.data.keyword.ibmwatson_notm}} {{site.data.keyword.pm_short}}
{: #frmwrks-wml}

You can use {{site.data.keyword.pm_full}} to perform payload logging, feedback logging, and to measure performance accuracy, run-time bias detection, explainability, and auto-debias function in {{site.data.keyword.aios_full}}.
{: shortdesc}

{{site.data.keyword.aios_full}} fully supports the following {{site.data.keyword.pm_full}} frameworks: 

Table 1. Framework support details

| Framework | Problem type | Data type |
|:---|:---:|:---:|
| AutoAI<sup>1</sup> | Classification (binary and multi classes) | Structured (data, text) |
| AutoAI | Regression | Structured or Unstructured<sup>2</sup> (text only) |
| Apache Spark MLlib | Classification | Structured (data, text) |
| Apache Spark MLLib | Regression | Structured (data, text) |
| Keras with TensorFlow<sup>3</sup><sup>&</sup><sup>4</sup> | Classification | Unstructured<sup>2</sup> (image, text) |
| Keras with TensorFlow<sup>3</sup><sup>&</sup><sup>4</sup> | Regression | Unstructured<sup>2</sup> (image, text) |
| Python function | Classification | Structured (data, text) |
| Python function | Regression | Structured (data, text) |
| scikit-learn | Classification | Structured (data, text) |
| scikit-learn | Regression | Structured (data, text) |
| XGBoost<sup>5</sup> | Classification | Structured (data, text) |
| XGBoost | Regression | Structured (data, text) |
{: caption="Framework support details" caption-side="top"}

<sup>1</sup>AutoAI is only supported in {{site.data.keyword.wos4d_full}}. To learn more about AutoAI, see [AutoAI implementation details](https://dataplatform.cloud.ibm.com/docs/content/wsj/analyze-data/autoai-details.html?audience=wdp&context=analytics){: external}. For models that have where the training data is in Cloud Object Storage, there is no support for fairness attributes of type boolean. However, if the training data is in Db2, {{site.data.keyword.aios_short}} supports fairness attributes that are boolean type. When using the AutoAI option, {{site.data.keyword.aios_short}} does not support models where the data type of the model prediction is binary. You must change such models so that the data type of their prediction is a string data type.
{: note}

<sup>2</sup>Fairness and drift metrics are not supported for unstructured (image or text) data types.
{: note}


<sup>3</sup>Keras support does not include support for fairness.
{: note}

<sup>4</sup>Explainability is supported if your model / framework outputs prediction probabilities.
{: note}

<sup>5</sup>For XGBoost binary and multiple class models, you must update the model to return prediction probability in the form of numerical values for binary models and a list of probabilities per class for multi-class models. Support for the XGBoost framework has the following limitations for classification problems: For binary classification, {{site.data.keyword.aios_short}} supports the `binary:logistic` logistic regression function with an output as a probability of `True`. For multiclass classification, {{site.data.keyword.aios_short}} supports the `multi:softprob` function where the result contains the predicted probability of each data point belonging to each class.
{: note}


## AutoAI models and training data
{: #wml-framework-autoai}

AutoAI automatically prepares data, applies algorithms, or estimators, and builds model pipelines best suited for your data and use case. {{site.data.keyword.aios_short}} requires access to the training data to analyze the model, for more information, see [Why does {{site.data.keyword.aios_short}} need access to my training data?](/docs/ai-openscale?topic=ai-openscale-wos-faqs#trainingdata). 

Because {{site.data.keyword.aios_short}} cannot detect the training data location for an AutoAI model like it can for a regular model, you must explicitly provide the needed details to access the training data location:

- For the online path, where you manually configuring monitors, you must provide the database details from which training data can be accessed .
- For the custom notebook path, where you upload training data distribution, you can use the JSON file that is produced by running the notebook.

For more information, see [Provide model details](/docs/ai-openscale?topic=ai-openscale-mo-config#mo-work-model-dets) and [Numeric/categorical data](/docs/ai-openscale?topic=ai-openscale-mo-config#mo-nuca).


## Specifying an {{site.data.keyword.ibmwatson_notm}} {{site.data.keyword.pm_short}} service instance
{: #wml-connect}

Your first step in the {{site.data.keyword.aios_short}} tool is to specify an {{site.data.keyword.pm_full}} instance. Your {{site.data.keyword.pm_short}} instance is where you store your AI models and deployments.

## Prerequisites
{: #wml-prereq}

You should have provisioned an {{site.data.keyword.pm_full}} instance in the same account or cluster where the {{site.data.keyword.aios_short}} service instance is present. If you have provisioned a {{site.data.keyword.pm_full}} instance in some other account or cluster, then you will not be able to configure that instance with automatic payload logging with {{site.data.keyword.aios_short}}.

## Connect your {{site.data.keyword.pm_short}} service instance
{: #wml-config}

{{site.data.keyword.aios_short}} connects to AI models and deployments in an {{site.data.keyword.pm_full}} instance. To connect your service to {{site.data.keyword.aios_short}}, go to the **Configure** ![The configuration tab icon](/images/wos-config-tab.png) tab, add a machine learning provider, and click the **Edit** ![The edit icon](/images/wos-edit-icon.png) icon. In addition to a name and description and whether this is a **Pre-production** or **Production** environment type, you must provide the following information that is specific to this type of service instance:

- If you have an instance of {{site.data.keyword.pm_full}}, {{site.data.keyword.aios_short}} detects it, along with the configuration information.
- To specify a machine learning location outside of your account, choose the **Other** option. Provide credentials for your location by pasting valid JSON credentials.


### Next steps
{: #wml-next}

You are now ready to select deployed models and configure your monitors. {{site.data.keyword.aios_short}} lists your deployed models on the **Insights** dashboard where you can click the **Add to dashboard** button. Select the deployments you want to monitor and click **Configure**.

For more information, see [Configure monitors](/docs/ai-openscale?topic=ai-openscale-mo-config).
