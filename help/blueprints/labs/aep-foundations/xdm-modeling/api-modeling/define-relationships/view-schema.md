---
hold: true
title: 檢視結構描述
description: 透過結構描述UI和取得結構描述API，檢視客戶帳戶結構描述與計畫結構描述的查詢關係。
doc-type: article
solution: Experience Platform
exl-id: dae48ef4-f762-4173-8564-c1ad40c0109b
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---


# 檢視結構描述

## 透過UI檢視

1. 開啟瀏覽器並導覽回`Schema -> Browse`區段。
1. 搜尋結構描述`Sample Customer Schema - <your sandbox number>`
1. 請注意，已定義與`dep: Plan [Lookup]`的關係

![Experience Platform UI中的範例客戶結構描述顯示dep：計畫查閱關係](assets/view-schema-relationship-to-plan-lookup-schema.png)


## 透過API檢視

1. 按一下以選取`Step 4 - Get Customer Account Schema and its descriptors` API

![步驟4 — 取得客戶帳戶結構描述及其描述項API呼叫](assets/view-schema-step-4-get-schema-and-descriptors.png "步驟4 — 取得客戶帳戶結構描述及其描述項")



2. 在要求的URL中，將`<replace me>`取代為您從上一個區段[建立結構描述](../build-schema/create-schema.md)儲存的`$meta:altId`，如下所示

![步驟四要求附加中繼資料:altId，至URL](assets/view-schema-final-step-4-request.png "最後步驟四要求")



3. 使用`Save`按鈕儲存請求

4. 按一下`Send`按鈕以執行要求

您現在應該會看到`200 OK`回應，而且應該能夠瀏覽至您建立之結構描述的結尾，透過XDM JSON結構的鏡頭檢視身分識別



![客戶帳戶結構描述JSON中可見的關係描述項](assets/view-schema-relationship-descriptor.png "關係描述項")



![可在客戶帳戶結構描述JSON中看到的參考身分描述項](assets/view-schema-reference-identity-descriptor.png "參考身分描述項")
