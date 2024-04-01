---
title: 中心上的決策管理藍圖
description: 在各通道（包括資訊站、代理程式協助的體驗，以及電子郵件和其他傳出傳遞）為消費者提供個人化優惠方案。
solution: Experience Platform, Journey Optimizer
exl-id: 5a386e18-bbac-4216-a35f-0a5016785e4a
source-git-commit: 60a7785ea0ec4ee83fd9a1e843f0b84fc4cb1150
workflow-type: tm+mt
source-wordcount: '831'
ht-degree: 84%

---

# 中心上的決策管理藍圖

若要深入了解決策管理，請參閱[此處](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioning/get-started-decision/starting-offer-decisioning.html?lang=zh-Hant)的產品文件和[此處](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-overview.html?lang=zh-Hant)的決策管理概述

Adobe Decision Management 是 Adobe Journey Optimizer 中提供的服務。此藍圖概述了應用程式的使用案例和技術功能，並深入介紹構成「決策管理」的各種體系結構元件和注意事項。

Journey Optimizer 可用來在適當的時間，跨所有接觸點為客戶提供最佳方案和體驗。「決策管理」透過集中的行銷選件資料庫和決策引擎，將規則和限制套用至 Adobe Experience Platform 建立的豐富、即時個人檔案中，協助您在正確的時間為客戶傳送正確的優惠方案，讓個人化更加輕鬆。

決策管理可以透過以下兩種方式之一進行部署。第一個是透過 Adobe Experience Platform 中心，這是中央資料中心基礎架構。在「中心」方法中，會執行並個人化優惠方案，並在超過 500 毫秒的延遲內傳送。因此，中心基礎架構最適合不需要次秒延遲的客戶體驗，例如，為資訊站或代理輔助體驗（例如在呼叫中心或個人互動中）提供的優惠方案決策。插入電子郵件和傳出行銷活動的優惠方案，也由中心方法提供支援。

第二種方式是透過Experience [！DNL [!DNL Edge Network]]，此基礎架構是分散於全球各地的基礎建設，可提供快速且亞秒和毫秒的體驗。 由最接近消費者地理位置的邊緣基礎架構執行的最終消費者體驗，以將延遲降至最低。邊緣決策管理可提供即時消費者體驗，例如網路或行動傳入個人化請求。

此藍圖將涵蓋中心上「決策管理」的詳細資訊。

若要進一步了解 Edge 上的「決策管理」，請參閱 [Edge 上的「決策管理」](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-edge.html?lang=zh-Hant)藍圖。

## 中心上決策管理的使用案例

* 個人資料內容延遲不嚴格的串流使用案例 — 15分鐘或更長延遲。
* 資訊站和商店體驗上的個人化優惠方案。
* 透過代理輔助體驗（如呼叫中心或銷售互動）提供個性化優惠方案。
* 包含在電子郵件、簡訊、行動推播通知或其他傳出互動中的優惠方案。
* 向外部 ESP 和郵件傳送系統提供優惠方案以進行傳送。
* 跨通道歷程執行 — 透過 Adobe Journey Optimizer，提供網頁、行動裝置、電子郵件和其他互動通道的一致性。

>[!IMPORTANT]
>
>適用於需要存取設定檔以取得其他資訊和內容的優惠和歷程使用案例。 請務必考量在集線器上將資料擷取至設定檔的相關延遲，以確保可在決策時使用這些資料。 若情境是串流或內嵌至設定檔，且優惠或歷程必須在優惠決定後的數秒或數分鐘內提供該情境，則邊緣上的決定管理可提供最佳情境。

<br>

## 架構

<img src="../assets/offers_hub.svg" alt="邊緣上 Decision Management 藍圖參考架構" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## 先決條件

Adobe Experience Platform

* 必須先在系統中設定方案和資料集，才能設定 Journey Optimizer 資料來源
* 如果您想要觸發非規則型的事件，則針對體驗事件類別型方案，新增「Orchestration eventID」欄位群組
* 針對個別個人資料類別型方案，新增「個人資料測試詳細資料」欄位群組，以便載入測試個人資料以與 Journey Optimizer 搭配使用

<br>

## 護欄

* 有關 Journey Optimizer 護欄，請參閱下列 [Journey Optimizer 護欄](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/limitations.html?lang=zh-Hant)。
* 有關決策管理護欄，請參閱下面的[ Decision Management 產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/offer-decisioning-app-service.html)。

[護欄和端對端延遲指引](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html)

## 實作模式

* 透過與 [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioning/get-started-decision/offers-e2e.html?lang=zh-Hant) 直接整合，在電子郵件、簡訊和傳出通道中實作。
* 針對以伺服器 API 為基礎的決策管理實作，請運用 [決策 API](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/api-reference/offer-delivery/decisioning-vs-edge-apis.html?lang=zh-Hant)。
* 若要實作批次決策以大量傳送優惠方案給訊息傳送應用程式，請使用[批次決策 API](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/api-reference/offer-delivery/batch-decisioning-api.html?lang=zh-Hant)。
* 對於邊緣型即時體驗，請依照[邊緣上的決策管理藍圖](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-edge.html?lang=zh-Hant)中所述使用 Web/Mobile SDK 或 Edge Decisioning API。
<br>

## 實施步驟

### Adobe Experience Platform

#### 方案/資料集

1. 在 Experience Platform 中基於客戶提供的資料[設定個別個人資料、體驗事件及多實體方案。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm&amp;lang=zh-Hant)
1. 在 Experience Platform 中為要擷取的資料[建立資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=zh-Hant)。
1. 在 Experience Platform 中[新增資料使用標籤](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=zh-Hant)至資料集以便於治理。
1. [建立政策](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=zh-Hant)以在目標上執行治理。

#### 個人資料/身份

1. [建立任何客戶特定的命名空間。](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hant)
1. [新增身份至方案](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hant)。
1. [為個人資料啟用方案和資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=zh-Hant)。
1. 為[!UICONTROL 即時客戶個人資料]的不同檢視[設定合併政策](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=zh-Hant) (可選)。
1. 建立 Journey 使用的區段。

#### 來源/目標

1. 使用串流 API 和來源連接器[將資料擷取到 Experience Platform。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=zh-Hant)

## 相關文件

* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hant)
* [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer.html?lang=zh-Hant)
* [Adobe Journey Optimizer 決策管理](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioning/get-started-decision/starting-offer-decisioning.html?lang=zh-Hant)
* [Adobe Journey Optimizer 產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/adobe-journey-optimizer.html)
* [Adobe Decision Management 產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/offer-decisioning-app-service.html)
