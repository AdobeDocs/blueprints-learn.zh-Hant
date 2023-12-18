---
title: Journey Optimizer 搭配 Adobe Campaign v8 藍圖
description: 示範 Adobe Journey Optimizer 如何與 Adobe Campaign 搭配使用，以利用 Campaign 中的即時傳訊伺服器原生傳送訊息。
solution: Journey Optimizer, Campaign, Campaign v8, Campaign Classic v7, Campaign Standard
exl-id: 447a1b60-f217-4295-a0df-32292c4742b0
source-git-commit: 5f9384abe7f29ec764428af33c6dd1f0a43f5a89
workflow-type: tm+mt
source-wordcount: '645'
ht-degree: 98%

---

# Journey Optimizer 搭配 Adobe Campaign v8 藍圖

示範 Adobe Journey Optimizer 如何與 Adobe Campaign 搭配使用，以利用 Campaign 中的即時傳訊伺服器原生傳送訊息。

<br>

## 架構

<img src="assets/ajo-campaign-architecture.svg" alt="Journey Optimizer 參考架構藍圖" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

>[!IMPORTANT]
>可以同時使用 Journey Optimizer 和 Campaign 來彼此獨立傳送訊息，但有一些技術考量需加以考慮。如果您想沿用此路線，請與售前企業架構師合作，以確保您了解支援實施所需的內容。

<br>

## 先決條件

### Adobe Experience Platform

* 必須先在系統中設定方案和資料集，才能設定 Journey Optimizer 資料來源
* 如果您想要觸發非規則型的事件，則針對體驗事件類別型方案，新增「Orchestration eventID」欄位群組
* 針對個別個人資料類別型方案，新增「個人資料測試詳細資料」欄位群組，以便載入測試個人資料以與 Journey Optimizer 搭配使用
* Journey Optimizer 和 Campaign 會布建在相同的 IMS 組織中

### Campaign v8

* 即時訊息服務（即訊息中心）的執行實例必須由 Adobe Managed Cloud Services 托管
* 所有訊息編寫都是在 Campaign 實例本身內完成

<br>

## 護欄

[Journey Optimizer 護欄產品連結](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=zh-Hant)

[護欄和端對端延遲指引](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html)

## 實施步驟

### Adobe Experience Platform

#### 方案/資料集

1. 在 Experience Platform 中基於客戶提供的資料[設定個別個人資料、體驗事件及多實體方案。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm&amp;lang=zh-Hant)
1. 為 Adobe Campaign broadLog、trackingLog 和無法傳送的位址表建立以體驗事件類別為基礎的方案（選用）。
1. 在 Experience Platform 中為要擷取的資料[建立資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=zh-Hant)。
1. 在 Experience Platform 中[新增資料使用標籤](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=zh-Hant)至資料集以便於治理。
1. [建立政策](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=zh-Hant)以在目標上執行治理。

#### 個人資料/身份

1. [建立任何客戶特定的命名空間。](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hant)
1. [新增身份至方案](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hant)。
1. [為個人資料啟用方案和資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=zh-Hant)。
1. 為[!UICONTROL 即時客戶個人資料]的不同檢視[設定合併政策](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=zh-Hant) (可選)。
1. 建立 Journey 使用的區段。

#### 來源/目標

1. 使用串流 API 和來源連接器[將資料擷取到 Experience Platform。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=zh-Hant)

### Journey Optimizer

1. 設定 Experience Platform 資料來源，並確定應快取哪些欄位作為個人資料的一部分。用來起始客戶歷程的串流資料必須先在 Journey Optimizer 中設定，才能取得協調 ID。然後將此協調 ID 提供給開發人員在擷取時使用。
1. 設定外部資料來源
1. 設定 Campaign 實例的自訂動作

### Campaign v8

* 傳訊範本必須以適當的個人化內容來設定
* 適用於 Campaign Standard — 匯出工作流程需要設定，以將交易式訊息記錄檔匯出回 Experience Platform。建議最多每 4 小時執行一次。
* 有了 Campaign v8.4，您就可以在 Experience Platform 中運用 Adobe Campaign Managed Services Source Connector，將傳送和追蹤事件從 Campaign 同步至 Experience Platform。如需詳細資訊，請參閱來源連接器文件。[連結](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=zh-Hant)

### 行動推播設定（選用）

1. 實作 Experience Platform Mobile SDK 以收集推播權杖和登入資訊，以系結回已知的客戶個人資料
1. 運用 Adobe 標籤，並使用下列擴充功能建立行動屬性：
   * Adobe Journey Optimizer | Adobe Campaign Classic | Adobe Campaign Standard
   * Adobe Experience Platform Edge Network
   * 邊緣網路的身分識別
   * 行動裝置核心
1. 針對行動應用程式部署與網頁部署，確保您擁有專屬的資料流
1. 如需更多詳細資訊，請參閱 [Adobe Journey Optimizer 行動指南](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-journey-optimizer)

   >[!IMPORTANT]
   >如果需要透過 Journey Optimizer 傳送即時通訊，或需透過 Campaign 批次推播通知，行動權杖可能需要在 Journey Optimizer 和 Campaign 中收集。Campaign v8 需要專用 Campaign SDK 來擷取推播權杖。

<br>

## 相關文件

* [Journey Optimizer 文件](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=zh-Hant)
* [Journey Optimizer 產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/adobe-journey-optimizer.html)
* [Campaign v8 文件](https://experienceleague.adobe.com/docs/campaign-v8.html?lang=zh-Hant)
