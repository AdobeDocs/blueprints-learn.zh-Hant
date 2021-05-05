---
title: 線上／離線Audience Activation藍圖
description: 線上 / 離線 Audience Activation。
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7086
exl-id: 011f4909-b208-46db-ac1c-55b3671ee48c
translation-type: tm+mt
source-git-commit: 2fc1adc04a9ca2184c88970d5ba0785957327f68
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 63%

---

# 線上／離線Audience Activation藍圖

使用離線屬性和事件，例如離線訂單、事務、CRM 或忠誠度資料，與線上行為一起進行線上目標定位和個人化。

啟用對象至基於已知個人資料的目標，例如電子郵件供應商、社交網路及廣告目標。

線上／離線Audience Activation藍圖與[觀眾和描述檔啟動與Experience Cloud應用程式藍圖](platform-and-applications.md)緊密一致。 [「使用Experience Cloud應用程式啟動觀眾和設定檔」Blueprint](platform-and-applications.md)中提供了其他詳細資訊   特定於Experience Platform和Experience Cloud應用程式之間的整合。

## 使用案例

* 對社交及廣告目標上已知對象的對象目標定位。
* 使用線上和離線屬性的線上個人化。
* 啟用對象至已知通道，例如電子郵件和簡訊。

## 應用程式

* Adobe Experience Platform
* [!UICONTROL 即時客戶資料平台]

## 架構

### 線上／離線Audience Activation與目標

<img src="assets/online_offline_activation.svg" alt="線上／離線Audience Activation藍圖的參考架構" style="border:1px solid #4a4a4a" />
<br>

### 使用Experience Cloud應用程式進行線上／離線Audience Activation

<img src="assets/activation+apps.svg" alt="具有Experience Cloud應用程式的線上／離線Audience Activation藍圖參考架構" style="border:1px solid #4a4a4a" />

## 護欄

[請參閱「對象與描述檔啟動概述」頁面中概述的護欄。](overview.md)

## 實施步驟

1. [建立](https://experienceleague.adobe.com/docs/platform-learn/tutorials/schemas/create-a-schema.html) 要收錄的資料架構。
1. [建立](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html) 要收錄的資料資料集。
1. [在方案上設定正確的身份和身份命名空間，以確保擷取的資料可以嵌入統一的設定檔。](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html)
1. [為配置檔案啟用方案和資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html)。
1. [擷取資料到 Experience Platform。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion)
1. [在 Experience Platform 與 Audience Manager 之間為 Experience Platform 中定義要分享至 Audience Manager 的對象佈建即時客戶資料平台區段分享。](https://www.adobe.com/go/audiences)
1. [在Experience Platform](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=zh-Hant) 中建立區段。系統會自動確定區段是作為批次還是串流評估。
1. [將用於設定檔屬性和對象會籍分享的目標設定為所需的目標。](https://experienceleague.adobe.com/docs/platform-learn/tutorials/destinations/create-destinations-and-activate-data.html)

## 實施考量

* 分享設定檔資料到目標需要您在目標負載中包含目標使用的特定身份值。目標目標所需的任何身份都必須被收錄到平台中，並配置為[!UICONTROL 即時客戶概要檔案]的身份。

* 對於其中對象從 Experience Platform 分享至 Audience Manager 的啟用狀況，[!UICONTROL 即時客戶設定檔]中包含的所有身份將分享至 Audience Manager。當所需的目標身份包含在[!UICONTROL 即時客戶設定檔]中時，或者[!UICONTROL 即時客戶設定檔]中的身份可以關聯至 Audience Manager 中連結的所需目標身份時，Experience Platform 中的對象可透過 Audience Manager 目標分享。

## 相關文件

* [即時客戶資料平台產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/real-time-customer-data-platform.html)
* [描述檔與區段指南](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hant)
* [細分文件](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=zh-Hant)
* [目標文件](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=zh-Hant)

## 相關視訊與教學課程

* [即時客戶資料平台概覽](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=zh-Hant)
* [[!UICONTROL 即時客戶資料平台示範]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=zh-Hant)
* [建立區段](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html)
