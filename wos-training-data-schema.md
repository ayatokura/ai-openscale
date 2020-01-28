---

copyright:
  years: 2018, 2020
lastupdated: "2020-01-28"

keywords: training data, data, training, models

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

# Formatting and uploading training data in {{site.data.keyword.aios_short}}
{: #fmt-upld-training_data_schema-ovr}

The quality and size of training data is essential to building accurate predictive machine learning and deep learning models. It is the initial, and hopefully representative, dataset that a data scientist uses to train the model. Typically, if you are dividing a pool of data into training, validation, and test sets, training will be the largest of the three. {{site.data.keyword.aios_short}} relies on the training data schema to ensure that the information that you enter to identify the data is accurate and corresponds to the way that {{site.data.keyword.aios_short}} understands the model. 

## Sample training data schema
{: #fmt-upld-training_data_schema-sample}

The following output shows a sample training data schema from the German Credit Risk model:

```bash
"training_data_references": [
        {
            "connection": {
                "endpoint_url": "",
                "access_key_id": "",
                "secret_access_key": ""
            },
            "location": {
                "bucket": "",
                "path": ""
            },
            "type": "fs",
            "schema": {
                "id": "4cdb0a0a-1c69-43a0-a8c0-3918afc7d45f",
                "fields": [
                    {
                        "metadata": {},
                        "name": "CheckingStatus",
                        "nullable": true,
                        "type": "string"
                    },
                    {
                        "metadata": {},
                        "name": "LoanDuration",
                        "nullable": true,
                        "type": "integer"
                    },
                    {
                        "metadata": {},
                        "name": "CreditHistory",
                        "nullable": true,
                        "type": "string"
                    },
                    {
                        "metadata": {},
                        "name": "LoanPurpose",
                        "nullable": true,
                        "type": "string"
                    },
                    {
                        "metadata": {},
                        "name": "LoanAmount",
                        "nullable": true,
                        "type": "integer"
                    },
                    {
                        "metadata": {},
                        "name": "ExistingSavings",
                        "nullable": true,
                        "type": "string"
                    },
                    {
                        "metadata": {},
                        "name": "EmploymentDuration",
                        "nullable": true,
                        "type": "string"
                    },
                    {
                        "metadata": {},
                        "name": "InstallmentPercent",
                        "nullable": true,
                        "type": "integer"
                    },
                    {
                        "metadata": {},
                        "name": "Sex",
                        "nullable": true,
                        "type": "string"
                    },
                    {
                        "metadata": {},
                        "name": "OthersOnLoan",
                        "nullable": true,
                        "type": "string"
                    },
                    {
                        "metadata": {},
                        "name": "CurrentResidenceDuration",
                        "nullable": true,
                        "type": "integer"
                    },
                    {
                        "metadata": {},
                        "name": "OwnsProperty",
                        "nullable": true,
                        "type": "string"
                    },
                    {
                        "metadata": {},
                        "name": "Age",
                        "nullable": true,
                        "type": "integer"
                    },
                    {
                        "metadata": {},
                        "name": "InstallmentPlans",
                        "nullable": true,
                        "type": "string"
                    },
                    {
                        "metadata": {},
                        "name": "Housing",
                        "nullable": true,
                        "type": "string"
                    },
                    {
                        "metadata": {},
                        "name": "ExistingCreditsCount",
                        "nullable": true,
                        "type": "integer"
                    },
                    {
                        "metadata": {},
                        "name": "Job",
                        "nullable": true,
                        "type": "string"
                    },
                    {
                        "metadata": {},
                        "name": "Dependents",
                        "nullable": true,
                        "type": "integer"
                    },
                    {
                        "metadata": {},
                        "name": "Telephone",
                        "nullable": true,
                        "type": "string"
                    },
                    {
                        "metadata": {},
                        "name": "ForeignWorker",
                        "nullable": true,
                        "type": "string"
                    },
                    {
                        "metadata": {
                            "modeling_role": "target",
                            "values": [
                                "No Risk",
                                "Risk"
                            ]
                        },
                        "name": "Risk",
                        "nullable": true,
                        "type": "string"
                    }
                ],
                "type": "struct"
            }
        }
    ]

```
{: codeblock}


