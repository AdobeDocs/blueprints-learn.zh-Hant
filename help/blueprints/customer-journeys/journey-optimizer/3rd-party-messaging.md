---
title: Journey Optimizer — 第三方傳訊藍圖
description: 示範Adobe Journey Optimizer如何與第三方傳訊系統搭配使用，以傳送個人化通訊。
solution: Journey Optimizer
exl-id: 3a14fc06-6d9c-4cd8-bc5c-f38e253d53ce
source-git-commit: 0a3ebcbc6029df46bd988cb8f15ecf838f80c3c9
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 61%

---

# 第三方傳訊藍圖

示範Adobe Journey Optimizer如何與第三方傳訊系統搭配使用，以傳送個人化通訊。

<br>

## 架構

<img src="images/3rd-party-messaging-architecture.svg" alt="Journey Optimizer 參考架構藍圖" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## 先決條件

**Adobe Experience Platform**

* 必須先在系統中設定方案和資料集，才能設定 Journey Optimizer 資料來源
* 對於體驗事件類別型結構描述，當您想要觸發非規則型事件的事件時，請新增「Orchestration eventID」欄位群組
* 對於以個別設定檔類別為基礎的結構描述，新增「設定檔測試詳細資料」欄位群組以便載入測試設定檔以用於Journey Optimizer

**第三方傳訊應用程式**

* 傳送交易承載時必須支援 REST API 呼叫

<br>

## 護欄

[Journey Optimizer 護欄產品連結](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=zh-Hant)

[護欄與端對端延遲指引](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/guardrails.html?lang=zh-Hant)

<br>

## 實施步驟

### Adobe Experience Platform

#### 方案/資料集

1. 根據客戶提供的資料，在Experience Platform中[設定結構描述](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm&lang=zh-Hant)。
1. 在 Experience Platform 中為要擷取的資料[建立資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=zh-Hant)。
1. 在 Experience Platform 中[新增資料使用標籤](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=zh-Hant)至資料集以便於治理。
1. [建立政策](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=zh-Hant)以在目標上執行治理。

#### 個人資料/身份

1. [建立任何客戶特定的命名空間。](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hant)
1. [新增身份至方案](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hant)。
1. [為個人資料啟用方案和資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile)。
1. 為[!UICONTROL 即時客戶個人資料]的不同檢視[設定合併政策](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=zh-Hant) (可選)。
1. 建立 Journey 使用的區段。

#### 來源/目標

1. 使用串流 API 和來源連接器[將資料擷取到 Experience Platform。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&lang=zh-Hant)

### Journey Optimizer

1. 設定您的Experience Platform資料來源，並決定應在歷程中快取哪些欄位
1. 必須先設定串流資料（用於啟動客戶歷程）以取得協調流程ID。 然後會將此協調流程ID提供給開發人員在擷取期間使用
1. 設定外部資料來源
1. 為第三方應用程式設定自定動作

### 行動推播設定（選用，因為第三方可能收集權杖）

1. 實作 Experience Platform Mobile SDK 以收集推播權杖和登入資訊，以系結回已知的客戶個人資料
1. 運用 Adobe 標籤，並使用下列擴充功能建立行動屬性：
   * Adobe Journey Optimizer
   * Adobe Experience Platform Edge Network
   * [!DNL Edge Network]的身分
   * 行動裝置核心
1. 針對行動應用程式部署與網頁部署，確保您擁有專屬的資料流
1. 如需更多詳細資訊，請參閱 [Adobe Journey Optimizer 行動指南](https://developer.adobe.com/client-sdks/documentation/adobe-journey-optimizer/)

<br>

## 相關文件

* [Experience Platform 文件](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hant)
* [Experience Platform Tags 文件](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=zh-Hant)
* [Experience Platform Mobile SDK 文件](https://experienceleague.adobe.com/docs/mobile.html?lang=zh-Hant)
* [Journey Optimizer 文件](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=zh-Hant)
* [Journey Optimizer 產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/adobe-journey-optimizer.html)