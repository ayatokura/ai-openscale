---

copyright:
  years: 2018, 2020
lastupdated: "2020-05-18"

keywords: fairness, fairness monitor, payload, perturbation, training data, debiased

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

# Configuring the fairness monitor
{: #mf-monitor}

In {{site.data.keyword.aios_full}}, the fairness monitor scans your deployment for biases to ensure fair outcomes across different populations.
{: shortdesc}

## Requirements
{: #mf-monitor-reqs}

Throughout this process, {{site.data.keyword.aios_full}} analyzes your model and makes recommendations based on the most logical outcome. On the successive pages of the **Fairness** tab, you must provide the following information:

### Values that represent a favorable outcome for the model
{: #mf-monitor-reqs-fave}

Values are derived from the `label` column in the [training data](/docs/ai-openscale?topic=ai-openscale-trainingdata#trainingdata). By default the `predictedLabel` column is set as the `prediction` column.

Favorable and Unfavorable values need to be specified by using the value of the `prediction` column as a string data type, such as `0` or `1`.

### Features to monitor
{: #mf-monitor-reqs-feats}

Only features that are of categorical, numeric (integer), float, or double fairness data type are supported. Features with other data types are not supported. For each of the features, you must configure the following values:

#### Reference and monitored groups
{: #mf-monitor-reqs-refandmon}

Each feature has specific requirements to configure. For example, if you choose `age` as one of your monitored features, you must define the age ranges for a **Reference Group** and a **Monitored Group** by entering values directly in each group.

#### Fairness alert threshold for the feature
{: #mf-monitor-reqs-thresh}

A Fairness threshold is used to specify an acceptable difference between the percentage of Favorable outcomes for the Monitored group as compared to the percentage of Favorable outcomes for the Reference group.

Consider a model that predicts who gets a loan (`favorable outcome=loan granted`) and who doesn't (`unfavorable outcome=loan denied`). Further, the Monitored value for age is `[18,25]`, and the Reference value is `[26,100]`. When the bias detection algorithm runs, if it finds that the percentage of Favorable outcomes for people in the age group `[18,25]` in the last `N` records plus perturbed data is `50%`, while the percentage of Favorable outcomes for people in the age group `[26,100]` is `70%`, then Fairness is computed as 50*100/70 = 71.42.

If the Fairness threshold is set to 80%, then the algorithm flags the model as being biased, because the computed Fairness exceeds the threshold. However, if the threshold is set to 70% then it does not report the model as being biased.

You must enter the values that are sent to the model scoring endpoint (and consequently are added to the payload table). If the data is manipulated before it is sent to the scoring endpoint, then enter the manipulated values. For example, if the original data had values of `Male` and `Female` for *Gender* and it was changed to `M` and `F`, then enter `M` and `F` on this screen.

Depending on your fairness configuration, your fairness score can exceed 100 percent. It means that your monitored group is getting relatively more fair outcomes as compared to the reference group. Technically, it means that the model is unfair in the opposite direction.

### Minimum sample size
{: #mf-monitor-reqs-min}

By setting a minimum sample size, you prevent measuring fairness until a minimum number of records are available in the evaluation data set. This ensures that the sample size is not too small to skew results. Every time bias checking runs, it uses the minimum sample size to decide the number of records on which it does the bias computation.

## Steps
{: #mf-config}
{: help} 
{: support}

To start the configuration process, from the **Fairness** tab, in the **Favorable outcomes** box, click the **Edit** ![The edit icon](images/wos-edit-icon.png) icon.

Follow the prompts and enter required information. When you finish, save your work. 

After you save your settings for the fairness monitor, you can add features to monitor by clicking the **Add feature** button. You can remove features by clicking the **Delete** ![the delete icon is displayed](images/wos-delete-icon.png) icon. You can update the feature groups and thresholds by clicking the **Edit** ![the edit icon is displayed](images/wos-edit-icon.png) icon.
{: tip}


## Next steps
{: #mf-next}

To continue configuring monitors, click the **Drift** tab and click the **Edit** icon. For more information, see [Configuring the drift detection monitor](/docs/ai-openscale?topic=ai-openscale-behavior-drift-config).
