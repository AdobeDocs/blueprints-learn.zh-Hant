---
title: 驗證Data Lake的事件
description: 瞭解如何查詢Data Lake以確認串流的Web事件已寫入正確的資料集。
doc-type: article
solution: Experience Platform
exl-id: 14445089-aa3c-4cce-9d33-80032b6f9868
source-git-commit: 0b33b2740ee7f5af73d64f217b4475650c1d28a0
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 0%

---


# 驗證Data Lake的事件

## 學習目標

確認已將網頁事件寫入Experience Platform資料湖。

## 驗證事件

>[!NOTE]
>
>資料最終會出現在資料湖中。  **這可能需要60分鐘**。  我們知道資料集已啟用設定檔，因此事件將建立設定檔片段。
>
>您可以尋找及查詢網頁資料集。

1. 移至&#x200B;**查詢**&#x200B;和&#x200B;**建立查詢**

   ![在查詢區段中建立查詢畫面](assets/validate-event-on-data-lake-create-query.png)

2. 複製此SQL並將其貼到您的查詢中

   ```sql
   SELECT identityMap['email'][0].id, * FROM dep_web
   where identityMap['email'][0].id = 'henry.creel@emailsim.io'
   ```

3. **執行**&#x200B;查詢

>[!NOTE]
>
>**記住**：資料最終會出現在資料湖中。  **這可能需要60分鐘**。
>
>您不需要等待它出現。 歡迎您返回此步驟並稍後檢視。



![在資料湖](assets/validate-event-on-data-lake-query-results.png)中顯示串流的Web事件的查詢結果

## 重述

事件記錄會顯示在適當的資料集中。
