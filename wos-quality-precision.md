---

copyright:
  years: 2018, 2020
lastupdated: "2020-04-08"

keywords: metrics, monitoring, custom metrics, thresholds, precision, score, schedule, recommendation

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
{:note: .note}
{:note: .note}
{:note: .note}
{:note: .note}
{:faq: data-hd-content-type='faq'}

# Precision
{: #quality_precision}

Precision gives the proportion of correct predictions in predictions of positive class.
{: shortdesc}

## Precision at a glance
{: #quality_precision-glance}

- **Description**: Proportion of correct predictions in predictions of positive class
- **Default thresholds**: Lower limit = 80%
- **Default recommendation**:
   - **Upward trend**: An upward trend indicates that the metric is improving. This means that model retraining is effective.
   - **Downward trend**: A downward trend indicates that the metric is deteriorating. Feedback data is becoming significantly different than the training data.
   - **Erratic or irregular variation**: An erratic or irregular variation indicates that the feedback data is not consistent between evaluations. Increase the minimum sample size for the Quality monitor.
- **Problem type**: Binary classification
- **Chart values**: Last value in the time frame
- **Metrics details available**: Confusion matrix

## Interpreting the display
{: #quality_precision-display}

![the Precision chart is displayed.](images/wos-quality-precision.png)

## Do the math
{: #quality_precision-math}

Precision (P) is defined as the number of true positives (Tp) over the number of true positives plus the number of false positives (Fp).


```
             number of true positives
Precision =  __________________________________________________________

             (number of true positives + the number of false positives)
```