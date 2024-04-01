---
title: Campaign v8 藍圖、Campaign & Platform
description: 瞭解Campaign v8的藍圖。
solution: Campaign,Campaign v8
exl-id: 89b3a761-9cb3-4e01-8da0-043e634fa61f
source-git-commit: 16b233c7ea9077566ebf12238f0a87beec1c61ce
workflow-type: tm+mt
source-wordcount: '966'
ht-degree: 41%

---

# Campaign v8 藍圖

Adobe Campaign v8 是新一代的行銷工具，專為傳統行銷通道（例如電子郵件和直接郵件）而建置。它提供強大的 ETL 和資料管理功能，以幫助策劃和組織完美的行銷活動。其編排引擎為豐富的多點觸控行銷方案提供支援，其核心是批次型驅動歷程。

此外，它還隨附可擴充的即時傳訊伺服器，讓行銷團隊能根據來自任何 IT 系統的包含所有內容的承載傳送預先定義的訊息，以處理密碼重設、訂單確認、電子回執等更多事項。

## 使用案例

* 極為複雜的批次式傳訊程式。
* 入門和再次行銷活動。
* 直接郵件廣告、手冊和雜誌宣傳
* 簡單的交易式訊息（例如重設密碼、電子郵件收據、訂單確認等）。
* 將Campaign資料整合至Adobe Experience Platform，以進行分析及建立設定檔。
* 共用 Real-time Customer Data Platform 對象至 Campaign。

## 架構圖

進一步瞭解 [Campaign v8部署模型](https://experienceleague.adobe.com/docs/campaign/campaign-v8/config/architecture/architecture.html#ac-deployment){target="_blank"}.

### Campaign企業(FFDA)部署

<img src="assets/P4-architecture.png" alt="Campaign v8藍圖(P4)的參考架構" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

### Campaign v8 FDA部署

<img src="assets/P1-P3-architecture.png" alt="Campaign v8藍圖的參考架構(P1-P3)" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## 整合模式

| 狀況 | 說明 | 功能 |
| :-- | :--- | :--- |
| [[!DNL Real-time Customer Data Platform] 具有Adobe [!DNL Campaign]](rtcdp-and-campaign-v8.md) | 展示Adobe Experience Platform及其即時客戶設定檔和集中式細分工具如何與Adobe搭配使用 [!DNL Campaign] 提供個人化交談 | <ul><li>從共用設定檔和對象 [!DNL Real-Time CDP] 至Adobe [!DNL Campaign] 透過使用雲端儲存空間檔案交換和Adobe [!DNL Campaign] 擷取工作流程 </li><li>輕鬆將客戶對話中的傳遞和互動資料分享回 [!DNL Real-Time CDP] 從Adobe [!DNL Campaign] 增強Real-Time Customer Profile並就傳訊行銷活動提供跨管道報告</li></ul> |
| [[!DNL Journey Optimizer] 具有Adobe [!DNL Campaign]](ajo-and-campaign.md) | 顯示如何使用Adobe Journey Optimizer來利用即時客戶個人檔案及利用原生Adobe協調1:1體驗 [!DNL Campaign] 傳送訊息的交易式訊息系統 | 利用的即時客戶個人檔案和功能 [!DNL Journey Optimizer] 在利用Adobe的原生即時傳訊功能的同時，協調當下的體驗 [!DNL Campaign] 進行最後一哩通訊<br><br>考量事項：<br><ul><li>可透過即時消息伺服器每小時發送最多 1M 訊息<li>不從執行任何節流 [!DNL Journey Optimizer] 因此請確定售前企業架構師的技術審查</li><li>Campaign v8 承載不支援決策管理</li></ul> |

## 先決條件

此Blueprint有下列必要條件。

### 應用程式伺服器和即時傳訊伺服器

* Adobe [!DNL Campaign] 使用者端主控台必須與 [!DNL Campaign] v8軟體。 它是基於 Windows 的客戶端，使用標準 Internet 協定（SOAP、HTTP 等）。請確定您的組織已啟用必要權限，以分發、安裝及執行軟體

* IP位址允許清單：
   * 識別所有使用者在存取使用者端主控台期間使用的IP範圍。
   * 識別允許哪些企業系統與Real-Time Messaging Server通訊，並確定它們具有您可以允許清單的靜態指派IP或範圍。
   * 這可透過「行銷活動控制面板」來設定及控制。
* sFTP金鑰管理：
   * 具有可與 Campaign 提供的 sFTP 搭配使用的 SSH 公開金鑰。這可透過「行銷活動控制面板」來設定及控制。

### 電子郵件

* 讓子網域準備好用來傳送訊息。
* 子網域可以完全委派給Adobe（建議），或可以使用CNAME指向Adobe特定的DNS伺服器（自訂）。
* 每個子網域都需要Google TXT記錄以確保良好的傳遞能力。

### 行動裝置推送

* 讓行動開發人員部署、設定和建置行動應用程式。
* Adobe 僅提供 SDK 來收集來自 FCM (Android) 和 APNS (iOS) 以將訊息承載傳送至其伺服器的必要資訊。客戶應負責行動應用程式的程式碼、部署、管理和除錯。

### 網頁應用程式（可選）

* 可以委派Campaign託管取消訂閱和登陸頁面的其他子網域。
* 強烈建議使用SSL憑證。

## 護欄

護欄如下所述。

### 應用程式伺服器大小調整

* 儲存空間可擴充至2億個設定檔，並有可能擴充至1B個設定檔。
* 透過Adobe設定和控制使用者存取 [!DNL Admin Console].
* 資料載入到 [!DNL Campaign] 應透過批次檔案完成：
   * API 資料載入支援主要用於管理資料庫內的個人資料或簡單物件（即建立和更新）。它不用於載入大量資料或批處理作業。
   * 不支援使用 API 來讀取用於自訂應用程式的資料
   * 透過 API 載入的資料會儲存在應用程式資料庫中，然後每小時複製到雲端資料庫
* API呼叫數上限。 進一步瞭解 [Adobe Campaign產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/adobe-campaign-managed-cloud-services.html){target="_blank"}.

### 批次傳訊伺服器大小調整

* 可擴展以處理每小時多達 2000 萬條訊息

### 即時傳訊伺服器大小調整

* 每小時最多可發送 100 萬條消息
* 預設會布建兩個即時傳訊伺服器。能夠擴展至最多八個即時傳訊伺服器。

### SMS 設定

* Campaign 提供與簡訊提供者整合的功能。提供者由客戶採購，並與Campaign整合，用於傳送SMS訊息。
* 透過SMPP通訊協定提供支援。
* 簡訊有三(3)種，Adobe 皆可支援：
   * SMS MT （已終止行動裝置）：Adobe發出的SMS [!DNL Campaign] 透過SMPP提供者使用行動電話。
   * SMS MO （行動原始）：行動傳送給Adobe的SMS [!DNL Campaign] 透過SMPP提供者。
   * SMS SR （狀態報表）或DR或DLR （交貨收貨）：行動裝置傳送給Adobe的退貨收貨 [!DNL Campaign] 透過SMPP提供者指出已成功接收簡訊。 Adobe [!DNL Campaign] 也可能收到指出訊息無法傳送的SR，通常附有錯誤說明。

## 實施步驟

請參閱快速入門手冊， [實作 Adobe Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/config/implement/implement.html?lang=zh-Hant)

## 相關文件

* [Campaign v8 文件](https://experienceleague.adobe.com/docs/campaign-v8.html)
* [Campaign v8 產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/adobe-campaign-managed-cloud-services.html)
* [Experience Platform Tags 文件](https://experienceleague.adobe.com/docs/launch.html)
* [Experience Platform Mobile SDK 文件](https://experienceleague.adobe.com/docs/mobile.html)
