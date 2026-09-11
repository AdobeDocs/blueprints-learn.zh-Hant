---
hold: true
title: 儲存對象
description: 瞭解如何從協調的行銷活動工作流程變更維度、刪除重複專案，以及儲存對象至對象入口網站。
doc-type: article
solution: Experience Platform
exl-id: 6422ea8d-146b-4fc7-86e6-491f77590ca1
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 0%

---


# 儲存對象

## 目標

在接下來的幾個步驟中，您會將您建立的對象儲存回Audience Portal，讓Adobe Experience Platform及其應用程式中的其他解決方案可針對自己的使用案例加以運用。



## 變更維度

1. 在工作流程畫布上，按一下&#x200B;**儲存對象**&#x200B;分支上的&#x200B;**+** **圖示**，然後從活動清單中選取&#x200B;**變更維度**&#x200B;活動

![在「儲存對象」分支上新增「變更維度」活動](assets/save-the-audience-add-change-dimension.png)



&#x200B;2. 更新變更維度的屬性，如下所示：
   - **標籤：** `Convert Line to Account`
   - **新目標維度：** `dep-rel: Customer Account`

![變更維度標籤及新的目標維度欄位](assets/save-the-audience-change-dimension-label.png)

![已選取作為新目標維度的客戶帳戶](assets/save-the-audience-select-customer-account.png)

>[!NOTE]
>
>**您為何要這樣做？請問？**  請記住，若要加入即時客戶設定檔（您儲存對象到的位置），必須使用您設定的設定檔目標對應，該對應僅能從dep-rel：客戶帳戶結構描述加入。



&#x200B;3. 完成後，這是您畫布的外觀。  儲存您的工作！

新增變更維度活動後![工作流程畫布](assets/save-the-audience-canvas-after-change-dimension.png)



## 刪除重複結果

1. 在變更維度活動後按一下&#x200B;**+** **圖示**，並從活動清單中選取&#x200B;**重複資料刪除**&#x200B;活動

![在變更維度後新增重複資料刪除活動](assets/save-the-audience-add-deduplication-activity.png)



&#x200B;2. 將重複資料刪除活動的標籤更新為`Dedup customer id`

![重複資料刪除活動標籤已設定為重複資料刪除客戶ID](assets/save-the-audience-deduplication-label.png)



&#x200B;3. 現在按一下&#x200B;**+新增屬性**&#x200B;按鈕，並從標題為&#x200B;**客戶ID**&#x200B;的結構描述中選取欄位

![新增重複資料刪除活動的屬性按鈕](assets/save-the-audience-add-attribute-button.png)

從結構描述![&#128279;](assets/save-the-audience-select-customer-id-field.png)中選取的客戶識別碼欄位



&#x200B;4. 在「重複資料刪除」設定下，確定您有以下設定：
   - **要保留的重複專案：** `1`
   - **重複資料刪除方法：** `Random selection`

![重複資料刪除設定（包含要保留的重複專案）和方法](assets/save-the-audience-deduplication-settings.png)

>[!NOTE]
>
>重複資料刪除的其他選項可讓您指定自己的自訂邏輯。  大部分時間，如果您需要刪除重複資料，則會使用表格的主索引鍵執行此操作。



&#x200B;5. 完成後，您的畫布看起來像這樣。 在繼續之前，請按一下右上方的&#x200B;**儲存**&#x200B;按鈕。

![已在畫布上完整設定重複資料刪除活動](assets/save-the-audience-deduplication-configured.png)



## 新增儲存對象活動

1. 在重複資料刪除活動後按一下&#x200B;**+**&#x200B;圖示，然後選取&#x200B;**儲存對象**&#x200B;活動

![在重複資料刪除後新增儲存對象活動](assets/save-the-audience-add-save-audience-activity.png)

&#x200B;2. 在右側欄中，將活動的屬性設定如下：
   - **對象標籤**： `Apple Upgrade Eligible Customer Accounts`
   - **設定檔對應欄位**： `dep-rel: Customer Account - customer id`

![儲存對象標籤和設定檔對應欄位設定](assets/save-the-audience-label-and-profile-mapping.png)

>[!NOTE]
>
>「設定檔對應欄位」是您先前設定的專案，好讓關聯式存放區可以聯結至即時客戶設定檔。  設定檔已模型化為「客戶帳戶」層級，因此您要將對象儲存在相同層級。  因此，需要變更維度和重複資料刪除。



## 對象欄位對應

預設會將目標維度的主索引鍵（即客戶ID）作為欄位新增至對象。 如果您檢視右側並展開欄位，即可看到此內容。  請注意兩件事：

- **Source對象欄位** —>參考來自關聯式結構描述的欄位
- **目標對象欄位** —>將隨著對象儲存而建立的欄位名稱

![預設客戶ID欄位已新增至「儲存對象」活動](assets/save-the-audience-default-field-added.png)

>[!NOTE]
>
>請注意「目標對象」欄位的名稱是`Dep_rel_customer_account_Customer_id`的程度。  您應該隨時將此變更為行銷人員更容易辨識的內容，無需託辭。



## 修正預設對象欄位

1. 將預設的目標對象欄位重新命名為&#x200B;**Customer\_ID**，如下所示：

![目標對象欄位已重新命名為Customer_ID](assets/save-the-audience-field-renamed.png)

>[!TIP]
>
>現在您有了人類可辨識的欄位名稱🎉



&#x200B;2. 按一下&#x200B;**開始**&#x200B;按鈕以執行工作流程。 您的工作流程現在看起來像這樣，而您會看到如下的計數：
   - 建置對象： `65`
   - 將行轉換為帳戶： `65`
   - 重複資料刪除客戶ID： `46`

![顯示建置、轉換及重複資料刪除計數的工作流程測試回合](assets/save-the-audience-test-run-counts.png)

>[!NOTE]
>
>儲存閱聽眾活動只會在工作流程發佈時建立閱聽眾，而不會在工作流程啟動時建立。 建立對象時，會包含您新增的所有屬性，並會在下次排程的每日細分服務工作執行期間，加入即時客戶設定檔。

>[!CAUTION]
>
>不要發佈您的工作流程！



## 挑戰

如果您在儲存對象前沒有進行重複資料刪除，會發生什麼情況？  對象會儲存全部65筆記錄還是僅儲存46筆記錄？

![預先儲存不含重複資料刪除的受眾挑戰情境「預先儲存包含重複資料刪除活動的受眾」](assets/save-the-audience-challenge-without-dedup.png "預先儲存包含重複資料刪除活動的受眾")



## 回答

對象將會儲存所有65筆記錄，但讀取對象活動將會根據加入條件😁在匯入時刪除重複資料







## 重述

您現在應該清楚瞭解「儲存對象」的運作方式，以及重複資料刪除重要的原因。  請記住，您一律需要定義設定檔目標對應，因為關聯式存放區資料必須知道如何聯結至即時客戶設定檔。  設定檔目標對應是連線條件🙂
