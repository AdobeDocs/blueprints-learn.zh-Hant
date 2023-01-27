---
title: Real-Time CDP與Adobe Campaign v7及Campaign Standard整合模式
description: 展示 Adobe Experience Platform 及其即時客戶設定檔和集中式細分工具如何與 Adobe Campaign 一起使用，以提供個人化的對話體驗。
solution: Real-time Customer Data Platform, Campaign
exl-id: a15e8304-2763-42fc-9978-11f2482ea8b8
source-git-commit: b18d491fdefc57762932d1570401b5437bf97c76
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Real-Time CDP與Adobe Campaign整合模式

展示 Adobe Experience Platform 及其即時客戶設定檔和集中式細分工具如何與 Adobe Campaign 一起使用，以提供個人化的對話體驗。

<br>

## 應用程式

* Adobe Experience PlatformReal-Time CDP
* Adobe Campaign v7或Campaign Standard

<br>

## 架構

<img src="assets/rtcdp-campaign-architecture.svg" alt="批次傳訊和Adobe Experience Platform整合模式的參考架構" style="width:100%; border:1px solid #4a4a4a" />

<br>

## 先決條件

* 建議在相同的IMS組織中布建Experience Platform和促銷活動，並使用Adobe Admin Console來存取使用者。 這也可確保客戶從行銷UI中使用解決方案切換器

<br>

## 護欄

### Adobe Campaign

* 僅支援Adobe Campaign單一組織單位部署
* Adobe Campaign 是所有啟用的個人資料之真相來源，代表著個人資料必須存在於 Adobe Campaign 中，且不應基於 Experience Platform 區段建立新的個人資料。
* Campaign 匯出工作流程最多每隔 4 小時執行一次
* Adobe Campaign broadLog、trackingLogs和無法傳送的位址的XDM結構和資料集不會立即提供，且必須進行設計和建置

### Experience PlatformCDP區段共用

* 建議20個區段限額
* 啟動限制為每24小時
* 僅聯合結構屬性可用於激活（不支援陣列/地圖/體驗事件）
* 建議每個區段最多20個屬性
* 具有「已實現」區段成員資格的所有設定檔的每個區段有一個檔案，或如果區段成員資格已新增為檔案中「已實現」和「已退出」設定檔的屬性
* 支援增量和完整區段匯出
* 不支援檔案加密

<br>

## 實作步驟

### Adobe Experience Platform

#### 結構/資料集

1. 在 Experience Platform 中基於客戶提供的資料[設定個別個人資料、體驗事件及多實體方案。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm)
1. 建立 broadLog、trackingLog、無法送達的地址及個人資料偏好設定 (可選)　的 Adobe Campaign 方案。
1. 在 Experience Platform 中為要擷取的資料[建立資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=zh-Hant)。
1. [在 Experience Platform 中新增使用標籤](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=zh-Hant)至資料集以便於治理。
1. [建立政策](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=zh-Hant)以在目標上執行治理。

#### 設定檔/身分

1. [建立任何客戶特定的命名空間。](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hant)
1. [新增身份至方案](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hant)。
1. [為個人資料啟用方案和資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=zh-Hant)。
1. 為[!UICONTROL 即時客戶個人資料]的不同檢視[設定合併政策](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=zh-Hant) (可選)。
1. 建立 Adobe Campaign 使用的區段。

#### 來源/目的地

1. [Experience Platform和Campaign Standard來源和說明](https://experienceleague.adobe.com/docs/campaign-standard/using/integrating-with-adobe-cloud/adobe-experience-platform/aep-sources-destinations/get-started-sources-destinations.html)
1. [Experience Platform和促銷活動v7來源和說明](https://experienceleague.adobe.com/docs/campaign-classic/using/integrating-with-adobe-experience-cloud/aep-sources-destinations/get-started-sources-destinations.html)
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


### 行動推送設定

* 兩種支援的推播通知與行動裝置整合方法：
   * Experience Platform Mobile SDK
   * Campaign行動SDK
* Experience Platform行動SDK路由：
   * 運用Adobe標籤和Campaign Classic擴充功能，設定您與Experience Platform行動SDK的整合
   * 需要Adobe標籤和資料收集的實用知識
   * 在Android和iOS中均需具備推播通知的行動開發體驗，才能部署SDK、與FCM(Android)和APNS(iOS)整合以取得推播代號、設定應用程式以接收推播通知並處理推播互動
* Campaign行動SDK
   * 請遵循 [Campaign SDK檔案]（Campaign Mobile SDK請遵循此處概述的部署檔案）

   >[!IMPORTANT]
   >如果您部署Campaign SDK，且正與其他Experience Cloud應用程式合作，則需要使用Experience Platform行動SDK來收集資料。 這會在裝置上建立重複的用戶端呼叫。

## 相關檔案

* [Adobe Experience Platform 文件](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hant)
* [Campaign Classic 文件](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=zh-Hant)
* [Campaign Standard 文件](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=zh-Hant)
* [Experience Platform Launch 文件](https://experienceleague.adobe.com/docs/launch.html?lang=zh-Hant)
* [Experience Platform Mobile SDK 文件](https://experienceleague.adobe.com/docs/mobile.html?lang=zh-Hant)
