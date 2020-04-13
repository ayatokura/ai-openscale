---

copyright:
  years: 2018, 2020
lastupdated: "2020-04-08"

keywords: metrics, monitoring, custom metrics, thresholds

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

# Performance metrics overview
{: #anlz_metrics_performance}

Use performance monitoring to know the velocity of data records processed by your deployment. You enable performance monitoring when you select the deployment to be tracked and monitored by {{site.data.keyword.aios_short}}.
{: shortdesc}

Performance metrics are calculated based on the following information:

- scoring payload data

For proper monitoring purpose, every scoring request should be logged in {{site.data.keyword.aios_short}} as well. Payload data logging is automated for {{site.data.keyword.pm_full}} engines. For other machine learning engines, the payload data can be provided either by using using the Python client or the REST API. Performance monitoring does not create any additional scoring requests on the monitored deployment.

You can review performance metrics value over time on the {{site.data.keyword.aios_short}} dashboard:

![performance chart](images/wos-performance_metrics_001.png)

## Supported performance metrics
{: #anlz_metrics_performance_supp_quality_mets}

The following performance metrics are supported by {{site.data.keyword.aios_short}}:

- [Throughput](/docs/ai-openscale?topic=ai-openscale-performance_mets_through)