---
title: 建立Edge受眾
description: 建立並發佈Edge評估對象與批次同等專案，以比較每個對象對即時傳入事件的回應方式。
doc-type: article
solution: Experience Platform
exl-id: 79265a8f-81dd-41a3-89c5-c6646e435328
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---


# 建立Edge受眾

當裝載（例如頁面檢視）來自使用者端（例如網頁SDK）至Edge時，此對象將用於授與某人資格。

>[!NOTE]
>
>我們通常會在Edge上評估受眾，以便在Personalization中變換使用對象。 如果我們沒有在Edge上執行Personalization，那麼我們只需將對象評估為集線器上的串流。

## 建立對象

1. 在左側欄中按一下「對象」
1. 然後按一下畫面右上角的「建立對象」
1. 然後按一下「建置規則」



![具有「建立對象」按鈕和「建置規則」選項的「對象」頁面反白顯示](assets/create-edge-audience-create-audience-step-1.png)



![已開啟用於建立新對象的建置規則畫布](assets/create-edge-audience-create-audience-step-2.png)



## 將受眾轉換為規則

1. 前往&#x200B;**對象**&#x200B;並按一下&#x200B;**Experience Platform**&#x200B;資料夾
1. 將「n」拖放名為&#x200B;**dep：任何事件串流（一小時內）**&#x200B;的對象到畫布上

   ![將dep： Any Event Streaming （一小時內）對象拖曳至規則產生器畫布](assets/create-edge-audience-drag-audience-to-canvas.png)



1. 按一下下方顯示的&#x200B;**圖示**，然後按一下&#x200B;**轉換**，將對象轉換為畫布中的一組規則

畫布中的![轉換圖示，用來將對象轉換為一組規則](assets/create-edge-audience-convert-to-rules-icon.png)

## 更新事件規則

對事件規則進行下列變更（您可能需要展開事件才能檢視）

1. 最近
1. 15
1. 分鐘

![事件規則已設定為在過去15分鐘內觸發](assets/create-edge-audience-update-event-rules.png)

## 發佈區段

1. 將區段的名稱更新為&#x200B;**任何事件Edge （15分鐘內）**
1. 將評估方法更新至Edge
1. 發佈區段

![在發佈前顯示Edge評估方法的區段詳細資料](assets/create-edge-audience-publish-segment.png)

## 建立批次評估區段

對建立的邊區段重複您剛才的相同步驟，但改用下列資訊：

>[!NOTE]
>
>我們將建立批次對象，以便您看到即使事件傳遞到Edge，任何儲存為批次評估的對象都不會以串流方式評估。

事件規則：

- 最近
- 1
- 日



區段詳細資料：

- 名稱 — > **任何事件批次（1天內）**
- 評估方法 — >批次
