---
hold: true
title: 重述
description: 檢閱API模型化實驗室步驟，包括透過JSON修補建立客戶帳戶結構、標籤身分以及建立查詢關係。
doc-type: article
solution: Experience Platform
exl-id: 0279cd68-af7b-43b4-8c6c-d8f8f96f0c0e
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---


# 重述

以下影片會概述您如何透過API呼叫建立結構、身分和關係描述元，並示範如何使用JSON修補程式修改結構。

>[!VIDEO](https://video.tv.adobe.com/v/3459564/?quality=12&learn=on)

&#x200B;> [!TIP]
>
>首先恭喜您！ 透過API建置專案並不容易，但瞭解其運作方式將有助於您瞭解系統整體。 榮譽！



## 已建立客戶帳戶結構描述

您已由`$ref`建立結構描述，其中包含Adobe建立的欄位群組，以及您自己的自訂建立的欄位群組（即租使用者）。  您也`$ref`結構描述要代表的類別（即XDM個別設定檔）

![透過$ref](assets/recap-customer-account-schema.png "客戶帳戶結構描述參考欄位群組和類別的客戶帳戶結構描述")


## JSON修補程式識別客戶帳戶結構描述

您使用JSON修補程式方法來修改客戶帳戶結構，以新增欄位至計畫物件。 您是透過修補您在[建立自訂欄位群組](build-schema/create-custom-field-groups.md)中定義的名為`Customer Account Details`的`$ref`自訂欄位群組來達成此目的，而不是修補結構描述本身。

![JSON修補程式請求將planDescription欄位新增至「客戶帳戶詳細資料」欄位群組](assets/recap-json-patch-plan-description-field.png "planDescription欄位的JSON修補程式")


## 已標籤的身分欄位

在此步驟中，您已執行兩個相同的`POST`呼叫，以便為客戶帳戶結構描述內的`_devbc.customerID`和`personalEmail.address`欄位建立`Identity Descriptors`。

1. `_devbc.customerID`欄位已設定為&#x200B;**主要**&#x200B;身分
1. `personalEmail.address`欄位&#x200B;**未設定**&#x200B;為主要欄位

![客戶帳戶結構描述顯示主要和非主要身分描述項](assets/recap-marked-identity-fields.png "客戶帳戶結構描述身分識別欄位")

## 已建立查閱關係

最後一個步驟是從XDM ERD on Paper lab建立客戶帳戶與計畫結構描述之間的關係。  這要求您在客戶帳戶結構描述上建立關係描述項（亦即如何將`Customer Account`結構描述關聯至`dep: Plan [Lookup]`結構描述）和參考身分描述項。

![關聯性描述項和參照身分描述項，將客戶帳戶連結至計畫查詢結構描述](assets/recap-relationship-reference-identity-descriptors.png "關聯性和參照身分描述項")

>[!NOTE]
>
>`referenceIdentity`描述項會告訴即時客戶設定檔中，`Customer Account`結構描述中的哪個欄位符合哪個身分名稱空間。 請記住，定義查閱結構描述時，您必須將欄位標示為主要身分，並指派型別為`non-person`的名稱空間給它。
