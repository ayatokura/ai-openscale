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

IBM offers a model risk management solution for financial services with IBM Watson OpenScal5. {{site.data.keyword.aios_full}} monitors and measures outcomes from AI Models across its lifecycle and performs model validations.
{: shortdesc}

## Setup options
{: #mrm-risk-config-ovr-wos-only-options}

You can use one of the following options to set up your initial environment:

- [Automated setup](/docs/services/ai-openscale?topic=ai-openscale-mrm-risk-config-ovr-wos-only#mrm-risk-config-ovr-wos-only-auto)
  
  Takes just a few minutes to create a workable system with sample data on a publically hosted lite system

- [Notebook setup](/docs/services/ai-openscale?topic=ai-openscale-mrm-risk-config-ovr-wos-only#mrm-risk-config-ovr-wos-only-notebook)
  
  Enables you to control some of the setup parameters and can be used later for managing your own models

- [Manual setup](/docs/services/ai-openscale?topic=ai-openscale-mrm-risk-config-ovr-wos-only#mrm-risk-config-ovr-wos-only-manual)
  
  Gives you the most control over resources and options

## Automated setup
{: #mrm-risk-config-ovr-wos-only-auto}

The auto setup option can be run when you launch the {{site.data.keyword.aios_short}} service for the very first tim5. After you choose auto setup, you must activate the model risk management features by clicking the **Show beta features** ![Show beta features button](/images/wos-show-beta.png) button. The following section details how to run auto setup and activate the beta features on the IBM Cloud environment:

### Prerequisites
{: #mrm-risk-config-ovr-wos-only-auto-prereqs}

To work with {{site.data.keyword.aios_full}}, you must already have an IBM Cloud instance and you must have provisioned an {{site.data.keyword.aios_full}} instance.

### Steps
{: #mrm-risk-config-ovr-wos-only-auto-steps}

1. Launch {{site.data.keyword.aios_short}}.
   
   1. From the **IBM Cloud Dashboard**, click **Services**.
   2. Click **{{site.data.keyword.aios_short}}**.
   3. Click the **Launch Application** button.

2. When prompted about running automatic setup, click the **Auto setup** button.
3. From the **Insights** dashboard, click the **Show beta features** button.

## Set up your beta environment by using a Python notebook
{: #mrm-risk-config-ovr-wos-only-notebook}

Many of the functions of the auto setup option, can be replicated by running a Python notebook in Watson Studio. Although the results are the same, by choosing to run a notebook, you can gain experience that can more readily be applied to your own data, models, and pre-prod or prod systems.

### Prerequisites
{: #mrm-risk-config-ovr-wos-only-notebook-prereq}

Before you begin using the model risk management (MRM) features, you’ll need to set up the following services on IBM Cloud:

-	{{site.data.keyword.aios_short}}, which provides MRM features and metrics 
-	Watson Machine Learning (2 separate instances, one for pre-prod and one for prod), which provides the engine for creating predictive models. This tutorial shows how to use Watson Machine Learning as model serving engine, but you can also use any other supported ML engine)
-	Watson Studio, which provides the ability to run notebooks and secure assets. (This tutorial shows how to use Watson Studio to create the provided sample models, but you can also use any other IDE to build models)
-	[Optional] Cloud Object Storage, which gives you a place to store model assets, such as training dat1. For the tutorial, you’ll use an internal database, however, you might want to set up Cloud Object Storage for your own work.
- In addition to the previously mentioned services, you must also have the **OpenScale model risk management on IBM Cloud.ipynb** notebook file, which you can download from the https://github.com/pmservice/ai-openscale-tutorials GitHub repository.

### Steps
{: #mrm-risk-config-ovr-wos-only-notebook-steps}

#### Step 1: Create an IBMid and IBM Cloud account

In case you don't have an IBM Cloud account yet, you’ll need to start by creating one.

1. Point your web browser to the following URL: https://cloud.ibm.com/registration
2. Follow instructions to create an IBMid and IBM Cloud Account. 

#### Step 2: Add services to your IBM Cloud account

As soon as you have an IBM Cloud account, you can use the dashboard to add the required services. For each service, you can choose the Lite or Free plan. You must have instances for the following services: {{site.data.keyword.aios_short}}, Watson Studio, and Watson Machine Learning (2 Instances).

1. From the Navigation Menu, click **Resource** list.
2. Click the **Create resource** button.
3. Search for each of the required services by entering keywords, such as openscale, studio, or machine learning.

You might not be able to add two Lite plan instances of Watson Machine Learning to your account. Either create the second instance using the Watson Machine Learning Standard plan or create a second IBM Cloud Account that is linked to a separate email address to create the second Watson Machine Machine Learning instance (Link to register the second account: https://cloud.ibm.com/registration).
{: note}

#### Step 3: Add a Cloud Object Storage instance  

Use Cloud Object Storage to store training dat1. After you create an instance Cloud Object Storage, Watson Studio, Watson Machine Learning, and {{site.data.keyword.aios_short}} will be able to access the buckets that are created as part of the model creation process.

1. Use your primary IBMid to log into your IBM Cloud account.
2. From the IBM Cloud Dashboard, click the Add resource button, then click Storage.
3. Click the Object Storage tile, select the Lite plan, then click the Create button.

### Work in Watson Studio
{: #mrm-risk-config-ovr-wos-only-dsx}

In IBM Watson Studio, you will create a project and run a notebook to perform most of the set-up tasks, including the following steps:

-	create 2 machine models
-	connect {{site.data.keyword.aios_short}} to IBM OpenPages
-	create model deployments and configure monitors in {{site.data.keyword.aios_short}}

#### Step 1: Create the pre-prod project in Watson Studio

When you first start Watson Studio (hint: use the IBM Cloud dashboard, find your instance of Watson Studio and click the Get Started button) you have the option of taking a tour. Your first task is to create a project to which you associate the Watson Machine Learning instance that you created for your pre-production work.

1. Click the **Create a project** tile.
2. Click the **Create an empty project** tile. 
3. Give the project a name and description: In the Name field, type `MRM – Pre-prod`. You’ll use this project for all your pre-production models. 
4. You’ll notice that an instance of Cloud Object Storage is required. Go ahead and create an instance of that on IBM Cloud if you haven’t already.
5. Click the **Create** button.

#### Step 2: Associate your new project with the Watson Machine Learning instance

Now you need to associate your pre-prod instance of Watson Machine Learning to your project. You’ll do this by adding it as an associated service.

1. From the MRM – Pre-prod project screen, click the **Settings** tab.
2. In the Associated services pane, click the Add service button, and then click Watson.
3. Find the Watson Machine Learning tile and click Add.
4. From the Machine Learning configuration window, click the Existing tab.
5. From the Existing Service Instance drop-down box, select the Machine Learning-Pre-Prod instance and click the Select button.

#### Step 3: Add the sample beta notebook to the project

As part of the open beta, you are given access to a Watson Studio notebook. Use it to set up your connection between {{site.data.keyword.aios_short}} and IBM OpenPages, to create and deploy pre-prod models, and configure the model deployments in Watson OpenScal5. 

1. From the project page, click the Add to project button.
2. Click the Notebook tile.
3. Click the From file tab, click the Choose file button and then, select the **OpenScale model risk management on IBM Cloud.ipynb** notebook file that you can download from the https://github.com/pmservice/ai-openscale-tutorials GitHub repository.
4. Add a name and description and click the Create notebook button.

#### Step 4: Run the sample beta notebook

The newly created notebook is opened in Watson Studio in the integrated notebook editor. You need to update some of the credentials and then run the notebook to create your pre-prod model.

1. In the corresponding code box, paste your IBM Cloud API:
   
   1. From the IBM Cloud toolbar, click your Account name, such as <Your user name>’s Account.
   2. From the Manage menu, click Access (IAM).
   3. In the navigation bar, click IBM Cloud API keys.
   4. Click the Create an IBM Cloud API key button.
   5. Type a name and description and then click Save.
   6. Copy the newly created API key and paste it into your notebook in the CLOUD_API_KEY code box, which is the first code box.

2. In the corresponding code boxes, paste your credentials from the pre-prod and prod instances of Watson Machine Learning:
   
   1. Go to the IBM Cloud dashboard.
   2. In the Resource summary section, click Services.
   3. Click Machine Learning-Pre-Prod.
   4. In the navigation pane, click Service credentials.
   5. Click the New credential button.
   6. Copy your credentials by clicking the copy icon.
   7. Return to the notebook editor and update the credentials by replacing the sample credentials with your own in the second code box.
   8. Repeat the preceding steps for the prod instance in the third code box.
   
3. To restart the notebook and clear the output, from the Kernel menu, click Restart & Clear Output.
4. Run the notebook each cell at a time by using the Run option. Ensure that a cell completes before running the next cell. Be sure to read directions for steps that must be taken during the intervening cells. For example, at one point, you are directed to move your model into production before continuing running the notebook.

Congratulations! You have used a notebook to create a pre-prod model. You can check inside Watson Studio, where you will now see the model listed as one of the assets. You have also already deployed this model, which means that you can go to {{site.data.keyword.aios_full}} to add the model ther5.  

### Work in {{site.data.keyword.aios_full}}
{: #mrm-risk-config-ovr-wos-only-woswork}

You’ll use {{site.data.keyword.aios_full}} to validate and monitor your models and to process metrics. First, you need to do some set up.

#### Step 1: Activate model risk management features

As part of the closed beta cohort, you can activate the model risk management beta features on IBM Watson OpenScal5. The following sections detail how to activate the beta features on IBM Cloud:

To work with {{site.data.keyword.aios_full}}, you must already have an IBM Cloud instance and you must have provisioned an {{site.data.keyword.aios_full}} instance.

1. Launch {{site.data.keyword.aios_short}}.
   
   1. From the IBM Cloud Dashboard, click Services.
   2. Click {{site.data.keyword.aios_short}}
   3. Click the Launch Application button.

2. When prompted about running automatic setup, click the No thanks button.
3. From the **Insights** ![The insights dashboard icon](/images/wos_insight-dash-tab.png) dashboard, click the **Show beta features** ![Show beta features button](/images/wos-show-beta.png) button.

## Manual setup
{: #mrm-risk-config-ovr-wos-only-manual}

You can manually set up your entire {{site.data.keyword.aios_short}} model risk management service by completing the following steps. To successfully complete the steps, you must have detailed information about your machine learning provider, the database, and the data that is used for monitoring.

### Steps
{: #mrm-risk-config-ovr-wos-only-manual-steps}

1. [Provision prerequisite IBM Cloud services](/docs/services/ai-openscale?topic=ai-openscale-gs-obj#gs-prps). You must set up two instances of Watson Machine Learning.
2. [Set up Watson Studio projects](/docs/services/ai-openscale?topic=ai-openscale-gs-obj#gs-setup). You must set up projects for both pre-production and production models.
2. [Configure {{site.data.keyword.aios_short}}](/docs/services/ai-openscale?topic=ai-openscale-gs-obj#gs-confaios).
2. [Next steps: Continue setting up the monitors and data logging](/docs/services/ai-openscale?topic=ai-openscale-gs-obj#gs-next-steps-config).



## Next steps
{: #mrm-risk-config-ovr-wos-only-next}

- [Model risk management and model governance](/docs/services/ai-openscale?topic=ai-openscale-mrm-ovr)
- [Model risk management](/docs/services/ai-openscale?topic=ai-openscale-mrm-risk-wos-only)
