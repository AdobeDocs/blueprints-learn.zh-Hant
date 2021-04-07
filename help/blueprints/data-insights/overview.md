---
title: 資料分析、智慧與AI/ML
description: 這份藍圖顯示了Adobe Experience Platform內部對資料湖中存在的資料執行探索性查詢和分析的能力。
solution: Experience Platform
kt: 7207
thumbnail: null
exl-id: 3b22dfdd-3fbe-40b3-b798-1ee983723039
translation-type: tm+mt
source-git-commit: f5d8b3fea11df0ffaeb59f0b53e93d76426ef252
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# 資料分析、智慧與AI/ML

企業資料探索與報告功能包括在Adobe Experience Platform內對資料湖中的資料執行探索式查詢和分析的能力。

Experience Platform的查詢服務允許對資料執行SQL查詢。 資料科學工作區可讓資料探索、資料科學和機器學習工作量在資料上執行。

此外，Experience Platform允許與第三方SQL客戶端、介面和Business Intelligence(BI)工具的連接，使用PostgreSQL協定直接連接、訪問和查詢Experience Platform內的資料。

某些護欄適用於查詢超時和查詢結果中包含的資料量，如方案詳細資訊中所述。

## 藍圖

| Blueprint | 說明 | Experience Cloud應用程式 |
|---|---|---|
| **[資料分析與智慧](analysis.md)** | <ul><li>資料準備和擷取藍圖涵蓋所有資料準備和擷取至Adobe Experience Platform的方法。</ul></li> | <ul><li> Adobe Experience Platform </ul></li> |
| **[描述檔擴充藍圖的自訂資料科學](data-science.md)** | <ul><li>啟動至已知的個人檔案型目標，例如電子郵件提供者、社交網路和廣告目標。 </li><li>使用離線屬性和事件，例如離線訂單、交易、CRM或忠誠度資料，以及線上行為，以進行線上鎖定和個人化。</li></ul> | <ul><li>Adobe Experience Platform</li><li> 即時客戶資料平台</li><li>Adobe Audience Manager（可選）</li></ul> |
