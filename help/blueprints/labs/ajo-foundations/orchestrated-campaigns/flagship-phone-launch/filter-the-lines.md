---
hold: true
title: 篩選行
description: 瞭解如何透過分割活動篩選掉選擇退出的客戶行，並使用變更維度以使工作流程的目標維度與簡訊頻道設定一致。
doc-type: article
solution: Experience Platform
exl-id: fb556a27-5c73-4457-ae98-dba43d445c7f
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '776'
ht-degree: 0%

---


# 篩選行

## 目標

在接下來的幾個步驟中，您將篩選掉實際上不允許以SMS訊息鎖定的所有行，因為這些行在行層級選擇退出。  您無法在此信賴設定檔同意，因為這是行層級目標。



## 設定分割活動

1. 按一下Fork活動底部轉變上的&#x200B;**+**&#x200B;圖示，然後在快顯視窗中選取&#x200B;**分割**&#x200B;活動。

![新增分割活動至底部分支分支](assets/filter-the-lines-add-split-activity.png)



&#x200B;2. 在右邊欄更新標籤以指出下列專案： `Filter out opt'd out lines`

![分割活動標籤設定為篩選退出選擇退出行](assets/filter-the-lines-set-split-label.png)



&#x200B;3. 在右側邊欄中，展開預設區段&#x200B;**子集**&#x200B;區段，然後按一下&#x200B;**建立篩選器**&#x200B;按鈕

![在子集區段中建立篩選器按鈕](assets/filter-the-lines-create-filter-button.png)



&#x200B;4. 新增條件，以確保您移除所有選擇退出簡訊的客戶連結，然後按一下&#x200B;**確認**。

![條件移除已選擇退出簡訊的客戶線路](assets/filter-the-lines-sms-optin-condition.png)

>[!NOTE]
>
>您必須找出如何建立條件，但最終結果符合上方的熒幕擷圖。  知道了！



&#x200B;5. 按一下右上角的「儲存」按鈕以儲存作業。  您的畫布現在看起來像這樣\...

儲存分割活動後![工作流程畫布](assets/filter-the-lines-canvas-after-split-save.png)



## 新增簡訊活動

1. 在工作流程畫布上，在您新增的分割條件後按一下&#x200B;**+**&#x200B;圖示，並選取&#x200B;**簡訊活動**

![在分割條件後新增簡訊活動](assets/filter-the-lines-add-sms-activity.png)

![簡訊活動已新增至工作流程畫布](assets/filter-the-lines-sms-activity-on-canvas.png)



&#x200B;2. 在右側欄中按一下編輯簡訊按鈕，開始設定簡訊

在右側邊欄中![編輯簡訊按鈕](assets/filter-the-lines-edit-sms-button.png)



&#x200B;3. 在頂端導覽列中，按一下「動作」功能表專案，然後從SMS設定下拉式清單中選取您先前建立的管道。

![簡訊設定下拉式清單顯示無結果錯誤](assets/filter-the-lines-sms-configuration-no-results.png)

>[!CAUTION]
>
>糟糕，沒有🫨！  為什麼沒有結果？  您尚未設定簡訊通道嗎？  產品是否損壞？
>
>嚇壞了!!!!!!!!!



## 驚慌時刻

分叉轉變目前具有客戶行的目標維度（即目前結果與關聯式存放區中的表格相關）。  協調行銷活動的獨特之處在於，您一律在傳送時間加入回即時客戶設定檔，因此訊息的傳送和追蹤資訊會歸因於設定檔。  此連線是從Customer Account表格為您預先建立的。

簡訊的頻道設定已預先為您設定，目前看起來如下所示……

![在設定SMS通道實驗室期間設定的執行詳細資料設定](assets/configure-sms-channel-final-execution-details.png)

**閱讀方式如下：**

- 針對在次要維度（即客戶明細行）中找到的相關記錄數，針對目標維度（即客戶帳戶）傳遞一則訊息
- 使用在次要維度（即客戶線路）中找到的行動電話號碼執行每次SMS傳送

這種將許多訊息傳送至一個設定檔的獨特功能，是協調行銷活動的主要功能之一，使其與歷程不同。


您如何讓此功能發揮作用？  新增變更維度😀



## 新增變更維度

1. 按一下簡訊編輯畫面上的上一頁按鈕

![返回按鈕以結束簡訊編輯畫面](assets/filter-the-lines-exit-sms-editor.png)



&#x200B;2. 在工作流程畫布上，按一下篩選和簡訊活動之間的&#x200B;**+** **圖示**，然後選取&#x200B;**變更維度**。

![在篩選器和簡訊之間新增變更維度活動](assets/filter-the-lines-add-change-dimension.png)



&#x200B;3. 在右側，使用下列資訊更新變更維度：
   - **標籤：** `Convert Line to Account`
   - **新目標維度：**`dep-rel: Customer Account`

![變更維度設定為將Line轉換為帳戶](assets/filter-the-lines-change-dimension-settings.png)



&#x200B;4. 按一下畫布右上角的&#x200B;**儲存**&#x200B;按鈕以儲存您的工作。 完成後，您的工作流程現在看起來像這樣……

新增變更維度後![工作流程畫布](assets/filter-the-lines-workflow-after-change-dimension.png)



## SMS訊息設定

現在您已修正工作流程，請重新設定簡訊。



1. 按一下工作流程畫布中的簡訊活動，然後在左側邊欄中按一下&#x200B;**編輯簡訊**&#x200B;按鈕

![編輯簡訊按鈕以重新設定簡訊訊息](assets/filter-the-lines-edit-sms-button.png)

>[!NOTE]
>
>此畫面需要一些時間載入。  我知道這很煩人，相信我已得到修正





&#x200B;2. 在頂端導覽列中按一下&#x200B;**動作**&#x200B;功能表專案，然後從SMS設定下拉式清單中選取您先前建立的管道。

![簡訊設定已成功顯示選取的頻道](assets/filter-the-lines-sms-configuration-selected.png)

>[!TIP]
>
>感覺良好，不是😮‍💨



## 重述

您順利通過本課程，並滿懷希望地學習了兩項非常重要的東西：

1. 您的最終結果目標維度必須符合您要使用的管道設定
1. 變更維度活動可能會成為您確保此功能正常運作的最佳朋友
