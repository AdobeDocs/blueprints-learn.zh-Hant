---
title: Journey Optimizer — 觸發的訊息傳送與 Adobe Experience Platform Blueprint
description: 使用 Adobe Experience Platform 做為串流資料、客戶個人資料和分眾的中心，執行觸發式訊息和體驗。
solution: Experience Platform, Campaign, Journey Orchestration
kt: 7197
exl-id: 97831309-f235-4418-bd52-28af815e1878
source-git-commit: 93561231286b5bfd9bf3660399b542d27aedb52c
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 95%

---

# Journey Optimizer

Adobe Journey Optimizer 是行銷團隊專門建立的一款系統，可即時回應客戶行為，並滿足客戶需求。資料管理功能已移至 Adobe Experience Platform，有助於行銷團隊專注於其最佳作法：建立一流的客戶歷程和個人化對話。此 Blueprint 概述了應用程式的技術功能，並深入探討了組成 Adobe Journey Optimizer 的各種架構元件。

## 使用案例

* 觸發的訊息
* 註冊確認
* 購物車與申請表格放棄
* 位置觸發的訊息

## 架構

<img src="assets/journey-optimizer.png" alt="觸發的訊息傳送與 Adobe Experience Platform Blueprint 之參考架構" style="border:1px solid #4a4a4a" />

## 整合模式

* Adobe Experience Platform -> Journey Optimizer

## 先決條件

1. 必須使用有效的 IMS Org，才能為 Experience Cloud 佈建客戶
1. 行動裝置推送

* 客戶必須有可建立應用程式的行動裝置開發人員
* Adobe Experience Platform Mobile SDK
* 資料收集
   * 行動標籤屬性
      * 擴充功能：
         * Adobe Journey Optimizer 擴充功能
         * Adobe Experience Platform Edge Network
         * 身分
         * 行動裝置核心
         * 個人檔案
   * 應用程式設定
   * 資料流
      * 啟用 Experience Platform
      * 事件資料集 — 用於收集一般行動裝置行為
      * 個人資料之資料集 — AJO 推送個人資料之資料集 (不可不同)

## 護欄

* 如需Journey Optimizer [LINK](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=en)護欄的詳細資訊，請參閱連結
* 批次區段 — 需要確保您瞭解符合資格使用者的每日流量，並確保目標系統可以處理每個歷程以及所有歷程的高載輸送量
* 串流區段 — 需要確保個人資料資格的初始高載可隨每個歷程及所有歷程中符合資格的每日串流流量一起處理
* 個人資料更新活動 — 即時客戶個人資料可從歷程內以原生方式更新。將更新處理至個人資料儲存區時，延遲最多 1 分鐘
* 業務事件 — 可根據進入 JO 系統的外部呼叫觸發以讀取區段為基礎的歷程。
* 僅原生支援訊息中的 Offer Decisioning。未來透過原生操作提供支援
* 支援的通道：
   * 電子郵件
   * 推送 (FCM / APNS)
   * 重設 API 端點
* 以水平縮放方式每秒處理 5k 個事件 (電子錢包受限)
* A/B 測試需使用兩個傳送，並使用 QS 或 CJA 確認結果
* Litmus 整合 — 必須有 Litmus 帳戶才可運用整合

## 實施步驟

### Adobe Experience Platform

#### 方案 / 資料集

1. 在 Experience Platform 中基於客戶提供的資料[設定個別個人資料、體驗事件及多實體方案。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm)
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

1. 必須先在 Journey Optimizer 中設定用於啟動客戶歷程的串流資料才可獲得協調 ID。此協調 ID 然後提供給開發者與擷取一起使用。
1. 設定外部資料來源。
1. 設定自訂動作。

## 相關文件

* [Adobe Experience Platform 文件](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hant)
* [Journey Optimizer 文件](https://experienceleague.adobe.com/docs/journey-orchestration.html?lang=zh-Hant)
* [Experience Platform Launch 文件](https://experienceleague.adobe.com/docs/launch.html?lang=zh-Hant)
* [Experience Platform Mobile SDK 文件](https://experienceleague.adobe.com/docs/mobile.html?lang=zh-Hant)
