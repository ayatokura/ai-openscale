---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-28"

keywords: release notes, what's new 

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

# 新增功能
{: #rn-relnotes}

本文件概述 {{site.data.keyword.aios_full_notm}} 的新特性。
{: shortdesc}

## 2019 年 7 月 2 日
{: #rn-2jul2019}

{{site.data.keyword.aios_short}} 的新特性及變更如下。

- __*漂移偵測*__：![測試版標記](images/beta.png)

  {{site.data.keyword.aios_short}} 現在支援漂移偵測。

   如需相關資訊，請參閱[漂移偵測](/docs/services/ai-openscale?topic=ai-openscale-behavior-drift-ovr)。

- __*Microsoft Azure ML Service 支援*__：{{site.data.keyword.aios_short}} 現在支援 Microsoft Azure ML Service，藉以將您的 Azure ML 服務 AI 模型與 {{site.data.keyword.aios_short}} 的公平性、精確度和可解釋性整合在一起。

   如需相關資訊，請參閱 [Microsoft Azure ML Service 架構](/docs/services/ai-openscale-icp?topic=ai-openscale-icp-frmwrks-azure-service)。

- __*工作流程已改良*__：{{site.data.keyword.aios_short}} 努力改良工作流程，以致於您可以更快處理您的工作，點選次數減少，取得的可解釋性增多。導覽畫面可讓您看到您的所在位置，並且輕鬆在配置作業之間來回切換。

   如需相關資訊，請參閱[準備適用於部署的監視器](/docs/services/ai-openscale?topic=ai-openscale-mo-config)。

- __*多個機器學習提供者*__：為何只綁定一個機器學習提供者或引擎？利用 {{site.data.keyword.aios_short}} 最新版本，您可以新增多個提供者，以便充分利用它們的獨特特性，或提供與舊式應用程式之間的連貫性。

   如需相關資訊，請參閱[支援多個機器學習引擎](/docs/services/ai-openscale?topic=ai-openscale-fmrk-workaround-multmleng)。

- __*更多現成的度量*__：這個 {{site.data.keyword.aios_short}} 版本提供許多新的公平性、品質、行為、效能和分析度量。我們需要更大的空間！

   如需相關資訊，請參閱[品質度量概觀](/docs/services/ai-openscale?topic=ai-openscale-anlz_metrics)，然後開始四處點選，以造訪下列：[公平性](/docs/services/ai-openscale?topic=ai-openscale-anlz_metrics_fairness)、[效能](/docs/services/ai-openscale?topic=ai-openscale-performance_mets_through)、[分析](/docs/services/ai-openscale?topic=ai-openscale-anlz_metrics_payload)和[行為](/docs/services/ai-openscale?topic=ai-openscale-behavior-ovr)。

- __*加快處理偏誤*__：透過針對偏誤配置所建議的公平性屬性和自動值，很容易就能查看 {{site.data.keyword.aios_short}} 是在所部署模型中的何處偵測到可能違反公平性臨界值。您可以選擇接受所建議之要監視的特性，以及選擇變更那些值。

   如需相關資訊，請參閱[公平性度量概觀](/docs/services/ai-openscale?topic=ai-openscale-anlz_metrics_fairness)。

## 2019 年 6 月 11 日
{: #rn-11June2019}

該服務的新特性和變更如下。

- __*已更新儀表板功能*__：「{{site.data.keyword.aios_short}} 儀表板」已歷經多次修訂。這個新版本包含下列幾項改良：

    - 新的說明畫面可讓您更容易尋找 StackOverflow、IBM Support 等之類的資源，以及 
    - 儀表板已啟用全球化
    - 易用性加強功能

## 2019 年 6 月 7 日
{: #rn-7June2019}

該服務的新特性和變更如下。

- __*已加強指令行介面*__：ibm-ai-openscale-cli 指令行介面已更新，現在發行的是 0.2.148 版。這個新版本包含下列幾項改良：

    - 已更新品質度量歷程，OpenScale 支援的全套新品質度量都包含在內
    - 當使用 IBM Db2 時，支援直接指定 SSL 憑證
    - 支援新的 ibm-ai-openscale 2.1.8 Python SDK
    - 其他的錯誤修正程式和穩定性改良

   執行 `pip install -U ibm-ai-openscale-cli` 指令，以從 PyPI 安裝；執行 `ibm-ai-openscale-cli --help` 指令，以取得使用說明。如需相關資訊，請參閱 [PyPI 專案頁面](https://pypi.org/project/ibm-ai-openscale-cli)。

## 2019 年 5 月 29 日
{: #rn-29May2019}

該服務的新特性和變更如下。

- __*偏誤視覺化加強功能*__：![測試版標記](images/beta.png) 偏誤視覺化包含下列視圖： 

    - 有效負載 + 擾動：如果未符合評估所需的最低記錄數目，則包含所選那個小時內所收到的評分要求，外加過去幾個小時內的其他記錄。如果受監視特性的值有變更，會包含用來測試模型回應的其他擾動/合成記錄。
    - 有效負載：模型在所選那個小時內所收到的實際評分要求。
    - 訓練：用來訓練模型的訓練資料記錄。
    - 除去偏誤：處理執行時期和擾動資料之後的除去偏誤演算法的輸出。

   如需相關資訊，請參閱[偏誤視覺化](/docs/services/ai-openscale?topic=ai-openscale-mf-monitor#mf-monitor-bias-viz)。

- __*計算已除去偏誤輸出的精確度*__： 精確度計算會包含已除去偏誤的輸出。您可以將已除去偏誤模型的精確度，與正式作業模型的精確度相互比較。

   如需相關資訊，請參閱[精確度](/docs/services/ai-openscale?topic=ai-openscale-acc-monitor#acc-debias-view)。

- __*支援多個機器學習引擎*__：{{site.data.keyword.aios_short}} 可在單一實例內支援多個機器學習引擎，但前提是您要透過 [Python SDK](http://ai-openscale-python-client.mybluemix.net/?cm_mc_uid=70732728440115575086192&cm_mc_sid_50200000=62539451560175957820) 來執行佈建。

   如需相關資訊，請參閱[支援多個機器學習引擎](/docs/services/ai-openscale?topic=ai-openscale-fmrk-workaround-multmleng)。

- __*國際化支援*__：{{site.data.keyword.aios_short}} 支援本地化版本，並且包含採用支援語言的處理程序資料。{{site.data.keyword.aios_short}} 使用者介面、說明文件和錯誤訊息目前會轉換成下列語言： 
    - 德文
    - 法文
    - 義大利文
    - 西班牙文
    - 巴西葡萄牙文
    - 日文
    - 簡體中文
    - 繁體中文
    - 韓文

   如需相關資訊（包括限制），請參閱 [{{site.data.keyword.aios_short}} 支援語言](/docs/services/ai-openscale?topic=ai-openscale-sl-langs)。

- __*{{site.data.keyword.pm_full}} 架構加強功能*__：{{site.data.keyword.aios_short}} 現在在 {{site.data.keyword.pm_full}} 引擎上支援 scikit-learn 和 XGBoost 架構。

   如需相關資訊，請參閱 [{{site.data.keyword.pm_full}} 架構](/docs/services/ai-openscale?topic=ai-openscale-frmwrks-wml)。

## 2019 年 4 月 25 日
{: #rn-25April2019}

該服務的新特性和變更如下。

除了可用性改良和安全更新項目之外，我們的開發人員還忙碌於新增特性。過去這幾週所新增或加強的 {{site.data.keyword.aios_short}} 特性包括：

- __*自動化設置導覽*__：設置 {{site.data.keyword.aios_short}} 環境的新導覽方式。使用[自動化設置](/docs/services/ai-openscale?topic=ai-openscale-wos-fast-start)來佈建服務及下載和配置模型。當您有 {{site.data.keyword.aios_short}} 的新實例時，就會看到此選項。
- __*切換至測試版*__：![測試版標記](images/beta.png)新的切換按鈕**探索新的測試版**可讓您在測試版環境中工作，您可以在其中檢查所有最新特性和新功能。不喜歡您看到的內容？只要按一下**回到原始版本**就可以切回。您的配置和監視器不受影響。下列功能是現行測試版程式的一部分：
    - __*混淆矩陣*__：[混淆矩陣顯示](/docs/services/ai-openscale?topic=ai-openscale-it-conf-mtx)誤肯定和誤否定。按一下資料格以檢視意見記錄的子集。

## 2019 年 4 月 10 日
{: #rn-10April2019}

- __*Express Path 工具現在支援客戶模型*__：自動執行 {{site.data.keyword.aios_short}} 上線程序。

   如需相關資訊，請參閱 [ibm-ai-openscale-cli](https://pypi.org/project/ibm-ai-openscale-cli/)。


## 2019 年 3 月 5 日
{: #rn-5March2019}

該服務的新特性和變更如下。

從舊版以來已新增或加強的 {{site.data.keyword.aios_short}} 特性包括：

- __*新的 Credit Risk 模型*__：所有的評分引擎都支援新的 Credit Risk 模型範例/指導教學。如需相關資訊，請參閱[開始使用](/docs/services/ai-openscale?topic=ai-openscale-gettingstarted#gettingstarted)和[其他資源](/docs/services/ai-openscale?topic=ai-openscale-arsc-ov#arsc-ov)主題。

- __*計算除去偏誤*__：您可以在正式作業模型與 {{site.data.keyword.aios_short}} 所建立的除去偏誤模型之間切換。如需相關資訊，請參閱[正式作業模型和除去偏誤模型](/docs/services/ai-openscale?topic=ai-openscale-it-ov#it-prdb)以及[瞭解除去偏誤如何運作](/docs/services/ai-openscale?topic=ai-openscale-mf-monitor#mf-debias)。

## 2019 年 2 月 22 日
{: #rn-22February2019}

該服務的新特性和變更如下。

從舊版以來已新增或加強的 {{site.data.keyword.aios_short}} 特性包括：

- __*使用者介面更新*__：您可以匯入 JSON 檔案，以便在建立訂閱期間，以程式設計方式來配置所有監視器和特性。您也可以匯出配置檔。如需相關資訊，請參閱[使用 JSON 檔案來配置部署訂閱](/docs/services/ai-openscale?topic=ai-openscale-cf-ov)主題。

## 2019 年 2 月 7 日
{: #rn-7February2019}

該服務的新特性和變更如下。

從舊版以來已新增或加強的 {{site.data.keyword.aios_short}} 特性包括：

- __*使用者介面更新*__：{{site.data.keyword.aios_short}} 使用者介面已有一些改良，包括[隨需檢查公平性和精確度](/docs/services/ai-openscale?topic=ai-openscale-it-ov#it-vdep)的作法，以及能夠從[公平性明細圖表](/docs/services/ai-openscale?topic=ai-openscale-it-ov#it-tra)來查看交易清單。

- __*「可解釋性」的加強*__：現在所有數字在「相關正向 (PP)」和「相關負向 (PN)」值之間的精準度和小數位數都是相同的。

- __*Db2 SSL 支援*__：{{site.data.keyword.aios_short}} 支援將自簽憑證（Base-64 編碼）與 Db2 認證一起傳遞。

- __*{{site.data.keyword.Bluemix}} 資料庫支援*__：除了 Compose for PostgreSQL 和 Db2，{{site.data.keyword.aios_short}} 現在還支援 Databases for PostgreSQL

## 2018 年 12 月 14 日
{: #rn-14December2018}

該服務的新特性、變更和已知問題如下。

{{site.data.keyword.aios_short}} 從測試版以來已新增或加強的特性包括：

- __*通用版*__：{{site.data.keyword.aios_full_notm}} 通用版 (GA) 屬於 {{site.data.keyword.Bluemix}} 標準（付費）方案。

- __*{{site.data.keyword.icp4dfull_notm}} 1.2 版*__：如果您使用的是 {{site.data.keyword.wos4d_full}} 1.2 版，請參閱這裡的說明文件（包括安裝指示）：[安裝核對清單](/docs/services/ai-openscale-icp?topic=ai-openscale-icp-inst-install-icp#install)

- __*支援您的模型類型*__：除了 {{site.data.keyword.pm_full}} 中的 AI 模型部署，{{site.data.keyword.aios_short}} 還支援 Microsoft Azure、Amazon SageMaker 和「自訂」環境中的模型部署。如需相關資訊，請參閱[支援的模型類型](/docs/services/ai-openscale?topic=ai-openscale-in-ov)。

- __*免費的「精簡」資料庫*__：免費的「精簡」受管理資料庫可提供您在開始使用 {{site.data.keyword.aios_short}} 時所需的一切。如需詳細資料，請參閱 [{{site.data.keyword.aios_short}} 定價方案](https://{DomainName}/catalog/services/watson-openscale){: external}。

- __*偏誤監視*__：支援 `float` 和 `double` 類型的受保護屬性，以及支援在線性迴歸模型上偵測偏誤。此外，{{site.data.keyword.aios_short}} 可為您自動去除您 AI 模型的偏誤。如需相關資訊，請參閱[瞭解公平性](/docs/services/ai-openscale?topic=ai-openscale-mf-monitor)。

- __*可解釋性*__：支援迴歸模型、Python 函數和補充的對比解釋。如需相關資訊，請參閱[監視可解釋性](/docs/services/ai-openscale?topic=ai-openscale-ie-ov)。

- __*資料儲存庫*__：在不倚賴 {{site.data.keyword.pm_full}} 情況下進行品質監視，並且能夠使用您自己的資料庫，不論是 Db2、Postgres 或 Db2 on Cloud 都行。

- __*已加強的使用者介面*__：{{site.data.keyword.aios_short}} 使用者介面已改良，而包含直方圖分佈，可讓您從直方圖來切換顯示訓練資料、模型 ID 和版本化，以及交易 ID 表格。如需相關資訊，請參閱[將特定小時的資料視覺化](/docs/services/ai-openscale?topic=ai-openscale-it-ov#it-vdet)。

- __*Alternate tutorial set-up option*__：若要自動佈建及配置必要的 {{site.data.keyword.Bluemix}} 服務，以及查看 IBM {{site.data.keyword.aios_full}} 應用程式（包括樣本資料），您可以安裝及執行 Python 模組。請參閱[安裝 Python 模組以設置 {{site.data.keyword.aios_short}}](/docs/services/ai-openscale?topic=ai-openscale-as-module)

## 2018 年 9 月 17 日
{: #rn-17September2018}

- **測試搶鮮版** - 歡迎使用 {{site.data.keyword.aios_full_notm}} 測試搶鮮版。

<p>&nbsp;</p>

## 後續步驟
{: #relnotes-in-next}

還有其他問題嗎？

- [限制](/docs/services/ai-openscale?topic=ai-openscale-in-ov#in-lim)
- [已知問題](/docs/services/ai-openscale?topic=ai-openscale-in-ov#rn-12ki)