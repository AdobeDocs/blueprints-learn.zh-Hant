---
title: Customer Analytics與Insight開發
description: 瞭解如何建立跨管道分析工作區、計算量度和控制面板，以進行行為和效能分析。
solution: Customer Journey Analytics, Experience Platform
exl-id: 235a4eb0-91ae-4030-b90e-7eda08c67ae1
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1717'
ht-degree: 3%

---

# Customer Analytics與insight開發

本指南說明Customer Analytics和insight產生使用案例模式，此模式將[!DNL Adobe Experience Platform]個資料集連結至[!DNL Customer Journey Analytics]以建立資料檢視、自由格式分析工作區、計算量度、控制面板和行動計分卡，以及選擇性地將CJA定義的對象發佈回[!DNL Adobe Experience Platform]以供啟用。

它專為需要瞭解此模式的功能、其支援的業務目標、其啟用的戰術使用案例以及所涉及的Adobe應用程式的解決方案架構師、行銷技術人員和實作工程師所設計。

與分類法中聚焦於啟用和參與（傳送訊息、個人化內容、啟用對象）的其他模式不同，此模式聚焦於瞭解 — 分析客戶行為、衡量行銷活動績效、識別趨勢，並產生為策略及最佳化決策提供資訊的見解。

## 使用案例模式

**Customer Analytics與insight世代**

建立跨管道分析工作區、計算量度和儀表板，以瞭解客戶行為和行銷活動績效。

**執行計畫：**&#x200B;資料連線>資料檢視設定> Workspace Analysis >控制面板發佈

## 使用案例概述

組織需要瞭解客戶跨管道的行為、行銷活動的表現、客戶在歷程中的流失位置、哪些內容引起共鳴，以及不同區段如何隨著時間保留。 Customer Analytics和insight產生將[!DNL Adobe Experience Platform]中的豐富跨管道資料連結至[!DNL Customer Journey Analytics]，因應此需求，分析師可以在其中建立自由格式工作區、建立自訂量度、設定歸因模型，以及發佈控制面板以供利害關係人使用。

此模式適用於多個受眾：需要深入探索分析的行銷分析師、需要效能儀表板的行銷活動經理、需要參與和保留率深入分析的產品經理，以及需要概覽KPI計分卡的高階主管。 實作方式會因主要分析重點而有所不同，例如行銷活動績效測量、跨管道歷程分析、分析導向型對象啟用或引導式產品深入分析。

## 主要業務目標

此使用案例模式支援下列業務目標。

**改善分析和報告**

增強報告功能，透過統一的儀表板和自助服務工具提供更快、更實際可行的行銷深入分析。

- **KPI：**&#x200B;效率、生產力

如需此業務目標的詳細資訊，請參閱[改善分析與報告](/help/blueprints/business-objectives/analytics-insights/improve-analytics-reporting.md)。

**啟用資料導向式決策**

為團隊提供自助分析、即時客戶見解和AI支援的預測以指導策略。

- **KPI：**&#x200B;效率、生產力

如需此業務目標的詳細資訊，請參閱[啟用資料導向式決策](/help/blueprints/business-objectives/analytics-insights/enable-data-driven-decision-making.md)。

**改善行銷歸因**

準確衡量行銷接觸點、管道和行銷活動對轉換和收入結果的影響。

- **KPI：**&#x200B;效率、遞增收入

如需此業務目標的詳細資訊，請參閱[改善行銷歸因](/help/blueprints/business-objectives/analytics-insights/improve-marketing-attribution.md)。

**最佳化行銷支出和ROI**

透過瞭解哪些管道和行銷活動產生最高回報，最佳化行銷預算分配。

- **KPI：**&#x200B;效率、遞增收入

如需此業務目標的詳細資訊，請參閱[最佳化行銷支出和ROI](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md)。

## 戰術使用案例範例

以下是可使用此模式實施的戰術使用案例範例。

- 行銷活動績效儀表板 — 跨電子郵件、簡訊、推播和付費媒體行銷活動的傳遞量度、參與率、轉換和收入歸因
- Customer Journey流失分析 — 識別客戶在購買、註冊或到職漏斗中的流失位置
- 同類群組保留分析 — 衡量不同贏取同類群組在數週、數月及數季中的保留程度
- 管道歸因模型 — 比較首次接觸、上次接觸、線性及時間衰減歸因，以瞭解哪些管道可促進轉換
- 內容效能分析 — 依區段、管道和生命週期階段找出最能引起共鳴的內容
- 產品使用與採用分析 — 追蹤功能採用、參與頻率和使用者成長趨勢
- 客戶生命週期階段分析 — 依生命週期階段（新增、作用中、有風險、已失效）劃分及分析客戶
- 行銷組合最佳化儀表板 — 比較管道投資與收入貢獻
- 跨頻道參與計分和報告 — 從網頁、應用程式、電子郵件和行銷活動互動建立複合參與分數

## 關鍵績效指標

以下KPI可協助評估此使用案例模式的成功。

| KPI | 說明 | 測量方法 |
| --- | --- | --- |
| 效率 | 縮短insight時間和手動報告工作 | 追蹤分析師在CJA實施前後建置報表所花費的時間 |
| 生產力 | 業務使用者建立的自助服務分析數目 | 監視Workspace專案建立和儀表板使用情況 |
| 遞增收入 | 歸因於見解驅動的最佳化決策的收入 | 衡量根據CJA分析最佳化之行銷活動的收入成長 |
| 轉換率 | 關鍵客戶歷程中的Funnel完成率 | 使用CJA流失視覺效果追蹤每個歷程步驟的流失率 |
| 參與度 | 跨管道的客戶互動深度和頻率 | 在CJA中建立參與計分的計算量度 |
| 保留 | 已定義期間內的客戶退貨率 | 使用CJA同類群組分析來測量保留率曲線 |

## 應用程式

在此使用案例模式中使用以下應用程式。

- **[!DNL Customer Journey Analytics] (CJA)** — 連線、資料檢視、工作區分析、引導式分析、計算量度、控制面板、對象發佈和內容分析
- **[!DNL Adobe Experience Platform] (AEP)** — 資料湖、資料集、XDM結構描述、設定檔和事件資料（用於提供CJA連線）

## 相關文件

下列資源提供此使用案例模式的其他資訊。

### [!DNL Customer Journey Analytics] — 快速入門

- [CJA概觀](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-overview/cja-overview)
- [CJA護欄](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-admin/guardrails)

### 連線

- [連線總覽](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-connections/overview)
- [建立或編輯連線](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-connections/create-connection)
- [管理連線](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-connections/manage-connections)

### 資料視圖

- [資料檢視總覽](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dataviews/data-views)
- [建立或編輯資料檢視](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [元件設定概觀](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dataviews/component-settings/overview)
- [持續性設定](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dataviews/component-settings/persistence)
- [歸因設定](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dataviews/component-settings/attribution)
- [格式設定](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dataviews/component-settings/format)
- [量度重複資料刪除](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dataviews/component-settings/metric-deduplication)
- [包含/排除值](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dataviews/component-settings/include-exclude-values)
- [工作階段設定](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dataviews/session-settings)
- [衍生欄位](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dataviews/derived-fields)

### Workspace &amp; analysis

- [Workspace概觀](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/home)
- [建立專案](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/build-workspace-project/create-projects)
- [自由格式表格](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/visualizations/freeform-table/freeform-table)
- [流量視覺效果](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/visualizations/flow/flow)
- [流失視覺效果](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/visualizations/fallout/fallout-flow)
- [同類群組表格](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/visualizations/cohort-table/cohort-analysis)
- [歸因面板](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/panels/attribution)
- [劃分維度](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/components/dimensions/t-breakdown-fa)
- [共用專案](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/curate-share/share-projects)
- [排程專案](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/curate-share/send-schedule-files)
- [匯出概觀](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/export/export-cloud)

### 引導式分析

- [引導式分析概述](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/guided-analysis/overview)
- [funnel檢視](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/funnel/funnel)
- [趨勢檢視](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/guided-analysis/trends/usage)
- [參與頻率檢視](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/guided-analysis/trends/frequency)
- [保留檢視](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/guided-analysis/retention/retention-rates)
- [主動式成長檢視](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/guided-analysis/user-growth/active)
- [發行影響檢視](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/guided-analysis/impact/release)
- [首次使用影響檢視](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/guided-analysis/impact/first-use)
- [時間表檢視](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/guided-analysis/streams/timeline)

### 元件

- [篩選器概觀](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-components/cja-filters/filters-overview)
- [建立篩選器](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-components/cja-filters/create-filters)
- [計算量度概觀](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)
- [建立計算量度](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-workflow/cm-build-metrics)
- [計算量度函式](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-functions)
- [註解概述](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-components/annotations/overview)
- [日期範圍](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/date-ranges/overview)
- [量度元件](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-components/apply-create-metrics)

### 對象發佈

- [受眾概述](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-components/audiences/audiences-overview)
- [建立及發佈對象](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-components/audiences/publish)
- [管理對象](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-components/audiences/manage)

### 內容分析

- [Content Analytics](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/content-analytics/content-analytics)
- [Content Analytics設定](https://experienceleague.adobe.com/en/docs/analytics-platform/using/content-analytics/config/configuration)

### 控制面板和計分卡

- [建立行動計分卡](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dashboards/create-scorecard)
- [設定及組織計分卡](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/curate)
- [Adobe Analytics控制面板 — 執行指南](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dashboards/set-up-execs)
- [摘要數字視覺效果](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/visualizations/summary-number-change)

### AEP基礎

- [資料集總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/catalog/datasets/overview)
- [XDM系統概覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/xdm/home)
- [來源概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sources/home)
- [Identity Service總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/identity/home)
- [Audience Portal概述](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/ui/audience-portal)

### AJO報表整合

- [AJO + CJA整合指南](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [行銷活動電子郵件報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/reporting/campaign-global-report-cja-email)
- [歷程電子郵件報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/reporting/journey-global-report-cja-email)

### 教學課程與指南

- [結構描述組合基本面](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/xdm/schema/composition)
- [網頁SDK概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/web-sdk/home)
- [設定資料串流](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/datastreams/configure)
