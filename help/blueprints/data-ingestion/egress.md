---
title: 資料存取和匯出Blueprint
description: 此Blueprint提供並概述可從Adobe Experience Platform和應用程式存取和匯出資料的所有方法。
product: adobe experience platform
solution: Experience Platform, Journey Optimizer, Real-time Customer Data Platform, Tags
source-git-commit: 67e66068bb8a2106dd8aa9784b5a39377225c045
workflow-type: tm+mt
source-wordcount: '1490'
ht-degree: 2%

---

# 資料存取和匯出Blueprint

資料存取和匯出Blueprint概述了所有可從Adobe Experience Platform和應用程式存取或匯出資料的方法。

Blueprint分為兩個類別，以從Experience Platform和應用程式存取資料。 首先，從Experience Platform和應用程式中獲取資料的方法；這可視為資料輸出的推送類型方法。 其次，從Experience Platform和應用程式獲取資料的方法；這可視為資料存取的提取類型方法。

資料存取方法

* [即時客戶設定檔存取API](#rtcp-profile-access-api)
* [資料存取API](#data-access-api)
* [查詢服務](#query-service)

資料匯出方法

* [用戶端標籤](#client-side-tags-extensions)
* [事件轉送](#event-forwarding)
* [Real-time Customer Data Platform目的地](#RTCDP-destinations)
* [Journey Optimizer自訂動作](#jo-custom-actions)

## 資料存取和匯出概觀架構

<img src="../experience-platform/assets/aep_data_flow.svg" alt="資料準備與擷取 Blueprint 的參考架構" style="width:90%; border:1px solid #4a4a4a" />

## 資料存取方法

### 即時客戶設定檔存取API {#rtcp-profile-access-api}

客戶可使用即時客戶個人檔案存取API，從即時客戶個人檔案存放區存取單一統一的個人檔案，包括所有個人檔案身分、受眾會籍、屬性和體驗事件。

請參閱 [即時客戶設定檔存取API](https://experienceleague.adobe.com/docs/experience-platform/profile/api/entities.html?lang=en) 檔案以取得其他資訊。

#### 使用案例

* 查找單個配置檔案以將上下文添加到座席客戶交互，例如通過聊天和呼叫中心進行的支援交互，或銷售點的銷售交互。
* 允許將內容新增至外部系統（例如網頁個人化系統或優惠方案決策系統）所做的個人化決策。

#### 考量事項

* 即時客戶個人檔案 [護欄](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en) 的上界。
* 專為一次單一設定檔查閱而設計。 不用於大量存取設定檔或下載整個設定檔母體，以用於分析或資料科學。
* 設定檔查詢回應時間會貼上至設定檔護欄。 低延遲需求 — 例如針對相同頁面個人化需求，應使用邊緣設定檔或客戶個人化目的地，以低延遲設定檔存取。 [檔案](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/custom-personalization.html?lang=en).

### 資料存取API {#data-access-api}

使用資料存取API，客戶可以直接存取儲存在Experience Platform資料湖中的原始資料集檔案。

* 有關使用資料存取API的其他詳細資訊，請參閱 [檔案](https://experienceleague.adobe.com/docs/experience-platform/data-access/home.html?lang=en).

#### 使用案例

* 從Experience Platform中提取原始資料和已處理的資料檔案，以便在企業環境中進行儲存和評估。

#### 考量事項

* 與串流資料輸出方法（例如使用標籤、事件轉送或RTCDP目的地）相比，以非同步方式批次存取資料時，資料的存取將原本延遲。
* 將資料檔案處理為Experience Platform時，會以批量檔案的集合形式儲存，並以鑲木格式壓縮和儲存。 因此，在將檔案存取和下載到不同環境時，必須以與整個資料集對應的批次和檔案系統地存取這些檔案，且資料上的任何操作都必須考慮以鑲木地板格式壓縮的檔案。

### 查詢服務 {#query-service}

使用experience platform Query Service客戶可以在Experience Platform內查詢資料集，並保留查詢結果。 SQL Client可用於查詢和保存SQL客戶端可支援的所需儲存目標中的查詢響應。 Query Service UI可用於將SQL結果儲存在Experience Platform中的目標資料集，或將結果保存到本地電腦。

* 有關連接到SQL客戶端以保存Experience Platform查詢服務的SQL結果的其他詳細資訊，請參見以下內容 [檔案](https://experienceleague.adobe.com/docs/experience-platform/query/clients/overview.html?lang=en).

#### 使用案例

* 從Experience Platform資料集查詢原始資料，並保留查詢結果。
* 查詢設定檔快照資料集，以擷取即時客戶設定檔的深入分析。 [文件](https://experienceleague.adobe.com/docs/experience-platform/dashboards/query.html?lang=en#profile-attribute-datasets).
* 將查詢結果儲存到單獨的資料集中，以便訪問或放入啟用配置檔案的資料集中，這些資料集稍後可通過RTCDP和其他訪問即時Experience Cloud配置檔案的應用程式進行解析。

#### 考量事項

* 與串流資料輸出方法（例如使用標籤、事件轉送或RTCDP目的地）相比，以批次非同步方式查詢資料時，資料的存取將原本延遲。
* 只能使用「查詢服務」查詢Experience Platform資料湖中可用的資料。 即時客戶設定檔存放區、身分圖表、Customer Journey Analytics無法透過查詢服務直接查詢。 只有將資料集匯出至Data Lake時，才能查詢這些資料集，如設定檔快照資料集的範例。
* 請注意，查詢結果數和查詢逾時的護欄會套用，如 [查詢服務護欄](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html?lang=en) 檔案。

## 資料匯出方法

### 用戶端標籤擴充功能 {#client-side-tags-extensions}

可使用Adobe的標籤解決方案部署擴充功能。 在部署擴充功能後，資料請求會直接部署在用戶端瀏覽器或應用程式上，而且可以叫用請求，將資料和請求傳送至所需目的地。

請參閱 [標籤概述](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=en) 檔案以取得其他資訊。

#### 使用案例

* 使用標籤直接從用戶端環境收集原始串流資訊。

#### 考量事項

* 無法直接存取任何伺服器端資訊，例如Experience Platform即時客戶個人檔案和受眾會籍。
* 將其他資料收集標籤新增至頁面可能會增加頁面載入時間。
* 能夠設定規則，只在符合特定條件時要求資料。
* 直接從客戶端收集資料，限制在收集資料之前可以執行的轉換類型和擴充。

### 事件轉送 {#event-forwarding}

資料收集請求會直接收集至Adobe的邊緣網路。 從邊緣網路請求到外部RESTful端點可以配置為將這些請求轉發到外部目標。

請參閱下列內容 [事件轉送](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=en) 檔案以取得其他資訊。

#### 使用卡塞亞

* 使用Adobe的伺服器端事件轉送，直接從用戶端環境收集原始串流資訊至企業端點。

#### 考量事項

* 若要使用事件轉送，必須使用WebSDK或MobileSDK將資料傳送至邊緣網路。
* 事件轉送方法會因為頁面上新增其他標籤，而縮短頁面載入時間並減輕重量。
* 目前不支援從邊緣設定檔或其他資料來源進行擴充。
* 支援有限的資料過濾和簡單的映射轉換。

### Real-time Customer Data Platform目的地 {#RTCDP-destinations}

可將設定檔屬性資料和對象成員資格資料啟用至企業和廣告目的地。 這表示所擷取的資料必須擷取至Experience Platform即時客戶設定檔中。

請參閱 [Real-time Customer Data Platform目的地](https://experienceleague.adobe.com/docs/experience-platform/destinations/home.html?lang=en) 檔案以取得其他資訊。

#### 使用案例

* 啟用設定檔屬性資訊，包括對企業間資料存放區、分析工具、電子郵件系統或支援系統的對象成員資格。
* 為外部廣告供應商啟用設定檔對象成員資格，以定位並個人化設定檔的內容。

#### 考量事項

* 可啟用設定檔屬性和對象成員資格。 目前無法在RTCDP目的地中啟動原始體驗事件。
* 視區段評估的性質和目的地接受的擷取通訊協定的性質而定，會在串流或批次中進行啟用。

### Journey Optimizer自訂動作 {#jo-custom-actions}

使用Journey Optimizer的客戶可從歷程畫布叫用自訂動作，以傳送裝載或訊息至已設定的外部API端點。 動作可設為來自任何提供者的任何服務，這些服務可透過具有JSON格式裝載的REST API進行呼叫。 此裝載可包含歷程中設定的事件資訊、設定檔屬性和先前的事件資料、轉換和擴充。

請參閱 [Journey Optimizer自訂動作](https://experienceleague.adobe.com/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/using-custom-actions.html?lang=en) 檔案以取得其他資訊。

#### 使用案例

* 來自Experience Platform和Journey Optimizer的啟動事件，其中包含來自即時客戶設定檔的其他資訊。
* 當客戶到達歷程的特定點時，通知外部系統。

#### 考量事項

* 吞吐量的護欄，由 [Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/guardrails.html?lang=en) 以及 [即時客戶個人檔案](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en) 的上界。
* 您可以逐一對歷程中的每個事件或設定檔，以串流方式執行自訂動作。 無法跨客戶歷程執行大量作業或以檔案或匯總請求形式大量資料輸出。
* 串流存取即時客戶設定檔屬性和體驗事件，可包含在啟用裝載中。
* 在將事件傳送至外部目的地之前，可以篩選事件資料並套用簡單的對應轉換。










