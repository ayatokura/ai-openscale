---

copyright:
  years: 2020
lastupdated: "2020-02-24"

keywords: data encryption in {{site.data.keyword.aios_short}}, data storage for {{site.data.keyword.aios_short}}, bring your own keys for {{site.data.keyword.aios_short}}, BYOK for {{site.data.keyword.aios_short}}, key management for {{site.data.keyword.aios_short}}, key encryption for {{site.data.keyword.aios_short}}, personal data in {{site.data.keyword.aios_short}}, data deletion for {{site.data.keyword.aios_short}}, data in {{site.data.keyword.aios_short}}, data security in {{site.data.keyword.aios_short}}, {{site.data.keyword.aios_short}}

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}

_Name your file `data-security.md` and include it in the **How to** nav group in the **Enhancing security for servicename** topic group in your `toc` file. See https://test.cloud.ibm.com/docs/writing?topic=writing-security-content-guidance_

_Make sure that you use the following title for your topic._

# Securing your data in {{site.data.keyword.aios_short}}
{: #mng-data}

To ensure that you can securely manage your data when you use {{site.data.keyword.aios_short}}, it is important to know exactly what data is stored and encrypted and how you can delete any stored personal data. Data encryption by using customer-managed keys is supported by using Key Protect with {{site.data.keyword.aios_short}}.
{: shortdesc}

## How your data is stored and encrypted in {{site.data.keyword.aios_short}}
{: #data-storage}

_Document how your offering stores and encrypts user data as it relates to user activities. What data is encrypted and what is not? How is data encrypted?_  

_If you are using separate keys to encrypt each customer, provide that information here._

_Do not include any details that would give malicious persons an advantage to compromising your offering environment._


## Protecting your sensitive data in {{site.data.keyword.aios_short}}
{: #data-encryption}

_Document if your services supports Key Protect and/or Hyper Protect Crypto Services for customer-managed keys (also known as bring your own keys). Explain what data is encrypted with customer-managed keys and what data is not. The following is example text from a Watson service:_

You can add a higher level of encryption protection and control to your data at rest (when it is stored) and data in motion (when it is transported) by enabling integration with IBM® Key Protect for IBM Cloud™.

The data that you store in {{site.data.keyword.cloud_notm}} is encrypted at rest by using a randomly generated key. If you need to control the encryption keys, you can integrate Key Protect. This process is commonly referred to as Bring your own keys (BYOK). With Key Protect you can create, import, and manage encryption keys. You can assign access policies to the keys, assign users or service IDs to the keys, or give the key access only to a specific service. The first 20 keys are free.

### About customer-managed keys
{: #about-encryption}

_Include any information specific to how your service supports BYOK. As an example, see the following sample text from Watson (also available: https://test.cloud.ibm.com/docs/services/watson?topic=watson-keyservice#keyservice-about). Most services should be able to reuse this paragraph as-is because this is how encryption works with Key Protect on IBM Cloud_:

{{site.data.keyword.aios_short}} uses [envelope encryption](#x9860393){: term} to implement customer-managed keys. Envelope encryption describes encrypting one encryption key with another encryption key. The key used to encrypt the actual data is known as a [data encryption key (DEK)](#x4791827){: term}. The DEK itself is never stored but is wrapped by a second key that is known as the key encryption key (KEK) to create a wrapped DEK. To decrypt data, the wrapped DEK is unwrapped to get the DEK. This process is possible only by accessing the KEK, which in this case is your root key that is stored in {{site.data.keyword.keymanagementserviceshort}}.

{{site.data.keyword.keymanagementserviceshort}} keys are secured by FIPS 140-2 Level 3 certified cloud-based [hardware security modules (HSMs)](#x6704988){: term}.


### Enabling customer-managed keys for {{site.data.keyword.aios_short}}
{: #using-byok}

_Document the steps a customer must take to get their keys or bring their keys to encrypt their data with your service. As an example, see: https://test.cloud.ibm.com/docs/services/watson?topic=watson-keyservice#keyservice-steps_

### Working with customer-managed keys for {{site.data.keyword.aios_short}}
{: #working-with-keys}

_Document any common scenarios that can help your customers know how to use their keys to protect data within the service. As an example, see: https://test.cloud.ibm.com/docs/services/watson?topic=watson-keyservice#keyservice-using. You should consider documenting scenarios such as key rotation and temporarily preventing and restoring access._ 

## Deleting your data in {{site.data.keyword.aios_short}}
{: #data-delete}

_Document how users can delete their data within the service._

_If applicable, add H3s in this section to tailor the information to particular types of data. For example, you might have a "Deleting keys" section and a "Deleting a database" section._

### Deleting {{site.data.keyword.aios_short}} instances
{: #service-delete}

_Include information about whether deleting the service fully erases all data. If deleting the service doesn't remove all personal data, include information about how users can completely delete their data._

_Information about how long services keep data after instances are deleted is covered in the service description. Include the following reference for users to find their data retention period._

The {{site.data.keyword.aios_short}} data retention policy describes how long your data is stored after you delete the service. The data retention policy is included in the {{site.data.keyword.aios_short}} service description, which you can find in the [{{site.data.keyword.cloud_notm}} Terms and Notices](/docs/overview?topic=overview-terms).

### Restoring deleted data for {{site.data.keyword.aios_short}}
{: #data-restore}

_If users can restore deleted data within your service, include this optional section and the task that users can complete to do so._

_Important: Don't include information about restoring your resource via the reclamation controller because it's available only on a limited basis._
