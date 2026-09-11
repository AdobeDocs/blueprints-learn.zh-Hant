---
hold: true
title: 物件複製對應
description: 設定產品陣列的物件副本對應，然後在預設副本上方新增及移除欄位層級覆寫。
doc-type: article
solution: Experience Platform
exl-id: 762d0e19-ed1c-4f4d-91ec-a962bd6277a7
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---


# 物件複製對應

在本節中，您將新增物件複製對應並建立一些覆寫。

## 傳遞對應

按一下[新增欄位型別]，新增下列傳遞對應與&#x200B;**products\[\*]**&#x200B;和&#x200B;**products\[\*].productID**，並在此為每一列新增欄位。 由於ML Recommendations，某些可能已存在。

| Source欄 | XDM欄 |
| ----------------------- | ------------------------- |
| orderstatus | eventtype |
| lastOrderStatusUpdate | timestamp |
| products\[\*] | productListItems\[\*] |
| 產品\[\*].productID | productListItems\[\*].SKU |

>[!NOTE]
>
>請注意，**products\[\*]**&#x200B;正在物件欄位之間執行1-1欄位對應，而明確欄位對應&#x200B;**products\[\*].productID**&#x200B;正在覆寫預設復本。

>[!NOTE]
>
>除了&#x200B;**productListItems\[\*].\_id**&#x200B;之外，**products\[\*].productID**&#x200B;也對應到&#x200B;**productListItems\[\*].SKU**。 這是將單一輸入欄位對應到XDM結構描述中多個輸出欄位的範例。 保持對應。

1. 保留對應&#x200B;**products\[\*].price**&#x200B;至&#x200B;**productListItems\[\*].priceTotal**

## 在特定欄位上新增覆寫

1. 覆寫物件副本對應，方法為
   1. 將&#x200B;**products\[\*].make**&#x200B;對應至&#x200B;**productListItems\[\*].\_devbc.make**
   2. 將&#x200B;**products\[\*].model**&#x200B;對應至&#x200B;**productListItems\[\*].\_devbc.model**

## 刪除特定欄位的覆寫

1. 請注意，**productListItems.currencyCode**&#x200B;和&#x200B;**productListItems.quantity**&#x200B;已自動填入。
1. 移除&#x200B;**productListItems\[\*].quantity**&#x200B;與&#x200B;**productListItems\[\*].currencyCode**&#x200B;對應。
1. 覆寫不會發生，而且物件複製會透過傳遞欄位接管。


## 物件副本對應、覆寫和刪除的摘要

| Source欄 | XDM欄 | 動作 |
| -------------------------- | ----------------------------------- | -------------------------------------- |
| products\[\*] | productListItems\[\*] | `Add` |
| 產品\[\*].productID | productListItems\[\*].SKU | `Add` |
| 產品\[\*].productID | productListItems\[\*].\_id | `No change` |
| products\[\*].make | productListItems\[\*].\_devbc.make | `Change` |
| products\[\*].model | productListItems\[\*].\_devbc.model | `Change` |
| products\[\*].price | productListItems\[\*].priceTotal | `No change` |
| 產品\[\*].quantity | productListItems\[\*].quantity | `Remove` |
| products\[\*].currencyCode | productListItems\[\*].currencyCode | `Remove` |

## 驗證對應

您應該驗證兩組對應。 移除2個之後，您總共應該有6個對應。



新增物件復本覆寫後![productListItems的結果對應會覆寫](assets/object-copy-mappings-resultant-mappings-for-productlistitems.png "ProductListItems\[*]的結果對應應該像這樣")

![物件復本覆寫後productListItems結果對應的第二個檢視](assets/object-copy-mappings-resultant-mappings-for-productlistitems--2.png)
