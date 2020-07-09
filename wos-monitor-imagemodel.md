---

copyright:
  years: 2018, 2020
lastupdated: "2020-05-18"

keywords: accuracy, image, image model, keras, tensorflow, numpy, 

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


# Working with an image model
{: #ie-image-working}

You can use {{site.data.keyword.aios_short}} to work with image models. You must complete the following steps to set up you environment:
{: shortdesc}

1. Set up your environment.
   2. Install the {{site.data.keyword.aios_short}} and {{site.data.keyword.pm_full}} packages.
   3. Configure your credentials.
   4. Install the libraries that are needed for creating the models and doing analysis. These include the following libraries:
      - `keras`
      - `tensorflow`
      - `keras_sequential_ascii`
      - `numpy`
      - `pillow`

1. Create and deploy your image-based model.
   2. Create folders for the images based on how you classify them.
       - Inside the main `data` directory you must have `train` and `validation` subdirectories.
       - Within each of the subdirectories, you must have your classification directories.
  2. Standardize the image size and then set the subdirectories to be used for training and validation.
  3. Preprocess the data to rescale and retrieve the images and their classes.
  4. Define and train the model.
  5. Store the model.
  6. Deploy the model.

7. Configure {{site.data.keyword.aios_short}} by assigning the `APIClient`, subscribing the asset and scoring the model.
8. Configure explainability.
   9. Enable the explainability.
   10. Get explanations for the transactions.
   11. Display the explained images. 

