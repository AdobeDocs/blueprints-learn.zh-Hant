---
title: 已知訪客網頁/應用程式Personalization
description: 瞭解如何根據即時設定檔和區段會籍，將個人化內容、優惠或促銷活動傳遞給已識別的訪客。
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 585adc0e-f528-4a09-b931-ef6b45fa8ec8
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1819'
ht-degree: 4%

---

# 已知訪客的網頁/應用程式個人化

本指南說明已知訪客的網頁/應用程式個人化使用案例模式，此模式使用[!DNL Adobe Journey Optimizer] (AJO)和[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)將個人化內容傳送給跨數位表面的已識別訪客。 它專為需要瞭解此模式的功能、其支援的業務目標、其啟用的戰術使用案例以及所涉及的Adobe應用程式的解決方案架構師、行銷技術人員和實作工程師所設計。

已知訪客的網頁/應用程式個人化是已驗證數位體驗的主要個人化模式。 與只仰賴工作階段內行為訊號的匿名訪客個人化不同，此模式會利用完整的統一設定檔：歷史行為資料、區段會籍、忠誠度等級、購買歷史記錄、生命週期階段、運算屬性和傾向分數。 它支援跨網頁（透過AJO網路頻道）、行動應用程式內訊息和內容卡片的個人化。

## 使用案例模式

本節說明核心模式及其執行計畫。

**已知訪客的網頁/應用程式個人化**

根據跨網路、行動應用程式內和內容卡表面的即時設定檔和區段會籍，將個人化內容、優惠或促銷活動提供給已識別的訪客。

**執行計畫：**&#x200B;對象評估> Personalization Decisioning >表面/頻道設定>內容傳送>曝光追蹤>報告

## 使用案例概述

擁有已驗證數位屬性的組織（電子商務網站、銀行入口網站、訂閱服務、忠誠度計畫、行動應用程式）需要提供可反映每位客戶與品牌關係的個人化體驗。 當訪客登入或透過身分解析被識別時，平台可以存取其完整的統一設定檔，並根據其特定屬性、行為和偏好設定提供量身打造的內容。

此模式處理已識別訪客進入Web屬性或開啟行動應用程式的情況，系統必須根據即時設定檔資料和對象會籍，決定要顯示的最佳內容、選件或促銷活動。 個人化決策會在邊緣以毫秒為單位進行，啟用次秒內容傳送而不會出現可察覺的延遲。

此模式支援確定性個人化（其中特定內容對應至特定受眾區段）和動態決策（其中AJO決策會評估適用性規則和排名策略，以選取每個設定檔的最佳內容）。 它橫跨多個數位表面（網頁、行動應用程式內訊息和內容卡），實現客戶數位歷程中一致的個人化。

## 主要業務目標

此使用案例模式支援下列業務目標。

### 提供個人化的客戶體驗

根據個別偏好設定、行為和生命週期階段量身打造內容、選件和訊息。 如需詳細資訊，請參閱[提供個人化客戶體驗](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)。

**KPI：**&#x200B;參與度、轉換率、客戶滿意度(CSAT)

### 增加網站參與度

透過相關體驗，改善網站逗留時間、每個工作階段頁面數以及與網頁內容的互動。 如需詳細資訊，請參閱[增加網站參與度](../../business-objectives/acquisition-growth/increase-website-engagement.md)。

**KPI：**&#x200B;網頁逗留時間、參與度、轉換率

### 提高行動應用程式的參與度

透過個人化的應用程式內體驗，推動每日主動使用、功能採用和應用程式內轉換。

**KPI：**&#x200B;參與度、保留率、轉換率

## 戰術使用案例範例

以下是此模式的常見戰術實施：

- 依忠誠度等級或生命週期階段劃分的首頁主圖個人化 — 根據客戶是新客戶、活躍客戶、高風險客戶還是VIP客戶，顯示不同的主圖橫幅
- 根據購買歷史記錄的產品建議輪播 — 使用過去的購買資料和產品相似性分數來顯示相關的產品建議
- 依客戶細分的個人化促銷橫幅 — 針對高價值、高風險和新的客戶細分顯示不同的促銷活動
- 根據功能採用為行動使用者提供的應用程式內訊息 — 根據使用者的使用模式來引導使用者瞭解未充分利用的功能
- 在帳戶控制面板上具有個人化優惠的內容卡 — 根據客戶設定檔量身打造的持續、不允許的優惠
- 根據客戶層級顯示個人化定價或折扣 — 向熟客方案會員顯示層級特定定價或專屬折扣
- 根據擁有的產品的交叉銷售建議Widget — 根據目前的產品組合提出補充產品或服務的建議
- 根據興趣進行個人化導覽或內容排序 — 根據示範的偏好重新排序內容模組或導覽元素

## 關鍵績效指標

下列KPI有助於評估此使用案例模式的成效。

| KPI | 測量方法 | 基準指引 |
| --- | --- | --- |
| Personalization參與率 | 個人化內容元素的點選次數和互動除以曝光數 | 個人化內容的效能應比預設內容高20-50% |
| 轉換率提升 | 個人化體驗與控制/預設體驗的轉換率 | 目標比非個人化體驗提升10-30% |
| 點進率(CTR) | 個人化CTA、優惠和建議的點按次數除以曝光數 | 監視每個介面（網頁、應用程式內、內容卡）和每個區段 |
| 每次造訪帶來的收入 | 歸因於具有個人化體驗之工作階段的收入 | 比較個人化與非個人化訪客同類群組 |
| 內容卡互動率 | 與曝光數相關的內容卡點選數與關閉數 | 依卡片型別和對象區段追蹤 |
| 應用程式內訊息參與度 | 與曝光數相關的應用程式內訊息互動（CTA點選、解除） | 比較對象區段和訊息型別 |
| 頁面逗留時間 | 個人化內容與預設頁面平均逗留時間 | 個人化頁面應顯示增加的暫留時間 |
| 優惠接受率 | 導致轉換事件的決策選取優惠方案百分比 | 追蹤每個選件、每個位置和每個排名策略 |

## 應用程式

在此使用案例模式中使用以下應用程式。

- **[!DNL Adobe Journey Optimizer] (AJO)** — Web頻道設定、應用程式內頻道設定、內容卡片頻道設定、決策（優惠方案選擇和排名）、訊息製作（個人化內容建立）、行銷活動執行、內容實驗和報告
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** — 對象評估（邊緣、串流和批次）、透過Edge Network的即時設定檔查詢、使用運算屬性和傾向分數擴充設定檔
- **[!DNL Adobe Experience Platform] (AEP)** — 設定檔存放區、身分服務、Web SDK、行動SDK、資料流設定、邊緣網路傳遞

## 相關文件

下列資源提供本指南參考之技術和設定的其他詳細資訊。

### Web頻道個人化

- [開始使用網路頻道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [建立網站體驗](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [Web頻道設定](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/web-configuration)

### 應用程式內和內容卡頻道

- [應用程式內頻道概觀](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/get-started-in-app)
- [應用程式內頻道必要條件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/inapp-configuration)
- [建立應用程式內訊息](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/create-in-app)
- [內容卡頻道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/get-started-content-card)
- [內容卡設定](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/content-card-configuration)
- [建立內容卡](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/create-content-card)

### 決定管理

- [決策管理概觀](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [建立產品建議放置環境](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [建立決定規則](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [建立個人化優惠方案](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [建立後備產品建議](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [建立集合](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [建立決定](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [排名策略](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)
- [在訊息中傳遞優惠方案](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

### Personalization與內容

- [新增個人化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization語法](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [輔助函式](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [動態內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [使用內容範本](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [使用內容片段](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)

### 對象和細分

- [Segmentation Service概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [區段產生器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [邊緣分段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [串流區段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Profile Query Language參考](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### 身分和設定檔

- [Identity Service總覽](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [身分名稱空間概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/identity/features/namespaces)
- [身分識別圖連結規則](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/identity-linking-logic)
- [設定檔概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [合併原則概觀](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

### 資料收集和SDK

- [網頁SDK概觀](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [安裝Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/install/overview)
- [行動SDK概觀](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [設定資料串流](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Edge Network伺服器API總覽](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)

### 行銷活動和實驗

- [開始使用行銷活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [建立行銷活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [開始使用內容實驗](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [建立內容實驗](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [內容實驗報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)

### 計算的屬性和擴充

- [計算屬性概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [計算屬性UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/ui)
- [Customer AI概述](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview)

### 報告與分析

- [行銷活動即時報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [行銷活動全域報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [AJO + CJA整合指南](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [CJA概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Analysis Workspace概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)

### 治理和隱私權

- [資料控管概覽](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Journey Optimizer中的同意](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)
- [進階資料生命週期管理概觀](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)

### 護欄

- [Journey Optimizer護欄](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [即時客戶個人檔案護欄](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Identity Service護欄](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)
