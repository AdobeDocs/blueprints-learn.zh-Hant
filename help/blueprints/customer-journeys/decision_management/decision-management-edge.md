---
title: 邊緣藍圖上的決策管理
description: 跨管道（包括即時網路和行動體驗）為消費者提供個人化優惠方案。
solution: Experience Platform, Journey Optimizer
exl-id: 31e5f624-5578-49e1-ab92-5cabd596a632
source-git-commit: b18d491fdefc57762932d1570401b5437bf97c76
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Journey Optimizer - Edge Blueprint的決策管理

若要深入了解決策管理，請參閱產品檔案 [此處](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html) 和決策管理概述 [此處](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-overview.html?lang=en)

Adobe決策管理是Adobe Journey Optimizer中提供的服務。 此藍圖概述了應用程式的使用案例和技術功能，並深入介紹構成「決策管理」的各種體系結構元件和注意事項。

決策管理可以通過以下兩種方式之一進行部署。 第一個是透過Adobe Experience Platform Hub，這是單一資料中心架構。 在「中樞」方法中，選件會執行、個人化，並在第二次延遲時傳送。 因此，中心架構最適合不需要次秒延遲的客戶體驗，例如，為資訊站或座席輔助體驗（例如在呼叫中心或人員互動中）提供的選件決策。

第二種方法是透過Experience Edge Network，這是分散於全球各地的基礎架構，可提供亞秒數及毫秒的快速體驗。 由最接近消費者地理位置的邊緣基礎架構執行的最終消費者體驗，以將延遲降至最低。 Edge上的決策管理旨在提供即時消費者體驗。 這些包括網頁或行動傳入個人化請求之類的體驗。

此藍圖將涵蓋邊緣決策管理的詳細資訊。

若要進一步了解中樞上的決策管理，請參閱 [中心的決策管理](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-hub.html?lang=en) 藍圖。

## 邊緣決策管理的使用案例

* 透過網頁或行動傳入體驗進行線上個人化。
* 跨管道歷程執行 — 透過Adobe Journey Optimizer，提供網頁、行動裝置、電子郵件和其他互動管道的一致性。

<br>

## 架構

<img src="../assets/offers_edge.svg" alt="邊緣藍圖上的參考體系結構決策管理" style="width:100%; border:1px solid #4a4a4a" />

<br>

## 整合模式

| 整合 | 說明 |
| :-- | :--- |
| [使用Adobe Target進行決策管理](https://experienceleague.adobe.com/docs/target/using/integrate/ajo/offer-decision.html) | 決策管理可與Adobe Target整合，以便以Target體驗的形式測試和提供選件。 |

## 先決條件

Adobe Experience Platform

* 必須先在系統中設定結構和資料集，才能設定Journey Optimizer資料來源
* 如果您想要觸發非規則型事件的事件，則針對體驗事件類別型結構新增「Orchestration eventID」欄位群組
* 針對個別設定檔類別型結構，新增「設定檔測試詳細資料」欄位群組，以便載入測試設定檔以與Journey Optimizer搭配使用

<br>

## 護欄

* 若為Journey Optimizer護欄，請參閱下列 [Journey Optimizer護欄](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/limitations.html).
* 有關決策管理護欄，請參閱以下內容 [決策管理產品說明](https://helpx.adobe.com/legal/product-descriptions/offer-decisioning-app-service.html).
* 每秒請求數= 5000。
* 響應延遲&lt; 250毫秒。
* 存取邊緣即時設定檔。 設定檔中將僅提供邊緣預計對象和設定檔屬性。
* 如果首次體驗中需要個人化，則中心會是理想的選擇，因為有完整的設定檔可用。 邊緣設定檔必須從中樞同步，才能第一次出現邊緣體驗。 因此，來自Edge的第一個體驗將不包含先前上傳至中樞的設定檔資料。

### 資料擷取護欄

<img src="../../experience-platform/assets/aep_data_flow_guardrails.svg" alt="Experience Platform 資料流程" style="border:1px solid #4a4a4a" width="85%" />

<br>

### 激活護欄

<img src="../../experience-platform/assets/AJO_guardrails.svg" alt="參考架構Journey Optimizer Blueprint" style="width:85%; border:1px solid #4a4a4a" />

<br>

## 實作模式

* 將網頁或行動SDK用於在網站和行動應用程式上部署，以實作部署SDK的決策管理。
   * [Web/Mobile SDK藍圖](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/websdk.html?lang=en)
   * [Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/offer-decisioning/offer-decisioning-overview.html)
   * [MobileSDK](https://aep-sdks.gitbook.io/docs/)

或

* 若是以API伺服器對伺服器為基礎的實作，請使用邊緣網路服務API，將決策管理的伺服器對伺服器實作直接使用。
   * [邊緣網路伺服器API](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/api-reference/offer-delivery/deliver-offers.html)

<br>

## 實作步驟

### Adobe Experience Platform

#### 結構/資料集

1. 在 Experience Platform 中基於客戶提供的資料[設定個別個人資料、體驗事件及多實體方案。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm)
1. 在 Experience Platform 中為要擷取的資料[建立資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=zh-Hant)。
1. [在 Experience Platform 中新增使用標籤](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=zh-Hant)至資料集以便於治理。
1. [建立政策](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=zh-Hant)以在目標上執行治理。

#### 設定檔/身分

1. [建立任何客戶特定的命名空間。](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hant)
1. [新增身份至方案](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hant)。
1. [為個人資料啟用方案和資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=zh-Hant)。
1. 為[!UICONTROL 即時客戶個人資料]的不同檢視[設定合併政策](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=zh-Hant) (可選)。
1. 建立歷程使用情形的區段。

#### 來源/目的地

1. 使用串流 API 和來源連接器[將資料擷取到 Experience Platform。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=zh-Hant)

## 相關檔案

* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html)
* [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer.html)
* [Adobe Journey Optimizer決策管理](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html)
* [Adobe Journey Optimizer產品說明](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer.html)
* [Adobe決策管理產品說明](https://helpx.adobe.com/legal/product-descriptions/offer-decisioning-app-service.html)
