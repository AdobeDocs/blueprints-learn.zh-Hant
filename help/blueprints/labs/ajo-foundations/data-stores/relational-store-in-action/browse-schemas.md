---
title: 瀏覽結構描述
description: 瞭解如何在Adobe Experience Platform中瀏覽關聯式結構描述和檢視實體關係圖，以瞭解行銷活動中使用的結構描述關係。
doc-type: article
solution: Experience Platform
exl-id: ac0e6743-4a83-4a8b-9bc6-f012b636312e
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 0%

---


# 瀏覽結構描述

## 目標

在接下來的步驟中，您將導覽UI以檢視結構描述及其關係。  熟悉建立行銷活動時可用的結構描述和關係很重要。

## 檢視結構描述

已為您建立Connection 5G關聯式資料模型。 您可以導覽至UI中的&#x200B;**結構描述 — >瀏覽**&#x200B;頁面，自行檢視結構描述。

在搜尋方塊中輸入`dep-rel`以檢視所有結構描述。

![搜尋結果顯示所有相關關聯式結構描述](assets/browse-schemas-search-results.png)

>[!NOTE]
>
>請注意，所有結構描述的型別為&#x200B;*關聯式*



## 檢視關係圖

使用關聯式XDM結構描述，您可以透過選取任何結構描述並按一下「檢視關係圖表」按鈕，輕鬆檢視實體關係圖表(ERD)。

執行下列動作：

1. 按一下&#x200B;**關係**&#x200B;標籤，然後按一下&#x200B;**檢視關係圖**&#x200B;按鈕

   ![具有[檢視關聯圖]按鈕的[關聯性]索引標籤](assets/browse-schemas-relationships-tab.png)



2. 按一下&#x200B;**選取結構描述**
3. 從快顯視窗中選取`dep-rel: Customer Account`，然後按一下&#x200B;**確認**

   ![選擇結構描述快顯視窗，相關資訊：已選擇客戶帳戶](assets/browse-schemas-select-schema-popup.png)



4. 在ERD上，按一下&#x200B;**3點**&#x200B;並選取&#x200B;**顯示相關實體**

   ![在ERD內容功能表中顯示相關實體選項](assets/browse-schemas-show-related-entities.png)



5. 檢視ERD，其中包含與dep-rel：客戶帳戶直接相關的所有表格。 您可以選擇下載ERD作為PNG檔案。

![實體關係圖表顯示與客戶帳戶相關的表格](assets/browse-schemas-erd-diagram.png)

>[!TIP]
>
>酷斃了，嗯?!

## 重述

您現在已瞭解在結構描述和關係UI中導覽是多麼容易。  您可以選取特定結構並導覽以檢視關係，以協助瞭解並使用行銷活動協調流程中的資料。

若您有興趣，請參閱[此處](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/data-management/get-started-schemas)以瞭解詳情。
