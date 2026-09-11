---
title: 取得標準欄位群組
description: 查詢全域結構描述登入API以尋找並儲存建立客戶設定檔結構描述所需的標準XDM欄位群組的$ids。
doc-type: article
solution: Experience Platform
exl-id: 62017ece-eef2-4785-afed-5c690c00ed02
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%

---


# 取得標準欄位群組

>[!NOTE]
>
>**「欄位群組」**&#x200B;先前稱為&#x200B;**「Mixin」**，因此這些辭彙可在整個API請求和指南中互換使用。



## 請求XDM標準欄位群組

1. 按一下`XDM Schema Lab -> Create Schema`資料夾中的`Step 1 - Get XDM Standard Field Groups` API呼叫
1. 按一下`Send`按鈕以執行呼叫



**要求**

![步驟1 — 取得XDM標準欄位群組API要求](assets/get-standard-field-groups-step-1-request.jpeg "步驟1 — 要求")

>[!NOTE]
>
>請注意在下列請求URL中使用`global`值：
>
>https\：//platform.adobe.io/data/foundation/schemaristry/**global**/mixins
>
>`global`僅用於請求XDM標準元件（在此例中為欄位群組/mixin）。 Experience Platform XDM登入中有兩種型別的擁有者： Adobe和租使用者（即自訂）。
>
>- Adobe建立的物件在任何XDM清單或查詢請求中一律使用`global`這個字
>- 租使用者建立的物件（亦即自訂）在任何XDM清單或查詢呼叫中一律使用`tenant`這個字



**回應**

![API回應清單XDM標準欄位群組](assets/get-standard-field-groups-step-1-response.png "步驟1回應")


## 識別必要的XDM標準欄位群組

結構描述一律由一或多個欄位群組和類別組成。  對於Connection 5G Individual Profile結構描述，請找到結構描述所需的標準XDM欄位群組。

- 人口統計細節
- 個人聯絡詳細資訊
- 同意和偏好設定詳細資料



1. 搜尋通話回應中的`Demographic Details`欄位群組
1. 複製欄位群組的`$id`並將其儲存到某處以供日後參考
1. 對上述其他兩個欄位群組重複步驟1和2

![人口統計詳細資料欄位群組位於API回應](assets/get-standard-field-groups-demographic-details-field-group.png)

>[!WARNING]
>
>在您將所有三(3) `$ids`儲存到某處之前，請勿繼續。  稍後需要他們才能建立客戶帳戶結構描述
