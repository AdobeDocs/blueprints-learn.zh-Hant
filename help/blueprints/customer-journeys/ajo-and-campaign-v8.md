---
title: Journey Optimizer搭配Adobe Campaign v8blueprint
description: 示範Adobe Journey Optimizer如何與Adobe Campaign搭配使用，以利用Campaign中的即時訊息伺服器原生傳送訊息
solution: Journey Optimizer, Campaign, Campaign v8, Campaign Classic v7, Campaign Standard
exl-id: 447a1b60-f217-4295-a0df-32292c4742b0
source-git-commit: b18d491fdefc57762932d1570401b5437bf97c76
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Journey Optimizer搭配Adobe Campaign v8blueprint

示範如何搭配Adobe Journey Optimizer使用Adobe Campaign，利用Campaign中的即時訊息伺服器以原生方式傳送訊息。

<br>

## 架構

<img src="assets/ajo-campaign-architecture.svg" alt="參考架構Journey Optimizer Blueprint" style="width:100%; border:1px solid #4a4a4a" />

>[!IMPORTANT]
>可以同時使用Journey Optimizer和Campaign來彼此獨立傳送訊息，但有一些技術考量需加以考慮。 如果您想沿用此路線，請與售前企業架構師合作，以確保您了解支援實施所需的內容。

<br>

## 先決條件

### Adobe Experience Platform

* 必須先在系統中設定結構和資料集，才能設定Journey Optimizer資料來源
* 如果您想要觸發非規則型事件的事件，則針對體驗事件類別型結構新增「Orchestration eventID」欄位群組
* 針對個別設定檔類別型結構，新增「設定檔測試詳細資料」欄位群組，以便載入測試設定檔以與Journey Optimizer搭配使用
* Journey Optimizer和Campaign會布建在相同的IMS組織中

### Campaign v8

* 即時訊息服務（即訊息中心）的執行例項必須由Adobe管理Cloud Services托管
* 所有訊息編寫都是在Campaign執行個體本身內完成

<br>

## 護欄

[Journey Optimizer護欄產品連結](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=en)

### 其他Journey Optimizer護欄

* 今天可透過API使用上限設定，以確保目的地系統未飽和至故障點。 這表示超過上限的訊息會完全刪除，且不會傳送。 不支援限制。
   * 最大連接數 — 目標可處理的最大http/s連接數
   * 呼叫計數上限 — periodInMs參數中要進行的呼叫數上限
   * periodInMs — 以毫秒為單位的時間
* 由區段會籍發起的歷程可以兩種模式操作：
   * 批次區段（每24小時重新整理一次）
   * 串流區段（&lt;5分鐘資格）
* 批次區段 — 需要確保您瞭解符合資格使用者的每日流量，並確保目標系統可以處理每個歷程以及所有歷程的高載輸送量
* 串流區段 — 需要確保個人資料資格的初始高載可隨每個歷程及所有歷程中符合資格的每日串流流量一起處理
* 不支援的決策管理
* 不支援業務事件
* 傳出整合至第三方系統
   * 不支援單個靜態IP，因為我們的基礎架構是多租戶（必須允許列出所有資料中心IP）
   * 自訂動作僅支援POST和PUT方法
   * 驗證支援：token |密碼 | OAuth2
* 無法在各種沙箱之間封裝及移動Adobe Experience Platform或Journey Optimizer的個別元件。 必須在新環境中重新實作

<br>

### 促銷活動(v8)

* 消息中心的執行實例必須由Adobe管理Cloud Services托管
* 報文傳送吞吐量
   * AC(v8)每小時最多1M（基於包）
* AC(v8)不支援報文中的「決策管理」
* 未對Campaign進行傳出API呼叫限制
* 有了Campaign v8.4，您就可以在Experience Platform中運用Adobe Campaign Managed Services Source Connector，將傳送和追蹤事件從Campaign同步至Experience Platform。 如需詳細資訊，請參閱來源連接器檔案。 [連結](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html)

<br>

## 實作步驟

### Adobe Experience Platform

#### 結構/資料集

1. 在 Experience Platform 中基於客戶提供的資料[設定個別個人資料、體驗事件及多實體方案。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm)
1. 為Adobe Campaign broadLog、trackingLog和無法傳送的位址表建立以體驗事件類別為基礎的結構（選用）。
1. 在 Experience Platform 中為要擷取的資料[建立資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=zh-Hant)。
1. [在 Experience Platform 中新增使用標籤](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=zh-Hant)至資料集以便於治理。
1. [建立政策](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=zh-Hant)以在目標上執行治理。

#### 設定檔/身分

1. [建立任何客戶特定的命名空間。](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hant)
1. [新增身份至方案](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hant)。
1. [為個人資料啟用方案和資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=zh-Hant)。
1. 為[!UICONTROL 即時客戶個人資料]的不同檢視[設定合併政策](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=zh-Hant) (可選)。
1. 建立歷程使用情形的區段。

#### 來源/目的地

1. 使用串流 API 和來源連接器[將資料擷取到 Experience Platform。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=zh-Hant)

### Journey Optimizer

1. 設定Experience Platform資料來源，並決定在設定檔串流資料中應快取哪些欄位，這些資料用來起始客戶歷程，必須先在Journey Optimizer中設定，才能取得協調ID。 然後，系統會將此協調ID提供給開發人員，以便用於擷取
1. 設定外部資料來源
1. 設定Campaign執行個體的自訂動作

### Campaign v8

* 傳訊範本必須以適當的個人化內容來設定
* 針對Campaign standard — 匯出工作流程需要設定，以將交易式訊息記錄檔匯出回Experience Platform。 建議最多每4小時執行一次。
* 若使用Campaign v8.4，可在Experience Platform中運用Adobe Campaign Managed Services來源連接器，將傳送和追蹤事件從Campaign同步至Experience Platform。 如需詳細資訊，請參閱來源連接器檔案。 [連結](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html)

### 行動推送設定（選用）

1. 實作Experience PlatformMobile SDK以收集推送代號和登入資訊，以系結回已知的客戶設定檔
1. 運用Adobe標籤，並使用下列擴充功能建立行動屬性：
   * Adobe Journey Optimizer | Adobe Campaign Classic | Adobe Campaign Standard
   * Adobe Experience Platform Edge Network
   * 身分 邊緣網路
   * 行動裝置核心
1. 針對行動應用程式部署與網頁部署，確保您擁有專屬的資料流
1. 如需詳細資訊，請參閱 [Adobe Journey Optimizer Mobile指南](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-journey-optimizer)

   >[!IMPORTANT]
   >如果需要透過Journey Optimizer傳送即時通訊，或需透過Campaign批次推播通知，行動代號可能需要在Journey Optimizer和Campaign中收集。 Campaign v8需要專用Campaign SDK來擷取推播代號。

<br>

## 相關檔案

* [Journey Optimizer 文件](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=en)
* [Journey Optimizer產品說明](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer.html)
* [Campaign v8檔案](https://experienceleague.adobe.com/docs/campaign-v8.html?lang=en)
