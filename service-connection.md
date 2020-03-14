---

copyright:
  years: 2020
lastupdated: "2020-03-03"

keywords: isolation for {{site.data.keyword.aios_short}}, service endpoints for {{site.data.keyword.aios_short}}, private network for {{site.data.keyword.aios_short}}, network isolation in {{site.data.keyword.aios_short}}, non-public routes for {{site.data.keyword.aios_short}}, private connection for {{site.data.keyword.aios_short}}

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}

_Name your file `service-connection.md` and include it in the **How to** nav group in the **Enhancing security for servicename** topic group in your `toc` file. See https://test.cloud.ibm.com/docs/writing?topic=writing-security-content-guidance_

_Make sure that you use the following title for your topic._

# Securing your connection to {{site.data.keyword.aios_short}}
{: #service-connection}

To ensure that you have enhanced control and security over your data when you use {{site.data.keyword.aios_short}}, you have the option of using private routes to {{site.data.keyword.cloud}} service endpoints. Private routes are not accessible or reachable over the internet. By using the {{site.data.keyword.cloud_notm}} private service endpoints feature, you can protect your data from threats from the public network and logically extend your private network.
{: shortdesc}

_Required: Document any customer data that goes over public routes even with the IBM Cloud service endpoints feature enabled using a connection over private routes. For example, if your service sends customer data to a data-service using a public route or sends customer logs using public routes to LogDNA that should be documented._


## Before you begin
{: #prereq-service-endpoint}

_Document that users can connect to your service over a private network by using IBM Cloud private service endpoints. Point to the [core documentation](/docs/resources?topic=resources-private-network-endpoints) about how to enable the capability in their account, and then cover any details that are specific to your service about using it, for example:_

You must first enable virtual routing and forwarding in your account, and then you can enable the use of IBM Cloud private service endpoints. For more information about setting up your account to support the private connectivity option, see [Enabling VRF and service endpoints](/docs/account?topic=account-vrf-service-endpoint).

## Setting up service endpoints for {{site.data.keyword.aios_short}}
{: #endpoint-setup}

_Review the following example: https://cloud.ibm.com/docs/compare-comply?topic=watson-public-private-endpoints Depending on how your service supports and requires users to set up this capability, document the steps to ensure a user can successfully connect over the private service endpoint. You can use separate headers to break this into sections if the process includes a lot of steps or use numbered steps for a less lengthy process._

_High level steps typically covered are: Add a private network endpoint, view your endpoint URL, and modifying your apps to use the new endpoint_

## Disabling public service endpoints for for {{site.data.keyword.aios_short}}
{: #endpoint-disable}

_This section will not apply to all services. It does apply to compute services, databases, and Cloud Object Storage at this time._

_Review the following example: https://cloud.ibm.com/docs/containers?topic=containers-cs_network_cluster#set-up-public-se Depending on how and if your service supports users to disable public endpoints, document the steps for disabling a public endpoint to ensure a user can connectly over only the private endpoint, if this is an option. You can use separate headers to break this into sections if the process includes a lot of steps or use numbered steps for a less lengthy process._





