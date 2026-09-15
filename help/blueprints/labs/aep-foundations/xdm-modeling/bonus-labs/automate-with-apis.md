---
title: 使用API自動化
description: 執行Postman集合，於單次執行中自動建立結構描述、欄位群組、身分和關係描述項及資料集。
doc-type: article
solution: Experience Platform
exl-id: a490f93f-19da-4de3-81c8-4569c49c5354
source-git-commit: df6c1852a6e0357dc9f166c88e77dcf9d334f955
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%
---

# 使用API自動化

## 簡介

若要瞭解如何使用API來自動化部署，請執行可建立下列物件的API資料夾：

- 客戶帳戶與計畫\[查詢]結構描述
- 構成上述結構描述的欄位群組
- 設定檔所需的身分描述項
- 建立客戶帳戶與計畫之間關係所需的關係與參考描述元\[Lookup]
- 兩個資料集符合每個已建立的結構描述



## 執行資料夾

1. 在Postman中，導覽至&#x200B;**XDM結構描述實驗室**&#x200B;資料夾內的&#x200B;**使用API自動化**&#x200B;資料夾

   在Postman的XDM結構描述實驗室資料夾中![使用API資料夾自動化](assets/automate-with-apis-postman-automation-folder.png)



1. 按一下&#x200B;**使用API自動化**&#x200B;資料夾，然後在工作區中按一下&#x200B;**執行**&#x200B;按鈕

   >[!NOTE]
   >
   >「執行」按鈕位於Postman工作區的右上角

   針對「使用API自動化」資料夾，在Postman工作區右上角的![執行按鈕](assets/automate-with-apis-click-folder-run-button.png "按一下資料夾「執行」")



1. 新視窗會出現，顯示資料夾中的所有API呼叫。 將&#x200B;**延遲**&#x200B;設定為&#x200B;**500ms**，然後按一下&#x200B;**執行**&#x200B;按鈕。

   ![執行自動化對話方塊，延遲設定為500毫秒，再按一下[執行]](assets/automate-with-apis-execute-automation-dialog.png " [執行自動化]")



1. 您會看到API呼叫開始依序執行，而當完成時，您會看到32項通過測試。

   ![自動執行成功，共有32項通過測試](assets/automate-with-apis-successful-automation-32-passed-tests.png "自動執行成功")



1. 前往Experience Platform UI，您會看到針對前置詞為&#x200B;**postman：**&#x200B;的設定檔建立和啟用的兩個結構描述和兩個資料集

![已建立並啟用兩個結構描述以作為郵遞員設定檔：前置詞](assets/automate-with-apis-schemas-created-in-ui.png "自動化結構描述")



![以Postman建立的兩個資料集：前置詞符合自動化結構描述](assets/automate-with-apis-datasets-created-in-ui.png "自動化資料集")

>[!SUCCESS]
>
>恭喜！  您會自動部署身分識別名稱空間、欄位群組、結構描述、身分/關係描述項，並為設定檔啟用結構描述，然後使用該結構描述產生資料集
