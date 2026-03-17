---
title: 使用案例目錄
description: 依垂直、成熟度等級或實施模式瀏覽產業使用案例，以尋找Adobe Experience Platform歷程的正確起點。
doc-type: overview-page
exl-id: 7a3c2f1e-9b4d-4e6a-8f5c-2d1b3a4e7c9f
source-git-commit: 8ad59ff130dae13553f10049eb685cf557a73ead
workflow-type: tm+mt
source-wordcount: '1022'
ht-degree: 6%

---

# 使用案例目錄

探索[!DNL Adobe Experience Platform]和應用程式的產業使用案例。 依產業瀏覽，瞭解您垂直方向的使用案例、依成熟度層級瀏覽，以尋找適合您組織的起點，或依實施模式瀏覽，以瞭解適合您需求的技術方法。

每個使用案例會透過使用案例模式連結到詳細的實施指引，該模式會說明讓使用案例變成現實所需的功能鏈、決策點和設定步驟。

## 依產業瀏覽

>[!BEGINTABS]

>[!TAB 零售業]

零售組織使用[!DNL Adobe Experience Platform]將線上商店、實體地點和熟客方案的客戶資料整合為每位購物者的單一檢視。

| | 使用案例 | 說明 | 成熟度 | 圖樣 |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-product-recommendations.png" alt="個人化產品推薦" width="40"> | [個人化產品推薦](retail/retail-overview.md#personalized-product-recommendations) | 根據瀏覽和購買記錄顯示個人化產品 | [!BADGE 新增]{type=Informative} | [行為建議](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| <img src="assets/use-case-icons/icon-abandoned-cart.png" alt="捨棄的購物車" width="40"> | [放棄的購物車電子郵件復原](retail/retail-overview.md#abandoned-cart-email-recovery) | 傳送放棄購物車的個人化提醒 | [!BADGE 基礎]{type=Neutral} | [事件觸發訊息](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/icon-inventory-urgency.png" alt="詳細目錄急迫性" width="40"> | [詳細目錄型緊急行銷活動](retail/retail-overview.md#inventory-based-urgency-campaigns) | 產品詳細目錄不足時觸發即時警報 | [!BADGE 基礎]{type=Neutral} | [事件觸發訊息](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/icon-cross-sell-upsell.png" alt="交叉銷售向上銷售" width="40"> | [交叉銷售和追加銷售建議](retail/retail-overview.md#cross-sell-and-upsell-recommendations) | 在結帳時和電子郵件中顯示相關的交叉銷售和追加銷售產品 | [!BADGE 進階]{type=Caution} | [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) |
| <img src="assets/use-case-icons/icon-welcome-series.png" alt="歡迎系列" width="40"> | [新客戶歡迎系列](retail/retail-overview.md#new-customer-welcome-series) | 透過個人化建議自動執行多封電子郵件歡迎系列 | [!BADGE 新增]{type=Informative} | [多步驟協調歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/icon-price-drop.png" alt="價格下降" width="40"> | [價格下降警示](retail/retail-overview.md#price-drop-alerts) | 當願望清單或已檢視專案降價時通知客戶 | [!BADGE 基礎]{type=Neutral} | [事件觸發訊息](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/icon-replenishment.png" alt="補貨" width="40"> | [補充提醒](retail/retail-overview.md#replenishment-reminders) | 傳送定期購買消耗性產品的自動提醒 | [!BADGE 新增]{type=Informative} | [多步驟協調歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/icon-category-pages.png" alt="類別頁面" width="40"> | [個人化類別頁面](retail/retail-overview.md#personalized-category-pages) | 根據每位客戶的偏好以動態方式重新排序類別頁面 | [!BADGE 新增]{type=Informative} | [行為建議](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| <img src="assets/use-case-icons/icon-post-purchase.png" alt="購買後" width="40"> | [購買後後續行銷活動](retail/retail-overview.md#post-purchase-follow-up-campaigns) | 傳送服務秘訣、檢閱要求和相關產品建議 | [!BADGE 新增]{type=Informative} | [多步驟協調歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| | [VIP客戶專屬優惠方案](retail/retail-overview.md#vip-customer-exclusive-offers) | 提供專屬優惠方案，並搶先接觸高價值客戶 | [!BADGE 進階]{type=Caution} | [具有決策的跨頻道歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |
| | [無庫存通知](retail/retail-overview.md#out-of-stock-notifications) | 缺貨的產品可用時通知客戶 | [!BADGE 基礎]{type=Neutral} | [事件觸發訊息](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [社交校訂Personalization](retail/retail-overview.md#social-proof-personalization) | 根據客戶設定檔顯示個人化評論和評分 | [!BADGE 新增]{type=Informative} | [已知訪客網頁/應用程式Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) |

>[!TAB 金融服務]

金融服務使用案例即將推出。[檢視目前的Financial Services使用案例](financial-services/financial-services-overview.md)。

>[!TAB 醫療保健]

醫療保健使用案例即將推出。[檢視目前的醫療保健使用案例](healthcare/healthcare-overview.md)。

>[!TAB 汽車]

汽車使用案例即將推出。[檢視目前的汽車使用案例](automotive/automotive-overview.md)。

>[!TAB 旅遊業及旅館業]

旅行和酒店使用案例即將推出。[檢視目前的旅遊及旅館使用案例](travel-hospitality/travel-hospitality-overview.md)。

>[!TAB 電信]

電信使用案例即將推出。[檢視目前的電信使用案例](telecommunications/telecommunications-overview.md)。

>[!TAB 媒體與娛樂]

媒體與娛樂使用案例即將推出。[檢視目前的媒體與娛樂使用案例](media-entertainment/media-entertainment-overview.md)。

>[!TAB 保險]

保險使用案例即將推出。[檢視目前的保險使用案例](insurance/insurance-overview.md)。

>[!TAB B2B]

B2B使用案例即將推出。[檢視目前的B2B使用案例](b2b/b2b-overview.md)。

>[!ENDTABS]

## 依成熟度層級瀏覽

>[!BEGINTABS]

>[!TAB 基礎]

使用單通道傳送的基本且經驗證的模式。 對於開始其[!DNL Experience Platform]歷程的組織來說，是理想的起點。

| | 使用案例 | 產業 | 業務影響 | 圖樣 |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-abandoned-cart.png" alt="捨棄的購物車" width="40"> | [放棄的購物車電子郵件復原](retail/retail-overview.md#abandoned-cart-email-recovery) | 零售 | 購物車回覆率25-35% | [事件觸發訊息](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/icon-inventory-urgency.png" alt="詳細目錄急迫性" width="40"> | [詳細目錄型緊急行銷活動](retail/retail-overview.md#inventory-based-urgency-campaigns) | 零售 | 轉換率增加30-40% | [事件觸發訊息](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/icon-price-drop.png" alt="價格下降" width="40"> | [價格下降警示](retail/retail-overview.md#price-drop-alerts) | 零售 | 20-30%轉換率 | [事件觸發訊息](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [無庫存通知](retail/retail-overview.md#out-of-stock-notifications) | 零售 | 40-50%轉換率 | [事件觸發訊息](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |

>[!TAB 新增]

多頻道和多步驟模式，這些模式以AI驅動的個人化和協調歷程的基礎功能為基礎。

| | 使用案例 | 產業 | 業務影響 | 圖樣 |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-product-recommendations.png" alt="產品推薦" width="40"> | [個人化產品推薦](retail/retail-overview.md#personalized-product-recommendations) | 零售 | CTR增加20-30%，轉換率提升15-25% | [行為建議](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| <img src="assets/use-case-icons/icon-category-pages.png" alt="類別頁面" width="40"> | [個人化類別頁面](retail/retail-overview.md#personalized-category-pages) | 零售 | 參與率增加25-35% | [行為建議](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| <img src="assets/use-case-icons/icon-welcome-series.png" alt="歡迎系列" width="40"> | [新客戶歡迎系列](retail/retail-overview.md#new-customer-welcome-series) | 零售 | 40-50%參與率 | [多步驟協調歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/icon-replenishment.png" alt="補貨" width="40"> | [補充提醒](retail/retail-overview.md#replenishment-reminders) | 零售 | 30-40%重複購買率 | [多步驟協調歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/icon-post-purchase.png" alt="購買後" width="40"> | [購買後後續行銷活動](retail/retail-overview.md#post-purchase-follow-up-campaigns) | 零售 | 15-20%的評論率，10-15%的重複購買 | [多步驟協調歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| | [社交校訂Personalization](retail/retail-overview.md#social-proof-personalization) | 零售 | 轉換率增加10-15% | [已知訪客網頁/應用程式Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) |

>[!TAB 進階]

跨頻道協調，提供即時決策和AI驅動的優惠選擇，適合最複雜的客戶體驗。

| | 使用案例 | 產業 | 業務影響 | 圖樣 |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-cross-sell-upsell.png" alt="交叉銷售向上銷售" width="40"> | [交叉銷售和追加銷售建議](retail/retail-overview.md#cross-sell-and-upsell-recommendations) | 零售 | AOV增加25至75美元，收入增加10-15% | [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) |
| | [VIP客戶專屬優惠方案](retail/retail-overview.md#vip-customer-exclusive-offers) | 零售 | 來自VIP的50-70%參與率 | [具有決策的跨頻道歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |

>[!ENDTABS]

## 依實施模式瀏覽

>[!BEGINTABS]

>[!TAB 行銷活動管理與協調]

### 事件觸發式傳訊

透過即時的單一通道訊息回應即時行為事件。

| | 使用案例 | 產業 | 成熟度 | 業務影響 |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-abandoned-cart.png" alt="捨棄的購物車" width="40"> | [放棄的購物車電子郵件復原](retail/retail-overview.md#abandoned-cart-email-recovery) | 零售 | [!BADGE 基礎]{type=Neutral} | 購物車回覆率25-35% |
| <img src="assets/use-case-icons/icon-inventory-urgency.png" alt="詳細目錄急迫性" width="40"> | [詳細目錄型緊急行銷活動](retail/retail-overview.md#inventory-based-urgency-campaigns) | 零售 | [!BADGE 基礎]{type=Neutral} | 轉換率增加30-40% |
| <img src="assets/use-case-icons/icon-price-drop.png" alt="價格下降" width="40"> | [價格下降警示](retail/retail-overview.md#price-drop-alerts) | 零售 | [!BADGE 基礎]{type=Neutral} | 20-30%轉換率 |
| | [無庫存通知](retail/retail-overview.md#out-of-stock-notifications) | 零售 | [!BADGE 基礎]{type=Neutral} | 40-50%轉換率 |

### 多步驟協調歷程

引導客戶瞭解根據參與度和行為調整的多點觸控順序。

| | 使用案例 | 產業 | 成熟度 | 業務影響 |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-welcome-series.png" alt="歡迎系列" width="40"> | [新客戶歡迎系列](retail/retail-overview.md#new-customer-welcome-series) | 零售 | [!BADGE 新增]{type=Informative} | 40-50%參與率 |
| <img src="assets/use-case-icons/icon-replenishment.png" alt="補貨" width="40"> | [補充提醒](retail/retail-overview.md#replenishment-reminders) | 零售 | [!BADGE 新增]{type=Informative} | 30-40%重複購買率 |
| <img src="assets/use-case-icons/icon-post-purchase.png" alt="購買後" width="40"> | [購買後後續行銷活動](retail/retail-overview.md#post-purchase-follow-up-campaigns) | 零售 | [!BADGE 新增]{type=Informative} | 15-20%的評論率，10-15%的重複購買 |

### 具有決策的跨頻道歷程

在每個接觸點使用即時Offer Decisioning協調跨管道體驗。

| | 使用案例 | 產業 | 成熟度 | 業務影響 |
| --- | --- | --- | --- | --- |
| | [VIP客戶專屬優惠方案](retail/retail-overview.md#vip-customer-exclusive-offers) | 零售 | [!BADGE 進階]{type=Caution} | 來自VIP的50-70%參與率 |

>[!TAB Personalization]

### 行為建議

使用AI驅動模型，根據行為訊號呈現個人化內容和產品。

| | 使用案例 | 產業 | 成熟度 | 業務影響 |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-product-recommendations.png" alt="產品推薦" width="40"> | [個人化產品推薦](retail/retail-overview.md#personalized-product-recommendations) | 零售 | [!BADGE 新增]{type=Informative} | CTR增加20-30%，轉換率提升15-25% |
| <img src="assets/use-case-icons/icon-category-pages.png" alt="類別頁面" width="40"> | [個人化類別頁面](retail/retail-overview.md#personalized-category-pages) | 零售 | [!BADGE 新增]{type=Informative} | 參與率增加25-35% |

### Offer Decisioning

使用集中式決策邏輯，評估並選取適合每個客戶和內容的最佳優惠方案。

| | 使用案例 | 產業 | 成熟度 | 業務影響 |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-cross-sell-upsell.png" alt="交叉銷售向上銷售" width="40"> | [交叉銷售和追加銷售建議](retail/retail-overview.md#cross-sell-and-upsell-recommendations) | 零售 | [!BADGE 進階]{type=Caution} | AOV增加25至75美元，收入增加10-15% |

### 已知訪客網頁/應用程式Personalization

根據設定檔、偏好設定和瀏覽內容，為已識別的訪客個人化網頁和應用程式內容。

| | 使用案例 | 產業 | 成熟度 | 業務影響 |
| --- | --- | --- | --- | --- |
| | [社交校訂Personalization](retail/retail-overview.md#social-proof-personalization) | 零售 | [!BADGE 新增]{type=Informative} | 轉換率增加10-15% |

>[!ENDTABS]
