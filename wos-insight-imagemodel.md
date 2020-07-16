---

copyright:
  years: 2018, 2020
lastupdated: "2020-05-18"

keywords: accuracy, explainability, image classification, image model

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

# Explaining image models
{: #ie-image}

{{site.data.keyword.aios_short}} supports explainability for image data.
{: shortdesc}

## Explaining image model transactions
{: #ie-image-workingviewing}

For an image classification model example of explainability, you can see which parts of an image contributed positively to the predicted outcome and which contributed negatively. In the following example, the image in the positive pane shows the parts which impacted positively to the prediction. The image in the negative pane shows the parts of images that had a negative impact on the outcome.

![Explainability image classification confidence detail displays with an image of a tree frog. Different parts of the picture are highlighted in separate frames. Each part shows the extent to which it did or did not help to determine that the image is a frog.](images/wos-insight-explain-image.png)

See the image zones that contributed to the model output and the zones that did not contribute. Click an image for a larger view.

## Image model examples
{: #ie-image-working-ntbks}

Use the following two Notebooks to see detailed code samples and develop your own {{site.data.keyword.aios_short}} deployments:

- [Tutorial on generating an explanation for an image-based model](https://github.com/pmservice/ai-openscale-tutorials/blob/master/notebooks/Watson%20OpenScale%20Explanation%20for%20Image%20Multiclass%20Classification%20Model.ipynb){: external}
- [Tutorial on generating an explanation for an image-based binary classifier model](https://github.com/pmservice/ai-openscale-tutorials/blob/master/notebooks/Watson%20OpenScale%20Explanation%20for%20Image%20Binary%20Classification%20Model.ipynb){: external}

