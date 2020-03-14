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

# Securing your data in {{site.data.keyword.aios_short}}
{: #mng-data}

To ensure that you can securely manage your data when you use {{site.data.keyword.aios_short}}, it is important to know exactly what data is stored and encrypted and how you can delete any stored personal data. Data encryption by using customer-managed keys is supported by using Key Protect with {{site.data.keyword.aios_short}}.
{: shortdesc}

## What is Bring Your Own Key (BYOK)?
{: #byok-ovr-byok}

Bring your own key (BYOK) or bring your own encryption (BYOE) refers to the infrastructure and method by which cloud service clients can manage their own encryption software and keys. This adds a layer of security that protects both data at rest and data in motion. 

## How your data is stored and encrypted in {{site.data.keyword.aios_short}}
{: #data-storage}

{{site.data.keyword.keymanagementservicefull}} helps secure your sensitive data from unauthorized access or inadvertent employee release while meeting compliance auditing standards. It provides mandatory control of user access requests to encryption keys and manages the entire lifecycle of keys from creation through application use, key archival, and key destruction. Offered as a Platform as a Service on the IBM Cloud™, Key Protect provisions and stores cryptographic keys using FIPS 140-2 Level 3 certified (Federal Information Processing Standard) hardware security module (HSM) devices located within secure IBM data centers.

## Protecting your sensitive data in {{site.data.keyword.aios_short}}
{: #data-encryption}

You can add a higher level of encryption protection and control to your data at rest (when it is stored) and data in motion (when it is transported) by enabling integration with IBM® Key Protect for IBM Cloud™.

The data that you store in {{site.data.keyword.cloud_notm}} is encrypted at rest by using a randomly generated key. If you need to control the encryption keys, you can integrate Key Protect. This process is commonly referred to as Bring your own keys (BYOK). With Key Protect you can create, import, and manage encryption keys. You can assign access policies to the keys, assign users or service IDs to the keys, or give the key access only to a specific service. The first 20 keys are free.

### About customer-managed keys
{: #about-encryption}

{{site.data.keyword.aios_short}} uses [envelope encryption](#x9860393){: term} to implement customer-managed keys. Envelope encryption describes encrypting one encryption key with another encryption key. The key used to encrypt the actual data is known as a [data encryption key (DEK)](#x4791827){: term}. The DEK itself is never stored but is wrapped by a second key that is known as the key encryption key (KEK) to create a wrapped DEK. To decrypt data, the wrapped DEK is unwrapped to get the DEK. This process is possible only by accessing the KEK, which in this case is your root key that is stored in {{site.data.keyword.keymanagementserviceshort}}.

{{site.data.keyword.keymanagementserviceshort}} keys are secured by FIPS 140-2 Level 3 certified cloud-based [hardware security modules (HSMs)](#x6704988){: term}.


### Enabling customer-managed keys for {{site.data.keyword.aios_short}}
{: #using-byok}

Integrating Key Protect with Watson Premium services involves the following steps in the IBM Cloud console.

1. Create an instance of Key Protect.
2. Add a root key to the Key Protect instance.
3. Grant Key Protect access to all instances of your Watson service.
4. Encrypt the Watson service data.

### Working with customer-managed keys for {{site.data.keyword.aios_short}}
{: #working-with-keys}

You can integrate {{site.data.keyword.aios_short}} with {{site.data.keyword.keymanagementservicefull}} through the use of the API by making `user_preferences` calls. The following parameters apply:

- HTTP method: PUT
- URL: https://aiopenscale.cloud.ibm.com/openscale/{service-instance-id}/v2/user_preferences/user_root_key_crn
- Payload: {"user_root_key_crn": crn_from_step_1}

### Case 1: Key Protect during initial set up
{: #byok-ovr-wos-scenario1}

1. Provision a {{site.data.keyword.aios_short}} instance.
2. After you provision an instance, but before you do any other configuration, you must complete the following steps:

    1. Provision an instance of {{site.data.keyword.keymanagementservicefull}} and obtain the instance `CRN` value.
    2. Make an API call to {{site.data.keyword.aios_short}} /v2/user_preferences, and specify the `{"user_root_key_crn": crn_from_step_1}` variable.

3. Create a DataMart, for which a database configuration is created.
4. The configuration service makes an API call to {{site.data.keyword.keymanagementservicefull}} specified by the `user_root_key_crn` property. The service returns a new encryption key in both a wrapped and unwrapped form. Use the unwrapped key form to encrypt the database password. The wrapped key form is persisted in instance properties. To decrypt a database password, use the wrapped key form to get the unwrapped key form either from cache or through API call to {{site.data.keyword.keymanagementservicefull}}. Then, decryption is done by using the unwrapped key.

### Case 2: Key Protect after set up
{: #byok-ovr-wos-scenario2}

1. Provision a {{site.data.keyword.aios_short}} instance.
2. After you provision an instance, initialize the system either by running the auto setup or by performing a manual configuration. In this scenario, the database configuration is created with a password that is not encrypted with the user's key protect root key.
3. After configuration, you must provision an instance of {{site.data.keyword.keymanagementservicefull}} and get the instance `CRN` value.
4. Make an API call to {{site.data.keyword.aios_short}} /v2/user_preferences, and specify the `{"user_root_key_crn": crn_from_step_1}` variable. When you specify the `user_root_key_crn` variable, all instance secrets are automatically re-encrypted by using {{site.data.keyword.keymanagementservicefull}. If you delete the  `user_root_key_crn` variable, all instance secrets are automatically re-encrypted by using global key. The actual re-encryption is the same as in the previous case, **Case 1**.

<!--
## Deleting your data in {{site.data.keyword.aios_short}}
{: #data-delete}

_Document how users can delete their data within the service._

_If applicable, add H3s in this section to tailor the information to particular types of data. For example, you might have a "Deleting keys" section and a "Deleting a database" section._

_Include information about whether deleting the service fully erases all data. If deleting the service doesn't remove all personal data, include information about how users can completely delete their data._

-->
### Deleting {{site.data.keyword.aios_short}} instances
{: #service-delete}

The {{site.data.keyword.aios_short}} data retention policy describes how long your data is stored after you delete the service. The data retention policy is included in the {{site.data.keyword.aios_short}} service description, which you can find in the [{{site.data.keyword.cloud_notm}} Terms and Notices](/docs/overview?topic=overview-terms).

For more details, see the following topics:

- [Getting started tutorial](/docs/key-protect?topic=key-protect-getting-started-tutorial).
  
  {{site.data.keyword.keymanagementservicefull}} helps you provision encrypted keys for apps across IBM Cloud services. This tutorial shows you how to create and add existing cryptographic keys by using the Key Protect dashboard, so you can manage data encryption from one central location.
  
- [Integrating services](/docs/key-protect?topic=key-protect-integrate-services).
  
  {{site.data.keyword.keymanagementservicefull}} integrates with a number of IBM Cloud services to enable encryption with customer-managed keys for those services. Encryption with customer-managed encryption keys is sometimes called Bring Your Own Key (BYOK).
  
- [Integrating with IBM Cloud Object Storage](/docs/key-protect?topic=key-protect-integrate-cos).
  
  {{site.data.keyword.keymanagementservicefull}} and IBM® Cloud Object Storage work together to help you own the security of your at-rest data. Learn how to add advanced encryption to your IBM® Cloud Object Storage resources by using the IBM Key Protect service.
  
- [Provisioning the service](/docs/key-protect?topic=key-protect-provision).
  
  You can create an instance of {{site.data.keyword.keymanagementservicefull}} by using the IBM Cloud console or the IBM Cloud CLI.
  
