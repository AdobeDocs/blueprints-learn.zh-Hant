---
hold: true
title: 設定對應
description: 從批次擷取實驗室匯入對應集，並更新計算日期欄位以符合串流來源的日期格式。
doc-type: article
solution: Experience Platform
exl-id: c05792af-5eab-4e62-a26e-a54478a988a8
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%

---


# 設定對應

> [!NOTE]
>
>請僅當您成功完成批次擷取實驗室時，才依照本節操作。  否則，請遵循在批次擷取實驗室中找到的[對應資料](../batch-ingestion/mapping-data/overview.md)步驟。

## 匯入對應集

如果您已完成批次擷取實驗室，您可以重複使用您在該處建立的對應集😄🎉

執行下列步驟：

1. 按一下對應畫面上的&#x200B;**匯入對應**&#x200B;按鈕

對應畫面上的![匯入對應按鈕](assets/configure-mapping-import-mapping-button.png)



1. 選擇您在「批次擷取」區段中建立的資料流，然後選取它。  其名稱應類似於&#x200B;**客戶帳戶批次v2 - \&lt;您的縮寫>.**

![選擇批次擷取資料流從](assets/configure-mapping-choose-batch-ingestion-dataflow.png)匯入其對應集



匯入後，您將會看到錯誤出現。  這是因為範例檔案中用於birth\_Date欄位的日期格式已變更。

- 使用的批次範例檔案 — > mm/dd/yyyy
- 使用的資料流範例檔案 — > yyyy-mm-dd

使用&#x200B;**date**&#x200B;函式的計算欄位需要更新，以考慮使用的日期格式變更。

匯入批次擷取對應集後顯示的![對應錯誤](assets/configure-mapping-mapping-after-the-import.png)



## 更新計算欄位

只需按一下每個計算欄位旁的箭頭圖示，即可更新每個計算欄位，然後驗證您的對應

按一下![箭頭圖示以編輯計算欄位的公式](assets/configure-mapping-arrow-to-edit-calculated-field-formula.png)

| 目標欄位 | 新增計算欄位 |
| ----------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| person.birthYear | date\_part(&quot;yyyy&quot;，date(birth\_Date，&quot;yyyy-M-d&quot;)) |
| person.birthDayAndMonth | concat(date\_part(&quot;mm&quot;， date(birth\_Date， &quot;yyyy-M-d&quot;))。toString()， &quot;-&quot;， date\_part(&quot;dd&quot;， date(birth\_Date， &quot;yyyy-M-d&quot;))。toString()) |
