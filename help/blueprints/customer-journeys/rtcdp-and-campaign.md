---
title: Real-Time CDP與Adobe Campaign整合模式
description: 展示 Adobe Experience Platform 及其即時客戶設定檔和集中式細分工具如何與 Adobe Campaign 一起使用，以提供個人化的對話體驗。
solution: Experience Platform, Campaign
exl-id: a15e8304-2763-42fc-9978-11f2482ea8b8
source-git-commit: 1d286f4dabe71f359c14a88c91f306ea443646a6
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Real-Time CDP與Adobe Campaign整合模式

展示 Adobe Experience Platform 及其即時客戶設定檔和集中式細分工具如何與 Adobe Campaign 一起使用，以提供個人化的對話體驗。

<br>

## 應用程式

* Adobe Experience PlatformReal-Time CDP
* Adobe Campaignv7或Campaign Standard

<br>

## 架構

<img src="assets/rtcdp-campaign-architecture.svg" alt="批量消息和Adobe Experience Platform整合模式的參考體系結構" style="width:100%; border:1px solid #4a4a4a" />

<br>

## 先決條件

* 建議在同一IMS組織中設定Experience Platform和活動，並利用Adobe Admin Console進行用戶訪問。 這還確保客戶可以從營銷UI中利用解決方案切換器

<br>

## 護欄

### Adobe Campaign

* 僅支援Adobe Campaign單個組織單位部署
* Adobe Campaign 是所有啟用的個人資料之真相來源，代表著個人資料必須存在於 Adobe Campaign 中，且不應基於 Experience Platform 區段建立新的個人資料。
* Campaign 匯出工作流程最多每隔 4 小時執行一次
* 用於Adobe CampaignbroadLog、trackingLogs和不可交付地址的XDM架構和資料集不是現成的，必須設計和構建

### Experience PlatformCDP段共用

* 建議20個段次限額
* 激活時間限制為每24小時
* 僅聯合架構屬性可用於激活（不支援陣列/映射/體驗事件）
* 關於每段不超過20個屬性的建議
* 所有「已實現」區段會籍的個人資料為每個區段一個檔案；或者擁有「已實現」和「已退出」個人資料的檔案，則將區段匯集新增為一個屬性
* 支援增量和完整段導出
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

#### 個人資料　/　身份

1. [建立任何客戶特定的命名空間。](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hant)
1. [新增身份至方案](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html)。
1. [為個人資料啟用方案和資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=zh-Hant)。
1. 為[!UICONTROL 即時客戶個人資料]的不同檢視[設定合併政策](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=zh-Hant) (可選)。
1. 建立 Adobe Campaign 使用的區段。

#### 來源/目標

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


### 移動推送配置

* 兩種支援的與移動設備整合推送通知的方法：
   * Experience Platform Mobile SDK
   * 活動移動SDK
* Experience PlatformMobileSDK路由：
   * 利用Adobe標籤和Campaign Classic擴展設定與Experience Platform移動SDK的整合
   * 需要有關Adobe標籤和資料收集的工作知識
   * 在Android和iOS都需要具有推送通知的移動開發經驗來部署SDK，與FCM(Android)和APNS(iOS)整合以獲得推送令牌，配置應用以接收推送通知和處理推送交互
* 活動移動SDK
   * 請關注 [市場活動SDK文檔](市場活動MobileSDK請遵循此處概述的部署文檔)

   >[!IMPORTANT]
   >如果您部署市場活動SDK並正在使用其他Experience Cloud應用程式，則需要使用Experience PlatformMobileSDK進行資料收集。 這將在設備上建立重複的客戶端調用。

## 相關文件

* [Adobe Experience Platform 文件](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hant)
* [Campaign Classic 文件](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=zh-Hant)
* [Campaign Standard 文件](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=zh-Hant)
* [Experience Platform Launch 文件](https://experienceleague.adobe.com/docs/launch.html?lang=zh-Hant)
* [Experience Platform Mobile SDK 文件](https://experienceleague.adobe.com/docs/mobile.html?lang=zh-Hant)
