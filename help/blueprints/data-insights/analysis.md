---
title: 資料分析與智慧藍圖
description: 此 Blueprint 顯示 Adobe Experience Platform 中對資料湖中現有資料執行探索查詢和分析的功能。
solution: Experience Platform
kt: 7207
thumbnail: null
exl-id: 3b22dfdd-3fbe-40b3-b798-1ee983723039,a972ea56-d1c8-45da-9044-ed31222a2441
translation-type: tm+mt
source-git-commit: 9e0954334e8b8a8c5bf52651611e7afa165f6d21
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 44%

---

# 資料分析與智慧藍圖

Data Analysis and Intelligence包括Adobe Experience Platform內部對資料湖中存在的資料執行探索性查詢和分析的能力。

Experience Platform的[!UICONTROL 查詢服務]允許對資料執行SQL查詢。 [!UICONTROL Data Science ] Workspace可讓資料探索、資料科學和機器學習工作量在資料上執行。

此外，Experience Platform允許與第三方SQL客戶端、介面和Business Intelligence(BI)工具的連接，使用[!DNL PostgreSQL]協定直接連接、訪問和查詢Experience Platform中的資料。

某些護欄適用於查詢超時和查詢結果中包含的資料量，如Blueprint詳細資訊中所述。

## 使用案例

* 互動式查詢與資料彙總
* 存取擷取資料列與欄以進行探索和驗證
* 透過 Business Intelligence 工具進行儀表板處理與視覺化

## 應用程式

* Adobe Experience Platform

## 架構

<img src="assets/data_exploration.svg" alt="企業資料探索與報告 Blueprint 的參考架構" style="border:1px solid #4a4a4a" />

## 護欄

* 互動式查詢限時 10 分鐘
* UI 中傳回限 100 條記錄
* SQL 連接器中傳回限 50,000 條記錄

## 實施步驟

1. 為資料湖的資料擷取設定資料集與方案。
1. 擷取資料。
1. 確認資料可供[!UICONTROL 查詢服務]和[!UICONTROL 資料科學工作區]用於原始存取和查詢。
1. 將Business Intelligence工具和SQL客戶端連接到[!UICONTROL 查詢服務]，以實現可視化、資料查詢和探索。

## 相關文件

* [Adobe Experience Platform Intelligence 產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [Query Service 文件](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=zh-Hant)
