---
title: 透過Experience Cloud應用程式啟動受眾和設定檔藍圖
description: 在 Experience Platform 中管理個人資料和對象，以及與 Experience Cloud 應用程式分享它們。
solution: Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services
kt: 7722
exl-id: f36014e8-170d-47e1-b4ec-10c0ea70612d
source-git-commit: 5110ee2a7a079945475055cbcfdabf7cdcaa0ab5
workflow-type: tm+mt
source-wordcount: '896'
ht-degree: 31%

---

# 透過Experience Cloud應用程式啟動受眾和設定檔藍圖

在 Experience Platform 中管理個人資料和對象，以及與 Experience Cloud 應用程式分享它們。在 Experience Platform 中建立並分享豐富的客戶區段和客戶分析，並且在 Experience Cloud 應用程式中分享它們。

通過Experience Cloud應用程式激活與 [已知客戶啟用Blueprint](known.md).

## 使用案例

* Experience Cloud 支援的各客戶互動頻道中的個人化和目標。
* 在 Experience Platform 與 Experience Cloud 應用程式之間分享對象和個人資料。
* 從多管道資料（包括線上行為資料和資料科學模型）建立豐富的深入分析，以豐富Experience Platform中的即時客戶個人檔案，然後可與Experience Cloud應用程式共用。

## 應用程式

* Adobe Experience Platform
* [!UICONTROL Real-time Customer Data Platform]
* Experience Platform 啟用
* Experience Cloud 應用程式
   * Adobe Audience Manager
   * Adobe Target
   * Adobe Campaign
   * Journey Optimizer
   * Marketo Engage
   * Adobe Commerce
   * Customer Journey Analytics

## 架構

請參閱 [Experience Platform和應用程式體系結構部分](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/platform-applications.html?lang=zh-Hant) 以取得與Experience Platform與Experience Cloud應用程式整合相關的其他架構圖表。

### 透過Experience Cloud應用程式啟動受眾和設定檔

<img src="../experience-platform/assets/aep+apps_horizontal.svg" alt="透過Experience Cloud應用程式啟動受眾和設定檔的參考架構" style="width:90%; border:1px solid #4a4a4a"  class="modal-image" />
<br>

## 護欄

請參閱[「對象與個人資料啟用」概觀頁面所述的護欄](overview.md) 和 [部署護欄](../experience-platform/deployment/guardrails.md) 頁面。

## 實作考量事項

* 分享個人資料資料到目標需要您在目標負載中包含目標使用的特定身份值。對目標必要的任何身份必須擷取到 Platform，並且設定為[!UICONTROL 即時客戶個人資料]的身份。

### 受眾從Real-time Customer Data Platform分享至Audience Manager

* 如需詳細資訊，請參閱下列檔案。 [使用 Audience Manager 及其他 Experience Cloud 解決方案的 Experience Platform 區段分享](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html?lang=zh-Hant).

* 當區段評估完成並寫入即時Audience Manager設定檔（不論是批次或串流）,RT-CDP的受眾成員資格會立即以串流方式共用給客戶。
* 如果符合資格的設定檔包含相關設定檔裝置的地區路由資訊，則來自RTCDP的對象成員資格會在相關Audience ManagerEdge上以串流方式符合資格。 如果將地區路由資訊套用至過去14天具有時間戳記的設定檔，則會在串流的Audience Manager邊緣進行評估。 如果RTCDP的配置檔案中不包含區域路由資訊，或區域路由資訊大於14天，則RTCDP對象成員會發送到Audience Manager中心位置，以便進行基於批次的評估和激活。
* 有了地區路由資訊，這些設定檔即有資格啟用Edge，並將在RTCDP區段資格認證後幾分鐘內啟動，不符合Edge啟動資格的設定檔將在Audience Manager中心取得資格，且可能有12至24小時的處理時間。
* 您可以收集Audience Manager設定檔所儲存的地區路由資訊，以從Audience Manager、訪客ID服務、Analytics、Launch，或直接從Web SDKExperience Platform為個別的設定檔記錄類別資料集，使用「資料擷取地區資訊」XDM欄位群組。 如需詳細資訊，請參閱取得地區資訊檔案 [連結](https://experienceleague.adobe.com/docs/id-service/using/reference/regions.html?lang=en).
* 在啟用案例中，會從Experience Platform共用閱聽眾，以Audience Manager下列身分自動共用：ECID、IDFA、GAID、雜湊電子郵件地址(EMAIL_LC_SHA256)、AdCloud ID。 目前不共用自訂命名空間。
* 當所需的目標身份包含在[!UICONTROL 即時客戶個人資料]中時，或者[!UICONTROL 即時客戶個人資料]中的身份可以關聯至 Audience Manager 中連結的所需目標身份時，Experience Platform 中的對象可透過 Audience Manager 目標分享。

### 從Real-time Customer Data Platform到Target的受眾共用

* 請參閱 [已知客戶個人化 — Target和RTCDP Blueprint](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/web-personalization/known-personalization.html) 如需從Real-time Customer Data Platform共用設定檔和對象的其他詳細資訊，請參閱Target。

### 從Real-time Customer Data Platform到Campaign和Journey Optimizer的受眾共用

* 請參閱 [客戶歷程藍圖](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/b2b-activation/b2bactivation.html?lang=en) 如需共用設定檔和對象的詳細資訊，請參閱Real-time Customer Data Platform、Campaign和Journey Optimizer。

### 受眾從Real-time Customer Data Platform分享至Marketo Engage

* 請參閱 [B2B激活藍圖](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/b2b-activation/b2bactivation.html?lang=en) 如需從Real-time Customer Data Platform共用設定檔和對象到Marketo Engage的其他詳細資訊。

### 受眾從Real-time Customer Data Platform分享至Customer Journey Analytics

* 請參閱 [與Customer Journey Analytics共用的RTCDP受眾](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/ingest-aep-segments.html?lang=en) 如需共用Real-time Customer Data Platform受眾以Customer Journey Analytics的其他詳細資訊。

## 相關檔案

* [[!UICONTROL Real-time Customer Data Platform] 產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/real-time-customer-data-platform.html)
* [個人資料與細分準則](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hant)
* [細分文件](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=zh-Hant)
* [目標文件](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=zh-Hant)

## 相關影片和教學課程

* [[!UICONTROL Real-time Customer Data Platform] 概述](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=zh-Hant)
* [示範 [!UICONTROL Real-time Customer Data Platform]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=zh-Hant)
* [建立區段](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=zh-Hant)
