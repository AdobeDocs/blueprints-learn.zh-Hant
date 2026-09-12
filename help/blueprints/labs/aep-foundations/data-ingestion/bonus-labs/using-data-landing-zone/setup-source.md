---
title: 設定來源
description: 將範例客戶帳戶檔案上傳至資料登陸區域，並設定新的雲端儲存空間來源資料流。
doc-type: article
solution: Experience Platform
exl-id: 1c80e71b-19a7-45e9-9961-d72b3f03ecae
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 0%

---


# 設定來源

## 上傳範例檔案

您需要透過Azure Storage Explorer將範例資料檔案上傳至您的資料登陸區域，以便在實驗室期間使用。  若要這麼做，請執行下列動作：

1. 下載[範例檔案](../../sample-files.md)
1. 拖放和/或上傳&#x200B;**Lab\_Customer\_Account.csv**&#x200B;檔案至您在上一步中儲存的資料登陸區域。

上傳後，您的畫面應該看起來像下面的熒幕擷圖。

>[!WARNING]
>
>請勿將檔案上傳至&#x200B;*專案*&#x200B;資料夾。 它包含您未在Labs中使用的預先載入資料。

![資料登陸區域檔案瀏覽器顯示上傳的Lab_Customer_Account.csv檔案，而非專案資料夾](assets/setup-source-make-sure-you-do-not-upload-the-file.png)

## 導覽至來源

1. 前往Adobe Experience Platform並導覽至： **來源** -> **目錄** -> **雲端儲存空間**
1. 按一下資料登陸區域的&#x200B;**設定** / **新增資料**

![為資料登陸區域雲端儲存空間來源設定或新增資料動作](assets/setup-source-add-data-landing-zone-source.png "存取資料登陸區域")

>[!NOTE]
>
>如果該來源至少有一個連線，您會看到&#x200B;**新增資料**&#x200B;為預設動作。 如果該來源沒有連線，您會看到&#x200B;**Setup**&#x200B;為預設動作

## 預覽檔案

1. 選取&#x200B;**Lab\_Customer\_Account.csv**

   ![選取Lab_Customer_Account.csv檔案以在Azure儲存體總管中預覽](assets/setup-source-select-lab-customer-account-csv.png "存取Adobe Experience Platform中的Azure儲存體總管檔案")

1. 在預覽窗格中，檢視下列屬性並觀察下列專案：

   - **sms\_optIn**&#x200B;為同意欄位，有數個遺失值（在預覽中顯示為 — ）
   - **account\_create\_date**&#x200B;沒有適當的日期格式。 它有一個字串值，以及一個字串中的日期和時間值。
   - **account\_end\_date**&#x200B;具有適當的日期格式。



   ![sms_optIn欄位，檔案預覽](assets/setup-source-sms-optin-missing-values.png "sms_optin")中會顯示數個遺失值



   檔案預覽中顯示的![account_create_date和account_end_date欄位](assets/setup-source-account-create-date-account-end-date.png "account_create_date &amp; account_end_date")

   >[!NOTE]
   >
   >稍後在本實驗後面的對應步驟中，您將需要處理缺少的值、日期以及格式不正確的欄位

1. 按一下畫面右上角的&#x200B;**[下一步]**&#x200B;以繼續下一步



## 設定資料流

1. 在資料流詳細資訊畫面中，選擇&#x200B;**新資料集**。
1. 將輸出資料集命名為&#x200B;**客戶帳戶 — \&lt;您的縮寫>**
1. 從下拉式清單中選取&#x200B;**dep：客戶帳戶**&#x200B;結構描述。
1. 開啟&#x200B;**設定檔資料集**&#x200B;切換方塊。
（如果您未開啟此功能，設定檔存放區將無法監視是否有新資料進入此資料集，因此不會將此資料擷取到設定檔中）
1. 開啟&#x200B;**啟用部分擷取**。
（如果您未開啟此功能，如果其中一個記錄發生錯誤，擷取可能會失敗）
1. 將資料流名稱設為&#x200B;**客戶帳戶批次擷取 — \&lt;您的首字母>**
1. 開啟所有警示&#x200B;**來源資料流開始/成功/失敗**

![資料流詳細資訊畫面，已設定新資料集、設定檔切換，以及部分擷取設定](assets/setup-source-dataflow-detail-screen-settings.png "資料流詳細資料")

>[!CAUTION]
>
> 請確定您已針對設定檔和部分擷取啟用&#x200B;**該**&#x200B;資料集。

按一下畫面右上角的&#x200B;**[下一步]**&#x200B;以繼續下一步。

>[!NOTE]
>
>**啟用部分擷取**&#x200B;指定錯誤數目（**INGEST**&#x200B;和&#x200B;**DCVS**），以在整個資料流宣告失敗之前可以失敗的記錄總數百分比表示。
