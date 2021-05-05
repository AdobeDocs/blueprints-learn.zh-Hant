---
title: 批次訊息與Adobe Experience Platform藍圖
description: 使用 Adobe Experience Platform 作為客戶設定檔與細分的中樞，以執行排程的批次訊息傳送行銷活動。
solution: Experience Platform, Campaign
kt: 7196
exl-id: 4e55218c-c158-4f78-9f0b-c03528d992fa
translation-type: tm+mt
source-git-commit: 81df87f850b7ac4be9dce7a3b96d39a3a47685c5
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 48%

---

# 批次訊息與Adobe Experience Platform藍圖

使用 Adobe Experience Platform 作為客戶設定檔與細分的中樞，以執行排程的批次訊息傳送行銷活動。

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

<img src="assets/aepbatch.svg" alt="批傳訊與Adobe Experience Platform藍圖的參考架構" style="border:1px solid #4a4a4a" />

## 護欄

* 僅支援Adobe Campaign單個組織單位部署
* Adobe Campaign是所有活動配置檔案的真實來源，這意味著配置檔案必須存在於Adobe Campaign，而且不應基於Experience Platform段建立新配置檔案。
* Experience Platform 中的區段會籍實現對於批次 (每天 1 次) 和串流 (約 5 分鐘) 是潛在的

**[!UICONTROL 即時客戶資料平] 台區段共用給Adobe Campaign:**

* 建議限制為 20 個區段
* 啟用限制於每隔 24 小時
* 僅聯合方案屬性可啟用 (不支援陣列/地圖/體驗事件)。
* 建議每個區段不超過 20 項屬性
* 所有「已實現」區段會籍的設定檔為每個區段一個檔案；或者擁有「已實現」和「已退出」設定檔的檔案，則將區段匯集新增為一個屬性
* 支援漸進式或完整區段匯出
* 不支援檔案加密
* Adobe Campaign出口工作流程最多每4小時執行一次
* 請參閱 [Experience Platform 的設定檔和資料擷取護欄](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hant)

## 實施步驟

### Adobe Experience Platform

#### 方案/資料集

1. [在 Experience Platform 中基於客戶提供的資料設定個別設定檔、體驗事件及多實體方案。](https://experienceleague.adobe.com/docs/platform-learn/tutorials/schemas/create-a-schema.html)
1. 為broadLog、trackingLog、非交付項位址和描述檔偏好設定建立Adobe Campaign結構（選用）。
1. [建立](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html) 要收錄資料的資料Experience Platform。
1. [將資料使用](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html) Experience Platform新增至資料集以利管理。
1. [建立政策以在目標上執行治理。](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html)

#### 設定檔　/　身份

1. [建立任何客戶專屬的命名空間](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html)。
1. [將身分新增至結構](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html)。
1. [為配置檔案啟用模式和資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html)。
1. [為「即時客](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html) 戶個人資料」的 [!UICONTROL 不同檢視設定合併政策] （可選）。
1. 建立區段以利Adobe Campaign使用。

#### 來源 / 目標

1. [使用串流 API 和來源連接器將資料擷取到 Experience Platform。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion)
1. 配置[!DNL Azure]blob儲存目標以用於Adobe Campaign。

#### 行動應用程式部署

1. 實作Adobe Campaign Classic的Adobe CampaignSDK或Adobe Campaign Standard的Experience PlatformSDK。 如果有Experience Platform Launch，建議將Adobe Campaign Classic或Adobe Campaign Standard擴充功能與Experience PlatformSDK搭配使用。

#### Adobe Campaign

1. 為設定檔、查詢資料及相關的傳送個人化資料設定方案。

>[!IMPORTANT]
>
>目前，您必須瞭解描述檔和事件資料的Experience Platform資料模型，以便瞭解Adobe Campaign需要哪些資料。

#### 匯入工作流程

1. 將簡化的描述檔資料載入並收錄至Adobe Campaign的sFTP。
1. 將協調及傳訊個人化資料載入Adobe Campaign的sFTP並收錄。
1. 透過工作流程從 [!DNL Azure] blob 擷取 Experience Platform 區段。

#### 匯出工作流程

1. 每四小時透過工作流程將Adobe Campaign記錄檔傳回Experience Platform（broadLog、trackingLog、無法傳送的位址）。
1. 每隔四小時透過咨詢建置的工作流程，將設定檔偏好設定傳送回 Experience Platform (可選)。


## 相關文件

* [Adobe Experience Platform 文件](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hant)
* [Campaign Classic 文件](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=zh-Hant)
* [Campaign Standard 文件](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=zh-Hant)
* [Experience Platform Launch 文件](https://experienceleague.adobe.com/docs/launch.html?lang=zh-Hant)
* [Experience Platform Mobile SDK 文件](https://experienceleague.adobe.com/docs/mobile.html?lang=zh-Hant)
