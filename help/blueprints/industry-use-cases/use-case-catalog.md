---
title: 使用案例目錄
description: 依垂直方向瀏覽產業使用案例，以尋找Adobe Experience Platform歷程的正確起點，並附上實作模式與業務目標的連結。
doc-type: overview-page
exl-id: 38593314-b8c9-49f6-85db-a4345ec444e7
source-git-commit: 9d1ba8ce3fed83b1bd2b2615309ae7e3683e14f1
workflow-type: tm+mt
source-wordcount: '2379'
ht-degree: 100%

---

# 使用案例目錄

產業使用案例顯示特定垂直產業的組織如何套用Adobe Experience Platform和應用程式來取得可衡量的業務成果。 每個使用案例都描述具體的業務情境、其預期影響，以及提供詳細實作指引的[使用案例模式](/help/blueprints/use-case-patterns/overview.md)的連結。

依產業瀏覽以尋找與貴組織相關的使用案例，然後遵循實施參考的模式連結，包括決定指引、功能鏈和Experience League檔案。

| 產業 | 主要主題 |
| --- | --- |
| [汽車](automotive/automotive-overview.md) | 車輛購買歷程、服務生命週期、連線車輛體驗、車主忠誠度 |
| [B2B](b2b/b2b-overview.md) | 帳戶式行銷、銷售機會評分、管道加速、客戶擴展 |
| [金融服務](financial-services/financial-services-overview.md) | 產品推薦、流失預防、終生階段優惠、詐騙個人化 |
| [醫療保健](healthcare/healthcare-overview.md) | 預約管理、藥物依從性、患者入門、護理協調 |
| [保險](insurance/insurance-overview.md) | 保單續約、索賠體驗、風險預防、交叉銷售最佳化 |
| [媒體與娛樂](media-entertainment/media-entertainment-overview.md) | 內容推薦、訂閱保留、試用轉換、跨平台參與 |
| [零售業](retail/retail-overview.md) | 產品個人化、購物車回覆、交叉銷售最佳化、忠誠度參與 |
| [電信](telecommunications/telecommunications-overview.md) | 裝置升級、防止流失、計畫最佳化、網路參與 |
| [旅遊業及旅館業](travel-hospitality/travel-hospitality-overview.md) | 預訂個人化、放棄復原、忠誠度方案、季節性行銷活動 |

## 使用案例如何連結至實作指引

每個使用案例都連結到&#x200B;**使用案例模式** — 一種可重複的實作方法，可描述讓使用案例變成現實所需的功能鏈、決策點和設定步驟。 使用案例模式進而與[關鍵業務目標](/help/blueprints/business-objectives/overview.md)連結，協助您將實作工作與策略性結果保持一致。

```
Industry Use Case → Use Case Pattern → Key Business Objective
```

## 依產業瀏覽

>[!BEGINTABS]

>[!TAB 零售業]

| | 使用案例 | 說明 | 成熟度 | 圖樣 |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/retail/icon-abandoned-cart.png" alt="捨棄的購物車" width="40"> | [放棄的購物車電子郵件復原](retail/retail-overview.md#abandoned-cart-email-recovery) | 傳送放棄購物車的個人化提醒 | [!BADGE 基礎]{type=Neutral} | [事件觸發訊息](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/retail/icon-inventory-urgency.png" alt="詳細目錄急迫性" width="40"> | [詳細目錄型緊急行銷活動](retail/retail-overview.md#inventory-based-urgency-campaigns) | 產品詳細目錄不足時觸發即時警報 | [!BADGE 基礎]{type=Neutral} | [事件觸發訊息](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/retail/icon-price-drop.png" alt="價格下降" width="40"> | [價格下降警示](retail/retail-overview.md#price-drop-alerts) | 當願望清單或已檢視專案降價時通知客戶 | [!BADGE 基礎]{type=Neutral} | [事件觸發訊息](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [無庫存通知](retail/retail-overview.md#out-of-stock-notifications) | 缺貨的產品可用時通知客戶 | [!BADGE 基礎]{type=Neutral} | [事件觸發訊息](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/retail/icon-product-recommendations.png" alt="產品推薦" width="40"> | [個人化產品推薦](retail/retail-overview.md#personalized-product-recommendations) | 根據瀏覽和購買記錄顯示個人化產品 | [!BADGE 新增]{type=Informative} | [行為建議](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| <img src="assets/use-case-icons/retail/icon-category-pages.png" alt="類別頁面" width="40"> | [個人化類別頁面](retail/retail-overview.md#personalized-category-pages) | 根據客戶偏好設定動態地重新排序類別頁面 | [!BADGE 新增]{type=Informative} | [行為建議](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| <img src="assets/use-case-icons/retail/icon-welcome-series.png" alt="歡迎系列" width="40"> | [新客戶歡迎系列](retail/retail-overview.md#new-customer-welcome-series) | 透過個人化建議自動執行多電子郵件歡迎系列 | [!BADGE 新增]{type=Informative} | [多步驟協調歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/retail/icon-replenishment.png" alt="補貨" width="40"> | [補充提醒](retail/retail-overview.md#replenishment-reminders) | 傳送定期購買消耗性產品的自動提醒 | [!BADGE 新增]{type=Informative} | [多步驟協調歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/retail/icon-post-purchase.png" alt="購買後" width="40"> | [購買後後續行銷活動](retail/retail-overview.md#post-purchase-follow-up-campaigns) | 傳送服務秘訣、檢閱要求和相關產品建議 | [!BADGE 新增]{type=Informative} | [多步驟協調歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| | [社交校訂Personalization](retail/retail-overview.md#social-proof-personalization) | 根據客戶設定檔顯示個人化評論和評分 | [!BADGE 新增]{type=Informative} | [已知訪客網頁/應用程式Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) |
| <img src="assets/use-case-icons/retail/icon-cross-sell-upsell.png" alt="交叉銷售向上銷售" width="40"> | [交叉銷售和追加銷售建議](retail/retail-overview.md#cross-sell-and-upsell-recommendations) | 在結帳時和電子郵件中顯示相關的交叉銷售和追加銷售產品 | [!BADGE 進階]{type=Caution} | [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) |
| | [VIP客戶專屬優惠方案](retail/retail-overview.md#vip-customer-exclusive-offers) | 提供專屬優惠方案，並搶先接觸高價值客戶 | [!BADGE 進階]{type=Caution} | [具有決策的跨頻道歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |

>[!TAB 汽車]

| | 使用案例 | 說明 | 成熟度 | 圖樣 |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/automotive/icon-service-reminders.png" alt="服務提醒" width="40"> | [服務約會提醒](automotive/automotive-overview.md#service-appointment-reminders) | 根據車輛里程和服務歷史記錄傳送個人化服務提醒 | [!BADGE 基礎]{type=Neutral} | [事件觸發訊息](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/automotive/icon-recall-notifications.png" alt="撤回通知" width="40"> | [車輛召回通知](automotive/automotive-overview.md#vehicle-recall-notifications) | 使用服務排程選項傳送個人化召回通知 | [!BADGE 基礎]{type=Neutral} | [事件觸發訊息](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/automotive/icon-test-drive.png" alt="試用版" width="40"> | [測試磁碟機排程](automotive/automotive-overview.md#test-drive-scheduling) | 使用經銷商建議啟用個人化測試驅動程式排程 | [!BADGE 基礎]{type=Neutral} | [事件觸發訊息](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/automotive/icon-model-launch.png" alt="模型啟動" width="40"> | [新模型啟動促銷活動](automotive/automotive-overview.md#new-model-launch-campaigns) | 根據目前的車輛和偏好設定，鎖定對新車型感興趣的客戶 | [!BADGE 基礎]{type=Neutral} | [批次傳出訊息啟用](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md) |
| <img src="assets/use-case-icons/automotive/icon-trade-in.png" alt="以舊換新" width="40"> | [折價促銷活動](automotive/automotive-overview.md#trade-in-value-campaigns) | 主動為準備升級的客戶提供折價評估 | [!BADGE 新增]{type=Informative} | [多步驟協調歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/automotive/icon-parts-accessories.png" alt="零件配件" width="40"> | [零件與配件建議](automotive/automotive-overview.md#parts-and-accessories-recommendations) | 根據車輛型號和擁有時間推薦零件和配件 | [!BADGE 新增]{type=Informative} | [行為建議](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| <img src="assets/use-case-icons/automotive/icon-warranty.png" alt="保固" width="40"> | [保固與延長服務計畫](automotive/automotive-overview.md#warranty-and-extended-service-plans) | 根據車輛使用時間，在最佳時間建議保固和服務計畫 | [!BADGE 新增]{type=Informative} | [多步驟協調歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/automotive/icon-connected-car.png" alt="連線汽車" width="40"> | [連線汽車功能啟用](automotive/automotive-overview.md#connected-car-feature-activation) | 根據車輛功能提供個人化的連線車輛功能建議 | [!BADGE 新增]{type=Informative} | [多步驟協調歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/automotive/icon-dealer-network.png" alt="經銷商網路" width="40"> | [經銷商網路協調](automotive/automotive-overview.md#dealer-network-coordination) | 根據位置和偏好設定啟用個人化經銷商推薦 | [!BADGE 新增]{type=Informative} | [已知訪客網頁/應用程式Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) |
| <img src="assets/use-case-icons/automotive/icon-vehicle-purchase.png" alt="車輛購買" width="40"> | [車輛購買歷程Personalization](automotive/automotive-overview.md#vehicle-purchase-journey-personalization) | 個人化從研究到購買的車輛購買歷程 | [!BADGE 進階]{type=Caution} | [具有決策的跨頻道歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |
| <img src="assets/use-case-icons/automotive/icon-financing.png" alt="財務" width="40"> | [財務與保險優惠方案](automotive/automotive-overview.md#financing-and-insurance-offers) | 根據信用設定檔呈現個人化融資和保險優惠方案 | [!BADGE 進階]{type=Caution} | [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) |
| <img src="assets/use-case-icons/automotive/icon-owner-loyalty.png" alt="所有者忠誠度" width="40"> | [所有者忠誠度方案](automotive/automotive-overview.md#owner-loyalty-programs) | 依擁有權歷程記錄個人化忠誠度通訊、獎勵和獨家優惠 | [!BADGE 進階]{type=Caution} | [具有決策的跨頻道歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |

>[!TAB 金融服務]

| | 使用案例 | 說明 | 成熟度 | 圖樣 |
| --- | --- | --- | --- | --- |
| | [交易式警示與建議](financial-services/financial-services-overview.md#transaction-based-alerts-and-recommendations) | 傳送交易和個人化建議的即時警報 | [!BADGE 基礎]{type=Neutral} | [事件觸發訊息](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [信用卡應用程式放棄復原](financial-services/financial-services-overview.md#credit-card-application-abandonment-recovery) | 與已開始但未完成信用卡申請的客戶重新互動 | [!BADGE 基礎]{type=Neutral} | [事件觸發訊息](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [詐騙警示Personalization](financial-services/financial-services-overview.md#fraud-alert-personalization) | 依客戶偏好設定個人化詐騙警示和安全性通訊 | [!BADGE 基礎]{type=Neutral} | [事件觸發訊息](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/financial-services/icon-lead-nurturing.png" alt="潛在客戶培養" width="40"> | [高價值銷售機會培養](financial-services/financial-services-overview.md#high-value-lead-nurturing) | 識別高價值潛在客戶，並透過個人化內容和優惠方案培育 | [!BADGE 新增]{type=Informative} | [多步驟協調歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/financial-services/icon-account-dashboard.png" alt="帳戶儀表板" width="40"> | [個人化帳戶儀表板](financial-services/financial-services-overview.md#personalized-account-dashboard) | 根據帳戶活動和財務目標個人化線上銀行儀表板 | [!BADGE 新增]{type=Informative} | [已知訪客網頁/應用程式Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) |
| | [投資Portfolio建議](financial-services/financial-services-overview.md#investment-portfolio-recommendations) | 根據風險設定檔和目標提供個人化投資建議 | [!BADGE 新增]{type=Informative} | [行為建議](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| | [抵押貸款預先核准行銷活動](financial-services/financial-services-overview.md#mortgage-pre-approval-campaigns) | 根據設定檔和人生階段，鎖定可能行銷抵押貸款的客戶 | [!BADGE 新增]{type=Informative} | [多步驟協調歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/financial-services/icon-product-recommendation.png" alt="產品推薦" width="40"> | [現有客戶的產品推薦](financial-services/financial-services-overview.md#product-recommendation-for-existing-customers) | 根據設定檔、交易和生命週期階段建議相關金融產品 | [!BADGE 進階]{type=Caution} | [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) |
| <img src="assets/use-case-icons/financial-services/icon-churn-prevention.png" alt="防止流失" width="40"> | [預防流失行銷活動](financial-services/financial-services-overview.md#churn-prevention-campaigns) | 識別具有AI支援的預測的風險客戶，並參與保留期優惠 | [!BADGE 進階]{type=Caution} | [具有決策的跨頻道歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |
| <img src="assets/use-case-icons/financial-services/icon-life-stage.png" alt="生命階段" width="40"> | [終生階段式產品優惠方案](financial-services/financial-services-overview.md#life-stage-based-product-offers) | 識別進入新生命階段的客戶，並提供相關的金融產品 | [!BADGE 進階]{type=Caution} | [具有決策的跨頻道歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |
| | [熟客方案參與度](financial-services/financial-services-overview.md#loyalty-program-engagement) | 依層級和歷程記錄個人化忠誠度通訊、獎勵和優惠 | [!BADGE 進階]{type=Caution} | [具有決策的跨頻道歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |
| | [個人化的財務教育內容](financial-services/financial-services-overview.md#personalized-financial-education-content) | 根據客戶個人資料和興趣提供個人化的財務教育 | [!BADGE 進階]{type=Caution} | [具有決策的跨頻道歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |

>[!TAB 醫療保健]

| | 使用案例 | 說明 | 成熟度 | 圖樣 |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/healthcare/icon-appointment-reminder.png" alt="約會提醒" width="40"> | [約會提醒自動化](healthcare/healthcare-overview.md#appointment-reminder-automation) | 透過偏好的通訊通道傳送個人化約會提醒 | [!BADGE 基礎]{type=Neutral} | [事件觸發訊息](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/healthcare/icon-post-visit.png" alt="造訪後" width="40"> | [造訪後後續追蹤行銷活動](healthcare/healthcare-overview.md#post-visit-follow-up-campaigns) | 傳送造訪後調查、照護指示和後續預約提醒 | [!BADGE 基礎]{type=Neutral} | [事件觸發訊息](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [實驗室結果通知](healthcare/healthcare-overview.md#lab-results-notification) | 當實驗室結果透過患者偏好的管道取得時通知患者 | [!BADGE 基礎]{type=Neutral} | [事件觸發訊息](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [保險範圍驗證](healthcare/healthcare-overview.md#insurance-coverage-verification) | 在預約之前主動確認並傳達保險範圍 | [!BADGE 基礎]{type=Neutral} | [事件觸發訊息](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [電話健康約會提醒](healthcare/healthcare-overview.md#telehealth-appointment-reminders) | 傳送包含連線指示的遠端健康約會的個人化提醒 | [!BADGE 基礎]{type=Neutral} | [事件觸發訊息](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/healthcare/icon-preventive-care.png" alt="預防護理" width="40"> | [預防性照護提醒](healthcare/healthcare-overview.md#preventive-care-reminders) | 根據年齡和病史提醒病人建議的預防性護理 | [!BADGE 基礎]{type=Neutral} | [批次傳出訊息啟用](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md) |
| <img src="assets/use-case-icons/healthcare/icon-medication-adherence.png" alt="藥物依從性" width="40"> | [藥物遵守行銷活動](healthcare/healthcare-overview.md#medication-adherence-campaigns) | 傳送個人化提醒，協助病人按計畫服用藥物 | [!BADGE 新增]{type=Informative} | [多步驟協調歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| | [慢性病管理方案](healthcare/healthcare-overview.md#chronic-disease-management-programs) | 個人化慢性疾病管理通訊與監控提醒 | [!BADGE 新增]{type=Informative} | [多步驟協調歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| | [新病人上線歷程](healthcare/healthcare-overview.md#new-patient-onboarding-journey) | 使用歡迎資訊、入口網站存取和排程自動化多步驟上線 | [!BADGE 新增]{type=Informative} | [多步驟協調歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| | [健康方案參與](healthcare/healthcare-overview.md#wellness-program-engagement) | 個人化健康計畫通訊、挑戰和獎勵 | [!BADGE 新增]{type=Informative} | [多步驟協調歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| | [服務團隊協調](healthcare/healthcare-overview.md#care-team-coordination) | 在病人與其護理團隊之間啟用個人化溝通 | [!BADGE 新增]{type=Informative} | [多步驟協調歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| | [個人化健康內容傳遞](healthcare/healthcare-overview.md#personalized-health-content-delivery) | 提供因應病人狀況而量身打造的個人化健康教育內容 | [!BADGE 進階]{type=Caution} | [具有決策的跨頻道歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |

>[!TAB 保險]

| | 使用案例 | 說明 | 成熟度 | 圖樣 |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/insurance/icon-policy-renewal.png" alt="原則續約" width="40"> | [原則更新行銷活動](insurance/insurance-overview.md#policy-renewal-campaigns) | 傳送個人化原則更新提醒與優惠 | [!BADGE 基礎]{type=Neutral} | [事件觸發訊息](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [原則變更通知](insurance/insurance-overview.md#policy-change-notifications) | 傳送有關原則變更和涵蓋範圍更新的個人化通知 | [!BADGE 基礎]{type=Neutral} | [事件觸發訊息](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [報價放棄復原](insurance/insurance-overview.md#quote-abandonment-recovery) | 與已開始但未完成保險報價的客戶重新互動 | [!BADGE 基礎]{type=Neutral} | [事件觸發訊息](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [防止宣告詐騙](insurance/insurance-overview.md#claims-fraud-prevention) | 使用智慧型詐騙偵測來識別可疑的宣告模式 | [!BADGE 基礎]{type=Neutral} | [事件觸發訊息](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [災難性事件回應](insurance/insurance-overview.md#catastrophic-event-response) | 在自然災害期間主動與受影響地區的客戶溝通 | [!BADGE 基礎]{type=Neutral} | [事件觸發訊息](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [代理程式與代理人協調](insurance/insurance-overview.md#agent-and-broker-coordination) | 啟用客戶和受指派代理之間的個人化通訊 | [!BADGE 基礎]{type=Neutral} | [批次傳出訊息啟用](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md) |
| <img src="assets/use-case-icons/insurance/icon-claims-process.png" alt="索賠程式" width="40"> | [宣告程式Personalization](insurance/insurance-overview.md#claims-process-personalization) | 個人化索賠程式通訊、狀態更新和支援資源 | [!BADGE 新增]{type=Informative} | [多步驟協調歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| | [風險評估與預防](insurance/insurance-overview.md#risk-assessment-and-prevention) | 提供個人化的風險評估資訊和預防秘訣 | [!BADGE 新增]{type=Informative} | [多步驟協調歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| | [健康與預防方案](insurance/insurance-overview.md#wellness-and-prevention-programs) | 為保險客戶個人化健康方案通訊與獎勵 | [!BADGE 新增]{type=Informative} | [多步驟協調歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/insurance/icon-cross-sell.png" alt="交叉銷售" width="40"> | [交叉銷售產品建議](insurance/insurance-overview.md#cross-sell-product-recommendations) | 根據現有保單和壽險階段，建議額外的保險產品 | [!BADGE 進階]{type=Caution} | [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) |
| <img src="assets/use-case-icons/insurance/icon-life-stage-based-product-offers.png" alt="生命階段" width="40"> | [終生階段式產品優惠方案](insurance/insurance-overview.md#life-stage-based-product-offers) | 識別進入新生命階段的客戶，並提供相關的保險產品 | [!BADGE 進階]{type=Caution} | [具有決策的跨頻道歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |
| | [折扣與節省機會](insurance/insurance-overview.md#discount-and-savings-opportunities) | 識別並傳達個人化折扣機會 | [!BADGE 進階]{type=Caution} | [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) |

>[!TAB 媒體與娛樂]

| | 使用案例 | 說明 | 成熟度 | 圖樣 |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/media-entertainment/icon-new-content.png" alt="新內容" width="40"> | [新內容發行通知](media-entertainment/media-entertainment-overview.md#new-content-release-notifications) | 通知訂閱者符合其偏好設定的新內容 | [!BADGE 基礎]{type=Neutral} | [事件觸發訊息](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [監看清單與我的最愛提醒](media-entertainment/media-entertainment-overview.md#watchlist-and-favorites-reminders) | 傳送關注清單中未觀看內容的提醒 | [!BADGE 基礎]{type=Neutral} | [事件觸發訊息](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [即時活動檢視提醒](media-entertainment/media-entertainment-overview.md#live-event-viewing-reminders) | 通知使用者與其興趣相符的即將上線活動 | [!BADGE 基礎]{type=Neutral} | [事件觸發訊息](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [內容完成行銷活動](media-entertainment/media-entertainment-overview.md#content-completion-campaigns) | 提醒使用者完成他們已開始但未完成的內容 | [!BADGE 基礎]{type=Neutral} | [事件觸發訊息](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/media-entertainment/icon-content-recommendations.png" alt="內容建議" width="40"> | [內容推薦引擎](media-entertainment/media-entertainment-overview.md#content-recommendation-engine) | 根據檢視紀錄提供個人化內容建議 | [!BADGE 新增]{type=Informative} | [行為建議](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| | [個人化首頁體驗](media-entertainment/media-entertainment-overview.md#personalized-homepage-experience) | 以動態方式個人化首頁，以便先顯示最相關的內容 | [!BADGE 新增]{type=Informative} | [行為建議](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| | [個人化播放清單產生](media-entertainment/media-entertainment-overview.md#personalized-playlist-generation) | 根據聆聽歷程記錄和偏好設定自動產生播放清單 | [!BADGE 新增]{type=Informative} | [行為建議](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| | [免費試用轉換行銷活動](media-entertainment/media-entertainment-overview.md#free-trial-conversion-campaigns) | 使用個人化內容與免費試用使用者互動，以鼓勵轉換 | [!BADGE 新增]{type=Informative} | [多步驟協調歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| | [跨平台內容同步](media-entertainment/media-entertainment-overview.md#cross-platform-content-sync) | 透過同步的偏好設定，提供跨裝置的順暢內容體驗 | [!BADGE 新增]{type=Informative} | [已知訪客網頁/應用程式Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) |
| | [社交分享Personalization](media-entertainment/media-entertainment-overview.md#social-sharing-personalization) | 根據內容偏好設定個人化社交分享提示 | [!BADGE 新增]{type=Informative} | [已知訪客網頁/應用程式Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) |
| <img src="assets/use-case-icons/media-entertainment/icon-subscription-churn.png" alt="訂閱流失" width="40"> | [防止訂閱流失](media-entertainment/media-entertainment-overview.md#subscription-churn-prevention) | 識別有風險的訂閱者，並參與保留優惠方案 | [!BADGE 進階]{type=Caution} | [具有決策的跨頻道歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |
| | [進階功能追加銷售](media-entertainment/media-entertainment-overview.md#premium-feature-upsell) | 識別將受益於個人化優惠的高級功能的使用者 | [!BADGE 進階]{type=Caution} | [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) |

>[!TAB 電信]

| | 使用案例 | 說明 | 成熟度 | 圖樣 |
| --- | --- | --- | --- | --- |
| | [資料使用警示與建議](telecommunications/telecommunications-overview.md#data-usage-alerts-and-recommendations) | 當客戶達到資料限制時傳送個人化警報 | [!BADGE 基礎]{type=Neutral} | [事件觸發訊息](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [服務中斷通知](telecommunications/telecommunications-overview.md#service-outage-notifications) | 主動通知客戶其所在區域的服務中斷 | [!BADGE 基礎]{type=Neutral} | [事件觸發訊息](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [帳單付款提醒](telecommunications/telecommunications-overview.md#bill-payment-reminders) | 傳送具有付款選項的個人化帳單付款提醒 | [!BADGE 基礎]{type=Neutral} | [事件觸發訊息](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [5G升級行銷活動](telecommunications/telecommunications-overview.md#5g-upgrade-campaigns) | 符合資格獲得個人化優惠方案5G升級的目標客戶 | [!BADGE 基礎]{type=Neutral} | [批次傳出訊息啟用](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md) |
| <img src="assets/use-case-icons/telecommunications/icon-plan-optimization.png" alt="計畫最佳化" width="40"> | [計畫最佳化行銷活動](telecommunications/telecommunications-overview.md#plan-optimization-campaigns) | 分析使用模式並建議最佳計畫變更 | [!BADGE 新增]{type=Informative} | [多步驟協調歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| | [新客戶上線歷程](telecommunications/telecommunications-overview.md#new-customer-onboarding-journey) | 使用歡迎資訊和功能教學課程，自動個人化上線 | [!BADGE 新增]{type=Informative} | [多步驟協調歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| | [網路效能Personalization](telecommunications/telecommunications-overview.md#network-performance-personalization) | 根據位置和裝置個人化網路效能資訊 | [!BADGE 新增]{type=Informative} | [已知訪客網頁/應用程式Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) |
| <img src="assets/use-case-icons/telecommunications/icon-device-upgrade.png" alt="裝置升級" width="40"> | [裝置升級建議](telecommunications/telecommunications-overview.md#device-upgrade-recommendations) | 識別符合資格的客戶，並提供個人化裝置推薦 | [!BADGE 進階]{type=Caution} | [具有決策的跨頻道歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |
| <img src="assets/use-case-icons/telecommunications/icon-churn-prevention.png" alt="防止流失" width="40"> | [高價值客戶的流失預防](telecommunications/telecommunications-overview.md#churn-prevention-for-high-value-customers) | 識別高價值風險客戶，並參與保留期優惠方案 | [!BADGE 進階]{type=Caution} | [具有決策的跨頻道歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |
| | [家庭計畫管理](telecommunications/telecommunications-overview.md#family-plan-management) | 依家庭使用狀況為家庭計畫管理員提供個人化通訊 | [!BADGE 進階]{type=Caution} | [具有決策的跨頻道歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |
| | [附加服務建議](telecommunications/telecommunications-overview.md#add-on-service-recommendations) | 根據計畫、使用和偏好設定，建議相關的附加服務 | [!BADGE 進階]{type=Caution} | [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) |
| | [熟客方案參與度](telecommunications/telecommunications-overview.md#loyalty-program-engagement) | 依層級和歷程記錄個人化忠誠度通訊、獎勵和優惠 | [!BADGE 進階]{type=Caution} | [具有決策的跨頻道歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |

>[!TAB 旅遊業及旅館業]

| | 使用案例 | 說明 | 成熟度 | 圖樣 |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/travel-hospitality/icon-cart-abandonment.png" alt="放棄購買" width="40"> | [購物車放棄復原歷程](travel-hospitality/travel-hospitality-overview.md#cart-abandonment-recovery-journey) | 偵測放棄的預訂購物車並觸發個人化電子郵件歷程 | [!BADGE 基礎]{type=Neutral} | [事件觸發訊息](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/travel-hospitality/icon-booking-reminders.png" alt="預訂提醒" width="40"> | [多頻道預約提醒](travel-hospitality/travel-hospitality-overview.md#multi-channel-booking-reminders) | 透過電子郵件、文字和推播傳送個人化預訂提醒 | [!BADGE 基礎]{type=Neutral} | [事件觸發訊息](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/travel-hospitality/icon-seasonal-campaigns.png" alt="季節性行銷活動" width="40"> | [季節性行銷活動Personalization](travel-hospitality/travel-hospitality-overview.md#seasonal-campaign-personalization) | 根據季節性偏好和過去的預訂，個人化行銷活動 | [!BADGE 基礎]{type=Neutral} | [批次傳出訊息啟用](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md) |
| <img src="assets/use-case-icons/travel-hospitality/icon-personalized-homepage.png" alt="個人化首頁" width="40"> | [新訪客的個人化首頁](travel-hospitality/travel-hospitality-overview.md#personalized-homepage-for-new-visitors) | 根據位置和瀏覽行為顯示個人化建議 | [!BADGE 新增]{type=Informative} | [匿名訪客網頁Personalization](/help/blueprints/use-case-patterns/personalization/anonymous-visitor-web-personalization.md) |
| <img src="assets/use-case-icons/travel-hospitality/icon-high-intent.png" alt="高色彩比對方式" width="40"> | [高意圖訪客目標定位](travel-hospitality/travel-hospitality-overview.md#high-intent-visitor-targeting) | 識別具有AI評分的高意圖訪客，並透過個人化優惠方案鎖定目標 | [!BADGE 新增]{type=Informative} | [已知訪客網頁/應用程式Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) |
| <img src="assets/use-case-icons/travel-hospitality/icon-post-booking-upsell.png" alt="預約後追加銷售" width="40"> | [預約後追加銷售行銷活動](travel-hospitality/travel-hospitality-overview.md#post-booking-upsell-campaigns) | 在預訂後觸發升級、離開和套件的向上銷售行銷活動 | [!BADGE 新增]{type=Informative} | [多步驟協調歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/travel-hospitality/icon-win-back.png" alt="雙贏" width="40"> | [失效客戶的贏回行銷活動](travel-hospitality/travel-hospitality-overview.md#win-back-campaigns-for-lapsed-customers) | 透過個人化的回饋優惠與失效的客戶互動 | [!BADGE 新增]{type=Informative} | [多步驟協調歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/travel-hospitality/icon-dynamic-itinerary.png" alt="動態行程" width="40"> | [動態行程建議](travel-hospitality/travel-hospitality-overview.md#dynamic-itinerary-recommendations) | 根據過去的預約和偏好設定顯示個人化行程 | [!BADGE 新增]{type=Informative} | [已知訪客網頁/應用程式Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) |
| <img src="assets/use-case-icons/travel-hospitality/icon-recently-browsed.png" alt="最近瀏覽" width="40"> | 首頁上[最近瀏覽的產品](travel-hospitality/travel-hospitality-overview.md#recently-browsed-products-on-homepage) | 顯示最近檢視的目的地以鼓勵回訪 | [!BADGE 新增]{type=Informative} | [已知訪客網頁/應用程式Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) |
| <img src="assets/use-case-icons/travel-hospitality/icon-group-booking.png" alt="群組預訂" width="40"> | [群組預訂建議](travel-hospitality/travel-hospitality-overview.md#group-booking-recommendations) | 向頻繁的群組預約者建議群組套件和適閤家庭的選項 | [!BADGE 新增]{type=Informative} | [行為建議](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| <img src="assets/use-case-icons/travel-hospitality/icon-exit-intent.png" alt="退出目的" width="40"> | [具有目標選件的退出意圖強制回應視窗](travel-hospitality/travel-hospitality-overview.md#exit-intent-modal-with-targeted-offers) | 當訪客顯示退出意向時，使用相關優惠方案顯示個人化強制回應視窗 | [!BADGE 進階]{type=Caution} | [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) |
| <img src="assets/use-case-icons/travel-hospitality/icon-loyalty-program.png" alt="熟客方案" width="40"> | [忠誠計畫Personalization](travel-hospitality/travel-hospitality-overview.md#loyalty-program-personalization) | 依忠誠度等級和點數平衡，個人化網站、優惠和通訊 | [!BADGE 進階]{type=Caution} | [具有決策的跨頻道歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |

>[!TAB B2B]

| | 使用案例 | 說明 | 成熟度 | 圖樣 |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/b2b/icon-webinar-demo.png" alt="網路研討會示範" width="40"> | [網路研討會與示範排程](b2b/b2b-overview.md#webinar-and-demo-scheduling) | 根據潛在客戶興趣個人化網路研討會邀請和示範排程 | [!BADGE 基礎]{type=Neutral} | [事件觸發訊息](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/b2b/icon-abm.png" alt="ABM" width="40"> | [Account-Based Marketing Personalization](b2b/b2b-overview.md#account-based-marketing-personalization) | 根據購買訊號為目標帳戶個人化行銷通訊 | [!BADGE 新增]{type=Informative} | [B2B 對象啟用](/help/blueprints/use-case-patterns/audience-building-activation/b2b-audience-activation.md) |
| <img src="assets/use-case-icons/b2b/icon-lead-scoring.png" alt="潛在客戶評分" width="40"> | [銷售機會評分與培養](b2b/b2b-overview.md#lead-scoring-and-nurturing) | 透過培養行銷活動，自動對潛在客戶評分並將高分客戶導向銷售 | [!BADGE 新增]{type=Informative} | [多步驟協調歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/b2b/icon-content-personalization.png" alt="內容個人化" width="40"> | 潛在客戶的[內容Personalization](b2b/b2b-overview.md#content-personalization-for-prospects) | 根據潛在客戶產業、角色和參與，個人化網站內容和資源 | [!BADGE 新增]{type=Informative} | [已知訪客網頁/應用程式Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) |
| <img src="assets/use-case-icons/b2b/icon-event-registration.png" alt="活動註冊" width="40"> | [活動註冊與後續追蹤](b2b/b2b-overview.md#event-registration-and-follow-up) | 自動化個人化事件註冊確認、提醒和追蹤 | [!BADGE 新增]{type=Informative} | [多步驟協調歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/b2b/icon-trial-conversion.png" alt="試用轉換" width="40"> | [產品試用轉換行銷活動](b2b/b2b-overview.md#product-trial-conversion-campaigns) | 透過個人化建議與試用使用者互動，以鼓勵付費轉換 | [!BADGE 新增]{type=Informative} | [多步驟協調歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/b2b/icon-customer-onboarding.png" alt="客戶入門" width="40"> | [客戶成功和上線](b2b/b2b-overview.md#customer-success-and-onboarding) | 使用相關培訓和資源個人化入門歷程 | [!BADGE 新增]{type=Informative} | [多步驟協調歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/b2b/icon-competitive-replacement.png" alt="競爭產品取代" width="40"> | [競爭取代行銷活動](b2b/b2b-overview.md#competitive-replacement-campaigns) | 使用具有個人化移轉優惠之競爭者產品的目標潛在客戶 | [!BADGE 新增]{type=Informative} | [多步驟協調歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/b2b/icon-case-study.png" alt="案例研究" width="40"> | [個案研究和ROI Personalization](b2b/b2b-overview.md#case-study-and-roi-personalization) | 根據潛在客戶產業提供個人化的個案研究和ROI電腦 | [!BADGE 新增]{type=Informative} | [已知訪客網頁/應用程式Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) |
| | [客戶宣傳計畫](b2b/b2b-overview.md#customer-advocacy-programs) | 尋找並吸引滿意的客戶，以取得參考資料和證明 | [!BADGE 新增]{type=Informative} | [多步驟協調歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/b2b/icon-contract-renewal.png" alt="合約續約" width="40"> | [合約續約行銷活動](b2b/b2b-overview.md#contract-renewal-campaigns) | 主動與透過個人化優惠方案尋求續約的客戶互動 | [!BADGE 進階]{type=Caution} | [具有決策的跨頻道歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |
| <img src="assets/use-case-icons/b2b/icon-upsell-expansion.png" alt="追加銷售擴充" width="40"> | [追加銷售與擴充機會](b2b/b2b-overview.md#upsell-and-expansion-opportunities) | 根據使用模式和成長指標，識別準備好升級的客戶 | [!BADGE 進階]{type=Caution} | [具有決策的跨頻道歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |

>[!ENDTABS]
