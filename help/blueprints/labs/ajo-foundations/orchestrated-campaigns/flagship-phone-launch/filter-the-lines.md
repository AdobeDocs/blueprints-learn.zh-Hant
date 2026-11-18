---
title: 篩選行
description: 瞭解如何透過分割活動篩選掉選擇退出的客戶行，並使用變更維度以使工作流程的目標維度與簡訊頻道設定一致。
doc-type: article
solution: Experience Platform
exl-id: fb556a27-5c73-4457-ae98-dba43d445c7f
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: f189618dc8bfa198b25d646faa3ca0e0f5af5916
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%
---

# 篩選行

## 目標

在接下來的幾個步驟中，您將篩選掉實際上不允許以SMS訊息鎖定的所有行，因為這些行在行層級選擇退出。  您無法在此信賴設定檔同意，因為這是行層級目標。



## 設定分割活動

1. 按一下Fork活動底部轉變上的&#x200B;**+**&#x200B;圖示，然後在快顯視窗中選取&#x200B;**分割**&#x200B;活動。

   ![新增分割活動至底部分支分支](assets/filter-the-lines-add-split-activity.png)



2. 在右邊欄更新標籤以指出下列專案： `Filter out opt'd out lines`

   ![分割活動標籤設定為篩選退出選擇退出行](assets/filter-the-lines-set-split-label.png)



3. 在右側邊欄中，展開預設區段&#x200B;**子集**&#x200B;區段，然後按一下&#x200B;**建立篩選器**&#x200B;按鈕

   ![在子集區段中建立篩選器按鈕](assets/filter-the-lines-create-filter-button.png)



4. 新增條件，以確保您移除所有選擇退出簡訊的客戶連結，然後按一下&#x200B;**確認**。

   ![條件移除已選擇退出簡訊的客戶線路](assets/filter-the-lines-sms-optin-condition.png)

   >[!NOTE]
   >
   >您必須找出如何建立條件，但最終結果符合上方的熒幕擷圖。  知道了！



5. 按一下右上角的「儲存」按鈕以儲存作業。  您的畫布現在看起來像這樣\...

儲存分割活動後![工作流程畫布](assets/filter-the-lines-canvas-after-split-save.png)



## 新增變更維度

1. 在工作流程畫布上，在您新增的分割條件後按一下&#x200B;**+**&#x200B;圖示，並選取&#x200B;**變更維度**&#x200B;活動

   ![在分割條件後新增變更維度活動](assets/filter-the-lines-add-change-dimension-activity.png)

2. 更新變更維度的屬性，如下所述，然後按一下&#x200B;**確認**：
標籤： `Convert Line to Account`
新的目標維度： `dep-rel: Customer Account`

   ![編輯目標維度](assets/filter-the-lines-add-edit-target-dimension.png)

   ![編輯目標維度](assets/filter-the-lines-add-select-target-dimension.png)



## 新增簡訊活動

1. 在您新增的變更維度之後，按一下&#x200B;**+**&#x200B;圖示，並選取&#x200B;**行動訊息活動**

   ![在分割條件之後新增行動訊息活動](assets/filter-the-lines-add-sms-activity.png)

   ![簡訊活動已新增至工作流程畫布](assets/filter-the-lines-sms-activity-on-canvas.png)



2. 在右側邊欄中，請先將Target選擇變更為&#x200B;**每個次要維度一個訊息**，然後按一下&#x200B;**編輯行動訊息**&#x200B;按鈕以開始設定SMS訊息

   ![在右側邊欄中鎖定並編輯行動訊息按鈕](assets/filter-the-lines-edit-sms-button.png)



3. 在頂端導覽列中，按一下「動作」功能表專案，然後從行動訊息設定下拉式清單中選取您先前建立的頻道。

![簡訊設定已成功顯示選取的頻道](assets/filter-the-lines-sms-configuration-selected.png)




## 重述

您篩選掉所有因選擇退出而不允許以SMS訊息鎖定的行，將維度從行變更為帳戶，並為允許鎖定的對象新增SMS活動。
