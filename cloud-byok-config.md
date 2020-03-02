---

copyright:
  years: 2018, 2020
lastupdated: "2020-01-28"


keywords: security, security keys, bring your own key, byok, byoe, 

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

# Protecting sensitive information in {{site.data.keyword.aios_short}}
{: #byok-ovr}

You can add a higher level of encryption protection and control to your data both when it is stored and transported by enabling integration with {{site.data.keyword.keymanagementservicefull}}. 
{: shortdesc}

## What is Bring Your Own Key (BYOK)?
{: #byok-ovr-byok}

Bring your own key (BYOK) or bring your own encryption (BYOE) refers to the infrastructure and method by which cloud service clients can manage their own encryption software and keys. This adds a layer of security that protects both data at rest and data in motion. 

## Why {{site.data.keyword.keymanagementservicefull}}?
{: #byok-ovr-ikpfc}

{{site.data.keyword.keymanagementservicefull}} helps secure your sensitive data from unauthorized access or inadvertent employee release while meeting compliance auditing standards. It provides mandatory control of user access requests to encryption keys and manages the entire lifecycle of keys from creation through application use, key archival, and key destruction. Offered as a Platform as a Service on the IBM Cloud™, Key Protect provisions and stores cryptographic keys using FIPS 140-2 Level 3 certified (Federal Information Processing Standard) hardware security module (HSM) devices located within secure IBM data centers.

## Integrating {{site.data.keyword.aios_full}}
{: #byok-ovr-wos}

You can integrate {{site.data.keyword.aios_short}} with {{site.data.keyword.keymanagementservicefull}} by referring to the following tasks:

- [Getting started tutorial](/docs/key-protect?topic=key-protect-getting-started-tutorial).
  
  {{site.data.keyword.keymanagementservicefull}} helps you provision encrypted keys for apps across IBM Cloud services. This tutorial shows you how to create and add existing cryptographic keys by using the Key Protect dashboard, so you can manage data encryption from one central location.
  
- [Integrating services](/docs/key-protect?topic=key-protect-integrate-services).
  
  {{site.data.keyword.keymanagementservicefull}} integrates with a number of IBM Cloud services to enable encryption with customer-managed keys for those services. Encryption with customer-managed encryption keys is sometimes called Bring Your Own Key (BYOK).
  
- [Integrating with IBM Cloud Object Storage](/docs/key-protect?topic=key-protect-integrate-cos).
  
  {{site.data.keyword.keymanagementservicefull}} and IBM® Cloud Object Storage work together to help you own the security of your at-rest data. Learn how to add advanced encryption to your IBM® Cloud Object Storage resources by using the IBM Key Protect service.
  
- [Provisioning the service](/docs/key-protect?topic=key-protect-provision).
  
  You can create an instance of {{site.data.keyword.keymanagementservicefull}} by using the IBM Cloud console or the IBM Cloud CLI.
  
