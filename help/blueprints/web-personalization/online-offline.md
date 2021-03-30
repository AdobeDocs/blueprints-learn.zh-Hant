---
title: 線上／離線網路個人化藍本
description: 將網路個人化與電子郵件及其他已知和匿名通道個人化同步。
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7194thumb-web-personalization-scenario2.jpg
translation-type: tm+mt
source-git-commit: 9b6c220a515c5abae22b58fe33558d7d2fed375d
workflow-type: tm+mt
source-wordcount: '958'
ht-degree: 0%

---



# 線上／離線網路個人化藍本

將網路個人化與電子郵件及其他已知和匿名通道個人化同步。

## 使用案例

* 著陸頁面最佳化
* 行為與離線描述檔定位
* 除了離線見解（例如交易、忠誠度和CRM資料）以及模型化見解外，還根據先前的產品／內容檢視、產品／內容親和力、環境屬性、協力廠商受眾資料和人口統計資料進行個人化

## 應用程式

* 即時客戶資料平台
* Adobe Target
* Adobe Audience Manager（可選）:新增協力廠商受眾資料、合作型裝置圖形、在Adobe Analytics呈現平台區段的能力，以及在平台呈現Adobe Analytics區段的能力
* Adobe Analytics（可選）:新增根據歷史行為資料建立區段的能力，以及從Adobe Analytics資料細部細分

## 建築

<img src="assets/onoff.svg" alt="線上／離線網頁個人化情境的參考架構" style="border:1px solid #4a4a4a" />

## 瓜德賴爾

* 從Experience Platform到Audience Manager共用的區段在區段實現後幾分鐘內即可共用——不論是透過串流或批次評估方法。 AEP和約4小時之間的初始區段AAM設定同步，讓AEP區段會籍開始在設定檔中AAM實現。 在設定檔中AAM,AEP區段會籍即可透過Adobe Target取得相同的頁面個人化。
* 請注意，對於在AEP和之間4小時區段設定同步內發生的區段實現AAM，這些區段實現將會在後續AAM的批次區段工作中，以「現有」區段的形式實現。
* 從AEP批次區段共用——每天一次，或透過API手動啟動。 這些區段會籍一經實現，即可在幾分鐘內共AAM用至Target中，並可供相同／下一頁個人化。
* 在約p95 5min內實現流分割。 一旦這些區段實現，它們就會在幾分AAM鐘內共用，並可在Target中供相同／下一頁個人化使用。
* 依預設，區段共用服務允許每個Adobe Analytics報表套裝共用最多75個對象。 如果客戶有Audience Manager授權，Adobe Analytics與Adobe Target或Audience Manager與Adobe Target之間可共用的受眾數目沒有限制。

## 實施先決條件

| 應用程式／服務 | 必要的程式庫 | 附註 |
|---|---|---|
| Adobe Target | 平台網頁SDK*、at.js 0.9.1+或mbox.js 61+ | at.js是偏好的，因為mbox.js不再開發。 |
| Adobe Audience Manager（選用） | Platform Web SDK*或dil.js 5.0+ |  |
| Adobe Analytics（選用） | 平台網頁SDK*或AppMeasurement.js 1.6.4+ | Adobe Analytics追蹤必須使用地區資料收集(RDC)。 |
| Experience CloudID服務 | 平台網頁SDK*或VisitorAPI.js 2.0+ | （建議）使用Experience Platform Launch來部署ID服務，以確保在任何應用程式呼叫前設定ID |
| Experience Platform行動SDK（選用） | iOS和Android™適用的4.11或更新版本 |  |
| Experience Platform網頁SDK | 1.0，目前的Experience PlatformSDK版本有[Experience Cloud應用程式尚未支援的各種使用案例](https://github.com/adobe/alloy/projects/5) |  |


## 實施步驟

1. [為您的網頁](https://experienceleague.adobe.com/docs/target/using/implement-target/implementing-target.html) 或行動應用程式建置Adobe定位
1. [實作Adobe Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html) （選用）
1. [實作Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/implementation/home.html)  （選用）
1. [實作Experience Platform與即時客戶個人檔案](https://experienceleague.adobe.com/docs/platform-learn/getting-started-for-data-architects-and-data-engineers/overview.html)
1. 實作[Experience Cloud身分服務](https://experienceleague.adobe.com/docs/id-service/using/implementation/implementation-guides.html)或[Experience Platform網頁SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html)
   >[!NOTE]
   >
   >每個應用程式都必須使用Experience CloudID，並且是同一Experience Cloud組織的一部分，才能允許應用程式之間的觀眾共用。
1. [請求布建Experience Platform與Adobe Target（共用觀眾）之間的觀眾共用](https://www.adobe.com/go/audiences)

## 實施資料流圖

Web/Mobile個人化藍圖可使用傳統應用程式專用的SDK（例如AppMeasurement.js），或使用Platform Web SDK/Mobile SDK和Edge Network來建置。

### 平台網頁／行動SDK與Edge方法

<img src="assets/websdkflow.svg" alt="平台網頁SDK/行動SDK與Edge網路方法的參考架構" style="border:1px solid #4a4a4a" />

### 應用程式專用的SDK方法

<img src="assets/appsdkflow.png" alt="應用程式專用SDK方法的參考架構" style="border:1px solid #4a4a4a" />

## 相關檔案

* [Experience Platform分部與Audience Manager及其他Experience Cloud解決方案共用](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html)
* [Experience Platform區段概觀](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html)
* [串流區段](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)
* [Experience Platform區段產生器概觀](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/overview.html)
* [Audience Manager源連接器](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/audience-manager.html)
* [Adobe Analytics區段分享透AAM過](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html)
* [Experience Platform網頁SDK檔案](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html)
* [Experience CloudID服務檔案](https://experienceleague.adobe.com/docs/id-service/using/home.html)
* [Experience Platform Launch檔案](https://experienceleague.adobe.com/docs/launch/using/home.html)

## 相關部落格文章

* [使用Adobe Experience Platform即時客戶個人檔案的網路個人化藍圖](https://medium.com/adobetech/blueprint-for-web-personalization-using-adobe-experience-platform-real-time-customer-profile-fef2ce7a4b2f)
* [建立最佳線上體驗：利用查詢服務豐富統一的配置檔案](https://medium.com/adobetech/build-an-optimal-online-experience-enrich-unified-profile-with-query-service-8027c196ab33)
* [整合Adobe Experience Platform決策引擎與網AEM站](https://jaeness.medium.com/integrating-adobe-experience-platform-decisioning-engine-with-aem-websites-9c222acd12e2)
* [Adobe Experience Platform的身分服務——如何解決客戶身分難題](https://medium.com/adobetech/adobe-experience-platforms-identity-service-how-to-solve-the-customer-identity-conundrum-f95e22d16ea9)
* [Adobe Experience Platform預測性受眾如何改善個人化體驗](https://medium.com/adobetech/how-adobe-experience-platform-predictive-audiences-improves-personalized-experiences-1f75a60cb7a3)
* [Adobe Experience PlatformWeb SDK的觀眾管理](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
* [通過我們的「客戶零」計畫實施Adobe Experience Platform即時客戶概要資訊](https://medium.com/adobetech/implementing-adobe-experience-platform-real-time-customer-profile-through-our-customer-zero-32e7cd952896)
* [Adobe Experience Platform公司如何通過Journey Orchestration服務和移動消息服務供應商幫助客戶即時個性化其移動消息服務](https://medium.com/adobetech/how-adobe-experience-platform-helped-a-client-personalize-their-mobile-messaging-in-real-time-with-7d634aefa098)
* [數秒即可劃分：Adobe Experience Platform如何讓即時客戶個人檔案成為現實](https://medium.com/adobetech/segmentation-in-seconds-how-adobe-experience-platform-made-real-time-customer-profiles-a-reality-a7a8552b0847)
* [建立最佳線上體驗：利用查詢服務豐富統一的配置檔案](https://medium.com/adobetech/build-an-optimal-online-experience-enrich-unified-profile-with-query-service-8027c196ab33)


