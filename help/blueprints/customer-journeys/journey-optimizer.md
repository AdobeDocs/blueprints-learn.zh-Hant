---
title: Journey Optimizer — 觸發訊息與Adobe Experience Platform Blueprint
description: 使用 Adobe Experience Platform 做為串流資料、客戶個人資料和分眾的中心，執行觸發式訊息和體驗。
solution: Experience Platform, Campaign, Journey Orchestration
kt: 7197
exl-id: 97831309-f235-4418-bd52-28af815e1878
source-git-commit: dc13a1fe9a32f70497c5c73485618e6989b7a644
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 49%

---

# Journey Optimizer

Adobe Journey Optimizer是行銷團隊專門建立的系統，可即時回應客戶行為，並在客戶行為所在的位置符合他們。 資料管理功能已移至Adobe Experience Platform，讓行銷團隊可專注於其最佳作法：它創造了世界級的客戶歷程和個人化對話。  此藍圖概述應用程式的技術功能，並深入探討組成Adobe Journey Optimizer的各種架構元件。

## 使用案例

* 觸發的訊息
* 註冊確認
* 購物車與申請表格放棄
* 位置觸發的訊息

## 架構

<img src="assets/journey-optimizer.png" alt="觸發的訊息傳送與 Adobe Experience Platform Blueprint 之參考架構" style="border:1px solid #4a4a4a" />

## 整合模式

* Adobe Experience Platform—>Journey Optimizer

## 先決條件

1. 必須使用有效的IMS組織布建Experience Cloud，才能布建客戶
1. 行動推播

* 客戶必須有可用來建立應用程式的行動開發人員
* Adobe Experience Platform Mobile SDK
* Adobe啟動
   * 行動屬性
      * 擴充功能：
         * Adobe Journey Optimizer擴充功能
         * Adobe Experience Platform Edge Network
         * 身分
         * 行動核心
         * 設定檔
   * 應用程式設定
   * 資料流
      * 啟用Experience Platform
      * 事件資料集 — 用於收集一般行動行為
      * 設定檔資料集 — AJO推送設定檔資料集（不能不同）

## 護欄

* 請參閱連結以獲取關於限制的更多詳情
* 批次區段 — 需要確保您了解合格使用者的每日流量，並確保目的地系統可處理每個歷程及所有歷程的突發吞吐量
* 串流區段 — 需要確保可處理設定檔資格的初始突發，以及每個歷程和所有歷程的每日串流合格數量
* 設定檔更新活動 — 即時客戶設定檔可從歷程內以原生方式更新。  將更新處理到設定檔存放區時，延遲最多1分鐘
* 業務事件 — 可根據進入JO系統的外部呼叫觸發以讀取區段為基礎的歷程以開始
* 本機僅支援訊息中的Offer decisioning。 未來透過原生動作提供支援
* 支援的管道：
   * 電子郵件
   * 推播(FCM / APNS)
   * 重設API端點
* 以水準縮放方式每秒處理5k個事件（Wallet受限）
* A/B測試需使用兩個傳送，並使用QS或CJA決定結果
* Litmus整合 — 必須有Litmus帳戶才能運用整合

## 實施步驟

### Adobe Experience Platform

#### 方案 / 資料集

1. 在 Experience Platform 中基於客戶提供的資料[設定個別個人資料、體驗事件及多實體方案。](https://experienceleague.adobe.com/docs/platform-learn/tutorials/schemas/create-a-schema.html?lang=zh-Hant)
1. 建立 broadLog、trackingLog、無法送達的地址及個人資料偏好設定 (可選)　的 Adobe Campaign 方案。
1. 在 Experience Platform 中為要擷取的資料[建立資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=zh-Hant)。
1. [在 Experience Platform 中新增使用標籤](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=zh-Hant)至資料集以便於治理。
1. [建立政策](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=zh-Hant)以在目標上執行治理。

#### 個人資料 / 身份

1. [建立任何客戶特定的命名空間。](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hant)
1. [新增身份至方案](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html)。
1. [為個人資料啟用方案和資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=zh-Hant)。
1. 為[!UICONTROL 即時客戶個人資料]的不同檢視[設定合併政策](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=zh-Hant) (可選)。
1. 建立行銷活動使用的區段。

#### 來源 / 目標

1. 使用 API 與來源連接器[擷取資料到 Experience Platform](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=zh-Hant)。1. 設定[!DNL Azure]要與 Adobe Campaign 一起使用的 Blob 儲存目標。

#### 行動應用程式部署

1. 對 Adobe Campaign Classic 實施 Adobe Campaign SDK，或對 Adobe Campaign Standard 實施 Experience Platform SDK。如果 Experience Platform Launch 存在，建議 Adobe Campaign Classic 或 Adobe Campaign Standard 延伸與 Experience Platform SDK 一起使用。


### Journey Orchestration

1. 用於起始客戶歷程的串流資料，必須先在Journey Optimizer中進行設定，才能取得協調ID。 此協調 ID 然後提供給開發者與擷取一起使用。
1. 設定外部資料來源。
1. 設定自訂動作。

## 相關文件

* [Adobe Experience Platform 文件](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hant)
* [Journey Optimizer檔案](https://experienceleague.adobe.com/docs/journey-orchestration.html?lang=zh-Hant)
* [Experience Platform Launch 文件](https://experienceleague.adobe.com/docs/launch.html?lang=zh-Hant)
* [Experience Platform Mobile SDK 文件](https://experienceleague.adobe.com/docs/mobile.html?lang=zh-Hant)
