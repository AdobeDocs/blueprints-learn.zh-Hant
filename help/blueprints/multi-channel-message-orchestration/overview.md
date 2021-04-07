---
title: '多通道消息協調 '
description: 跨螢幕提供個別、及時的客戶體驗。
solution: Experience Platform
kt: null
thumbnail: null
exl-id: 273d024f-a220-4336-89f2-e3bffafcdc37
translation-type: tm+mt
source-git-commit: 844fff1cefe367575beb5c03aa0f0d026eb9f39b
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---

# 多通道消息協調

多通道訊息協調功能顯示品牌如何透過電子郵件、簡訊和行動提醒等通道主動吸引客戶並與其溝通。

協調工具可與其他互動通道（例如與傳入通道）整合，以便與其他通道的決策引擎共用受眾狀態，以利網頁和行動個人化。 各種因素都有助於決定要使用哪些應用程式和部署選項，例如客戶互動是以觸發器為基礎還是排程，定位和個人化需要哪些資料等等。 這些因素在構建消息協調功能時產生了各種可能的場景和部署選項。

## 藍圖


| Blueprint | 說明 | Experience Cloud應用程式 |
|---|---|---|
| **批處理和交易傳訊** | <ul><li>製作並執行排程和批次傳出促銷活動</li><li>傳遞交易訊息</li></ul> | <ul><li>Adobe Campaign Classic和Managed Services</li><li>Adobe Campaign Standard</li></ul> |
| **[批次訊息與Adobe Experience Platform](batch-messaging.md)** | <ul><li>使用Adobe Experience Platform作為客戶個人檔案和細分的中心，執行排程和批次傳訊促銷活動</li></ul> | <ul><li>即時客戶資料平台</li><li>Adobe Campaign Classic、Managed Services或Campaign Standard</li><li>支援的協力廠商訊息提供者</li></ul> |
| **[觸發訊息與Adobe Experience Platform](triggered-messaging.md)** | <ul><li>使用Adobe Experience Platform作為串流資料、客戶個人檔案和細分的中心，並具備串流歷程協調與訊息傳送的Journey Orchestration，執行觸發式與串流訊息傳送</li></ul> | <ul><li>Adobe Experience Platform</li><li>Journey Orchestration</li><li>Adobe Campaign或其他第三方訊息傳送應用程式</li></ul> |
