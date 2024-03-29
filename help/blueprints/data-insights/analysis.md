---
title: 資料分析與情報藍圖
description: 此 Blueprint 顯示 Adobe Experience Platform 中對資料湖中現有資料執行探索查詢和分析的功能。
solution: Experience Platform
kt: 7207
thumbnail: null
exl-id: a972ea56-d1c8-45da-9044-ed31222a2441
source-git-commit: b18d491fdefc57762932d1570401b5437bf97c76
workflow-type: ht
source-wordcount: '293'
ht-degree: 100%

---

# 資料分析與情報藍圖

資料分析與情報包括 Adobe Experience Platform 中對資料湖中現有資料執行探索查詢和分析的功能。

Experience Platform 的[!UICONTROL 查詢服務]顯示對資料執行的 SQL 查詢。

Experience Platform 還允許連接協力廠商 SQL 用戶端、介面及 Business Intelligence (BI) 工具，以使用[!DNL PostgreSQL]通訊協定直接連接、存取及查詢 Experience Platform 中的資料。

## 使用案例

* 互動式查詢與資料彙總
* 存取擷取資料列與欄以進行探索和驗證
* 透過 Business Intelligence 工具進行儀表板處理與視覺化

此處概述查詢服務的其他常見使用案例[查詢服務使用案例](https://experienceleague.adobe.com/docs/experience-platform/query/use-cases/abandoned-browse.html?lang=zh-Hant)

## 應用程式

* Adobe Experience Platform

## 架構

<img src="assets/data_exploration.svg" alt="企業資料探索與報告 Blueprint 的參考架構" style="width:90%; border:1px solid #4a4a4a" />

## 護欄

請參閱查詢服務產品文件，以了解關於最佳實踐與護欄的詳細資訊。
[查詢服務指南](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html?lang=zh-Hant)

## 實施步驟

1. 為要擷取的資料[建立資料方案](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm&amp;lang=zh-Hant)。
1. 為要擷取的資料[建立資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=zh-Hant)。
1. [擷取資料](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=zh-Hant)到 Experience Platform。
1. 確認資料可供[[!UICONTROL 查詢服務]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/queries/explore-data.html?lang=zh-Hant)使用。
1. [將 Business Intelligence 工具和 SQL 用戶端連接到 [!UICONTROL Query Service] 以進行視覺化、資料查詢和探索。](https://experienceleague.adobe.com/docs/experience-platform/query/clients/overview.html?lang=zh-Hant)

## 相關文件

* [Adobe Experience Platform Intelligence 產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [[!UICONTROL Query Service] 文件](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=zh-Hant)
