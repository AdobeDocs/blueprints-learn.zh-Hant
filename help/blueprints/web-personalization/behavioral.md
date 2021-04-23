---
title: 行為網頁個人化藍圖
description: 基於線上行為及對象資料進行個人化。
solution: Experience Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7085thumb-web-personalization-scenario1.jpg
exl-id: b9882c2c-cb45-4efa-a85c-8fe48f641a12
translation-type: tm+mt
source-git-commit: 870541f548266ab82d74fec2e84b8cb6d5c952eb
workflow-type: tm+mt
source-wordcount: '532'
ht-degree: 78%

---

# 行為網頁／行動個人化藍圖

基於線上行為及對象資料進行個人化。

## 使用案例

* 登陸頁面最佳化
* 行為目標定位
* 基於先前產品 / 內容視圖、產品 / 內容相似性、環境屬性、協力廠商受眾資料及人口統計資料的個人化

## 應用程式

* Adobe Target
* Adobe Analytics (可選)
* Adobe Audience Manager (可選)

## 架構

<img src="assets/personalization.svg" alt="行為網站個人化藍圖的參考架構" style="border:1px solid #4a4a4a" />


## 護欄

依照預設，區段分享服務允許最多與 75 個對象分享每個 Adobe Analytics 報告套裝。如果使用 Audience Manager 和對象分享，可以分享的對象數量則沒有限制。 

## 實施模式

Web/Mobile個人化藍圖可透過下列方法實作，如下所述。

1. 使用[!UICONTROL 平台網頁SDK]或[!UICONTROL 平台行動SDK]和[!UICONTROL 邊緣網路]。
1. 使用傳統應用程式專用的SDK（例如AppMeasurement.js）

### 1.平台網頁／行動SDK與Edge方法

<img src="assets/websdkflow.svg" alt="[!UICONTROL Platform Web SDK]或[!UICONTROL Platform Mobile SDK]和[!UICONTROL Edge Network]方法的參考體系結構" style="border:1px solid #4a4a4a" />

### 2.應用程式專用的SDK方法

<img src="assets/appsdkflow.png" alt="應用程式特定 SDK 方法的參考架構" style="border:1px solid #4a4a4a" />




## 實施先決條件

| 應用程式 / 服務 | 所需的資料庫 | 附註 |
|---|---|---|
| Adobe Target | [!UICONTROL 平台網頁SDK]*、at.js 0.9.1+或mbox.js 61+ | 首選 at.js，因為 mbox.js 不再進行開發。 |
| Adobe Audience Manager (可選) | [!UICONTROL Platform Web SDK]*或dil.js 5.0+ |  |
| Adobe Analytics (可選) | [!UICONTROL Platform Web SDK]*或AppMeasurement.js 1.6.4+ |  |
| Experience Cloud Identity 服務 | [!UICONTROL 平台網頁SDK]*或VisitorAPI.js 2.0+ |  |
| Experience Platform Mobile SDK (可選) | iOS 和 Android™ 的 4.11 或更高版本 |  |
| Experience Platform Web SDK | 1.0，目前的 Experience Platform SDK 版本具有[ Experience Cloud 應用程式尚不支援的各種使用案例](https://github.com/adobe/alloy/projects/5) |  |

## 實施步驟

1. 對您的網路或行動應用程式[實施 Adobe Target](https://experienceleague.adobe.com/docs/target/using/implement-target/implementing-target.html?lang=zh-Hant)。

   如果使用Audience Manager或Adobe Analytics:

1. [實施 Adobe Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html?lang=zh-Hant)
1. [實施 Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/implementation/home.html?lang=zh-Hant)
1. [實施 Experience Cloud Identity 服務](https://experienceleague.adobe.com/docs/id-service/using/implementation/implementation-guides.html?lang=zh-Hant)

   >[!NOTE]
   >
   >每個應用程式必須使用 Experience Cloud ID 且屬於同一 Experience Cloud Org，才允許在應用程式之間進行對象分享。

1. [請求佈建人員與對象分享服務 (已分享對象)](https://www.adobe.com/go/audiences)
1. 在 [Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-build.html?lang=zh-Hant) 或 [Adobe Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/features/segments/segment-builder.html?lang=zh-Hant) 中建置區段，並[設定這些對象分享到 Experience Cloud](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=zh-Hant) (若使用 Audience Manager 或 Adobe Analytics)
1. 一旦可在 Adobe Target 中使用對象後，便可將之用於[使用 Adobe Target 的目標定位體驗](https://experienceleague.adobe.com/docs/target/using/audiences/target.html?lang=zh-Hant)

## 相關文件

* [Experience Cloud 受眾](https://experienceleague.adobe.com/docs/core-services/interface/audiences/audience-library.html?lang=zh-Hant)
* [整合 Audience Manager 與 Adobe Target](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-other-solutions/aam-target-integration.html?lang=zh-Hant)
* [Adobe Analytics透過Adobe Audience Manager分享區段](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html)


## 相關部落格貼文

* [[!DNL Blueprint for Web Personalization using Adobe Experience Platform Real-Time Customer Profile]](https://medium.com/adobetech/blueprint-for-web-personalization-using-adobe-experience-platform-real-time-customer-profile-fef2ce7a4b2f)
* [[!DNL Integrating Adobe Experience Platform Decisioning Engine with AEM Websites]](https://jaeness.medium.com/integrating-adobe-experience-platform-decisioning-engine-with-aem-websites-9c222acd12e2)
* [[!DNL How Adobe Experience Platform Predictive Audiences improves Personalized Experiences]](https://medium.com/adobetech/how-adobe-experience-platform-predictive-audiences-improves-personalized-experiences-1f75a60cb7a3)
* [[!DNL Adobe Experience Platform Web SDK for Audience Management]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
* [[!DNL Implementing Adobe Experience Platform Real-Time Customer Profile through our “Customer Zero” Program]](https://medium.com/adobetech/implementing-adobe-experience-platform-real-time-customer-profile-through-our-customer-zero-32e7cd952896)
* [[!DNL How Adobe Experience Platform Can Help Customers Personalize Their Mobile Messaging in Real-Time with Journey Orchestration Service and a Mobile Messaging Vendor]](https://medium.com/adobetech/how-adobe-experience-platform-helped-a-client-personalize-their-mobile-messaging-in-real-time-with-7d634aefa098)
* [[!DNL Segmentation in Seconds: How Adobe Experience Platform Made Real-time Customer Profiles a Reality]](https://medium.com/adobetech/segmentation-in-seconds-how-adobe-experience-platform-made-real-time-customer-profiles-a-reality-a7a8552b0847)
