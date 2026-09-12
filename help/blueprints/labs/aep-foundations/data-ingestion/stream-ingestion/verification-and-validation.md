---
title: 驗證與驗證
description: 在UI中預覽串流資料集，並執行SQL查詢以驗證擷取的記錄和巢狀結構描述欄位。
doc-type: article
solution: Experience Platform
exl-id: fbdb0b6b-08b6-49b8-b6ab-d59d5941c678
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 0%

---


# 驗證與驗證

## 預覽資料集

1. 按一下&#x200B;**資料集**
1. **找到**&#x200B;並&#x200B;**按一下**&#x200B;您建立的資料集名稱。

   ![存取「資料集」窗格中建立的資料集](assets/verification-and-validation-access-the-dataset-in-the-datasets-pane.png "存取「資料集」窗格中的資料集")



1. 按一下右上角的&#x200B;**預覽資料集**

   ![預覽資料集按鈕位於資料集畫面的右上角](assets/verification-and-validation-preview-dataset-button.png "預覽資料集位於右上角")



1. 按一下顯示結構描述階層的左窗格，**驗證**&#x200B;和&#x200B;**驗證**&#x200B;您所擷取的相同記錄。

![使用結構描述階層窗格驗證及驗證內嵌的記錄](assets/verification-and-validation-verify-and-validate-the-dataset.png "驗證及驗證資料集")

>[!NOTE]
>
>**預覽資料集**&#x200B;只會顯示資料集的前幾列。 無法檢視陣列物件。



## 查詢資料集

1. **關閉**&#x200B;預覽
1. 在資料集畫面中，按一下&#x200B;**資料表名稱**&#x200B;上的復製圖示。 在下列範例畫面中，資料表名稱為`customer_account_sm`

   ![從資料集畫面複製資料表名稱以用於查詢](assets/verification-and-validation-copy-the-table-name.png "複製資料表名稱")



1. 瀏覽至&#x200B;**查詢**&#x200B;區段

1. 按一下&#x200B;**建立查詢**

   ![從查詢區段存取查詢編輯器](assets/verification-and-validation-access-the-query-editor.png "存取查詢編輯器")



1. 開啟&#x200B;**增強型查詢編輯器**&#x200B;的切換按鈕

   ![查詢編輯器介面已啟用增強型查詢編輯器切換](assets/verification-and-validation-enhanced-query-editor-toggle.png "查詢編輯器介面")



1. 將下列SQL查詢複製貼到&#x200B;**編輯器**&#x200B;中。 記得要以您在步驟2中取得的值取代`<table_name>`。

   ```sql
   SELECT * FROM <table_name>
   ```



1. 按&#x200B;**播放**&#x200B;按鈕。

1. **預覽**&#x200B;結果。

1. 此外，執行以下SQL查詢以擷取XDM結構描述以及資料：

   ```sql
   SELECT to_json(shippingAddress) FROM <table_name>
   ```



1. 若要存取`postalCode` **節點**&#x200B;中的資料，您可以輸入：

```sql
SELECT shippingAddress.postalCode FROM <table_name>
```

>[!TIP]
>
>恭喜！  您已成功內嵌並建立一組即時客戶個人檔案的範例
