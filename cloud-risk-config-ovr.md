---

copyright:
  years: 2018, 2020
lastupdated: "2020-01-28"

keywords: risk, governance, model risk management, model risk governance

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
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}
{:faq: data-hd-content-type='faq'}

# Configure model risk management and model governance ![beta tag](images/beta.png)
{: #mrm-risk-config-ovr}

Before you can use either the model risk managment or model governance features, you must set up your environment.
{: shortdesc}

- To set up model risk management using Watson OpenScale, see [Configure Watson OpenScale for model risk management](/docs/services/ai-openscale?topic=ai-openscale-mrm-risk-config-ovr-wos-only).
- To set up model governance using Watson OpenScale and IBM OpenPages, see [Configure model governance with IBM OpenPages MRG](/docs/services/ai-openscale?topic=ai-openscale-mrm-risk-config-openpages).

## Turning beta features on and off
{: #mrm-risk-config-ovr-beta-toggling}

As you work with model risk management and governance features, you should keep in mind the following behaviors when turning beta features on and off:

- When you turn beta features off, the pre-production models are hidden.
- Pre-production models, even with beta features turned off, count towards your Lite plan limit. Remove them before hiding beta features if you are finished working with them. If you turn beta features off, it is possible that you receive the following message: "Deployment monitoring quota has been reached. No more deployments can be added. Show beta features to view and manage any hidden pre-production models." It's possible that the pre-prod models that are hidden are causing you to reach your limit.
- If you have models that you created before the model risk management beta, they appear as production models. You can continue to work with them, and any new production models with the beta features turned on or off.




