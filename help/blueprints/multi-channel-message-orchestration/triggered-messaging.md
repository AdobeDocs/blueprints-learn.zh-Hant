---
title: 觸發訊息與Adobe Experience Platform情境
description: 使用Adobe Experience Platform作為中心的串流資料、客戶個人檔案和細分，執行觸發式訊息和體驗。
solution: Experience Platform, Campaign, Journey Orchestration
kt: 7197
translation-type: tm+mt
source-git-commit: df1e14631eddb0055f8e7a42db1e34d459667433
workflow-type: tm+mt
source-wordcount: '605'
ht-degree: 1%

---


# 觸發訊息與Adobe Experience Platform情境

使用Adobe Experience Platform作為中心的串流資料、客戶個人檔案和細分，執行觸發式訊息和體驗。

## 使用案例

* 觸發訊息
* 註冊確認
* 放棄購物車和申請表
* 位置觸發訊息

## 建築

<img src="assets/triggered.svg" alt="觸發訊息與Adobe Experience Platform情境的參考架構" style="border:1px solid #4a4a4a" />

## 整合模式

* Adobe Experience Platform->Journey Orchestration

## 必要條件

* Adobe Experience Platform
* Journey Orchestration

## 瓜德賴爾

### Journey Orchestration

* 請參閱[有關限制的詳細資訊連結](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=en#starting-with-journeys)
* 可透過API設定使用封閉功能，以確保目標系統未飽和至故障點。 封頂表示超過封頂的訊息會完全丟棄，且從未傳送。 仍不支援頻寬限制。
   * 最大連接數：目標可處理的http/s連接數上限
   * 最大呼叫計數：periodInMs參數中要進行的最大呼叫數
   * periodInMs:時間（毫秒）
* 區段會籍啟始的歷程可以兩種模式運作：
   * 批次區段（每24小時重新整理一次）
   * 串流區段（&lt;5分鐘資格）
* 批次區段：確保您瞭解合格用戶的每日數量，並確保目標系統能夠處理每個旅程和所有旅程的突發吞吐量
* 串流區段：確保可以處理初次的描述檔資格，以及每個歷程和所有歷程的每日串流合格容量
* 最終目的地必須支援REST API和JSON裝載
* 目前不支援Offer decisioning
* 請參閱[Experience Platform的概要檔案和資料接收護欄](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)

### Campaign Standard

* 吞吐量僅支援14 tps（每小時50k）
* 不支援區段會籍啟始的歷程
* Journey Orchestration中支援對交易訊息的開啟／點按次數反應事件。
* 事務性消息日誌當前不會與Experience Platform同步，需要手動配置。 建議最多每四小時匯出一次記錄檔。


## 實施步驟

### Adobe Experience Platform

#### 架構／資料集

1. 根據客戶提供的資料，在Experience Platform中設定個別描述檔、體驗事件和多實體結構。
1. 建立下列促銷活動結構：broadLog、trackingLog、非交付項位址和描述檔偏好設定（選用）。
1. 將資料使用標籤新增至資料集以利管理。
1. 建立策略以對目標實施治理。

#### 個人檔案／身分識別

1. 建立任何客戶專屬的命名空間。
1. 將身分新增至結構。
1. 啟用描述檔和資料集。
1. 為即時客戶個人檔案的不同檢視設定合併規則（可選）。
1. 建立促銷活動使用的區段。

#### 來源／目標

1. 使用串流API和來源連接器將資料內嵌至Experience Platform。
1. 設定[!DNL Azure] blob儲存目標以搭配促銷活動使用。

#### 行動應用程式部署

1. 實作Campaign Classic的促銷活動SDK或Campaign Standard的Experience PlatformSDK。 如果有Experience Platform Launch，建議使用Campaign Classic/標準擴充功能與Experience PlatformSDK。


### Journey Orchestration

1. 用於啟動客戶歷程的串流資料必須先在Journey Orchestration中設定，才能取得協調ID。 然後，此協調ID會提供給開發人員，以便用於擷取。
1. 設定外部資料來源。
1. 設定自訂動作。

### Campaign Standard

1. 使用適當的個人化設定來設定訊息範本。
1. 設定匯出工作流程以匯出交易訊息記錄檔。 建議最多每四小時執行一次。


## 相關檔案

* [Adobe Experience Platform檔案](https://experienceleague.adobe.com/docs/experience-platform.html?lang=en)
* [Journey Orchestration檔案](https://experienceleague.adobe.com/docs/journey-orchestration.html?lang=en)
* [Campaign Classic檔案](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=en)
* [Campaign Standard檔案](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=en)
* [Experience Platform Launch檔案](https://experienceleague.adobe.com/docs/launch.html?lang=en)
* [Experience Platform行動SDK檔案](https://experienceleague.adobe.com/docs/mobile.html?lang=en)
