---

copyright:
  years: 2018, 2020
lastupdated: "2020-08-08"

keywords: deployment, monitors, data

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

# Prepare models for monitoring
{: #mo-config}

Set up and enable monitors for each deployment that you are tracking with {{site.data.keyword.aios_short}}.
{: shortdesc}

For example, if you are using the **German Credit Risk** sample model for the interactive tutorial, select the model deployment, set the data type for payload logging, and confirm the settings that are presented as part of the model details section.

<p>&nbsp;</p>

## Selecting a deployment
{: #mo-select-deploy}

1. From the **Insights dashboard**, on the **Model monitor** tab, click the **Add to dashboard** button. 

   A list of available model deployments appears. If you don't see any model deployments, you must deploy a model using your machine learning provider. For the tutorial, select the **German Credit Risk model**.

   ![The select a model deployment screen is shown. It has selections for a machine learning provider and a deployment.](images/wos-select-model-deployment.png)

2. Click a model deployment and then click **Configure**.

   After your selections are saved, you are ready to configure monitors, which include payload logging, accuracy, and fairness. 

2. To get started, click **Configure monitors**.

<p>&nbsp;</p>

## Provide model details
{: #mo-work-model-dets}

Provide information about your model so that {{site.data.keyword.aios_short}} can access the database and understand how the model is set up. 

Specifically to configure monitors, you must provide the following information:

### Model input
{: #mo-work-model-dets-input}

Select the data type and algorithm type.

### Training data
{: #mo-work-model-dets-training-data}

If you do not use a notebook to provide a training data summary, you must enter the location of the training data. Specify the exact location in the Db2 database or Cloud Object Storage where the training data is located. After you select the storage type (either `Db2` or `Cloud Object Storage`), you must complete the following information:

- For a Db2 database, enter the following information:
  
  - Host name or IP address, excluding the initial `https://` prefix and the final forward slash (/)
  - Port
  - Database (name)
  - Username
  - Password
  
- For Cloud Object Storage, enter the following information:
  
  - Login URL: The Login URL must match the region setting of the bucket where your training data is located. You will specify the training data bucket in the next step.
  - Resource instance (ID)
  - API key

To ensure a valid connection, click the **Connect** button to connect to the training data. After you successfully connect, you must make additional selections and save your work:

- For a Db2 database, select both a schema and a training table that includes columns expected by your model.
- For Cloud Object Storage, select a Bucket and a Data Set.

### Model transaction
{: #mo-work-model-dets-mtrxn}

{{site.data.keyword.aios_short}} checks the payload logging automatically for models that you create with {{site.data.keyword.pm_full}}. For external machine learning providers, you must send a sample payload either by pasting a JSON file into the JSON payload box or by using the API to send a request.

### Training data label
{: #mo-work-model-dets-training-data-label}

You must select a single unique feature from the data to serve as the label column. This is what the model was designed to predict.

### Training features
{: #mo-work-model-dets-training-data-features}

Select all the features that were used to train the model before it was deployed.



### Model output details
{: #mo-work-model-dets-output-dets}

Select model output details and save your work. Specifically, you must select a prediction column and a prediction probability column. {{site.data.keyword.aios_short}} might detect these values for you.

<p>&nbsp;</p>

## Continuing the interactive tutorial
{: #mo-work-model-dets-int-tut}

If you use the Lite plan option, the Db2 configuration information is provided within the sample model metadata. Optionally, if you want to use your own Db2 or Cloud Object Storage, you can continue with the following section, which shows how to set up the Cloud Object Storage instance that you created previously. 

You must enter the location of the training data. Training data must be stored in a Db2 database or Cloud Object Storage. Enter your connection information, then click **Test** to verify the connection. You do this by entering the location, hostname or IP address, the database name, and the authentication information from {{site.data.keyword.Bluemix_notm}}.

### Location of training data (tutorial example)
{: #mo-work-model-dets-int-tut-train}

For the interactive tutorial, use the Cloud Object Storage instance that you created and load the following [training data german_credit_data_biased_training.csv file](https://raw.githubusercontent.com/pmservice/ai-openscale-tutorials/master/assets/historical_data/german_credit_risk/wml/german_credit_data_biased_training.csv) into a bucket that you create. 

You'll need the following information, which you can obtain by clicking the Cloud Object Storage instance from the {{site.data.keyword.Bluemix_notm}} dashboard:

- **Login URL**: This is the Service Endpoint. From the Navigation pane click **Endpoint**. Copy the `us-geo` public service endpoint and paste it into the Login URL box. Be sure to include the HTTPS:// at the beginning of your URL.  

For the following two items, from the Navigation pane, click **Service credentials** and then click the **New Credential** button. Retrieve the following two values from the JSON service credentails you just created:

- **Resource Instance ID**: From the `resource_instance_id` field.
- **API Key**: From the `apikey` field.

  One of the automatic service credentials does not have enough access to support your training data. You must create your own service credentials to establish access.
  {: note}

### The training bucket and file (tutorial example)
{: #mo-work-model-dets-int-tut-bucket}

- From the drop-down boxes, select the bucket that you created and the `german_credit_data_biased_training.csv` file that you uploaded there.

### Information about the training data and model (tutorial example)
{: #mo-work-model-dets-int-tut-mods}

- The label column from the training table: For example, for the tutorial, click the **Risk** tile.
- The features that were used to train the AI deployment: For example, for the tutorial,select all features.
- The text and categorical features: For example, for the tutorial, click CheckingStatus, CreditHistory, EmploymentDuration, ExistingSavings, ForeignWorker, Housing, InstallmentPlans, Job, LoanPurpose, OthersOnLoan, OwnsProperty, Sex, and Telephone.
- The deployment prediction column: For example, for the tutorial, click the **predictedLabel** tile.


When you finish providing all the required information, a summary of your selections is presented for review. If you want to change anything, click the **Edit** icon for that section, otherwise, save your work.

The following sections give some specific information that you encounter depending on the type of model, either [Numeric/categorical data](#mo-nuca) or [Images and Unstructured text](#mo-imun).


<p>&nbsp;</p>

## Numeric/categorical data
{: #mo-nuca}

For numeric or categorical data, you need to provide information about the training data for your model, in order to configure the monitors.

- **Manually configure monitors** - Requires you to provide connection information to your training data. 

  The format of the training data must match the model. For example, if the model expects `M` and `F` for the feature `Gender`, then the training data should have `M` and `F`, not `Male` and `Female`.  The current release of {{site.data.keyword.aios_short}} supports either Db2 or Cloud Object Storage locations.

  - Specify the Location (either `Db2` or `Cloud Object Storage`), then:
      - For a Db2 database, enter the following information:
          - Host name or IP address
          - Port
          - Database (name)
          - Username
          - Password
      - For Cloud Object Storage, enter the following information:
          - Login URL: The Login URL must match the region setting of the bucket where your training data is located. You will specify the training data bucket in the next step.
          - Resource instance (ID)
          - API key
  - To ensure a valid connection, click the **Test** button to connect to the trainingdata.
  - Specify the exact location in the Db2 database or Cloud Object Storage where thetraining data is located.
      - For a Db2 database, select both a schema and a training table that includes columns expected by your model.
      - For Cloud Object Storage, select a Bucket and a Data Set.

- **Upload a training data distribution file** - Choose this option if you prefer to keep your training data private. You can use a custom Python notebook to provide {{site.data.keyword.aios_short}} with information to analyze your training data without providing access to the training data itself.

  Running the Python notebook lets you capture distinct values in the schema columns, as well as the column names. In addition, you can use the notebook to pre-configure the Fairness monitor.

   - Download the [custom notebook](https://github.com/IBM-Watson/aios-data-distribution/blob/master/training_statistics_notebook.ipynb){: external}, and replace any credentials with your own credentials.
   - Review the notebook carefully, specifying data for your model where appropriate. Save the notebook.
   - Run the notebook to generate a JSON-formatted configuration file.
   - Upload the JSON configuration file.

     ![Upload config JSON](images/wos-config-json-monitor.png)

- {{site.data.keyword.aios_short}} locates your training data from the metadata stored with the model in {{site.data.keyword.pm_full}}. 
- Select the columns used to train the model - these are the features that your model deployment expects in a request. Do not select the label column.
- You can choose either a string column or a numeric column as the prediction column.

<p>&nbsp;</p>

## Images and Unstructured text
{: #mo-imun}

- **Images**

  For models that accept images as input, the image needs to be represented as a (height) x (width) x (# channels) format, where each point represents either monochrome or RGB values for each pixel.

- **Unstructured text**

   For models that accept text as input, it is expected that the model accepts the entire text, and not a vectorized representation of the text.

Fairness and drift metrics are not supported for unstructured (image or text) data types.
{: note}

<p>&nbsp;</p>

## Review and save configuration
{: #mo-save}

Save your work and review your selection summary to continue.

  ![Select data table](images/wos-config-summary-monitor.png)

## Next steps
{: #mo-next}

To continue configuring monitors, click the **Quality** tab and click the **Edit** icon. For more information, see [Configuring the Quality monitor](/docs/ai-openscale?topic=ai-openscale-acc-monitor).

[See the sample payload files](https://github.com/pmservice/ai-openscale-tutorials/tree/master/assets/historical_data/german_credit_risk/wos){: external}.
