---
user-guide-title: 數位體驗 Blueprint
breadcrumb-title: Blueprint
user-guide-description: Blueprint 是可重複的實作，用於解決既有的業務問題，含有架構圖、技術考量及相關的文件連結。
product: adobe experience platform
mini-toc-levels: 3
role: Architect, Developer, User
source-git-commit: 374f3afa12611b21121e9bfe2fd906342ba1ea4f
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 44%

---


# 數位體驗 Blueprint {#architecture}

+ [概覽](/help/blueprints/overview.md)
+ 垂直行業藍圖{#vertical-blueprints}
   + [概覽](/help/blueprints/vertical-blueprints/overview.md)
   + [服裝](/help/blueprints/vertical-blueprints/apparel.md)
   + [零售](/help/blueprints/vertical-blueprints/retail.md)
   + [電信](/help/blueprints/vertical-blueprints/telecommunications.md)
   + [旅宿業](/help/blueprints/vertical-blueprints/travel-hospitality.md)
+ 架構概覽 {#architecture-overview}
   + [Experience Cloud](/help/blueprints/experience-platform/experience-cloud.md)
   + [Experience Platform 與應用程式](/help/blueprints/experience-platform/platform-applications.md)
   + [Experience Platform 資料流程](/help/blueprints/experience-platform/platform-data-flow.md)
   + 部署{#deployment}
      + [Experience PlatformWeb SDK和邊緣網路](/help/blueprints/experience-platform/deployment/websdk.md)
      + [應用程式SDK](/help/blueprints/experience-platform/deployment/appsdk.md)
      + [護欄](/help/blueprints/experience-platform/deployment/guardrails.md)
+ 對象與個人資料啟用 {#audience-activation}
   + [概覽](/help/blueprints/audience-activation/overview.md)
   + [匿名對象啟用 (AAM)](/help/blueprints/audience-activation/anonymous.md)
   + 已知客戶激活(RTCDP) {#known-customer-audience-activation}
      + [概覽](/help/blueprints/audience-activation/known.md)
      + [啟動社交和廣告管道](/help/blueprints/audience-activation/advertising-activation.md)
      + [啟動至檔案和企業串流目的地](/help/blueprints/audience-activation/enterprise-destinations.md)
      + [客戶活動中樞](/help/blueprints/audience-activation/customer-activity.md)
      + [區段符合](/help/blueprints/audience-activation/segment-match.md)
   + [使用 Experience Cloud 應用程式啟用](/help/blueprints/audience-activation/platform-and-applications.md)
+ B2B啟動與行銷{#b2b-activation}
   + [概覽](/help/blueprints/b2b/overview.md)
   + [B2B啟動](/help/blueprints/b2b/b2bactivation.md)
   + Campaign供應鏈及Marketo和Workfront{#optimize-campaign-supply-chain-with-marketo-and-workfront}
      + [概覽](/help/blueprints/b2b/campaign-supply-chain/overview.md)
      + [Intang and Create](/help/blueprints/b2b/campaign-supply-chain/intake-and-create.md)
      + [客戶成功案例](/help/blueprints/b2b/campaign-supply-chain/customer-success-stories.md)
+ Customer Journey Analytics {#customer-journey-analytics}
   + [概覽](/help/blueprints/customer-journey-analytics/overview.md)
   + [共用CJA受眾至RTCDP](/help/blueprints/customer-journey-analytics/cja-rtcdp.md)
   + [CJA與Journey Optimizer](/help/blueprints/customer-journey-analytics/cja-ajo.md)
+ 客戶歷程 {#customer-journeys}
   + [概覽](/help/blueprints/customer-journeys/overview.md)
   + Journey Optimizer{#journey-optimizer}
      + [Journey Optimizer](/help/blueprints/customer-journeys/journey-optimizer.md)
      + 決策管理{#decision-management}
         + [概覽](/help/blueprints/customer-journeys/decision_management/decision-management-overview.md)
         + [邊緣決策管理](/help/blueprints/customer-journeys/decision_management/decision-management-edge.md)
         + [中心的決策管理](/help/blueprints/customer-journeys/decision_management/decision-management-hub.md)
      + [Journey Optimizer搭配Adobe Campaign](/help/blueprints/customer-journeys/ajo-and-campaign.md)
      + [第三方傳訊](/help/blueprints/customer-journeys/3rd-party-messaging.md)
   + Campaign Standard{#campaign-standard}
      + [Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard.html){target="_blank"}
      + [Real-Time CDP搭配Adobe Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard/using/integrating-with-adobe-cloud/adobe-experience-platform/aep-sources-destinations/get-started-sources-destinations.html){target="_blank"}
   + Campaign v8{#campaign-v8}
      + [Campaign v8](/help/blueprints/customer-journeys/campaign-v8.md)
      + [Real-Time CDP搭配Adobe Campaign v8](/help/blueprints/customer-journeys/rtcdp-and-campaign-v8.md)
      + [Journey Optimizer搭配Adobe Campaign v8](/help/blueprints/customer-journeys/ajo-and-campaign-v8.md)
   + Campaign v7{#campaign-v7}
      + [Campaign v7](/help/blueprints/customer-journeys/campaign-v7.md)
      + [Real-Time CDP搭配Adobe Campaign v7](/help/blueprints/customer-journeys/rtcdp-and-campaign.md)
      + [Journey Optimizer搭配Adobe Campaign v7](/help/blueprints/customer-journeys/ajo-and-campaign-v7.md)
+ 資料收集、存取和匯出{#data-ingestion}
   + [概覽](/help/blueprints/data-ingestion/overview.md)
   + [資料準備與擷取 ](/help/blueprints/data-ingestion/ingestion.md)
   + [資料存取與匯出](/help/blueprints/data-ingestion/egress.md)
   + [事件轉送](/help/blueprints/data-ingestion/server-side-collection.md)
+ 資料分析、情報與 AI/ML {#data-exploration}
   + [概覽](/help/blueprints/data-insights/overview.md)
   + [資料分析與情報](/help/blueprints/data-insights/analysis.md)
   + [自訂資料科學以豐富個人資料](/help/blueprints/data-insights/data-science.md)
+ 網路與行動個人化 {#web-personalization}
   + [概覽](/help/blueprints/web-personalization/overview.md)
   + [行為個人化 - Target](/help/blueprints/web-personalization/behavioral.md)
   + [已知客戶個人化 — Target和RTCDP](/help/blueprints/web-personalization/known-personalization.md)
   + [決策管理](/help/blueprints/web-personalization/decision-management-edge.md)