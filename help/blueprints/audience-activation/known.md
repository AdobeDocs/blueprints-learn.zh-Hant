---
title: 已知客戶啟用藍圖
description: 線上/離線對象啟用。
solution: Real-Time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7086
exl-id: 011f4909-b208-46db-ac1c-55b3671ee48c
source-git-commit: ae7347be5095ca4a7f99f9371dd94d87097112b0
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 100%

---

# 已知客戶啟用藍圖

使用離線屬性和事件，例如離線訂單、事務、CRM 或忠誠度資料，與線上行為一起進行線上目標定位和個人化。

具有內建治理控制的擴充識別碼可提供更多與已知客戶通訊的機會。啟用對象至基於已知個人資料的目標，例如電子郵件供應商、社交網路及廣告目標。

在針對 Experience Platform 與 Experience Cloud 應用程式之間整合的[ Experience Cloud 應用程式的對象與個人資料啟用藍圖](platform-and-applications.md)中提供其他詳細資料。

## 使用案例

* 對社交及廣告目標上已知對象的對象目標定位。
* 使用線上和離線屬性的線上個人化。
* 啟用對象至已知通道，例如電子郵件和簡訊。

## 應用程式

* [!UICONTROL Real-time Customer Data Platform]
* Audience Manager 以人物為基礎的目的地也可用於以人物為基礎的 Facebook、LinkedIn 和 Google 目標客戶比對的啟動。

## 架構

### 透過 Real-time Customer Data Platform 啟用已知客戶

<img src="assets/known_activation.svg" alt="已知客戶啟用藍圖的參考架構" style="width:90%; border:1px solid #4a4a4a"  class="modal-image" />
<br>

### 透過 Audience Manager 以人物為基礎的目標啟用已知客戶

<img src="assets/AAM_PBD.svg" alt="已知客戶啟用藍圖的參考架構" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />
<br>

## 護欄

[請參閱「對象與個人資料啟用概觀」頁面所述的護欄。](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/overview.html?lang=zh-Hant#guardrails-for-audience-and-profile-activation-blueprints)

## Real-time Customer Data Platform 的實作步驟

1. 為要擷取的資料[建立資料方案](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm&amp;lang=zh-Hant)。
1. 為要擷取的資料[建立資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=zh-Hant)。
1. [在方案上設定正確的身份和身份命名空間](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hant)，以確保擷取的資料可以嵌入統一的個人資料。
1. [為個人資料啟用方案和資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=zh-Hant)。
1. [擷取資料](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=zh-Hant)到 Experience Platform。
1. [在 Experience Platform 與 Audience Manager 之間為 Experience Platform 中定義要分享至 Audience Manager 的對象佈建[!UICONTROL Real-time Customer Data Platform]區段分享。](https://www.adobe.com/go/audiences)
1. 在 Experience Platform 中[建立區段](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=zh-Hant)。系統會自動確定區段是作為批次還是串流評估。
1. 將用於個人資料屬性和對象會籍分享的目標[設定為所需的目標。](https://experienceleague.adobe.com/docs/platform-learn/tutorials/destinations/create-destinations-and-activate-data.html?lang=zh-Hant)

## 實施考量

* 分享個人資料資料到目標需要您在目標負載中包含目標使用的特定身份值。對目標必要的任何身份必須擷取到 Platform，並且設定為[!UICONTROL 即時客戶個人資料]的身份。

* 有關將 Real-time Customer Data Platform 的對象共用給 Audience Manager、Analytics、Target、Campaign 以及 Journey Optimizer 的其他資訊，請參閱[透過 Experience Cloud 應用程式啟用受眾和個人資料藍圖](platform-and-applications.md)。

## Audience Manager 以人物為基礎的目標的實作步驟

* 如需實作 Audience Manager 的詳細資訊，請參閱下列[文件](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html?lang=zh-Hant)。

* 如需在 Audience Manager 中實作以人為基礎的目標的詳細資訊，請參閱下列[檔案](https://experienceleague.adobe.com/docs/audience-manager/user-guide/faqs/faq-people-based-destinations.html?lang=zh-Hant)。

## 相關文件

* [[!UICONTROL Real-time Customer Data Platform]產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/real-time-customer-data-platform.html)
* [個人資料與細分準則](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hant)
* [細分文件](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=zh-Hant)
* [目標文件](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=zh-Hant)

## 相關視訊與教學課程

* [[!UICONTROL Real-time Customer Data Platform]概覽](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=zh-Hant)
* [[!UICONTROL Real-time Customer Data Platform]示範](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=zh-Hant)
* [建立區段](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=zh-Hant)
