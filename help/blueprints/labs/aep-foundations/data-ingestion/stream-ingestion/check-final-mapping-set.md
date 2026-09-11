---
hold: true
title: 檢查最終對應集
description: 將串流擷取對應與預期的最終通過和計算欄位對應集進行比較。
doc-type: article
solution: Experience Platform
exl-id: 8802aaca-f566-4972-8bd6-41aca9fae9bf
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---


# 檢查最終對應集

## 傳遞對應

> [!NOTE]
>
>在繼續之前，請確定您的最終對應符合下面顯示的內容。

>[!NOTE]
>
>將\&lt;tenant-name>取代為您沙箱中的值

| Source欄位 | 目標欄位 |
| ------------------------- | --------------------------------- |
| account\_create\_date | \&lt;租使用者名稱稱>.account.createDate |
| account\_end\_date | \&lt;租使用者名稱稱>.account.endDate |
| customer\_id | \&lt;租使用者名稱稱>.customerID |
| plan\_name | \&lt;租使用者名稱稱>.plan.name |
| plan\_id | \&lt;租使用者名稱稱>.plan.planID |
| billing\_city | billingAddress.city |
| billing\_zip\_code | billingAddress.postalCode |
| billing\_state | billingAddress.state |
| billing\_street\_address | billingAddress.street1 |
| email\_optIn | consents.marketing.email.val |
| mobile\_phone | mobilePhone.number |
| 名字 | person.name.firstName |
| 姓氏 | person.name.lastName |
| 電子郵件 | personalemail.address |
| createDate | repo.createDate |
| modifyDate | repo.modifyDate |
| shipping\_city | shippingAddress.city |
| shipping\_zip\_code | shippingAddress.postalCode |
| shipping\_state | shippingAddress.state |
| shipping\_street\_address | shippingAddress.street1 |



## 計算的對應

>[!NOTE]
>
>請注意，`birth_Date`的對映與批次擷取實驗室對應不同，因為日期格式不同。  批次使用斜線`/`，而串流使用虛線`-`

| 計算欄位 | XDM欄位 |
| ----------------------------------------------------------------------------------------------------------------------------------- | -------------------------- |
| iif（sms\_optIn == null或sms\_optIn == &quot;&quot;， &#39;n&#39;， sms\_optIn） | consents.marketing.sms.val |
| concat(date\_part(&quot;mm&quot;， date(birth\_Date， &quot;yyyy-M-d&quot;))。toString()， &quot;-&quot;， date\_part(&quot;dd&quot;， date(birth\_Date， &quot;yyyy-M-d&quot;))。toString()) | person.birthDayAndMonth |
| date\_part(&quot;yyyy&quot;，date(birth\_Date，&quot;yyyy-M-d&quot;)) | person.birthYear |

> [!NOTE]
>
>在繼續之前，請確定您的最終對應符合下面顯示的內容



## 完成資料流

完成後，請按一下&#x200B;**下一步**&#x200B;按鈕，然後按一下「完成」按鈕，以使用新的對應邏輯更新資料流。

![在按一下[完成]儲存資料流之前，先檢閱資料流詳細資料](assets/check-final-mapping-set-review-and-finish-dataflow.png)



現在，您應該會看到一個畫面，顯示您建立的HTTP API帳戶以及使用該帳戶的所有相關資料流。 您建立的資料流也會顯示。
