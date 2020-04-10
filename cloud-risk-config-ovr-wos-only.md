---

copyright:
  years: 2018, 2020
lastupdated: "2020-04-08"

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
{:note: .note}
{:note: .note}
{:note: .note}
{:note: .note}
{:faq: data-hd-content-type='faq'}

# Configure {{site.data.keyword.aios_short}} for model risk management
{: #mrm-risk-config-ovr-wos-only}

IBM offers a model risk management solution for financial services with IBM Watson OpenScale. {{site.data.keyword.aios_full}} monitors and measures outcomes from AI Models across its lifecycle and performs model validations.
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

The auto setup option can be run when you launch the {{site.data.keyword.aios_short}} service for the very first tim5. 

### Prerequisites
{: #mrm-risk-config-ovr-wos-only-auto-prereqs}

To work with {{site.data.keyword.aios_full}}, you must already have an {{site.data.keyword.Bluemix_notm}} instance and you must have provisioned an {{site.data.keyword.aios_full}} instance.

### Steps
{: #mrm-risk-config-ovr-wos-only-auto-steps}

1. Launch {{site.data.keyword.aios_short}}.
   
   1. From the **{{site.data.keyword.Bluemix_notm}} Dashboard**, click **Services**.
   2. Click **{{site.data.keyword.aios_short}}**.
   3. Click the **Launch Application** button.

2. When prompted about running automatic setup, click the **Auto setup** button.

## Set up your environment by using a Python notebook
{: #mrm-risk-config-ovr-wos-only-notebook}

Many of the functions of the auto setup option, can be replicated by running a Python notebook in {{site.data.keyword.DSX}}. Although the results are the same, by choosing to run a notebook, you can gain experience that can more readily be applied to your own data, models, and pre-prod or prod systems.

### Prerequisites
{: #mrm-risk-config-ovr-wos-only-notebook-prereq}

Before you begin using the model risk management (MRM) features, you’ll need to set up the following services on {{site.data.keyword.Bluemix_notm}}:

-	{{site.data.keyword.aios_short}}, which provides MRM features and metrics 
-	{{site.data.keyword.pm_full}} (2 separate instances, one for pre-prod and one for prod), which provides the engine for creating predictive models. This tutorial shows how to use {{site.data.keyword.pm_full}} as model serving engine, but you can also use any other supported ML engine)
-	{{site.data.keyword.DSX}}, which provides the ability to run notebooks and secure assets. (This tutorial shows how to use {{site.data.keyword.DSX}} to create the provided sample models, but you can also use any other IDE to build models)
-	[Optional] Cloud Object Storage, which gives you a place to store model assets, such as training dat1. For the tutorial, you’ll use an internal database, however, you might want to set up Cloud Object Storage for your own work.
- In addition to the previously mentioned services, you must also have the **OpenScale model risk management on {{site.data.keyword.Bluemix_notm}}.ipynb** notebook file, which you can download from the https://github.com/pmservice/ai-openscale-tutorials GitHub repository.

### Steps
{: #mrm-risk-config-ovr-wos-only-notebook-steps}

#### Step 1: Create an IBMid and {{site.data.keyword.Bluemix_notm}} account

In case you don't have an {{site.data.keyword.Bluemix_notm}} account yet, you’ll need to start by creating one.

1. Point your web browser to the following URL: https://cloud.ibm.com/registration
2. Follow instructions to create an IBMid and {{site.data.keyword.Bluemix_notm}} Account. 

#### Step 2: Add services to your {{site.data.keyword.Bluemix_notm}} account

As soon as you have an {{site.data.keyword.Bluemix_notm}} account, you can use the dashboard to add the required services. For each service, you can choose the Lite or Free plan. You must have instances for the following services: {{site.data.keyword.aios_short}}, {{site.data.keyword.DSX}}, and {{site.data.keyword.pm_full}} (2 Instances).

1. From the Navigation Menu, click **Resource** list.
2. Click the **Create resource** button.
3. Search for each of the required services by entering keywords, such as openscale, studio, or machine learning.

You might not be able to add two Lite plan instances of {{site.data.keyword.pm_full}} to your account. Either create the second instance using the {{site.data.keyword.pm_full}} Standard plan or create a second {{site.data.keyword.Bluemix_notm}} Account that is linked to a separate email address to create the second Watson Machine Machine Learning instance (Link to register the second account: https://cloud.ibm.com/registration).
{: note}

#### Step 3: Add a Cloud Object Storage instance  

Use Cloud Object Storage to store training dat1. After you create an instance Cloud Object Storage, {{site.data.keyword.DSX}}, {{site.data.keyword.pm_full}}, and {{site.data.keyword.aios_short}} will be able to access the buckets that are created as part of the model creation process.

1. Use your primary IBMid to log into your {{site.data.keyword.Bluemix_notm}} account.
2. From the {{site.data.keyword.Bluemix_notm}} Dashboard, click the Add resource button, then click Storage.
3. Click the Object Storage tile, select the Lite plan, then click the Create button.

### Work in {{site.data.keyword.DSX}}
{: #mrm-risk-config-ovr-wos-only-dsx}

In IBM {{site.data.keyword.DSX}}, you will create a project and run a notebook to perform most of the set-up tasks, including the following steps:

-	create 2 machine models
-	connect {{site.data.keyword.aios_short}} to IBM OpenPages
-	create model deployments and configure monitors in {{site.data.keyword.aios_short}}

#### Step 1: Create the pre-prod project in {{site.data.keyword.DSX}}

When you first start {{site.data.keyword.DSX}} (hint: use the {{site.data.keyword.Bluemix_notm}} dashboard, find your instance of {{site.data.keyword.DSX}} and click the Get Started button) you have the option of taking a tour. Your first task is to create a project to which you associate the {{site.data.keyword.pm_full}} instance that you created for your pre-production work.

1. Click the **Create a project** tile.
2. Click the **Create an empty project** tile. 
3. Give the project a name and description: In the Name field, type `MRM – Pre-prod`. You’ll use this project for all your pre-production models. 
4. You’ll notice that an instance of Cloud Object Storage is required. Go ahead and create an instance of that on {{site.data.keyword.Bluemix_notm}} if you haven’t already.
5. Click the **Create** button.

#### Step 2: Associate your new project with the {{site.data.keyword.pm_full}} instance

Now you need to associate your pre-prod instance of Watson Machine Learning to your project. You’ll do this by adding it as an associated service.

1. From the MRM – Pre-prod project screen, click the **Settings** tab.
2. In the Associated services pane, click the Add service button, and then click Watson.
3. Find the {{site.data.keyword.pm_full}} option and click Add.
4. From the Machine Learning configuration window, click the Existing tab.
5. From the Existing Service Instance drop-down box, select the Machine Learning-Pre-Prod instance and click the Select button.

#### Step 3: Add the sample notebook to the project

As part of this tutorial, you are given access to a {{site.data.keyword.DSX}} notebook. Use it to set up your connection between {{site.data.keyword.aios_short}} and IBM OpenPages, to create and deploy pre-prod models, and configure the model deployments in {{site.data.keyword.aios_short}}. 

1. From the project page, click the Add to project button.
2. Click the Notebook tile.
3. Click the From file tab, click the Choose file button and then, select the **OpenScale model risk management on {{site.data.keyword.Bluemix_notm}}.ipynb** notebook file that you can download from the https://github.com/pmservice/ai-openscale-tutorials GitHub repository.
4. Add a name and description and click the Create notebook button.

#### Step 4: Run the sample notebook

The newly created notebook is opened in {{site.data.keyword.DSX}} in the integrated notebook editor. You need to update some of the credentials and then run the notebook to create your pre-prod model.

1. In the corresponding code box, paste your {{site.data.keyword.Bluemix_notm}} API key:
   
   1. From the {{site.data.keyword.Bluemix_notm}} toolbar, click your Account name, such as <Your user name>’s Account.
   2. From the Manage menu, click Access (IAM).
   3. In the navigation bar, click {{site.data.keyword.Bluemix_notm}} API keys.
   4. Click the Create an {{site.data.keyword.Bluemix_notm}} API key button.
   5. Type a name and description and then click Save.
   6. Copy the newly created API key and paste it into your notebook in the CLOUD_API_KEY code box, which is the first code box.

2. In the corresponding code boxes, paste your credentials from the pre-prod and prod instances of {{site.data.keyword.pm_full}}:
   
   1. Go to the {{site.data.keyword.Bluemix_notm}} dashboard.
   2. In the Resource summary section, click Services.
   3. Click Machine Learning-Pre-Prod.
   4. In the navigation pane, click Service credentials.
   5. Click the New credential button.
   6. Copy your credentials by clicking the copy icon.
   7. Return to the notebook editor and update the credentials by replacing the sample credentials with your own in the second code box.
   8. Repeat the preceding steps for the prod instance in the third code box.
   
3. To restart the notebook and clear the output, from the Kernel menu, click Restart & Clear Output.
4. Run the notebook each cell at a time by using the Run option. Ensure that a cell completes before running the next cell. Be sure to read directions for steps that must be taken during the intervening cells. For example, at one point, you are directed to move your model into production before continuing running the notebook.

Congratulations! You have used a notebook to create a pre-prod model. You can check inside {{site.data.keyword.DSX}}, where you will now see the model listed as one of the assets. You have also already deployed this model, which means that you can go to {{site.data.keyword.aios_full}} to add the model there.  

### Work in {{site.data.keyword.aios_full}}
{: #mrm-risk-config-ovr-wos-only-woswork}

You’ll use {{site.data.keyword.aios_full}} to validate and monitor your models and to process metrics. First, you need to do some set up.

#### Step 1: Activate model risk management features

As part of this tutorial, you can automatically set up the model risk management features on {{site.data.keyword.aios_short}}. The following sections detail how to activate the features on {{site.data.keyword.Bluemix_notm}}:

To work with {{site.data.keyword.aios_full}}, you must already have an {{site.data.keyword.Bluemix_notm}} instance and you must have provisioned an {{site.data.keyword.aios_full}} instance.

1. Launch {{site.data.keyword.aios_short}}.
   
   1. From the {{site.data.keyword.Bluemix_notm}} Dashboard, click Services.
   2. Click {{site.data.keyword.aios_short}}
   3. Click the Launch Application button.

2. When prompted about running automatic setup, click the No thanks button.


## Manual setup
{: #mrm-risk-config-ovr-wos-only-manual}

You can manually set up your entire {{site.data.keyword.aios_short}} model risk management service by completing the following steps. To successfully complete the steps, you must have detailed information about your machine learning provider, the database, and the data that is used for monitoring.

### Steps
{: #mrm-risk-config-ovr-wos-only-manual-steps}

1. [Provision prerequisite {{site.data.keyword.Bluemix_notm}} services](/docs/services/ai-openscale?topic=ai-openscale-gs-obj#gs-prps). You must set up two instances of {{site.data.keyword.pm_full}}.
2. [Set up {{site.data.keyword.DSX}} projects](/docs/services/ai-openscale?topic=ai-openscale-gs-obj#gs-setup). You must set up projects for both pre-production and production models.
2. [Configure {{site.data.keyword.aios_short}}](/docs/services/ai-openscale?topic=ai-openscale-gs-obj#gs-confaios).
2. [Next steps: Continue setting up the monitors and data logging](/docs/services/ai-openscale?topic=ai-openscale-gs-obj#gs-next-steps-config).



## Next steps
{: #mrm-risk-config-ovr-wos-only-next}

- [Model risk management and model governance](/docs/services/ai-openscale?topic=ai-openscale-mrm-ovr)
- [Model risk management](/docs/services/ai-openscale?topic=ai-openscale-mrm-risk-wos-only)
