---
title: 使用 Experience Cloud 應用程式的對象與個人資料啟用 Blueprint
description: 在 Experience Platform 中管理個人資料和對象，以及與 Experience Cloud 應用程式分享它們。
solution: Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services
kt: 7722
exl-id: f36014e8-170d-47e1-b4ec-10c0ea70612d
source-git-commit: 3425495df36ff8da0f2fd737b35d294ccafe31bd
workflow-type: tm+mt
source-wordcount: '741'
ht-degree: 46%

---

# 使用 Experience Cloud 應用程式的對象與個人資料啟用 Blueprint

在 Experience Platform 中管理個人資料和對象，以及與 Experience Cloud 應用程式分享它們。在 Experience Platform 中建立並分享豐富的客戶區段和客戶分析，並且在 Experience Cloud 應用程式中分享它們。

使用Experience Cloud應用程式激活與 [已知客戶激活藍圖](known.md)。

## 使用案例

* Experience Cloud 支援的各客戶互動頻道中的個人化和目標。
* 在 Experience Platform 與 Experience Cloud 應用程式之間分享對象和個人資料。

## 應用程式

* Adobe Experience Platform
* [!UICONTROL 即時客戶資料平台]
* Experience Platform 啟用
* Experience Cloud 應用程式
   * Adobe Audience Manager
   * Adobe Target
   * Adobe Campaign
   * Journey Optimizer

## 架構

查看 [Experience Platform和應用程式體系結構部分](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/platform-applications.html?lang=zh-Hant) 有關與Experience Platform與Experience Cloud應用程式整合相關的其他體系結構圖。

### 使用 Experience Cloud 應用程式的對象與個人資料啟用

<img src="../experience-platform/assets/aep+apps_horizontal.svg" alt="使用 Experience Cloud 應用程式的對象與個人資料啟用之參考架構" style="width:90%; border:1px solid #4a4a4a" />
<br>

## 護欄

請參閱[「對象與個人資料啟用」概觀頁面所述的護欄](overview.md)

## 實施考量

* 分享個人資料資料到目標需要您在目標負載中包含目標使用的特定身份值。對目標必要的任何身份必須擷取到 Platform，並且設定為[!UICONTROL 即時客戶個人資料]的身份。

### 從Real-time Customer Data Platform到Audience Manager的觀眾分享

* 有關更多詳細資訊，請參閱以下文檔。 [使用 Audience Manager 及其他 Experience Cloud 解決方案的 Experience Platform 區段分享](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html?lang=zh-Hant).

* 一旦完成段評估並將其寫入即時客戶配置檔案（無論段評估是批處理還是流處理）,RT-CDP的受眾成員身份將以流方式共用到Audience Manager。 如果限定的簡檔包含相關簡檔設備的區域路由資訊，則RTCDP的觀眾成員在相關的Audience Manager邊緣上以流方式限定。 如果將區域路由資訊應用於過去14天內時間戳記的配置檔案，則將在Audience Manager邊緣上以流形式進行計算。 如果RTCDP中的配置檔案不包含區域路由資訊或區域路由資訊大於14天，則配置檔案成員資格將發送到Audience Manager中心位置以進行基於批的評估和激活。 符合邊緣激活資格的配置檔案將在RTCDP的細分市場鑑定後幾分鐘內激活，不符合邊緣激活資格的配置檔案將在Audience Manager集線器中獲得資格，並且可能有12-24小時的處理時間。

* 可以從Audience Manager、訪問者ID服務、分析、啟動或直接從Web SDK中收集儲存了Audience Manager配置檔案的邊緣區域路由資訊，以便使用「資料捕獲區域資訊」 XDM欄位組作為單獨的配置檔案記錄類資料集進行Experience Platform。

* 對於從Experience Platform到Audience Manager的受眾共用的激活情形，將自動共用以下標識：ECID、IDFA、GAID、散列電子郵件地址(EMAIL_LC_SHA256)、AdCloud ID。 當前，未共用自定義命名空間。

* 當所需的目標身份包含在[!UICONTROL 即時客戶個人資料]中時，或者[!UICONTROL 即時客戶個人資料]中的身份可以關聯至 Audience Manager 中連結的所需目標身份時，Experience Platform 中的對象可透過 Audience Manager 目標分享。

### 從Real-time Customer Data Platform到目標的觀眾共用

* 查看 [Web/Mobile個性化，帶線上和離線資料藍圖](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/web-personalization/online-offline.html) 有關從Real-time Customer Data Platform到塔吉特共用簡介和觀眾的更多詳情。

### 從Real-time Customer Data Platform到運動和Journey Optimizer的觀眾分享

* 查看 [客戶旅程藍圖](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/overview.html) 有關分享簡介和觀眾的更多詳情，請訪問Real-time Customer Data Platform、競選和Journey Optimizer。

## 相關文件

* [[!UICONTROL 即時客戶資料平台]產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/real-time-customer-data-platform.html)
* [個人資料與細分準則](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hant)
* [細分文件](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=zh-Hant)
* [目標文件](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=zh-Hant)

## 相關視訊與教學課程

* [[!UICONTROL 即時客戶資料平台]概覽](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=zh-Hant)
* [[!UICONTROL 即時客戶資料平台]示範](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=zh-Hant)
* [建立區段](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=zh-Hant)
