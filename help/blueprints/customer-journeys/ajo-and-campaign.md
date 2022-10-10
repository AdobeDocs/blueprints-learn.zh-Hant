---
title: Journey Optimizer與Adobe Campaign Blueprint
description: 示範Adobe Journey Optimizer如何與Adobe Campaign搭配使用，以利用Campaign中的即時訊息伺服器原生傳送訊息
solution: Journey Optimizer, Campaign, Campaign v8, Campaign Classic v7, Campaign Standard
exl-id: 076446a9-dfb9-464c-a04f-6864b8cb7b48
source-git-commit: 6901596cbb661ffa8cf57c6ae958db1978bf1520
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Journey Optimizer搭配Adobe Campaign

示範如何搭配Adobe Journey Optimizer使用Adobe Campaign，利用Campaign中的即時訊息伺服器以原生方式傳送訊息。

<br>

## 架構

<img src="assets/ajo-campaign-architecture.svg" alt="參考架構Journey Optimizer Blueprint" style="width:100%; border:1px solid #4a4a4a" />

>[!IMPORTANT]
>可以同時使用Journey Optimizer和Campaign來彼此獨立傳送訊息，但有一些技術考量需加以考慮。 如果您想沿用此路線，請與售前企業架構師合作，以確保您了解支援實施所需的內容。

<br>

## 先決條件

### Adobe Experience Platform

* 必須先在系統中設定結構和資料集，才能設定Journey Optimizer資料來源
* 如果您想要觸發非規則型事件的事件，則針對體驗事件類別型結構新增「Orchestration eventID」欄位群組
* 針對個別設定檔類別型結構，新增「設定檔測試詳細資料」欄位群組，以便載入測試設定檔以與Journey Optimizer搭配使用
* Journey Optimizer和Campaign會布建在相同的IMS組織中

### 促銷活動v7/v8或Campaign Standard

* 即時訊息服務（即訊息中心）的執行例項必須由Adobe管理Cloud Services托管
* 所有訊息編寫都是在Campaign執行個體本身內完成

<br>

## 護欄

[Journey Optimizer護欄產品連結](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=en)

### 其他Journey Optimizer護欄

* 今天可透過API使用上限設定，以確保目的地系統未飽和至故障點。 這表示超過上限的訊息會完全刪除，且不會傳送。 不支援限制。
   * 最大連接數 — 目標可處理的最大http/s連接數
   * 呼叫計數上限 — periodInMs參數中要進行的呼叫數上限
   * periodInMs — 以毫秒為單位的時間
* 由區段會籍發起的歷程可以兩種模式操作：
   * 批次區段（每24小時重新整理一次）
   * 串流區段（&lt;5分鐘資格）
* 批次區段 — 需要確保您瞭解符合資格使用者的每日流量，並確保目標系統可以處理每個歷程以及所有歷程的高載輸送量
* 串流區段 — 需要確保個人資料資格的初始高載可隨每個歷程及所有歷程中符合資格的每日串流流量一起處理
* 不支援的決策管理
* 不支援業務事件
* 傳出整合至第三方系統
   * 不支援單個靜態IP，因為我們的基礎架構是多租戶（必須允許列出所有資料中心IP）
   * 自訂動作僅支援POST和PUT方法
   * 驗證支援：token |密碼 | OAuth2
* 無法在各種沙箱之間封裝及移動Adobe Experience Platform或Journey Optimizer的個別元件。 必須在新環境中重新實作

<br>

### Campaign整合

如需與您特定版本的Adobe Campaign和Adobe Journey Optimizer整合的指引，請參閱每個Adobe Campaign版本的對應指南。

* [Adobe Journey Optimizer與Campaign v7](ajo-and-campaign-v7.md)
* [Adobe Journey Optimizer與Campaign v8](ajo-and-campaign-v8.md)