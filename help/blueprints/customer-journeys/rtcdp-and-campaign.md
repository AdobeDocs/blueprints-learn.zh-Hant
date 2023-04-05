---
title: Real-Time CDP 與 Adobe Campaign v7 及 Campaign Standard 整合模式
description: 展示 Adobe Experience Platform 及其即時客戶設定檔和集中式細分工具如何與 Adobe Campaign 一起使用，以提供個人化的對話體驗。
solution: Real-time Customer Data Platform, Campaign
exl-id: a15e8304-2763-42fc-9978-11f2482ea8b8
source-git-commit: 5110ee2a7a079945475055cbcfdabf7cdcaa0ab5
workflow-type: ht
source-wordcount: '804'
ht-degree: 100%

---

# Real-Time CDP 與 Adobe Campaign 整合模式

展示 Adobe Experience Platform 及其即時客戶設定檔和集中式細分工具如何與 Adobe Campaign 一起使用，以提供個人化的對話體驗。

<br>

## 應用程式

* Adobe Experience Platform Real-Time CDP
* Adobe Campaign v7 或 Campaign Standard

<br>

## 架構

<img src="assets/rtcdp-campaign-architecture.svg" alt="批次訊息傳送與 Adobe Experience Platform 整合模式之參考架構" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## 先決條件

* 建議在相同的 IMS 組織中布建 Experience Platform 和 Campaign，並使用 Adobe Admin Console 來存取使用者。這也可確保客戶可以從行銷 UI 中使用解決方案切換器

<br>

## 護欄

### Adobe Campaign

* 僅支援 Adobe Campaign 單一組織單位部署
* Adobe Campaign 是所有啟用的個人資料之真相來源，代表著個人資料必須存在於 Adobe Campaign 中，且不應基於 Experience Platform 區段建立新的個人資料。
* Campaign 匯出工作流程最多每隔 4 小時執行一次
* Adobe Campaign broadLog、trackingLogs 和無法傳送的位址的 XDM 結構和資料集不會立即提供，且必須進行設計和建置

### Experience Platform CDP 區段共用

* 建議限制為 20 個區段
* 啟用限制於每隔 24 小時
* 僅聯合方案屬性可啟用 (不支援陣列/地圖/體驗事件)
* 建議每個區段不超過 20 項屬性
* 所有「已實現」區段會籍的個人資料為每個區段一個檔案；或者擁有「已實現」和「已退出」個人資料的檔案，則將區段匯集新增為一個屬性
* 支援漸進式和完整區段匯出
* 不支援檔案加密

<br>

## 實施步驟

### Adobe Experience Platform

#### 方案/資料集

1. 在 Experience Platform 中基於客戶提供的資料[設定個別個人資料、體驗事件及多實體方案。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm)
1. 建立 broadLog、trackingLog、無法送達的地址及個人資料偏好設定 (可選)　的 Adobe Campaign 方案。
1. 在 Experience Platform 中為要擷取的資料[建立資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=zh-Hant)。
1. [在 Experience Platform 中新增使用標籤](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=zh-Hant)至資料集以便於治理。
1. [建立政策](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=zh-Hant)以在目標上執行治理。

#### 個人資料/身份

1. [建立任何客戶特定的命名空間。](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hant)
1. [新增身份至方案](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hant)。
1. [為個人資料啟用方案和資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=zh-Hant)。
1. 為[!UICONTROL 即時客戶個人資料]的不同檢視[設定合併政策](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=zh-Hant) (可選)。
1. 建立 Adobe Campaign 使用的區段。

#### 來源/目標

1. [Experience Platform 和 Campaign Standard 來源和目標](https://experienceleague.adobe.com/docs/campaign-standard/using/integrating-with-adobe-cloud/adobe-experience-platform/aep-sources-destinations/get-started-sources-destinations.html?lang=zh-Hant)
1. [Experience Platform 和 Campaign v7 來源和目標](https://experienceleague.adobe.com/docs/campaign-classic/using/integrating-with-adobe-experience-cloud/aep-sources-destinations/get-started-sources-destinations.html?lang=zh-Hant)
1. 使用串流 API 和來源連接器[將資料擷取到 Experience Platform。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=zh-Hant)
1. 設定要與 Adobe Campaign 一起使用的 [!DNL Azure]Blob 儲存目標。

#### Adobe Campaign

1. 為個人資料、查詢資料及相關的傳送個人化資料設定方案。

>[!IMPORTANT]
>
>此時瞭解 Experience Platform 中什麼資料模型用於個人資料和事件資料很關鍵，因此您要知道 Adobe Campaign 中需要什麼資料。

#### 匯入工作流程

1. 將簡化的個人資料資料加入並擷取到 Adobe Campaign sFTP。
1. 將協調與訊息傳送個人化資料載入並擷取到 Adobe Campaign sFTP。
1. 透過工作流程從 [!DNL Azure]blob 擷取 Experience Platform 區段。

#### 匯出工作流程

1. 每隔四小時透過工作流程將 Adobe Campaign 記錄傳送回 Experience Platform (broadLog、trackingLog、無法傳遞的地址)。
1. 每隔四小時透過咨詢建置的工作流程，將個人資料偏好設定傳送回 Experience Platform (可選)。


### 行動推播設定

* 兩種支援的推播通知與行動裝置整合方法：
   * Experience Platform Mobile SDK
   * Campaign 行動 SDK
* Experience Platform Mobile SDK 路由：
   * 運用 Adobe 標籤和 Campaign Classic 擴充功能，設定您與 Experience Platform Mobile SDK 的整合
   * 需要 Adobe 標籤和資料收集的實用知識
   * 在 Android 和 iOS 中均需推播通知的行動開發體驗，才能部署 SDK、與 FCM (Android) 和 APNS (iOS) 整合以取得推播代號、設定應用程式以接收推播通知並處理推播互動
* Campaign 行動 SDK
   * 請遵循 [Campaign SDK 文件]（Campaign Mobile SDK
請遵循此處概述的部署檔案）

   >[!IMPORTANT]
   >如果您部署 Campaign SDK，且正與其他 Experience Cloud 應用程式合作，則需要使用 Experience Platform Mobile SDK 來收集資料。這會在裝置上建立重複的用戶端呼叫。

## 相關文件

* [Adobe Experience Platform 文件](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hant)
* [Campaign Classic 文件](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=zh-Hant)
* [Campaign Standard 文件](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=zh-Hant)
* [Experience Platform Launch 文件](https://experienceleague.adobe.com/docs/launch.html?lang=zh-Hant)
* [Experience Platform Mobile SDK 文件](https://experienceleague.adobe.com/docs/mobile.html?lang=zh-Hant)
