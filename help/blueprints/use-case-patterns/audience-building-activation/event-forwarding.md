---
title: 事件轉送
description: 瞭解如何將透過Edge Network收集的即時事件資料轉送至分析、儲存或廣告的非Adobe目的地。
solution: Experience Platform
exl-id: 24964d27-db56-4fa4-a79f-1b6750564b34
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1165'
ht-degree: 0%

---

# 事件轉送

本指南說明事件轉送使用案例模式，其使用[!DNL Adobe Experience Platform] Edge Network上的伺服器端處理，將即時事件資料發佈至非Adobe目的地，例如協力廠商分析平台、雲端儲存空間端點、廣告網路或自訂Webhook。 它專為需要瞭解此模式的功能、其支援的業務目標、其啟用的戰術使用案例以及所涉及的Adobe應用程式的解決方案架構師、行銷技術人員和實作工程師所設計。

## 使用案例模式

本節說明用於實作事件轉送的模式和執行計畫。

**事件轉送** — 將透過Edge Network收集的即時事件資料轉送至非Adobe目的地，以用於分析、儲存或廣告。

**執行計畫：**&#x200B;資料流設定>事件規則定義>目的地對應>轉送執行>監視

## 使用案例概述

透過[!DNL Adobe Experience Platform]網頁SDK、Mobile SDK或伺服器API收集行為資料的組織，通常需要與非Adobe系統（例如[!DNL Google Analytics]或[!DNL Snowflake]等分析平台、轉換追蹤的廣告網路、長期儲存的資料倉儲或自訂內部服務）共用相同的事件資料流。 傳統上，這需要使用者端標籤大量增加，這會增加頁面重量、造成延遲，並產生隱私權和治理風險。

事件轉送可透過在Edge Network上操作伺服器端來解決此問題。 當訪客互動透過網頁SDK或伺服器API觸發事件時，該事件會透過資料流路由傳送至Edge Network。 事件轉送規則（在專用事件轉送屬性中設定）會評估傳入事件資料，並選擇性地將其轉送至一或多個已設定的目的地。 伺服器端方法可減少使用者端標籤膨脹、改善頁面效能、集中資料控管，並讓組織能夠確切控制哪些資料離開Adobe生態系統。

此模式的目標對象包括已部署（或計畫部署）用於資料收集的[!DNL Adobe Experience Platform] Web SDK或伺服器API，並想要透過將事件資料分發到非Adobe端點來擴大該投資的組織，而不新增使用者端JavaScript標籤。

## 主要業務目標

此使用案例模式支援下列業務目標。

### 改善資料品質和管理

確保資料乾淨、完整且合規，以實現準確定位、減少浪費及可靠分析。 事件轉送可在伺服器端集中處理資料分佈，為組織提供與外部系統共用資料的單一控制點，降低資料洩漏的風險，並確保在資料離開[!DNL Adobe] Edge Network之前套用治理原則。

**KPI：**&#x200B;效率、成本節省

如需詳細資訊，請參閱[改善資料品質和控管](../../business-objectives/cost-efficiency/improve-data-quality-governance.md)。

### 整合併更新行銷技術

遷移至統一、可擴充的平台，減少工具分散和技術負債。 事件轉送可讓組織使用單一伺服器端資料發佈機制來取代多個使用者端廠商標籤，減少頁面載入開銷並簡化技術棧疊。

**KPI：**&#x200B;節省成本、效率、上市速度

如需詳細資訊，請參閱[整合併更新行銷技術](../../business-objectives/cost-efficiency/consolidate-modernize-marketing-technology.md)。

## 戰術使用案例範例

以下是適用於此使用案例模式的常見戰術情境。

- **協力廠商分析擴充** — 即時將頁面檢視、點按和轉換事件轉寄給[!DNL Google Analytics]、[!DNL Snowflake]或其他分析平台，而不新增使用者端標籤
- **Advertising轉換追蹤** — 將購買和銷售機會產生事件傳送至[!DNL Meta]轉換API、[!DNL Google Ads]、[!DNL TikTok]或[!DNL Snap]，以用於伺服器端轉換測量和最佳化
- **資料倉儲串流** — 將原始事件資料路由到雲端資料倉儲([!DNL Google BigQuery]、[!DNL Amazon S3]、[!DNL Azure Event Hubs])，以進行長期儲存和離線分析
- **自訂webhook整合** — 透過HTTP端點將經過篩選或轉換的事件資料轉送至內部微服務、CRM系統或合作夥伴平台
- **減少標籤與改善頁面效能** — 以單一Web SDK實作以及伺服器端事件轉送規則，取代多個使用者端廠商JavaScript標籤，減輕頁面重量並改善Core Web Vitals
- **符合隱私權規範的資料共用** — 在與協力廠商共用事件資料之前，先在伺服器端套用資料篩選和欄位層級密文規則，確保PII在到達外部系統之前被清除或雜湊
- **多雲端事件分佈** — 從單一伺服器端規則集同時將相同的事件資料流轉送至多個目的地（例如，分析、廣告和資料倉儲）
- **即時詐騙訊號轉送** — 將高價值交易事件轉送至詐騙偵測系統，以便即時取得風險評分和警示

## 關鍵績效指標

以下KPI可協助評估此使用案例模式的成功。

- **減少頁面載入時間** — 測量到將使用者端標籤移轉至伺服器端事件轉送後，頁面載入速度和Core Web Vitals的改善
- **資料傳送成功率** — 成功轉送至目的地端點的事件百分比，且沒有錯誤或逾時
- **標籤計數減少** — 實作伺服器端對等項後移除的使用者端廠商標籤數目
- **資料新鮮度/延遲** — 使用者端上發生事件與事件到達目的地端點之間的時間（目標：次秒至秒）
- **治理合規率** — 通過伺服器端篩選規則的傳出資料共用百分比，可確保沒有PII或受限制的資料到達未經授權的目的地
- **營運效率** — 減少開發人員管理使用者端標籤部署和疑難排解標籤衝突所花費的時間

## 應用程式

在此使用案例模式中使用以下應用程式。

- **[!DNL Adobe Experience Platform] (Edge Network)** — 透過已設定的資料串流，從Web SDK、Mobile SDK或伺服器API接收及路由即時事件資料
- **[!DNL Adobe Experience Platform]（事件轉送）** — 提供伺服器端規則引擎，用於評估、篩選、轉換事件資料並將資料轉送至外部目的地
- **[!DNL Adobe Experience Platform]（標籤/資料集合）** — 管理事件轉送屬性生命週期、擴充功能、規則和發佈工作流程

## 相關文件

下列資源提供本指南涵蓋主題的額外詳細資料。

**事件轉送**

- [事件轉送概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/tags/event-forwarding/overview)
- [事件轉送快速入門](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/tags/event-forwarding/getting-started)
- [事件轉送監控](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/tags/event-forwarding/monitoring)
- [事件轉送密碼](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/tags/event-forwarding/secrets)

**事件轉送延伸模組**

- [伺服器端擴充功能目錄](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/tags/extensions/server/overview)
- [Adobe Cloud Connector擴充功能](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/tags/extensions/server/cloud-connector/overview)
- [Meta Conversions API擴充功能](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/tags/extensions/server/meta/overview)
- [Google Cloud Platform擴充功能](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/tags/extensions/server/google-cloud-platform/overview)
- [AWS擴充功能](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/tags/extensions/server/aws/overview)
- [Snowflake擴充功能](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/tags/extensions/server/snowflake/overview)
- [Google Ads增強型轉換延伸功能](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/tags/extensions/server/google-ads-enhanced-conversions/overview)
- [Mailchimp擴充功能](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/tags/extensions/server/mailchimp/overview)

**資料收集和Edge Network**

- [設定資料串流](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/datastreams/configure)
- [資料串流概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/datastreams/overview)
- [網頁SDK概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/web-sdk/home)
- [Edge Network伺服器API總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/edge-network-server-api/overview)
- [標籤總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/tags/home)
