---

copyright:
  years: 2018, 2020
lastupdated: "2020-04-08"

keywords: risk, governance, model risk management, model risk governance

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
{:note: .note}
{:swift: .ph data-hd-programlang='swift'}
{:faq: data-hd-content-type='faq'}
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}


# Model risk management and model governance ![beta tag](images/beta.png)
{: #mrm-ovr}

Manage model risk with {{site.data.keyword.aios_short}}. Financial institutions manage many complex and integrated areas of risk. Management of model risk is critical to meet regulatory requirements and to protect institutions from operational and reputational risk.
{: shortdesc}

## What is a Model?
{: #mrm-ovr-model}

The Federal Reserve and Office of the Comptroller of the Currency guidance SR Letter 11-7 defines a Model. It is “…a quantitative method, system, or approach that applies statistical, economic, financial, or mathematical theories, techniques, and assumptions to process input data into quantitative estimates.” 

These types of models, either deterministic or probabilistic, raise different model risk management challenges.

## What is Model Risk? 
{: #mrm-ovr-model-risk}

Model risk is a type of risk that occurs when a mathematical model is used in financial institutions to predict and measure quantitative information, and the model performs inadequately. Inadequate performance leads to adverse outcomes for the firm and operational losses in millions. 

## Model Development Cycle
{: #mrm-ovr-model-dev-cycle}

There are many challenges with machine learning and deep learning models. For example, you need to face the lack of knowledge of methods that are used by Model Developers / Vendors along with inconsistent documentation and increased volume of model change.

Tests to be run on machine learning and deep learning models differ from straightforward application testing: 

- Drift: Any change in input data also known as Drift can cause the model to make inaccurate decisions, impacting business predictions
- Bias: Training data can be cleaned to be free from bias but runtime data might induce biased behavior of model 
- Explainability: Traditional statistical models are simpler to interpret and explain 
- Missing Validation or Test Data: Model training data sets might not capture the range of data or combinations that are encountered in runtime. Validation and monitoring of AI models is necessary in addition to govern and manage risk.

## Options
{: #mrm-ovr-wos}
{: help} 
{: support}

IBM offers a model risk management solution for financial services with {{site.data.keyword.aios_full}}. {{site.data.keyword.aios_full}} monitors and measures outcomes from AI Models across its lifecycle and validates models. Specifically, you can use the following configurations:

- [Model risk management with {{site.data.keyword.aios_short}}](/docs/services/ai-openscale?topic=ai-openscale-mrm-risk-wos-only)

  Use {{site.data.keyword.aios_short}} as a stand-alone solution. Enable the model risk management features to create pre-production and production repositories and compare models.

- [Model governance with {{site.data.keyword.aios_short}} and IBM OpenPages MRG](/docs/services/ai-openscale?topic=ai-openscale-mrm-risk-openpages-mrg)
  
  Use {{site.data.keyword.aios_short}} as part of an overall model risk governance solution by integrating with IBM OpenPages MRG.

## Known issues and limitations for the open beta
{: #mrm-ovr-limits}

Because this is an open beta, you are working in a non-standard and non-production environment. It is expected that there are some limitations, issues, and non-standard ways of working. At the start of the beta, take note of the following issues:

### Only structured data is supported for the open beta

Model risk management and governance support only structured input data types. Models that deal with unstructured data are not supported currently. If you attempt to use an unsupported data type, you receive the following error message:

Selected monitor is not applicable for this subscription. It requires `input_data_type` to be one of [structured], while subscription defines `input_data_type` as `unstructured_text`.

### You cannot create a second free instance of Watson Machine Learning on IBM Cloud

Although you are welcome to use lite plans or free instances of the IBM Cloud services, it is impossible to create two free instances of Watson Machine Learning. Without a paid account, you cannot create the second instance in the same IBM Cloud account. As a workaround, you can create a second IBMid and a second IBM Cloud instance so that you can then create a second free Watson Machine Learning instance. You must ensure that one is designated as your pre-production and the other as your production system consistently within Watson Studio and {{site.data.keyword.aios_short}}.

### Payload logging requires extra submissions for Amazon Web Services binary, Microsoft Azure binary and multiclass, and Native XGBoost binary problem types

For any of the models that use certain frameworks, you must send the same record for initial scoring a second time. This extra scoring request is needed for the initial setup of payload logging when you configure monitors. The following frameworks and problem types are affected:

- Amazon Web Services binary
- Microsoft Azure binary and multiclass
- Native XGBoost binary

### Common log per client for IBM OpenPages

Each client in the closed beta is assigned a single user ID for IBM OpenPages. There is a single common log that is available to every participant. Clients are responsible for ensuring that no proprietary or personally identifiable information is recorded in the IBM OpenPages log.

### Payload logging not automatically happening

You see the following error in the notebook:

`Missing Payload: There is no payload logged in the payload table. First, log a payload, then enable Quality Monitoring.`

Payload processing does not complete in the specified time period. The notebook must be rerun from the beginning.
