---
title: offer decisioning
description: 通過包括即時Web和移動體驗在內的渠道向消費者提供個性化服務。
solution: Experience Platform, Journey Optimizer
exl-id: 31e5f624-5578-49e1-ab92-5cabd596a632
source-git-commit: bedfce6f9ded6c168656e8c37c59f85f250481a1
workflow-type: tm+mt
source-wordcount: '757'
ht-degree: 22%

---

# Journey Optimizer — 邊緣的Offer decisioning

Adobe決策管理是作為Adobe Journey Optimizer的一部分提供的服務。 此藍圖概述了應用程式的使用案例和技術功能，並深入介紹了構成Offer decisioning的各種體系結構元件和注意事項。

決策管理可以通過兩種方式之一進行部署。 第一種是通過Adobe Experience Platform集線器，它是一個資料中心體系結構。 在「集線器」方法中，服務執行、個性化並以第二延遲提供。 因此，中心架構最適合不需要亞秒延遲的客戶體驗，例如，包括為諸如呼叫中心或個人交互中的亭子或代理輔助體驗提供的服務決定。

第二種方法是通過「體驗邊緣網路」，它是一個分佈於全球各地、地理位置分佈的基礎架構，可提供快速的次秒和毫秒的體驗。 最終消費者體驗由最靠近消費者地理位置的邊緣基礎架構執行，以最小化延遲。 Edge上的決策管理旨在提供即時的消費者體驗。 這些包括Web或移動入站個性化請求等體驗。

此藍圖將涵蓋邊緣決策管理的具體內容。

要瞭解有關集線器上的決策管理的詳細資訊，請參閱 [中心的決策管理](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/offer-decisioning/offers-hub.html?lang=en) 藍圖。

要瞭解有關決策管理的詳細資訊，請參閱產品文檔 [這裡](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html)

## 使用案例

* 通過Web或移動線上個性化。
* 入站offer decisioning和提供建議。
* 跨渠道行程執行 — 通過Adobe Journey Optimizer提供跨Web、移動、電子郵件和其他交互渠道的一致性。

<br>

## 架構

<img src="../assets/offers_edge.svg" alt="邊緣藍圖上的參考體系結構Offer decisioning" style="width:100%; border:1px solid #4a4a4a" />

<br>

## 整合模式

| 整合 | 說明 |
| :-- | :--- |
| [offer decisioningAdobe Target](https://experienceleague.adobe.com/docs/target/using/integrate/ajo/offer-decision.html) | offer decisioning可以與Adobe Target整合，以便作為目標體驗來測試和提供服務。 |

## 先決條件

Adobe Experience Platform

* 必須先在系統中配置架構和資料集，然後才能配置Journey Optimizer資料源
* 對於基於經驗事件類的架構，當希望觸發的事件不是基於規則的事件時，添加「業務流程事件ID」欄位組
* 對於基於單個配置檔案類的架構，添加「配置檔案test詳細資訊」欄位組，以便能夠載入test配置檔案以與Journey Optimizer一起使用

<br>

## 護欄

* 有關Journey Optimizer護欄，請參閱以下 [Journey Optimizer瓜德賴爾](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/limitations.html)。
* 有關Offer decisioning護欄，請參閱以下內容 [offer decisioning產品說明](https://helpx.adobe.com/legal/product-descriptions/offer-decisioning-app-service.html)。

### 資料擷取護欄

<img src="../assets/aep-data-ingestion-details-latency.svg" alt="參考建築Journey Optimizer藍圖" style="width:80%; border:1px solid #4a4a4a" />

<br>

### 激活護欄

<img src="../assets/ajo-activation-details-latency.svg" alt="參考建築Journey Optimizer藍圖" style="width:80%; border:1px solid #4a4a4a" />

<br>

## 實施模式

* 使用Web或移動SDK在網站和移動應用程式上部署，以實現部署SDK的Offer decisioning。
   * [Web/Mobile SDK藍圖](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/data-ingestion/websdk.html)
   * [WebSDK](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/offer-decisioning/offer-decisioning-overview.html)
   * [移動軟體開發工具包](https://aep-sdks.gitbook.io/docs/)

或

* 對於基於API伺服器到伺服器的實現，使用邊緣網路服務API將伺服器直接實現到伺服器的Offer decisioning。
   * [邊緣網路伺服器API](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/api-reference/offer-delivery/deliver-offers.html)

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
* [AdobeOffer decisioning產品說明](https://helpx.adobe.com/legal/product-descriptions/offer-decisioning-app-service.html)
