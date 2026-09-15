---
user-guide-title: 客戶體驗協調業務目標、使用案例、架構圖表和藍圖
breadcrumb-title: 使用案例和藍圖
user-guide-description: 探索Adobe Experience Platform和應用程式的主要業務目標、使用案例模式及產業使用案例。 視覺化架構圖表和藍圖提供系統整合、資料流程和解決方案設計的技術參考，將業務價值連結至實作。
product: Adobe Experience Platform
mini-toc-levels: 3
role: Developer, User
nudge: orange
source-git-commit: df6c1852a6e0357dc9f166c88e77dcf9d334f955
workflow-type: tm+mt
source-wordcount: '1169'
ht-degree: 14%
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
    + [支援與銷售人員的即時設定檔查詢](/help/blueprints/use-case-patterns/audience-building-activation/real-time-profile-lookup.md)
    + [設定檔擴充的自訂資料科學](/help/blueprints/use-case-patterns/audience-building-activation/data-science-profile-enrichment.md)
  + 個人化{#personalization-patterns}
    + [匿名訪客網頁Personalization](/help/blueprints/use-case-patterns/personalization/anonymous-visitor-web-personalization.md)
    + [已知訪客網頁/應用程式Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md)
    + [Offer Decisioning](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md)
    + [行為建議](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md)
    + [適用於Web/行動Personalization的Edge設定檔存取](/help/blueprints/use-case-patterns/personalization/edge-profile-access.md)
    + [使用Adobe Target共用對象](/help/blueprints/use-case-patterns/personalization/audience-sharing-with-target.md)
  + 行銷活動管理與協調{#campaign-orchestration-patterns}
    + [批次傳出訊息啟用](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md)
    + [事件觸發式傳訊](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)
    + [多步驟協調歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)
    + [具有決策的跨頻道歷程](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md)
    + [Campaign v8批次協調與異動訊息](/help/blueprints/use-case-patterns/campaign-management-orchestration/campaign-v8-orchestration.md)
    + [協力廠商傳訊與Journey Optimizer整合](/help/blueprints/use-case-patterns/campaign-management-orchestration/third-party-messaging.md)
  + 分析{#analysis-patterns}
    + [Customer Analytics與Insight開發](/help/blueprints/use-case-patterns/analysis/customer-analytics-insight-generation.md)
  + B2B啟用與行銷{#b2b-patterns}
    + [B2B Audience Activation](/help/blueprints/use-case-patterns/b2b/account-audience-activation.md)
    + [購買群組式行銷與歷程管理](/help/blueprints/use-case-patterns/b2b/buying-group-marketing.md)
    + [B2B分析](/help/blueprints/use-case-patterns/b2b/account-analytics.md)
    + [使用Marketo資料的B2B歷程](/help/blueprints/use-case-patterns/b2b/marketo-data-journeys.md)
    + [AJO B2B付費媒體控制者](/help/blueprints/use-case-patterns/b2b/paid-media-orchestration.md)
    + [Marketo和Workfront攝入與建立](/help/blueprints/use-case-patterns/b2b/campaign-intake-and-creation.md)
    + [Marketo和Workfront檢閱與核准](/help/blueprints/use-case-patterns/b2b/campaign-review-and-approval.md)
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
  + [技術](/help/blueprints/industry-use-cases/technology/technology-overview.md)
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

+ 實作實驗室{#labs}
  + [實作實驗室概觀](/help/blueprints/labs/overview.md)
  + 實作研討會{#workshops}
    + AEP基礎{#aep-foundations}
      + [概觀](/help/blueprints/labs/aep-foundations/overview.md)
      + [設定](/help/blueprints/labs/aep-foundations/setup.md)
      + 沙箱設定{#aep-sandbox}
        + [Developer Console設定](/help/blueprints/labs/aep-foundations/sandbox-setup/developer-console-setup.md)
        + [部署指示](/help/blueprints/labs/aep-foundations/sandbox-setup/deployment-instructions.md)
      + Postman設定{#aep-postman}
        + [Postman安裝](/help/blueprints/labs/aep-foundations/postman-setup/postman-installation.md)
        + [環境檔案](/help/blueprints/labs/aep-foundations/postman-setup/environment-file.md)
        + [API集合](/help/blueprints/labs/aep-foundations/postman-setup/api-collection.md)
        + [沙箱存取](/help/blueprints/labs/aep-foundations/postman-setup/sandbox-access.md)
        + [存取權杖](/help/blueprints/labs/aep-foundations/postman-setup/access-token.md)
      + 即時客戶個人檔案{#aep-rtcp}
        + [講座](/help/blueprints/labs/aep-foundations/real-time-customer-profile/lectures.md)
        + 檢查設定檔{#aep-rtcp-inspect}
          + [概觀](/help/blueprints/labs/aep-foundations/real-time-customer-profile/inspecting-the-profile/overview.md)
          + [設定檔基本知識](/help/blueprints/labs/aep-foundations/real-time-customer-profile/inspecting-the-profile/profile-basics.md)
          + [合併政策](/help/blueprints/labs/aep-foundations/real-time-customer-profile/inspecting-the-profile/merge-policies.md)
          + [設定檔與身分API](/help/blueprints/labs/aep-foundations/real-time-customer-profile/inspecting-the-profile/profile-and-identity-apis.md)
      + LID方法{#aep-lid}
        + [先決條件](/help/blueprints/labs/aep-foundations/lid-methodology/prerequisites.md)
        + [標籤](/help/blueprints/labs/aep-foundations/lid-methodology/label.md)
        + 識別{#aep-lid-identify}
          + [概觀](/help/blueprints/labs/aep-foundations/lid-methodology/identify/overview.md)
          + [第1部分 — 剩餘表格型別](/help/blueprints/labs/aep-foundations/lid-methodology/identify/part-1-remaining-table-types.md)
          + [第2部分 — 主要欄位](/help/blueprints/labs/aep-foundations/lid-methodology/identify/part-2-key-fields.md)
        + [非正規化](/help/blueprints/labs/aep-foundations/lid-methodology/denormalize.md)
      + XDM模型化{#aep-xdm}
        + [講座](/help/blueprints/labs/aep-foundations/xdm-modeling/lectures.md)
        + UI模型化{#aep-xdm-ui}
          + [概觀](/help/blueprints/labs/aep-foundations/xdm-modeling/ui-modeling/overview.md)
          + [登入並瀏覽](/help/blueprints/labs/aep-foundations/xdm-modeling/ui-modeling/login-and-browse.md)
          + [模型標準物件](/help/blueprints/labs/aep-foundations/xdm-modeling/ui-modeling/model-standard-objects.md)
          + [模型自訂物件](/help/blueprints/labs/aep-foundations/xdm-modeling/ui-modeling/model-custom-objects.md)
          + [為設定檔進行設定](/help/blueprints/labs/aep-foundations/xdm-modeling/ui-modeling/configure-for-profile.md)
        + API模型化{#aep-xdm-api}
          + [概觀](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/overview.md)
          + 建置結構描述{#aep-xdm-api-build}
            + [概觀](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/build-schema/overview.md)
            + [取得標準欄位群組](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/build-schema/get-standard-field-groups.md)
            + [建立自訂欄位群組](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/build-schema/create-custom-field-groups.md)
            + [取得設定檔類別](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/build-schema/get-profile-class.md)
            + [建立結構描述](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/build-schema/create-schema.md)
            + [檢視結構描述](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/build-schema/view-schema.md)
            + [修改結構 — JSON修補程式](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/build-schema/modify-schema-json-patch.md)
          + 標示身分欄位{#aep-xdm-api-identity}
            + [概觀](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/mark-identity-fields/overview.md)
            + [建立主要身分](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/mark-identity-fields/create-primary-identity.md)
            + [建立其他身分](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/mark-identity-fields/create-other-identities.md)
            + [檢視結構描述](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/mark-identity-fields/view-schema.md)
          + 定義關係{#aep-xdm-api-relationships}
            + [概觀](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/define-relationships/overview.md)
            + [取得計畫結構描述ID](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/define-relationships/get-plan-schema-id.md)
            + [建立結構描述關係](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/define-relationships/create-schema-relationship.md)
            + [建立計畫參考身分](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/define-relationships/create-plan-reference-identity.md)
            + [檢視結構描述](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/define-relationships/view-schema.md)
          + [重述](/help/blueprints/labs/aep-foundations/xdm-modeling/api-modeling/recap.md)
        + 額外的Labs{#aep-xdm-bonus}
          + [使用API自動化](/help/blueprints/labs/aep-foundations/xdm-modeling/bonus-labs/automate-with-apis.md)
      + 資料攝取{#aep-ingestion}
        + [講座](/help/blueprints/labs/aep-foundations/data-ingestion/lectures.md)
        + [Lab概述](/help/blueprints/labs/aep-foundations/data-ingestion/lab-overview.md)
        + [範例檔案](/help/blueprints/labs/aep-foundations/data-ingestion/sample-files.md)
        + 批次擷取{#aep-ingestion-batch}
          + [概觀](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/overview.md)
          + [建立資料流](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/create-dataflow.md)
          + 對應資料{#aep-ingestion-batch-mapping}
            + [概觀](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/mapping-data/overview.md)
            + [修正傳遞對應](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/mapping-data/fix-passthrough-mappings.md)
            + [計算欄位](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/mapping-data/calculated-fields.md)
            + [檢查最終對應集](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/mapping-data/check-final-mapping-set.md)
          + [執行資料流](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/run-dataflow.md)
          + [偵錯錯誤](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/debugging-errors.md)
          + [建立新的資料流](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/create-a-new-dataflow.md)
          + [修正錯誤](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/fixing-errors.md)
          + [驗證與驗證](/help/blueprints/labs/aep-foundations/data-ingestion/batch-ingestion/verification-and-validation.md)
        + 串流擷取{#aep-ingestion-stream}
          + [概觀](/help/blueprints/labs/aep-foundations/data-ingestion/stream-ingestion/overview.md)
          + [設定Source](/help/blueprints/labs/aep-foundations/data-ingestion/stream-ingestion/setup-source.md)
          + [設定對應](/help/blueprints/labs/aep-foundations/data-ingestion/stream-ingestion/configure-mapping.md)
          + [檢查最終對應集](/help/blueprints/labs/aep-foundations/data-ingestion/stream-ingestion/check-final-mapping-set.md)
          + [串流設定檔](/help/blueprints/labs/aep-foundations/data-ingestion/stream-ingestion/stream-a-profile.md)
          + [驗證已擷取的設定檔](/help/blueprints/labs/aep-foundations/data-ingestion/stream-ingestion/verify-ingested-profile.md)
          + [監視和偵錯錯誤](/help/blueprints/labs/aep-foundations/data-ingestion/stream-ingestion/monitoring-and-debugging-errors.md)
          + [驗證與驗證](/help/blueprints/labs/aep-foundations/data-ingestion/stream-ingestion/verification-and-validation.md)
        + 額外的Labs{#aep-ingestion-bonus}
          + [修正CreateDate的MAPPER錯誤](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/fix-mapper-errors-for-createdate.md)
          + [串流訂單事件](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/stream-an-order-event.md)
          + 使用資料登陸區域{#aep-ingestion-dlz}
            + [概觀](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/overview.md)
            + [設定Source](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/setup-source.md)
            + [建立對應](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/create-mappings.md)
            + [排程資料流](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/schedule-dataflow.md)
            + [重試失敗的資料流](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/retry-a-failed-dataflow.md)
            + 載入訂單{#aep-ingestion-dlz-orders}
              + [概觀](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/load-orders/overview.md)
              + [設定Source](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/load-orders/setup-source.md)
              + [初始對應](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/load-orders/initial-mappings.md)
              + [物件複製對應](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/load-orders/object-copy-mappings.md)
              + [驗證及排程資料流](/help/blueprints/labs/aep-foundations/data-ingestion/bonus-labs/using-data-landing-zone/load-orders/verify-and-schedule-dataflow.md)
      + 細分和啟動{#aep-segmentation}
        + [講座](/help/blueprints/labs/aep-foundations/segmentation-and-activation/lecture.md)
        + Edge啟用{#aep-segmentation-edge}
          + [概觀](/help/blueprints/labs/aep-foundations/segmentation-and-activation/edge-activation/overview.md)
          + [建立Edge受眾](/help/blueprints/labs/aep-foundations/segmentation-and-activation/edge-activation/create-edge-audience.md)
          + [傳送Edge事件](/help/blueprints/labs/aep-foundations/segmentation-and-activation/edge-activation/send-an-edge-event.md)
          + 設定事件轉送{#aep-segmentation-edge-ef}
            + [概觀](/help/blueprints/labs/aep-foundations/segmentation-and-activation/edge-activation/setup-event-forwarding/overview.md)
            + [建立屬性](/help/blueprints/labs/aep-foundations/segmentation-and-activation/edge-activation/setup-event-forwarding/create-property.md)
            + [建立資料串流](/help/blueprints/labs/aep-foundations/segmentation-and-activation/edge-activation/setup-event-forwarding/create-datastream.md)
      + 對象建立{#aep-audiences}
        + 使用案例1 — 贏取{#aep-uc1}
          + [概觀](/help/blueprints/labs/aep-foundations/audience-building/use-case-1-acquisition/overview.md)
          + 設定目的地{#aep-uc1-destinations}
            + [設定自訂Personalization目的地](/help/blueprints/labs/aep-foundations/audience-building/use-case-1-acquisition/configure-destinations/setup-custom-personalization-destination.md)
            + [設定串流目的地](/help/blueprints/labs/aep-foundations/audience-building/use-case-1-acquisition/configure-destinations/setup-streaming-destination.md)
          + [建立對象1](/help/blueprints/labs/aep-foundations/audience-building/use-case-1-acquisition/build-audience-1.md)
          + [建立對象2](/help/blueprints/labs/aep-foundations/audience-building/use-case-1-acquisition/build-audience-2.md)
          + [建立對象3](/help/blueprints/labs/aep-foundations/audience-building/use-case-1-acquisition/build-audience-3.md)
          + [傳送Edge事件](/help/blueprints/labs/aep-foundations/audience-building/use-case-1-acquisition/send-an-edge-event.md)
          + [批判性思維評論](/help/blueprints/labs/aep-foundations/audience-building/use-case-1-acquisition/critical-thinking-review.md)
        + 使用案例2 — 向上銷售{#aep-uc2}
          + [概觀](/help/blueprints/labs/aep-foundations/audience-building/use-case-2-upsell/overview.md)
          + [前期工作](/help/blueprints/labs/aep-foundations/audience-building/use-case-2-upsell/pre-work.md)
          + [選項1 — 使用對象來彙總](/help/blueprints/labs/aep-foundations/audience-building/use-case-2-upsell/option-1-using-audiences-to-aggregate.md)
          + [選項2 — 使用預先彙總](/help/blueprints/labs/aep-foundations/audience-building/use-case-2-upsell/option-2-use-pre-aggregates.md)
          + [批判性思維評論](/help/blueprints/labs/aep-foundations/audience-building/use-case-2-upsell/critical-thinking-review.md)
        + 使用案例3 — 外聯{#aep-uc3}
          + [概觀](/help/blueprints/labs/aep-foundations/audience-building/use-case-3-outreach/overview.md)
          + [建置使用案例3](/help/blueprints/labs/aep-foundations/audience-building/use-case-3-outreach/build-use-case-3.md)
          + [批判性思維評論](/help/blueprints/labs/aep-foundations/audience-building/use-case-3-outreach/critical-thinking-review.md)
        + 額外的Labs{#aep-audiences-bonus}
          + [傳送訂單事件至中樞](/help/blueprints/labs/aep-foundations/audience-building/bonus-labs/send-order-event-to-hub.md)
          + [傳送Web事件至中樞](/help/blueprints/labs/aep-foundations/audience-building/bonus-labs/send-web-event-to-hub.md)
          + [監視您的事件](/help/blueprints/labs/aep-foundations/audience-building/bonus-labs/monitor-your-event.md)
    + AJO基礎{#ajo-foundations}
      + [概觀](/help/blueprints/labs/ajo-foundations/overview.md)
      + [設定](/help/blueprints/labs/ajo-foundations/setup.md)
      + 沙箱設定{#ajo-sandbox}
        + [Developer Console設定](/help/blueprints/labs/ajo-foundations/sandbox-setup/developer-console-setup.md)
        + [部署指示](/help/blueprints/labs/ajo-foundations/sandbox-setup/deployment-instructions.md)
      + Postman設定{#ajo-postman}
        + [Postman安裝](/help/blueprints/labs/ajo-foundations/postman-setup/postman-installation.md)
        + [匯入環境檔案](/help/blueprints/labs/ajo-foundations/postman-setup/import-environment-file.md)
        + [匯入API集合](/help/blueprints/labs/ajo-foundations/postman-setup/import-api-collection.md)
      + 架構建置區塊{#ajo-architecture}
        + [講座](/help/blueprints/labs/ajo-foundations/architecture-building-blocks/lecture.md)
        + 將使用案例對應至架構{#ajo-architecture-mapping}
          + [概觀](/help/blueprints/labs/ajo-foundations/architecture-building-blocks/mapping-use-cases-to-architecture/overview.md)
          + [Lab簡介](/help/blueprints/labs/ajo-foundations/architecture-building-blocks/mapping-use-cases-to-architecture/lab-introduction.md)
          + [實驗室練習](/help/blueprints/labs/ajo-foundations/architecture-building-blocks/mapping-use-cases-to-architecture/lab-exercise.md)
          + [實驗室審查](/help/blueprints/labs/ajo-foundations/architecture-building-blocks/mapping-use-cases-to-architecture/lab-review.md)
      + 資料存放區{#ajo-data-stores}
        + [即時客戶個人檔案講座](/help/blueprints/labs/ajo-foundations/data-stores/real-time-customer-profile-lecture.md)
        + 作用中的設定檔{#ajo-profile}
          + [概觀](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/overview.md)
          + [登入並瀏覽](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/login-and-browse.md)
          + [建立資料串流](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/create-datastream.md)
          + [傳送Edge Web事件](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/send-an-edge-web-event.md)
          + [驗證集線器上的設定檔](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/validate-profile-on-hub.md)
          + [在Edge上驗證設定檔](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/validate-profile-on-edge.md)
          + [驗證Data Lake的事件](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/validate-event-on-data-lake.md)
          + [驗證設定檔快照](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/validate-profile-snapshot.md)
          + [摘要](/help/blueprints/labs/ajo-foundations/data-stores/profile-in-action/summary.md)
        + [關聯式商店講座](/help/blueprints/labs/ajo-foundations/data-stores/relational-store-lecture.md)
        + 關聯式存放區執行中{#ajo-relational}
          + [概觀](/help/blueprints/labs/ajo-foundations/data-stores/relational-store-in-action/overview.md)
          + [瀏覽結構描述](/help/blueprints/labs/ajo-foundations/data-stores/relational-store-in-action/browse-schemas.md)
          + [設定檔目標Dimension](/help/blueprints/labs/ajo-foundations/data-stores/relational-store-in-action/profile-target-dimension.md)
          + [讀取對象](/help/blueprints/labs/ajo-foundations/data-stores/relational-store-in-action/read-an-audience.md)
          + [摘要](/help/blueprints/labs/ajo-foundations/data-stores/relational-store-in-action/summary.md)
        + 設定電子郵件通道{#ajo-email}
          + [概觀](/help/blueprints/labs/ajo-foundations/data-stores/configure-email-channels/overview.md)
          + [為設定檔進行設定](/help/blueprints/labs/ajo-foundations/data-stores/configure-email-channels/configure-for-profile.md)
          + [設定關聯式](/help/blueprints/labs/ajo-foundations/data-stores/configure-email-channels/configure-for-relational.md)
          + [正在等待作用中狀態](/help/blueprints/labs/ajo-foundations/data-stores/configure-email-channels/waiting-for-active-status.md)
      + 協調的行銷活動{#ajo-campaigns}
        + [訊息傳遞講座](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/message-delivery-lecture.md)
        + 訊息傳遞正在執行中{#ajo-campaigns-delivery}
          + [概觀](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/message-delivery-in-action/overview.md)
          + [建立行銷活動](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/message-delivery-in-action/create-a-campaign.md)
          + [建立對象](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/message-delivery-in-action/build-an-audience.md)
          + [新增分叉活動](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/message-delivery-in-action/add-fork-activity.md)
          + [新增電子郵件活動](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/message-delivery-in-action/add-email-activities.md)
          + [測試行銷活動](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/message-delivery-in-action/test-the-campaign.md)
          + [摘要](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/message-delivery-in-action/summary.md)
        + [工作流程建置區塊講座](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/workflow-building-blocks-lecture.md)
        + 旗艦手機上市{#ajo-campaigns-flagship}
          + [概觀](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/overview.md)
          + [設定簡訊頻道](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/configure-sms-channel.md)
          + [建立協調的行銷活動](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/create-an-orchestrated-campaign.md)
          + [建立對象](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/build-an-audience.md)
          + [取用結果](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/fork-the-result.md)
          + [儲存對象](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/save-the-audience.md)
          + [篩選線條](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/filter-the-lines.md)
          + [撰寫簡訊](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/compose-the-sms.md)
          + [執行工作流程](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/run-the-workflow.md)
          + [摘要](/help/blueprints/labs/ajo-foundations/orchestrated-campaigns/flagship-phone-launch/summary.md)
      + 歷程{#ajo-journeys}
        + [講座](/help/blueprints/labs/ajo-foundations/journeys/lecture.md)
        + 購買後的興奮感{#ajo-journeys-post-purchase}
          + [概觀](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/overview.md)
          + [設定事件](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/configure-event.md)
          + [設定自訂動作](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/configure-custom-action.md)
          + [建立歷程](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/build-journey.md)
          + [測試歷程](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/test-journey.md)
          + [傳送事件](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/send-an-event.md)
          + [驗證已擷取的事件](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/validate-event-ingested.md)
          + [驗證歷程](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/validate-journey.md)
          + [摘要](/help/blueprints/labs/ajo-foundations/journeys/post-purchase-excitement/summary.md)
      + 決策{#ajo-decisioning}
        + [體驗Edge](/help/blueprints/labs/ajo-foundations/decisioning/experience-edge.md)
        + 說明決策{#ajo-decisioning-explained}
          + [概觀](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/overview.md)
          + [簡介](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/introduction.md)
          + [決定專案XDM](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/decision-item-xdm.md)
          + [建立決定專案](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/decision-item-creation.md)
          + [集合](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/collections.md)
          + [排名公式](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/ranking-formulas.md)
          + [選取策略](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/selection-strategies.md)
          + [決定原則](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/decision-policies.md)
          + [護欄，AI模型未來決策](/help/blueprints/labs/ajo-foundations/decisioning/decisioning-explained/guardrails-ai-models-decisioning-future.md)
        + 捨棄的瀏覽{#ajo-decisioning-abandoned}
          + [概觀](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/overview.md)
          + [建立決定規則](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/create-decision-rule.md)
          + [建立優惠屬性](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/create-offer-attributes.md)
          + [建立選件專案](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/create-offer-items.md)
          + [建立優惠收藏](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/create-offer-collection.md)
          + [建立排名公式](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/create-ranking-formula.md)
          + [建立選取策略](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/create-selection-strategy.md)
          + [建立程式碼型體驗管道](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/create-code-based-experience-channel.md)
          + [建立歷程](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/create-the-journey.md)
          + [決策和CBE的實際運作](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/decisioning-and-cbes-in-action.md)
          + [摘要](/help/blueprints/labs/ajo-foundations/decisioning/abandoned-browse/summary.md)
      + 使用AI編寫內容{#ajo-content-ai}
        + [講座](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/lecture.md)
        + [概觀](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/overview.md)
        + [品牌管理](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/brand-management.md)
        + [建立內容片段](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/building-content-fragments.md)
        + [建立內容範本](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/building-content-template.md)
        + [建立電子郵件](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/creating-the-email.md)
        + [AI助理與內容Personalization](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/ai-assistant-and-content-personalization.md)
        + [Personalization與內容實驗](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/personalization-and-content-experimentation.md)
        + [內容模擬](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/content-simulation.md)
        + [品牌一致性](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/brand-alignment.md)
        + [測試電子郵件](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/test-the-email.md)
        + [摘要](/help/blueprints/labs/ajo-foundations/content-authoring-with-ai/summary.md)
