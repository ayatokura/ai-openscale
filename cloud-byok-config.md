---

copyright:
  years: 2018, 2020
lastupdated: "2020-01-28"


keywords: identity and access management, authentication

subcollection: ai-openscale

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:pre: .pre}
{:codeblock: .codeblock}
{:table: .aria-labeledby="caption"}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}
{:faq: data-hd-content-type='faq'}

# {{site.data.keyword.aios_short}} Identity and Access Management 
{: #iam-docs-template}


Bring your own encryption (BYOE)—also called bring your own key (BYOK)—refers to a cloud computing security marketing model that purports to help cloud service customers to use their own encryption software and manage their own encryption keys.[1] BYOE allows cloud service customers to use a virtualized example of their own encryption software together with the business applications they are hosting in the cloud, in order to encrypt their data. The business applications hosted is then set up such that all its data will be processed by the encryption software, which then writes the ciphertext version of the data to the cloud service provider's physical data store, and readily decrypts ciphertext data upon retrieval requests.[2] This gives the enterprise the perceived control of its own keys and producing its own master key by relying on its own internal hardware security modules (HSM) that is then transmitted to the HSM within the cloud. Data owners may believe their data is secured because the master key lies in the enterprise's HSM and not that of the cloud service provider's.[3] When the data is no longer needed (i.e. when cloud users choose to abandon the cloud service), the keys can simply be deleted. That practice is called crypto-shredding.

What is Bring Your Own Key (BYOK)?
While cloud computing offers many advantages, a major disadvantage has been security, because data physically resides with the cloud service provider (CSP) and out of the direct control of the owner of the data. For enterprises that elect to use encryption to protect their data, securing their encryption keys is of paramount importance.

Bring Your Own Key (BYOK) allows enterprises to encrypt their data and retain control and management of their encryption keys. However, some BYOK plans upload the encryption keys to the CSP infrastructure. In these cases, the enterprise has once again forfeited control of its keys.

A best-practice solution to this "Bring Your Own Key" problem is for the enterprise to generate strong keys in a tamper-resistant hardware security module (HSM) and control the secure export of its keys to the cloud, thereby strengthening its key management practices.


