---
title: 篩選行
description: 瞭解如何透過分割活動篩選掉選擇退出的客戶行，並使用變更維度以使工作流程的目標維度與簡訊頻道設定一致。
doc-type: article
solution: Experience Platform
exl-id: fb556a27-5c73-4457-ae98-dba43d445c7f
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: 8d5a87f094e2fba7abd7f5a9acf8e9e775d9b534
workflow-type: tm+mt
source-wordcount: '748'
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



2. 在右側邊欄中，按一下&#x200B;**編輯行動裝置訊息**&#x200B;按鈕以開始設定SMS訊息

   ![編輯右邊欄中的行動訊息按鈕](assets/filter-the-lines-edit-sms-button-only.png)



3. 在頂端導覽列中，按一下「動作」功能表專案，然後從行動訊息設定下拉式清單中選取您先前建立的頻道。

![簡訊設定下拉式清單顯示無結果錯誤](assets/filter-the-lines-sms-configuration-no-results.png)

>[!CAUTION]
>
>糟糕，沒有🫨！  為什麼沒有結果？  您尚未設定簡訊通道嗎？  產品是否損壞？
>
>嚇壞了!!!!!!!!!



## 驚慌時刻

簡訊的頻道設定已由您預先設定，目前看起來像這樣……

![在設定SMS通道實驗室期間設定的執行詳細資料設定](assets/configure-sms-channel-final-execution-details.png)

**閱讀方式如下：**

- 針對在次要維度（即客戶明細行）中找到的相關記錄數，針對目標維度（即客戶帳戶）傳遞一則訊息
- 使用在次要維度（即客戶線路）中找到的行動電話號碼執行每次SMS傳送

這種將許多訊息傳送至一個設定檔的獨特功能，是協調行銷活動的主要功能之一，使其與歷程不同。 不過，您進入行動訊息活動的轉變設為「客戶帳戶」。 這可讓您在傳送時將其加入Real-time Customer Profile，以便將訊息的傳送和追蹤資訊歸因於設定檔。


您如何讓此功能發揮作用？ 變更訊息執行的目標以符合您的頻道設定😀



## 變更Target並完成簡訊設定

1. 按一下簡訊編輯畫面上的上一頁按鈕

   ![返回按鈕以結束簡訊編輯畫面](assets/filter-the-lines-exit-sms-editor.png)



2. 選取行動訊息活動後，在右側邊欄中，先將Target選擇從預設選項（每個設定檔一個訊息）變更為&#x200B;**每個次要維度一個訊息**&#x200B;選項，然後按一下返回&#x200B;**編輯行動訊息**

   ![變更目標，然後在右側邊欄中編輯行動訊息按鈕](assets/filter-the-lines-edit-sms-button.png)



3. 在頂端導覽列中按一下&#x200B;**動作**&#x200B;功能表專案，然後從行動訊息設定下拉式清單中選取您先前建立的頻道。

   ![簡訊設定已成功顯示選取的頻道](assets/filter-the-lines-sms-configuration-selected.png)



## 重述

您篩選掉因選擇退出而無法以SMS訊息鎖定的所有行，將維度從行變更為帳戶，並在最後成功為允許鎖定的使用者設定簡訊活動。
希望您也學到了一件非常重要的事 — **您的目標必須符合您要使用的頻道設定**
