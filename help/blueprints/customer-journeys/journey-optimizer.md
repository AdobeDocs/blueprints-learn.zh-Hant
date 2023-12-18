---
title: Journey Optimizer — 觸發的訊息傳送與 Adobe Experience Platform 藍圖
description: 使用 Adobe Experience Platform 做為串流資料、客戶個人資料和分眾的中心，執行觸發式訊息和體驗。
solution: Journey Optimizer
exl-id: 97831309-f235-4418-bd52-28af815e1878
source-git-commit: 3102ab35e48fe51010185ea5a0352c77f068d0d4
workflow-type: tm+mt
source-wordcount: '710'
ht-degree: 97%

---

# Journey Optimizer藍圖

Adobe Journey Optimizer 是行銷團隊專門建立的一款系統，可即時回應客戶行為，並滿足客戶需求。資料管理功能已移至 Adobe Experience Platform，有助於行銷團隊專注於其最佳作法：建立一流的客戶歷程和個人化對話。此 Blueprint 概述了應用程式的技術功能，並深入探討了組成 Adobe Journey Optimizer 的各種架構元件。

<br>

## 使用案例

* 觸發的訊息
* 歡迎和註冊確認資訊
* 購物車與申請表格放棄
* 位置觸發的訊息
* 體育場內體驗
* 旅行和酒店業抵達前和住宿期間的體驗

<br>

## 架構

<img src="assets/ajo-architecture.svg" alt="Journey Optimizer 參考架構藍圖" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## 藍圖方案

| 狀況 | 說明 | 功能 |
| :-- | :--- | :--- |
| [第三方傳訊](3rd-party-messaging.md) | 展示如何搭配第三方訊息系統使用 Adobe Journey Optimizer 來協調和傳送個人化通訊 | 在客戶與您的品牌或公司互動時，立即提供 1:1 的個人化通訊<br><br>考量事項：<br><ul><li>第三方系統必須支援用於驗證的承載令牌</li><li>由於多租用戶架構，不支援靜態 IP</li><li>每秒的 API 呼叫次數，請注意協力廠商系統的架構限制。  客戶可能需要向第三方供應商購買額外的量，以支援來自 Journey Optimizer 的量</li><li>在消息或承載中不支援決策管理</li></ul> |

<br>

## 整合模式

| 整合 | 說明 | 功能 |
| :-- | :--- | :--- |
| [Journey Optimizer 搭配 Adobe Campaign](ajo-and-campaign.md) | 顯示如何使用 Adobe Journey Optimizer 藉助 Real-Time Customer Profile 來協調 1:1 體驗，並運用原生 Adobe Campaign 交易訊息系統來傳送訊息 | 運用 Real-Time Customer Profile 和 Journey Optimizer 的強大功能，協調即時體驗，同時運用 Adobe Campaign 的原生即時訊息傳送功能進行最後一英里的通訊<br><br>考量事項：<br><ul><li>Campaign 應用程式必須位於 v7 版本編號 21.1 以上或 v8 上</li><li>傳送訊息輸送量</li><ul><li>Campaign v7 — 每小時最多 50k</li><li>Campaign v8 — 每小時最多 1M</li><li>Campaign Standard — 每小時最多 50k</li></ul><li>不執行限制，因此使用案例需要企業架構師的技術審查</li><li>不支援在 Campaign 傳送的訊息中使用決策管理</li></ul> |

<br>

## 先決條件

Adobe Experience Platform

* 必須先在系統中設定方案和資料集，才能設定 Journey Optimizer 資料來源
* 如果您想要觸發非規則型的事件，則針對體驗事件類別型方案，新增「Orchestration eventID」欄位群組
* 針對個別個人資料類別型方案，新增「個人資料測試詳細資料」欄位群組，以便載入測試個人資料以與 Journey Optimizer 搭配使用

電子郵件

* 必須準備好要用於訊息傳送的子網域
* 子網域可以完全委派給 Adobe（建議），或 CNAME 可用來指向 Adobe 專用的 DNS 伺服器（自訂）
* 每個子網域都需要 Google TXT 記錄，以確保良好的傳遞能力

行動裝置推送

* 客戶必須有可建立應用程式的行動裝置開發人員
* Adobe Experience Platform Mobile SDK

<br>

## 護欄

[Journey Optimizer 護欄產品連結](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html)

[端對端延遲指引](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html)

請注意下列其他考量事項：

* 批次區段 — 需要確保您瞭解符合限定條件使用者的每日流量，並確保目標系統可以處理每個歷程以及所有歷程的高載輸送量
* 串流區段 — 需要確保個人資料限定條件的初始高載可隨每個歷程及所有歷程中符合限定條件的每日串流流量一起處理
* 僅在訊息中本機支援「決策管理」（無自訂動作）
* 支援的訊息類型：
   * 電子郵件
   * 推播 (FCM / APNS)
   * 自訂動作（透過 Rest API）
* 傳出整合至第三方系統
   * 不支援單個靜態 IP，因為我們的基礎架構是多租戶（必須允許列出所有資料中心 IP）
   * 自訂動作僅支援 POST 和 PUT 方法
   * 透過使用者/通行證或授權權杖進行驗證
* 無法在各種沙箱之間封裝及移動 Adobe Experience Platform 或 Journey Optimizer 的個別元件。必須在新環境中重新實作

## 相關文件

* [Experience Platform 文件](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hant)
* [Experience Platform Tags 文件](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=zh-Hant)
* [Experience Platform Mobile SDK 文件](https://experienceleague.adobe.com/docs/mobile.html?lang=zh-Hant)
* [Journey Optimizer 文件](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=zh-Hant)
* [Journey Optimizer 產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/adobe-journey-optimizer.html)
