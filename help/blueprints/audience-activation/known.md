---
title: 已知客戶激活
description: 線上/離線對象啟用。
solution: Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7086
exl-id: 011f4909-b208-46db-ac1c-55b3671ee48c
source-git-commit: 4fef6460b305dc01671eeb9a90e58483f42d35e2
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 69%

---

# 已知客戶激活藍圖

使用離線屬性和事件，例如離線訂單、事務、CRM 或忠誠度資料，與線上行為一起進行線上目標定位和個人化。

擴展的具有內置治理控制的標識符提供了更多與已知客戶溝通的機會。 啟用對象至基於已知個人資料的目標，例如電子郵件供應商、社交網路及廣告目標。

其他詳細資料在[對象與個人資料啟用中提供，其中 Experience Cloud 應用程式 Blueprint](platform-and-applications.md) 特定於 Experience Platform 與 Experience Cloud 應用程式之間的互動。

## 使用案例

* 對社交及廣告目標上已知對象的對象目標定位。
* 使用線上和離線屬性的線上個人化。
* 啟用對象至已知通道，例如電子郵件和簡訊。

## 應用程式

* [!UICONTROL 即時客戶資料平台]
* 基於Audience Manager的目的地還可用於基於人員的Facebook、LinkedIn和Google客戶匹配活動。

## 架構

### 已知客戶激活(通過Real-time Customer Data Platform)

<img src="assets/known_activation.svg" alt="已知客戶激活藍圖的參考體系結構" style="width:80%; border:1px solid #4a4a4a" />
<br>

### 通過基於Audience Manager人的目的地激活已知客戶

<img src="assets/AAM_PBD.svg" alt="已知客戶激活藍圖的參考體系結構" style="width:80%; border:1px solid #4a4a4a" />
<br>

## 護欄

[請參閱「受眾和配置檔案激活概述」頁上概述的護欄](overview.md)。

## Real-time Customer Data Platform實施步驟

1. 為要擷取的資料[建立資料方案](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm)。
1. 為要擷取的資料[建立資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=zh-Hant)。
1. [在方案上設定正確的身份和身份命名空間](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hant)，以確保擷取的資料可以嵌入統一的個人資料。
1. [為個人資料啟用方案和資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=zh-Hant)。
1. [擷取資料](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=zh-Hant)到 Experience Platform。
1. [在 Experience Platform 與 Audience Manager 之間為 Experience Platform 中定義要分享至 Audience Manager 的對象佈建[!UICONTROL 即時客戶資料平台]區段分享。](https://www.adobe.com/go/audiences)
1. 在 Experience Platform 中[建立區段](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=zh-Hant)。系統會自動確定區段是作為批次還是串流評估。
1. 將用於個人資料屬性和對象會籍分享的目標[設定為所需的目標。](https://experienceleague.adobe.com/docs/platform-learn/tutorials/destinations/create-destinations-and-activate-data.html?lang=zh-Hant)

## 實施考量

* 分享個人資料資料到目標需要您在目標負載中包含目標使用的特定身份值。對目標必要的任何身份必須擷取到 Platform，並且設定為[!UICONTROL 即時客戶個人資料]的身份。

* 查看 [使用Experience Cloud應用程式藍圖激活受眾和配置檔案](platform-and-applications.md) 有關分享從Real-time Customer Data Platform到Audience Manager、分析、目標、活動和Journey Optimizer的受眾的更多詳細資訊。

## 基於人員的目標的Audience Manager實施步驟

* 有關實施Audience Manager的詳細資訊，請參閱以下 [文檔](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html?lang=zh-Hant)。

* 有關在Audience Manager中實施基於人員的目標的詳細資訊，請參閱以下 [文檔](https://experienceleague.adobe.com/docs/audience-manager/user-guide/faqs/faq-people-based-destinations.html)。

## 相關文件

* [[!UICONTROL 即時客戶資料平台]產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/real-time-customer-data-platform.html)
* [個人資料與細分準則](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hant)
* [細分文件](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=zh-Hant)
* [目標文件](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=zh-Hant)

## 相關視訊與教學課程

* [[!UICONTROL 即時客戶資料平台]概覽](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=zh-Hant)
* [[!UICONTROL 即時客戶資料平台]示範](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=zh-Hant)
* [建立區段](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html)
