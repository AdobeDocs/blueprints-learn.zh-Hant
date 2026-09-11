---
hold: true
title: 標籤
description: 將關聯式資料倉儲表格標示為XDM Individual Profile、Experience Event或Lookup類別，作為LID方法的一部分。
doc-type: article
solution: Experience Platform
exl-id: 332ead7a-ca6e-4e30-bb35-8419c060c596
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---


# 標籤

## 講座

在本影片中，您將會瞭解如何使用Connection 5G ERD作為範例，將關聯式表格標示為XDM Individual Profile (P)、Experience Event (E)或Lookup (L)表格。

>[!VIDEO](https://video.tv.adobe.com/v/3459087/?quality=12&learn=on)



## 實驗室詳細資訊

使用「個別設定檔」、「體驗事件」和「查詢」表格的適當XDM類別標籤，標示「連線5G資料倉儲ERD」和「串流ERD」中的表格。

執行實驗室時，請牢記下列事項：

- **個人設定檔（特徵） -**&#x200B;會唯一描述個人特徵（例如姓名、電子郵件、地址、偏好設定等）
- **體驗事件（行為） -**&#x200B;說明個人與品牌/公司的互動和接觸點（例如網頁造訪、購買、客服中心互動、應用程式提交等）
- **查詢（支援） -**&#x200B;提供其他內容資訊，以支援個人設定檔或體驗事件



## 步驟1. 標籤XDM個別設定檔表格

1. 識別代表客戶資料倉儲ERD和客戶串流ERD中個別人員的所有來源表格。
1. 以「**P**」標籤每個資料表，表示它屬於XDM個別設定檔類別的一部分

>[!NOTE]
>
>僅標籤唯一代表個人特徵的表格



## 步驟2. 標籤XDM體驗事件表格

1. 識別在Connection 5G資料倉儲ERD和串流ERD中代表個人行為的所有來源表格。
1. 以&quot;**E**&quot;標籤每個表格，表示它屬於XDM體驗事件類別的一部分。

>[!NOTE]
>
>僅標籤唯一代表個人行為的表格



## 步驟3. 標籤XDM支援表格

1. 識別所有來源資料表，這些資料表代表查閱資料，並且與您在Connection 5G Data Warehouse ERD和Streaming ERD中標籤的&#x200B;**&quot;P&quot;**&#x200B;或&#x200B;**&quot;E&quot;**&#x200B;資料表直接相關。
1. 以&#x200B;**&quot;L&quot;**&#x200B;標籤每個資料表，表示它是非人員自訂XDM類別的一部分。

>[!NOTE]
>
>查閱表格只能是1個聯結層級，或是「跳躍」，遠離標示為「P」或「E」的表格



## 檢閱

以下影片檢閱Connection 5G倉儲和串流ERD的正確標籤，說明為何客戶帳戶、訂單和帳單表會標示為原樣。

>[!VIDEO](https://video.tv.adobe.com/v/3459081/?quality=12&learn=on)
