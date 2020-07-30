---

copyright:
  years: 2018, 2020
lastupdated: "2020-05-18"

keywords: deleting, service plans, plans, Lite plan, standard plan, datamart

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
{:faq: data-hd-content-type='faq'}

# Deleting the {{site.data.keyword.aios_short}} service instance and data
{: #cf-deleting-wos}

You can delete the {{site.data.keyword.aios_full}} service instance and related data. As a Lite plan user, after 30 days of not using the service, the datamart is automatically deleted.
{: shortdesc}

When the datamart is deleted, it includes the following service configuration settings and tables:

- all configuration tables, including the following configuration tables and files:
  
  - bindings
  - subscriptions
  - settings

- the tables that are created by the {{site.data.keyword.aios_short}} service, including, but not limited to, the following tables:
  
  - payload 
  - feedback
  - manual labeling
  - monitors
  - performance 
  - explaination 
  - annotation tables


## Lite plan
{: #cf-deleting-wos-lite-plan}

Lite plan services are deleted after 30 days of inactivity.
{: important}

If you stop using {{site.data.keyword.aios_short}} and your {{site.data.keyword.aios_short}} service instance is on the Lite plan, even if you don't delete your instance from {{site.data.keyword.bluemix_short}}, your datamart is deleted after 30 days of inactivity.

## Standard plan
{: #cf-deleting-wos-standard-plan}

As a user of the Standard plan, your datamart is not automatically deleted, however you can delete your {{site.data.keyword.aios_short}} service instance from {{site.data.keyword.Bluemix}} and use the command line interface to delete the datamart.

You must delete your instance from the {{site.data.keyword.Bluemix}} dashboard and then use the command line interface tool to completely remove your data. For more information, see [ibmcloud resource reclamations](https://cloud.ibm.com/docs/cli?topic=cli-ibmcloud_commands_resource#ibmcloud_resource_reclamations).


## Next steps
{: #cf-deleting-wos-next-steps}

To understand more about upgrading {{site.data.keyword.Bluemix}} services, see [Changing service plans](/docs/resources?topic=resources-changing){: external}.