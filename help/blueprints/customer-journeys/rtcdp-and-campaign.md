---
title: 具有 [!DNL Campaign] v7和Campaign Standard整合模式的Real-Time CDP
description: 展示Adobe Experience Platform及其即時客戶設定檔和集中式細分工具如何與Adobe [!DNL Campaign] 搭配使用，以提供個人化的對話。
solution: Real-Time Customer Data Platform, [!DNL Campaign]
exl-id: a15e8304-2763-42fc-9978-11f2482ea8b8
source-git-commit: 258aea64f6ff2f620b1adaa0c9ba4b02b47acce9
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 42%

---

# 具有[!DNL Campaign]整合模式的[!DNL Real-Time Customer Data Platform]

展示Adobe [!DNL Experience Platform]及其即時客戶設定檔和集中式細分工具如何與Adobe [!DNL Campaign]搭配使用，以提供個人化的對話。

## 應用程式

* Adobe [!DNL Experience Platform Real-Time Customer Data Platform]
* Adobe [!DNL Campaign] v7或[!DNL Campaign Standard]

## 架構

<img src="assets/rtcdp-campaign-architecture.svg" alt="批次訊息傳送與 Adobe Experience Platform 整合模式之參考架構" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## 先決條件

* 建議將Experience Platform和[!DNL Campaign]布建在相同的IMS組織中，並利用Adobe Admin Console進行使用者存取。 這也可確保客戶可以從行銷 UI 中使用解決方案切換器

## 護欄

以下各節將說明這項整合的護欄。

### Adobe [!DNL Campaign]

* 僅支援Adobe [!DNL Campaign]單一組織單位部署
* Adobe [!DNL Campaign]是所有作用中設定檔的信任來源，表示設定檔必須存在於Adobe [!DNL Campaign]中，且不應根據Experience Platform區段建立新設定檔。
* [!DNL Campaign]匯出工作流程最多每4小時執行一次
* Adobe [!DNL Campaign] broadLog、trackingLogs和無法傳遞的位址的XDM結構描述和資料集並非現成可用，必須設計和建置

### Real-Time Customer Data Platform區段共用

* 請參閱RTCDP [!DNL Campaign]目的地聯結器 — [RTCDP促銷活動連線](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign-managed-services.html?lang=zh-Hant)

* 檢視 [!DNL Real-Time Customer Profile Data] 和區段[&#128279;](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hant)的預設護欄

## 實施步驟

以下各節將說明每個應用程式的實施步驟。

### Adobe Experience Platform

#### 方案/資料集

1. 在 Experience Platform 中基於客戶提供的資料[設定個別個人資料、體驗事件及多實體方案。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm&amp;lang=zh-Hant)
1. 為broadLog、trackingLog、無法傳遞的地址和設定檔偏好設定建立Adobe [!DNL Campaign]結構描述（選用）。
1. 在 Experience Platform 中為要擷取的資料[建立資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=zh-Hant)。
1. 在 Experience Platform 中[新增資料使用標籤](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=zh-Hant)至資料集以便於治理。
1. [建立政策](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=zh-Hant)以在目標上執行治理。

#### 個人資料/身份

1. [建立任何客戶特定的命名空間。](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hant)
1. [新增身份至方案](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hant)。
1. [為個人資料啟用方案和資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=zh-Hant)。
1. 為[!UICONTROL 即時客戶個人資料]的不同檢視[設定合併政策](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=zh-Hant) (可選)。
1. 建立Adobe [!DNL Campaign]使用的區段。

#### 來源/目標

1. [Experience Platform和 [!DNL Campaign] 標準來源和設計](https://experienceleague.adobe.com/docs/campaign-standard/using/integrating-with-adobe-cloud/adobe-experience-platform/aep-sources-destinations/get-started-sources-destinations.html?lang=zh-Hant)
1. [Experience Platform和 [!DNL Campaign] v7來源和設計](https://experienceleague.adobe.com/docs/campaign-classic/using/integrating-with-adobe-experience-cloud/aep-sources-destinations/get-started-sources-destinations.html?lang=zh-Hant)
1. 使用串流 API 和來源連接器[將資料擷取到 Experience Platform。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=zh-Hant)
1. 設定[!DNL Azure] Blob儲存體目的地，以搭配Adobe [!DNL Campaign]使用。

#### Adobe [!DNL Campaign]

1. 為個人資料、查詢資料及相關的傳送個人化資料設定方案。

>[!IMPORTANT]
>
>此時瞭解設定檔和事件資料的Experience Platform中的資料模型非常重要，這樣您才能知道Adobe [!DNL Campaign]中需要哪些資料。

#### 匯入工作流程

1. 將簡化的設定檔資料載入並擷取至Adobe [!DNL Campaign] sFTP。
1. 將協調流程和訊息個人化資料載入並擷取至Adobe [!DNL Campaign] sFTP。
1. 透過工作流程從 [!DNL Azure]blob 擷取 Experience Platform 區段。

#### 匯出工作流程

1. 每四小時透過工作流程將Adobe [!DNL Campaign]記錄檔傳送回Experience Platform （broadLog、trackingLog、無法傳遞的地址）。
1. 每隔四小時透過咨詢建置的工作流程，將個人資料偏好設定傳送回 Experience Platform (可選)。

### 行動推播設定

* 兩種支援的推播通知與行動裝置整合方法：
   * Experience Platform Mobile SDK
   * [!DNL Campaign]行動SDK
* Experience Platform Mobile SDK 路由：
   * 運用Adobe標籤和[!DNL Campaign Classic]擴充功能，設定您與Experience Platform Mobile SDK的整合
   * 需要 Adobe 標籤和資料收集的實用知識
   * 在 Android 和 iOS 中均需推播通知的行動開發體驗，才能部署 SDK、與 FCM (Android) 和 APNS (iOS) 整合以取得推播代號、設定應用程式以接收推播通知並處理推播互動
* [!DNL Campaign]行動SDK
   * 請參閱[Campaign Classic SDK檔案](https://developer.adobe.com/client-sdks/solution/adobe-campaign-classic/)

>[!IMPORTANT]
>
>如果您部署[!DNL Campaign] SDK並使用其他Experience Cloud應用程式，則須使用Experience Platform Mobile SDK進行資料收集。 這會在裝置上建立重複的用戶端呼叫。

## 相關文件

* [Adobe [!DNL Experience Platform] 檔案](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hant)
* [[!DNL Campaign Classic] 檔案](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=zh-Hant)
* [[!DNL Campaign Standard] 檔案](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=zh-Hant)
* [[!DNL Experience Platform] 啟動檔案](https://experienceleague.adobe.com/docs/launch.html?lang=zh-Hant)
* [[!DNL Experience Platform] 行動SDK檔案](https://experienceleague.adobe.com/docs/mobile.html?lang=zh-Hant)
