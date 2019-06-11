---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-29"

keywords: metrics, monitoring, custom metrics, thresholds

subcollection: ai-openscale

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}

# Analisi delle metriche e delle transazioni ![tag beta](images/beta.png)
{: #anlz_metrics}

È possibile utilizzare {{site.data.keyword.aios_full}} per analizzare le metriche e le transazioni tramite varie modalità.
{: shortdesc}

## Matrice di confusione ![tag beta](images/beta.png)
{: #it-conf-mtx}

Come un dettaglio delle metriche di qualità, è possibile visualizzare i record che il modello ha analizzato in modo non corretto. Tali anomalie possono essere falsi positivi o falsi negativi per i modelli di classificazione binari o possono essere assegnazioni di classi non corrette per i modelli multi-classe. È anche possibile visualizzare un elenco di record di feedback che il modello non ha analizzato correttamente.
{: shortdesc}

1. Da uno qualsiasi dei grafici **Qualità**, come **Correttezza** fare clic su un'ora/giorno nel grafico.
    
    ![Elenco transazioni distorte](images/Confusion_Matrix_040819.004.png)

1. Una matrice di confusione visualizza i falsi positivi e falsi negativi. Fare clic su una cella per visualizzare il sottoinsieme dei record di feedback.

    ![Elenco transazioni distorte](images/Confusion_Matrix_040819.005.png)

1. Esaminare i record di feedback e richiedere una spiegazione dell'analisi rispetto al record di feedback.

    ![Elenco transazioni distorte](images/Confusion_Matrix_040819.006.png)

1. Le transazioni appaiono in linea.

    ![Elenco transazioni distorte](images/Confusion_Matrix_040819.007.png)
