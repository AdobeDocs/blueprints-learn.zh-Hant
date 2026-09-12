---
title: 建立對象
description: 瞭解如何使用「建立對象」活動，從關聯式結構描述中鎖定基本計畫成員，並驗證產生的列計數。
doc-type: article
solution: Experience Platform
exl-id: 7576e64b-d99a-4864-b877-f4ae77e1d7bd
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---


# 建立對象

## 目標

在接下來的步驟中，您將選取正確的目標維度並設定適當的條件，從關聯式架構建立對象。 您也會使用重新整理選項來檢查預期的列計數。

## 建置客群

1. 轉譯行銷活動後，按一下畫布中的&#x200B;**+**&#x200B;以開啟選項功能表，然後從&#x200B;**目標定位活動**&#x200B;中選取&#x200B;**建立對象**

   ![從目標定位活動中選取組建對象](assets/build-an-audience-select-build-audience-activity.png)

2. **建立對象**&#x200B;活動會開啟右側的詳細資料窗格，按一下「搜尋」圖示以選取&#x200B;**目標維度**。

   ![選取目標維度](assets/build-an-audience-select-targeting-dimension.png)

3. 從清單中選取`dep-rel: Customer Account`並按一下&#x200B;**確認**

   ![選取dep-rel：客戶帳戶結構描述](assets/build-an-audience-select-customer-account-schema.png)

4. 設定&#x200B;**目標維度**&#x200B;後，按一下「建立對象」以開始從關聯式結構描述建立對象的程式

   ![按一下「建立對象」按鈕](assets/build-an-audience-create-audience-button.png)

5. 建立對象詳細資料窗格隨即開啟，請按一下&#x200B;**新增條件**

   ![在[建立對象]窗格中按一下[新增條件]](assets/build-an-audience-add-condition.png)

6. 按一下`dep-rel: Plan Lookup`旁邊的&#x200B;**>**，向下捲動並展開它

   ![展開dep-rel：計畫查閱](assets/build-an-audience-expand-plan-lookup.png)

7. 選取`dep-rel: Plan Name`並按一下&#x200B;**確認**

   ![選取dep-rel：計畫名稱](assets/build-an-audience-select-plan-name.png)

8. 在「自訂條件」面板中，將運運算元保留為「等於」，並在「值」中，從下拉式清單中選取「基本」。

   ![計畫名稱等於Basic的自訂狀態](assets/build-an-audience-plan-name-equals-basic.png)

   >[!NOTE]
   >
   >請注意，所有可用於所選欄的相異值都會顯示在下拉式清單中，讓您輕鬆建立自訂條件。



9. 設定自訂條件後，按一下「重新整理」圖示以計算並檢視計數。 有兩個位置可協助計算結果

   ![按一下[重新整理]圖示以計算預期的資料列計數](assets/build-an-audience-refresh-row-counts.png)

   >[!NOTE]
   >
   >重新整理作業會根據關聯式資料評估條件，並顯示預期的結果。 這項作業通常只需要幾秒鐘的時間，對於微調准則並確保符合預期非常有用。



10. 計數(**38**)表示關聯式存放區中符合指定條件的列數。 按一下&#x200B;**確認**&#x200B;以結束&#x200B;**建立對象**&#x200B;窗格

![確認資料列計數並結束[建立對象窗格]](assets/build-an-audience-confirm-row-count.png)

>[!NOTE]
>
>「規則屬性」區段底下有選項可取得詳細資訊。 按一下&#x200B;**檢視結果**&#x200B;以檢視傳回的實際結果。 使用&#x200B;**程式碼檢視**&#x200B;選項檢視正在執行的查詢。

## 重述

您現在已瞭解在行銷活動中使用建立對象活動的簡易程度，只需從關聯式結構描述選擇正確的目標維度。 然後，您新增條件來調整對象建立條件，並使用重新整理選項來檢查預期的列數。

若您有興趣，請參閱[此處](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/campaigns/orchestrated-campaigns/design-campaigns/build-audience)以瞭解詳情。
