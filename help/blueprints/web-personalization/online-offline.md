---
title: 線上／離線網路個人化藍圖
description: 同步網路個人化與電子郵件及其他已知和匿名的通道個人化。
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7194thumb-web-personalization-scenario2.jpg
exl-id: 29667c0e-bb79-432e-af3a-45bd0b3b43bb
translation-type: tm+mt
source-git-commit: 61cb72965cd528cf264231058b1010829a87df9e
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 77%

---

# 線上／離線網路／行動個人化藍圖

同步網路個人化與電子郵件及其他已知和匿名的通道個人化。

## 使用案例

* 登陸頁面最佳化
* 行為與離線設定檔目標定位
* 除離線深入見解 (如異動、忠誠度與 CRM 資料及建模的深入見解) 外，基於之前產品/內容視圖、產品/內容相似性、環境屬性、協力廠商對象資料及人口統計資料的個人化

## 應用程式

* [!UICONTROL 即時客戶資料平台]
* Adobe Target
* Adobe Audience Manager (可選)：新增協力廠商對象資料、基於協作的裝置圖、在 Adobe Analytics 中顯示 Platform 區段的能力，以及在 Platform 中顯示 Adobe Analytics 區段的能力
* Adobe Analytics (可選)：新增基於歷史行為資料以及 Adobe Analytics 資料的細分建立區段的能力

## 架構

### 線上／離線個人化架構圖及即時客戶資料平台、目標和Audience Manager

<img src="assets/online_offline_personalization_with_apps.svg" alt="線上／離線網頁個人化藍圖的參考架構" style="border:1px solid #4a4a4a" />

## 護欄

請參閱「觀眾與描述檔啟動藍圖」區段- [LINK](../audience-activation/overview.md)下的護欄

### 線上／離線個人化護欄圖

<img src="assets/personalization_guardrails.svg" alt="線上／離線網頁個人化藍圖的護欄圖" style="border:1px solid #4a4a4a" />

## 實施模式

Web/Mobile個人化藍圖可透過下列方法實作，如下所述。

1. 使用[!UICONTROL 平台網頁SDK]或[!UICONTROL 平台行動SDK]和[!UICONTROL 邊緣網路]。
1. 使用傳統應用程式專用的SDK（例如AppMeasurement.js）

### 1.平台網頁／行動SDK與Edge方法

<img src="assets/web_sdk_flow.svg" alt="[!UICONTROL Platform Web SDK]或[!UICONTROL Platform Mobile SDK]和[!UICONTROL Edge Network]方法的參考體系結構" style="border:1px solid #4a4a4a" />

### 2.應用程式專用的SDK方法

<img src="assets/app_sdk_flow.png" alt="應用程式特定 SDK 方法的參考架構" style="border:1px solid #4a4a4a" />

## 實施先決條件

| 應用程式 / 服務 | 所需的資料庫 | 附註 |
|---|---|---|
| Adobe Target | [!UICONTROL 平台網頁SDK]*、at.js 0.9.1+或mbox.js 61+ | 首選 at.js，因為 mbox.js 不再進行開發。 |
| Adobe Audience Manager (可選) | [!UICONTROL Platform Web SDK]*或dil.js 5.0+ |  |
| Adobe Analytics (可選) | [!UICONTROL Platform Web SDK]*或AppMeasurement.js 1.6.4+ | Adobe Analytics 追蹤必須使用 Regional Data Collection (RDC)。 |
| Experience Cloud ID 服務 | [!UICONTROL 平台網頁SDK]*或VisitorAPI.js 2.0+ | (推薦) 使用 Experience Platform Launch 部署 ID 服務以確保在任何應用程式調用之前設定 ID |
| Experience Platform Mobile SDK (可選) | iOS 和 Android™ 的 4.11 或更高版本 |  |
| Experience Platform Web SDK | 1.0，目前的 Experience Platform SDK 版本具有[ Experience Cloud 應用程式尚不支援的各種使用案例](https://github.com/adobe/alloy/projects/5) |  |


## 實施步驟

1. 對您的網路或行動應用程式[實施 Adobe Target](https://experienceleague.adobe.com/docs/target/using/implement-target/implementing-target.html?lang=zh-Hant)
1. [實施 Adobe Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html?lang=zh-Hant) (可選)
1. [實施 Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/implementation/home.html?lang=zh-Hant) (可選)
1. [[!UICONTROL 實施 Experience Platform 與即時客戶設定檔]](https://experienceleague.adobe.com/docs/platform-learn/getting-started-for-data-architects-and-data-engineers/overview.html?lang=zh-Hant)
1. 實施 [Experience Cloud Identity 服務](https://experienceleague.adobe.com/docs/id-service/using/implementation/implementation-guides.html?lang=zh-Hant) 或 [Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html?lang=zh-Hant)
   >[!NOTE]
   >
   >每個應用程式必須使用 Experience Cloud ID 且屬於同一 Experience Cloud Org，才允許在應用程式之間進行對象分享。
1. [請求在 Experience Platform 與 Adobe Target 之間佈建對象分享 (已分享對象)](https://www.adobe.com/go/audiences)

## 相關文件

* [使用 Audience Manager 及其他 Experience Cloud 解決方案的 Experience Platform 區段分享](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html?lang=zh-Hant)
* [Experience Platform 細分概覽](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=zh-Hant)
* [串流細分](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=zh-Hant)
* [Experience Platform Segment Builder 概覽](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/overview.html?lang=zh-Hant)
* [Audience Manager 來源連接器](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/audience-manager.html?lang=zh-Hant)
* [Adobe Analytics透過Adobe Audience Manager分享區段](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=zh-Hant)
* [Experience Platform Web SDK 文件](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html)
* [Experience Cloud ID 服務文件](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=zh-Hant)
* [Experience Platform Launch 文件](https://experienceleague.adobe.com/docs/launch/using/home.html?lang=zh-Hant)

## 相關部落格貼文

* [[!DNL Blueprint for Web Personalization using Adobe Experience Platform Real-Time Customer Profile]](https://medium.com/adobetech/blueprint-for-web-personalization-using-adobe-experience-platform-real-time-customer-profile-fef2ce7a4b2f)
* [[!DNL Build an Optimal Online Experience: Enrich Unified Profile with Query Service]](https://medium.com/adobetech/build-an-optimal-online-experience-enrich-unified-profile-with-query-service-8027c196ab33)
* [[!DNL Integrating Adobe Experience Platform Decisioning Engine with AEM Websites]](https://jaeness.medium.com/integrating-adobe-experience-platform-decisioning-engine-with-aem-websites-9c222acd12e2)
* [[!DNL Adobe Experience Platform’s Identity Service — How to Solve the Customer Identity Conundrum]](https://medium.com/adobetech/adobe-experience-platforms-identity-service-how-to-solve-the-customer-identity-conundrum-f95e22d16ea9)
* [[!DNL How Adobe Experience Platform Predictive Audiences improves Personalized Experiences]](https://medium.com/adobetech/how-adobe-experience-platform-predictive-audiences-improves-personalized-experiences-1f75a60cb7a3)
* [[!DNL Adobe Experience Platform Web SDK for Audience Management]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
* [[!DNL Implementing Adobe Experience Platform Real-Time Customer Profile through our “Customer Zero” Program]](https://medium.com/adobetech/implementing-adobe-experience-platform-real-time-customer-profile-through-our-customer-zero-32e7cd952896)
* [[!DNL How Adobe Experience Platform Can Help Customers Personalize Their Mobile Messaging in Real-Time with Journey Orchestration Service and a Mobile Messaging Vendor]](https://medium.com/adobetech/how-adobe-experience-platform-helped-a-client-personalize-their-mobile-messaging-in-real-time-with-7d634aefa098)
* [[!DNL Segmentation in Seconds: How Adobe Experience Platform Made Real-time Customer Profiles a Reality]](https://medium.com/adobetech/segmentation-in-seconds-how-adobe-experience-platform-made-real-time-customer-profiles-a-reality-a7a8552b0847)
* [[!DNL Build an Optimal Online Experience: Enrich Unified Profile with Query Service]](https://medium.com/adobetech/build-an-optimal-online-experience-enrich-unified-profile-with-query-service-8027c196ab33)
