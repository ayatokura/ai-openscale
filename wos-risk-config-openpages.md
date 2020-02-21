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

# Configure model governance with IBM OpenPages MRG ![beta tag](images/beta.png)
{: #mrm-risk-config-openpages}

YYY
{: shortdesc}

  Work in Watson Studio
In IBM Watson Studio, you will create a project and run a notebook to perform most of the set-up tasks, including the following steps:
•	create 2 machine models
•	connect Watson OpenScale to IBM OpenPages
•	create model deployments and configure monitors in Watson OpenScale
Step 1: Create the pre-prod project in Watson Studio
When you first start Watson Studio (hint: use the IBM Cloud dashboard, find your instance of Watson Studio and click the Get Started button) you have the option of taking a tour. Your first task is to create a project to which you associate the Watson Machine Learning instance that you created for your pre-production work.
1.	Click the Create a project tile.
2.	Click the Create an empty project tile. 
3.	Give the project a name and description: In the Name field, type MRM – Pre-prod. You’ll use this project for all your pre-production models. 
4.	You’ll notice that an instance of Cloud Object Storage is required. Go ahead and create an instance of that on IBM Cloud if you haven’t already.
5.	Click the Create button.

Step 2: Associate your new project with the Watson Machine Learning instance
Now you need to associate your pre-prod instance of Watson Machine Learning to your project. You’ll do this by adding it as an associated service.
1.	From the MRM – Pre-prod project screen, click the Settings tab.
2.	In the Associated services pane, click the Add service button, and then click Watson.
3.	Find the Watson Machine Learning tile and click Add.
4.	From the Machine Learning configuration window, click the Existing tab.
5.	From the Existing Service Instance drop-down box, select the Machine Learning-Pre-Prod instance and click the Select button.
Step 3: Add the sample beta notebook to the project
As part of your closed beta information package, you were given access to a Watson Studio notebook. You’ll use it to set up your connection between Watson OpenScale and IBM OpenPages, to create and deploy pre-prod models, and configure the model deployments in Watson OpenScale. 
1.	From the project page, click the Add to project button.
2.	Click the Notebook tile.
3.	Click the From file tab, click the Choose file button and then, select the IBM_Cloud_MRM.ipynb  notebook file that you can download from  https://ibm.box.com/v/modelriskmanagement/
4.	Add a name and description and click the Create notebook button.
Step 4: Run the sample beta notebook 
The newly created notebook is opened in Watson Studio in the integrated notebook editor. You need to update some of the credentials and then run the notebook to create your pre-prod model.
1.	In the corresponding code box, paste your IBM Cloud API:
a.	From the IBM Cloud toolbar, click your Account name, such as <Your user name>’s Account.
b.	From the Manage menu, click Access (IAM).
c.	In the navigation bar, click IBM Cloud API keys.
d.	Click the Create an IBM Cloud API key button.
e.	Type a name and description and then click Save.
f.	Copy the newly created API key and paste it into your notebook in the CLOUD_API_KEY code box, which is the first code box.
2.	In the corresponding code boxes, paste your credentials from the pre-prod and prod instances of Watson Machine Learning:
a.	Go to the IBM Cloud dashboard.
b.	In the Resource summary section, click Services.
c.	Click Machine Learning-Pre-Prod.
d.	In the navigation pane, click Service credentials.
e.	Click the New credential button.
f.	Copy your credentials by clicking the copy icon.
g.	Return to the notebook editor and update the credentials by replacing the sample credentials with your own in the second code box.
h.	Repeat the preceding steps for the prod instance in the third code box.
3.	To restart the notebook and clear the output, from the Kernel menu, click Restart & Clear Output.
4.	Run the notebook each cell at a time by using the Run option. Ensure that a cell completes before running the next cell. Be sure to read directions for steps that must be taken during the intervening cells. For example, at one point, you are directed to move your model into production before continuing running the notebook.
Congratulations! You have used a notebook to create a pre-prod model. You can check inside Watson Studio, where you will now see the model listed as one of the assets. You have also already deployed this model, which means that you can go to IBM Watson OpenScale to add the model there.  
  Work in IBM Watson OpenScale   
You’ll use IBM Watson OpenScale to validate and monitor your models and to process metrics and KPIs. First, you need to do some set up.
Step 1: Activate model risk management features
As part of the closed beta cohort, you can activate the model risk management beta features on IBM Watson OpenScale. The following sections detail how to activate the beta features on the IBM Cloud and the IBM Cloud Pak for Data environments:
On IBM Cloud
To work with IBM Watson OpenScale, you must already have an IBM Cloud instance and you must have provisioned an IBM Watson OpenScale instance.
1.	Launch Watson OpenScale.
a.	From the IBM Cloud Dashboard, click Services.
b.	Click Watson OpenScale
c.	Click the Launch Application button.
2.	When prompted about running automatic setup, click the No thanks button.
3.	From the Insights dashboard, add the following to the URL: ?mrm=true
After you append the variable, the URL should look like the following sample: https://aiopenscale.cloud.ibm.com/aiopenscale/insights?mrm=true
Step 2: Perform analysis in Watson OpenScale
After you run the set-up notebook and activate the MRM beta features, you can both see and compare the sample evaluations in Watson OpenScale. There is a downloadable report, the Model Summary Report, that includes all the quality measures, fairness measures, and drift magnitude.
1.	From the Insights dashboard, click the model deployment tile
2.	From the Actions drop-down box, click one of the following analysis options:
a.	Past evaluations: Lists all the previous versions of the evaluation. 
b.	Compare: Compare any of the models, but especially versions of the same model, for best performance.
c.	Download report PDF: Generates the model summary report, which gives you all of the metrics and the explanation for why they were scored the way they were. 
Deploy a new model to production in Watson OpenScale
Push the best model to production. Create a production record by importing from a pre-production model. After the model is approved for deployment in IBM OpenPages, you can send the model to production in Watson OpenScale. 
1.	Review the status of the model deployment:

 

2.	Return to the sample beta notebook and run the cells to send the model to production.
3.	You can now view the production model deployment tile. In a regular production environment, it initially appears empty until enough data is gathered and time has passed for metric calculation to be triggered. For the beta, the notebook adds data and runs the monitors so that you can see the results right away.

 

Use the analysis of fairness to redefine the model, possibly by using a different algorithm. 
Watson OpenScale enables you to compare models by looking at the key metrics in a side-by-side comparison. Use this feature to determine which version of a model is the best one to send to production or which model might need work:



## Next steps
{: #mrm-risk-config-openpages-next}

