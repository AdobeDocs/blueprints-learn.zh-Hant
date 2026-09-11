---
title: 建立自訂欄位群組
description: 使用結構描述登入API來建立自訂客戶帳戶詳細資料欄位群組，並儲存其$id以用於之後的結構描述。
doc-type: article
solution: Experience Platform
exl-id: d3262db9-7c0b-476a-843f-1a2c224ee792
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---


# 建立自訂欄位群組

## 欄位群組結構

欄位群組一律由下列欄位組成。 您會在下一個步驟的請求中看到此訊息。

| 必要值 | 說明 |
| --------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 標題 | 您要在結構描述登入中建立的欄位群組名稱。 請注意，名稱必須是唯一的。 |
| 說明 | 有關欄位群組用途的簡短說明 |
| type | 永遠是物件 |
| meta\：intendedToExtend | 定義欄位群組可以搭配使用的類別。 類別一律由其`$id`值參考 |
| allOf | 說明可包含在欄位群組中的資源。 對於自訂已定義的欄位，路徑一律為`#/definitions/customFields` |
| definitions.customFields... | 這是建立自訂欄位群組所需的預設JSON結構描述結構。 它必須符合上面的`allOf` |
| \&lt;租使用者\_名稱> | 租使用者名稱稱（即唯一名稱）會在布建流程中建立。 這可確保所做的任何自訂都不會與現有或未來Adobe結構描述登入變更發生衝突 |



## 建立客戶帳戶詳細資料欄位群組

1. 按一下`XDM Schema Lab -> Create Schema`資料夾中的請求`Step 2 - Create Customer Account Details Field Group` API呼叫



![步驟2 — 建立客戶帳戶詳細資料欄位群組API要求](assets/create-custom-field-groups-step-2-field-group-request.png "步驟2 — 建立客戶帳戶詳細資料欄位群組")



執行前先檢閱要求內文。 請注意，「欄位群組結構」區段中提及的必要欄位會顯示如下：

![自訂欄位群組的必要欄位，如要求內文中所示](assets/create-custom-field-groups-field-group-structure.png "欄位群組結構")



![參考自訂欄位定義路徑的allOf屬性](assets/create-custom-field-groups-field-group-structure-allof.png "欄位群組結構allOf")

>[!NOTE]
>
>請注意，`allOf`右上方的影像如何參照「/definitions/customFields」的路徑。  這必須符合結構描述中定義的結構（左側的影像），因為它會告訴XDM系統到哪裡尋找自訂建立的物件。
>
>![比較：醒目提示allOf路徑必須符合自訂欄位定義路徑](assets/create-custom-field-groups-allof-path-highlighted.png)



也請注意對應表中的每個特定欄位如何在XDM JSON結構中具現化。



![將工作表計畫點標籤法轉換為XDM JSON結構](assets/create-custom-field-groups-plan-dot-notation-to-xdm-json.png "計畫點標籤法轉換為XDM JSON")



![將工作表帳戶和客戶ID點標籤法轉換為XDM](assets/create-custom-field-groups-account-customer-id-dot-notation-to-xdm.png "帳戶和客戶ID點標籤法對映到XDM")



&#x200B;2. 使用以下格式更新欄位群組的`title`和`description`： `Customer Account Details - Sandbox <your number here>`



   ![為自訂欄位群組填寫的標題和說明範例](assets/create-custom-field-groups-field-group-title-description-example.png "欄位群組標題和說明範例")



&#x200B;3. 按一下`Send`按鈕以執行。  您應該會看到類似下列熒幕擷圖的回應。

&#x200B;4. 複製您新建立的客戶帳戶詳細資料欄位群組的`$id`值。

建立自訂欄位群組後![成功的API回應](assets/create-custom-field-groups-step-2-create-custom-field-group-success.png "步驟2 — 建立自訂欄位群組成功")

>[!WARNING]
>
>在您將`$id`儲存到某處之前，請勿繼續。  稍後需要建立客戶帳戶結構描述
>
>
