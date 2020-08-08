---

copyright:
  years: 2018, 2020
lastupdated: "2020-08-08"

keywords: metrics, monitoring, custom metrics, thresholds, Fairness for a group, sex, age, race

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

# Fairness for a group
{: #quality_group}

The Fairness for a group metric gives the model's propensity to deliver favorable outcomes to one group over another. A group can be any group, such as age, sex, or race.
{: shortdesc}


## Fairness for a group at a glance
{: #quality_group-glance}

- **Description**: The models propensity to deliver favorable outcomes to one group over another.
- **Default thresholds**: Lower limit = 80%
- **Default recommendation**: Debiased scoring endpoint that you can use in your business application for receiving debiased responses from your deployed model.
- **Problem type**: All
- **Data type**: Structured
- **Chart values**: Last value in the timeframe
- **Metrics details available**: Yes

## Protected attributes
{: #quality_group-atts}

{{site.data.keyword.aios_short}} automatically identifies whether any known protected attributes are present in a model. When {{site.data.keyword.aios_short}} detects these attributes, it can automatically configure bias monitors for each attribute present to ensure that bias against these potentially sensitive attributes is tracked in production. 

### Sex
{: #quality_group-sex}

{{site.data.keyword.aios_short}} configures the bias monitor for the **Sex** attribute so that `Female` and `Non-Binary` are the monitored values, and `Male` is the reference value. 

### Ethnicity
{: #quality_group-ethnicity}

{{site.data.keyword.aios_short}} configures the bias monitor for the **ethnicity** attribute so that `White-caucasian` is the reference value while other ethnicities are monitored values.

### Marital status
{: #quality_group-marital}

{{site.data.keyword.aios_short}} configures the bias monitor for the **marital status** attribute so that `married` is the reference value and `single` is the monitored value.

### Age
{: #quality_group-age}

{{site.data.keyword.aios_short}} configures the bias monitor for the **age** attribute so that the range of ages produces actionable debiasing, for example `18-25` and `26-75`.

### Postal code
{: #quality_group-zip}

{{site.data.keyword.aios_short}} configures the bias monitor for the **postal code** attribute so that individual postal codes are scored.

## Interpreting the display
{: #quality_group-display}

Fairness alerts display on the dashboard in tiles.

![Example of tile with fairness alert](images/wos-faststart-model-tile.png)

You can review all metrics values over time on the {{site.data.keyword.aios_short}} dashboard:

![Fairness metrics chart showing drift lower than the set threshold](images/wos-fairness-sex.png)

### Fairness Score for a group
{: #quality_group-display-fairnessscore}

![Fairness score pane with display of a violation for sex that is 13 percent below the threshold of 98 percent](images/wos-fairness-sex-scorepanel.png)


### Monitored Groups
{: #quality_group-display-monitoredgroups}

![Monitored groups pane with display of average score and score for female group](images/wos-fairness-sex-monitored.png)


### Schedule
{: #quality_group-display-schedule}

The **Schedule** pane shows the **Last evaluation** and **Next evaluation** times. Quality metrics are evaluated every hour. You can force evaluation by clicking **Check fairness now**. You can also add feedback by clicking **Make a scoring request**.

![Fairness schedule pane with display of last and next evaluations and links to check fairness now and make a scoring requests](images/wos-fairness-button.png)


### Do the math
{: #quality_group-display-disparate-imp-rat}



```
                          (% of favorable outcome in monitored group)
Disparate Impact Ratio =  ____________________________________________
                          (% of favorable outcome in reference group)
```


