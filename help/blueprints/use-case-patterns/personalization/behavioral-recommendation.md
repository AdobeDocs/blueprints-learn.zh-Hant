---
title: 行為建議
description: 瞭解如何使用選擇策略和排名模型來產生專案和內容推薦。
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: db16e773-e0da-46c4-9fa5-d16f04feb46b
source-git-commit: 9ea30e48ec0fade2f9a97b185e35fbfa93f49c43
workflow-type: tm+mt
source-wordcount: '1652'
ht-degree: 5%

---

# 行為建議

本指南說明行為建議使用案例模式，此模式使用[!DNL Adobe Journey Optimizer] (AJO) Decisioning、[!DNL Real-Time Customer Data Platform] (RT-CDP)和[!DNL Adobe Experience Platform] (AEP)來跨網路、行動應用程式和電子郵件通道提供個人化建議體驗。 它專為需要瞭解此模式的功能、其支援的業務目標、其啟用的戰術使用案例以及所涉及的Adobe應用程式的解決方案架構師、行銷技術人員和實作工程師所設計。

行為建議使用行為訊號（產品檢視、購買、內容互動、搜尋查詢）與AJO Decisioning選擇策略和排名模型結合，產生專案層級或內容層級的建議。 與Offer Decisioning （使用適用性規則和業務限制來控制一組有限的優惠、促銷活動或獎勵）不同，此模式適用於持續變更的大型專案目錄（產品、文章、影片），其中的選擇是由行為相關性訊號驅動，而非受控制的適用性。

## 使用案例模式

**行為建議**

使用AJO Decisioning選擇策略和排名模型，根據行為訊號產生專案層級或內容層級的建議，以提供內容相關內容。

**執行計畫：**&#x200B;行為訊號擷取>決策策略評估>建議傳送>報告

## 使用案例概述

擁有產品目錄、內容庫或媒體庫的組織需要根據訪客的行為歷史記錄和工作階段中的活動，向每位訪客呈現最相關的專案。 無論是首頁上的「為您推薦」輪播、產品詳細資料頁面上的交叉銷售Widget，或內嵌在電子郵件促銷活動中的產品推薦，基本挑戰都相同：將每位訪客的行為設定檔與目錄中最相關的專案進行比對，然後在適當的時間在適當的管道中提供這些推薦。

此模式可透過[!DNL Web SDK]或[!DNL Mobile SDK]即時擷取行為訊號、透過AJO Decisioning選擇策略處理這些訊號（這些策略會將專案屬性與行為內容相結合），以及透過Web、應用程式內或電子郵件通道傳遞建議專案，藉此解決該挑戰。 排名模型可根據公式（例如依類別相關性分數排序）或AI排名（例如個人化推薦模型）。 此模式也會透過設定遞補建議來處理沒有行為歷史記錄的新訪客的冷啟動案例。

此模式的目標受眾包括電子商務銷售團隊、內容個人化團隊和數位體驗團隊，這些團隊尋求透過真實使用者行為驅動的個人化建議，改善參與度、轉換和平均訂單價值。

## 主要業務目標

此使用案例模式支援下列業務目標。

### 推動交叉銷售和追加銷售收入

[推動交叉銷售和追加銷售收入](../../business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)

根據行為和購買記錄，向現有客戶推廣補充性和優質產品或服務。

**KPI：**&#x200B;向上銷售/交叉銷售%、遞增收入、客戶期限值

### 提高轉換率

[提高轉換率](../../business-objectives/revenue-monetization/increase-conversion-rates.md)

提高完成所需動作（例如購買、註冊或提交表單）的訪客和潛在客戶的百分比。

**KPI：**&#x200B;轉換率、潛在客戶轉換、每個潛在客戶的成本

### 提供個人化的客戶體驗

[提供個人化的客戶體驗](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)

根據個別偏好設定、行為和生命週期階段量身打造內容、選件和訊息。

**KPI：**&#x200B;參與度、轉換率、客戶滿意度(CSAT)

## 戰術使用案例範例

以下是此模式的常見戰術實施：

- 產品詳細資料頁面上的產品交叉銷售Widget （「客戶也購買了」）
- 根據瀏覽歷史記錄，首頁上的「為您推薦」輪播
- 根據閱讀行為在媒體網站上提供內容建議
- 結合類似專案Widget的「最近檢視」
- 購買後補充產品推薦
- 根據行為相似性以電子郵件傳送產品建議
- 根據工作階段中瀏覽行為的類別特定建議
- 根據行為訊號重新排名的搜尋結果

## 關鍵績效指標

下列KPI有助於評估行為建議實作的效益。

| KPI | 測量方法 |
| --- | --- |
| 建議點進率(CTR) | 建議專案的點按次數除以建議曝光數 |
| 建議轉換率 | 建議點選數的購買或所需動作除以建議點選總數 |
| 受Recommendations影響的收入 | 來自至少包含一個建議導向產品的訂單的總收入 |
| 平均訂購值(AOV)提升度 | 參與建議工作階段與未參與工作階段的AOV增加 |
| 每個訂單的專案 | 建議參與工作階段的每張訂單專案數 |
| 建議涵蓋範圍 | 收到個人化（非備援）建議的合格頁面檢視或工作階段百分比 |
| 冷啟動後援率 | 因行為記錄不足而由遞補邏輯提供的建議要求百分比 |

## 應用程式

在此使用案例模式中使用以下應用程式。

- **[!DNL Adobe Journey Optimizer] (AJO)決策** — 選擇策略、排名模型、專案目錄和決策原則，用於評估行為訊號並傳回每個訪客最相關的專案
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** — 行為設定檔資料累積、建議範圍的對象評估，以及行為相似性評分的計算屬性
- **[!DNL Adobe Experience Platform] (AEP)** — 透過[!DNL Web SDK]和[!DNL Mobile SDK]的行為事件擷取，[!DNL Edge Network]處理，事件和目錄資料的XDM結構描述管理

## 相關文件

下列資源提供在此模式中使用的技術和功能的更多詳細資料。

### 決定管理

- [決策管理概觀](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [建立產品建議放置環境](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [建立決定規則](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [建立個人化優惠方案](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [建立後備產品建議](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [建立集合](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [建立集合限定詞](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-tags)
- [建立決定](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [排名策略](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)
- [在訊息中傳遞優惠方案](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [使用Edge Decisioning API傳遞優惠方案](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/edge-decisioning-api)

### 資料收集與網頁/行動SDK

- [網頁SDK概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/web-sdk/home)
- [安裝Web SDK](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/web-sdk/install/overview)
- [行動SDK概觀](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [設定資料串流](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/datastreams/configure)
- [Edge Network伺服器API總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/edge-network-server-api/overview)

### XDM和資料模型化

- [XDM系統概覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/xdm/home)
- [結構描述組合基本面](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/xdm/schema/composition)
- [建立資料集](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/catalog/datasets/create)
- [定義兩個結構描述之間的關係](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/xdm/tutorials/relationship-api)

### 身分和設定檔

- [Identity Service總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/identity/home)
- [身分名稱空間概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/identity/features/namespaces)
- [合併原則概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/merge-policies/overview)
- [即時客戶個人檔案總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/home)

### 對象和細分

- [Segmentation Service概述](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/home)
- [區段產生器UI指南](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/ui/segment-builder)
- [串流區段](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [邊緣分段](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/methods/edge-segmentation)

### 計算的屬性和設定檔擴充

- [計算屬性概述](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/computed-attributes/overview)
- [計算屬性UI指南](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/computed-attributes/ui)
- [Customer AI概述](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/intelligent-services/customer-ai/overview)

### 管道設定

- [開始使用電子郵件設定](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [設定頻道介面](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [委派子網域](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)

### 訊息製作與個人化

- [設計電子郵件內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [新增個人化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization語法](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [動態內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [使用內容範本](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/content-management/content-templates/content-templates)

### 報告與分析

- [行銷活動全域報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [歷程全域報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [使用Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [CJA概觀](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-overview/cja-overview)
- [Analysis Workspace概觀](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/home)
- [計算量度概觀](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)

### 資料控管和生命週期

- [資料控管概覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/home)
- [資料使用標籤概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/labels/overview)
- [進階資料生命週期管理概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-lifecycle/home)
- [資料集有效期](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-lifecycle/ui/dataset-expiration)

### 監視和可觀察性

- [可觀察性深入分析概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/observability/home)
- [警報概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/observability/alerts/overview)

### 護欄

- [Journey Optimizer護欄](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/get-started/guardrails)
- [即時客戶個人檔案護欄](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/guardrails)
- [擷取護欄](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/ingestion/guardrails)
- [Identity Service護欄](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/identity/guardrails)

### 教學課程與指南

- [來源概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sources/home)
- [標籤總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/tags/home)
- [同意和偏好設定欄位群組](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/xdm/field-groups/profile/consents)
