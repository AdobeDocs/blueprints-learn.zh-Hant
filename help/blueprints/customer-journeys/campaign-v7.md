---
title: Campaign v7 藍圖
description: Adobe Campaign v7 是專為傳統行銷通道（例如電子郵件和直接郵件）所建置的宣傳工具。它提供強大的 ETL 和資料管理功能，以幫助策劃和組織完美的行銷活動。其協調引擎提供豐富的多點接觸行銷計畫，核心著重於批次導向歷程。此外，它還隨附即時傳訊伺服器，讓行銷團隊能根據來自任何 IT 系統的包含所有內容的承載，傳送預先定義的訊息，以處理密碼重設、訂單確認、電子回執等更多事項。
solution: Campaign,Campaign Classic v7
exl-id: 71c808f5-59e6-4f49-a6ba-581ed508bc04
source-git-commit: 5110ee2a7a079945475055cbcfdabf7cdcaa0ab5
workflow-type: ht
source-wordcount: '1195'
ht-degree: 100%

---

# Campaign v7 藍圖

Adobe Campaign v7 是專為傳統行銷通道（例如電子郵件和直接郵件）所建置的宣傳工具。它提供強大的 ETL 和資料管理功能，以幫助策劃和組織完美的行銷活動。其協調引擎提供豐富的多點接觸行銷計畫，核心著重於批次導向歷程。此外，它還隨附即時傳訊伺服器，讓行銷團隊能根據來自任何 IT 系統的包含所有內容的承載，傳送預先定義的訊息，以處理密碼重設、訂單確認、電子回執等更多事項。

<br>

## 使用案例

* 基於批次的傳訊程式
* 登入與再行銷活動
* 直接郵件廣告、手冊和雜誌宣傳
* 低流量的簡單交易式傳訊（例如密碼重設、電子郵件接收、訂單確認等）

<br>

## 架構

<img src="assets/campaign-v7-architecture.svg" alt="Campaign v7 藍圖的參考架構" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## 整合模式

| 狀況 | 說明 | 功能 |
| :-- | :--- | :--- |
| [Real-Time CDP 搭配 Adobe Campaign](rtcdp-and-campaign.md) | 展示 Adobe Experience Platform 的 Real-Time CDP 和集中式細分工具如何與 Adobe Campaign 一起使用，以提供個人化的對話體驗。 | <ul><li>使用雲端儲存檔案交換和 Adobe Campaign 擷取工作流程，共用從 Real-Time CDP 到 Adobe Campaign 的個人資料和對象 </li><li>輕鬆將客戶對話的傳遞和互動資料從 Adobe Campaign 分享回 Real-Time CDP，以增強 Real-Time Customer Profile，並提供傳訊行銷活動的跨通道報表</li></ul> |
| [Journey Optimizer 搭配 Adobe Campaign](ajo-and-campaign.md) | 顯示如何使用 Adobe Journey Optimizer 藉助 Real-Time Customer Profile 來協調 1:1 體驗，並運用原生 Adobe Campaign 交易訊息系統來傳送訊息 | 運用 Real-Time Customer Profile 和 Journey Optimizer 的強大功能，協調即時體驗，同時運用 Adobe Campaign 的原生即時訊息傳送功能進行最後一英里的通訊<br><br>考量事項：<br><ul><li>可透過即時消息伺服器每小時發送最多 50k 訊息<li>不會從 Journey Optimizer 執行節流，以確保售前企業架構師的技術審查</li><li>Campaign v7 即時傳訊伺服器承載不支援決策管理</li></ul> |

<br>

## 先決條件

### 應用程式伺服器和即時傳訊伺服器

* 必須有 Adobe Campaign Client Console 才能與 Campaign v8 軟體互動和使用。它是基於 Windows 的客戶端，使用標準 Internet 協定（SOAP、HTTP 等）。請確定您的組織已啟用必要權限，以分發、安裝及執行軟體

* IP 位址允許清單
   * 識別所有使用者在存取用戶端主控台期間將利用的 IP 範圍
   * 識別允許哪些企業系統與即時傳訊伺服器對話，並確保它們具有您可以允許列出的靜態分配的 IP 或範圍
   * 這可透過「行銷活動控制面板」來設定及控制
* sFTP 金鑰管理
   * 具有可與 Campaign 提供的 sFTP 搭配使用的 SSH 公開金鑰。這可透過「行銷活動控制面板」來設定及控制。

### 電子郵件

* 已準備好要用於訊息傳送的子網域
* 子網域可以完全委派給 Adobe（建議），或 CNAME 可用來指向 Adobe 專用的 DNS 伺服器（自訂）
* 每個子網域都需要 Google TXT 記錄，以確保良好的傳遞能力

### 行動裝置推送

* 讓行動開發人員可部署、設定和建置行動應用程式
* Adobe 僅提供 SDK 來收集來自 FCM (Android) 和 APNS (iOS) 以將訊息承載傳送至其伺服器的必要資訊。客戶應負責如何對行動應用程式進行編碼、部署、管理和除錯

### 網頁應用程式（可選）

* 可以為 Campaign 托管的取消訂閱和登陸頁面委派其他子網域
* 強烈建議使用 SSL 憑證

<br>

## 護欄

### 應用程式伺服器大小調整

* 儲存可擴展到 100M 個人資料
* 透過 Adobe Admin Console（建議）或在應用程式本身本機設定及控制使用者存取權
* 載入至 Campaign 的資料應透過批次檔案完成
   * API 資料載入支援主要用於管理資料庫內的個人資料或簡單物件（即建立和更新）。它不用於載入大量資料或批處理作業。
   * 不支援使用 API 來讀取用於自訂應用程式的資料
* API 呼叫以每秒 15 次或每天 15 萬次為上限

### 批次傳訊伺服器大小調整

* 可擴展以處理每小時多達 2.5M 訊息

### 即時傳訊伺服器大小調整

* 每小時最多可發送 50k 訊息
* 預設會布建兩個即時傳訊伺服器。能夠擴展至最多八個即時傳訊伺服器。

### SMS 設定

* Campaign 提供與簡訊提供者整合的功能。提供者由客戶採購，並與行銷活動整合，以傳送 SMS 訊息
* 透過 SMPP 通訊協定支援
* 簡訊有三(3)種，Adobe 皆可支援：
   * SMS MT（行動已終止）:由 Adobe Campaign 透過 SMPP 提供者向行動電話發出的簡訊。
   * SMS Mo（行動產生）:行動裝置透過 SMPP 提供者傳送至 Adobe Campaign 的簡訊。
   * SMS SR（狀態報表）、DR 或 DLR（傳送回執）:行動裝置透過 SMPP 提供者傳送至 Adobe Campaign 的回執，指出 SMS 已成功接收。Adobe Campaign 也可能會收到 SR，指出無法傳送訊息，且通常包含錯誤的說明。

### 行動推播設定

* 兩種支援的推播通知與行動裝置整合方法：
   * Experience Platform Mobile SDK (推薦)
   * Campaign 行動 SDK
* Experience Platform Mobile SDK 路由：
   * 運用 Adobe 標籤和 Campaign Classic 擴充功能，設定您與 Experience Platform Mobile SDK 的整合
   * 需要 Adobe 標籤和資料收集的實用知識
   * 在 Android 和 iOS 中均需推播通知的行動開發體驗，才能部署 SDK、與 FCM (Android) 和 APNS (iOS) 整合以取得推播代號、設定應用程式以接收推播通知並處理推播互動
* Campaign 行動 SDK
   * 聯絡 Adobe 客戶服務以取得存取權
   * 請遵循 [Campaign SDK 文件](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-push-notifications/integrating-campaign-sdk-into-the-mobile-application.html?lang=zh-Hant)了解如何安裝和設定 SDK

   >[!IMPORTANT]
   >如果您部署 Campaign SDK，且正與其他 Experience Cloud 應用程式合作，則需要使用 Experience Platform Mobile SDK 來收集資料。這是不同的 SDK，需要與 Campaign SDK 一起安裝

<br>

## 實施步驟

請參閱實作 Adobe Campaign v7 的[快速入門手冊](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/starting-with-adobe-campaign/about-adobe-campaign-classic.html?lang=zh-Hant)


## 相關文件

* [Campaign v7 文件](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=zh-Hant)
* [Campaign v7 產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/adobe-campaign-managed-cloud-services.html)
* [Experience Platform Tags 文件](https://experienceleague.adobe.com/docs/launch.html?lang=zh-Hant)
* [Experience Platform Mobile SDK 文件](https://experienceleague.adobe.com/docs/mobile.html?lang=zh-Hant)
