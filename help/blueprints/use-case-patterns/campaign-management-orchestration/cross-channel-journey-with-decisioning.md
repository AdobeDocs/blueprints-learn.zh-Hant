---
title: 具有決策的跨頻道歷程
description: 瞭解如何結合即時決策來協調多步驟歷程，以選取最佳頻道、內容或選件。
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: eabdd91f-bb7d-4de3-adb5-5940d3ca4a78
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1983'
ht-degree: 5%

---

# 具有決策的跨頻道歷程

本指南說明具有決策功能的跨頻道歷程使用案例模式，其使用[!DNL Adobe Journey Optimizer]和[!DNL Adobe Real-Time Customer Data Platform]來協調多步驟、多頻道歷程，這些歷程包含一個或多個歷程節點上的即時決策。 它專為需要瞭解此模式的功能、其支援的業務目標、其啟用的戰術使用案例以及所涉及的Adobe應用程式的解決方案架構師、行銷技術人員和實作工程師所設計。

具有決策的跨頻道歷程是[!DNL Adobe Experience Platform]生態系統中最複雜的行銷活動協調模式。 透過結合即時決策（使用[!DNL AJO]決策評估設定檔的目前內容，並在歷程畫布內的一個或多個決策點動態選取最佳管道、內容或選件），來擴充多步驟協調歷程。

## 使用案例模式

**具有決策的跨頻道歷程**

協調多步驟、多頻道歷程，其整合一或多個節點的即時決策，以選取最佳頻道、內容或選件。

**執行計畫：**&#x200B;對象評估>歷程執行>決定節點>頻道選擇>訊息傳送>報告

## 使用案例概述

組織越來越需要提供最適化、個人化的客戶歷程，這些歷程會動態回應每個人的即時內容，而不是遵循固定的預先決定順序。 客戶的偏好管道、參與記錄、忠誠度等級、預測期限值以及目前產品興趣，都會影響每個接觸點下的最佳動作。

具有決策的跨頻道歷程結合兩種強大的[!DNL AJO]功能來解決此需求：歷程協調（管理多步驟流程、時間、條件和頻道傳送）和決策（評估適用性規則、套用排名策略，並在每個決策點選取最佳優惠或內容變體）。

此模式適用於下列情況：

- 歷程必須動態地適應每個設定檔的即時狀態，而不是遵循固定的頻道或內容順序
- 多個選件、內容變體或管道為一個或多個歷程節點的候選專案，應根據設定檔內容選取最佳選項
- 需要AI輔助或公式型排名，才能在整個歷程中最佳化優惠選擇
- 企業想要將管道選擇邏輯和優惠方案管理整合至集中的決策架構，而非維持複雜的分支邏輯

目標受眾包括管理生命週期計畫、忠誠度歷程、回傳序列和上線流程的行銷人員，其中大規模個人化需要在每個接觸點進行自動化決策。

>[!NOTE]
>如果您的歷程不需要在個別節點進行動態決策，例如固定順序的Nurture或上線計畫，請參閱[多步驟協調歷程](multi-step-orchestrated-journey.md)。 該模式設定起來比較簡單，而且不需要AJO Decisioning。

## 主要業務目標

此使用案例模式支援下列業務目標。

**[提供個人化的客戶體驗](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**
根據個別偏好設定、行為和生命週期階段量身打造內容、選件和訊息。
**KPI：**&#x200B;參與度、轉換率、客戶滿意度(CSAT)

**[提高客戶忠誠度和期限值](../../business-objectives/revenue-monetization/increase-customer-loyalty-lifetime-value.md)**
透過忠誠計畫、獎勵和個人化參與，深化客戶關係並最大化長期價值。
**KPI：**&#x200B;客戶期限值、保留率、向上銷售/交叉銷售%

**[改善客戶保留率](../../business-objectives/customer-experience/improve-customer-retention.md)**
透過價值導向的體驗和持續培養的關係，讓現有客戶持續參與並更新。
**KPI：**&#x200B;保留率、客戶期限值、參與度

**[推動交叉銷售和追加銷售收入](../../business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)**
根據行為和購買記錄，向現有客戶推廣補充性和優質產品或服務。
**KPI：**&#x200B;向上銷售/交叉銷售%、遞增收入、客戶期限值

## 戰術使用案例範例

以下案例說明如何將具有決策的跨管道歷程應用於實踐。

- **最適化回饋歷程** — 多步驟歷程，決策會根據每個設定檔的參與歷史記錄選取頻道（電子郵件、推播或簡訊），並根據預測的期限值以動態方式選取最佳激勵優惠
- **次佳動作生命週期歷程** — 決定決定要在客戶生命週期的每個階段進行溝通，從入門內容、交叉銷售優惠、忠誠度獎勵或保留獎勵中進行選取
- **使用動態內容選擇進行個人化上線** — 新的客戶上線歷程，其中每個接觸點使用決策來選取最相關的產品教育內容、提示或啟用優惠
- **具有個人化獎勵的跨管道忠誠度方案歷程** — 忠誠度會員在歷程中取得進展，決策會根據層級、購買歷史記錄和類別相關性來選取個人化獎勵優惠
- **動態重新參與管道和獎勵最佳化** — 休眠客戶重新參與，其中動態選取外聯管道和獎勵以最大化回應機率
- **具有AI排名內容推薦的客戶生命週期Nurture** — 持續的Nurture歷程，其中AI排名決策會從每個接觸點選取最相關的內容或產品推薦

## 關鍵績效指標

使用下列KPI來評估此使用案例模式的成效。

| KPI | 說明 | 測量方法 |
| --- | --- | --- |
| 歷程完成率 | 完成完整歷程的設定檔百分比 | 歷程報告：已完成/已進入 |
| 優惠接受率 | 參與決策所選優惠方案的百分比（已點按、已贖回） | 決策報告：優惠點按數/優惠曝光數 |
| 管道參與率 | 在歷程中使用的每個管道的開啟和點按率 | 歷程報告中的每管道傳遞量度 |
| 轉換率 | 完成目標轉換動作的歷程參與者百分比 | 歷程退出事件追蹤或CJA funnel分析 |
| 遞補優惠率 | 傳回遞補優惠而非個人化優惠的決策請求百分比 | 決策報告：遞補選擇/選擇總數 |
| 客戶期限值影響 | 歷程參與者與控制組的CLV變更 | CJA同類群組分析搭配保留比較 |
| 交叉銷售/追加銷售收入 | 歸因於決策所選優惠的遞增收入 | 優惠方案導向轉換的CJA歸因分析 |
| 決策排名有效性 | AI排名選件與隨機/優先順序型選擇之間的效能差異 | A/B實驗比較排名策略 |

## 應用程式

以下應用程式可用來實作此使用案例模式。

- **[!DNL Adobe Journey Optimizer] ([!DNL AJO])** — 歷程協調（多步驟畫布設計、進入條件、等待、條件、退出條件）、跨管道的訊息編寫、管道表面設定、衝突和優先順序管理
- **[!DNL Adobe Journey Optimizer]決策** — 優惠和內容專案管理、適用性規則、排名策略（優先順序、公式、AI）、決定原則、位置、遞補優惠
- **[!DNL Adobe Real-Time Customer Data Platform] ([!DNL RT-CDP])** — 歷程專案與優惠方案適用性區段的對象評估、使用運算屬性和傾向分數擴充設定檔、同意和治理強制執行
- **[!DNL Adobe Experience Platform] ([!DNL AEP])** — 即時客戶設定檔存放區、跨管道解析的身分服務、資料模型及擷取基礎結構

## 相關文件

下列資源提供在此使用案例模式中所使用功能的其他詳細資料。

### Journey orchestration

- [開始使用歷程](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [建立歷程](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [歷程屬性](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [讀取對象活動](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [一般事件](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [對象資格鑑定事件](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)
- [條件活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [等待活動](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [在歷程中新增訊息](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [退出條件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [歷程專案管理](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [測試您的歷程](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [發佈歷程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)

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

### 管道設定

- [開始使用電子郵件設定](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [委派子網域](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [建立 IP 池](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [IP熱身計畫](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [電子郵件表面設定](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [設定簡訊頻道](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [設定推播通知頻道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### 訊息製作與個人化

- [建立電子郵件](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/channels/email/create-email)
- [設計電子郵件內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [新增個人化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization語法](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [動態內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [使用內容範本](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [使用內容片段](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [預覽和測試您的內容](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### 衝突、優先順序和頻率管理

- [衝突與優先順序管理概觀](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [優先順序分數](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [識別潛在衝突](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/conflict-prioritization/conflicts)
- [歷程上限和仲裁](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/conflict-prioritization/journey-capping)
- [頻率規則](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)

### 對象和細分

- [Segmentation Service概述](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/home)
- [區段產生器UI指南](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/ui/segment-builder)
- [串流區段](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [邊緣分段](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/methods/edge-segmentation)
- [對象構成](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/ui/audience-composition)
- [Profile Query Language參考](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/pql/overview)

### 報告與分析

- [歷程即時報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [歷程全域報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [使用Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [AJO + CJA整合指南](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [CJA概觀](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-overview/cja-overview)
- [Analysis Workspace概觀](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/home)

### 設定檔與身分

- [即時客戶個人檔案總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/home)
- [Identity Service總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/identity/home)
- [合併原則概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/merge-policies/overview)
- [計算屬性概述](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/computed-attributes/overview)
- [Customer AI概述](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/intelligent-services/customer-ai/overview)

### 資料控管和同意

- [資料控管概覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/home)
- [Journey Optimizer中的同意](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)
- [管理隱藏清單](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### 護欄

- [Journey Optimizer護欄](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/get-started/guardrails)
- [即時客戶個人檔案護欄](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/guardrails)
- [Identity Service護欄](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/identity/guardrails)
