---
title: 決策管理概觀
description: 在客戶歷程中提供個人化優惠方案。
solution: Experience Platform, Journey Optimizer
exl-id: 1bc9335c-5321-4d0c-939e-4f402e2e8f51
source-git-commit: b3d4e89c7e4170ffee2cc1776ffa26d2e0ce79e6
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---

# Journey Optimizer — 決策管理概觀

若要深入了解決策管理，請參閱產品檔案 [此處](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html)

Adobe決策管理是Adobe Journey Optimizer中提供的服務。 此藍圖概述了應用程式的使用案例和技術功能，並深入介紹構成「決策管理」的各種體系結構元件和注意事項。

Journey Optimizer可用來在適當的時間，跨所有接觸點為客戶提供最佳選件和體驗。 Decision Management透過集中的行銷選件資料庫和決策引擎，將規則和限制套用至Adobe Experience Platform建立的豐富即時設定檔，協助您在正確的時間為客戶傳送正確的優惠方案，讓個人化更加輕鬆。

「決策管理」功能包含兩個主要元件：

* 集中式優惠方案程式庫，是您建立和管理組成優惠方案的不同元素，以及定義其規則和限制的介面。
* 優惠方案決策引擎會運用Adobe Experience Platform資料和即時客戶設定檔，以及優惠方案庫，以選擇將要提供優惠方案的正確時間、客戶和管道。

<img src="../assets/offers_overview.png" alt="決策管理" style="width:100%; border:1px solid #4a4a4a" />

決策管理可以通過兩種方式之一部署在邊緣或集線器上。 每種方法都有一組特定的介面和協定，用於運行服務，如下面分別參考的藍圖中所述。 決策管理檔案中也提供其他詳細資訊 [此處](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/api-reference/offer-delivery-api/decisioning-vs-edge-apis.html).

## 中心的決策管理

第一個是透過Adobe Experience Platform中樞，這是中央資料中心架構。 在「中樞」方法中，會執行、個人化優惠，並在超過500毫秒的延遲內提供。 因此，中心架構最適合不需要次秒延遲的客戶體驗，例如，為資訊站或代理輔助體驗（例如在呼叫中心或個人互動中）提供的選件決策。 插入電子郵件、簡訊或推播通知和其他傳出行銷活動的優惠方案，也採用中樞方法提供技術支援。 若要進一步了解中樞上的決策管理，請參閱 [中心的決策管理](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-hub.html?lang=en) 藍圖。

* 優惠方案資格可針對完整的即時客戶設定檔（包括所有屬性和體驗事件）運作

### 中心上決策管理的使用案例

* 資訊站和商店體驗上的個人化優惠方案。
* 通過座席輔助體驗（如呼叫中心或銷售互動）提供個性化優惠。
* 電子郵件、簡訊或其他對外互動中包含的優惠方案。
* 跨管道歷程執行 — 透過Adobe Journey Optimizer，提供網頁、行動裝置、電子郵件和其他互動管道的一致性。

### 中心技術考量的決策管理

* 每秒請求數= 2000。
* 響應延遲&lt; 500毫秒。
* 存取完整即時客戶設定檔，包括受眾會籍、屬性和體驗事件。

## 邊緣決策管理

第二種方法是透過Experience Edge Network，這是分散於全球各地的基礎架構，可提供亞秒數及毫秒的快速體驗。 由最接近消費者地理位置的邊緣基礎架構執行的最終消費者體驗，以將延遲降至最低。 Edge上的決策管理可提供即時消費者體驗，例如網路或行動傳入個人化請求。 若要進一步了解Edge上的決策管理，請參閱 [邊緣決策管理](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-edge.html?lang=en) 藍圖。

### 邊緣決策管理的使用案例

* 透過網頁或行動傳入體驗進行線上個人化。
* 跨管道歷程執行 — 透過Adobe Journey Optimizer，提供網頁、行動裝置、電子郵件和其他互動管道的一致性。

### 邊緣技術考量的決策管理

* 每秒請求數= 5000。
* 響應延遲&lt; 250毫秒。
* 存取邊緣即時設定檔。 設定檔中將僅提供邊緣預計對象和設定檔屬性。
* 如果首次體驗中需要個人化，則中心會是理想的選擇，因為有完整的設定檔可用。 邊緣設定檔必須從中樞同步，才能第一次出現邊緣體驗。 因此，來自Edge的第一個體驗將不包含先前上傳至中樞的設定檔資料。

## 相關文件

* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html)
* [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer.html)
* [Adobe Journey Optimizer決策管理](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html)
* [Adobe Journey Optimizer產品說明](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer.html)
* [Adobe決策管理產品說明](https://helpx.adobe.com/legal/product-descriptions/offer-decisioning-app-service.html)
