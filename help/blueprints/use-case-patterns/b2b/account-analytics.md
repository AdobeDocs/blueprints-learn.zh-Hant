---
title: B2B分析
description: 瞭解如何在跨管道客戶歷程分析中加入B2B帳戶層級資訊。
solution: Customer Journey Analytics, Real-Time Customer Data Platform
exl-id: 9d576e5c-cbd2-4c60-a6b0-88f8b8b963b4
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1811'
ht-degree: 2%

---

# B2B分析

本指南說明B2B分析使用案例模式，此模式使用[!DNL Customer Journey Analytics] ([!DNL CJA]) B2B edition和[!DNL Real-Time Customer Data Platform] ([!DNL RT-CDP]) B2B edition將B2B帳戶層級資訊併入跨管道客戶歷程分析。 它專為需要瞭解此模式的功能、其支援的業務目標、其啟用的戰術使用案例以及所涉及的Adobe應用程式的解決方案架構師、行銷技術人員和實作工程師所設計。

B2B Analytics透過帳戶型連線、B2B特定容器（帳戶、全域帳戶、商機、購買群組）和帳戶層級報表，擴充標準[!DNL CJA]功能。 此功能可讓組織在帳戶層次分析行銷與銷售參與度、追蹤商機進展、測量購買群組完整性，以及將收入歸因於延長B2B銷售週期內的行銷接觸點。

## 使用案例模式

**B2B分析**

在跨管道客戶歷程分析中加入B2B帳戶層級資訊。

**執行計畫：** B2B資料連線>帳戶資料檢視設定> Workspace Analysis >控制面板發佈

## 使用案例概述

B2B組織面臨根本性的分析挑戰：他們的客戶不是個別人員，而是由多個利害關係人、購買群組和機會組成的帳戶。 標準人員型分析無法回答「哪些帳戶最參與？」、「我們的購買群組有多完整？」或「哪些行銷接觸點推動機會進展？」等問題。

B2B Analytics利用[!DNL CJA] B2B edition建立以帳戶為中心的分析檢視，將個人層級的行為資料與帳戶、商機及購買群組維度相結合，藉此解決此問題。[!DNL RT-CDP] B2B edition提供基礎的帳戶設定檔統一和B2B身分解析度，可提供analytics層。 這些解決方案可共同讓組織在帳戶層級建立跨管道歷程分析、將行銷參與與管道進展建立關聯，並向行銷和銷售團隊提供可操作的深入分析。

目標受眾包括B2B行銷營運團隊、需求產生負責人、收入營運分析師，以及需要深入瞭解帳戶層級參與度和管道運作狀態的銷售負責人。

## 主要業務目標

此使用案例模式支援下列業務目標。

### 改善分析和報告

增強報告功能，透過統一的儀表板和自助服務工具提供更快、更實際可行的行銷深入分析。 B2B Analytics可讓組織將來自多個來源的帳戶層級參與資料合併成單一分析環境，提供行銷方案如何影響管道和收入的跨管道可見度。

**KPI：**&#x200B;效率、生產力

[進一步瞭解改善分析和報告](/help/blueprints/business-objectives/analytics-insights/improve-analytics-reporting.md)

### 啟用資料導向式決策

為團隊提供自助分析、即時客戶見解和AI支援的預測以指導策略。 帳戶層級的分析可為行銷和銷售團隊提供排定帳戶優先順序、最佳化參與策略，以及把握潛在商機所需的資料。

**KPI：**&#x200B;效率、生產力

[進一步瞭解如何啟用資料導向式決策](/help/blueprints/business-objectives/analytics-insights/enable-data-driven-decision-making.md)

### 改善銷售機會資格和轉換

透過評分、培育及個人化的後續追蹤，提高銷售機會品質並加速管道進度。 CJA B2B edition提供專為B2B銷售週期設計的延長13個月帳戶回顧期間，以便在整個帳戶歷程中實現準確的多點接觸歸因。

**KPI：**&#x200B;效率、遞增收入

[進一步瞭解如何改善銷售機會資格和轉換](/help/blueprints/business-objectives/qualification-sales-b2b/improve-lead-qualification-conversion.md)

## 戰術使用案例範例

以下案例說明此模式在實際中如何套用。

- **帳戶參與評分分析** — 透過帳戶在網路、電子郵件、事件和內容互動中的彙總參與，來衡量和排名帳戶，以識別高意圖帳戶以進行銷售追蹤
- **購買群組完整度追蹤** — 分析跨帳戶的購買群組構成，以找出角色涵蓋範圍的差距，並優先為不完整的購買群組取得潛在客戶
- **機會管道關聯** — 將行銷參與資料與機會階段進展建立關聯，以瞭解哪些行銷活動和接觸點可促進管道進展
- **多重接觸B2B歸因** — 將具有13個月回顧期間的歸因模型套用至整個B2B購買歷程（從首次接觸到結束交易）中的評分行銷接觸點
- **帳戶歷程對應** — 透過機會建立和關閉，識別共同路徑和摩擦點，將跨管道帳戶歷程從最初的認知視覺化
- **行銷活動對管道的影響** — 測量特定行銷活動對帳戶管道建立、機會提升和收入產生的影響
- **購買群組參與進度** — 追蹤購買群組參與分數如何隨時間演變，並將參與臨界值與機會結果建立關聯
- **以帳戶為基礎的內容效能** — 分析哪些內容資產和主題與特定帳戶區段、產業或購買群組角色產生共鳴
- **銷售和行銷一致性儀表板** — 建置共用儀表板，為行銷和銷售團隊提供帳戶參與度、管道狀況和收入歸因的統一檢視
- **啟用的帳戶區段** — 根據帳戶層級的分析建立B2B區段（例如，「沒有開啟機會的高度參與帳戶」），並發佈這些區段以供下游啟用

## 關鍵績效指標

以下KPI可協助評估此使用案例模式的成功。

| KPI | 說明 | 測量方法 |
| --- | --- | --- |
| 帳戶參與分數 | 彙總帳戶內所有聯絡人的參與量度 | 結合帳戶層級的網站造訪、電子郵件互動、事件出席和內容下載的計算量度 |
| 購買群組完整性 | 購買群組內所需角色的百分比 | 一段時間內追蹤的已填角色與每個購買群組所需角色總數的比率 |
| 受行銷影響的管道 | 行銷活動觸及的管道中的收入 | 相關帳戶聯絡人在歸因時段內具有行銷接觸點的機會值 |
| 帳戶對商機的轉換率 | 產生合格商機的參與客戶百分比 | 具有商機的帳戶除以定義期間內的參與帳戶總數 |
| 平均交易週期長度 | 從首次行銷接觸到成功關閉的時間 | 從第一個已歸因的接觸點到機會關閉日期的平均持續時間 |
| 行銷歸因收入 | 歸因於行銷接觸點的收入 | 透過歸因模型分銷，從具有行銷接觸的成功機會中獲得的收入 |
| 帳戶觸及率和滲透率 | 每個目標帳戶的參與聯絡人數目 | 每個帳戶具有行銷互動的不重複聯絡人，與已知聯絡人總數相比 |
| 購買角色的內容參與度 | 依購買群組角色區段的參與量度 | 依購買群組中的角色/角色劃分的頁面檢視、下載和逗留時間 |

## 應用程式

以下應用程式可用來實作此使用案例模式。

- **[!DNL Customer Journey Analytics]B2B edition** — 提供帳戶型連線、B2B特定資料檢視容器、帳戶層級工作區分析、購買群組分析、商機分析、B2B區段，以及具有延伸回顧期間的B2B歸因
- **[!DNL Real-Time CDP]B2B edition** — 提供B2B資料基礎，包括帳戶設定檔統一、B2B身分解析、B2B結構描述類別（Account、Opportunity、購買群組），以及用於擷取B2B參與資料的[!DNL Marketo Engage]整合

## 相關文件

以下資源提供實施此使用案例模式的其他資訊。

**[!DNL CJA]B2B edition**

- [CJA B2B edition概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)
- [CJA概觀](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-overview/cja-overview)
- [CJA護欄](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-admin/guardrails)

**連線**

- [連線總覽](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-connections/overview)
- [建立或編輯連線](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-connections/create-connection)
- [管理連線](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-connections/manage-connections)

**資料檢視**

- [資料檢視總覽](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dataviews/data-views)
- [建立或編輯資料檢視](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [元件設定概觀](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dataviews/component-settings/overview)
- [持續性設定](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dataviews/component-settings/persistence)
- [歸因設定](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dataviews/component-settings/attribution)
- [格式設定](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dataviews/component-settings/format)
- [衍生欄位](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dataviews/derived-fields)
- [工作階段設定](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dataviews/session-settings)

**Workspace和分析**

- [Workspace概觀](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/home)
- [建立專案](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/build-workspace-project/create-projects)
- [自由格式表格](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/visualizations/freeform-table/freeform-table)
- [流量視覺效果](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/visualizations/flow/flow)
- [流失視覺效果](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/visualizations/fallout/fallout-flow)
- [同類群組表格](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/visualizations/cohort-table/cohort-analysis)
- [歸因面板](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/panels/attribution)
- [共用專案](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/curate-share/share-projects)
- [排程專案](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/curate-share/send-schedule-files)
- [劃分維度](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/components/dimensions/t-breakdown-fa)

**元件**

- [篩選器概觀](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-components/cja-filters/filters-overview)
- [建立篩選器](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-components/cja-filters/create-filters)
- [計算量度概觀](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)
- [建立計算量度](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-workflow/cm-build-metrics)
- [註解概述](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-components/annotations/overview)
- [日期範圍](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/date-ranges/overview)

**對象**

- [受眾概述](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-components/audiences/audiences-overview)
- [建立及發佈對象](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-components/audiences/publish)
- [管理對象](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-components/audiences/manage)

**儀表板和計分卡**

- [建立行動計分卡](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dashboards/create-scorecard)
- [設定及組織計分卡](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/curate)
- [Adobe Analytics控制面板 — 執行指南](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dashboards/set-up-execs)

**引導式分析**

- [引導式分析概述](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/guided-analysis/overview)
- [funnel檢視](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/funnel/funnel)
- [趨勢檢視](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/guided-analysis/trends/usage)
- [保留檢視](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/guided-analysis/retention/retention-rates)

**[!DNL RT-CDP]B2B edition**

- [RT-CDP B2B edition概述](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/overview#702702)
- [B2B edition結構描述](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/rtcdp/schemas/b2b)
- [B2B來源概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/rtcdp/sources/b2b)

**AEP資料基礎**

- [XDM系統概覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/xdm/home)
- [來源概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sources/home)
- [Marketo Engage聯結器](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
- [Identity Service總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/identity/home)
- [沙箱概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sandbox/home)

**資料控管和生命週期**

- [資料控管概覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/home)
- [進階資料生命週期管理](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-lifecycle/home)

**教學課程與指南**

- [結構描述組合基本面](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/xdm/schema/composition)
- [計算屬性概述](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/computed-attributes/overview)
- [可觀察性深入分析概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/observability/home)
