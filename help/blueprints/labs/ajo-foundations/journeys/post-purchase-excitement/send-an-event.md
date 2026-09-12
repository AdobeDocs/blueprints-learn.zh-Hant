---
title: 傳送事件
description: 使用Postman將模擬的Order Shipped事件直接串流至中心，以觸發歷程，而非傳送至Edge。
doc-type: article
solution: Experience Platform
exl-id: a0f75f5a-e3b3-42a2-8547-f075a7661a22
source-git-commit: 0b33b2740ee7f5af73d64f217b4475650c1d28a0
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---


# 傳送事件

## 學習目標

使用Postman傳送模擬的「已送出訂單」事件以觸發歷程

## 串流至集線器與Edge

之前，我們已將事件傳送至Edge。  在某些使用案例中，我們可能有後端系統，想要在事件中串流，但不需要將其傳送至Edge。  本實驗說明如何透過&#x200B;**將訂單傳送事件串流至集線器** （亦即伺服器對伺服器，例如Commerce Server傳送至AEP，表示已傳送訂單）。

## 驗證事件不在設定檔中

1. 移至您的&#x200B;**設定檔**&#x200B;並查詢設定檔。
   - **身分名稱空間** -> `email`
   - **身分值** -> `henry.creel@emailsim.io`
1. 按一下「**事件**」標籤。
   - 應該有&#x200B;**no** `orders.shipped`個事件

## 修改API請求

若要建立API請求，您需要在API請求內文中填寫以下片段。

首先，收集下列值：

### 尋找帳戶串流端點

1. 導覽至左側邊欄中的&#x200B;**來源**，然後按一下頂端導覽列中的&#x200B;**帳戶**
1. 搜尋&#x200B;**dep： HTTP API \[raw]**，反白標示該列，並複製&#x200B;**串流端點**&#x200B;的值並儲存於您稍後可參考的位置

![dep： HTTP API [原始]帳戶列以串流端點值強調顯示](assets/send-an-event-streaming-endpoint-account-row.png "dep： HTTP API \[原始]")


### 尋找資料流ID

1. 按一下&#x200B;**dep： HTTP API \[raw]**
1. 尋找&#x200B;**dep：訂單（串流）**&#x200B;的記錄，按一下資料流連結
1. 在右邊欄複製並將&#x200B;**資料流ID**&#x200B;值儲存到您稍後可參考的位置

>[!WARNING]
>
>在列的空白處按一下。  請勿按一下藍色連結！

右側邊欄中顯示的![資料流ID值](assets/send-an-event-dataflow-id-in-right-rail.png "網頁資料流和資料集ID")



### 開啟Postman

在電腦上啟動Postman，並導覽至下列API呼叫：

- **Postman左側邊欄** —> `Collections`
- **集合** —> `AJO Bootcamp (Labs)`
- **資料夾** —> `Profile & Journey Labs`
- **API要求** —> `Ship Order Event`

位於Postman集合中的![出貨訂單事件要求](assets/send-an-event-open-ship-order-event-postman.png)



### 建立最終API請求

1. 將您先前步驟中儲存的值複製到下面反白顯示的位置。
1. 按一下&#x200B;**標頭**&#x200B;並貼入這些值（移除任何尾端空格）：
   - **紅色** —> `Streaming Endpoint URL`
   - **綠色** —> `Dataflow ID`
     - 值類似於GUID （開頭不是http）

>[!CAUTION]
>
>尚未執行！

![串流端點URL和資料流ID已貼入Postman標頭](assets/send-an-event-paste-headers-in-postman.png)

## 執行API

1. 按一下&#x200B;**儲存**&#x200B;按鈕以儲存您的API呼叫
1. 按一下&#x200B;**傳送**&#x200B;按鈕以執行您的要求

成功的呼叫應導致下列回應……

傳送Web事件後![成功回應](assets/send-an-event-successful-web-event-send.png)

## 重述

出貨單事件已成功傳送至平台
