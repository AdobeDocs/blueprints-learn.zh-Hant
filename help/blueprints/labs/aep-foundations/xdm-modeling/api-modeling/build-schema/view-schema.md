---
title: 檢視結構描述
description: 在Experience Platform UI中及透過取得結構描述API呼叫，檢視新建立的客戶結構描述。
doc-type: article
solution: Experience Platform
exl-id: 29302546-46dc-4c97-8fd8-deab6977635c
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 0%

---


# 檢視結構描述

## 透過UI檢視

1. 開啟瀏覽器並導覽回`Schema -> Browse`區段。

   >[!NOTE]
   >
   >重新整理UI以檢視它，因為您剛才已建立它，而且需要重新查詢結構描述登入

2. 搜尋結構描述`Sample Customer Schema - <your sandbox number>`

3. 請注意，必要類別和相關聯的欄位群組已新增到結構描述中

![在Experience Platform UI中顯示的範例客戶結構描述及其類別和欄位群組](assets/view-schema-ui-view-of-sample-customer-schema.png "範例客戶結構描述的UI檢視")


## 透過API檢視

1. 按一下以選取`Step 5 - Get Customer Account Schema` API。
1. 在要求的URL中，將`<replace me>`取代為您從上一節（建立您的結構描述）儲存到呼叫結尾的`$meta:altId`，如下所示
1. 儲存您對請求所做的編輯
1. 按一下`Send`按鈕以執行要求

![步驟5 — 取得客戶帳戶結構描述API呼叫](assets/view-schema-step-5-get-customer-account-schema.jpeg "步驟5 — 取得客戶帳戶結構描述")



新增`$meta:altId`後您的最終請求範例

![步驟五要求附加中繼資料:altId，至URL](assets/view-schema-final-step-5-request.png "最後步驟五要求")



如果您收到`200 OK`回應，應該就能透過XDM JSON結構的鏡頭瀏覽您建立的結構描述

![200 OK回應顯示完整的範例客戶帳戶結構描述JSON](assets/view-schema-sample-customer-account-schema.png "範例客戶帳戶結構描述")
