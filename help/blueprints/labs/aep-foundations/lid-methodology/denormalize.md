---
hold: true
title: 非正規化
description: 套用LID方法的反正規化規則，將橋接器和相依表格從ERD摺疊回其父設定檔、事件和查詢表格。
doc-type: article
solution: Experience Platform
exl-id: c98c9f58-03bc-4b28-becb-f84f3de04300
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---


# 非正規化

## 講座

在本影片中，您將瞭解將查閱和橋接表格摺疊回父表格的三個反標準化規則，以及個人化和串流區段需求如何影響這些決策。

>[!VIDEO](https://video.tv.adobe.com/v/3459083/?quality=12&learn=on)



## 實驗室詳細資訊

>[!NOTE]
>
>本實驗僅針對Connection 5G倉儲ERD

## 反正規化規則：

1. 在關聯式模型中標示為&quot;**D**&quot;且有1\：M基數或標示為&quot;**B**&quot;的任何資料表，都會在父資料表上定義為物件陣列或對應
1. 由規則#1引發，在將&quot;**D**&quot;或&quot;**B**&quot;資料表（做為陣列或對應）反正規化之前，請詢問資料表以決定如何將這些資料表反正規化回其父資料表
1. 在關聯式模型中標示為&quot;**D**&quot;且基數為M：1的任何資料表都會做為物件或其父資料表上的欄位清單

## 個人化規則的非正規化：

建置資料模型時，請務必記得檢閱客戶使用案例。  請牢記以下事項：

- 串流區段在評估時無權存取查閱表格
- 個人化內容只能存取設定檔的特徵和區段會籍

![套用個人化非正規化時的連線5G使用案例](assets/denormalize-connection-5g-use-cases.png "連線5G使用案例")

>[!NOTE]
>
>請記得在本實驗期間參考Connection 5G訓練案例.pdf！



## 步驟1 — 填入個別設定檔表格

1. 將任何相關&quot;**B**&quot;或&quot;**D**&quot;結構描述中的需要反正規化的欄位寫回客戶帳戶表格
1. 檢閱上方使用案例，瞭解支援串流細分和/或個人化需要哪些其他欄位？ 將這些欄位新增至表格



## 步驟2 — 填寫體驗事件表格

1. 將需要反正規化的欄位從任何相關的&quot;**B**&quot;或&quot;**D**&quot;表格寫入Billing和Orders表格
1. 檢閱上方使用案例，瞭解支援串流細分和/或個人化需要哪些其他欄位？ 將這些欄位新增至表格



## 步驟3 — 填寫查閱表格

1. 將需要反正規化的欄位寫入任何相關&quot;**B**&quot;或&quot;**D**&quot;資料表的Product查閱資料表中
1. 檢閱上方使用案例，瞭解支援串流細分和/或個人化需要哪些其他欄位？ 將這些欄位新增至表格




## 檢閱

以下影片會檢閱Connection 5G表格如何反正規化為陣列和物件，以及贏取和追加銷售使用案例如何需要將其他欄位帶回主要設定檔和事件表格。

>[!VIDEO](https://video.tv.adobe.com/v/3459086/?quality=12&learn=on)
