---

copyright:
  years: 2018, 2020
lastupdated: "2020-08-08"

keywords: drift, anomalies, data, data drift, drift detection, transactions, constraints

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

# Drift in data
{: #behavior-anomalies}

In addition to checking for the drift in model accuracy, the drift monitor can detect the drift in data. This type of drift is defined as something that deviates from what is standard, normal, or expected. {{site.data.keyword.aios_short}} detects data drift so that you can make changes to the model.
{: shortdesc}

## Understanding drift detection
{: #behavior-anomalies-understand}

Drift is the degradation of predictive performance over time because of hidden context. As your data changes over time, the ability of your model to make accurate predictions may deteriorate. {{site.data.keyword.aios_short}} both detects and highlights drift so that you can take corrective action.

### How it works
{: #behavior-anomalies-works}

{{site.data.keyword.aios_short}} analyzes all transactions to find the ones that contribute to drift. It then groups the records based on the similarity of data inconsistency patterns that were significant in contributing to drift.

### Data drift constraint specification 
{: #behavior-anomalies-constraints}

The constraints schema describes the statistics of training data as a set of single column and two column data boundaries. These statistics identify input data outliers to a machine learning model at runtime. Single-column constraints deal with each column individually while two-column constraints assume a relationship might exist between any two columns in the training data.

#### Constraints JSON Object
{: #behavior-anomalies-constraints-json}

The constraints schema itself is specified as a JSON object with two array fields that describe all the columns and the constraints in the training data. The JSON object takes the following format:

```
{
      columns: [],
      constraints: []
}
```

#### Column statistics
{: #behavior-anomalies-constraints-col-stat}

Each element in the `columns` describes the standard statistical properties of a column.

The data type of the column is indicated by the `dtype` variable. Allowed values of `dtype` variable are one of the following items: 

- `categorical`
- `numeric_discrete`
- `numeric_continuous`

A numeric column is described with its standard numerical bounds, such as minimum, maximum, mean, standard deviation, and its first, second and third quartile percentile values. 

#### Common attributes of all constraints:
{: #behavior-anomalies-constraints-com-att}

The `name` field identifies the concrete type of a constraint. The value of the `name` can be one of the following items:

- `categorical_distribution_constraint`
- `numeric_range_constraint`
- `numeric_distribution_constraint`
- `catnum_range_constraint`
- `catnum_distribution_constraint`
- `catcat_distribution_constraint`

The `id` field is an internal field to identify each constraint uniquely. Its value is a UUID.

The `kind` field identifies if the constraint is a single or two column constraint. Allowed values are one of `single_column`, `two_column`

The `columns` field is an array of column names. If the constraint deals with a single column, array contains a single element whose value is the name of the column. If the constraint deals with two columns, array contains the names of the two columns.





### Single-feature constraints
{: #behavior-anomalies-sing-feat}

Single-feature constraints, also know as single-column constraints, cannot be generated in the following instances:

- The contents of `categorical_distribution_constraint` has a `frequency_distribution` attribute which has the frequency counts of each categorical value of the specified category. If a numeric column can be fitted in a distribution and it is not discrete or sparse, {{site.data.keyword.aios_short}} generates both range and distribution constraint.
- The contents of `numeric_range_constraint` has a `ranges` attribute which has the high density regions of the numeric column. Any numeric ranges which rarely occur in training data are not included. If a numeric column is sparse or discrete {{site.data.keyword.aios_short}} generates the frequency distribution constraint , but not regular distribution and range.
- The contents of `numeric_distribution_constraint` has a `distribution` attribute which indicates if the specified numeric value follows a uniform, beta, exponential or normal distribution. The allowed values of the `name` of the distribution are one of `beta`, `uniform`, `expon` or `norm`.The `distribution.parameters` has all the parameters of the corresponding distribution. Refer to the documentation of scipy.stats.beta, scipy.stats.uniform, scipy.stats.expon, scipy.stats.norm for the details ofeach parameter. If a numeric column data cannot be fitted into a distribution - depending on p-value computed , {{site.data.keyword.aios_short}} computes only the range constraint.


### Double-feature constraints
{: #behavior-anomalies-dbl-feat}


Double-feature constraints, also known as two-column constraints, cannot be generated in the following instances:

- The contents of `catnum_range_constraint` has the source categorical column specified as `source_column` and the target numeric column specified as `target_column`. The `ranges` attribute contains the range of numeric values that can occur for a given value of categorical column. All such categories are dropped which very rarely occur. The numeric range only includes minimum, maximum values and the number of rows in training data with the corresponding categorical value.
- The contents of `catnum_distribution_constraint` has the source categorical column specified as `source_column` and the target numeric column specified as `target_column`. The `distribution` attribute contains the distribution of numeric values for a given value of categorical column. Refer to the `numeric_distribution_constraint` above for more details on the distribution parameters.
- The contents of `catcat_distribution_constraint` has the source categorical column specified as `source_column` and the target categorical column specified as `target_column`. The `rare_combinations` attribute contains all such pairs of source and target column values which rarely occur together in training data.


### Working with large datasets
{: #behavior-anomalies-large-datasets}

For data drift to be calculated successfully, very large datasets that consist of more than one-thousand columns (1,012) must be broken up. You must split the dataset into multiple datasets, each with a subset of columns, and the generate constraints. 

For datasets, which have a large number of columns, that use one hot encoding, it is suggested that you write a wrapper on top of the model and provide {{site.data.keyword.aios_short}} a REST API of the scoring end point. In this way, {{site.data.keyword.aios_short}} can accept non one hot encoded data during training time and also while adding payload data. 

For more information about the limits, see [Limit on the number of features for a model](/docs/ai-openscale?topic=ai-openscale-rn-12ki#wos-limitations-feat-col-size-limit)

### Do the math
{: #behavior-anomalies-math}


{{site.data.keyword.aios_short}} analyzes each transaction for data inconsistency, by comparing the transaction content with the training data patterns. If a transaction violates one or more of the training data patterns, the transaction is marked as drifted. {{site.data.keyword.aios_short}} then estimates the magnitude of data inconsistency as the fraction of drifted transactions to the total number of transactions analyzed. Further, {{site.data.keyword.aios_short}} analyzes all the drifted transactions; and then, groups transactions that violate similar training data patterns into different clusters. In each cluster, {{site.data.keyword.aios_short}} also estimates the important features that played a major role in the data inconsistency and classifies their feature impact as large, some, and small.

## Next steps
{: #behavior-anomalies-ns}

- For information on how to set up drift detection, see [Configuring the drift detection monitor](/docs/ai-openscale?topic=ai-openscale-behavior-drift-config).
- To mitigate drift, after it has been detected by {{site.data.keyword.aios_short}}, you must build a new version of the model that fixes the problem. A good place to start is with the data points that are highlighted as reasons for the drift. Introduce the new data to the predictive model after you have manually labeled the drifted transactions and use them to re-train the model.
