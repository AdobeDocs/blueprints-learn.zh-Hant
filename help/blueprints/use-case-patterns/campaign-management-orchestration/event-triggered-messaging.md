---
title: 事件觸發式傳訊
description: 瞭解如何傳遞情境式即時訊息來回應行為或系統事件。
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 75137990-9848-40c0-abf3-adbd21d2de52
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1955'
ht-degree: 5%

---

# 事件觸發式傳訊

本指南說明事件觸發的訊息使用案例模式，此模式使用[!DNL Adobe Journey Optimizer] (AJO)、[!DNL Real-Time Customer Data Platform] (RT-CDP)和[!DNL Adobe Experience Platform] (AEP)來傳遞情境式即時訊息，以回應行為或系統事件。 它專為需要瞭解此模式的功能、其支援的業務目標、其啟用的戰術使用案例以及所涉及的Adobe應用程式的解決方案架構師、行銷技術人員和實作工程師所設計。

此模式涵蓋從事件擷取到歷程建立，再到訊息傳送和效能報告的完整生命週期。

## 使用案例模式

本節說明驅動事件觸發式傳訊的核心模式和執行計畫。

**事件觸發訊息**

接聽即時行為或系統事件，然後將內容相關訊息傳遞至觸發的設定檔。

**執行計畫：**&#x200B;事件擷取>歷程專案>條件評估>訊息傳送>報告

## 使用案例概述

事件觸發的傳訊功能會傳送內容式訊息來回應即時行為或系統事件。 批次傳出訊息啟動會依排程傳送給預先評估的對象，不同於批次傳出訊息啟動，此模式會監聽合格事件（例如購物車放棄、瀏覽工作階段、表單提交或系統狀態變更），並立即將觸發設定檔輸入歷程，以評估條件並傳送訊息。

此模式仰賴串流至AEP的即時事件（透過網頁SDK、Mobile SDK或伺服器端API）、在AJO中具有單一事件專案的歷程，以及決定是否要傳送及傳送何種內容的條件評估邏輯。 訊息通常會在觸發事件後的數分鐘內傳送，因此這種模式非常適合時間敏感型與情境相關的通訊。

與排程的批次通訊相比，組織可利用此模式即時回應客戶動作、提高關聯性，並提高參與度和轉換率。 常見的情況包括放棄的購物車復原、購買後的後續追蹤、註冊後的歡迎訊息，以及付款失敗或價格下降警示等時效性很強的通知。

## 主要業務目標

此使用案例模式支援下列業務目標。

**[復原放棄的購物車與歷程](../../business-objectives/customer-experience/recover-abandoned-carts-journeys.md)**

透過及時且個人化的後續追蹤，重新吸引在購買、應用程式或註冊流程中休假的使用者。

| KPI |
| --- |
| 轉換率、遞增收入、參與 |

**[提高轉換率](../../business-objectives/revenue-monetization/increase-conversion-rates.md)**

提高完成所需動作（例如購買、註冊或提交表單）的訪客和潛在客戶的百分比。

| KPI |
| --- |
| 轉換率、銷售機會轉換、每個銷售機會的成本 |

**[提供個人化的客戶體驗](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**

根據個別偏好設定、行為和生命週期階段量身打造內容、選件和訊息。

| KPI |
| --- |
| 參與度、轉換率、客戶滿意度(CSAT) |

**[改善客戶上線](../../business-objectives/customer-experience/improve-customer-onboarding.md)**

透過簡化的個人化歡迎體驗和啟動歷程，加快新客戶的價值實現時間。

| KPI |
| --- |
| 參與度、保留率、轉換率 |

## 戰術使用案例範例

下列案例說明如何將事件觸發式訊息套用至不同的業務內容。

- **購物車放棄電子郵件或簡訊** — 當客戶新增商品到購物車但未在定義的時間範圍內完成購買時，傳送提醒訊息
- **瀏覽放棄後續追蹤** — 重新與檢視過產品或內容但未採取轉換動作的訪客互動
- **購買後感謝您或交叉銷售** — 在購買事件後立即提供確認和交叉銷售建議
- **試用到期提醒** — 通知即將結束免費試用且提供續約或轉換訊息的使用者
- **註冊後的歡迎訊息** — 當新使用者註冊或建立帳戶時，立即傳送上線訊息
- **表單提交確認** — 以內容式確認來確認表單提交（連絡人要求、申請、註冊）
- **付款失敗通知** — 當定期付款失敗時提醒客戶，提示他們更新付款資訊
- **應用程式解除安裝回呼推播通知** — 當使用者解除安裝行動應用程式時觸發回呼訊息
- **預約或約會確認** — 在排程預訂、預約或約會後，立即傳送確認
- **願望清單專案的價格下降警報** — 當願望清單上的產品降價時通知客戶

## 關鍵績效指標

下列KPI可協助評估事件觸發訊息實作的效能。

| KPI | 說明 | 測量方法 |
| --- | --- | --- |
| 轉換率 | 完成所需動作（購買、註冊、續約）的觸發訊息收件者百分比 | 轉換/傳遞的訊息* 100 |
| 遞增收入 | 與不傳送控制組相比，由事件觸發的訊息所產生的額外收入 | 來自觸發傳送的收入 — 控制組基準 |
| 開啟率 | 收件者開啟的傳遞訊息百分比 | 開啟/傳送* 100 |
| 點進率(CTR) | 至少產生一次點按的傳遞訊息百分比 | 點按數/送達* 100 |
| 轉換時間 | 訊息傳遞和轉換事件之間的平均經過時間 | Avg（轉換時間戳記 — 傳遞時間戳記） |
| 歷程完成率 | 進入歷程並到達訊息傳送步驟的設定檔百分比（不會因條件或退出而捨棄） | 到達傳送的設定檔/進入歷程的設定檔* 100 |
| 訊息隱藏率 | 由於頻率上限、同意或條件評估而抑制的合格設定檔百分比 | 隱藏的設定檔/符合資格的設定檔總數* 100 |
| 跳出率 | 因硬退信或軟退信而無法傳遞的訊息百分比 | 彈回數/已傳送* 100 |

## 應用程式

在此使用案例模式中使用以下Adobe應用程式。

- **[!DNL Adobe Journey Optimizer](AJO)** — 具有單一事件專案、條件評估、等待步驟、訊息編寫、頻道設定、頻率控管和傳遞報告的歷程協調
- **[!DNL Adobe Real-Time Customer Data Platform](RT-CDP)** — 歷程中條件式篩選的對象評估、同意和治理實施、設定檔擴充
- **[!DNL Adobe Experience Platform](AEP)** — 透過Web SDK、Mobile SDK或伺服器端API的即時事件擷取；資料模式；身分解析；Edge Network

## 相關文件

下列資源提供此實作中所使用功能的其他詳細資料。

### Journey orchestration

- [開始使用歷程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [建立歷程](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [歷程屬性](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [一般事件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [對象資格鑑定事件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)
- [條件活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [等待活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [在歷程中新增訊息](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [退出條件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [歷程專案管理](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [測試您的歷程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [發佈歷程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)

### 管道設定

- [開始使用電子郵件設定](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [委派子網域](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [建立 IP 池](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [IP熱身計畫](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [電子郵件表面設定](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [設定簡訊頻道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [設定推播通知頻道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [管理隱藏清單](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### 訊息製作與個人化

- [建立電子郵件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [設計電子郵件內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [新增個人化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization語法](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [輔助函式](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [動態內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [使用內容範本](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [使用內容片段](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [預覽和測試您的內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)
- [建立簡訊訊息](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/create-sms)
- [設計推播通知](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/design-push)

### 頻率與商業規則

- [頻率規則](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [商業規則概觀](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [設定API上限](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/channel-surfaces/capping)

### 衝突與優先順序管理

- [開始使用衝突與優先順序管理](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [識別潛在衝突](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)
- [優先順序分數](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [歷程上限和仲裁](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)

### 報告與效能

- [歷程即時報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [歷程全域報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [AJO + CJA整合指南](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

### 資料收集與擷取

- [網頁SDK概觀](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [行動SDK概觀](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [Edge Network伺服器API總覽](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)
- [設定資料串流](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [串流擷取概觀](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/streaming/overview)

### 資料模型與結構描述

- [XDM系統概覽](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [結構描述組合基本面](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)

### 身分和設定檔

- [Identity Service總覽](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [身分名稱空間概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/identity/features/namespaces)
- [身分識別圖連結規則](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/identity-linking-logic)
- [設定檔概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [合併原則概觀](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

### 細分與對象

- [Segmentation Service概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [區段產生器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [串流區段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)

### 資料控管和同意

- [資料控管概覽](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [資料使用標籤概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/labels/overview)
- [同意和偏好設定欄位群組](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)
- [Journey Optimizer中的同意](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)

### 計算的屬性

- [計算屬性概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [計算屬性UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/ui)

### 監視和可觀察性

- [警報概觀](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [可觀察性深入分析概觀](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)

### 護欄

- [Journey Optimizer護欄](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [即時客戶個人檔案護欄](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [擷取護欄](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)

### 教學課程與指南

- [建立歷程教學課程](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [安裝Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/install/overview)
