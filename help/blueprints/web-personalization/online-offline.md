---
title: 使用線上和離線資料的網頁/行動個人化
description: 同步網路個人化與電子郵件及其他已知和匿名的通道個人化。
landing-page-description: 同步網路個人化與電子郵件及其他已知和匿名的通道個人化。
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7194thumb-web-personalization-scenario2.jpg
exl-id: 29667c0e-bb79-432e-af3a-45bd0b3b43bb
source-git-commit: 0de426911553ae3b7907d7d08b25a07a11b34c0f
workflow-type: tm+mt
source-wordcount: '1078'
ht-degree: 57%

---

# 使用線上和離線資料的網頁/行動個人化

同步網路個人化與電子郵件及其他已知和匿名的通道個人化。

## 使用案例

* 登陸頁面最佳化
* 行為與離線個人資料目標定位
* 除離線深入見解 (如異動、忠誠度與 CRM 資料及建模的深入見解) 外，基於之前產品/內容視圖、產品/內容相似性、環境屬性、協力廠商對象資料及人口統計資料的個人化
* 在使用Adobe Target的網站和行動應用程式上共用和鎖定Real-time Customer Data Platform中定義的對象。

## 應用程式

* [!UICONTROL 即時客戶資料平台]
* Adobe Target
* Adobe Audience Manager (可選)：新增協力廠商對象資料、基於協作的裝置圖、在 Adobe Analytics 中顯示 Platform 區段的能力，以及在 Platform 中顯示 Adobe Analytics 區段的能力
* Adobe Analytics (可選)：新增基於歷史行為資料以及 Adobe Analytics 資料的細分建立區段的能力

## 整合模式

<table class="tg" style="undefined;table-layout: fixed; width: 790px">
<colgroup>
<col style="width: 20px">
<col style="width: 276px">
<col style="width: 229px">
<col style="width: 265px">
</colgroup>
<thead>
  <tr>
    <th class="tg-y6fn">#</th>
    <th class="tg-f7v4">整合模式</th>
    <th class="tg-y6fn">功能</th>
    <th class="tg-f7v4">先決條件</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0lax">1</td>
    <td class="tg-73oq"><span style="font-weight:400;font-style:normal">透過受眾共用服務方法，將受眾串流和批次共用給Target和Audience Manager</span></td>
    <td class="tg-0lax"><span style="font-weight:400;font-style:normal"> — 透過受眾共用服務，從RTCDP共用串流和批次受眾至Target及Audience Manager。 即時評估的對象需要整合模式3中概述的WebSDK和即時對象評估。</span></td>
    <td class="tg-73oq"> — 必須透過受眾共用服務布建受眾投影。<br> — 與Target整合需要與Experience Platform例項相同的IMS組織。<br> — 身分必須解析為ECID才能共用至邊緣，Target才能執行動作。 AAM有獨立的已核准身分清單，可比對<br> — 此整合不需要部署WebSDK。</td>
  </tr>
  <tr>
    <td class="tg-0lax">2</td>
    <td class="tg-73oq">透過Edge方法將RTCDP串流和批次受眾共用給Target</td>
    <td class="tg-0lax"> — 透過Edge Network將串流和批次受眾從RTCDP共用至Target。 即時評估的對象需要整合模式3中概述的WebSDK和即時對象評估。</td>
    <td class="tg-73oq"><span style="text-decoration:none"> — 目前測試版</span><br> — 必須在RTCDP目標中配置目標目標。<br> — 與Target整合需要與Experience Platform例項相同的IMS組織。<br>WebSDK不是必要項目。 支援WebSDk和AT.js。 <br> — 如果使用AT.js，則僅支援對ECID進行設定檔查閱。 <br> — 若要在Edge上查閱自訂ID命名空間，需要WebSDK部署，且每個身分必須在身分對應中設定為身分。</td>
  </tr>
  <tr>
    <td class="tg-0lax">3</td>
    <td class="tg-73oq">透過使用WebSDK的Edge網路與Target共用的Edge上，進行RTCDP即時區段評估。</td>
    <td class="tg-0lax"> — 即時評估Edge上相同或下一頁個人化的對象。</td>
    <td class="tg-73oq"><span style="text-decoration:none"> — 目前測試版</span><br> — 必須在RTCDP目標中配置目標目標。<br> — 與Target整合需要與Experience Platform例項相同的IMS組織。<br> — 必須實作WebSDK。<br> — 也支援透過API使用。</td>
  </tr>
</tbody>
</table>


## 架構

概述架構

<img src="assets/RTCDP+Target.png" alt="線上/離線網路個人化 Blueprint 的參考架構" style="width:80%; border:1px solid #4a4a4a" />

詳細架構

<img src="assets/online_offline_personalization_with_apps.svg" alt="線上/離線網路個人化 Blueprint 的參考架構" style="width:80%; border:1px solid #4a4a4a" />

## 護欄

[請參閱「網路與行動個人化 Blueprints」概觀頁面所述的護欄。](overview.md)

## 實施模式

網路/行動個人化 Blueprint 可透過下列方法實施，如下所述。

1. 使用 [!UICONTROL Platform Web SDK] 或 [!UICONTROL Platform Mobile SDK] 及 [!UICONTROL Edge Network]。
1. 使用傳統應用程式特定的 SDK (例如 AppMeasurement.js)

### 1. Platform Web/Mobile SDK 與 Edge 方法

[請參閱 Experience Platform Web 和 Mobile SDK Blueprint](../data-ingestion/websdk.md)

### 2. 應用程式特定的 SDK 方法

<img src="assets/app_sdk_flow.png" alt="應用程式特定 SDK 方法的參考架構" style="width:80%; border:1px solid #4a4a4a" />

## 實施先決條件

身分先決條件

* 將受眾從Adobe Experience Platform共用至Adobe Target需要使用ECID做為身分。
* 替代身分也可用來透過Audience Manager與Adobe Target共用Experience Platform對象。 Experience Platform會透過下列支援的命名空間啟用對象以Audience Manager:IDFA、GAID、AdCloud、Google、ECID、EMAIL_LC_SHA256。 請注意，Audience Manager和Target會透過ECID身分識別解析對象成員資格，因此要將對象共用至Adobe Target，仍需要ECID。

| 應用程式 / 服務 | 所需的資料庫 | 附註 |
|---|---|---|
| Adobe Target | [!UICONTROL Platform Web SDK]*、at.js 0.9.1+ 或 mbox.js 61+ | 首選 at.js，因為 mbox.js 不再進行開發。 |
| Adobe Audience Manager (可選) | [!UICONTROL Platform Web SDK]* 或 dil.js 5.0+ |  |
| Adobe Analytics (可選) | [!UICONTROL Platform Web SDK]* 或 AppMeasurement.js 1.6.4+ | Adobe Analytics 追蹤必須使用 Regional Data Collection (RDC)。 |
| Experience Cloud ID 服務 | [!UICONTROL Platform Web SDK]* 或 VisitorAPI.js 2.0+ | (推薦) 使用 Experience Platform Launch 部署 ID 服務以確保在任何應用程式調用之前設定 ID |
| Experience Platform Mobile SDK (可選) | iOS 和 Android™ 的 4.11 或更高版本 |  |
| Experience Platform Web SDK | 1.0，目前的 Experience Platform SDK 版本具有[Experience Cloud 應用程式尚不支援的各種使用案例](https://github.com/adobe/alloy/projects/5) |  |




## 實施步驟

1. 對您的網路或行動應用程式[實施 Adobe Target](https://experienceleague.adobe.com/docs/target/using/implement-target/implementing-target.html?lang=zh-Hant)
1. [實施 Adobe Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html?lang=zh-Hant) (可選)
1. [實施 Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/implementation/home.html?lang=zh-Hant) (可選)
1. [實施 Experience Platform 與[!UICONTROL 即時客戶個人資料]](https://experienceleague.adobe.com/docs/platform-learn/getting-started-for-data-architects-and-data-engineers/overview.html?lang=zh-Hant)
1. 實施 [Experience Cloud Identity 服務](https://experienceleague.adobe.com/docs/id-service/using/implementation/implementation-guides.html?lang=zh-Hant) 或 [Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html?lang=zh-Hant)
1. [請求在 Experience Platform 與 Adobe Target 之間佈建對象分享 (已分享對象)](https://www.adobe.com/go/audiences)
   >[!NOTE]
   >
   >在RTCDP和Adobe Target之間使用「對象共用」服務時，必須使用Experience CloudID共用對象，並成為相同Experience Cloud組織的一部分。若要支援ECID以外的身分識別，必須使用WebSDK和Experience Edge Network。


## 相關文件

* [使用 Audience Manager 及其他 Experience Cloud 解決方案的 Experience Platform 區段分享](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html?lang=zh-Hant)
* [Experience Platform 細分概覽](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=zh-Hant)
* [串流細分](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=zh-Hant)
* [Experience Platform Segment Builder 概覽](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/overview.html?lang=zh-Hant)
* [Audience Manager 來源連接器](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/audience-manager.html?lang=zh-Hant)
* [透過 Adobe Audience Manager 分享 Adobe Analytics 區段](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=zh-Hant)
* [Experience Platform Web SDK 文件](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html)
* [Experience Cloud ID 服務文件](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=zh-Hant)
* [Experience Platform標籤檔案](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html)

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
