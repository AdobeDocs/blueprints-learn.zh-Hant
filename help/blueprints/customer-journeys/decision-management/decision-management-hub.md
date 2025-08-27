---
title: 中心上的決策管理藍圖
description: 在各通道（包括資訊站、代理程式協助的體驗，以及電子郵件和其他傳出傳遞）為消費者提供個人化產品建議。
solution: Experience Platform, Journey Optimizer
exl-id: 5a386e18-bbac-4216-a35f-0a5016785e4a
source-git-commit: 65eaffe8af093cc410b556778ae327ed16202f10
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 76%

---

# 中心Blueprint上的決定管理

若要深入了解決策管理，請參閱[此處](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioning/get-started-decision/starting-offer-decisioning.html?lang=zh-Hant)的產品文件和[此處](decision-management-overview.md)的決策管理概觀

Adobe Decision Management 是 Adobe Journey Optimizer 中提供的服務。此藍圖概述了應用程式的使用案例和技術功能，並深入介紹構成「決策管理」的各種體系結構元件和注意事項。

Journey Optimizer 可用來在適當的時間，跨所有接觸點為客戶提供最佳方案和體驗。「決策管理」透過集中的行銷產品建議資料庫和決策引擎，將規則和限制套用至 Adobe Experience Platform 建立的豐富、即時個人檔案中，協助您在正確的時間為客戶傳送正確的產品建議，讓個人化更加輕鬆。

決策管理可以透過以下兩種方式之一進行部署。第一個是透過 Adobe Experience Platform 中心，這是中央資料中心基礎架構。在「中心」方法中，會執行並個人化產品建議，並在超過 500 毫秒的延遲內傳送。因此，中心基礎架構最適合不需要次秒延遲的客戶體驗，例如，為資訊站或代理輔助體驗（例如在呼叫中心或個人互動中）提供的產品建議決策。插入電子郵件和傳出行銷活動的產品建議，也由中心方法提供支援。

第二種方式是透過Experience [！DNL [!DNL Edge Network]]，這是一種分散於全球各地的基礎架構，可提供快速次秒和毫秒的體驗。 由最接近消費者地理位置的邊緣基礎架構執行的最終消費者體驗，以將延遲降至最低。邊緣決策管理可提供即時消費者體驗，例如網路或行動傳入個人化請求。

此藍圖將涵蓋中心上「決策管理」的詳細資訊。

若要進一步了解 Edge 上的「決策管理」，請參閱 [Edge 上的「決策管理」](decision-management-edge.md)藍圖。

## 中心上決策管理的使用案例

* 個人資料內容延遲不嚴格的串流使用案例 — 15分鐘或更長延遲。
* 資訊站和商店體驗上的個人化產品建議。
* 透過代理輔助體驗（如呼叫中心或銷售互動）提供個性化產品建議。
* 包含在電子郵件、簡訊、行動推播通知或其他傳出互動中的產品建議。
* 向外部 ESP 和郵件傳送系統提供產品建議以進行傳送。
* 跨通道歷程執行 — 透過 Adobe Journey Optimizer，提供網頁、行動裝置、電子郵件和其他互動通道的一致性。

>[!IMPORTANT]
>
>適用於需要存取設定檔以取得其他資訊和內容的優惠和歷程使用案例。 請務必考量在集線器上將資料擷取至設定檔的相關延遲，以確保可在決策時使用這些資料。 若情境是串流或內嵌至設定檔，且優惠或歷程必須在優惠決定後的數秒或數分鐘內提供該內容，則這些情境最好透過Edge上的決定管理提供。

## 架構

<img src="images/offers_hub.svg" alt="邊緣上 Decision Management 藍圖參考架構" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## 護欄

* 有關 Journey Optimizer 護欄，請參閱下列 [Journey Optimizer 護欄](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/limitations.html?lang=zh-Hant)。
* 有關決策管理護欄，請參閱下面的[ Decision Management 產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/offer-decisioning-app-service.html)。

[護欄和端對端延遲指引](/help/blueprints/experience-platform/guardrails.md)

## 實作模式

* 透過與 [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioning/get-started-decision/offers-e2e.html?lang=zh-Hant) 直接整合，在電子郵件、簡訊和傳出通道中實作。
* 針對以伺服器 API 為基礎的決策管理實作，請運用 [決策 API](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/api-reference/offer-delivery/decisioning-vs-edge-apis.html?lang=zh-Hant)。
* 若要實作批次決策以大量傳送產品建議給訊息傳送應用程式，請使用[批次決策 API](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/api-reference/offer-delivery/batch-decisioning-api.html?lang=zh-Hant)。
* 針對以Edge為基礎的即時體驗，請使用Web/Mobile SDK或Edge Decisioning API，如Edge Blueprint上的[決定管理](decision-management-edge.md)中所述

## 相關文件

* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hant)
* [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer.html?lang=zh-Hant)
* [Adobe Journey Optimizer 決策管理](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioning/get-started-decision/starting-offer-decisioning.html?lang=zh-Hant)
* [Adobe Journey Optimizer 產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/adobe-journey-optimizer.html)
* [Adobe Decision Management 產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/offer-decisioning-app-service.html)
