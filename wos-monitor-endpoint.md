---

copyright:
  years: 2018, 2020
lastupdated: "2020-04-18"

keywords: fairness, monitoring, charts, de-biasing, bias, accuracy

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

# Configuring the endpoint monitor 
{: #mf-endpoints}

To properly log scoring requests or evaluate models for quality, {{site.data.keyword.aios_short}} uses endpoints. The fairness and drift monitors use a payload logging endpoint. The quality monitor uses the feedback endpoint. You can generate a code snippet for the payload and feedback endpoints and for debiased transactions so that you can integrate them into your application.
{: shortdesc}

From the **Endpoints** tab, click **Endpoints**, and then in the **Endpoint** drop-down box, choose one of the following endpoints:

- Payload logging
- Feedback logging
- Debiased transactions

## Next steps
{: #mf-endpoints-nxt-steps}

- For more information about payload or feedback logging, see [Payload and feedback logging in {{site.data.keyword.aios_short}}](/docs/ai-openscale?topic=ai-openscale-cdb-payload).
- For more information about debiased transactions, see [Understanding how de-biasing works](/docs/ai-openscale?topic=ai-openscale-mf-debias).