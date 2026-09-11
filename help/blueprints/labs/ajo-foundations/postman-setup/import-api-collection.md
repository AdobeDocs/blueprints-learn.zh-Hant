---
hold: true
title: 匯入API集合
description: 匯入Bootcamp的Postman API集合，並驗證其環境變數可針對您的沙箱正確解析。
doc-type: article
solution: Experience Platform
exl-id: 7562c7f1-0d60-4a3a-8bce-fa42bda08962
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---


# 匯入API集合

## 目標

在此步驟中，您將匯入API集合，其中包含您在整個Bootcamp中需要提出的所有各種請求。  這些API要求取決於您剛匯入的環境檔案。



## 匯入要求集合

1. 下載&#x200B;**AJO Bootcamp (Labs)。postman\_collection.json**&#x200B;檔案：

下載檔案 — [AJO Bootcamp (Labs)。postman_collection.json](assets/ajo-bootcamp-labs.postman_collection.json)

&#x200B;2. 就像之前一樣，按一下&#x200B;**匯入**&#x200B;按鈕。
&#x200B;3. 將&#x200B;**AJO Bootcamp (Labs)。postman\_collection.json**&#x200B;檔案的本機URL貼入匯入模組文字方塊，或將它拖放到匯入對話方塊中。  這會觸發自動匯入。
&#x200B;4. 匯入程式完成後，請按一下左側導覽列中的&#x200B;**集合**，展開&#x200B;**AJO Bootcamp (Labs)**&#x200B;資料夾，然後您會看到新匯入的集合

![驗證postman集合匯入](assets/import-api-collection-verify-collection-imported.png)

>[!TIP]
>
>恭喜！  您已成功匯入啟動營的Postman集合



## 驗證環境變數

您匯入的集合包含您在整個bootcamp中用於Labs的所有必要API呼叫。  每個實驗室都會整理到特定的資料夾中，其中包含自己的請求集。

您可以在下方找到每個資料夾的詳細資訊：

- **設定檔與Journey Labs** — 包含一組傳送Web事件的要求，以及模擬出貨確認的事件。
- **決策Labs** — 包含3位訪客的請求，這些請求會模擬通常可在AEP Web SDK標籤的網站上找到的頂端和底部頁面呼叫。

為確保環境和集合一起正常運作，請按照以下步驟操作。

1. 如有必要，請按一下左側邊欄中的&#x200B;**集合**，然後展開&#x200B;**Profile &amp; Journey Labs**&#x200B;資料夾。
2. 按一下&#x200B;**建立Web事件**&#x200B;要求，您會看到環境變數為&#x200B;**紅色**

![Postman要求顯示以紅色反白顯示的環境變數，因為未選取任何環境](assets/import-api-collection-environment-variables-shown-red.png "驗證Postman環境變數是否為紅色")

&#x200B;3. 按一下右上角的&#x200B;**環境下拉式清單**，然後選擇&#x200B;**AJO Bootcamp**&#x200B;環境。

![選取正確的Postman環境](assets/import-api-collection-select-postman-environment.png)

&#x200B;4. 選取適當的環境後，您會看到EDGE\_REGION變數現在會變更為較淺的藍色。 這表示變數現在具有所選環境的值。 DATASTREAM\_CONFIG變數保持紅色，因為您尚未建立資料流，因此您還沒有該環境變數的值。 將游標暫留在EDGE\_REGION上會顯示環境值的值。

![Postman EDGE_REGION變數已填入且不再顯示於red](assets/import-api-collection-environment-works-with-collection.png "確認Postman環境可搭配集合使用")

## 重述

您現在已匯入環境和集合檔案，並知道如何使用它們。
