---
title: 購買後的興奮感
description: 瞭解如何建置事件導向的購買後歷程，以觸發包含協力廠商API動態追蹤詳細資訊的送貨通知電子郵件。
doc-type: overview-page
solution: Experience Platform
exl-id: 570dc378-e7a3-4895-8f14-89d420b6b340
source-git-commit: df6c1852a6e0357dc9f166c88e77dcf9d334f955
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%
---

# 購買後的興奮感

## 先決條件

>[!WARNING]
>
>下列Labs必須在開始本實驗前完成

- **Postman安裝程式** **—>** [Postman安裝](../../postman-setup/postman-installation.md)
- **資料存放區 — 動作中的關聯存放區** **—>** [設定檔目標Dimension](../../data-stores/relational-store-in-action/profile-target-dimension.md)
- **資料存放區 — 設定電子郵件通道 — >** [設定設定檔](../../data-stores/configure-email-channels/configure-for-profile.md)
  *（此步驟最多需要3小時才能完成）*

如果您尚未這麼做，請立即完成這些步驟

>[!CAUTION]
>
>本實驗需要在沙箱中委派給Adobe的子網域。 如果您是自學型且還沒有設定，請參閱[設定](../../setup.md)。

## Lab概述

在這段影片中，您會瞭解購買後興奮的使用案例如何對應到歷程，逐步解說重要的思考問題和架構，以便在訂單送貨後傳送個人化送貨通知。

>[!VIDEO](https://video.tv.adobe.com/v/3491146/)

## 學習目標

- 建立從單一事件開始的歷程
- 設定並設定自訂動作以呼叫第三方系統，以傳回歷程中使用的資訊
- 透過在事件裝載中串流來執行歷程
- 測試和偵錯設定檔與歷程
- 透過報告和記錄檔驗證預期的體驗
- 在簡單的電子郵件中設定個人化，並檢視其運作情況



## 使用案例說明

客戶下訂單時，您想要傳送包含訂單詳細資料的確認訊息。  訂單出貨後，您想要觸發第二則訊息，其中包含從第三方API動態擷取的追蹤資訊。

**索引鍵圖說文字：**

- 初始訂單確認通常會實施為交易式訊息，因為客戶不想在下單後等待確認。
- 訂單送貨通知也可以使用交易式訊息實施，但可在歷程中建置，以便允許自訂動作擷取送貨資訊並增強客戶溝通。

>[!NOTE]
>
>在本實驗中，您只會建立「已出貨訂單」訊息，並略過「訂單確認」訊息。
