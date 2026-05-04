---
title: 決策管理藍圖
description: 在客戶歷程中提供個人化產品建議。
solution: Experience Platform, Journey Optimizer
exl-id: 1bc9335c-5321-4d0c-939e-4f402e2e8f51
TQID: https://experienceleague.adobe.com/FWKq0QzEzCXp8TrfECmhY4E3ocA4zZkTGyHrrKQCOBw
product_v2:
  - id: cb954087-f4fc-4456-afb9-e939cabcdc79
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: c132d929-fa62-4271-803e-b823be07b914
  - id: d998adac-2f81-400b-a669-d07bb196e4eb
  - id: daec7ead-f475-492a-a3b3-02ae08565d6f
  - id: df64005d-8f9a-422e-ba4d-c6f6dc3454b4
  - id: fe338112-e2ce-4876-8989-fc4d497613f1
subfeature_v2:
  - id: e5ae22e3-a3b0-46ed-804f-9abf1bbe3e74
  - id: fa683eda-48de-4558-af32-2673edcd44fe
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
  - id: d00e9f03-e50b-4162-b143-0c0817c937c2
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
  - id: fd2e3797-f2ea-4b36-a9af-52acf5e90513
source-git-commit: a99add31cc9f485db119ca00426798545e6a7316
workflow-type: tm+mt
source-wordcount: 731
ht-degree: 76%

---

# Journey Optimizer — 決定管理藍圖

請參閱下列[決定管理](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioning/get-started-decision/starting-offer-decisioning.html?lang=zh-Hant)檔案

有關與決定管理相關的護欄，請參閱以下檔案。 [決定管理護欄](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails#decision-management.html)

Adobe Decision Management 是 Adobe Journey Optimizer 中提供的服務。 此藍圖概述了應用程式的使用案例和技術功能，並深入介紹構成「決策管理」的各種體系結構元件和注意事項。

Journey Optimizer 可用來在適當的時間，跨所有接觸點為客戶提供最佳方案和體驗。 決定管理透過集中行銷優惠資料庫和決定引擎（將規則和限制套用至Adobe Experience Platform建立的即時設定檔），讓個人化變得容易。 這可讓您在適當的時間輕鬆傳送適當的優惠。

「決策管理」功能包含兩個主要元件：

* 集中式產品建議庫，是您建立和管理組成產品建議的不同元素，以及定義其規則和限制的介面。
* 產品建議決策引擎，會運用 Adobe Experience Platform 資料和即時客戶個人資料，以及產品建議庫，以選擇將要提供產品建議的恰當時間、客戶和通道。

<img src="images/offers_overview.png" alt="決策管理" style="width:100%; border:1px solid #4a4a4a" />

「決策管理」可以透過兩種方式之一部署在邊緣或中心上。 每種方法都有一組特定的介面和協定，用於運行服務，如下面參考的各自藍圖中所述。 其他詳細資訊也可包含在[「決策管理」文件](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/api-reference/offer-delivery-api/decisioning-vs-edge-apis.html?lang=zh-Hant)中。

## 中心的決策管理

第一個是透過 Adobe Experience Platform 中心，這是中央資料中心基礎架構。 中樞架構最適合不要求低延遲和高輸送量，但需要更全面檢視客戶設定檔的客戶體驗，範例包括針對資訊站或代理程式協助體驗（例如客服中心或個人互動）提供的優惠決定。 插入電子郵件、簡訊或推播通知以及其他傳出行銷活動的產品建議，也採用中心方法提供技術支援。 若要進一步了解中心上的決策管理，請參閱[中心的決策管理](decision-management-hub.md)藍圖。

* 產品建議資格可針對完整的即時客戶個人資料（包括所有屬性和體驗事件）運作

### 中心上決策管理的使用案例

* 資訊站和商店體驗上的個人化產品建議。
* 透過代理輔助體驗（如呼叫中心或銷售互動）提供個性化產品建議。
* 電子郵件、簡訊或其他傳出互動中包含的產品建議。
* 跨通道歷程執行 — 透過 Adobe Journey Optimizer，提供網頁、行動裝置、電子郵件和其他互動通道的一致性。

### 中心決策管理的技術考量

* 存取完整的即時客戶個人資料,包括對象資格、屬性和體驗事件。

## 邊緣決策管理

第二種方式是透過Experience [!DNL Edge Network]，這是一種分散於全球各地的基礎架構，可提供快速次秒和毫秒的體驗。 由最接近消費者地理位置的邊緣基礎架構執行的最終消費者體驗，以將延遲降至最低。 邊緣決策管理可提供即時消費者體驗，例如網路或行動傳入個人化請求。 若要進一步了解邊緣上的「決策管理」，請參閱邊緣[上的「決策管理」](decision-management-edge.md)藍圖。

### 邊緣決策管理的使用案例

* 透過網頁或行動傳入體驗進行線上個人化。
* 跨通道歷程執行 — 透過 Adobe Journey Optimizer，提供網頁、行動裝置、電子郵件和其他互動通道的一致性。

### 邊緣決策管理的技術考量

* 存取邊緣即時個人資料。 個人資料中將僅提供邊緣預計對象和個人資料屬性。

## 相關文件

* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hant)
* [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer.html?lang=zh-Hant)
* [Adobe Journey Optimizer 決策管理](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioning/get-started-decision/starting-offer-decisioning.html?lang=zh-Hant)
* [Adobe Journey Optimizer產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/adobe-journey-optimizer.html)
* [Adobe決定管理產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/offer-decisioning-app-service.html)
