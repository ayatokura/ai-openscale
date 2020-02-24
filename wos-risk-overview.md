---

copyright:
  years: 2018, 2020
lastupdated: "2020-01-28"

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
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}
{:faq: data-hd-content-type='faq'}

# Model risk management and model governance ![beta tag](images/beta.png)
{: #mrm-ovr}

Manage model risk with {{site.data.keyword.aios_short}}. Financial institutions manage many complex and integrated areas of risk. Management of model risk is critical to meet regulatory requirements and to protect institutions from operational and reputational risk.
{: shortdesc}

## What is a Model?
{: #mrm-ovr-model}

The Federal Reserve and Office of the Comptroller of the Currency guidance SR Letter 11-7 defines a Model as “…a quantitative method, system, or approach that applies statistical, economic, financial, or mathematical theories, techniques, and assumptions to process input data into quantitative estimates.” 
These types of models, either deterministic or probabilistic, raise different model risk management challenges.

## What is Model Risk? 
{: #mrm-ovr-model-risk}

Model risk is a type of risk that occurs when a mathematical model is used in financial institutions to predict and measure quantitative information, and the model performs inadequately. This can lead to adverse outcomes for the firm and operational losses in millions. 

## Model Development Cycle
{: #mrm-ovr-model-dev-cycle}

There are many challenges with machine learning and deep learning models. For example, you need to face the lack of knowledge of methods used by Model Developers / Vendors along with inconsistent documentation and increased volume of model change.

Tests to be run on machine learning and deep learning models differ from straightforward application testing: 

- Drift: Any change in input data also known as Drift can cause the model to make inaccurate decisions, impacting business KPIs 
- Bias: Training data may be cleaned to be free from bias but runtime data may induce biased behavior of model 
- Explainability: Traditional statistical models are simpler to interpret and explain 
- Missing Validation/Test Data: Model training data sets may not capture the range of data or combinations that could be encountered in runtime 
Validation and monitoring of AI models is necessary in addition to govern and manage risk.

## Options
{: #mrm-ovr-wos}

IBM offers a model risk management solution for financial services with IBM Watson OpenScale. IBM Watson OpenScale monitors and measures outcomes from AI Models across its lifecycle and performs model validations. Specifically, you can use the following configurations:

- [Model risk management with Watson OpenScale](/docs/services/ai-openscale?topic=ai-openscale-mrm-risk-wos-only)

  Use Watson OpenScale as a stand-alone solution. Enable the model risk management features to create pre-production and production repositories and compare models.

- [Model governance with Watson OpenScale and IBM OpenPages MRG](/docs/services/ai-openscale?topic=ai-openscale-mrm-risk-openpages-mrg)
  
  Use Watson OpenScale as part of an overall model risk governance solution by integrating with IBM OpenPages MRG.

## Next steps
{: #mrm-ovr-next}



