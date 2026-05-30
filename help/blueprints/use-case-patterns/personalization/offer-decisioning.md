---
title: Offer Decisioning
description: 瞭解如何使用集中式決定邏輯，跨頻道為設定檔選取次優優惠或內容。
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 8fd511b3-0200-41bf-aff1-e3f2a00a578e
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1640'
ht-degree: 5%

---

# Offer decisioning

本指南說明Offer Decisioning使用案例模式，此模式使用[!DNL Adobe Journey Optimizer] (AJO) Decisioning和[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)實作集中式優惠方案選擇邏輯，以決定跨管道每個客戶設定檔的次優優惠方案。 它專為需要瞭解此模式的功能、其支援的業務目標、其啟用的戰術使用案例以及所涉及的Adobe應用程式的解決方案架構師、行銷技術人員和實作工程師所設計。

此模式會將「要顯示的內容」決定與「顯示位置」頻道邏輯分離，以啟用跨電子郵件、網頁、行動應用程式和任何其他接觸點的一致最佳化優惠選擇。 AJO Decisioning會管理完整的優惠生命週期：優惠建立和目錄管理、適用性規則（誰可以看到每個優惠）、排名策略（如何在合格優惠中進行選取）、位置（優惠出現的位置）和決定策略（將所有內容繫結在一起）。

## 使用案例模式

本節說明Offer Decisioning的執行計畫和模式定義。

**Offer Decisioning**

使用集中式決定邏輯，跨管道為設定檔選取次優優惠或內容。

**執行計畫：**&#x200B;對象評估>優惠資格>排名策略>決定執行>傳遞>報告

## 使用案例概述

組織經常需要在互動的時刻向每位客戶提供最相關的優惠方案、促銷活動或獎勵。 無論互動發生在電子郵件促銷活動、網站首頁、行動應用程式中，還是多步驟歷程中的決策點，挑戰都相同：根據客戶身分、客戶資格，以及最有可能帶來所要結果的選件，從可用選項的目錄中選取最佳選件。

Offer Decisioning可透過在AJO的決策管理引擎中集中所有優惠方案選擇邏輯來解決此問題。 決定引擎不會將優惠指派硬式編碼至個別行銷活動或管道，而是評估每個設定檔的屬性、對象成員資格和內容訊號，以即時決定最佳優惠。 這種集中化可確保同一個客戶無論透過哪個管道進行互動，都能獲得一致且最佳化的優惠方案。

此模式在範圍上與已知訪客的網頁/應用程式個人化不同 — offer decisioning不受通道限制，而且是集中式，而已知訪客的個人化著重於數位介面個人化。 它與目錄模型中的行為建議不同 — 當符合資格的專案集受商業規則、資格限制或法規要求（促銷活動、金融產品、獎勵）控管時，請使用Offer Decisioning。 當專案集很大、持續變更，且選擇是由行為相似度或相似性訊號（產品目錄、內容資料庫）驅動時，使用行為建議。

## 主要業務目標

此使用案例模式支援下列業務目標。

**[提供個人化的客戶體驗](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**
根據個別偏好設定、行為和生命週期階段量身打造內容、選件和訊息。
**KPI：**&#x200B;參與度、轉換率、客戶滿意度(CSAT)

**[推動交叉銷售和追加銷售收入](../../business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)**
根據行為和購買記錄，向現有客戶推廣補充性和優質產品或服務。
**KPI：**&#x200B;向上銷售/交叉銷售%、遞增收入、客戶期限值

**[提高客戶忠誠度和期限值](../../business-objectives/revenue-monetization/increase-customer-loyalty-lifetime-value.md)**
透過忠誠計畫、獎勵和個人化參與，深化客戶關係並最大化長期價值。
**KPI：**&#x200B;客戶期限值、保留率、向上銷售/交叉銷售%

## 戰術使用案例範例

下列案例說明如何在實務中套用Offer Decisioning。

- 電子郵件行銷活動中的下一個最佳優惠方案 — 選取傳送時每個收件者的最相關促銷活動
- 網站上的即時促銷橫幅 — 決策功能會根據訪客的設定檔，在頁面載入時選取優惠方案
- 個人化應用程式內卡，為使用者的生命週期階段提供最佳獎勵
- 跨頻道優惠方案一致性 — 相同的決策邏輯提供電子郵件、Web和推播，讓客戶看到統一的優惠方案體驗
- 根據客戶價值層級選擇動態優惠券或折扣（例如，高價值客戶會獲得優惠方案）
- 根據目前訂閱層級的產品升級或追加銷售選件選擇
- 根據層級和活動記錄的熟客獎勵優惠個人化

## 關鍵績效指標

下列KPI有助於評估Offer Decisioning實作的成效。

| KPI | 說明 | 測量方法 |
| --- | --- | --- |
| 優惠接受率 | 導致點選、贖回或轉換的已傳遞優惠方案的百分比 | 優惠點按或贖回/已傳遞的優惠總數 |
| 優惠選擇分佈 | 在所有決定中選取的每個優惠比例 | 每個優惠計數/呈現的決策總數 |
| 遞補率 | 未符合個人化優惠條件且未提供遞補優惠的決策百分比 | 遞補曝光次數/決定總數 |
| 轉換率 | 完成所需動作（購買、註冊、贖回）的優惠方案收件者百分比 | 轉換/選件曝光次數 |
| 遞增收入 | 歸因於決策所選優惠與控制組或遞補優惠的收入 | 個人化優惠方案收入 — 遞補/控制項收入 |
| 跨管道一致性分數 | 在定義的視窗內，跨多個管道接收相同優惠的個人檔案百分比 | 一致優惠/多頻道曝光總數 |
| 優惠點進率 | 導致點按的優惠方案曝光百分比 | 優惠點按數/優惠閱聽 |

## 應用程式

在此使用案例模式中使用以下Adobe應用程式。

- **[!DNL Adobe Journey Optimizer] (AJO)** — 優惠方案建立、適用性規則、排名策略、位置和決定政策的決定管理引擎；優惠方案傳遞的頻道設定和訊息編寫；行銷活動和歷程執行
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** — 優惠方案適用性區段的對象評估；適用性和排名中使用的設定檔資料和計算屬性
- **[!DNL Adobe Experience Platform] (AEP)** — 支援AJO和RT-CDP的統一設定檔存放區、身分解析和資料基礎

## 相關文件

下列資源提供在此使用案例模式中使用的元件的其他詳細資料。

### 決策管理

- [決策管理概觀](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [建立產品建議放置環境](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [建立決定規則](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [建立個人化優惠方案](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [建立後備產品建議](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [建立集合](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [建立集合限定詞](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-tags)
- [建立決定](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [排名策略](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### 選件傳送

- [在訊息中傳遞優惠方案](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [使用Edge Decisioning API傳遞優惠方案](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/edge-decisioning-api)
- [使用Decisioning API傳遞優惠方案](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/decisioning-api)

### 管道設定

- [開始使用電子郵件設定](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [電子郵件表面設定](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [委派子網域](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [設定推播通知頻道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [設定簡訊頻道](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)

### 訊息製作與個人化

- [設計電子郵件內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [新增個人化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization語法](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [動態內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [使用內容範本](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [預覽和測試您的內容](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### 行銷活動和歷程

- [開始使用行銷活動](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [建立行銷活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [開始使用歷程](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/journey)

### 內容實驗

- [開始使用內容實驗](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [建立內容實驗](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)

### 對象和細分

- [Segmentation Service概述](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/home)
- [區段產生器UI指南](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/ui/segment-builder)
- [串流區段](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [邊緣分段](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/methods/edge-segmentation)

### 設定檔與身分

- [Identity Service總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/identity/home)
- [合併原則概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/merge-policies/overview)
- [計算屬性概述](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/computed-attributes/overview)
- [Customer AI概述](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/intelligent-services/customer-ai/overview)

### 資料模式與收集

- [XDM系統概覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/xdm/home)
- [網頁SDK概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/web-sdk/home)
- [設定資料串流](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/datastreams/configure)

### 報告與分析

- [行銷活動全域報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [歷程全域報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [使用Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [CJA概觀](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-overview/cja-overview)
- [Analysis Workspace概觀](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/home)

### 資料控管和生命週期

- [資料控管概覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/home)
- [資料使用標籤概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/labels/overview)
- [進階資料生命週期管理概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-lifecycle/home)
- [Journey Optimizer中的同意](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)

### 護欄

- [Journey Optimizer護欄](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/get-started/guardrails)
- [即時客戶個人檔案護欄](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/guardrails)

### 教學課程

- [決定管理API快速入門](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/getting-started)
