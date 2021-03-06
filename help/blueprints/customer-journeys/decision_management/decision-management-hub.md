---
title: 中心的決策管理
description: 跨渠道向消費者提供個性化服務，包括亭子、代理協助體驗，以及電子郵件和其他出站遞送。
solution: Experience Platform, Journey Optimizer
exl-id: 5a386e18-bbac-4216-a35f-0a5016785e4a
source-git-commit: 5b2f7531cc05178127fb08d3fdafcbce70192ecd
workflow-type: tm+mt
source-wordcount: '901'
ht-degree: 17%

---

# Journey Optimizer — 中心決策管理

要瞭解有關決策管理的詳細資訊，請參閱產品文檔 [這裡](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html) 和決策管理概述 [這裡](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/offer-decisioning/decision-management-overview.html)

Adobe決策管理是作為Adobe Journey Optimizer的一部分提供的服務。 此藍圖概述了應用程式的使用案例和技術功能，並深入介紹了構成決策管理的各種體系結構元件和考慮事項。

Journey Optimizer習慣於在適當的時間為您的客戶在所有接觸點上提供最佳服務和體驗。 決策管理通過集中的營銷優惠和決策引擎來輕鬆實現個性化，該引擎將規則和約束應用於Adobe Experience Platform建立的豐富的即時概要檔案，以幫助您在適當的時間向客戶發送適當的優惠。

決策管理可以通過兩種方式之一進行部署。 第一種是通過Adobe Experience Platform中心，該中心是一個中央資料中心體系結構。 在&quot;集線器&quot;方法中，服務的執行、個性化和交付時間超過500毫秒。 因此，中心架構最適合不需要亞秒延遲的客戶體驗，例如，包括為諸如呼叫中心或個人交互中的亭子或代理輔助體驗提供的服務決定。 插入電子郵件和出站活動的優惠也由中心方法提供支援。

第二種方法是通過「體驗邊緣網路」，它是一個分佈於全球各地、地理位置分佈的基礎架構，可提供快速的次秒和毫秒的體驗。 最終消費者體驗由最靠近消費者地理位置的邊緣基礎架構執行，以最小化延遲。 Edge上的Decision Management旨在提供即時消費者體驗，如Web或移動入站個性化請求。

此藍圖將介紹中心上的決策管理的具體內容。

要瞭解有關邊緣上的決策管理的詳細資訊，請參閱 [邊緣決策管理](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/offer-decisioning/decision-management-edge.html) 藍圖。

## 在集線器上進行決策管理的使用案例

* 在售貨亭和商店體驗上提供個性化服務。
* 通過座席輔助體驗（例如呼叫中心或銷售互動）提供個性化服務。
* 包括在電子郵件、SMS、移動推送通知或其他出站交互中的服務。
* 向外部ESP和消息傳遞系統提供服務，以便交付。
* 跨渠道行程執行 — 通過Adobe Journey Optimizer提供跨Web、移動、電子郵件和其他交互渠道的一致性。

<br>

## 架構

<img src="../assets/offers_hub.svg" alt="邊緣藍圖上的參考體系結構決策管理" style="width:100%; border:1px solid #4a4a4a" />

<br>

## 先決條件

Adobe Experience Platform

* 必須先在系統中配置架構和資料集，然後才能配置Journey Optimizer資料源
* 對於基於經驗事件類的架構，當希望觸發的事件不是基於規則的事件時，添加「業務流程事件ID」欄位組
* 對於基於單個配置檔案類的架構，添加「配置檔案test詳細資訊」欄位組，以便能夠載入test配置檔案以與Journey Optimizer一起使用

<br>

## 護欄

* 有關Journey Optimizer護欄，請參閱以下 [Journey Optimizer瓜德賴爾](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/limitations.html)。
* 有關決策管理護欄，請參閱以下內容 [決策管理產品說明](https://helpx.adobe.com/legal/product-descriptions/offer-decisioning-app-service.html)。
* 每秒請求數= 2000。
* 響應延遲&lt; 500毫秒。
* 訪問全面即時客戶配置檔案，包括訪問者成員身份、屬性和體驗事件。


### 資料擷取護欄

<img src="../assets/aep-data-ingestion-details-latency.svg" alt="參考建築Journey Optimizer藍圖" style="width:80%; border:1px solid #4a4a4a" />

<br>

### 激活護欄

<img src="../assets/ajo-activation-details-latency.svg" alt="參考建築Journey Optimizer藍圖" style="width:80%; border:1px solid #4a4a4a" />

<br>

## 實施模式

* 通過與直接整合在電子郵件、簡訊和出站通道中實現 [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/offers-e2e.html)。
* 對於基於伺服器API的決策管理實施， [決策API](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/api-reference/offer-delivery/decisioning-vs-edge-apis.html)。
* 對於實施基於批的決策以批量將優惠遞送到消息遞送應用程式，使用 [批處理決策API](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/api-reference/offer-delivery/batch-decisioning-api.html)。
* 對於基於邊緣的即時體驗，請使用Web/Mobile SDK或邊緣決策API，如 [邊緣藍圖上的決策管理](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/offer-decisioning/decision-management-edge.html)。
<br>

## 實施步驟

### Adobe Experience Platform

#### 方案 / 資料集

1. 在 Experience Platform 中基於客戶提供的資料[設定個別個人資料、體驗事件及多實體方案。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm)
1. 在 Experience Platform 中為要擷取的資料[建立資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=zh-Hant)。
1. [在 Experience Platform 中新增使用標籤](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=zh-Hant)至資料集以便於治理。
1. [建立政策](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=zh-Hant)以在目標上執行治理。

#### 個人資料 / 身份

1. [建立任何客戶特定的命名空間。](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hant)
1. [新增身份至方案](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html)。
1. [為個人資料啟用方案和資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=zh-Hant)。
1. 為[!UICONTROL 即時客戶個人資料]的不同檢視[設定合併政策](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=zh-Hant) (可選)。
1. 為行程使用建立段。

#### 來源 / 目標

1. 使用串流 API 和來源連接器[將資料擷取到 Experience Platform。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=zh-Hant)

## 相關文件

* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html)
* [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer.html)
* [Adobe Journey Optimizer決策管理](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html)
* [Adobe Journey Optimizer產品說明](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer.html)
* [Adobe決策管理產品說明](https://helpx.adobe.com/legal/product-descriptions/offer-decisioning-app-service.html)
