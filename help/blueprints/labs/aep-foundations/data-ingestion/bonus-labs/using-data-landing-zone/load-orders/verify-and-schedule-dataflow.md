---
title: 驗證及排程資料流
description: 驗證完整的「訂單」對應集、預覽輸出，以及排程每15分鐘執行一次資料流。
doc-type: article
solution: Experience Platform
exl-id: b7f0c43b-092c-45ba-b95b-27cb4a49d110
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 7%

---


# 驗證及排程資料流

## 仔細檢查對應集

| # | Source欄 | XDM欄 |
| -- | ------------------------------------------- | -------------------------------------------------------- |
| 1 | orderstatus | eventtype |
| 2 | lastOrderStatusUpdate | timestamp |
| 3 | orderID | order.orderID |
| 4 | orderDate | order.orderDate |
| 5 | orderTotal | order.priceTotal |
| 6 | paymentType | order.payment.paymentType |
| 7 | paymentAmount | order.payment.paymentAmount |
| 8 | paymentCurrencyCode | order.payment.currencyCode |
| 9 | paymenttransactionid | order.payment.transactionID |
| 10 | plan.ID | order.\_devbc.plan.planID |
| 11 | customerID | \_devbc.customerID |
| 12 | 個人電子郵件 | \_devbc.personalEmail |
| 13 | storeID | store.storeID |
| 14 | shippingStreetAddress | shipping.address.street1 |
| 15 | shippingCity | shipping.address.city |
| 16 | shippingState | shipping.address.state |
| 17 | shippingZip | shipping.address.postalCode |
| 18 | shippingmethod | shipping.shippingMethod |
| 19 | shippingAmount | shipping.shippingAmount |
| 20 | shippingDestination | shipping.shippingDestination |
| 21 | billingStreetAddress | billing.address.street1 |
| 22 | 帳單城市 | billing.address.city |
| 23 | billingState | billing.address.state |
| 24 | billingZip | billing.address.postalCode |
| 25 | products\[\*] | productListItems\[\*] |
| 26 | 產品\[\*].productID | - productListItems\[\*].\_id - productListItems\[\*].SKU |
| 27 | products\[\*].make | productListItems\[\*].\_devbc.make |
| 28 | products\[\*].model | productListItems\[\*].\_devbc.model |
| 29 | products\[\*].price | productListItems\[\*].priceTotal |
| 30 | concat(orderID， &quot;-&quot;， lastOrderStatusUpdate) | \_id |
| 31 | &quot;inStore&quot; | order.\_devbc.acqSource |



## 預覽對應輸出

1. 預覽對應輸出。 捲動所有屬性，確保右側任何屬性旁邊都沒有紅色驚歎號。

   ![任何對應屬性上的預覽對應畫面都沒有錯誤](assets/verify-and-schedule-dataflow-preview-mapping-screen.png "預覽對應畫面看起來像這樣")

1. 在預覽的左側導覽中，選取&#x200B;**productListItems**&#x200B;物件陣列。 右側會更新為只顯示該物件陣列中的屬性。

>[!NOTE]
>
>請注意，**productListItems.currencyCode**&#x200B;和&#x200B;**productListItems.quantity**&#x200B;會自動填入（即使在移除對應之後）。 發生此狀況是因為作為父物件的&#x200B;**productListItems**&#x200B;已經對應。

![在移除重複覆寫之後完成productListItems的對映畫面](assets/verify-and-schedule-dataflow-completed-mapping-screenshot.png "完成的對應看起來會類似於下列熒幕擷圖")

## 排程執行

1. 將頻率設定為[分鐘]並將間隔設定為[15]，以將此排程設定為每15分鐘執行&#x200B;****。 檢閱流程，然後按一下「完成」。

   >[!CAUTION]
   >
   >請確認您的排程已設為15分鐘。 如果您將執行排程為&#x200B;**執行一次**，則即使您稍後對對應進行變更，也無法再次執行。

1. 資料流執行不會立即開始，而且需要幾分鐘的時間。 因此，上次資料流執行狀態已設定為&quot;*沒有執行*&quot;。

1. 幾分鐘後，資料流成功。 請注意&#x200B;**上次資料流執行狀態**&#x200B;和&#x200B;**上次資料流執行日期**。

1. 按一下資料流名稱以取得資料流執行清單。 應擷取10筆記錄。

1. 按一下「資料流執行開始」時間，檢視錯誤診斷詳細資料。

1. 在左側導覽列中，前往Platform中的資料集，然後按一下&#x200B;**訂單 — 您的名稱這裡**

1. 按一下&#x200B;**預覽資料集。**
