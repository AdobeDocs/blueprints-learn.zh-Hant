---
title: 汽車使用案例
description: 瞭解汽車組織如何使用Adobe Experience Platform來個人化車輛購買歷程、改善服務保留率，並建立擁有者忠誠度。
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
source-git-commit: 126dd712603494513b71a8a6e1c4b99bdb7ff212
workflow-type: tm+mt
source-wordcount: '1843'
ht-degree: 0%

---


# 汽車使用案例

汽車組織使用Adobe Experience Platform將經銷商互動、線上車輛研究、服務記錄及連線車輛系統的客戶資料整合為每個擁有者的單一檢視。 此基礎可在整個擁有權生命週期中啟用個人化體驗，從最初的車輛研究到購買、服務和忠誠度。

## 使用案例摘要

| 使用案例 | 說明 | 業務影響 | 實作模式 |
| --- | --- | --- | --- |
| [車輛購買歷程Personalization](#vehicle-purchase-journey-personalization) | 使用相關的車輛建議、融資選項和經銷商資訊，個人化從研究到購買的車輛購買歷程。 當潛在買家在每個階段都收到量身打造的指引時，他們會更快更自信地在銷售funnel中移動。 | 從銷售線索到購買的轉換率提高20%至30%，改善銷售管道 | [具有決策的跨頻道歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |
| [服務約會提醒](#service-appointment-reminders) | 根據車輛里程數、服務歷史記錄和客戶偏好設定傳送個人化服務提醒。 主動式的外聯保持車輛持續保養，並確保客戶回到經銷商，而不是尋求第三方供應商。 | 服務預約費率提高40-50%，服務收入增加 | [事件觸發訊息](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| [折價促銷活動](#trade-in-value-campaigns) | 主動為準備升級的客戶提供以舊換新價值評估。 在擁有者擁有週期的適當時間接觸擁有者，可加快購買新車輛的速度。 | 交易參與增加25-35%，新車銷售增加 | [多步驟協調歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| [零件與配件建議](#parts-and-accessories-recommendations) | 根據車輛型號、擁有時間及客戶喜好設定，建議相關零件、配件及升級。 個人化的售後推薦可帶來遞增收入，同時協助擁有者從車輛中獲得更多利益。 | 零件/配件採購增加30-40%，售後收入增加 | [行為建議](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| [車輛召回通知](#vehicle-recall-notifications) | 傳送包含服務排程選項和安全資訊的個人化召回通知。 及時、清楚的召回通訊可保護客戶安全，並展現品牌對負責任所有權支援的承諾。 | 召回回應率提高60-70%，安全性法規遵循改善 | [事件觸發訊息](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| [新模型啟動促銷活動](#new-model-launch-campaigns) | 根據目前的車輛、偏好和購買記錄，鎖定可能對新模型啟動感興趣的客戶。 焦點受眾目標定位可最大化啟動影響力，並建立早期訂單動量。 | 發行促銷活動參與增加35-45%，提高新機型興趣 | [批次傳出訊息啟用](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md) |
| [財務與保險優惠方案](#financing-and-insurance-offers) | 根據信用設定檔、車輛選擇和購買時間表，展示個人化的融資和保險優惠方案。 量身打造的金融產品消除了購買障礙，並幫助客戶對自己的條款充滿信心。 | 融資接受率增加25-35%，增加每次銷售收入 | [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) |
| [測試磁碟機排程](#test-drive-scheduling) | 透過經銷商推薦和車輛可用性，啟用個人化的測試驅動程式排程。 讓感興趣的買家輕鬆掌握最新消息，加速購買過程。 | 測試磁碟機完成率提高50-60%，提升銷售轉換率 | [事件觸發訊息](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| [所有者忠誠度方案](#owner-loyalty-programs) | 根據擁有權記錄和忠誠度等級，個人化忠誠度方案通訊、獎勵和獨家優惠。 辨識長期擁有者可加強與品牌的情感聯絡。 | 忠誠度計畫參與度提高40-50%，重複購買次數增加 | [具有決策的跨頻道歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |
| [保固與延長服務計畫](#warranty-and-extended-service-plans) | 根據車輛使用年限、里程和購買模式，在最佳時間建議保固和延長服務計畫。 適時拓展功能可在工廠保固到期前擷取收入。 | 延長保固採用率增加20-30%，服務收入增加 | [多步驟協調歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| [連線汽車功能啟用](#connected-car-feature-activation) | 根據車輛功能和技術偏好提供個人化的連線車輛功能建議。 協助擁有者發現未使用的功能，可提升滿意度並強化數位關係。 | 功能啟用率提高35-45%，改善客戶體驗 | [多步驟協調歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| [經銷商網路協調](#dealer-network-coordination) | 根據客戶地點、偏好和經銷商詳細目錄啟用個人化經銷商推薦。 將客戶與正確的經銷商連線起來，可改善購買和服務體驗。 | 經銷商參與率提高30-40%，改善銷售協調工作 | [已知訪客網頁/應用程式Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) |

## 使用案例的技術考量

### 車輛購買歷程個人化

- 經銷商管理系統的車輛庫存資料必須經常整合和更新，以便建議能反映附近經銷商的實際可用性。
- 必須擷取客戶在網站上的研究行為，包括車輛設定活動、比較工具使用情況和手冊下載，才能準確識別購買意向訊號。
- 潛在客戶評分模型應同時考量線上參與和離線訊號，例如經銷商造訪和電話查詢，以優先處理最高意圖的潛在客戶。
- 潛在客戶註冊或造訪代理後，[!DNL Real-Time Customer Data Platform]個設定檔必須將匿名Web Research工作階段與已知的客戶身分合併。

### 服務約會提醒

- 來自已連線汽車系統或經銷商服務記錄的車輛里程與遠端訊息資料，必須流入客戶設定檔，才能在正確的服務間隔觸發提醒。
- 提醒訊息應包含一鍵式排程連結，以預先填入客戶的車輛資訊與建議的服務專案，將預訂摩擦降至最低。
- 必須整合服務歷史記錄，以避免建議最近完成的服務，並以到期的特定維護專案來個人化提醒。
- [!DNL Journey Optimizer]訊息時間應該考慮經銷商服務容量和營業時間，以確保客戶在收到提醒時可以預約約會。

### 折價促銷活動

- 來自協力廠商的車輛估價資料必須定期整合和更新，以確保與客戶共用的折舊估計值準確且具有競爭力。
- 持有權生命週期模型應考慮租約到期日、貸款償還時間表及車輛區段的平均持有權期間等因素，以找出最佳的外聯視窗。
- 行銷活動訊息應動態參考客戶目前的工具，並根據其偏好和預算建議特定的升級選項。
- [!DNL Experience Platform]區段應排除最近購買車輛或目前處於有效服務糾紛中的客戶，以避免安排錯誤的外聯時間。

### 零件與配件建議

- 產品目錄資料必須包含車輛相容性資訊，因此建議僅會顯示符合客戶特定車輛年份、製造商和型號的零件和配件。
- 季節和區域因素應影響建議；冬季配件應在較冷的氣候中推廣，而效能升級可能會在活躍愛好者社群的區域引起更多共鳴。
- 零件和配件頁面的瀏覽行為必須擷取並與客戶設定檔建立關聯，以根據表達的興趣來調整建議。
- [!DNL Experience Platform]網頁SDK實作應從已驗證的工作階段擷取車輛識別號碼資料，以確保相容性篩選準確。

### 車輛召回通知

- 必須在客戶設定檔中準確維護車輛識別碼記錄，以便召回通知可送達每個受影響的擁有者，而不會傳送給未受影響的客戶。
- 召回訊息必須符合各適用市場對於安全通知內容、時間及傳遞確認的法規要求。
- 多頻道傳遞（電子郵件、簡訊、推播通知和實體郵件）應該用於最大化觸及率，因為安全關鍵型通訊需要比行銷訊息更高的傳遞保證。
- [!DNL Journey Optimizer]應該追蹤個別層級的召回回應狀態，並向未在定義的時間範圍內排程服務的擁有者升級後續通訊。

### 新模型上市行銷活動

- 上市促銷活動的對象區段應考慮目前的車輛模型、擁有持續時間、過去的模型興趣訊號及人口統計適合度，以識別最高傾向的潛在客戶。
- Launch內容應進行個人化，以參考客戶目前的工具，並強調可解決其可能優先順序的特定改善或功能。
- 行銷活動時間必須與禁運日期和區域推出排程相協調，以確保客戶在市場適當時間收到資訊。
- [!DNL Real-Time Customer Data Platform]對象啟用應將啟動區段同步至廣告平台，以取得協調的付費媒體支援及自有頻道外展活動。

### 融資與保險優惠方案

- 財務優惠方案適用性規則必須謹慎設定，以符合借貸法規，確保向客戶呈現的優惠方案是客戶實際可符合的資格。
- 信用設定檔資料整合需要安全的處理和嚴格的存取控制，因為財務資訊受到加強的隱私權和法規要求的約束。
- 優惠方案簡報必須明確披露條款、費率及條件，以符合各適用市場的消費者金融法規。
- [!DNL Journey Optimizer]決策規則應將車輛價格、首期付款和貸款期限偏好設定納入考量，以依據關聯性而非單純依據費率來排名優惠。

### 測試磁碟機排程

- 經銷商存貨系統必須整合，以確認客戶感興趣的特定車輛型號及配飾可在建議經銷商處試駕使用。
- 根據地點的經銷商推薦應考量客戶地址、經銷商評級和目前的預約可用性，以建議最方便的選項。
- 試用確認和提醒訊息應包括指示、經銷商聯絡資訊和期望，降低不顯示率。
- [!DNL Experience Platform]行為資料應識別建議測試的最佳時機，避免過早聯絡尚未準備就緒的早期研究人員。

### 所有者熟客方案

- 忠誠度等級計算必須結合參與度的多個維度，包括服務造訪、零件購買、轉介和事件出席率，而不僅僅是車輛購買記錄。
- 經銷商和服務中心的獎勵履行系統必須整合，以便在服務點可順暢地兌現忠誠度福利。
- 通訊應根據擁有權生命週期階段進行調整，在新擁有者的第一年向新擁有者提供不同的價值主張，而不是根據長期擁有者尋求潛在升級。
- [!DNL Journey Optimizer]歷程邏輯應即時偵測層級變更，並在客戶在忠誠度等級之間移動時觸發恭喜或重新參與訊息。

### 保固與延長服務計畫

- 必須在客戶設定檔中準確追蹤保固到期日和涵蓋範圍詳細資料，以在適當時間（通常是在到期前60至90天）觸發外展活動。
- 車輛里程及使用模式（來自於連線的車輛資料或服務記錄）應提供計畫建議，因為里程高的司機與里程低的車主相比，可享有不同的涵蓋範圍。
- 計畫比較內容應清楚且不含術語，協助客戶確切瞭解涵蓋範圍以及相對於潛在自付維修成本的價值。
- [!DNL Real-Time Customer Data Platform]區段應該區分工廠保固即將到期的客戶、現有延長計畫即將續約的客戶，以及目前沒有涵蓋範圍的客戶。

### 連線車輛功能啟用

- 必須整合連線汽車平台資料，以識別每輛汽車上可用的功能，以及車主已啟動或使用哪些功能。
- 功能採用追蹤應擷取啟動事件、使用頻率和參與深度，以便個人化功能建議的順序和步調。
- 車內通知頻道應與電子郵件和應用程式通知協調，以在與內容最相關的時刻傳送功能提示，例如在偵測到公路旅行時建議導覽功能。
- [!DNL Experience Platform]設定檔應儲存車輛技術設定資料，包括已安裝的套件和軟體版本，以確保功能建議與擁有者的特定車輛相容。

### 經銷商網路協調

- 經銷商庫存摘要必須經常整合和更新，以確保向客戶顯示的車輛可用效能準確反映每個經銷商的貨品。
- 客戶對經銷商的指派邏輯應考慮近似程度、經銷商專業化、語言偏好設定，以及任何現有的經銷商關係，以提供最佳比對。
- 潛在客戶路由規則必須確保在客戶線上上表示購買興趣時，查詢會快速到達適當的經銷商，並包含有關客戶研究活動的完整內容。
- [!DNL Experience Platform]身分解析必須處理客戶與多個經銷商互動的案例，維護統一的設定檔，同時尊重每個經銷商對自己客戶關係的看法。
