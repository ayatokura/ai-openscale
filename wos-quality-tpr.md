---

copyright:
  years: 2018, 2020
lastupdated: "2020-04-08"

keywords: metrics, monitoring, custom metrics, thresholds, score, schedule, recommendation

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

# True positive rate (TPR)
{: #quality_tpr}

The True positive rate (TPR) gives the proportion of correct predictions in predictions of positive class. 
{: shortdesc}

## True positive rate (TPR) at a glance
{: #quality_tpr-glance}

- **Description**: Proportion of correct predictions in predictions of positive class
- **Default thresholds**: lower limit = 80%
- **Default recommendation**:
   - **Upward trend**: An upward trend indicates that the metric is improving. This means that model retraining is effective.
   - **Downward trend**: A downward trend indicates that the metric is deteriorating. Feedback data is becoming significantly different than the training data.
   - **Erratic or irregular variation**: An erratic or irregular variation indicates that the feedback data is not consistent between evaluations. Increase the minimum sample size for the Quality monitor.
- **Problem type**: Binary classification
- **Chart values**: Last value in the time frame
- **Metrics details available**: Confusion matrix

## Interpreting the display
{: #quality_tpr-display}

![the True positive rate chart is displayed.](images/wos-quality-tpr.png)

## Do the math
{: #quality_tpr-math}

The True positive rate is calculated by the following formula:

```
                  number of true positives
TPR =  _________________________________________________________

        (number of true positives + number of false negatives)
```