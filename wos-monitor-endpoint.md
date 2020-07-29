---

copyright:
  years: 2018, 2020
lastupdated: "2020-05-18"

keywords: fairness, monitoring, charts, debiasing, bias, accuracy

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
{:faq: data-hd-content-type='faq'}

# Configuring the endpoint monitor 
{: #mf-endpoints}

To properly log scoring requests or evaluate models for quality, {{site.data.keyword.aios_short}} uses endpoints. The fairness and drift monitors use a payload logging endpoint. The quality monitor uses the feedback endpoint. You can generate a code snippet for the payload and feedback endpoints and for debiased transactions so that you can integrate them into your application.
{: shortdesc}

## Steps
{: #mf-endpoints-steps}

1. On the **Evaluations** window, click **Configure monitors**.
2. In the navigation pane, click **Endpoints**.
3. In the **Information** pane, click the **Endpoints** tab.
4. From the **Endpoint** list, choose the type of endpoint: **Payload logging**, **Feedback logging**, or **Debiased transactions**.
5. From the **Code language** list, choose the type of code: **cURL**, **Java**, or **Python**.
6. To copy the code snippet, click the **Copy to clipboard** ![The copy to clipboard icon is displayed.](images/copy-icon.png) icon.


## Next steps
{: #mf-endpoints-nxt-steps}

- For more information about payload or feedback logging, see [Payload and feedback logging in {{site.data.keyword.aios_short}}](/docs/ai-openscale?topic=ai-openscale-cdb-payload).
- For more information about debiased transactions, see [Understanding how debiasing works](/docs/ai-openscale?topic=ai-openscale-mf-debias).