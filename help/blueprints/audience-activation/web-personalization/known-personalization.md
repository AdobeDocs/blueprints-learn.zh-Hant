---
title: Web/Mobile 個人化概述 — Adobe Target 與 RTCDP
description: 同步網路個人化與電子郵件及其他已知和匿名的通道個人化。
landing-page-description: 同步網路個人化與電子郵件及其他已知和匿名的通道個人化。
short-description: 同步網路個人化與電子郵件及其他已知和匿名的通道個人化。
solution: Real-Time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection, Experience Platform
kt: 7194
thumbnail: thumb-web-personalization-scenario2.jpg
exl-id: 29667c0e-bb79-432e-af3a-45bd0b3b43bb
source-git-commit: 845655a275cdb6d4a9cd397ec7c3515cbf02d321
workflow-type: tm+mt
source-wordcount: '891'
ht-degree: 83%

---


# 使用已知客戶資料的網頁/行動個人化藍圖

## 使用案例

* 使用已知客戶資料進行線上個人化
* 登陸頁面最佳化
* 除離線資料 (如異動、忠誠度與 CRM 資料及建模的見解) 外，基於之前產品/內容視圖、產品/內容相似性、環境屬性及人口統計資料的個人化
* 在使用 Adobe Target 的網站和行動應用程式上共用和鎖定 Real-time Customer Data Platform 中定義的對象。

## 應用程式

* [!UICONTROL Real-time Customer Data Platform]
* Adobe Target
* Adobe Audience Manager（可選）:新增第三方對象資料
* Adobe Analytics 或 Customer Journey Analytics（可選）:新增根據歷史客戶和行為資料建立區段並執行微調細分的功能

### 參考文件

* [Adobe Target Connection for Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html)
* [邊緣資料流配置](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=zh-Hant)
* [使用 Audience Manager 及其他 Experience Cloud 解決方案的 Experience Platform 區段分享](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html?lang=zh-Hant)


## 整合模式

| 整合模式 | 功能 | 先決條件 |
|---|---|---|
| 對從 Real-time Customer Data Platform 共用至 Target 的 Edge 進行即時區段評估 | <ul><li>在 Edge 上即時評估同一或下一頁面的個人化的對象。</li><li>此外，任何以串流或批次方式評估的區段也會投影至 [!DNL Edge Network] 將包含在邊緣區段評估與個人化中。</li></ul> | <ul><li>Web/Mobile SDK必須實作或 [!DNL Edge Network] 伺服器API</li><li>必須在 Experience Edge 中設定資料流，並啟用 Target 和 Experience Platform 擴充功能</li><li>Target 目標必須在 Real-time Customer Data Platform 目標中設定。</li><li>與 Target 整合需要與 Experience Platform 實例相同的 IMS 組織。</li></ul> |
| 透過 Edge 方法將受眾從 Real-time Customer Data Platform 串流和批次共用至 Target | <ul><li>透過將串流和批次對象從Real-time Customer Data Platform分享到Target [!DNL Edge Network]. 即時評估的對象需要Web SDK和 [!DNL Edge Network] 實作。</li></ul> | <ul><li>將串流和批次 RTCDP 對象共用至 Target 時，不需要 Target 的 Web/Mobile SDK 或 Edge API 實作，不過需要進行上述的即時邊緣區段評估。</li><li>如果使用 At.js，則僅支援針對 ECID 身分命名空間的個人資料整合。</li><li>在 Edge 上進行自訂身分命名空間查閱時，需要部署 Web SDK/Edge API，且每個身分都必須在身分對應中設定為身分。</li><li>Target 目標必須在 Real-time Customer Data Platform 目標中設定，僅支援 RTCDP 中的預設生產沙箱。</li><li>與 Target 整合需要與 Experience Platform 實例相同的 IMS 組織。</li></ul> |
| 透過對象共用服務方法，從 Real-time Customer Data Platform 串流和批次共用受眾至 Target 和 Audience Manager | <ul><li>當需要從第三方資料和 Audience Manager 中的對象進行額外擴充時，可運用此整合模式。</li></ul> | <ul><li>將串流和批次對象共用至 Target 並不需要 Web/Mobile SDK，不過需要 Web/Mobile SDK 才能進行即時邊緣區段評估。</li><li>如果使用 At.js，則僅支援針對 ECID 身分命名空間的個人資料整合。</li><li>在 Edge 上進行自訂身分命名空間查閱時，需要部署 Web SDK/Edge API，且每個身分都必須在身分對應中設定為身分。</li><li>必須透過對象共用服務布建對象投影。</li><li>與 Target 整合需要與 Experience Platform 實例相同的 IMS 組織。</li><li>只有來自預設生產沙箱的對象才支援對象共用核心服務。</li></ul> |

## 將即時、串流和批次對象分享至 Adobe Target

架構

<img src="assets/RTCDP+Target.svg" alt="線上/離線網路個人化 Blueprint 的參考架構" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

序列詳細資訊

<img src="assets/RTCDP+Target_flow.svg" alt="線上/離線網路個人化 Blueprint 的參考架構" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

概述架構

<img src="assets/personalization_with_apps.svg" alt="線上/離線網路個人化 Blueprint 的參考架構" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

## 實作模式

已知客戶個人化透過數種實作方法受支援。

### 實作模式1 - [!DNL Edge Network] 使用Web/Mobile SDK或 [!DNL Edge Network] API （建議方法）

* 使用 [!DNL Edge Network] 與Web/Mobile SDK搭配使用。 即時邊緣分段需要 Web/Mobile SDK 或 Edge API 實作方法。
* [請參閱 Experience Platform Web 與 Mobile SDK 藍圖](../../experience-platform/deployment/websdk.md)進行以 SDK 為基礎的實作。
* 若要用於 Mobile SDK，[Adobe Journey Optimizer — 決策擴充功能](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-journey-optimizer-decisioning)必須安裝在 Mobile SDK 中。
* [請參閱 [!DNL Edge Network] 伺服器API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=zh-Hant) 適用於使用Edge Profile的Adobe Target的API型實作。

### 實作模式 2 — 應用程式專用 SDK

使用傳統應用程式專用的 SDK（例如 At.js 和 AppMeasurement.js）。此實作方法不支援即時邊緣區段評估。不過，使用此實作方法，可支援從 Experience Platform 中心串流和批次共用對象。

[請參閱Adobe Target聯結器檔案](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection)
[請參閱應用程式特定的SDK藍圖](../../experience-platform/deployment/appsdk.md)

## 實施考量

身分先決條件

* 使用上述實施模式1時，可利用任何主要身分，搭配 [!DNL Edge Network] 和Web SDK。 首次登入個人化需要個人化請求設定與Real-time Customer Data Platform中設定檔的主要身分相符的主要身分。

## 相關文件

### SDK 檔案

* [Experience Platform Web SDK 文件](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html?lang=zh-Hant)
* [Experience Platform Tags 文件](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=zh-Hant)
* [Experience Cloud ID Service 文件](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=zh-Hant)

### 細分文件

* [Experience Platform 細分概覽](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=zh-Hant)
* [即時細分](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/edge-segmentation.html?lang=zh-Hant)
* [串流細分](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=zh-Hant)
* [透過 Adobe Audience Manager 分享 Adobe Analytics 區段](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=zh-Hant)
* [合併原則設定](https://experienceleague.adobe.com/docs/experience-platform/profile/merge-policies/ui-guide.html?lang=zh-Hant#create-a-merge-policy)

### 教學課程

* [使用 Real-Time CDP 和 Adobe Target 進行下次點擊個人化](https://experienceleague.adobe.com/docs/platform-learn/tutorials/experience-cloud/next-hit-personalization.html?lang=zh-Hant)

### 相關部落格貼文

* [Adobe 宣佈使用 Adobe Target 和 Real-time Customer Data Platform 實現相同頁面增強個人化](https://blog.adobe.com/en/publish/2021/10/05/adobe-announces-same-page-enhanced-personalization-with-adobe-target-real-time-customer-data-platform)
* [[!DNL Blueprint for Web Personalization using Adobe Experience Platform Real-Time Customer Profile]](https://medium.com/adobetech/blueprint-for-web-personalization-using-adobe-experience-platform-real-time-customer-profile-fef2ce7a4b2f)
* [[!DNL Adobe Experience Platform's Identity Service — How to Solve the Customer Identity Conundrum]](https://medium.com/adobetech/adobe-experience-platforms-identity-service-how-to-solve-the-customer-identity-conundrum-f95e22d16ea9)
* [[!DNL Adobe Experience Platform Web SDK for Audience Management]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
* [[!DNL Implementing Adobe Experience Platform Real-Time Customer Profile through our "Customer Zero" Program]](https://medium.com/adobetech/implementing-adobe-experience-platform-real-time-customer-profile-through-our-customer-zero-32e7cd952896)
* [[!DNL Segmentation in Seconds: How Adobe Experience Platform Made Real-time Customer Profiles a Reality]](https://medium.com/adobetech/segmentation-in-seconds-how-adobe-experience-platform-made-real-time-customer-profiles-a-reality-a7a8552b0847)
