---

copyright:
  years: 2018, 2020
lastupdated: "2020-04-08"

keywords: metrics, monitoring, custom metrics, thresholds, Proportion explained variance, score, schedule, recommendation

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

# Proportion explained variance
{: #quality_var}

Proportion explained variance gives the ratio of explained variance and target variance. Explained variance is the difference between target variance and variance of prediction error.
{: shortdesc}

## Proportion explained variance at a glance
{: #quality_var-glance}

- **Description**: Proportion explained variance is the ratio of explained variance and target variance. Explained variance is the difference between target variance and variance of prediction error.
- **Default thresholds**: Lower limit = 80%
- **Default recommendation**:
   - **Upward trend**: An upward trend indicates that the metric is improving. This means that model retraining is effective.
   - **Downward trend**: A downward trend indicates that the metric is deteriorating. Feedback data is becoming significantly different than the training data.
   - **Erratic or irregular variation**: An erratic or irregular variation indicates that the feedback data is not consistent between evaluations. Increase the minimum sample size for the Quality monitor.
- **Problem type**: Regression
- **Chart values**: Last value in the time frame
- **Metrics details available**: None



## Do the math
{: #quality_var-math}

The Proportion explained variance is calculated by averaging the numbers, then for each number, subtract the mean and square the results. Then work out the squares

```
                                  sum of squares between groups 
Proportion explained variance =  ________________________________

                                      sum of squares total
```