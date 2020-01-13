---

copyright:
  years: 2018, 2020
lastupdated: "2019-11-22"

keywords: release notes, what's new 

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

# What's new
{: #rn-relnotes}

This document outlines new features for {{site.data.keyword.aios_full_notm}}.
{: shortdesc}

## 31 October 2019
{: #rn-31oct2019}

The following new features and changes to {{site.data.keyword.aios_short}} are available.

- __*{{site.data.keyword.pm_full}} framework enhancements*__: {{site.data.keyword.aios_short}} now supports the native XGBoost frameworks on the {{site.data.keyword.pm_full}} engine.

   For more information, see [{{site.data.keyword.pm_full}} frameworks](/docs/services/ai-openscale?topic=ai-openscale-frmwrks-wml).

- __*{{site.data.keyword.aios_short}} supports Auto AI models created in {{site.data.keyword.pm_full}}*__: Models that are created by using the Auto AI feature of {{site.data.keyword.pm_full}} are now supported.

   For more information, see [{{site.data.keyword.pm_full}} frameworks](/docs/services/ai-openscale?topic=ai-openscale-frmwrks-wml).

## 24 September 2019
{: #rn-24sep2019}

A new version of the {{site.data.keyword.aios_short}} Python SDK, ibm_ai_openscale-2.1.16, has been released. In addition to bug fixes, such as addressing the {{site.data.keyword.icpfull}} timeout issue the new version contains drift monitoring (including status messaging) and the ability to get a count of payload records. 

## 9 August 2019
{: #rn-9aug2019}

The following new features and changes to {{site.data.keyword.aios_short}} are available.

- __*Drift detection GA*__:
  
  Drift detection is now in GA and includes both drift in accuracy and drift in data.
  For more information, see [Drift detection](/docs/services/ai-openscale?topic=ai-openscale-behavior-ovr).
  
- __*Business KPIs*__:  ![beta tag](images/beta.png)

  Through an application monitor, you can monitor business KPIs as well as understand the impact of model metrics, such as model drift on an application’s business key performance indicators (KPIs).
  
  For more information, see [Configuring the application monitor](/docs/services/ai-openscale?topic=ai-openscale-app-monitor).


## 9 July 2019
{: #rn-9jul2019}

The following new features and changes to {{site.data.keyword.aios_short}} are available.

- __*Updated and expanded online help*__: The {{site.data.keyword.aios_short}} online help was recently reorganized to make it easier to find topics by using the contents pane. In addition, many new topics were written and expanded.

   For more information, see [Getting insights](/docs/services/ai-openscale?topic=ai-openscale-io-ov) and [Updating {{site.data.keyword.aios_short}} from a lite to a paid plan](/docs/services/ai-openscale?topic=ai-openscale-cf-upgrade).
   
## 2 July 2019
{: #rn-2jul2019}

The following new features and changes to {{site.data.keyword.aios_short}} are available.

- __*Drift detection*__: ![beta tag](images/beta.png)

  {{site.data.keyword.aios_short}} now supports drift detection.

   For more information, see [Drift detection](/docs/services/ai-openscale?topic=ai-openscale-behavior-drift-ovr).

- __*Microsoft Azure ML Service support*__: {{site.data.keyword.aios_short}} now supports Microsoft Azure ML Service, which provides a means for integrating your Azure ML service AI models with the fairness, accuracy, and explainability of {{site.data.keyword.aios_short}}.

   For more information, see [Microsoft Azure ML Service frameworks](/docs/services/ai-openscale?topic=ai-openscale-frmwrks-azure-service).

- __*Improved work flow*__: {{site.data.keyword.aios_short}} has been busy improving the workflow so that you can speed through your work with fewer clicks and more explainability. The navigation panel lets you see where you are and makes it easy to jump back and forth between configuration tasks.

   For more information, see [Prepare model for monitoring](/docs/services/ai-openscale?topic=ai-openscale-mo-config).

- __*Multiple machine learning providers*__: Why be tied down to just one machine learning provider or engine? With the newest version of {{site.data.keyword.aios_short}}, you can add multiple providers so that you can take advantage of their unique features or provide continuity with legacy apps.

   For more information, see [Support for multiple machine learning engines](/docs/services/ai-openscale?topic=ai-openscale-fmrk-workaround-multmleng).

- __*More out-of-the-box metrics*__: With this version of {{site.data.keyword.aios_short}}, there are many new fairness, quality, behavior, performance, and analytics metrics. We're going to need a bigger box!

   For more information, see [Quality metrics overview](/docs/services/ai-openscale?topic=ai-openscale-anlz_metrics) and then start clicking around to visit the others: [Fairness](/docs/services/ai-openscale?topic=ai-openscale-anlz_metrics_fairness), [Performance](/docs/services/ai-openscale?topic=ai-openscale-performance_mets_through), [Analytics](/docs/services/ai-openscale?topic=ai-openscale-anlz_metrics_payload), and [Behavior](/docs/services/ai-openscale?topic=ai-openscale-behavior-ovr).

- __*Speeding along the bias*__: With suggested fairness attributes and automatic values for bias configuration, it's easy to see where {{site.data.keyword.aios_short}} detects the potential for violation of fairness thresholds in the deployed model. You have the choice to accept the recommended features to monitor and to change the values.

   For more information, see [Fairness metrics overview](/docs/services/ai-openscale?topic=ai-openscale-anlz_metrics_fairness).

## 11 June 2019
{: #rn-11June2019}

The following new features and changes to the service are available.

- __*Updated Dashboard functionality*__: The {{site.data.keyword.aios_short}} Dashboard has undergone several revisions. This new version contains the following improvements:

    - A new help panel makes it easier to find resources, such as StackOverflow, IBM Support, and 
    - Globalization has been enabled for the dashboard
    - Usability enhancements

## 7 June 2019
{: #rn-7June2019}

The following new features and changes to the service are available.

- __*Enhanced command line interface*__: The command line interface, ibm-ai-openscale-cli, has been updated and version 0.2.148 is now released. This new version contains the following improvements:

    - Updated the quality metrics history to include the full range of new quality metrics supported by OpenScale
    - Support for specifying an SSL certificate directly when using IBM DB2
    - Support for the new ibm-ai-openscale 2.1.8 Python SDK
    - Other bug fixes and stability improvements

   Install from PyPI by running the `pip install -U ibm-ai-openscale-cli` command, and get usage help by running the  `ibm-ai-openscale-cli --help` command. For more information, see the [PyPI project page](https://pypi.org/project/ibm-ai-openscale-cli){: external}.

## 29 May 2019
{: #rn-29May2019}

The following new features and changes to the service are available.

- __*Bias Visualization Enhancements*__: ![beta tag](images/beta.png) The bias visualization includes the following views: 

    - Payload + Perturbed: Includes the scoring request received for the selected hour plus additional records from previous hours if the minimum number of records required for evaluation was not met. Includes additional perturbed/synthesized records used to test the model's response when the value of the monitored feature changes.
    - Payload: The actual scoring requests received by the model for the selected hour.
    - Training: The training data records used to train the model.
    - Debiased: The output of the debiasing algorithm after processing the runtime and perturbed data.

   For more information, see [Bias visualization](/docs/services/ai-openscale?topic=ai-openscale-mf-monitor#mf-monitor-bias-viz).

- __*Accuracy computation for de-biased output*__: Accuracy computation includes de-biased output. You can compare the accuracy of the de-biased model with the accuracy of a production model

   For more information, see [Accuracy](/docs/services/ai-openscale?topic=ai-openscale-acc-monitor#acc-debias-view).

- __*Support for multiple machine learning engines*__: {{site.data.keyword.aios_short}} supports multiple machine learning engines within a single instance provided that provisioning is performed through the [Python SDK](http://ai-openscale-python-client.mybluemix.net/?cm_mc_uid=70732728440115575086192&cm_mc_sid_50200000=62539451560175957820){: external}.

   For more information, see [Support for multiple machine learning engines](/docs/services/ai-openscale?topic=ai-openscale-fmrk-workaround-multmleng).

- __*Internationalization Support*__: {{site.data.keyword.aios_short}} supports localized versions and includes processing data in supported languages. The {{site.data.keyword.aios_short}} user interface, documentation, and error messages are currently available in the following languages: 
    - German
    - French
    - Italian
    - Spanish
    - Brazilian Portuguese
    - Japanese
    - Simplified Chinese
    - Traditional Chinese
    - Korean

   For more information (including limitations), see [Supported languages for {{site.data.keyword.aios_short}}](/docs/services/ai-openscale?topic=ai-openscale-sl-langs).

- __*{{site.data.keyword.pm_full}} framework enhancements*__: {{site.data.keyword.aios_short}} now supports the scikit-learn and XGBoost frameworks on the {{site.data.keyword.pm_full}} engine.

   For more information, see [{{site.data.keyword.pm_full}} frameworks](/docs/services/ai-openscale?topic=ai-openscale-frmwrks-wml).

## 25 April 2019
{: #rn-25April2019}

The following new features and changes to the service are available.

In addition to usability improvements and security updates, our developers have been busy with new features. {{site.data.keyword.aios_short}} features that have been added or enhanced over the preceding several weeks include:

- __*Automated setup tour*__: A new tour-led way to set up your {{site.data.keyword.aios_short}} environment. Use the [Automated setup](/docs/services/ai-openscale?topic=ai-openscale-wos-fast-start) to provision services and download and configure a model. You will notice this option when you have a new instance of {{site.data.keyword.aios_short}}.
- __*Switch to beta*__: ![beta tag](images/beta.png) A new toggle, **Explore the new beta version**, enables you to work in our beta environment, where you can check out all the latest features and new functionality. Don't like what you see? Just switch back by clicking **Go back to the original version**. Your configuration and monitors are unaffected. The following capabilities are part of the current beta program:
    - __*Confusion matrix*__: A [confusion matrix displays](/docs/services/ai-openscale?topic=ai-openscale-it-conf-mtx) the false positives and false negatives. Click a cell to view the subset of feedback records.

## 10 April 2019
{: #rn-10April2019}

- __*Express Path tool now supports customer models*__: Automates the onboarding process to {{site.data.keyword.aios_short}}.

   For more information, see [ibm-ai-openscale-cli](https://pypi.org/project/ibm-ai-openscale-cli/){: external}.


## 5 March 2019
{: #rn-5March2019}

The following new features and changes to the service are available.

{{site.data.keyword.aios_short}} features that have been added or enhanced since the previous release include:

- __*New Credit Risk model*__: A new Credit Risk model example/tutorial is supported for all scoring engines. For more information see the [Getting started](/docs/services/ai-openscale?topic=ai-openscale-gettingstarted#gettingstarted) and [Additional resources](/docs/services/ai-openscale?topic=ai-openscale-arsc-ov#arsc-ov) topics.

- __*Computing debias*__: You can toggle between your production model and a de-biased model created by {{site.data.keyword.aios_short}}. See [Production model and De-biased model](/docs/services/ai-openscale?topic=ai-openscale-it-ov#it-prdb) and [Understanding how de-biasing works](/docs/services/ai-openscale?topic=ai-openscale-mf-monitor#mf-debias) for more information.

## 22 February 2019
{: #rn-22February2019}

The following new features and changes to the service are available.

{{site.data.keyword.aios_short}} features that have been added or enhanced since the previous release include:

- __*UI updates*__: You can import a JSON file to programmatically configure all monitors and features during subscription creation. You can also export the configuration file. See the [Configure deployment subscription using JSON files](/docs/services/ai-openscale?topic=ai-openscale-cf-ov) topic for more information.

## 7 February 2019
{: #rn-7February2019}

The following new features and changes to the service are available.

{{site.data.keyword.aios_short}} features that have been added or enhanced since the previous release include:

- __*UI updates*__: Several improvements have been made to the {{site.data.keyword.aios_short}} user interface, including a way to [check fairness and accuracy on demand](/docs/services/ai-openscale?topic=ai-openscale-it-ov#it-vdep), and the ability to see a list of transactions from the [fairness details chart](/docs/services/ai-openscale?topic=ai-openscale-it-ov#it-tra).

- __*Explainability enhancements*__: All numbers now have the same precision/scale across Pertinent Positive (PP) and Pertinent Negative (PN) values.

- __*Db2 SSL support*__: {{site.data.keyword.aios_short}} supports passing self-signed certificates (Base-64 encoded) with DB2 credentials.

- __*{{site.data.keyword.Bluemix}} Database support*__: {{site.data.keyword.aios_short}} now supports Databases for PostgreSQL, in addition to Compose for PostgreSQL and Db2)

## 14 December 2018
{: #rn-14December2018}

The following new features, changes, and known issues with the service are available.

{{site.data.keyword.aios_short}} features that have been added or enhanced since the beta release include:

- __*General availability*__: The General Availability (GA) release of {{site.data.keyword.aios_full_notm}} as an {{site.data.keyword.Bluemix}} Standard (paid) plan.

- __*{{site.data.keyword.icp4dfull_notm}} V1.2*__: If you are using {{site.data.keyword.wos4d_full}} V1.2, see the documentation, including installation instructions, here: [Installation checklist](/docs/services/ai-openscale?topic=ai-openscale-inst-install-icp#install)

- __*Support for your model type*__: In addition to AI model deployments in {{site.data.keyword.pm_full}}, {{site.data.keyword.aios_short}} supports model deployments in Microsoft Azure, Amazon SageMaker, and Custom environments. See [Supported model types](/docs/services/ai-openscale?topic=ai-openscale-in-ov) for more information.

- __*Free "lite" database*__: A free "lite" managed database provides everything you need to begin using {{site.data.keyword.aios_short}}. See the [{{site.data.keyword.aios_short}} pricing plans](https://{DomainName}/catalog/services/watson-openscale){: external} for details.

- __*Bias monitoring*__: Support for protected attributes of type `float` and `double`, and bias detection on linear regression models. And {{site.data.keyword.aios_short}} can automatically de-bias your AI model for you. See [Understanding fairness](/docs/services/ai-openscale?topic=ai-openscale-mf-monitor) for more information.

- __*Explainability*__: Support for regression models, Python functions, and complementary contrastive explanations. See [Monitoring explainability](/docs/services/ai-openscale?topic=ai-openscale-ie-ov) for more information.

- __*Data Store*__: Quality monitoring without reliance on {{site.data.keyword.pm_full}}, and the ability to use your own database, whether it's Db2, Postgres or Db2 on Cloud.

- __*Enhanced UI*__: The {{site.data.keyword.aios_short}} UI has been improved to include a runtime histogram distribution with toggle for training data, Model ID & Versioning, and a Transaction ID table from the histogram. See [Visualizing data for a specific hour](/docs/services/ai-openscale?topic=ai-openscale-it-ov#it-vdet) for more information.

- __*Alternate tutorial set-up option*__: To automate the provisioning and configuration of the required {{site.data.keyword.Bluemix}} services, and to see an IBM {{site.data.keyword.aios_full}} application, including sample data, you can install and run a Python module. See [Installing a Python module to set up {{site.data.keyword.aios_short}}](/docs/services/ai-openscale?topic=ai-openscale-as-module)

## 17 September 2018
{: #rn-17September2018}

- **Beta preview release** - Welcome to the beta preview release of {{site.data.keyword.aios_full_notm}}.

<p>&nbsp;</p>

## Next steps
{: #relnotes-in-next}

Still have questions?

- [Limitations](/docs/services/ai-openscale?topic=ai-openscale-rn-12ki#wos-limitations)
- [Known issues](/docs/services/ai-openscale?topic=ai-openscale-rn-12ki#cloud-known-unknowns-issues)
