---

copyright:
  years: 2018, 2020
lastupdated: "2020-04-08"

keywords: accuracy, 

subcollection: ai-openscale

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:pre: .pre}
{:codeblock: .codeblock}
{:help: data-hd-content-type='help'}
{:support: data-reuse='support'}
{:screen: .screen}
{:note: .note}
{:note: .note}
{:note: .note}
{:note: .note}
{:faq: data-hd-content-type='faq'}

# Configuring the quality monitor
{: #acc-monitor}

The quality monitor (previously known as the accuracy monitor) reveals how well your model predicts outcomes.
{: shortdesc}

## Requirements
{: #acc-config-reqs}

On the successive pages of the **Quality** tab, you must provide the following information:

### Quality alert threshold

Select a value that represents an acceptable accuracy level. For example, if you are using the **German Credit Risk model** for the interactive tutorial, set the alert to **90%**.

Quality is a value that is synthesized from relevant data science metrics that are associated with each particular model type. The score is a normalized measure that compares accuracy across different model types. In typical situations, an accuracy score of 80 is sufficient. For the tutorial, to generate more data, enter 90.
{: note}

### Minimum and maximum sample sizes

By setting a minimum sample size, you prevent measuring quality until a minimum number of records are available in the evaluation data set. This ensures that the sample size is not too small to skew results. Every time quality checking runs, it uses the minimum sample size to decide the number of records on which it does the quality metrics computation.

The maximum sample size helps better manage the time and effort it takes to evaluate the data set. Only the most recent records are evaluated if this size is exceeded. For example, if you are using the **German Credit Risk model** for the interactive tutorial, set the minimum sample size to **100** and the maximum sample size to **10000**.

## Steps
{: #acc-config}
{: help} 
{: support}

To start the configuration process, from the **Quality** tab, in the **Quality threshold** box, click the **Edit** ![The edit icon](images/wos-edit-icon.png) icon.

Follow the prompts and enter required information. When you finish, a summary of your selections is presented for review. If you want to change anything, click the **Edit** icon for that section, otherwise, save your work.

### Next steps
{: #acc-next}

To continue configuring monitors, click the **Fairness** tab and click the **Edit** icon. For more information, see [Configuring the fairness monitor](/docs/ai-openscale?topic=ai-openscale-mf-monitor).
