---
title: 在Edge上驗證設定檔
description: 瞭解如何檢查Edge設定檔存放區和「對象成員資格」標籤，以確認Edge網路上的設定檔狀態。
doc-type: article
solution: Experience Platform
exl-id: f82ceba7-6916-49ff-8776-2d0238560df8
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 0%

---


# 在Edge上驗證設定檔

## 學習目標

確認Edge網路設定檔存放區中不存在設定檔。

## 檢查Edge設定檔

1. 按一下&#x200B;**屬性**&#x200B;標籤和&#x200B;**Edge**&#x200B;選項按鈕以檢視Edge設定檔

   ![顯示在[屬性]索引標籤上的Edge設定檔](assets/validate-profile-on-edge-attributes-tab.png)

   >[!NOTE]
   >
   >您可能會看到設定檔的「刪減」版本，其中僅包含身分，視已過去的時間而定。



2. 按一下「對象成員資格」標籤。  它將是&#x200B;**空白**。

![Edge設定檔上的空白對象會籍標籤](assets/validate-profile-on-edge-empty-audience-membership-tab.png)

>[!NOTE]
>
>**為什麼沒有Edge會籍？**
>
>我們是否應該看到&#x200B;**dep：任何事件Edge （一小時內）**&#x200B;合格？
>
>即使我們的對象進行了Edge評估，該對象不存在於Edge上，因為我們還沒有理由存在於該對象上……
>
>如果我們要使用該對象（例如Decisioning或Destinations），則對象規則會推送至Edge，而下次事件串流至Edge時，系統會評估該對象。
>
>此外，我們並未開啟Edge細分服務。



## 重述

Edge上不存在設定檔（尚）
