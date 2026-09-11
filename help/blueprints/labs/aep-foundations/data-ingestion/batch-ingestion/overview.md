---
hold: true
title: 批次擷取
description: 修正對應和資料品質錯誤時，透過批次擷取將客戶帳戶資料載入資料湖和設定檔。
doc-type: overview-page
solution: Experience Platform
exl-id: 76830e79-8fc0-4fda-98b1-2c1de19e8158
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---


# 批次擷取

## 學習目標

在本練習中，您會將客戶帳戶資料從檔案型來源聯結器載入AEP資料湖，然後載入設定檔。 您將學習下列內容：

1. 瞭解直通對應
1. 修正ML產生的傳遞對應
1. 使用來源資料預覽以檢查任何資料品質問題
1. 排程資料流執行
1. 處理因必填欄位中缺少值導致的錯誤
1. 處理因資料型別不符錯誤所導致的錯誤
1. 處理資料擷取錯誤，並從此類失敗中復原
1. 反複使用測試資料以產生完整的對應集。

>[!NOTE]
>
>如果您未在先前Labs中完成客戶帳戶結構描述建立，您可以瀏覽結構描述目錄並改用&#x200B;**dep：客戶帳戶**
