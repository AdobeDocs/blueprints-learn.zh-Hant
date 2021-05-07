---
title: '多通道訊息協調  '
description: 在各畫面中提供個別、即時的客戶體驗。
solution: Experience Platform
kt: null
thumbnail: null
exl-id: 273d024f-a220-4336-89f2-e3bffafcdc37
translation-type: ht
source-git-commit: 9a5137c5e71946c258cb94188ee53d742396d361
workflow-type: ht
source-wordcount: '233'
ht-degree: 100%

---

# 多通道訊息協調 

多通道訊息協調 顯示品牌如何主動透過電子郵件、簡訊及手機提醒等通道與其客戶通訊。

協調工具可以透過與其他通道的決策引擎分享閱聽眾狀態來整合其他互動通道 (如傳入通道)，以進行網頁及行動個人化。有不同因素協助確認所要使用的應用程式和部署選項，例如客戶互動是否基於觸發或排程，目標定位和個人化需要哪些資料等。這些因素在構建訊息協調功能時會產生各種可能的狀況和部署選項。


| Blueprint | 說明 | Experience Cloud 應用程式 |
|---|---|---|
| **批次與異動訊息** | <ul><li>建立及執行排程的批次傳出行銷活動</li><li>傳送異動訊息</li></ul> | <ul><li>Adobe Campaign Classic 與 Managed Services</li><li>Adobe Campaign Standard</li></ul> |
| **[批次訊息傳送與 Adobe Experience Platform](batch-messaging.md)** | <ul><li>使用 Adobe Experience Platform 作為客戶個人資料與細分的中樞，以執行排程的批次訊息傳送行銷活動</li></ul> | <ul><li>[!UICONTROL 即時客戶資料平台]</li><li>Adobe Campaign Classic、Managed Services 或 Campaign Standard</li><li>支援的協力廠商訊息服務供應商</li></ul> |
| **[觸發的訊息傳送與 Adobe Experience Platform](triggered-messaging.md)** | <ul><li>使用 Adobe Experience Platform 作為串流資料、客戶個人資料與細分的中樞，以執行觸發的串流訊息傳送，使用 Journey Orchestration 串流歷程協調與訊息傳送</li></ul> | <ul><li>Adobe Experience Platform</li><li>Journey Orchestration</li><li>Adobe Campaign 或用於訊息傳送的其他協力廠商應用程式</li></ul> |
