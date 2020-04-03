---

copyright:
  years: 2018, 2020
lastupdated: "2020-04-08"

keywords: fairness, monitoring, charts, de-biasing, bias, accuracy

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

# Explaining unstructured text models
{: #ie-unstruct}

{{site.data.keyword.aios_short}} supports explainability for unstructured text data.
{: shortdesc}

If you are using a Keras model that takes the input as byte array, you must create a deployable function in {{site.data.keyword.pm_full}} that accepts the entire text as a single feature in input (as opposed to text which is vectorised and represented as a tensor or split across multiple features). Creating a deployable function is part of the functionality that {{site.data.keyword.pm_full}} support. For more information, see [Passing payload data to model deployments](https://dataplatform.cloud.ibm.com/docs/content/wsj/analyze-data/ml-deploy-functions.html?linkInPage=true#models){: external}

## Working with unstructured text models
{: #ie-unstruct-steps}

1. Set up your environment.
   2. Install the {{site.data.keyword.aios_short}} and {{site.data.keyword.pm_full}} packages.
   3. Configure your credentials.
   4. Install the libraries that are needed for creating the models and doing analysis. These include the following libraries:
      - `pandas`
      - `pyspark` (if not using {{site.data.keyword.DSX}})

1. Create and deploy your image-based model.
   2. Load training data into a pandas frame.
   2. Train the model on the data.
   3. Publish the model.
   4. Deploy and score the model.

7. Configure {{site.data.keyword.aios_short}} by assigning the `APIClient`, sbuscribing the asset and scoring the model.
8. Configure explainability.
   9. Enable the explainability.
   10. Get explanations for the transactions.

## Explaining unstructured text transactions
{: #ie-unstruct-xplan}

The following example of explainability shows a classification model that evaluates unstructured text. The explanation shows the keywords that had a positive as well as a negative impact on the model prediction. We also show the position of the identified keywords in the original text which was fed as input to the model.

![Explainability image classification chart is displayed. it shows confidence levels for the unstructured text](images/wos-insight-explain-text.png)

## Enabling non-space-delimited language support
{: #ie-unstruct-xplan-langsupport}

Explainability and the use of word highlighting is supported even for languages, such as Japanese, Chinese, and Korean that are not space-delimited. You have the ability to turn this feature on or off. You must enable this feature manually. Optionally, you can have the system auto-detect the language. With this feature enabled, expanations that are generated for non-whitespace languages such as Japanese, Chinese, or Korean properly indicate which characters influence the model's prediction. 

1. From the **Configure** window, click **Explainability**.
2. In the **Language support** panel, click the **Edit** ![The edit icon](/images/wos-edit-icon.png) icon, and then set the **Word segmentation** to **On**. 
3. After you enable word segementation, the **Language** drop-down field is enabled and the "Automatically detect" option is selected by default. To manually set the language, click the drop-down box and select the language from the list.
4. Click the **Save** button.

After you save your changes, the tile in the **Explainability** configuration reflects the changed state.

## Unstructured text model example
{: #ie-unstruct-ntbkssample}

Use the following notebook to see detailed code samples and develop your own {{site.data.keyword.aios_short}} deployments:

- [Tutorial on generating an explanation for a text-based model](https://github.com/pmservice/ai-openscale-tutorials/blob/master/notebooks/Watson%20OpenScale%20Explanation%20for%20Text%20Model.ipynb){: external}

