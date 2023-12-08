---
title: Experience Platform和應用程式護欄和端對端延遲
description: 護欄定義了對 Adobe Experience Platform 和應用程式中的元件和服務的效能期望和影響
solution: Customer Journey Analytics, Journey Orchestration, Real-Time Customer Data Platform
thumbnail: null
exl-id: b64cf3e4-cc5d-4984-8a0f-4736d432b8e1
source-git-commit: 94197d1b450694f96eb1ef17245c0353494859b1
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 23%

---

# 護欄

護欄是建議的臨界值，可為Adobe Experience Platform和應用程式中的資料和系統使用提供指引。 護欄可反映系統限制和效能期望，以最佳化客戶架構和使用案例效能，並有助於避免錯誤或意外結果。 護欄並非服務等級協定。

如需應用程式與功能之特定服務等級協定的相關資訊，請參閱 [應用程式和功能說明](#application-feature-descriptions) 區段。


## Adobe Experience Platform和應用程式的護欄參考檔案

下列頁面提供Adobe Experience Platform功能、服務和應用程式護欄的相關資訊：

**Experience Platform應用程式**

* [Real-Time CDP護欄概觀](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/guardrails/overview.html)
* [Customer Journey Analytics受眾共用護欄](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html?lang=en#latency)
* [Customer Journey Analytics資料擷取護欄](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html?lang=en#what-is-the-expected-latency-for-analytics-data-on-platform%3F)
* [Journey Optimizer護欄](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/guardrails.html?lang=zh-Hant)

**Experience Platform服務**

* [資料擷取護欄](https://experienceleague.adobe.com/docs/experience-platform/ingestion/guardrails.html?lang=zh-Hant)
* [Edge Network API 護欄](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/guardrails.html?lang=zh-Hant)
* [Real-time Customer Profile 護欄](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hant)
* [身分護欄](https://experienceleague.adobe.com/docs/experience-platform/identity/guardrails.html?lang=zh-Hant)
* [Query Service 護欄](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html?lang=zh-Hant)
* [目標啟用護欄](https://experienceleague.adobe.com/docs/experience-platform/destinations/guardrails.html?lang=zh-Hant)

## 端到端延遲圖表 {#end-to-end-latency}

### 資料擷取 {#data-ingestion}

下圖透過顯示預期的資料擷取延遲值 [串流擷取](https://experienceleague.adobe.com/docs/experience-platform/ingestion/streaming/overview.html) 和 [批次擷取](https://experienceleague.adobe.com/docs/experience-platform/ingestion/batch/getting-started.html?lang=zh-Hant) 將資料帶入Real-Time CDP時。 按一下影像即可檢視高解析度版本。

![資料擷取高階視覺化概觀。](/help/blueprints/experience-platform/deployment/assets/aep_data_flow_guardrails.svg "資料擷取高階視覺概覽和延遲值"){width="1000" zoomable="yes"}

### 區段 {#segmentation}

下圖顯示使用中的對象時的預期延遲值 [Real-Time CDP細分服務](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=zh-Hant). 按一下影像即可檢視高解析度版本。

![區段高階視覺化概觀。](/help/blueprints/experience-platform/deployment/assets/segmentation_guardrails.svg "區段高階視覺效果概觀和延遲值"){width="1000" zoomable="yes"}

### Real-time Customer Data Platform 與 Adobe Target {#adobe-target-latency}

下圖顯示從Real-Time CDP將對象匯出至時的預期延遲值 [Adobe Target](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=zh-Hant). 按一下影像即可檢視高解析度版本。

![匯出至Adobe Target高階視覺化概觀。](/help/blueprints/experience-platform/deployment/assets/RTCDP_Target_guardrails.svg "將對象匯出至Adobe Target高階視覺概觀和延遲值"){width="1000" zoomable="yes"}

### Customer Journey Analytics {#customer-journey-analytics}

下圖顯示使用時的預期延遲值 [Customer Journey Analytics](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-overview/cja-overview.html?lang=en). 按一下影像即可檢視高解析度版本。

![使用Customer Journey Analytics高階視覺化概觀。](/help/blueprints/experience-platform/deployment/assets/CJA_guardrails.svg "使用Customer Journey Analytics高階視覺化概覽和延遲值"){width="1000" zoomable="yes"}

### Journey Optimizer {#journey-optimizer}

下圖顯示使用時的預期延遲值 [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/get-started.html?lang=en). 按一下影像即可檢視高解析度版本。

![使用Adobe Journey Optimizer高階視覺效果概述。](/help/blueprints/experience-platform/deployment/assets/AJO_guardrails.svg "使用Adobe Journey Optimizer高階視覺化概覽和延遲值"){width="1000" zoomable="yes"}

## 應用程式和功能說明 {#application-feature-descriptions}

如需功能特定服務等級協定的資訊，請參閱下列產品說明：

* [Experience Platform Collection Enterprise](https://helpx.adobe.com/tw/legal/product-descriptions/adobe-experience-platform-collection-enterprise.html)
* [Real-time Customer Data Platform](https://helpx.adobe.com/tw/legal/product-descriptions/real-time-customer-data-platform.html)
* [B2B Customer Data Platform](https://helpx.adobe.com/tw/legal/product-descriptions/adobe-experience-platform-b2b.html)
* [Experience Platform 啟用](https://helpx.adobe.com/tw/legal/product-descriptions/adobe-experience-platform0.html)
* [Experience Platform 情報](https://helpx.adobe.com/tw/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [Intelligent Services](https://helpx.adobe.com/tw/legal/product-descriptions/intelligent-services.html)
* [Data Distiller](https://helpx.adobe.com/tw/legal/product-descriptions/data-distiller.html)
* [Customer Journey Analytics](https://helpx.adobe.com/tw/legal/product-descriptions/customer-journey-analytics.html)
* [Journey Optimizer](https://helpx.adobe.com/tw/legal/product-descriptions/adobe-journey-optimizer.html)
* [Journey Orchestration](https://helpx.adobe.com/tw/legal/product-descriptions/journey-orchestration.html)
* [Offer Decisioning](https://helpx.adobe.com/tw/legal/product-descriptions/offer-decisioning-app-service.html)
