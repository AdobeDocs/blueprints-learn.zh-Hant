---
hold: true
title: 取得設定檔類別
description: 呼叫全域結構描述登入API以擷取並儲存XDM Individual Profile類別的$id，以用於自訂結構描述。
doc-type: article
solution: Experience Platform
exl-id: d87c21a2-dad4-4666-b917-cdf8e16058d4
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---


# 取得設定檔類別

## 執行步驟3 — 取得設定檔類別

1. 按一下`XDM API Lab -> Create Schema`資料夾中的`Step 3 - Get Profile Class`要求
1. 按一下`Send`按鈕以執行

![步驟3 — 取得設定檔類別API要求](assets/get-profile-class-step-3-api-request.jpeg "步驟3 — 取得設定檔類別API要求")

>[!NOTE]
>
>請注意，在GET要求中，`global`路徑： .../schemaristry/**global**/classes。 請記住，使用`global`會告訴結構描述登入，我們只想傳回Adobe標準XDM物件


## 找到並儲存類別$id

在您執行API要求之後，請執行以下步驟來尋找並儲存XDM個別設定檔類別的`$id`。

1. 搜尋回應中的`XDM Individual Profile`類別
1. 複製`XDM Individual Profile`類別的`$id`並將其儲存到您稍後可以參考的位置。

位於API回應中的![XDM個別設定檔類別](assets/get-profile-class-xdm-individual-profile-class.png "XDM個別設定檔類別")

>[!WARNING]
>
>在您將`$id`儲存到某處之前，請勿繼續。  稍後需要建立客戶帳戶結構描述
