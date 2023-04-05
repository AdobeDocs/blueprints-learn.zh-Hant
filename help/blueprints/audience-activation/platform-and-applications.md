---
title: 使用 Experience Cloud 應用程式的對象與個人資料啟用藍圖
description: 在 Experience Platform 中管理個人資料和對象，以及與 Experience Cloud 應用程式分享它們。
solution: Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services
kt: 7722
exl-id: f36014e8-170d-47e1-b4ec-10c0ea70612d
source-git-commit: 16ca42fdb944e658bfc1fb3e960e81cd67be049c
workflow-type: ht
source-wordcount: '896'
ht-degree: 100%

---

# 使用 Experience Cloud 應用程式的對象與個人資料啟用藍圖

在 Experience Platform 中管理個人資料和對象，以及與 Experience Cloud 應用程式分享它們。在 Experience Platform 中建立並分享豐富的客戶區段和客戶分析，並且在 Experience Cloud 應用程式中分享它們。

Experience Cloud 應用程式啟用與[已知客戶啟用藍圖](known.md)相一致。

## 使用案例

* Experience Cloud 支援的各客戶互動頻道中的個人化和目標。
* 在 Experience Platform 與 Experience Cloud 應用程式之間分享對象和個人資料。
* 從多通道資料（包括線上行為資料和資料科學模型）建立豐富的見解，以豐富 Experience Platform 中的即時客戶個人檔案，然後可與 Experience Cloud 應用程式共用。

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

如需與 Experience Cloud 應用程式整合的 Experience Platform 相關的其他架構圖，請參閱[Experience Platform 和應用程式架構部分](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/platform-applications.html?lang=zh-Hant)。

### Experience Cloud 應用程式的對象與個人資料啟用

<img src="../experience-platform/assets/aep+apps.svg" alt="使用 Experience Cloud 應用程式的對象與個人資料啟用之參考架構" style="width:90%; border:1px solid #4a4a4a"  class="modal-image" />
<br>

## 護欄

請參閱[「對象與個人資料啟用」概觀頁面所述的護欄](overview.md)和[部署護欄](../experience-platform/deployment/guardrails.md) 頁面。

## 實施考量

* 分享個人資料資料到目標需要您在目標負載中包含目標使用的特定身份值。對目標必要的任何身份必須擷取到 Platform，並且設定為[!UICONTROL 即時客戶個人資料]的身份。

### 受眾從 Real-time Customer Data Platform 分享至 Audience Manager

* 如需詳細資訊，請參閱下列文件。[使用 Audience Manager 及其他 Experience Cloud 解決方案的 Experience Platform 區段分享](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html?lang=zh-Hant).

* 當區段評估完成並寫入即時客戶個人檔案（不論是批次或串流中發生區段評估）時，RT-CDP 的對象成員資格會立即以串流方式共用給 Audience Manager。
* 如果符合資格的設定檔包含相關個人資料裝置的地區路由資訊，則來自 RTCDP 的對象成員資格會在相關 Audience Manager Edge 上以串流方式符合資格。如果將地區路由資訊套用至過去 14 天具有時間戳記的個人資料，則會串流到 Audience Manager Edge 上進行評估。如果 RTCDP 的個人資料中不包含區域路由資訊，或區域路由資訊超過 14 天，則 RTCDP 對象成員資格會發送到 Audience Manager 中心位置，以便進行基於批次的評估和啟用。
* 有了地區路由資訊，這些個人資料符合 Edge 啟用，並將在 RTCDP 區段資格認證後幾分鐘內啟用，不符合 Edge 啟動資格的設定檔將在 Audience Manager 中心取得資格，且可能有 12 至 24 小時的處理時間。
* 您可以收集存儲 Audience Manager 個人資料的 Edge 上所儲存的地區路由資訊，以從 Audience Manager、訪客 ID 服務、Analytics、Launch，或直接從 Web SDK Experience Platform 為個別的設定檔記錄類別資料集，使用「資料擷取地區資訊」XDM 欄位群組。如需詳細資訊，請參閱獲取地區資訊文件[連結](https://experienceleague.adobe.com/docs/id-service/using/reference/regions.html?lang=zh-Hant)。
* 在啟用案例中，會從 Experience Platform 將對象共用給 Audience Manager，下列身分自動共用：ECID、IDFA、GAID、雜湊電子郵件地址 (EMAIL_LC_SHA256)、AdCloud ID。目前不共用自訂命名空間。
* 當所需的目標身份包含在[!UICONTROL 即時客戶個人資料]中時，或者[!UICONTROL 即時客戶個人資料]中的身份可以關聯至 Audience Manager 中連結的所需目標身份時，Experience Platform 中的對象可透過 Audience Manager 目標分享。

### 從 Real-time Customer Data Platform 到 Target 的對象共用

* 如需從 Real-time Customer Data Platform 共用個人資料和對象的其他詳細資訊，請參閱[已知客戶個人化 — Target 和 RTCDP 藍圖](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/web-personalization/known-personalization.html?lang=zh-Hant)。

### 從 Real-time Customer Data Platform 到 Campaign 和 Journey Optimizer 的對象共用

* 如需從 Real-time Customer Data Platform 向 Campaign 和 Journey Optimizer 共用個人資料和對象的詳細資訊，請參閱 [Customer Journeys 藍圖](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/b2b-activation/b2bactivation.html?lang=zh-Hant)。

### 從 Real-time Customer Data Platform 至 Marketo Engage 共用對象

* 如需從 Real-time Customer Data Platform 向 Marketo Engage 共用設定檔和對象的其他詳細資訊，請參閱 [B2B 啟用藍圖](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/b2b-activation/b2bactivation.html?lang=zh-Hant)。

### 從 Real-time Customer Data Platform 向 Customer Journey Analytics 共用對象

* 如需將 Real-time Customer Data Platform 的對象共用給 Customer Journey Analytics 的其他詳細資訊，請參閱[與 Customer Journey Analytics 共用的 RTCDP 受眾](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/data-ingestion/ingest-aep-segments.html?lang=zh-Hant)。 

## 相關文件

* [[!UICONTROL Real-time Customer Data Platform]產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/real-time-customer-data-platform.html)
* [個人資料與細分準則](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hant)
* [細分文件](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=zh-Hant)
* [目標文件](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=zh-Hant)

## 相關視訊與教學課程

* [[!UICONTROL Real-time Customer Data Platform]概覽](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=zh-Hant)
* [[!UICONTROL Real-time Customer Data Platform]示範](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=zh-Hant)
* [建立區段](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=zh-Hant)
