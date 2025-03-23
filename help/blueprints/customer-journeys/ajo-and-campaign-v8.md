---
title: Journey Optimizer 搭配 Adobe Campaign v8 藍圖
description: 示範 Adobe Journey Optimizer 如何與 Adobe Campaign 搭配使用，以利用 Campaign 中的即時傳訊伺服器原生傳送訊息。
solution: Journey Optimizer, Campaign, Campaign v8, Campaign v8 Client Console
version: Campaign v8, Campaign v8 Client Console
exl-id: 447a1b60-f217-4295-a0df-32292c4742b0
source-git-commit: 1d10727899aaae6b8cd339ce10d2a520c73bdaa2
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 64%

---

# Journey Optimizer 搭配 Adobe Campaign v8 藍圖

示範Adobe [!DNL Journey Optimizer]如何與Adobe [!DNL Campaign]搭配使用，以利用[!DNL Campaign]中的即時傳訊伺服器以原生方式傳送訊息。

## 架構

<img src="assets/ajo-campaign-architecture.svg" alt="Journey Optimizer 參考架構藍圖" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

>[!IMPORTANT]
>可以同時使用 Journey Optimizer 和 Campaign 來彼此獨立傳送訊息，但有一些技術考量需加以考慮。如果您想沿用此路線，請與售前企業架構師合作，以確保您了解支援實施所需的內容。

## 先決條件

檢閱每個應用程式的下列先決條件。

### Adobe Experience Platform

* 必須先在系統中設定方案和資料集，才能設定 Journey Optimizer 資料來源
* 如果您想要觸發非規則型的事件，則針對體驗事件類別型方案，新增「Orchestration eventID」欄位群組
* 針對個別個人資料類別型方案，新增「個人資料測試詳細資料」欄位群組，以便載入測試個人資料以與 Journey Optimizer 搭配使用
* Journey Optimizer 和 Campaign 會布建在相同的 IMS 組織中

### Campaign v8

* 即時訊息服務（即訊息中心）的執行實例必須由 Adobe Managed Cloud Services 托管
* 所有訊息編寫都是在 Campaign 實例本身內完成

## 護欄

* [Journey Optimizer護欄產品限制](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)

* [護欄與端對端延遲指引](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html)

## 實施步驟

請遵循以下所述每個應用程式的實作。

### Adobe Experience Platform

#### 方案/資料集

1. 在 Experience Platform 中基於客戶提供的資料[設定個別個人資料、體驗事件及多實體方案。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm&amp;lang=zh-Hant)
1. （可選）為Adobe Campaign broadLog、trackingLog和無法傳遞的地址表格建立體驗事件類別型結構描述。
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

1. 使用串流API和來源聯結器[將資料擷取到 [!DNL Experience Platform]](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=zh-Hant)。

### Journey Optimizer

1. 設定您的[!DNL Experience Platform]資料來源，並決定應該快取哪些欄位做為啟動客戶歷程的設定檔資料的一部分。必須先在Journey Optimizer中設定以取得協調流程ID。 此協調 ID 然後提供給開發者與擷取一起使用。
1. 設定外部資料來源。
1. 設定Campaign執行個體的自訂動作。

### Campaign v8

* 訊息範本需要設定適當的個人化內容。
* 對於[!DNL Campaign]標準：匯出工作流程需要設定為將交易式訊息記錄匯出回Experience Platform。 建議最多每四小時執行一次。
* 對於[!DNL Campaign] v8.4，可利用Experience Platform中的Adobe [!DNL Campaign] Managed Services Source Connector，將傳遞和追蹤事件從Campaign同步至Experience Platform。 如需詳細資訊，請參閱[Source Connector](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=zh-Hant)檔案。

### 行動推播設定（選用）

1. 實作[!DNL Experience Platform] Mobile SDK以收集推播權杖和登入資訊，以連結回已知的客戶設定檔。
1. 運用 Adobe 標籤，並使用下列擴充功能建立行動屬性：
   * Adobe [!DNL Journey Optimizer] | Adobe [!DNL Campaign Classic] | Adobe [!DNL Campaign Standard]
   * Adobe [!DNL Experience Platform] [!DNL Edge Network]
   * [!DNL Edge Network]的身分
   * 行動裝置核心
1. 確保您擁有適用於行動應用程式部署與Web部署的專用資料流。
1. 如需詳細資訊，請參閱[Adobe Journey Optimizer行動指南](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-journey-optimizer)。

   >[!IMPORTANT]
   >如果需要透過 Journey Optimizer 傳送即時通訊，或需透過 Campaign 批次推播通知，行動權杖可能需要在 Journey Optimizer 和 Campaign 中收集。Campaign v8 需要專用 Campaign SDK 來擷取推播權杖。

## 相關文件

* [Journey Optimizer 文件](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=zh-Hant)
* [Journey Optimizer 產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/adobe-journey-optimizer.html)
* [Campaign v8 文件](https://experienceleague.adobe.com/docs/campaign-v8.html?lang=zh-Hant)
