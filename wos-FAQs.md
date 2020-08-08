---

copyright:
  years: 2018, 2020
lastupdated: "2020-05-18"

keywords: FAQs, frequently asked questions, questions

subcollection: ai-openscale

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:pre: .pre}
{:codeblock: .codeblock}
{:support: data-reuse='support'}
{:screen: .screen}
{:faq: data-hd-content-type='faq'}
{:video: .video}

# FAQs
{: #wos-faqs}

Here are some of the most frequently asked questions from users of {{site.data.keyword.aios_full}}.
{: shortdesc}


<p>&nbsp;</p>


## What is {{site.data.keyword.aios_short}}
{: #faq-whatsa}
{: faq}

{{site.data.keyword.aios_full}} tracks and measures outcomes from your AI models, and helps ensure they remain fair, explainable, and compliant wherever your models were built or are running. {{site.data.keyword.aios_short}} also detects and helps correct the drift in accuracy when an AI model is in production

Get a quick overview of {{site.data.keyword.aios_short}} by watching the following video:

![Mitigating AI Bias with {{site.data.keyword.aios_full}}](https://cdnapisec.kaltura.com/p/1773841/sp/177384100/embedIframeJs/uiconf_id/39954662/partner_id/1773841?iframeembed=true&playerId=kplayer&entry_id=1_1shu3261&flashvars[streamerType]=auto){: video output="iframe" data-script="#video-transcript-ui-faq-whatsa" id="mediacenterplayer" frameborder="0" width="560" height="315" allowfullscreen webkitallowfullscreen mozAllowFullScreen}


### Video transcript
{: #video-transcript-ui-faq-whatsa}
{: notoc}

Transcript text that will be displayed underneath this video is coming soon.

Thanks for your patience.


<p>&nbsp;</p>


## How is {{site.data.keyword.aios_short}} priced?
{: #faq-pricing}
{: faq}

There's a **Standard** pricing plan that includes monitoring of up to 24 deployed models, with no restrictions on the number of payload, feedback rows, or transactions for Explainability. The up-to-date information is available in the [{{site.data.keyword.Bluemix}} catalog](https://cloud.ibm.com/catalog/services/watson-openscale?cm_sp=WatsonPlatform-WatsonPlatform-_-OnPageNavCTA-IBMWatson_OpenScale-_-AIOSProductPage){: external}.

<p>&nbsp;</p>


## Is there a free trial for {{site.data.keyword.aios_short}}?
{: #faq-freetrial}
{: faq}

{{site.data.keyword.aios_short}} offers a free trial plan. To sign up, see [{{site.data.keyword.aios_short}} web page](https://www.ibm.com/cloud/watson-openscale/){: external} and click **Get started now**. You can use the free plan if you want (subject to monthly usage limits that refresh every month).

<p>&nbsp;</p>


## Does {{site.data.keyword.aios_short}} work with Microsoft Azure ML engine?
{: #faq-azure}
{: faq}
{: support}

{{site.data.keyword.aios_short}} supports both Microsoft Azure ML Studio and Microsoft Azure ML Service engines. For more information, see [Microsoft Azure ML Studio frameworks](/docs/ai-openscale?topic=ai-openscale-frmwrks-azure) and [Microsoft Azure ML Service frameworks](/docs/ai-openscale?topic=ai-openscale-frmwrks-azureservice).

<p>&nbsp;</p>


## Does {{site.data.keyword.aios_short}} work with Amazon SageMaker ML engine?
{: #faq-sagemaker}
{: faq}
{: support}

{{site.data.keyword.aios_short}} supports Amazon SageMaker ML engine. For more information, see [Amazon SageMaker frameworks](/docs/ai-openscale?topic=ai-openscale-frmwrks-aws-sage).

<p>&nbsp;</p>


## Is {{site.data.keyword.aios_short}} available on {{site.data.keyword.icp4dfull_notm}}?
{: #faq-icp}
{: faq}
{: support}

{{site.data.keyword.aios_short}} is one of the included services for {{site.data.keyword.icp4dfull_notm}}. 

<p>&nbsp;</p>


## To run {{site.data.keyword.aios_short}} on my own servers, how much computer processing power is required?
{: #faq-sizing}
{: faq}
{: support}

There are specific guidelines for hardware configuration for three-node and six-node configurations. Your IBM Technical Sales team can also help you with sizing your specific configuration. Because {{site.data.keyword.aios_short}} run as an add-on to {{site.data.keyword.icp4dfull_notm}}, you need to consider the requirements for both software products.

<p>&nbsp;</p>


## How do I convert a prediction column from an integer data type to a categorical data type?
{: #wos-faqs-convert-data-types}
{: faq}
{: support}

For fairness monitoring, the prediction column allows only an integer numerical value even though the prediction label is categorical. How do I configure a categorical feature that is not an integer? Is a manual conversion required? 

The training data might have class labels such as “Loan Denied”, “Loan Granted”. The prediction value that is returned by {{site.data.keyword.pm_full}} scoring end point has values such as “0.0”, “1.0". The scoring end point also has an optional column that contains the text representation of prediction. For example, if prediction=1.0, the predictionLabel column might have a value “Loan Granted”. If such a column is available, when you configure the favorable and unfavorable outcome for the model, specify the string values “Loan Granted” and “Loan Denied”. If such a column is not available, then you need to specify the integer and double values of 1.0, 0.0 for the favorable, and unfavorable classes.

{{site.data.keyword.pm_full}} has a concept of output schema that defines the schema of the output of {{site.data.keyword.pm_full}} scoring end point and the role for the different columns. The roles are used to identify which column contains the prediction value, which column contains the prediction probability, and the class label value, etc. The output schema is automatically set for models that are created by using model builder. It can also be set by using the {{site.data.keyword.pm_full}} Python client. Users can use the output schema to define a column that contains the string representation of the prediction. Set the `modeling_role` for the column to ‘decoded-target’. The documentation for the {{site.data.keyword.pm_full}} Python client is available at: http://wml-api-pyclient-dev.mybluemix.net/#repository. Search for “OUTPUT_DATA_SCHEMA” to understand the output schema and the API to use is to store_model API that accepts the OUTPUT_DATA_SCHEMA as a parameter.

<p>&nbsp;</p>


## Why does {{site.data.keyword.aios_short}} need access to training data?
{: #trainingdata}
{: faq}
{: support}

You must either provide {{site.data.keyword.aios_short}} access to training data that is stored in Db2 or {{site.data.keyword.cos_full_notm}}, or you must run a Notebook to access the training data. {{site.data.keyword.aios_short}} needs access to your training data for the following reasons:

- To generate contrastive explanations: To create explanations, access to statistics, such as median value, standard deviation, and distinct values from the training data is required.
- To display training data statistics: To populate the bias details page, {{site.data.keyword.aios_short}} must have training data from which to generate statistics.
- To build a drift detection model: The Drift monitor uses training data to create and calibrate drift detection.

In the Notebook-based approach, you are expected to upload the statistics and other information when you configure a deployment in {{site.data.keyword.aios_short}}. {{site.data.keyword.aios_short}} no longer has access to the training data outside of the Notebook, which is run in your environment. It has access only to the information uploaded during the configuration.

<p>&nbsp;</p>


## What internet browser does {{site.data.keyword.aios_short}} support?
{: #in-brw}
{: faq}
{: support}

The {{site.data.keyword.aios_short}} service requires the same level of browser software as is required by {{site.data.keyword.cloud_notm}}. See the {{site.data.keyword.cloud_notm}} [Prerequisites](https://cloud.ibm.com/docs/overview?topic=overview-prereqs-platform#browsers-platform){: external} topic for details.

<p>&nbsp;</p>

## Is there a command-line tool to use? 
{: #in-mop}
{: faq}
{: support}

Yes! There is a ModelOps CLI tool, whose official name is the [{{site.data.keyword.aios_short}} CLI model operations tool](https://github.com/IBM-Watson/aiopenscale-modelops-cli){: external}. Use it to run tasks related to the lifecycle management of machine learning models. This tool is complementary to the {{site.data.keyword.cloud_notm}} CLI tool, augmented with the [machine learning plug-in](https://www.ibm.com/support/knowledgecenter/DSXDOC/analyze-data/ml_dlaas_environment.html){: external}.

<p>&nbsp;</p>

## What version of Python can I use with {{site.data.keyword.aios_short}}?
{: #in-pyc}
{: faq}
{: support}

Because {{site.data.keyword.aios_short}} is independent of your model-creation process, it supports whatever Python versions your machine learning provider supports. The [{{site.data.keyword.aios_short}} Python client](http://ai-openscale-python-client.mybluemix.net/){: external} is a Python library that works directly with the {{site.data.keyword.aios_short}} service on {{site.data.keyword.cloud_notm}}. For the most up-to-date version information, see [the Requirements section](http://ai-openscale-python-client.mybluemix.net/#requirements){: external}. You can use the Python client, instead of the {{site.data.keyword.aios_short}} client UI, to directly configure a logging database, bind your machine learning engine, and select and monitor deployments. For examples by using the Python client in this way, see the [{{site.data.keyword.aios_short}} sample Notebooks](https://github.com/pmservice/ai-openscale-tutorials/tree/master/notebooks){: external}.

<p>&nbsp;</p>

## What does it mean if the fairness score is greater than 100 percent?
{: #fairness-score-over100}

Depending on your fairness configuration, your fairness score can exceed 100 percent. It means that your monitored group is getting relatively more “fair” outcomes as compared to the reference group. Technically, it means that the model is unfair in the opposite direction.


## Configuring a model requires information about the location of the training data and the options are Cloud Object Storage and Db2. If the data is in Netezza, can {{site.data.keyword.aios_short}} use Netezza?

Use this [{{site.data.keyword.aios_short}} Notebook](https://github.com/IBM-Watson/aios-data-distribution/blob/master/training_statistics_notebook.ipynb) to read the data from Netezza and generate the training statistics and also the drift detection model.

## Why doesn't {{site.data.keyword.aios_short}} see the updates that were made to the model?
{: #new-model-missing}

{{site.data.keyword.aios_short}} works on a deployment of a model, not on the model itself. You must create a new deployment and then configure this new deployment as a new subscription in {{site.data.keyword.aios_short}}. With this arrangement, you are able to compare the two versions of the model.