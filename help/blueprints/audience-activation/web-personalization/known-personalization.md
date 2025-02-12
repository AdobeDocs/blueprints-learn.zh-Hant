---
title: Web/Mobile 個人化概述 — Adobe Target 與 RTCDP
description: 同步網路個人化與電子郵件及其他已知和匿名的通道個人化。
landing-page-description: 同步網路個人化與電子郵件及其他已知和匿名的通道個人化。
short-description: 同步網路個人化與電子郵件及其他已知和匿名的通道個人化。
solution: Real-Time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection, Experience Platform
kt: 7194
thumbnail: thumb-web-personalization-scenario2.jpg
exl-id: 29667c0e-bb79-432e-af3a-45bd0b3b43bb
source-git-commit: 0d65ac8bcc8647683b6361a293d8c941869cd6b5
workflow-type: tm+mt
source-wordcount: '1130'
ht-degree: 30%

---


# 使用已知客戶資料的網頁/行動個人化藍圖

## 使用案例

* 使用已知客戶資料進行線上個人化
* 登陸頁面最佳化
* 除離線資料 (如異動、忠誠度與 CRM 資料及建模的見解) 外，基於之前產品/內容視圖、產品/內容相似性、環境屬性及人口統計資料的個人化
* 使用Adobe Target或Adobe Journey Optimizer Decisioning在網站和行動應用程式上分享及鎖定在Real-time Customer Data Platform中定義的對象。

## 應用程式

* [!UICONTROL Real-time Customer Data Platform]
* Adobe Target
* Adobe Journey Optimizer Decisioning
* Adobe Audience Manager（可選）:新增第三方對象資料
* Adobe Analytics 或 Customer Journey Analytics（可選）:新增根據歷史客戶和行為資料建立區段並執行微調細分的功能

### 參考文件

* [Adobe Target Connection for Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html)
* [Adobe Journey Optimizer Decisioning](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/gs-decision)
* [邊緣資料流配置](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=zh-Hant)
* [使用 Audience Manager 及其他 Experience Cloud 解決方案的 Experience Platform 區段分享](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html?lang=zh-Hant)

## 方法

在Web/行動裝置上進行已知客戶個人化的一個方法是將Real-time Customer Data Platform與Adobe Target整合。 以下指南會深入說明如何整合Real-time Customer Data Platform，以使用Adobe Target強化已知的客戶個人化。

已知的客戶網頁/行動個人化也可透過Adobe Journey Optimizer Decisioning實作，該功能可原生運用Experience Platform即時客戶個人檔案和區隔。 請參考[Adobe Journey Optimizer指南](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/ajo-home)，其中可以使用[程式碼型體驗](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based-experience/get-started-code-based)或[Web Channel體驗](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)。

架構藍圖也可在和[Journey Optimizer Blueprint](https://experienceleague.adobe.com/en/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/journey-optimizer)和[Journey Optimizer Decisioning Blueprint](https://experienceleague.adobe.com/en/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-overview)中使用。

## 整合模式

| 整合模式 | 功能 | 先決條件 |
|--------------------|------------|---------------|
| **從Real-time Customer Data Platform共用至Target的Edge即時區段評估** |  — 即時評估對象，以瞭解Edge上的相同或下一頁個人化。 <br> — 任何以串流或批次方式評估的區段也將投影到Edge Network，以包含在邊緣區段評估和個人化中。 |  — 必須實作Web/Mobile SDK或Edge Network伺服器API。 <br> — 必須在Experience Edge中設定資料串流，並啟用Target和Experience Platform擴充功能。 <br> — 目標目的地必須在Real-time Customer Data Platform目的地中設定。 <br> — 與Target整合需要與Experience Platform執行個體相同的IMS組織。 |
| **透過Edge方法從Real-time Customer Data Platform串流及批次對象共用至Target** |  — 透過Edge Network從Real-time Customer Data Platform分享串流和批次對象至Target。 <br> — 即時評估的對象需要Web SDK和Edge Network實作。 |  — 將串流和批次RTCDP對象共用至Target不需要Web/Mobile SDK或Edge API實作Target，但需要啟用即時邊緣區段評估。 <br> — 如果使用AT.js，則僅支援對ECID身分名稱空間進行設定檔整合。 <br> — 若要在Edge上進行自訂身分名稱空間查閱，需要Web SDK/Edge API部署，而且每個身分都必須在身分對應中設定為身分。 <br> — 目標目的地必須在Real-time Customer Data Platform目的地中設定，僅支援RTCDP中的預設生產沙箱。 <br> — 與Target整合需要與Experience Platform執行個體相同的IMS組織。 |
| **透過對象共用服務方法，從Real-time Customer Data Platform串流和批次對象共用至Target和Audience Manager** |  — 當需要從Audience Manager中的第三方資料和對象進行額外擴充時，可運用此整合模式。 |  — 將串流和批次對象共用至Target不需要Web/Mobile SDK，但需要啟用即時邊緣區段評估。 <br> — 如果使用AT.js，則僅支援對ECID身分名稱空間進行設定檔整合。 <br> — 若要在Edge上進行自訂身分名稱空間查閱，需要Web SDK/Edge API部署，而且每個身分都必須在身分對應中設定為身分。 <br> — 必須布建透過對象共用服務的對象投影。 <br> — 與Target整合需要與Experience Platform執行個體相同的IMS組織。 <br> — 只有來自預設生產沙箱的對象支援對象共用核心服務。 |

## 將即時、串流和批次對象分享至 Adobe Target

架構

<img src="assets/RTCDP+Target.svg" alt="線上/離線網路個人化 Blueprint 的參考架構" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

序列詳細資訊

<img src="assets/RTCDP+Target_flow.svg" alt="線上/離線網路個人化 Blueprint 的參考架構" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

概述架構

<img src="assets/personalization_with_apps.svg" alt="線上/離線網路個人化 Blueprint 的參考架構" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

## 實作模式

已知客戶個人化透過數種實作方法受支援。

### 實作模式1 - [!DNL Edge Network]搭配網頁/行動SDK或[!DNL Edge Network] API （建議做法）

* 搭配使用[!DNL Edge Network]與Web/行動SDK。 即時邊緣分段需要 Web/Mobile SDK 或 Edge API 實作方法。
* [請參閱 Experience Platform Web 與 Mobile SDK 藍圖](../../experience-platform/deployment/websdk.md)進行以 SDK 為基礎的實作。
* 若要在行動SDK中使用，必須安裝[Adobe Journey Optimizer - Decisioning擴充功能](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/)。
* [請參閱 [!DNL Edge Network] 伺服器API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=zh-Hant)，以取得具有Edge設定檔的Adobe Target之API實作。

### 實作模式 2 — 應用程式專用 SDK

使用傳統應用程式專用的 SDK（例如 At.js 和 AppMeasurement.js）。此實作方法不支援即時邊緣區段評估。不過，使用此實作方法，可支援從 Experience Platform 中心串流和批次共用對象。

[請參閱Adobe Target Connector檔案](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection)
[請參閱應用程式特定的SDK Blueprint](../../experience-platform/deployment/appsdk.md)

## 實施考量

* 透過[!DNL Edge Network]和網頁SDK使用上述實作模式1時，可以利用任何主要身分。
* 使用先前擷取到RTCDP中的已知客戶資料首次登入個人化時，個人化請求必須具備主要身分，且符合即時客戶資料平台中的已知客戶身分圖表。 如果主要ID設為ECID或尚未與已知客戶設定檔彙整的身分，則在Edge上實現身分彙整將需要幾分鐘的時間，以及Edge個人化需要幾分鐘的時間才能納入先前擷取的已知客戶資料。
* Edge設定檔目前有14天的TTL。 因此，如果使用者未登入或在邊緣上已活動14天，邊緣上的設定檔可能會過期，因此邊緣必須從中心擷取設定檔，才能使用歷史設定檔檢視來強化個人化，其中包含先前擷取的設定檔屬性和區段，如此一來，個人化便能以後續頁面檢視與首次登入時發生的設定檔歷史檢視來進行個人化。

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
