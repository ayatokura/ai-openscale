---

copyright:
  years: 2018, 2020
lastupdated: "2020-08-08"

keywords: activity, tracker, events, API, public API, subscription, binding

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

# Activity Tracker events
{: #at-events}

When you have {{site.data.keyword.aios_short}} provisioned as a service in your {{site.data.keyword.cloud_notm}} account, you can see the following events in the [{{site.data.keyword.cloud_notm}} Activity Tracker](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started){: external}.
{: shortdesc}

## Events for public APIs
{: #at-pubapi}

| Action | Description |
| -- | -- |
| aiopenscale.metrics.create | Store metric in the {{site.data.keyword.aios_short}} instance |
| aiopenscale.payload.create | Log payload in the {{site.data.keyword.aios_short}} instance |

## Events for private APIs
{: #at-priapi}

| Action | Description |
| -- | -- |
| aiopenscale.datamart.configure | Configure the {{site.data.keyword.aios_short}} instance |
| aiopenscale.datamart.delete | Delete the {{site.data.keyword.aios_short}} instance |
| aiopenscale.binding.create | Add service binding to the {{site.data.keyword.aios_short}} instance |
| aiopenscale.binding.delete | Delete service binding from the {{site.data.keyword.aios_short}} instance |
| aiopenscale.subscription.create | Add subscription to the {{site.data.keyword.aios_short}} instance |
| aiopenscale.subscription.delete | Delete subscription from the {{site.data.keyword.aios_short}} instance |
