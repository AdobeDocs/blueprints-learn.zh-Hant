---
hold: true
title: 驗證已擷取的事件
description: 確認已將訂單出貨事件擷取到設定檔中，並符合預期對象的資格。
doc-type: article
solution: Experience Platform
exl-id: c04397dd-8b5c-48a8-82b5-78188b8374f1
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---


# 驗證已擷取的事件

## 學習目標

確認事件已成功擷取至Adobe Experience Platform。

## 驗證設定檔中的事件

1. 移至您的&#x200B;**設定檔**&#x200B;並查詢您的設定檔，檢視事件是否已內嵌至設定檔中。  它會在秒數內顯示。
   - **身分名稱空間** -> `email`
   - **身分值** -> `henry.creel@emailsim.io`
2. 按一下「**事件**」標籤。 尋找`orders.shipped`事件。

![orders.shipped事件顯示在設定檔](assets/validate-event-ingested-orders-shipped-event.png)的Events標籤上

>[!WARNING]
>
>您收到任何&#x200B;**message.feedback**&#x200B;事件嗎？  這些來自歷程，通常表示失敗或排除。  按一下並檢視`reason`。
>
>您可能在生產中遇到的一些範例可能是：
>
>- EmailNoAddressFoundInProfile （您嘗試傳送電子郵件給沒有電子郵件的設定檔）
>- EmailNoConsent (您嘗試傳送電子郵件給同意設定為no的設定檔。



3. 驗證設定檔符合&#x200B;**對象**&#x200B;的資格（可能需要幾分鐘的時間）。
   - 任何活動Edge （15分鐘內）
   - 任何事件串流（15分鐘內）

![設定檔符合任何活動Edge和任何活動串流對象的資格](assets/validate-event-ingested-profile-qualified-audiences.png)



## 嘗試使用您自己的電子郵件

現在您已驗證設定檔已進入，請使用您自己的電子郵件傳送一些「訂單出貨事件」。

1. 返回Postman，尋找&#x200B;**出貨訂單事件**
2. 按一下&#x200B;**內文**&#x200B;並將&#x200B;**電子郵件地址**&#x200B;變更為您的。

![在Postman要求內文中變更的電子郵件地址](assets/validate-event-ingested-change-email-in-postman-body.png)

3. **儲存**&#x200B;並點選&#x200B;**傳送**。
4. 返回步驟1至3，並使用您的電子郵件地址進行驗證。

## 重述

事件會顯示在設定檔存放區中，而設定檔現在是尋找該事件的對象的一部分。
