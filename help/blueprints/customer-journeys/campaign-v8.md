---
title: 促銷活動v8 Blueprint、促銷活動與AEP
description: Adobe Campaign v8是新一代的宣傳工具，專為傳統行銷管道（例如電子郵件和直接郵件）而建置。 它提供強大的ETL和資料管理功能，以幫助策劃和組織完美的促銷活動。 其協調引擎提供豐富的多點接觸行銷計畫，核心著重於批次導向歷程。  此外，它還隨附可擴充的即時訊息伺服器，讓行銷團隊能根據來自任何IT系統的包含所有內容的裝載，傳送預先定義的訊息，以處理密碼重設、訂單確認、電子回執等更多事項。
solution: Campaign,Campaign v8
exl-id: 89b3a761-9cb3-4e01-8da0-043e634fa61f
source-git-commit: c79422931cb4305347a4034ae1cb6bac2be1e229
workflow-type: tm+mt
source-wordcount: '1147'
ht-degree: 3%

---

# 促銷活動v8 Blueprint

Adobe Campaign v8是新一代的宣傳工具，專為傳統行銷管道（例如電子郵件和直接郵件）而建置。 它提供強大的ETL和資料管理功能，以幫助策劃和組織完美的促銷活動。 其協調引擎提供豐富的多點接觸行銷計畫，核心著重於批次導向歷程。  此外，它還隨附可擴充的即時訊息伺服器，讓行銷團隊能根據來自任何IT系統的包含所有內容的裝載，傳送預先定義的訊息，以處理密碼重設、訂單確認、電子回執等更多事項。

<br>

## 使用案例

* 高度複雜的基於批處理的報文傳送程式
* 引導與再行銷活動
* 直接郵件廣告、手冊和雜誌宣傳
* 簡單的交易式訊息（例如密碼重設、電子郵件接收、訂單確認等）
* 將Campaign資料整合至Adobe Experience Platform以進行分析和建立設定檔
* 共用Real-time Customer Data Platform對象至Campaign。

<br>

## 架構

<img src="assets/campaign-v8-architecture.svg" alt="Campaign v8 Blueprint的參考架構" style="width:100%; border:1px solid #4a4a4a" />

<br>

## 整合模式

| 狀況 | 說明 | 功能 |
| :-- | :--- | :--- |
| [具有Adobe Campaign的即時客戶資料平台](rtcdp-and-campaign-v8.md) | 展示Adobe Experience Platform及其即時客戶個人檔案和集中化細分工具如何與Adobe Campaign搭配使用，以提供個人化的對話 | <ul><li>使用雲端儲存檔案交換和Adobe Campaign擷取工作流程，共用從Real-Time CDP到Adobe Campaign的設定檔和閱聽眾 </li><li>輕鬆將客戶對話的傳遞和互動資料分享回Adobe Campaign的即時CDP，以增強即時客戶個人檔案，並提供訊息行銷活動的跨管道報表</li></ul> |
| [Journey Optimizer搭配Adobe Campaign](ajo-and-campaign.md) | 顯示如何使用Adobe Journey Optimizer利用即時客戶設定檔來協調1:1體驗，並運用原生Adobe Campaign交易訊息系統來傳送訊息 | 運用Journey Optimizer的即時客戶個人檔案和強大功能，協調即時體驗，同時運用Adobe Campaign的原生即時訊息傳送功能進行最後一英里的通訊<br><br>考量事項：<br><ul><li>可通過即時消息伺服器每小時發送最多100萬條消息<li>不會從Journey Optimizer執行限制，以確保售前企業架構師的技術審查</li><li>Campaign v8裝載不支援決策管理</li></ul> |

<br>

## 先決條件


### 應用程式伺服器和即時消息伺服器

* 必須有Adobe Campaign用戶端主控台才能與Campaign v8軟體互動和使用。 它是基於Windows的客戶端，使用標準Internet協定（SOAP、HTTP等）。 請確定您的組織已啟用必要權限，以分發、安裝及執行軟體

* IP位址允許清單
   * 識別所有使用者在存取用戶端主控台期間將利用的IP範圍
   * 標識將允許哪些企業系統與即時消息伺服器對話，並確保它們具有靜態分配的IP或範圍，您可以允許列出
   * 這可透過「促銷活動控制面板」來設定及控制
* sFTP金鑰管理
   * 具有可與Campaign提供的sFTP搭配使用的SSH公開金鑰。 這可透過「促銷活動控制面板」來設定及控制。

### 電子郵件

* 已準備好要用於訊息傳送的子網域
* 子網域可以完全委派給Adobe（建議），或CNAME可用來指向Adobe特定的DNS伺服器（自訂）
* 每個子網域都需要Google TXT記錄，以確保良好的傳遞能力

### 行動裝置推送

* 讓行動開發人員可部署、設定和建置行動應用程式
* Adobe僅提供SDK來收集來自FCM(Android)和APNS(iOS)以傳送訊息裝載至其伺服器的必要資訊。 客戶應負責如何對行動應用程式進行編碼、部署、管理和除錯

### 網頁應用程式（可選）

* 可以為托管的取消訂閱和登錄頁面委派其他子網域
* 強烈建議使用SSL憑證

<br>

## 護欄

### 應用程式伺服器大小調整

* 儲存可以擴展到2億個配置檔案，有可能擴展到1B配置檔案
* 透過Adobe Admin Console設定及控制使用者存取權
* 載入至Campaign的資料應透過批次檔案完成
   * API資料載入支援主要用於管理資料庫內的設定檔或簡單物件（即建立和更新）。 它不用於載入大量資料或批處理操作。
   * 不支援使用API來讀取自訂應用程式用途的資料
   * 透過API載入的資料會儲存在應用程式資料庫中，然後每小時複製到雲端資料庫
* API呼叫以每秒15次或每天15萬次為上限

### 批次傳訊伺服器大小調整

* 可擴展以處理每小時多達2000萬條報文

### 即時消息伺服器大小調整

* 每小時最多可發送100萬條消息
* 預設會布建兩個即時訊息伺服器。 能夠擴展至最多八個即時消息傳送伺服器。

### SMS設定

* Campaign提供與簡訊提供者整合的功能。 提供者由客戶採購，並與行銷活動整合，以傳送以簡訊為基礎的訊息
* 支援是透過SMPP通訊協定
* 簡訊有三(3)種，Adobe皆可支援：
   * SMS MT（已終止行動）:由Adobe Campaign透過SMPP提供者向行動電話發出的簡訊。
   * SMS MO（行動產生）:行動裝置透過SMPP提供者傳送至Adobe Campaign的SMS。
   * SMS SR（狀態報表）、DR或DLR（傳送回執）:行動裝置透過SMPP提供者傳送至Adobe Campaign的回執，指出SMS已成功接收。 Adobe Campaign也可能會收到SR，指出無法傳送訊息，且通常包含錯誤的說明。

### 行動推送設定

* Campaign v8僅支援Campaign SDK。 聯絡Adobe客戶服務以取得存取權
* 請遵循 [Campaign SDK檔案](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-push-notifications/integrating-campaign-sdk-into-the-mobile-application.html?lang=en) 了解如何安裝和設定SDK

   >[!IMPORTANT]
   >其他Experience Cloud應用程式則需使用Experience Platform行動SDK進行資料收集。 這是不同的SDK，需要與Campaign SDK一起安裝

<br>

## 實施步驟

請參閱快速入門手冊， [實作Adobe Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/implement/implement.html?lang=en)


## 相關文件

* [Campaign v8檔案](https://experienceleague.adobe.com/docs/campaign-v8.html?lang=en)
* [Campaign v8產品說明](https://helpx.adobe.com/legal/product-descriptions/adobe-campaign-managed-cloud-services.html)
* [Experience Platform標籤檔案](https://experienceleague.adobe.com/docs/launch.html?lang=zh-Hant)
* [Experience Platform Mobile SDK 文件](https://experienceleague.adobe.com/docs/mobile.html?lang=zh-Hant)
