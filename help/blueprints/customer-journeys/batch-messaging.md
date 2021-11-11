---
title: 批次訊息傳送與 Adobe Experience Platform Blueprint
description: 使用 Adobe Experience Platform 作為客戶個人資料與細分的中樞，以執行排程的批次訊息傳送行銷活動。
solution: Experience Platform, Campaign
kt: 7196
exl-id: 4e55218c-c158-4f78-9f0b-c03528d992fa
source-git-commit: 55584ea85570bbcd4c959b0bd94b9e0bdc2e962f
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 99%

---

# 批次訊息傳送與 Adobe Experience Platform Blueprint

使用 Adobe Experience Platform 作為客戶個人資料與細分的中樞，以執行排程的批次訊息傳送行銷活動。

## 使用案例

* 排程的電子郵件行銷活動
* 引導與再行銷活動

## 應用程式

* Adobe Experience Platform
* Adobe Campaign Classic 或 Standard

## 整合模式

* Adobe Experience Platform → Adobe Campaign Classic
* Adobe Experience Platform → Adobe Campaign Standard

## 架構

<img src="assets/aepbatch.svg" alt="批次訊息傳送與 Adobe Experience Platform Blueprint 之參考架構" style="width:80%; border:1px solid #4a4a4a" />

## 護欄

* 僅支援 Adobe Campaign 單一組織單位部署
* Adobe Campaign 是所有啟用的個人資料之真相來源，代表著個人資料必須存在於 Adobe Campaign 中，且不應基於 Experience Platform 區段建立新的個人資料。
* Experience Platform 中的區段會籍實現對於批次 (每天 1 次) 和串流 (約 5 分鐘) 是潛在的

**[!UICONTROL 即時客戶資料平台]區段分享至 Adobe Campaign：**

* 建議限制為 20 個區段
* 啟用限制於每隔 24 小時
* 僅聯合方案屬性可啟用 (不支援陣列/地圖/體驗事件)。
* 建議每個區段不超過 20 項屬性
* 所有「已實現」區段會籍的個人資料為每個區段一個檔案；或者擁有「已實現」和「已退出」個人資料的檔案，則將區段匯集新增為一個屬性
* 支援漸進式或完整區段匯出
* 不支援檔案加密
* Adobe Campaign 匯出工作流程最多每隔 4 小時執行一次
* 請參閱 [Experience Platform 的個人資料和資料擷取護欄](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hant)

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

#### 行動應用程式部署

1. 對 Adobe Campaign Classic 實施 Adobe Campaign SDK，或對 Adobe Campaign Standard 實施 Experience Platform SDK。如果 Experience Platform Launch 存在，建議 Adobe Campaign Classic 或 Adobe Campaign Standard 延伸與 Experience Platform SDK 一起使用。

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


## 相關文件

* [Adobe Experience Platform 文件](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hant)
* [Campaign Classic 文件](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=zh-Hant)
* [Campaign Standard 文件](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=zh-Hant)
* [Experience Platform Launch 文件](https://experienceleague.adobe.com/docs/launch.html?lang=zh-Hant)
* [Experience Platform Mobile SDK 文件](https://experienceleague.adobe.com/docs/mobile.html?lang=zh-Hant)
