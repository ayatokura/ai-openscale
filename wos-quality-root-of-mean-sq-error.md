---

copyright:
  years: 2018, 2020
lastupdated: "2020-08-08"

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
{:note: .note}
{:note: .note}
{:note: .note}
{:note: .note}
{:faq: data-hd-content-type='faq'}

# Root of mean squared error
{: #supqualdets_squ_errors_mean}

The root-mean-squared error (RMSE) view shows the difference between the predicted and observed values in your model.
{: shortdesc}

## Root of mean squared error at a glance
{: #anlz_metrics_supqualdets_squ_errors_mean}

- **Description**: Square root of mean of squared difference between model prediction and target value
- **Default thresholds**: Upper limit = 80%
- **Default recommendation**:
   - **Upward trend**: An upward trend indicates that the metric is deteriorating. Feedback data is becoming significantly different than the training data.
   - **Downward trend**: A downward trend indicates that the metric is improving. This means that model retraining is effective.
   - **Erratic or irregular variation**: An erratic or irregular variation indicates that the feedback data is not consistent between evaluations. Increase the minimum sample size for the Quality monitor.
- **Problem type**: Regression
- **Chart values**: Last value in the time frame
- **Metrics details available**: None


## Do the math
{: #supqualdets_squ_errors_mean-math}

The Root of mean squared error is equal to the Square root of the mean of (forecasts minus observed values) squared.

```
          ___________________________________________________________
RMSE  =  √(forecasts - observed values)*(forecasts - observed values)
```