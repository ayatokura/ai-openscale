---

copyright:
  years: 2018, 2020
lastupdated: "2020-01-28"

keywords: risk, governance, model risk management, model risk governance

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

# Configure {{site.data.keyword.aios_short}} for model risk management ![beta tag](images/beta.png)
{: #mrm-risk-config-ovr-wos-only}

IBM offers a model risk management solution for financial services with IBM Watson OpenScale. IBM Watson OpenScale monitors and measures outcomes from AI Models across its lifecycle and performs model validations.
{: shortdesc}

## Setup options
{: #mrm-risk-config-ovr-wos-only-options}

You can use one of the following options to set up your initial environment:

- [Automated setup]()
  
  Takes just a few minutes to create a workable system with sample data on a publically hosted lite system

- [Notebook setup]()
  
  Enables you to control some of the setup parameters and can be used later for managing your own models

- [Manual setup]()
  
  Gives you the most control over resources and options

## Automated setup
{: #mrm-risk-config-ovr-wos-only-auto}

The auto setup option can be run when you launch the Watson OpenScale service for the very first time. After you choose auto setup, you must activate the model risk management features by clicking the Beta features button. The following section details how to run auto setup and activate the beta features on the IBM Cloud environment:

### Prerequisites
{: #mrm-risk-config-ovr-wos-only-auto-prereqs}

To work with IBM Watson OpenScale, you must already have an IBM Cloud instance and you must have provisioned an IBM Watson OpenScale instance.

### Steps
{: #mrm-risk-config-ovr-wos-only-auto-steps}

1. Launch Watson OpenScale.
   
   a. From the IBM Cloud Dashboard, click Services.
   b. Click Watson OpenScale
   c. Click the Launch Application button.

2. When prompted about running automatic setup, click the Auto setup button.
3. From the Insights dashboard, click the Beta features button.

## Set up your beta environment by using a Python notebook
{: #mrm-risk-config-ovr-wos-only-notebook}


### Prerequisites

Before you begin using the model risk management features, you’ll need to set up the following services on IBM Cloud:

-	Watson OpenScale, which provides MRM features and metrics 
-	Watson Machine Learning (2 separate instances, one for pre-prod and one for prod), which provides the engine for creating predictive models. This tutorial shows how to use Watson Machine Learning as model serving engine, but you can also use any other supported ML engine)
-	Watson Studio, which provides the ability to run notebooks and secure assets. (This tutorial shows how to use Watson Studio to create the provided sample models, but you can also use any other IDE to build models)
-	[Optional] Cloud Object Storage, which gives you a place to store model assets, such as training data. For the tutorial, you’ll use an internal database, however, you might want to set up Cloud Object Storage for your own work.
- In addition to the previously mentioned services, you must also have the following sample file: IBM_Cloud_MRM.ipynb. The file can be downloaded from the following Box folder: https://ibm.box.com/v/modelriskmanagement/

### Steps

#### Step 1: Create an IBMid and IBM Cloud account

In case you don't have an IBM Cloud account yet, you’ll need to start by creating one.

1. Point your web browser to the following URL: https://cloud.ibm.com/registration
2. Follow instructions to create an IBMid and IBM Cloud Account. 

#### Step 2: Add services to your IBM Cloud account

As soon as you have an IBM Cloud account, you can use the dashboard to add the required services. For each service, you can choose the Lite or Free plan. You must have instances for the following services: Watson OpenScale, Watson Studio, and Watson Machine Learning (2 Instances).

1. From the Navigation Menu (    ), click Resource list.
2. Click the Create resource button.
3. Search for each of the required services by entering keywords, such as openscale, studio, or machine learning.

You might not be able to add two Lite plan instances of Watson Machine Learning to your account. Either create the second instance using the Watson Machine Learning Standard plan or create a second IBM Cloud Account that is linked to a separate email address to create the second Watson Machine Machine Learning instance (Link to register the second account: https://cloud.ibm.com/registration).
{: note}

#### Step 3: Add a Cloud Object Storage instance  

Use Cloud Object Storage to store training data. After you create an instance Cloud Object Storage, Watson Studio, Watson Machine Learning, and Watson OpenScale will be able to access the buckets that are created as part of the model creation process.

1. Use your primary IBMid to log into your IBM Cloud account.
2. From the IBM Cloud Dashboard, click the Add resource button, then click Storage.
3. Click the Object Storage tile, select the Lite plan, then click the Create button.

### Work in Watson Studio

In IBM Watson Studio, you will create a project and run a notebook to perform most of the set-up tasks, including the following steps:

-	create 2 machine models
-	connect Watson OpenScale to IBM OpenPages
-	create model deployments and configure monitors in Watson OpenScale

#### Step 1: Create the pre-prod project in Watson Studio

When you first start Watson Studio (hint: use the IBM Cloud dashboard, find your instance of Watson Studio and click the Get Started button) you have the option of taking a tour. Your first task is to create a project to which you associate the Watson Machine Learning instance that you created for your pre-production work.

1. Click the Create a project tile.
2. Click the Create an empty project tile. 
3. Give the project a name and description: In the Name field, type MRM – Pre-prod. You’ll use this project for all your pre-production models. 
4. You’ll notice that an instance of Cloud Object Storage is required. Go ahead and create an instance of that on IBM Cloud if you haven’t already.
5. Click the Create button.

#### Step 2: Associate your new project with the Watson Machine Learning instance

Now you need to associate your pre-prod instance of Watson Machine Learning to your project. You’ll do this by adding it as an associated service.

1. From the MRM – Pre-prod project screen, click the Settings tab.
2. In the Associated services pane, click the Add service button, and then click Watson.
3. Find the Watson Machine Learning tile and click Add.
4. From the Machine Learning configuration window, click the Existing tab.
5. From the Existing Service Instance drop-down box, select the Machine Learning-Pre-Prod instance and click the Select button.

#### Step 3: Add the sample beta notebook to the project

As part of your closed beta information package, you were given access to a Watson Studio notebook. You’ll use it to set up your connection between Watson OpenScale and IBM OpenPages, to create and deploy pre-prod models, and configure the model deployments in Watson OpenScale. 

1. From the project page, click the Add to project button.
2. Click the Notebook tile.
3. Click the From file tab, click the Choose file button and then, select the IBM_Cloud_MRM.ipynb  notebook file that you can download from  https://ibm.box.com/v/modelriskmanagement/
4. Add a name and description and click the Create notebook button.

#### Step 4: Run the sample beta notebook

The newly created notebook is opened in Watson Studio in the integrated notebook editor. You need to update some of the credentials and then run the notebook to create your pre-prod model.

1. In the corresponding code box, paste your IBM Cloud API:
   
   a. From the IBM Cloud toolbar, click your Account name, such as <Your user name>’s Account.
   b. From the Manage menu, click Access (IAM).
   c. In the navigation bar, click IBM Cloud API keys.
   d. Click the Create an IBM Cloud API key button.
   e. Type a name and description and then click Save.
   f. Copy the newly created API key and paste it into your notebook in the CLOUD_API_KEY code box, which is the first code box.

2. In the corresponding code boxes, paste your credentials from the pre-prod and prod instances of Watson Machine Learning:
   
   a. Go to the IBM Cloud dashboard.
   b. In the Resource summary section, click Services.
   c. Click Machine Learning-Pre-Prod.
   d. In the navigation pane, click Service credentials.
   e. Click the New credential button.
   f. Copy your credentials by clicking the copy icon.
   g. Return to the notebook editor and update the credentials by replacing the sample credentials with your own in the second code box.
   h. Repeat the preceding steps for the prod instance in the third code box.
   
3. To restart the notebook and clear the output, from the Kernel menu, click Restart & Clear Output.
4. Run the notebook each cell at a time by using the Run option. Ensure that a cell completes before running the next cell. Be sure to read directions for steps that must be taken during the intervening cells. For example, at one point, you are directed to move your model into production before continuing running the notebook.

Congratulations! You have used a notebook to create a pre-prod model. You can check inside Watson Studio, where you will now see the model listed as one of the assets. You have also already deployed this model, which means that you can go to IBM Watson OpenScale to add the model there.  

### Work in IBM Watson OpenScale

You’ll use IBM Watson OpenScale to validate and monitor your models and to process metrics and KPIs. First, you need to do some set up.

#### Step 1: Activate model risk management features

As part of the closed beta cohort, you can activate the model risk management beta features on IBM Watson OpenScale. The following sections detail how to activate the beta features on IBM Cloud:

To work with IBM Watson OpenScale, you must already have an IBM Cloud instance and you must have provisioned an IBM Watson OpenScale instance.

1. Launch Watson OpenScale.
   
   a. From the IBM Cloud Dashboard, click Services.
   b. Click Watson OpenScale
   c. Click the Launch Application button.

2. When prompted about running automatic setup, click the No thanks button.
3. From the Insights dashboard, click the Beta features button.

## Manual setup






## Next steps
{: #mrm-risk-config-ovr-wos-only-next}

Use the analysis of fairness to redefine the model, possibly by using a different algorithm. 
Watson OpenScale enables you to compare models by looking at the key metrics in a side-by-side comparison. Use this feature to determine which version of a model is the best one to send to production or which model might need work:

