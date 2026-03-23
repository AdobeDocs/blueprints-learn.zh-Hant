---
user-guide-title: 客戶體驗協調業務目標、使用案例、架構圖表和藍圖
breadcrumb-title: 使用案例和藍圖
user-guide-description: 探索Adobe Experience Platform和應用程式的主要業務目標、使用案例模式及產業使用案例。 視覺化架構圖表和藍圖提供系統整合、資料流程和解決方案設計的技術參考，將業務價值連結至實作。
product: adobe experience platform
mini-toc-levels: 3
role: Developer, User
source-git-commit: 63154ca158b773287f0d1a7f88a81ac3181c43a0
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 24%

---


# 客戶體驗協調藍圖 {#architecture}

+ [客戶體驗協調藍圖](/help/blueprints/overview.md)
+ AEP與應用程式的主要業務目標{#business-objectives}
   + [概觀](/help/blueprints/business-objectives/overview.md)
   + 收購與成長{#acquisition-growth}
      + [贏取新客戶](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)
      + [增加銷售機會開發](/help/blueprints/business-objectives/acquisition-growth/increase-lead-generation.md)
      + [增加網站參與度](/help/blueprints/business-objectives/acquisition-growth/increase-website-engagement.md)
   + 收入與營收{#revenue-monetization}
      + [提高轉換率](/help/blueprints/business-objectives/revenue-monetization/increase-conversion-rates.md)
      + [增加收入與銷售](/help/blueprints/business-objectives/revenue-monetization/increase-revenue-sales.md)
      + [提高交叉銷售和追加銷售收入](/help/blueprints/business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)
      + [提高客戶忠誠度和期限值](/help/blueprints/business-objectives/revenue-monetization/increase-customer-loyalty-lifetime-value.md)
   + 成本與效率{#cost-efficiency}
      + [降低客戶贏取成本](/help/blueprints/business-objectives/cost-efficiency/reduce-customer-acquisition-cost.md)
      + [最佳化行銷支出和ROI](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md)
      + [改善資料品質和控管](/help/blueprints/business-objectives/cost-efficiency/improve-data-quality-governance.md)
      + [整合及更新行銷技術](/help/blueprints/business-objectives/cost-efficiency/consolidate-modernize-marketing-technology.md)
   + 客戶體驗{#customer-experience-objectives}
      + [提供個人化的客戶體驗](/help/blueprints/business-objectives/customer-experience/deliver-personalized-customer-experiences.md)
      + [提升客戶保留率](/help/blueprints/business-objectives/customer-experience/improve-customer-retention.md)
      + [改善客戶入門](/help/blueprints/business-objectives/customer-experience/improve-customer-onboarding.md)
      + [復原放棄的購物車與歷程](/help/blueprints/business-objectives/customer-experience/recover-abandoned-carts-journeys.md)
   + Analytics &amp; Insights{#analytics-insights}
      + [改善分析和報告](/help/blueprints/business-objectives/analytics-insights/improve-analytics-reporting.md)
      + [啟用資料導向式決策](/help/blueprints/business-objectives/analytics-insights/enable-data-driven-decision-making.md)
      + [改善行銷歸因](/help/blueprints/business-objectives/analytics-insights/improve-marketing-attribution.md)
   + 資格與銷售(B2B){#qualification-sales-b2b}
      + [改善銷售機會資格和轉換](/help/blueprints/business-objectives/qualification-sales-b2b/improve-lead-qualification-conversion.md)
      + [改善客戶參與度](/help/blueprints/business-objectives/qualification-sales-b2b/improve-customer-engagement.md)
+ 使用案例模式{#use-case-patterns}
   + [概觀](/help/blueprints/use-case-patterns/overview.md)
   + Audience Builder &amp; Activation{#audience-building-activation}
      + [Audience Activation至目的地](/help/blueprints/use-case-patterns/audience-building-activation/audience-activation-to-destinations.md)
      + [有區段比對的對象Collaboration](/help/blueprints/use-case-patterns/audience-building-activation/audience-collaboration-segment-match.md)
      + [事件轉送](/help/blueprints/use-case-patterns/audience-building-activation/event-forwarding.md)
      + [B2B Audience Activation](/help/blueprints/use-case-patterns/audience-building-activation/b2b-audience-activation.md)
   + 個人化{#personalization-patterns}
      + [匿名訪客網頁Personalization](/help/blueprints/use-case-patterns/personalization/anonymous-visitor-web-personalization.md)
      + [已知訪客網頁/應用程式Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md)
      + [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md)
      + [行為建議](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md)
   + 行銷活動管理與協調{#campaign-orchestration-patterns}
      + [批次傳出訊息啟用](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md)
      + [事件觸發式傳訊](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)
      + [多步驟協調歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)
      + [具有決策的跨頻道歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md)
      + [購買群組式行銷與歷程管理](/help/blueprints/use-case-patterns/campaign-management-orchestration/buying-group-based-marketing.md)
   + 分析{#analysis-patterns}
      + [Customer Analytics與Insight開發](/help/blueprints/use-case-patterns/analysis/customer-analytics-insight-generation.md)
      + [B2B分析](/help/blueprints/use-case-patterns/analysis/b2b-analytics.md)
   + 對話體驗{#conversational-experience-patterns}
      + [Brand Concierge對話體驗](/help/blueprints/use-case-patterns/conversational-experience/brand-concierge-conversational-experience.md)
+ 產業使用案例範例{#industry-use-cases}
   + [使用案例目錄](/help/blueprints/industry-use-cases/use-case-catalog.md)
   + [汽車](/help/blueprints/industry-use-cases/automotive/automotive-overview.md)
   + [B2B](/help/blueprints/industry-use-cases/b2b/b2b-overview.md)
   + [金融服務](/help/blueprints/industry-use-cases/financial-services/financial-services-overview.md)
   + [保健](/help/blueprints/industry-use-cases/healthcare/healthcare-overview.md)
   + [保險業](/help/blueprints/industry-use-cases/insurance/insurance-overview.md)
   + [媒體與娛樂](/help/blueprints/industry-use-cases/media-entertainment/media-entertainment-overview.md)
   + [零售](/help/blueprints/industry-use-cases/retail/retail-overview.md)
   + [電信](/help/blueprints/industry-use-cases/telecommunications/telecommunications-overview.md)
   + [旅遊業及旅館業](/help/blueprints/industry-use-cases/travel-hospitality/travel-hospitality-overview.md)
+ 架構圖與藍圖{#architecture-diagrams}
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
         + [個人檔案擴充的自訂資料科學](/help/blueprints/audience-activation/data-science.md)
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
   + Customer Journey Analytics{#customer-journey-analytics}
      + [概觀](/help/blueprints/customer-journey-analytics/overview.md)
      + [B2B Customer Journey Analytics](/help/blueprints/customer-journey-analytics/b2b-cja.md)
      + [將CJA對象共用至RTCDP](/help/blueprints/customer-journey-analytics/cja-rtcdp.md)
      + [CJA 與 Journey Optimizer](/help/blueprints/customer-journey-analytics/cja-ajo.md)
      + [資料分析與情報](/help/blueprints/customer-journey-analytics/analysis.md)
   + 客戶歷程{#customer-journeys}
      + [概觀](/help/blueprints/customer-journeys/overview.md)
      + Journey Optimizer{#journey-optimizer}
         + [Journey Optimizer](/help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-overview.md)
         + [AJO歷程](/help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-journeys.md)
         + [AJO行銷活動](/help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-campaigns.md)
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
