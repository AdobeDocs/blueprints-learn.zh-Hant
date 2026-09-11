---
hold: true
title: 取得計畫結構描述ID
description: 查詢租使用者結構描述登入API以尋找並儲存計畫查閱結構描述的$id，以用於關係描述項中。
doc-type: article
solution: Experience Platform
exl-id: f66e0483-b5b3-4493-b752-c4e00211a8bd
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---


# 取得計畫結構描述ID

## 列出所有租使用者結構描述

1. 按一下`XDM Schema Lab -> Create Relationship Descriptors`資料夾中的`Step 1 - Get Lookup Schemas` API要求
1. 按一下`Send`按鈕執行API

![步驟1 — 取得查閱結構描述API要求](assets/get-plan-schema-id-step-1-get-lookup-schemas.jpeg "步驟1 — 取得查閱結構描述")

>[!NOTE]
>
>此GET呼叫會擷取結構描述登入的「租使用者」部分中存在的所有結構描述（即自訂建立的結構描述）。 我們只需要搜尋&#x200B;**計畫**&#x200B;結構描述，就能將其與客戶帳戶結構描述產生關聯。



## 識別計畫結構描述

1. 搜尋呼叫回應中的`dep: Plan [Lookup] `結構描述
1. 複製結構描述的`$id`並將其儲存到某處以供日後參考

![位於API回應中的dep：計畫查詢結構描述$id](assets/get-plan-schema-id-dep-lookup-plan-schema-sid.png "dep：查詢計畫結構描述$id")

>[!NOTE]
>
>此結構描述應該已經預先部署在您的沙箱中

>[!WARNING]
>
>您必須先將`$id`的結構描述儲存到某處，才能繼續。  稍後需要建立關係描述項
