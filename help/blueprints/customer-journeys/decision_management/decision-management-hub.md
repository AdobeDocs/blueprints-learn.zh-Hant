---
title: 中心藍圖上的決策管理
description: 在各管道（包括資訊站、代理程式協助的體驗，以及電子郵件和其他傳出傳遞）為消費者提供個人化優惠方案。
solution: Experience Platform, Journey Optimizer
exl-id: 5a386e18-bbac-4216-a35f-0a5016785e4a
source-git-commit: 5110ee2a7a079945475055cbcfdabf7cdcaa0ab5
workflow-type: tm+mt
source-wordcount: '906'
ht-degree: 16%

---

# 中心藍圖上的決策管理

若要深入了解決策管理，請參閱產品檔案 [此處](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html) 和決策管理概述 [此處](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-overview.html?lang=en)

Adobe決策管理是Adobe Journey Optimizer中提供的服務。 此藍圖概述了應用程式的使用案例和技術功能，並深入介紹構成「決策管理」的各種體系結構元件和注意事項。

Journey Optimizer可用來在適當的時間，跨所有接觸點為客戶提供最佳選件和體驗。 Decision Management透過集中的行銷選件資料庫和決策引擎，將規則和限制套用至Adobe Experience Platform建立的豐富即時設定檔，協助您在正確的時間為客戶傳送正確的優惠方案，讓個人化更加輕鬆。

決策管理可以通過以下兩種方式之一進行部署。 第一個是透過Adobe Experience Platform中樞，這是中央資料中心架構。 在「中樞」方法中，會執行、個人化優惠，並在超過500毫秒的延遲內提供。 因此，中心架構最適合不需要次秒延遲的客戶體驗，例如，為資訊站或代理輔助體驗（例如在呼叫中心或個人互動中）提供的選件決策。 插入電子郵件和傳出行銷活動的優惠方案，也由中樞方法提供支援。

第二種方法是透過Experience Edge Network，這是分散於全球各地的基礎架構，可提供亞秒數及毫秒的快速體驗。 由最接近消費者地理位置的邊緣基礎架構執行的最終消費者體驗，以將延遲降至最低。 Edge上的決策管理可提供即時消費者體驗，例如網路或行動傳入個人化請求。

此藍圖將涵蓋中心上「決策管理」的詳細資訊。

若要進一步了解Edge上的決策管理，請參閱 [邊緣決策管理](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-edge.html?lang=en) 藍圖。

## 中心上決策管理的使用案例

* 資訊站和商店體驗上的個人化優惠方案。
* 通過座席輔助體驗（如呼叫中心或銷售互動）提供個性化優惠。
* 包含在電子郵件、簡訊、行動推播通知或其他傳出互動中的選件。
* 提供外部ESP和郵件傳送系統的選件以進行傳送。
* 跨管道歷程執行 — 透過Adobe Journey Optimizer，提供網頁、行動裝置、電子郵件和其他互動管道的一致性。

<br>

## 架構

<img src="../assets/offers_hub.svg" alt="邊緣藍圖上的參考體系結構決策管理" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## 先決條件

Adobe Experience Platform

* 必須先在系統中設定結構和資料集，才能設定Journey Optimizer資料來源
* 如果您想要觸發非規則型事件的事件，則針對體驗事件類別型結構新增「Orchestration eventID」欄位群組
* 針對個別設定檔類別型結構，新增「設定檔測試詳細資料」欄位群組，以便載入測試設定檔以與Journey Optimizer搭配使用

<br>

## 護欄

* 若為Journey Optimizer護欄，請參閱下列 [Journey Optimizer護欄](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/limitations.html).
* 有關決策管理護欄，請參閱以下內容 [決策管理產品說明](https://helpx.adobe.com/legal/product-descriptions/offer-decisioning-app-service.html).
* 每秒請求數= 2000。
* 響應延遲&lt; 500毫秒。
* 存取完整即時客戶設定檔，包括受眾會籍、屬性和體驗事件。


### 資料擷取護欄

<img src="../../experience-platform/assets/aep_data_flow_guardrails.svg" alt="Experience Platform 資料流程" style="border:1px solid #4a4a4a" width="85%" class="modal-image" />

<br>

### 激活護欄

<img src="../../experience-platform/assets/AJO_guardrails.svg" alt="參考架構Journey Optimizer Blueprint" style="width:85%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## 實作模式

* 透過與直接整合，在電子郵件、簡訊和傳出通道中實作 [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/offers-e2e.html).
* 針對以伺服器API為基礎的決策管理實作，請運用 [決策API](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/api-reference/offer-delivery/decisioning-vs-edge-apis.html).
* 若要實作批次決策以大量傳送選件給訊息傳送應用程式，請使用 [批次決策API](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/api-reference/offer-delivery/batch-decisioning-api.html).
* 若為Edge型即時體驗，請依照 [邊緣藍圖上的決策管理](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-edge.html?lang=en).
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
