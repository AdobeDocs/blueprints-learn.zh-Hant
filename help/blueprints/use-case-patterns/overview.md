---
title: 使用案例模式
description: 瞭解實作Adobe Experience Platform和應用程式以實現關鍵業務目標的使用案例模式。
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
doc-type: overview-page
exl-id: 58caa6ad-0d1c-4290-9614-c68c9c9028bb
source-git-commit: 27f7e230982807ec70ca96af7f737944a6588f27
workflow-type: tm+mt
source-wordcount: '760'
ht-degree: 0%

---

# 使用案例模式

使用案例模式會為Adobe Experience Platform和應用程式定義可重複的實作方法。 每個模式都描述特定功能、提供功能的功能鏈、相關的應用程式，以及所支援的[關鍵業務目標](/help/blueprints/business-objectives/overview.md)。

使用下表來尋找符合您實作需求的模式，然後依照連結連結，前往完整的實作參考，包括選項、階段、決定指引和Experience League檔案。

## 對象建立和啟用

以下模式可協助您跨頻道和目的地建立、評估及啟用對象區段。

| 圖樣 | 主要功能 | 核心解決方案 |
| --- | --- | --- |
| [對目的地的對象啟用](audience-building-activation/audience-activation-to-destinations.md) | 評估對象區段並將其發佈到外部目的地以進行定位或抑制 | [!DNL Real-Time CDP] |
| [對象Collaboration](audience-building-activation/audience-collaboration-segment-match.md) | 使用「區段比對」在沙箱或組織間共用和比對受眾區段 | [!DNL Real-Time CDP], [!DNL Experience Platform] |
| [事件轉送](audience-building-activation/event-forwarding.md) | 將透過Edge Network收集的即時事件資料轉送至非Adobe目的地 | [!DNL Experience Platform] （Edge Network，事件轉送） |
| [B2B對象啟用](audience-building-activation/b2b-audience-activation.md) | 在網頁、電子郵件和廣告頻道中啟用以帳戶為基礎的B2B對象 | [!DNL Real-Time CDP] B2B edition |

## 個人化

以下模式會在網頁和應用程式介面中，為已知和未知的訪客提供量身打造的體驗。

| 圖樣 | 主要功能 | 核心解決方案 |
| --- | --- | --- |
| [匿名訪客網頁個人化](personalization/anonymous-visitor-web-personalization.md) | 根據工作階段中的行為訊號，為無法識別的訪客提供個人化內容 | [!DNL Journey Optimizer] （Web管道），[!DNL Real-Time CDP] |
| [已知訪客的網頁/應用程式個人化](personalization/known-visitor-web-app-personalization.md) | 根據即時設定檔和區段會籍，將個人化內容、優惠或促銷活動提供給已識別的訪客 | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [Offer Decisioning](personalization/offer-decisioning.md) | 使用集中式決定邏輯，跨頻道為設定檔選取次佳優惠或內容 | [!DNL Journey Optimizer] （決策），[!DNL Real-Time CDP] |
| [行為建議](personalization/behavioral-recommendation.md) | 使用選擇策略和排名模型產生專案和內容推薦 | [!DNL Journey Optimizer] （決策），[!DNL Real-Time CDP] |

## 行銷活動管理與協調

以下模式涵蓋跨頻道已排程、已觸發和多步驟訊息傳送。

| 圖樣 | 主要功能 | 核心解決方案 |
| --- | --- | --- |
| [批次傳出訊息啟用](campaign-management-orchestration/batch-outbound-message-activation.md) | 評估對象，然後在單一批次執行中傳遞已排程的傳出訊息 | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [事件觸發訊息](campaign-management-orchestration/event-triggered-messaging.md) | 接聽即時行為或系統事件，然後將內容相關訊息傳遞至觸發的設定檔 | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [多步驟協調歷程](campaign-management-orchestration/multi-step-orchestrated-journey.md) | 透過分支和多點觸控歷程，使用等待、條件和多個訊息動作來引導設定檔 | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [具有決策的跨頻道歷程](campaign-management-orchestration/cross-channel-journey-with-decisioning.md) | 協調包含即時決策的多步驟歷程，以選取最佳頻道、內容或選件 | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [購買群組行銷與歷程管理](campaign-management-orchestration/buying-group-based-marketing.md) | 開發符合潛在客戶購買群組資格的帳戶層級歷程，以改善B2B行銷效率 | [!DNL Journey Optimizer] B2B edition，[!DNL Real-Time CDP] B2B edition |

## 分析

以下模式支援跨管道行為和效能分析。

| 圖樣 | 主要功能 | 核心解決方案 |
| --- | --- | --- |
| [Customer Analytics與insight世代](analysis/customer-analytics-insight-generation.md) | 建立跨管道分析工作區、計算量度和儀表板，以進行行為和效能分析 | [!DNL Customer Journey Analytics], [!DNL Experience Platform] |
| [B2B分析](analysis/b2b-analytics.md) | 在跨管道客戶歷程分析中加入B2B帳戶層級資訊 | [!DNL Customer Journey Analytics] B2B edition，[!DNL Real-Time CDP] B2B edition |

## 對話體驗

以下模式可在數位屬性上啟用AI支援、品牌安全的對話互動。

| 圖樣 | 主要功能 | 核心解決方案 |
| --- | --- | --- |
| [Brand Concierge對話體驗](conversational-experience/brand-concierge-conversational-experience.md) | 將數位財產轉換為AI支援、品牌安全的對話體驗，以引導客戶探索 | [!DNL Brand Concierge], [!DNL Experience Platform], [!DNL Real-Time CDP] |

## 案例選擇器

當案例可能適合多個模式時，請使用此指南。 回答分支問題以尋找主要模式，然後選擇性延伸並列出模式。

### 以獎勵優惠回饋

*已失效的客戶已有90天未購買。 您想要透過目標優惠重新與他們互動。*

- **優惠方案選擇是否為動態的（不同客戶會根據資格或排名獲得不同的優惠方案）？**
   - 是→[Offer Decisioning](personalization/offer-decisioning.md)作為優惠方案圖層，封裝在[多步驟協調歷程](campaign-management-orchestration/multi-step-orchestrated-journey.md)中，適用於重新參與順序
   - 沒有（所有合格失效客戶都有相同優惠），僅→[多步驟協調歷程](campaign-management-orchestration/multi-step-orchestrated-journey.md)

### 購買後的後續追蹤

*客戶剛完成購買。 您想要傳送確認、交叉銷售建議和忠誠度獎勵通知。*

- **此序列是否需要根據即時事件（例如，已申請獎勵、已檢閱產品）的回應式分支？**
   - 是→[多步驟協調歷程](campaign-management-orchestration/multi-step-orchestrated-journey.md)
   - [批次傳出訊息啟用](campaign-management-orchestration/batch-outbound-message-activation.md)→無（固定順序，無分支）
- **它是否包含個人化產品推薦？**
   - 是→在內容層使用[行為建議](personalization/behavioral-recommendation.md)延伸

### 忠誠度里程碑個人化

*客戶達到新的忠誠度等級。 您想要顯示個人化網頁內容，並傳送祝賀訊息。*

- **網頁內容是否個人化（每個層級或區段有不同的內容）？**
   - 是→網頁表面的[已知訪客網頁/應用程式個人化](personalization/known-visitor-web-app-personalization.md)
- **傳出訊息是否為單一傳送或培養順序？**
   - 單一傳送→[事件觸發的訊息](campaign-management-orchestration/event-triggered-messaging.md)
   - [多步→協調歷程](campaign-management-orchestration/multi-step-orchestrated-journey.md)的順序

### 重新參與行銷活動

*非使用中使用者的區段需要多重觸控重新啟用順序。*

- **個別訊息需要即時從多個優惠方案變體中進行選擇嗎？**
   - 是→[具有決策的跨頻道歷程](campaign-management-orchestration/cross-channel-journey-with-decisioning.md)
   - 沒有→ [多步驟協調歷程](campaign-management-orchestration/multi-step-orchestrated-journey.md)
