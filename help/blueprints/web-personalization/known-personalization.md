---
title: Web/Mobile 個人化概述 — Adobe Target 與 RTCDP
description: 同步網路個人化與電子郵件及其他已知和匿名的通道個人化。
landing-page-description: 同步網路個人化與電子郵件及其他已知和匿名的通道個人化。
short-description: 同步網路個人化與電子郵件及其他已知和匿名的通道個人化。
solution: Real-Time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection, Experience Platform
kt: 7194
thumbnail: thumb-web-personalization-scenario2.jpg
exl-id: 29667c0e-bb79-432e-af3a-45bd0b3b43bb
source-git-commit: ae7347be5095ca4a7f99f9371dd94d87097112b0
workflow-type: tm+mt
source-wordcount: '1642'
ht-degree: 100%

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

## 整合模式

| 整合模式 | 功能 | 先決條件 |
|---|---|---|
| 對從 Real-time Customer Data Platform 共用至 Target 的 Edge 進行即時區段評估 | <ul><li>在 Edge 上即時評估同一或下一頁面的個人化的對象。</li><li>此外，以串流或批次方式評估的任何區段也會投影至邊緣網路，以納入邊緣區段評估和個人化中。</li></ul> | <ul><li>必須實作 Web/Mobile SDK，或使用 Edge Network Server API</li><li>必須在 Experience Edge 中設定資料流，並啟用 Target 和 Experience Platform 擴充功能</li><li>Target 目標必須在 Real-time Customer Data Platform 目標中設定。</li><li>與 Target 整合需要與 Experience Platform 實例相同的 IMS 組織。</li></ul> |
| 透過 Edge 方法將受眾從 Real-time Customer Data Platform 串流和批次共用至 Target | <ul><li>透過 Edge Network 將串流和批次對象從 Real-time Customer Data Platform 共用至 Target。即時評估的對象需要 Web SDK 和 Edge Network 實作。</li></ul> | <ul><li>將串流和批次 RTCDP 對象共用至 Target 時，不需要 Target 的 Web/Mobile SDK 或 Edge API 實作，不過需要進行上述的即時邊緣區段評估。</li><li>如果使用 At.js，則僅支援針對 ECID 身分命名空間的個人資料整合。</li><li>在 Edge 上進行自訂身分命名空間查閱時，需要部署 Web SDK/Edge API，且每個身分都必須在身分對應中設定為身分。</li><li>Target 目標必須在 Real-time Customer Data Platform 目標中設定，僅支援 RTCDP 中的預設生產沙箱。</li><li>與 Target 整合需要與 Experience Platform 實例相同的 IMS 組織。</li></ul> |
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

### 實作模式 1 — 使用 Web/Mobile SDK 或 Edge Network API 的邊緣網路（建議方法）

* 搭配 Web/Mobile SDK 使用邊緣網路。即時邊緣分段需要 Web/Mobile SDK 或 Edge API 實作方法。
* [請參閱 Experience Platform Web 與 Mobile SDK 藍圖](../experience-platform/deployment/websdk.md)進行以 SDK 為基礎的實作。
* 若要用於 Mobile SDK，[Adobe Journey Optimizer — 決策擴充功能](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-journey-optimizer-decisioning)必須安裝在 Mobile SDK 中。
* [請參閱 Edge Network Server API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=zh-Hant) 藉助 Edge 個人資料進行 Adobe Target 的 API 型實作。

### 實作模式 2 — 應用程式專用 SDK

使用傳統應用程式專用的 SDK（例如 At.js 和 AppMeasurement.js）。此實作方法不支援即時邊緣區段評估。不過，使用此實作方法，可支援從 Experience Platform 中心串流和批次共用對象。

[請參閱應用程式專屬的 SDK 藍圖](../experience-platform/deployment/appsdk.md)

### 實施步驟

1. 對您的網路或行動應用程式[實施 Adobe Target](https://experienceleague.adobe.com/docs/target/using/implement-target/implementing-target.html?lang=zh-Hant)
1. [實作 Experience Platform 和 [!UICONTROL Real-time Customer Profil]](https://experienceleague.adobe.com/docs/platform-learn/getting-started-for-data-architects-and-data-engineers/overview.html?lang=zh-Hant)，透過將[合併原則](https://experienceleague.adobe.com/docs/experience-platform/profile/merge-policies/ui-guide.html?lang=zh-Hant#create-a-merge-policy)設定為邊緣上的活動狀態，確保建立的對象啟用邊緣。
1. 實作 [Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html?lang=zh-Hant) 或 [Experience Platform Mobile SDK](https://aep-sdks.gitbook.io/docs/) 並安裝正確的擴充功能（Target 或 Adobe Journey Optimizer - Decisioning）。Experience Platform Web/Mobile SDK 或 EDGE API 是即時 Edge 細分的必要項目，但從 Real-time Customer Data Platform 到 Target 共用串流和批次對象時並非必要項目。
1. [使用邊緣資料流配置邊緣網路](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=zh-Hant)
1. [啟用 Adobe Target 作為 Real-time Customer Data Platform 的目標](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=zh-Hant)
1. （可選）[實作 Adobe Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html?lang=zh-Hant)。
1. （可選） [請求布建以在 Experience Platform 和 Adobe Target 之間共用對象](https://www.adobe.com/go/audiences) 以從 Experience Platform 共用對象至 Target。

## 護欄

[請參閱「網路與行動個人化 Blueprints」概觀頁面所述的護欄。](overview.md)

* 邊緣個人資料僅會在使用者於邊緣處於作用中狀態時建立，亦即其設定檔會透過 Web/Mobile SDK 或 Edge Server API 將串流事件提交至邊緣。這通常對應於在網站或行動應用程式上處於作用中狀態的使用者。
* 邊緣個人資料的預設存留時間為 14 天。如果使用者尚未收集作用中的邊緣事件，則個人資料閒置 14 天後會在邊緣過期。個人資料在中心將保持有效，並且當使用者再次在邊緣上變為作用中狀態時，會與邊緣同步。
* 在邊緣上建立新的個人資料時，會非同步呼叫中心，以擷取已透過目標為邊緣投影設定的任何對象和屬性。由於這是非同步流程，中心配置檔案可能需要 1 秒到數分鐘的時間才能同步到邊緣。因此，無法保證新個人資料具有來自第一頁體驗中心的個人資料情境。這同樣適用於中心新收集的資料。此資料會以非同步方式投影至邊緣，因此資料到達適當邊緣的時間會與邊緣活動分開。只有邊緣上作用中的個人資料才會保留從中心投影的屬性和對象。

## 實施考量

身分先決條件

* 透過邊緣網路和 Web SDK 使用上述實作模式 1 時，可運用任何主要身分。首次登入個人化需要個人化請求設定的主要身分，與 Real-time Customer Data Platform 中個人資料的主要身分相符。匿名裝置與已知客戶之間的身分識別拼接會在中心進行處理，然後投影至邊緣。
* 請注意，消費者造訪或登入網站之前上傳至中心的資料，將無法立即供個人化使用。作用中的邊緣個人資料必須先存在，中心資料才能同步。建立後，邊緣個人資料會以非同步方式與中心個人資料同步，進而產生下一頁個人化。
* 從 Adobe Experience Platform 共用受眾至 Adobe Target 時，若要使用上述整合模式 2 和 3 所述的受眾共用服務，必須以 ECID 作為身分。
* 替代身分也可用來透過 Audience Manager 與 Adobe Target 共用 Experience Platform 對象。Experience Platform 會透過下列支援的命名空間啟用對象至 Audience Manager：IDFA、GAID、AdCloud、Google、ECID、EMAIL_LC_SHA256。請注意，Audience Manager 和 Target 會透過 ECID 身分識別解析受眾成員資格，因此消費者在身分圖中仍需要有 ECID，才能最終分享至 Adobe Target。

## 相關文件

### SDK 檔案

* [Experience Platform Web SDK 文件](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html?lang=zh-Hant)
* [Experience Platform Tags 文件](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=zh-Hant)
* [Experience Cloud ID Service 文件](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=zh-Hant)

### 連線檔案

* [Adobe Target Connection for Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=zh-Hant)
* [邊緣資料流配置](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=zh-Hant)
* [使用 Audience Manager 及其他 Experience Cloud 解決方案的 Experience Platform 區段分享](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html?lang=zh-Hant)

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
