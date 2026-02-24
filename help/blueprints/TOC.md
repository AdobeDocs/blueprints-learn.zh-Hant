---
user-guide-title: 客戶體驗協調藍圖
breadcrumb-title: 藍圖
user-guide-description: Blueprint 是可重複的實作，用於解決既有的業務問題，含有架構圖、技術考量及相關的文件連結。
product: adobe experience platform
mini-toc-levels: 3
role: Developer, User
source-git-commit: fb814fe6f5e4e774a96cbe75fea2499d849716b4
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 30%

---


# 客戶體驗協調藍圖 {#architecture}

+ [客戶體驗協調藍圖](/help/blueprints/overview.md)
+ 架構概述{#architecture-overview}
   + [Experience Cloud](/help/blueprints/experience-platform/experience-cloud.md)
   + [Experience Platform與應用程式](/help/blueprints/experience-platform/platform-applications.md)
   + [Experience Platform資料流程](/help/blueprints/experience-platform/platform-data-flow.md)
   + [Experience Platform護欄](/help/blueprints/experience-platform/guardrails.md)
   + 部署{#deployment}
      + [Experience Platform Web SDK &amp; [!DNL Edge Network]](/help/blueprints/experience-platform/deployment/websdk.md)
      + [應用程式 SDK](/help/blueprints/experience-platform/deployment/appsdk.md)
+ 對象與個人資料啟用{#audience-activation}
   + [以裝置為基礎 — 使用Audience Manager鎖定匿名受眾](/help/blueprints/audience-activation/audience-manager.md)
   + Real-Time Customer Data Platform (RTCDP) {#known-customer-audience-activation}
      + [社交和廣告目的地的受眾啟用](/help/blueprints/audience-activation/advertising-activation.md)
      + [企業目的地Blueprint的對象和設定檔啟用](/help/blueprints/audience-activation/enterprise-destinations.md)
      + [支援和銷售情境的即時設定檔存取](/help/blueprints/audience-activation/customer-activity.md)
      + [網頁和行動個人化的即時邊緣設定檔存取](/help/blueprints/audience-activation/real-time-lookup.md)
      + [透過區段比對進行對象共同作業](/help/blueprints/audience-activation/segment-match.md)
      + [使用Target的已知客戶個人化](/help/blueprints/audience-activation/rtcdp-target.md)
+ B2B啟用與行銷{#b2b-activation}
   + [概觀](/help/blueprints/b2b/overview.md)
   + [B2B啟用](/help/blueprints/b2b/b2bactivation.md)
   + [B2B帳戶啟用](/help/blueprints/b2b/b2b-account-activation.md)
   + [購買群組式行銷和歷程管理](/help/blueprints/b2b/b2b-buying-group-journeys.md)
   + [使用Marketo資料的B2B歷程](/help/blueprints/b2b/b2b-journeys-with-marketo.md)
   + [B2B付費媒體控制器](/help/blueprints/b2b/ajo-b2b-paid-media-controller.md)
   + Marketo Engage與Workfront整合Blueprint{#marketo-engage-and-workfront-integration-blueprint}
      + [概觀](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/overview.md)
      + [攝入與建立](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/intake-and-create.md)
      + [檢閱和核准](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint.md)
      + [客戶成功案例](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/customer-success-stories.md)
+ 內容與商務{#content-commerce}
   + [Adobe Commerce與Real-Time CDP](/help/blueprints/content-commerce/commerce/commerce-rtcdp.md)
+ Customer Journey Analytics{#customer-journey-analytics}
   + [概觀](/help/blueprints/customer-journey-analytics/overview.md)
   + [將CJA對象共用至RTCDP](/help/blueprints/customer-journey-analytics/cja-rtcdp.md)
   + [CJA 與 Journey Optimizer](/help/blueprints/customer-journey-analytics/cja-ajo.md)
+ 客戶歷程{#customer-journeys}
   + [概觀](/help/blueprints/customer-journeys/overview.md)
   + Journey Optimizer{#journey-optimizer}
      + [Journey Optimizer](/help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-overview.md)
      + [AJO 歷程](/help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-journeys.md)
      + [AJO 行銷活動](/help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-campaigns.md)
      + [協力廠商訊息](/help/blueprints/customer-journeys/journey-optimizer/3rd-party-messaging.md)
   + 決策管理{#decision-management}
      + [概觀](/help/blueprints/customer-journeys/decision-management/decision-management-overview.md)
      + [Edge上的決定管理](/help/blueprints/customer-journeys/decision-management/decision-management-edge.md)
      + [中樞的決策管理](/help/blueprints/customer-journeys/decision-management/decision-management-hub.md)
   + Campaign v8{#campaign-v8}
      + [Campaign v8](/help/blueprints/customer-journeys/campaign-v8/campaign-v8-overview.md)
      + [Real-Time CDP與Adobe [!DNL Campaign] v8](/help/blueprints/customer-journeys/campaign-v8/rtcdp-and-campaign-v8.md)
      + [Journey Optimizer 搭配 Adobe Campaign v8](/help/blueprints/customer-journeys/campaign-v8/ajo-and-campaign-v8.md)
   + 已棄用的Blueprint{#deprecated-blueprints}
      + Campaign Standard{#campaign-standard}
         + [[!DNL Campaign Standard]](https://experienceleague.adobe.com/zh-hant/docs/campaign-standard){target="_blank"}
         + [Real-Time CDP與Adobe [!DNL Campaign Standard]](https://experienceleague.adobe.com/zh-hant/docs/campaign-standard/using/integrating-with-adobe-cloud/adobe-experience-platform/get-started-sources-destinations)
      + Campaign v7{#campaign-v7}
         + [Campaign v7](/help/blueprints/customer-journeys/campaign-v7/campaign-v7-overview.md)
+ 資料分析、情報與 AI/ML{#data-exploration}
   + [資料分析與情報](/help/blueprints/data-insights/analysis.md)
   + [個人檔案擴充的自訂資料科學](/help/blueprints/data-insights/data-science.md)
