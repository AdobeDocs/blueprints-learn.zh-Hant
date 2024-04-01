---
user-guide-title: 數位體驗 Blueprint
breadcrumb-title: Blueprint
user-guide-description: Blueprint 是可重複的實作，用於解決既有的業務問題，含有架構圖、技術考量及相關的文件連結。
product: adobe experience platform
mini-toc-levels: 3
role: Architect, Developer, User
source-git-commit: 60a7785ea0ec4ee83fd9a1e843f0b84fc4cb1150
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 51%

---


# 數位體驗 Blueprint {#architecture}

+ [數位體驗藍圖](/help/blueprints/overview.md)
+ 垂直產業藍圖{#vertical-blueprints}
   + [概覽](/help/blueprints/vertical-blueprints/overview.md)
   + [服裝](/help/blueprints/vertical-blueprints/apparel.md)
   + [零售](/help/blueprints/vertical-blueprints/retail.md)
   + [電信](/help/blueprints/vertical-blueprints/telecommunications.md)
   + [旅遊業及旅館業](/help/blueprints/vertical-blueprints/travel-hospitality.md)
+ 架構概覽 {#architecture-overview}
   + [Experience Cloud](/help/blueprints/experience-platform/experience-cloud.md)
   + [Experience Platform與應用程式](/help/blueprints/experience-platform/platform-applications.md)
   + [Experience Platform資料流程](/help/blueprints/experience-platform/platform-data-flow.md)
   + 部署 {#deployment}
      + [Experience PlatformWeb SDK &amp; [!DNL Edge Network]](/help/blueprints/experience-platform/deployment/websdk.md)
      + [應用程式 SDK](/help/blueprints/experience-platform/deployment/appsdk.md)
      + [護欄](/help/blueprints/experience-platform/deployment/guardrails.md)
+ 對象與個人資料啟用 {#audience-activation}
   + [概覽](/help/blueprints/audience-activation/overview.md)
   + [匿名Audience Activation(AAM)](/help/blueprints/audience-activation/anonymous.md)
   + 已知客戶啟用 (RTCDP) {#known-customer-audience-activation}
      + [概覽](/help/blueprints/audience-activation/known.md)
      + [啟用社交和廣告頻道](/help/blueprints/audience-activation/advertising-activation.md)
      + [啟用檔案和企業串流目的地](/help/blueprints/audience-activation/enterprise-destinations.md)
      + [客戶活動中心](/help/blueprints/audience-activation/customer-activity.md)
      + [區段比對](/help/blueprints/audience-activation/segment-match.md)
   + [使用Experience Cloud應用程式啟動](/help/blueprints/audience-activation/platform-and-applications.md)
   + 網路與行動個人化 {#web-personalization}
      + [概覽](/help/blueprints/audience-activation/web-personalization/overview.md)
      + [行為個人化 — 目標](/help/blueprints//audience-activation/web-personalization/behavioral.md)
      + [已知的客戶個人化 — Target和RTCDP](/help/blueprints/audience-activation/web-personalization/known-personalization.md)
      + [決定管理](/help/blueprints/audience-activation/web-personalization/decision-management-edge.md)
+ B2B 啟用與行銷 {#b2b-activation}
   + [概覽](/help/blueprints/b2b/overview.md)
   + [B2B啟用](/help/blueprints/b2b/b2bactivation.md)
   + Marketo Engage與Workfront整合藍圖{#marketo-engage-and-workfront-integration-blueprint}
      + [概覽](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/overview.md)
      + [攝入與建立](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/intake-and-create.md)
      + [檢閱和核准](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint.md)
      + [客戶成功案例](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/customer-success-stories.md)
+ 內容與商務{#content-commerce}
   + [Adobe Commerce與RTCDP](/help/blueprints/content-commerce/commerce/commerce-rtcdp.md)
+ Customer Journey Analytics {#customer-journey-analytics}
   + [概覽](/help/blueprints/customer-journey-analytics/overview.md)
   + [將CJA對象分享到RTCDP](/help/blueprints/customer-journey-analytics/cja-rtcdp.md)
   + [CJA 與 Journey Optimizer](/help/blueprints/customer-journey-analytics/cja-ajo.md)
+ 客戶歷程 {#customer-journeys}
   + [概覽](/help/blueprints/customer-journeys/overview.md)
   + Journey Optimizer {#journey-optimizer}
      + [Journey Optimizer](/help/blueprints/customer-journeys/journey-optimizer.md)
      + 決策管理 {#decision-management}
         + [概覽](/help/blueprints/customer-journeys/decision_management/decision-management-overview.md)
         + [邊緣決策管理](/help/blueprints/customer-journeys/decision_management/decision-management-edge.md)
         + [中心的決策管理](/help/blueprints/customer-journeys/decision_management/decision-management-hub.md)
      + [Journey Optimizer 搭配 Adobe Campaign](/help/blueprints/customer-journeys/ajo-and-campaign.md)
      + [協力廠商訊息](/help/blueprints/customer-journeys/3rd-party-messaging.md)
   + Campaign Standard {#campaign-standard}
      + [[!DNL Campaign Standard]](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=zh-Hant){target="_blank"}
      + [Real-Time CDP與Adobe [!DNL Campaign Standard]](https://experienceleague.adobe.com/docs/campaign-standard/using/integrating-with-adobe-cloud/adobe-experience-platform/aep-sources-destinations/get-started-sources-destinations.html?lang=zh-Hant){target="_blank"}
   + Campaign v8 {#campaign-v8}
      + [Campaign v8](/help/blueprints/customer-journeys/campaign-v8.md)
      + [Real-Time CDP與Adobe [!DNL Campaign] v8](/help/blueprints/customer-journeys/rtcdp-and-campaign-v8.md)
      + [Journey Optimizer 搭配 Adobe Campaign v8](/help/blueprints/customer-journeys/ajo-and-campaign-v8.md)
   + Campaign v7 {#campaign-v7}
      + [Campaign v7](/help/blueprints/customer-journeys/campaign-v7.md)
      + [Real-Time CDP與Adobe [!DNL Campaign] v7](/help/blueprints/customer-journeys/rtcdp-and-campaign.md)
      + [Journey Optimizer與Adobe [!DNL Campaign] v7](/help/blueprints/customer-journeys/ajo-and-campaign-v7.md)
+ 資料收集、存取和匯出 {#data-ingestion}
   + [概覽](/help/blueprints/data-ingestion/overview.md)
   + [多沙箱事件轉送資料收集](/help/blueprints/data-ingestion/multi-sandbox-event-forwarding.md)
   + [資料準備與擷取](/help/blueprints/data-ingestion/ingestion.md)
   + [資料存取與匯出](/help/blueprints/data-ingestion/egress.md)
   + [事件轉送](/help/blueprints/data-ingestion/server-side-collection.md)
+ 資料分析、情報與 AI/ML {#data-exploration}
   + [概覽](/help/blueprints/data-insights/overview.md)
   + [資料分析與情報](/help/blueprints/data-insights/analysis.md)
   + [個人檔案擴充的自訂資料科學](/help/blueprints/data-insights/data-science.md)
