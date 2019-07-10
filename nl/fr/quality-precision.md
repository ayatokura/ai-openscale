---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-11"

keywords: metrics, monitoring, custom metrics, thresholds, precision

subcollection: ai-openscale

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:pre: .pre}
{:codeblock: .codeblock}
{:download: .download}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}
{:faq: data-hd-content-type='faq'}

# Précision ![étiquette bêta](images/beta.png)
{: #quality_precision}

La précision donne la proportion de prévisions correctes dans les prévisions de la classe positive.
{: shortdesc}

## La précision en bref
{: #quality_precision-glance}

- **Description** : proportion de prévisions correctes dans les prévisions de la classe positive
- **Seuils par défaut** : limite inférieure = 80 %
- **Recommandation par défaut** :
   - **Tendance à la hausse** : une tendance à la hausse indique que la métrique s'améliore. Cela signifie que le recyclage des modèles est effectif.
   - **Tendance à la baisse** : une tendance à la baisse indique que la métrique se dégrade. Les données de commentaires deviennent nettement différentes des données de formation.
   - **Variation erratique ou irrégulière** : une variation erratique ou irrégulière indique que les données de commentaires ne sont pas cohérentes d'une évaluation à l'autre. Augmentez la taille d'échantillon minimale pour le moniteur de qualité.
- **Type de problème** : classification binaire
- **Valeurs de graphique** : dernière valeur dans la période
- **Détails de métriques disponibles** : matrice de confusion

## Interprétation de l'affichage
{: #quality_precision-display}

![affichage du graphique de précision](images/quality-precision.png)

## Calculs
{: #quality_precision-math}

La précision (P) est définie comme le nombre de vrais positifs (Tp - true positives) sur le nombre de vrais positifs plus le nombre de faux positifs (Fp).


```
             nombre de vrais positifs
Précision =  __________________________________________________________

             (nombre de vrais positifs + nombre de faux positifs)
```