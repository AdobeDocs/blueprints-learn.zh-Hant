---
title: 邊緣上 Decision Management 藍圖
description: 跨通道（包括即時網路和行動體驗）為消費者提供個人化優惠方案。
solution: Experience Platform, Journey Optimizer
exl-id: 31e5f624-5578-49e1-ab92-5cabd596a632
source-git-commit: f6c4a0f39acdc177ac23c4314d2f50f793cbf270
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 68%

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

## 架構

<img src="../assets/offers_edge.svg" alt="邊緣上 Decision Management 藍圖參考架構" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## 整合模式

| 整合 | 說明 |
| :-- | :--- |
| [Adobe Target 與 Decision Management 整合](https://experienceleague.adobe.com/docs/target/using/integrate/ajo/offer-decision.html?lang=zh-Hant) | Decision Management 可與 Adobe Target 整合，以便以 Target 體驗的形式測試和提供優惠方案。 |

## 護欄

* 有關 Journey Optimizer 護欄，請參閱下列 [Journey Optimizer 護欄](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/limitations.html?lang=zh-Hant)。

* 有關決策管理護欄，請參閱下面的[ Decision Management 產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/offer-decisioning-app-service.html)。

[護欄與端對端延遲指引](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html?lang=zh-Hant)

## 相關文件

* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hant)
* [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer.html?lang=zh-Hant)
* [Adobe Journey Optimizer 決策管理](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioning/get-started-decision/starting-offer-decisioning.html?lang=zh-Hant)
* [Adobe Journey Optimizer 產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/adobe-journey-optimizer.html)
* [Adobe Decision Management 產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/offer-decisioning-app-service.html)
