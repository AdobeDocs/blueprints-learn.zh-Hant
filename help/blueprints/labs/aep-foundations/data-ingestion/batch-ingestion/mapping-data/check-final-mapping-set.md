---
title: 檢查最終對應集
description: 將客戶帳戶結構的簡單和計算欄位對應與預期的最終對應集進行比較。
doc-type: article
solution: Experience Platform
exl-id: d1521d08-1ccb-405f-b728-a2777598cb9f
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---


# 檢查最終對應集

&#x200B;> [!NOTE]
>
>如果您來自串流擷取實驗室，請按一下以下連結以繼續該實驗室的下一個步驟：
>
>[串流擷取實驗室 — 檢查最終對應集](../../stream-ingestion/check-final-mapping-set.md)



## 簡單對應

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

&#x200B;> [!NOTE]
>
>在繼續之前，請確定您的最終對應符合下面顯示的內容。



## 計算的對應

| 計算欄位 | XDM欄位 |
| ------------------------------------------------------------------------------------------------------------------------------------- | -------------------------- |
| iif（sms\_optIn == null或sms\_optIn == &quot;&quot;， &#39;n&#39;， sms\_optIn） | consents.marketing.sms.val |
| concat(date\_part(&quot;month&quot;， date(birth\_Date，&quot;M/d/yyyy&quot;))。toString()， &quot;-&quot;， date\_part(&quot;day&quot;， date(birth\_Date，&quot;M/d/yyyy&quot;))。toString()) | person.birthDayAndMonth |
| date\_part(&quot;yyyy&quot;，date(birth\_Date，&quot;M/d/yyyy&quot;)) | person.birthYear |

&#x200B;> [!NOTE]
>
>在繼續之前，請確定您的最終對應符合下面顯示的內容
