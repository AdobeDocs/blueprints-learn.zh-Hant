---
title: Experience Platform 和應用程式護欄
description: 護欄定義了對 Adobe Experience Platform 和應用程式中的元件和服務的效能期望和影響
solution: Customer Journey Analytics, Journey Orchestration, Real-Time Customer Data Platform
thumbnail: null
exl-id: b64cf3e4-cc5d-4984-8a0f-4736d432b8e1
source-git-commit: 164793e15315d64cf38cb14928eac10cf6ae5c35
workflow-type: tm+mt
source-wordcount: '680'
ht-degree: 13%

---

# 護欄

護欄是建議的臨界值，可針對Adobe Experience Platform和應用程式中的資料、觀察到的延遲和系統使用情況提供指引。 護欄可反映系統限制和效能期望，以最佳化客戶架構和使用案例效能，並有助於避免錯誤或意外結果。 護欄並非服務等級協定，服務等級協定會記錄在下方連結的「產品說明」以及客戶授權協定中。 護欄旨在針對特定客戶使用案例提供架構解決方案的指引，以確保穩定性和執行力。

如需應用程式和功能的特定服務等級協定資訊，請參閱本頁底部的[應用程式和功能說明](#application-feature-descriptions)區段。

請注意，對於具有嚴格延遲或數量需求的任何客戶使用案例，Adobe建議與您的Adobe客戶團隊和實作合作夥伴詳細審視您的使用案例。 在某些情況下，建議在使用案例的生產推出前測試並觀察特定使用案例實施，以觀察和瞭解預期行為 — 因為每個客戶實施有不同的因素，包括資料擷取的性質和步調、正在建立的區段規則的細節，以及各種啟用管道和承載 — 每個使用案例實施的觀察效能將會不同。 因此，最好預先建立並測試預期的效能，以確保根據使用案例的延遲和效能需求提供適當的架構和實作。


## Adobe Experience Platform和應用程式的護欄參考檔案

下列頁面提供Adobe Experience Platform功能、服務和應用程式護欄的相關資訊：

**Experience Platform應用程式**

* [Real-Time CDP護欄總覽](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/guardrails/overview.html)
* [Customer Journey Analytics對象共用護欄](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html#latency)
* [Customer Journey Analytics資料擷取護欄](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html#what-is-the-expected-latency-for-analytics-data-on-platform%3F)
* [Journey Optimizer護欄](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/guardrails.html)

**Experience Platform服務**

* [資料擷取護欄](https://experienceleague.adobe.com/docs/experience-platform/ingestion/guardrails.html)
* [[!DNL Edge Network] API護欄](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/guardrails.html)
* [即時客戶設定檔和細分護欄](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hant)
* [身分護欄](https://experienceleague.adobe.com/docs/experience-platform/identity/guardrails.html?lang=zh-Hant)
* [Query Service 護欄](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html?lang=zh-Hant)
* [目標啟用護欄](https://experienceleague.adobe.com/docs/experience-platform/destinations/guardrails.html?lang=zh-Hant)

## 端到端延遲圖表 {#end-to-end-latency}

### Experience PlatformEdge Network和集線器主要觀察延遲 {#edge-hub-latencies}

下圖說明在Experience Platform和應用程式上建構使用案例時要注意的主要邊緣和集線器觀察延遲。

![Experience Platform[!DNL Edge Network]和中心主要觀察延遲。](/help/blueprints/experience-platform/deployment/assets/aep_edge_hub_latency_v1.svg "Experience PlatformEdge Network與中心主要觀察延遲"){width="1000" zoomable="yes"}

### 資料擷取 {#data-ingestion}

下圖顯示將資料引進Real-Time CDP時，透過[串流擷取](https://experienceleague.adobe.com/docs/experience-platform/ingestion/streaming/overview.html)和[批次擷取](https://experienceleague.adobe.com/docs/experience-platform/ingestion/batch/getting-started.html?lang=zh-Hant)預期的資料擷取延遲值。 按一下影像即可檢視高解析度版本。

![資料擷取高階視覺化概觀。](/help/blueprints/experience-platform/deployment/assets/aep_data_flow_guardrails.svg "資料擷取高階視覺概觀和延遲值"){width="1000" zoomable="yes"}

### 區段 {#segmentation}

下圖顯示使用[Real-Time CDP細分服務](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=zh-Hant)中的對象時的預期延遲值。 按一下影像即可檢視高解析度版本。

![分段高階視覺化概觀。](/help/blueprints/experience-platform/deployment/assets/segmentation_guardrails.svg "分段高階視覺概觀和延遲值"){width="1000" zoomable="yes"}

### Real-time Customer Data Platform &amp; [!DNL Edge Network] {#adobe-edge-latency}

下圖顯示運用[!DNL Edge Network]時的預期延遲值，例如在[Adobe Target](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=zh-Hant)中運用RTCDP對象。 按一下影像即可檢視高解析度版本。

![Adobe Edge網路和Experience Platform高階視覺化概觀。](/help/blueprints/experience-platform/deployment/assets/RTCDP_Edge_guardrails.svg "將對象匯出至Adobe Target高階視覺概觀和延遲"){width="1000" zoomable="yes"}

### Customer Journey Analytics {#customer-journey-analytics}

下圖顯示使用[Customer Journey Analytics](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-overview/cja-overview.html?lang=en)時的預期延遲值。 按一下影像即可檢視高解析度版本。

![使用Customer Journey Analytics高階視覺化概觀。](/help/blueprints/experience-platform/deployment/assets/CJA_guardrails.svg "使用Customer Journey Analytics高階視覺概覽和延遲值"){width="1000" zoomable="yes"}

### Journey Optimizer {#journey-optimizer}

下圖顯示使用[Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/get-started.html?lang=en)時的預期延遲值。 按一下影像即可檢視高解析度版本。

![使用Adobe Journey Optimizer高階視覺化概觀。](/help/blueprints/experience-platform/deployment/assets/AJO_guardrails.svg "使用Adobe Journey Optimizer高階視覺概觀和延遲值"){width="1000" zoomable="yes"}

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
