---

copyright:
  years: 2018, 2020
lastupdated: "2020-05-18"

keywords: drift, behavior, metrics

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

# Drift in accuracy
{: #behavior-drift-ovr}

Over time, the importance and impact of certain features in a model change. This affects the associated applications and resulting business outcomes. Through the drift detection, {{site.data.keyword.aios_short}} provides a way to track model metrics, model performance, and the way in which feature weights change over time. As data changes, the ability of your model to make accurate predictions may deteriorate. Drift magnitude is the extent of the degradation of predictive performance over time. Use the information about drift to take corrective action.
{: shortdesc}

## Understanding drift detection
{: #behavior-drift-understand}

Drift is the degradation of predictive performance over time because of hidden context. As your data changes over time, the ability of your model to make accurate predictions may deteriorate. {{site.data.keyword.aios_short}} both detects and highlights drift so that you can take corrective action. Watch the following video to see drift detection in action:

![Watch {{site.data.keyword.aios_short}} detect and mitigate drift](https://cdnapisec.kaltura.com/p/1773841/sp/177384100/embedIframeJs/uiconf_id/27941801/partner_id/1773841?iframeembed=true&playerId=ibm-dynid-1_playercontainer&entry_id=1_8tp11bp7&flashvars[streamerType]=auto){: video output="iframe" data-script="none" id="mediacenterplayer" frameborder="0" width="560" height="395" allowfullscreen webkitallowfullscreen mozAllowFullScreen}

### Video transcript
{: #video-transcript-ui-behavior-drift-understand}
{: notoc}

Transcript text that will be displayed underneath this video is coming soon.

Thanks for your patience.

<p>&nbsp;</p>


### How it works
{: #behavior-drift-works}

{{site.data.keyword.aios_short}} creates the drift detection model by looking at the data that was used to train and test the model. For example, if the model has an accuracy of 90% on the test data, it means that it provides incorrect predictions on 10% of the test data.  {{site.data.keyword.aios_short}} builds a binary classification model that accepts a data point and predicts whether that data point is similar to the data that the model either incorrectly (10%) or accurately (90%) predicted.  
 
After {{site.data.keyword.aios_short}} creates the drift detection model, at run time it scores this model by using all the data that the client model receives. For example, if the client model received 1000 records in the past 3 hours, {{site.data.keyword.aios_short}} runs the drift detection model on those same 1000 data points. It calculates how many of the records are similar to the 10% of records on which the model made an error when training. If 200 of these records are similar to the 10%, then it implies that the model accuracy is likely to be 80%. Because the model accuracy at training time was 90%, it means that there is an accuracy drift of 10% in the model.


### Do the math
{: #behavior-drift-math}

{{site.data.keyword.aios_short}} analyzes each transaction to estimate if the model prediction is accurate. If the model prediction is inaccurate, the transaction is marked as drifted. The Estimated accuracy is then calculated as the fraction of non-drifted transactions to the total number of transactions analyzed. The Base accuracy is the accuracy of the model on the test data. {{site.data.keyword.aios_short}} calculates the extent of the drift in accuracy as the difference between Base accuracy and Estimated accuracy. Further, {{site.data.keyword.aios_short}} analyzes all the drifted transactions; and then, groups transactions based on the similarity of each feature's contribution to the drift in accuracy. In each cluster, {{site.data.keyword.aios_short}} also estimates the important features that played a major role in the drift in accuracy and classifies their feature impact as large, some, and small. 



## Next steps

- For information on how to set up drift detection, see [Configuring the drift detection monitor](/docs/ai-openscale?topic=ai-openscale-behavior-drift-config).
- To mitigate drift, after it has been detected by {{site.data.keyword.aios_short}}, you must build a new version of the model that fixes the problem. A good place to start is with the data points that are highlighted as reasons for the drift. Introduce the new data to the predictive model after you have manually labeled the drifted transactions and use them to re-train the model.


