---
title: 建立對象
description: 瞭解如何在協調的行銷活動中使用「建立對象」活動，使用關聯式結構描述條件，以特定電話機代號來鎖定作用中的客戶系列。
doc-type: article
solution: Experience Platform
exl-id: 697d3edb-2b63-4038-a934-3587495e17f7
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '856'
ht-degree: 0%

---


# 建立對象

## 目標

在接下來的幾個步驟中，您將會建立您要針對促銷活動鎖定的對象，也就是擁有符合正在啟動的旗艦電話的品牌的所有作用中生產線持有者。  此目標是您要以SMS訊息作為目標群組，督促他們升級手機。



## 新增建立對象活動

1. 在畫布上按一下&#x200B;**+符號**，然後選取&#x200B;**建立對象**&#x200B;活動，以將其新增至工作流程

   ![將組建對象活動新增至工作流程畫布](assets/build-an-audience-add-activity.png)



2. 在右邊欄中，您會看到「建置對象」屬性。 更新標籤以指出下列專案： `Active Lines with Apple`

![使用Apple將對象標籤設為Active Lines ](assets/build-an-audience-set-label.png)


## 選取目標維度

下一步是選取&#x200B;**目標維度** （也就是您要查詢的表格）。 請執行下列步驟：

1. 按一下目標維度方塊中的&#x200B;**搜尋圖示**

   ![目標維度方塊中的搜尋圖示](assets/build-an-audience-search-targeting-dimension.png)

2. 在快顯視窗中，搜尋並選取名為&#x200B;**dep-rel： Customer Line**&#x200B;的資料表，然後按一下&#x200B;**確認**&#x200B;按鈕。

![選取dep-rel： Customer Line資料表並按一下[確認]](assets/build-an-audience-select-customer-line-table.png)

>[!NOTE]
>
>永遠記住您建立的每個對象的&#x200B;**目標維度**。 您將在後續步驟中瞭解其重要性。

>[!NOTE]
>
>如果您選取Adobe建立的結構描述，請注意該結構描述的開頭為 — > *(caas)*。 這只是套用至關聯式存放區中表格的名稱空間，代表Campaign as a Service ：)



## 建立對象

現在您已選取目標維度（您要查詢的關聯式結構描述），您可以開始建立定義。

1. 在右側邊欄中，按一下&#x200B;**建立對象**&#x200B;按鈕

   右側邊欄中的![建立對象按鈕](assets/build-an-audience-click-create-audience.png)

2. 接著按一下&#x200B;**新增條件**&#x200B;按鈕

![新增對象定義的條件按鈕](assets/build-an-audience-click-add-condition.png)



## 建立條件

現在可以使用結構描述中的屬性來寫入對象邏輯了。 目標是尋找所有作用中且使用Apple品牌的客戶系列。

### 建立條件#1

1. 使用下列資訊設定條件：
   - **屬性**： `Active Line`
   - **值**： `true`

   ![條件1設定為作用中行等於true](assets/build-an-audience-condition-active-line-true.png)

2. 按一下&#x200B;**重新整理**&#x200B;圖示以檢視條件的合格計數。

![重新整理圖示顯示條件1](assets/build-an-audience-condition-1-refresh-count.png)的合格計數為241

>[!TIP]
>
>如果您已正確建立條件，則會顯示241的結果



### 建立條件#2

1. 按一下&#x200B;**新增條件**&#x200B;按鈕，然後按一下&#x200B;**>**&#x200B;圖示來選取&#x200B;**dep-rel：** **產品\[查詢]**&#x200B;結構描述

   ![按一下>圖示](assets/build-an-audience-select-product-lookup-schema.png)以選取dep-rel：產品[查詢]結構描述


2. 尋找名為&#x200B;**Make**&#x200B;的欄位，然後按一下三個點並選取&#x200B;**分配值**

   Make欄位](assets/build-an-audience-make-distribution-of-values.png)的![值分佈選項



3. 記下各種值。 您只想要`Apple`，而且幸好它沒有100個不同的拼字。 按一下&#x200B;**Apple欄位**&#x200B;以選取它，然後按一下右上角的&#x200B;**選取屬性和值按鈕**。

   使用Select屬性和值按鈕](assets/build-an-audience-select-apple-attribute-value.png)選取的![Apple值

   >[!NOTE]
   >
   >這是資料架構師應該以分項清單設計結構描述的主要範例。  這樣行銷人員就不必手動選取/輸入值。  資料架構師的恥辱！



4. `Make`欄位會連同下列條件一起自動新增。
   - **運運算元：** `Equal to`
   - **值：** `Apple`
   - **區分大小寫：** `Enabled`

5. 按一下&#x200B;**計算圖示**，結果會顯示85。

![條件2已計算85](assets/build-an-audience-condition-2-final-count.png)的計數

>[!NOTE]
>
>請注意群組中是否使用了AND運運算元。 無論您是在顯示等單一群組或多個群組中建立此專案，AND都非常重要，因為它會告知Orchested Campaigns兩個條件都必須為true。



## 驗證計數

1. 按一下「設定檔目標」標題下右側邊欄中的&#x200B;**計算圖示**，以取得對象規模的精確預估。 您將&#x200B;**65**&#x200B;視為&#x200B;**最終計數**。

   ![顯示最終對象人數的計算圖示65](assets/build-an-audience-calculate-final-audience-size.png)

   >[!NOTE]
   >
   >請注意每個個別條件如何傳回不同的數字（條件#1 —> 241和條件#2 —> 85），但最終對象人數是兩個條件中較小者。  這是因為該AND運運算元。



2. 如果您看到&#x200B;**65**&#x200B;的最終計數，請按一下熒幕右上方的&#x200B;**Confirm**&#x200B;按鈕，然後按一下右上方的&#x200B;**Save**&#x200B;按鈕以儲存您的工作。



## 挑戰

假設您輸入了最後一個條件，使`Make`等於`apple` （小寫），而且您已將`Case sensitive`的組態選項保留為Togged `on`。  這會使條件記錄計數等於0。  因此您會有241個使用中明細行和0，其中製造商是蘋果。



**在這種情況下，最終對象人數會是多少？**

![顯示記錄計數為0的最後一個條件「最後一個條件為0」](assets/build-an-audience-challenge-zero-count-condition.png "最後一個條件為0")

## 回答

是零。 您知道為什麼嗎？

![最終計數為零原因的解釋](assets/build-an-audience-answer-zero-count-explanation.png)



## 重述

您已成功建立第一個對象，現在應該會看到在建置對象活動中開發和驗證計數的簡易程度。

回顧後![已完成建立對象活動](assets/build-an-audience-recap-completed-audience.png)
