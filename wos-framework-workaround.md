---

copyright:
  years: 2018, 2020
lastupdated: "2020-08-08"

keywords: machine learning engines, frameworks, Microsoft Azure, Amazone SageMaker, custom ML engine 

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

# Integrating 3rd-party ML engines with {{site.data.keyword.aios_short}}
{: #fmrk-workaround}
{: help} 
{: support}

{{site.data.keyword.aios_full}} integrates with external machine learning service engines, such as Microsoft Azure ML Studio, Microsoft Azure ML Service, and Amazon SageMaker.
{: shortdesc}

You can integrate {{site.data.keyword.aios_short}} with 3rd-party engines in the following ways:

- Engine binding level

  Ability to list deployments and get deployment details.
  
- Deployment subscription level

  {{site.data.keyword.aios_short}} needs to be able to score subscribed deployment in the required format, such as the {{site.data.keyword.pm_full}} format and receive the output in the same compatible format. {{site.data.keyword.aios_short}} must be configured to process both input and output formats.
   
- Payload logging

  Each input and output to the deployed model triggered by a user’s application must be stored in a payload store. The format of the payload records follows the same specification as mentioned in the preceding section on deployment subscription levels.
   
   {{site.data.keyword.aios_short}} uses those records to calculate bias, explanations, and others. It is not possible for {{site.data.keyword.aios_short}} to automatically store transactions that run on the user site, which is outside the {{site.data.keyword.aios_short}} system. This method is one of the ways that {{site.data.keyword.aios_short}} safeguards proprietary information. Use the {{site.data.keyword.aios_short}} Rest API or Python SDK to work with secure data.
   
## Steps to implement this solution
{: #fmrk-workaround-steps}

1. [Learn about custom machine learning engines](/docs/ai-openscale?topic=ai-openscale-fmrk-workaround-customengine).
2. [Set up payload logging](/docs/ai-openscale?topic=ai-openscale-cdb-payload).
3. [Automate payload logging](/docs/ai-openscale?topic=ai-openscale-fmrk-workaround-pyld-lg).
4. Set up a custom machine learning engine by using one of these [Custom machine learning engine examples](/docs/ai-openscale?topic=ai-openscale-fmrk-workaround-cstmmlsengex).

