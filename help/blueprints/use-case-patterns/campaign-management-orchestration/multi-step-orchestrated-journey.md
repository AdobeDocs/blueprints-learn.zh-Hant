---
title: 多步驟協調歷程
description: 瞭解如何透過分支和多點接觸歷程，隨時間推移使用等待、條件和多個訊息動作來引導設定檔。
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 5667b188-1b20-4a85-aebb-74efd5f771a1
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1798'
ht-degree: 5%

---

# 多步驟協調歷程

本指南說明多步驟協調歷程使用案例模式，此模式使用[!DNL Adobe Journey Optimizer] (AJO)和[!DNL Real-Time Customer Data Platform] (RT-CDP)來協調隨時間傳送多則訊息的分支、多點觸控客戶歷程。 它專為需要瞭解此模式的功能、其支援的業務目標、其啟用的戰術使用案例以及所涉及的Adobe應用程式的解決方案架構師、行銷技術人員和實作工程師所設計。

## 使用案例模式

**多步驟協調歷程**

引導設定檔完成分支、多重接觸歷程，其中包含一段時間的等待、條件和多個訊息動作。

**執行計畫：**&#x200B;對象評估>歷程執行（多節點） >條件分支>訊息傳送(xN) >退出條件>報告

## 使用案例概述

多步驟協調的歷程會處理單一訊息不足以達成所要客戶結果的業務案例。 歷程不會是一次性傳送，而是透過一系列接觸點（電子郵件、簡訊訊息、推播通知或應用程式內訊息）引導每個設定檔，間隔為數天或數週，並根據設定檔屬性、行為訊號或事件資料調整路徑的分支邏輯。

這些歷程是AJO中最複雜的行銷活動模式。 它們結合受眾型或事件型進入與動作節點（訊息）、條件節點（分支邏輯）、等待節點（時間延遲）和退出條件（轉換事件或逾時）的畫布。 每個設定檔會以自己的步調獨立地完成歷程，在每個步驟接收內容相關的內容。

此模式包含更簡單的模式 — 針對單一傳送行銷活動批次傳出訊息啟用，以及針對單一事件回應的事件觸發訊息。 當使用案例需要隨時間透過多次互動來培養輪廓時，請使用此模式。

>[!NOTE]
>如果您的歷程需要在個別決策點動態選取最佳優惠、內容或頻道，請參閱[具有決策的跨頻道歷程](cross-channel-journey-with-decisioning.md)。 該模式透過AJO Decisioning整合延伸了這一模式。

## 主要業務目標

此使用案例模式支援下列業務目標。

### 提升客戶保留率

透過價值導向的體驗和持續培養的關係，讓現有客戶持續參與並更新。

**KPI：**&#x200B;保留率、客戶期限值、參與度

[進一步瞭解如何改善客戶保留率](/help/blueprints/business-objectives/customer-experience/improve-customer-retention.md)

### 改善客戶入門

透過簡化的個人化歡迎體驗和啟動歷程，加快新客戶的價值實現時間。

**KPI：**&#x200B;參與度、保留率、轉換率

[進一步瞭解如何改善客戶入門](/help/blueprints/business-objectives/customer-experience/improve-customer-onboarding.md)

### 與休眠客戶重新互動

使用根據行為訊號的目標重新啟用行銷活動，以贏回非作用中或失效的客戶。

**KPI：**&#x200B;參與度、保留率、轉換率

[進一步瞭解如何改善客戶保留率](/help/blueprints/business-objectives/customer-experience/improve-customer-retention.md)

### 復原放棄的購物車和歷程

透過及時且個人化的後續追蹤，重新吸引在購買、應用程式或註冊流程中休假的使用者。

**KPI：**&#x200B;轉換率、遞增收入、參與

[進一步瞭解如何復原放棄的購物車和歷程](/help/blueprints/business-objectives/customer-experience/recover-abandoned-carts-journeys.md)

## 戰術使用案例範例

以下案例說明多步驟協調歷程模式的常見應用程式。

- **客戶入門系列** — 歡迎電子郵件，隨後是功能教育，然後在註冊後的前14天提供啟用提示
- **重新參與滴漏式行銷活動** — 先傳送提醒電子郵件，再傳送獎勵優惠方案，接著傳送逾期三週之失效客戶的最終通知
- **忠誠度里程碑歷程** — 層級升級通知，接著是專屬優惠，然後在會員資格週年臨近時收到續約提醒
- **贏回順序** — 「我們很想念您」電子郵件，接著透過電子郵件提供折扣優惠，然後是最後的SMS提醒，提醒買家購買失敗
- **產品採用歷程** — 試用歡迎、使用提示，然後隨著試用期進行而提示升級
- **訂閱續約順序** — 30天通知、7天提醒，然後是即將續約的到期日訊息
- **購買後的培養** — 感謝您電子郵件、使用指南、交叉銷售建議，然後在購買30天後提出檢閱要求

## 關鍵績效指標

使用下列KPI來評估您的多步驟協調歷程實作的成效。

| KPI | 說明 | 測量方法 |
| --- | --- | --- |
| 歷程完成率 | 完成完整歷程且未提早退出的設定檔百分比 | 歷程報告：已退出（完成）/已進入 |
| 步驟轉換率 | 從一個步驟進展到下一個步驟的設定檔百分比 | 歷程報告中的每節點量度 |
| 管道參與率 | 每個接觸點的開啟率、點進率和回應率 | 每則訊息的傳遞和參與量度 |
| 退出條件轉換率 | 在歷程逾時前觸發退出事件的設定檔百分比（例如，購買、註冊） | 退出條件點選計數/輸入的總數 |
| 轉換時間 | 從歷程進入到退出條件事件的平均持續時間 | Journey Analytics：從進入時間戳記到轉換事件時間戳記 |
| 歷程還車率 | 在每個步驟停止參與的設定檔百分比（流失分析） | 跨歷程步驟的CJA流失視覺效果 |
| 保留/重新參與率 | 目標設定檔返回作用中狀態的百分比 | CJA中的歷程後行為分析 |

## 應用程式

以下應用程式可用來實作此使用案例模式。

- **[!DNL Adobe Journey Optimizer](AJO)** — Journey Orchestration引擎、訊息製作、頻道設定、內容實驗、頻率和衝突管理，以及報告
- **[!DNL Adobe Real-Time Customer Data Platform](RT-CDP)** — 歷程專案對象的對象評估和定義、個人化的設定檔資料和條件分支
- **[!DNL Adobe Experience Platform](AEP)** — 設定檔存放區、身分服務、事件資料擷取和基礎資料基礎架構

## 相關文件

下列資源提供此實作中所使用功能的其他詳細資料。

### 歷程

- [開始使用歷程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [建立歷程](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [歷程屬性](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [發佈歷程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)
- [測試您的歷程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)

### 歷程活動

- [讀取對象活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [一般事件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [對象資格鑑定事件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)
- [條件活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [等待活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [在歷程中新增訊息](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [結束活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/end-activity)
- [設定自訂動作](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/using-custom-actions)

### 登入與退出管理

- [歷程專案管理](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [退出條件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)

### 管道設定

- [開始使用電子郵件設定](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [設定頻道介面](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [委派子網域](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [建立 IP 池](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [IP熱身計畫](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [設定簡訊頻道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [設定推播通知頻道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### 訊息製作與個人化

- [建立電子郵件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [設計電子郵件內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [使用電子郵件Designer內容元件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/content-components)
- [新增個人化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization語法](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [輔助函式](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [動態內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [使用內容範本](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [使用內容片段](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [預覽和測試您的內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### 內容實驗

- [開始使用內容實驗](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [建立內容實驗](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [內容實驗報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [統計計算](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-calculations)

### 頻率、衝突和優先順序

- [頻率規則](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [商業規則概觀](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [開始使用衝突與優先順序管理](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [優先順序分數](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [歷程上限和仲裁](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)
- [識別潛在衝突](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)

### 對象和細分

- [Segmentation Service概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [區段產生器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Profile Query Language參考](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)
- [串流區段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/api/streaming-segmentation)
- [邊緣分段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/api/edge-segmentation)

### 報告與分析

- [歷程即時報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [歷程全域報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [使用Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [AJO + CJA整合指南](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [Analysis Workspace概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [CJA概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)

### 同意與治理

- [Journey Optimizer中的同意](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)
- [資料控管概覽](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [管理隱藏清單](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### 資料基礎

- [XDM系統概覽](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Identity Service總覽](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [設定檔概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [計算屬性概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
