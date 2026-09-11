---
title: 重試失敗的資料流
description: 重試失敗的資料流執行，以便根據新資料流中更新的對應規則重新處理來源資料。
doc-type: article
solution: Experience Platform
exl-id: 83ecf037-e524-4887-b833-5ed96af40419
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '117'
ht-degree: 0%

---


# 重試失敗的資料流

若要重試工作流程，請執行下列動作：

1. 導覽至&#x200B;**來源 — >資料流 — > \[資料流名稱] -> \[執行失敗]**
1. 反白標示無法顯示右側邊欄的資料流執行。
1. 按一下&#x200B;**重試**。 重試將取得與失敗執行相關聯的資料復本，現在會將新的對應規則套用至該復本

![正在從右邊欄重試失敗的資料流執行](assets/retry-a-failed-dataflow.png)

>[!NOTE]
>
>請注意，當您重試失敗的資料流時，會建立並執行新的資料流。 它會出現在資料流清單的頂端
