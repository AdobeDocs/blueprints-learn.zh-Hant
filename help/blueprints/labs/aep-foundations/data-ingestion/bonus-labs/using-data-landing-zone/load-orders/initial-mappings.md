---
title: 初始對應
description: 使用計算欄位運算式，手動對應Experience事件資料集的必要_id和時間戳記欄位。
doc-type: article
solution: Experience Platform
exl-id: 4052d104-bf0c-4b2d-a298-8075279aeaf8
source-git-commit: 0b33b2740ee7f5af73d64f217b4475650c1d28a0
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---


# 初始對應

如同上一個練習，您將需要驗證對應，並在某些情況下修改對應。

## 驗證ML建議

1. 在「對應」步驟中，「ML建議」會自動對應大部分的屬性。 不過，您也會看到數個錯誤。 初始畫面看起來可能類似下文。

![對應畫面將_id和時間戳記顯示為ML](assets/initial-mappings-id-timestamp-unmapped-fields.png "_id不建議的未對應欄位，時間戳記是ML建議程式不會產生")對應的兩個欄位

>[!NOTE]
>
>由於我們是第一次對應體驗事件資料集，請注意，根據預設，絕不會為Experience事件建議或對應&#x200B;**\_id**&#x200B;和&#x200B;**timestamp**。 您必須手動確定已正確對應這些專案。

## 對應\_id、時間戳記和順序。\_devbc.acqSource欄位

1. 若要對應&#x200B;**\_id，**&#x200B;請寫入下列計算欄位運算式，然後按一下預覽

   ```none
   concat(orderID, "-", lastOrderStatusUpdate)
   ```

   ![已準備儲存對應_id的計算欄位](assets/initial-mappings-calculated-field-for-id-mapping.png "對應_id的計算欄位將會看起來類似這樣。 按一下[儲存]儲存計算欄位")

   ![將計算欄位對應到_id屬性](assets/initial-mappings-map-calculated-field-to-id.png "將計算欄位對應到_id")

1. 請確定目標結構描述中的&#x200B;**timestamp**&#x200B;欄位已對應到下列計算欄位：

   ```none
   lastOrderStatusUpdate
   ```

   ![時間戳記對應的計算欄位運算式預覽](assets/initial-mappings-expression-preview.png "請撰寫下列運算式，然後按一下[預覽]。 請注意，此值區分大小寫，必須完全以此方式撰寫")

   ![將計算欄位運算式&quot;inStore&quot;對應到order._devbc.acqSource](assets/initial-mappings-map-instore-expression-to-acqsource.png)

1. 將計算欄位運算式&#x200B;**&quot;inStore&quot;**&#x200B;對應至&#x200B;**order.\_devbc.acqSource**

![正在寫入「inStore」計算欄位運算式，然後按一下[預覽]](assets/initial-mappings-write-instore-expression-preview.png "寫入下列運算式，然後按一下[預覽]。 請注意，此值區分大小寫，必須完全以此方式撰寫")

## 處理重複的對應

如果對應畫面現在抱怨有重複的對應，例如&#x200B;**orderStatus**&#x200B;對應到&#x200B;**order.\_devbc.acqSource，**&#x200B;請按一下「 — 」圖示以移除對應。

>[!NOTE]
>
>請記住，多個輸入欄位無法對應至相同的輸出欄位，因為這會使對應變得模稜兩可。 但單一輸入欄位可以對應到XDM結構描述中的多個輸出欄位。

![orderStatus對應至order._devbc.acqSource的重複對應警告](assets/initial-mappings-duplicate-mapping-warning.png "orderStatus對應至order._devbc.acqSource")的重複對應



![建立計算欄位後，order._devbc.acqSource出現重複對應警告](assets/initial-mappings-duplicate-mapping-for-acqsource.png "order._devbc.acqSource出現重複對應，因為我們已建立計算欄位並已對應至該欄位。")
