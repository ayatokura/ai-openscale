---

copyright:
  years: 2018, 2020
lastupdated: "2020-05-18"

keywords: supported frameworks, models, model types, limitations, limits, data types

subcollection: ai-openscale

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:apikey: data-credential-placeholder='apikey'}
{:url: data-credential-placeholder='url'}
{:tooling-url: data-tooling-url-placeholder='tooling-url'}
{:hide-dashboard: .hide-dashboard}
{:hide-in-docs: .hide-in-docs}
{:faq: data-hd-content-type='faq'}

# Known issues and limitations for {{site.data.keyword.aios_short}} for {{site.data.keyword.cloud_notm}}
{: #rn-12ki}

The following list contains the known issues and limitation that are common for {{site.data.keyword.aios_full}} for {{site.data.keyword.Bluemix}} and {{site.data.keyword.wos4d_full}} and specific to {{site.data.keyword.aios_full}} for {{site.data.keyword.Bluemix}}.
{: shortdesc}

<p>&nbsp;</p>

## Common issues
{: #wos-common-issues}

The following limitations and known issues are common to both {{site.data.keyword.aios_full}} on {{site.data.keyword.Bluemix}} and {{site.data.keyword.wos4d_full}}.

<p>&nbsp;</p>


### Common limitations
{: #wos-limitations}

- {{site.data.keyword.aios_short}} does not support models where the data type of the model prediction is binary. You must change such models so that the data type of their prediction is a string or integer data type.
- Support for the XGBoost framework has the following limitations for classification problems: For binary classification, {{site.data.keyword.aios_short}} supports the `binary:logistic` logistic regression function with an output as a probability of `True`. For multiclass classification, {{site.data.keyword.aios_short}} supports the `multi:softprob` function where the result contains the predicted probability of each data point belonging to each class.
- Fairness and drift metrics are not supported for unstructured (image or text) data types.
- Having an equals sign (=) in the column name of a data set causes an issue with explainability and generates the following error message: `Error: An error occurred while computing feature importance`. Do not use an equals sign (=) in a column name. It is not supported.

<p>&nbsp;</p>

### Unexpected data type causes automatic payload logging to fail
{: #wos-limitations-float-not-vector-error}

If your model output includes a field with a probability value, it must be a vector. Otherwise, automatic payload scoring is disabled even for {{site.data.keyword.pm_full}}.



<p>&nbsp;</p>

### Limit on the number of features for a model
{: #wos-limitations-feat-col-size-limit}

Scoring payloads for a model must fit within the maximum width that is allowed for the table that is created by the payload logging process in the data mart database. The maximum width includes some buffer for the internal-use columns that {{site.data.keyword.aios_short}} itself adds. In addition, apart from the width there is also a hardcoded limit of 1012 features.

The following table summarizes what this limit means for models with different sizes of features:

Table 1: Feature column limits

Feature type | Feature # limit
-|-
int64 or float64 or string length 1-64 | 1012
string length 65-2048 | 444
string length 2059-32K | 28
{: caption="Feature column limits" caption-side="top"}


Because many models have features of mixed types, the following sample configurations can be used for planning purposes:

- For int64 or float64 or strings of length 64 or less, count as 64.
- For strings in the range of 65 - 2048, count as 2048.
- For strings in the range of 2048 - 32 K, count as 32 K.
- The total length of all features must not exceed ~900 K.

<p>&nbsp;</p>


### Not all Db2 instances function identically
{: #wos-limitations-db2-version}

{{site.data.keyword.aios_short}} supports Db2 Warehouse add-on, Db2 Advanced Enterprise Server Edition add-on, and Db2 Enterprise Server Edition (v. 11.5.1 or later) installation that is accessible to the cluster. Be aware of the following limitation:

- {{site.data.keyword.aios_short}} requires a table space with a page size of 32k or larger.

<p>&nbsp;</p>


### Drift configuration errors prevent configuration of drift monitor
{: #wos-common-issues-mismatchdatatype}

The flexibility of the model configuration screen can also lead to problems later on when you want to configure monitors, such as the drift detection monitor. Because you can choose the data types, you must ensure that your choices match the input schema of the model. The following error might occur if the prediction column type is not properly selected:

```
"error": AIQDS2003E",
"message": "The model predictions '[0. 1.]' are different from class names in training data '['No' 'Yes']' for the subscription <<number>> in datamart <<datamart ID>> and service binding <<binding ID>>.
```

The following cases are the most-likely cause:

- The `class` label is of string type and `modeling_role` **prediction** is assigned to the **prediction** column as a double type because that is how the output data schema is defined.
- You select the **prediction** column of double type in the UI, which is not restricted.



### Payload formats
{: #wos-common-issues-payloadformat}

For proper processing of payload analytics, {{site.data.keyword.aios_short}} does not support column names with double quotation marks (") in the payload. This format limit affects both scoring payload and feedback data in CSV and JSON formats.

<p>&nbsp;</p>



### Microsoft Azure ML Studio
{: #wos-common-issues-msazure}

- Of the two types of Azure Machine Learning web services, only the `New` type is supported by {{site.data.keyword.aios_short}}. The `Classic` type is not supported.

- __*Default input name must be used*__: In the Azure web service, the default input name is `"input1"`. Currently, this field is mandated for {{site.data.keyword.aios_short}} and, if it is missing, {{site.data.keyword.aios_short}} fails.

  If your Azure web service does not use the default name, change the input field name to `"input1"`, then redeploy your web service and reconfigure your OpenScale machine learning provider settings.

- If calls to Microsoft Azure ML Studio to list the machine learning models causes the response to time out, for example when you have many web services, you must increase timeout values. You might need to work around this issue by changing the `/etc/haproxy/haproxy.cfg` configuration setting:

   - Log in to the load balancer node and update `/etc/haproxy/haproxy.cfg` to set the client and server timeout from `1m` to `5m`:

       ```bash
       timeout client           5m
       timeout server           5m
      ```

   - Running `systemctl restart haproxy` to restart the HAProxy load balancer.

If you are using a different load balancer, other than HAProxy, you might need to adjust timeout values in a similar fashion.
      {: note}

- Of the two types of Azure Machine Learning web services, only the `New` type is supported by {{site.data.keyword.aios_short}}. The `Classic` type is not supported.

<p>&nbsp;</p>


### Amazon SageMaker
{: #wos-common-issues-aws}

- __*BlazingText algorithm is not supported*__: The Amazon SageMaker BlazingText algorithm input payload format is not supported in the current release of {{site.data.keyword.aios_short}}.

<p>&nbsp;</p>


### Custom machine learning service instance
{: #wos-common-issues-custom}

- The [{{site.data.keyword.aios_short}} Python Client SDK](/docs/ai-openscale-icp?topic=ai-openscale-as-module) does not currently support explainability features for the custom engine. The custom serve engine requires a numerical prediction in the response data, which is not included with the module script.

<p>&nbsp;</p>


### Browser support
{: #abt-browser}

The {{site.data.keyword.aios_short}} service requires the same level of browser software as is required by {{site.data.keyword.cloud_notm}}. See the {{site.data.keyword.cloud_notm}} [Prerequisites](https://cloud.ibm.com/docs/overview?topic=overview-prereqs-platform#browsers-platform) topic for details.

<p>&nbsp;</p>



## Issues specific to {{site.data.keyword.aios_short}}
{: #cloud-issues}

The following limitations and known issues are specific to {{site.data.keyword.aios_short}} for {{site.data.keyword.Bluemix}}.

<p>&nbsp;</p>

### Limitations
{: #cloud-limitations}

- The current release supports one database, one {{site.data.keyword.pm_full}} instance, and one instance of {{site.data.keyword.aios_short}}. 

- The database and {{site.data.keyword.pm_full}} instance must be deployed in the same {{site.data.keyword.cloud_notm}} account.

- {{site.data.keyword.aios_short}} uses a PostgreSQL or Db2 database to store model-related data (feedback data, scoring payload) and calculated metrics. Lite Db2 plans are not currently supported.

- The free Lite plan database is not GDPR-compliant. If your model processes personally identifiable information (PII), you must purchase a new database or use an existing database that does conform to GDPR rules.

### Known issues
{: #cloud-known-unknowns-issues}

<p>&nbsp;</p>

#### Drift configuration is started but never finishes
{: #wos-common-issues-timeout}

Drift configuration is started but never finishes and continues to show the spinner icon. If you see the spinner run for more than 10 minutes, it is possible that the system is left in an inconsistent state. There is a workaround to this behavior: Edit the drift configuration. Then, save it. The system might come out of this state and complete configuration. If drift reconfiguration does not rectify the situation, contact IBM Support.



<p>&nbsp;</p>
## Next steps
{: #abt-next}

- [Getting started](/docs/ai-openscale?topic=ai-openscale-getting-started)
- View the [API Reference material](https://cloud.ibm.com/apidocs/ai-openscale){: external}.
- [What's new in {{site.data.keyword.aios_short}}](/docs/ai-openscale?topic=ai-openscale-rn-relnotes)
- [Contact IBM](https://www.ibm.com/account/reg/us-en/signup?formid=MAIL-watson){: external}.
