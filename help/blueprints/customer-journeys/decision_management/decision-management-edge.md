---
title: 邊緣上 Decision Management 藍圖
description: 跨通道（包括即時網路和行動體驗）為消費者提供個人化優惠方案。
solution: Experience Platform, Journey Optimizer
exl-id: 31e5f624-5578-49e1-ab92-5cabd596a632
source-git-commit: 60a7785ea0ec4ee83fd9a1e843f0b84fc4cb1150
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 80%

---

# Journey Optimizer - Edge Blueprint上的[!DNL Decision Management]

[!DNL Decision Management]是作為[!DNL Journey Optimizer]的一部分提供的服務。 此藍圖概述了應用程式的使用案例和技術功能，並深入介紹構成「決策管理」的各種體系結構元件和注意事項。

>[!MORELIKETHIS]
>
>若要深入瞭解[!DNL Decision Management]，請參閱[藍圖概觀](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-overview.html?lang=zh-Hant)或造訪[產品檔案](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioning/get-started-decision/starting-offer-decisioning.html?lang=zh-Hant)。

[!DNL Decision Management]有兩種部署方式。 第一個是透過[!DNL Experience Platform]中心，這是單一資料中心架構。 在「中心」方法中，會執行和個人化優惠活動，並在第二次延遲時傳送。因此，中心架構最適合不需要次秒延遲的客戶體驗，例如，為資訊站或代理輔助體驗（例如在呼叫中心或人員互動中）提供的有貨決策。

第二種方式是透過Experience Platform[!DNL Edge Network]，這是全球分散的地理位置基礎架構，可提供快速次秒和毫秒的體驗。 Edge基礎結構所執行的最終消費者體驗，其位置最接近消費者地理位置，可將延遲降至最低。 Edge上的[!DNL Decision Management]旨在提供即時消費者體驗。 這些包括網頁或行動傳入個人化請求之類的體驗。

此藍圖將涵蓋邊緣上 Decision Management 的詳細資訊。

若要進一步了解中心上的決策管理，請參閱[中心的決策管理](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-hub.html?lang=zh-Hant)藍圖。

## 邊緣決策管理的使用案例

* 個人資料內容延遲嚴格低於15分鐘延遲且決策管理執行為次秒的串流使用案例。
* 透過網頁或行動傳入體驗進行線上個人化。
* 跨通道歷程執行 — 透過 Adobe Journey Optimizer，提供網頁、行動裝置、電子郵件和其他互動通道的一致性。

<br>

## 架構

<img src="../assets/offers_edge.svg" alt="邊緣上 Decision Management 藍圖參考架構" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## 整合模式

| 整合 | 說明 |
| :-- | :--- |
| [Adobe Target 與 Decision Management 整合](https://experienceleague.adobe.com/docs/target/using/integrate/ajo/offer-decision.html?lang=zh-Hant) | Decision Management 可與 Adobe Target 整合，以便以 Target 體驗的形式測試和提供優惠方案。 |

## 先決條件

Adobe Experience Platform

* 必須先在系統中設定方案和資料集，才能設定 Journey Optimizer 資料來源
* 如果您想要觸發非規則型的事件，則針對體驗事件類別型方案，新增「Orchestration eventID」欄位群組
* 針對個別個人資料類別型方案，新增「個人資料測試詳細資料」欄位群組，以便載入測試個人資料以與 Journey Optimizer 搭配使用

<br>

## 護欄

* 有關 Journey Optimizer 護欄，請參閱下列 [Journey Optimizer 護欄](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/limitations.html?lang=zh-Hant)。

* 有關決策管理護欄，請參閱下面的[ Decision Management 產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/offer-decisioning-app-service.html)。

[護欄與端對端延遲指引](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html)


## 實作模式

* 將 Web 或 Mobile SDK 用於在網站和行動應用程式上的部署，以在部署 SDK 後實作 Decision Management。
   * [Web/Mobile SDK 藍圖](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/websdk.html?lang=zh-Hant)
   * [Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/offer-decisioning/offer-decisioning-overview.html?lang=zh-Hant)
   * [Mobile SDK](https://aep-sdks.gitbook.io/docs/)

或

* 若是以 API 伺服器對伺服器為基礎的實作，請使 Edge Network Service API，直接進行伺服器對伺服器的 Decision Management 實作。
   * [Edge Network Server API](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioning/api-reference/offer-delivery-api/decisioning-api.html?lang=zh-Hant)

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
