---
title: offer decisioning概述
description: 跨客戶旅程提供個性化服務。
solution: Experience Platform, Journey Optimizer
source-git-commit: 7f566536c4ff5a6af321d60058ad67c13c28bf64
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 0%

---

# Journey Optimizer-Offer decisioning概述

要瞭解有關決策管理的詳細資訊，請參閱產品文檔 [這裡](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html)

Adobe決策管理是作為Adobe Journey Optimizer的一部分提供的服務。 此藍圖概述了應用程式的使用案例和技術功能，並深入介紹了構成Offer decisioning的各種體系結構元件和注意事項。

Journey Optimizer習慣於在適當的時間為您的客戶在所有接觸點上提供最佳服務和體驗。 offer decisioning通過集中的營銷優惠庫和決策引擎輕鬆實現個性化，決策引擎將規則和約束應用於Adobe Experience Platform建立的豐富的即時配置檔案，以幫助您在適當的時間向客戶發送合適的優惠。

「決策管理」功能由兩個主要元件組成：

* 集中式聘用庫是建立和管理構成聘用的不同元素並定義其規則和約束的介面。
* 服務決策引擎利用Adobe Experience Platform資料和即時客戶資料以及服務庫，以選擇提供服務的合適時間，客戶和渠道。

<img src="../assets/offers_overview.png" alt="offer decisioning" style="width:100%; border:1px solid #4a4a4a" />

決策管理可以通過兩種方式之一進行部署。

## 中心的決策管理

第一種是通過Adobe Experience Platform中心，該中心是一個中央資料中心體系結構。 在&quot;集線器&quot;方法中，服務的執行、個性化和交付時間超過500毫秒。 因此，中心架構最適合不需要亞秒延遲的客戶體驗，例如，包括為諸如呼叫中心或個人交互中的亭子或代理輔助體驗提供的服務決定。 插入電子郵件、SMS消息或推送通知等出站活動的優惠也由中心方法提供支援。 要瞭解有關集線器上的決策管理的詳細資訊，請參閱 [中心的決策管理](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/offer-decisioning/offers-hub.html?lang=en) 藍圖。

### 在集線器上進行決策管理的使用案例

* 在售貨亭和商店體驗上提供個性化服務。
* 通過座席輔助體驗（例如呼叫中心或銷售互動）提供個性化服務。
* 包括在電子郵件、SMS或其他出站交互中的服務。
* 跨渠道行程執行 — 通過Adobe Journey Optimizer提供跨Web、移動、電子郵件和其他交互渠道的一致性。

## 邊緣決策管理

第二種方法是通過「體驗邊緣網路」，它是一個分佈於全球各地、地理位置分佈的基礎架構，可提供快速的次秒和毫秒的體驗。 最終消費者體驗由最靠近消費者地理位置的邊緣基礎架構執行，以最小化延遲。 Edge上的Decision Management旨在提供即時消費者體驗，如Web或移動入站個性化請求。 要瞭解有關邊緣上的決策管理的詳細資訊，請參閱 [邊緣決策管理](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/offer-decisioning/offers-edge.html?lang=en) 藍圖。

### 邊緣決策管理的使用案例

* 通過Web或移動入站體驗實現線上個性化。
* 跨渠道行程執行 — 通過Adobe Journey Optimizer提供跨Web、移動、電子郵件和其他交互渠道的一致性。

## 相關文件

* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html)
* [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer.html)
* [Adobe Journey Optimizer決策管理](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html)
* [Adobe Journey Optimizer產品說明](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer.html)
* [AdobeOffer decisioning產品說明](https://helpx.adobe.com/legal/product-descriptions/offer-decisioning-app-service.html)