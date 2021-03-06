---
title: 市場活動v7藍圖
description: Adobe Campaignv7是為電子郵件和直郵等傳統營銷渠道構建的宣傳工具。 它提供強大的ETL和資料管理功能，幫助制定和組織完美的活動。 其業務流程引擎為豐富的多點觸控營銷計畫提供了支援，其核心是基於批處理的驅動行程。  它還配備了即時消息伺服器，使營銷團隊能夠基於來自任何IT系統的包含所有內容的負載來發送預定義的消息，用於諸如密碼重置、訂單確認、電子回執等等。
solution: Campaign,Campaign Classic v7
exl-id: 71c808f5-59e6-4f49-a6ba-581ed508bc04
source-git-commit: 37fa3bc00175a4636766564f0b8fb847fa8a951e
workflow-type: tm+mt
source-wordcount: '1193'
ht-degree: 3%

---

# 市場活動v7藍圖

Adobe Campaignv7是為電子郵件和直郵等傳統營銷渠道構建的宣傳工具。 它提供強大的ETL和資料管理功能，幫助制定和組織完美的活動。 其業務流程引擎為豐富的多點觸控營銷計畫提供了支援，其核心是基於批處理的驅動行程。  它還配備了即時消息伺服器，使營銷團隊能夠基於來自任何IT系統的包含所有內容的負載來發送預定義的消息，用於諸如密碼重置、訂單確認、電子回執等等。

<br>

## 使用案例

* 基於批處理的消息傳遞程式
* 引導與再行銷活動
* 直郵廣告、手冊和雜誌活動
* 低容量的簡單事務性消息傳遞（即密碼重置、電子郵件接收、訂單確認等）

<br>

## 架構

<img src="assets/campaign-v7-architecture.svg" alt="市場活動v7藍圖的參考體系結構" style="width:100%; border:1px solid #4a4a4a" />

<br>

## 整合模式

| 狀況 | 說明 | 功能 |
| :-- | :--- | :--- |
| [Journey Optimizer與Adobe Campaign](ajo-and-campaign.md) | 顯示如何使用Adobe Journey Optimizer來協調利用即時客戶概要資訊的1:1體驗，並利用本機Adobe Campaign事務性消息傳遞系統來發送消息 | 利用Journey Optimizer的即時客戶概況和能力，在利用Adobe Campaign的本機即時消息傳遞功能進行最後一英里通信的同時，協調即時體驗<br><br>注意事項：<br><ul><li>通過即時消息伺服器每小時最多可發送5萬條消息<li>沒有從Journey Optimizer執行限制，因此確保售前企業架構師進行技術審查</li><li>將Campaign v7即時消息伺服器的有效負載中不支援決策管理</li></ul> |
| [Real-Time CDP與Adobe Campaign](rtcdp-and-campaign.md) | 展示Adobe Experience PlatformReal-Time CDP及其集中分割工具如何與Adobe Campaign一起進行個性化對話 | <ul><li>利用雲儲存檔案交換和Adobe Campaign接收工作流共用從Real-Time CDP到Adobe Campaign的受眾 </li><li>輕鬆地將客戶對話中的交付和交互資料共用回Adobe Campaign的即時CDP中，以增強即時客戶概要資訊並提供關於消息傳遞活動的跨渠道報告</li></ul> |

<br>

## 先決條件

### 應用伺服器和即時消息伺服器

* Adobe Campaign客戶端控制台需要交互和使用Campaign v8軟體。 它是基於Windows的客戶端，使用標準的Internet協定（SOAP、HTTP等）。 確保您在組織中啟用了分發、安裝和運行軟體所需的權限

* IP地址允許清單
   * 確定所有用戶在訪問客戶端控制台期間將利用的IP範圍
   * 標識允許哪些企業系統與即時消息伺服器通話，並確保它們具有靜態分配的IP或範圍，您可以允許清單
   * 可通過「市場活動控制面板」設定和控制
* sFTP密鑰管理
   * 使SSH公共密鑰可用於市場活動提供的sFTP。 可通過「市場活動控制面板」設定和控制此操作。

### 電子郵件

* 使子域準備好用於消息發送
* 子域可以完全委託給Adobe（推薦），也可以使用CNAME指向特定於Adobe的DNS伺服器（自定義）
* 每個子域都需要GoogleTXT記錄，以確保良好的可交付性

### 行動裝置推送

* 讓移動開發人員可以部署、配置和構建移動應用
* Adobe只提供SDK從FCM(Android)和APNS(iOS)收集必要資訊，將消息負載發送到伺服器。 如何對移動應用進行編碼、部署、管理和調試是客戶的責任

### Webapps（可選）

* 可以為托管的市場活動取消訂閱和登錄頁委託其他子域
* 強烈建議使用SSL證書

<br>

## 護欄

### 應用程式伺服器調整大小

* 儲存可擴展到1億個配置式
* 通過Adobe Admin Console（推薦）或在應用程式本身中本地設定和控制用戶訪問
* 資料載入到市場活動預期將通過批處理檔案完成
   * API資料載入支援主要用於管理資料庫中的配置檔案或簡單對象（即建立和更新）。 它不打算用於載入大量資料或類似批處理的操作。
   * 不支援使用API讀取資料以用於自定義應用程式
* API調用限制為每秒15次或每天15萬次

### 批消息伺服器調整

* 可以擴展到每小時處理多達250萬條消息

### 即時消息伺服器調整

* 每小時最多可發送5萬條消息
* 預設情況下，配置兩個即時消息伺服器。 能夠擴展到多達八個即時消息伺服器。

### SMS配置

* 市場活動提供了與SMS提供商整合的能力。 供應商由客戶採購並與用於發送基於SMS的消息的促銷活動整合
* 支援通過SMPP協定
* 有三(3)種不同的SMS,Adobe都能支援：
   * SMS MT（移動終止）:Adobe Campaign通過SMPP提供商向行動電話發送的簡訊。
   * SMS MO(Mobile Sourced):由移動端通過SMPP提供商發送給Adobe Campaign的SMS。
   * SMS SR（狀態報告）、 DR或DLR（交貨回執）:移動設備通過SMPP提供商發送給Adobe Campaign的回執，表示SMS已成功接收。 Adobe Campaign可能還會收到SR，指出無法傳遞消息，通常會提供錯誤描述。

### 移動推送配置

* 兩種支援的與移動設備整合推送通知的方法：
   * Experience Platform移動SDK（推薦）
   * 活動移動SDK
* Experience Platform移動SDK路由：
   * 利用Adobe標籤和Campaign Classic擴展設定與Experience Platform移動SDK的整合
   * 需要有關Adobe標籤和資料收集的工作知識
   * 在Android和iOS都需要具有推送通知的移動開發經驗來部署SDK，與FCM(Android)和APNS(iOS)整合以獲得推送令牌，配置應用以接收推送通知和處理推送交互
* 活動移動SDK
   * 聯繫Adobe客戶服務以獲得訪問
   * 請關注 [市場活動SDK文檔](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-push-notifications/integrating-campaign-sdk-into-the-mobile-application.html?lang=en) 瞭解如何安裝和配置SDK

   >[!IMPORTANT]
   >如果您部署市場活動SDK並正在使用其他Experience Cloud應用程式，則需要使用Experience Platform移動SDK進行資料收集。 這是另一個SDK，需要在「活動SDK」旁邊安裝

<br>

## 實施步驟

查看 [入門指南](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/starting-with-adobe-campaign/about-adobe-campaign-classic.html?lang=en) 實施Adobe Campaignv7


## 相關文件

* [市場活動v7文檔](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=zh-Hant)
* [市場活動v7產品說明](https://helpx.adobe.com/legal/product-descriptions/adobe-campaign-managed-cloud-services.html)
* [Experience Platform標籤文檔](https://experienceleague.adobe.com/docs/launch.html?lang=zh-Hant)
* [Experience Platform Mobile SDK 文件](https://experienceleague.adobe.com/docs/mobile.html?lang=zh-Hant)
