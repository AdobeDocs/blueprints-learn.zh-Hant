---
title: 資料分析與智慧藍圖
description: 這份藍圖顯示了Adobe Experience Platform內部對資料湖中存在的資料執行探索性查詢和分析的能力。
solution: Experience Platform
kt: 7207
thumbnail: null
exl-id: 3b22dfdd-3fbe-40b3-b798-1ee983723039
translation-type: tm+mt
source-git-commit: 844fff1cefe367575beb5c03aa0f0d026eb9f39b
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# 資料分析與智慧藍圖

Data Analysis and Intelligence包括Adobe Experience Platform內部對資料湖中存在的資料執行探索性查詢和分析的能力。

Experience Platform的查詢服務允許對資料執行SQL查詢。 資料科學工作區可讓資料探索、資料科學和機器學習工作量在資料上執行。

此外，Experience Platform允許與第三方SQL客戶端、介面和Business Intelligence(BI)工具的連接，使用PostgreSQL協定直接連接、訪問和查詢Experience Platform內的資料。

某些護欄適用於查詢超時和查詢結果中包含的資料量，如方案詳細資訊中所述。

## 使用案例

* 資料的互動式查詢和聚合
* 行與欄存取所擷取的資料以供探索和驗證
* 透過Business Intelligence工具控制面板和視覺化資料

## 應用程式

* Adobe Experience Platform

## 藍本

| 藍本 | 說明 | Experience Cloud應用程式／服務 |
|---|---|---|
| **資料探索——資料的原始查詢** | <ul><li>使用交互查詢用戶介面或連接的SQL客戶端在資料湖中寫入和執行SQL查詢。 Data Science Workspace也可用來查詢及洞察Experience Platform中的原始資料。</li></ul> | <ul><li>Adobe Experience Platform</li></ul> |
| **企業儀表板** | <ul><li>將Business Intelligence工具與Experience Platform連接，以視覺化資料，以便控制面板和報告使用案例。</li></ul> | <ul><li>Adobe Experience Platform</li></ul> |

## 建築

<img src="assets/dataexplore.svg" alt="企業資料探索與報告藍圖的參考體系結構" style="border:1px solid #4a4a4a" />

## 瓜德賴爾

* 互動式查詢的10分鐘時限
* 在UI中傳回100個記錄限制
* 通過SQL連接器返回的50,000個記錄限制

## 實施步驟

1. 設定資料集和結構，以便將資料擷取至資料湖。
1. 收錄資料。
1. 確認資料可供查詢服務和資料科學工作區用於原始存取和查詢。
1. 將Business Intelligence工具和SQL用戶端連接至查詢服務，以進行視覺化、資料查詢和探索。

## 相關檔案

* [Adobe Experience Platform智慧產品說明](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [查詢服務文檔](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=en)
