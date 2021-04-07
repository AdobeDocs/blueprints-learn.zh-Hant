---
title: 資料準備和擷取藍圖
description: 這份藍圖顯示了在Adobe Experience Platform收集和準備資料的所有方法。
solution: Experience Platform,Data Collection
kt: 7204
thumbnail: null
exl-id: 21f8a73e-6be7-448e-8cd3-ebee9fc848e1,5c3c94b6-c928-4d93-8b38-f8bd2aad2e68
translation-type: tm+mt
source-git-commit: 77ddc003d4328074ad269de5837a02f5e6d6add5
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 0%

---

# 資料準備和擷取藍圖

資料準備和擷取藍圖涵蓋所有資料準備和擷取至Adobe Experience Platform的方法。

資料準備包括將來源資料對應至Experience Data Model(XDM)架構。 它還包括對資料執行轉換，包括日期格式、欄位拆分／串連／轉換，以及記錄的連接／合併／重新鍵入。 資料準備有助於統一客戶資料，提供匯整／篩選分析，包括報告或準備客戶個人檔案組合／資料科學／啟動的資料。

## 建築

<img src="assets/dataingest.svg" alt="資料準備與擷取藍圖的參考架構" style="border:1px solid #4a4a4a" />

## 資料擷取方法

| 擷取方法 | 說明 |
|------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 網頁／行動SDK | 延遲：<ul><li>即時——與Edge Network相同的頁面集合</li><li>串流擷取至描述檔~1分鐘</li><li>串流擷取至資料湖（微批次~15分鐘）</ul>檔案： <ul><li>[網頁SDK](https://experienceleague.corp.adobe.com/docs/web-sdk.html)</li><li>[行動SDK](https://experienceleague.adobe.com/docs/mobile.html?lang=en)</li></ul> |
| 串流來源 | 延遲：<ul><li>即時——與Edge Network相同的頁面集合</li><li>串流擷取至描述檔~1分鐘</li><li>串流擷取至資料湖（微批次~15分鐘）</li></ul>[檔案](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=en#connectors) |
| 串流API | 延遲：<ul><li>即時——與Edge Network相同的頁面集合</li><li>串流擷取至描述檔~1分鐘</li><li>串流擷取至資料湖（微批次~15分鐘）</li><li>7 GB/小時</li></ul>[檔案](https://experienceleague.adobe.com/docs/experience-platform/ingestion/streaming/overview.html?lang=en#what-can-you-do-with-streaming-ingestion%3F) |
| ETL工具 | 使用ETL工具，在將擷取至Experience Platform之前修改和轉換企業資料。<br><br>延遲：<ul><li>根據外部ETL工具調度的時序，在提取方法的基礎上應用標準的提取保障。</li></ul> |
| 批來源 | 已排程從來源擷取<br>延遲：~ 200 GB/小時<br><br>[說明檔案](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=en#connectors)<br>[視訊Tutorials](https://experienceleague.adobe.com/docs/platform-learn/tutorials/sources/overview.html) |
| 批次API | 延遲：<ul><li>依大小和流量載入大約45分鐘，批次擷取至描述檔</li><li>依據大小和流量負載，批次擷取資料湖</li></ul>[檔案](https://experienceleague.adobe.com/docs/experience-platform/ingestion/batch/overview.html?lang=en#batch) |
| Adobe應用程式連接器 | 自動收錄源自Adobe Experience Cloud應用程式的資料<ul><li>Adobe Analytics:[說明檔案](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html?lang=en#connectors)和[教學課程影片](https://experienceleague.adobe.com/docs/platform-learn/tutorials/sources/ingest-data-from-adobe-analytics.html)</li><li>Audience Manager:[說明檔案](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/audience-manager.html?lang=en#connectors)和[教學課程影片](https://experienceleague.adobe.com/docs/platform-learn/tutorials/sources/ingest-data-from-aam.html)</li></ul> |


## 資料準備方法

| 資料準備方法 | 說明 |
|------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 資料科學工作區——資料準備 | 模型驅動的轉換，指令碼式轉換。<br>[檔案](https://experienceleague.adobe.com/docs/experience-platform/data-science-workspace/home.html?lang=en) |
>[!NOTE]
>
>|外部ETL工具（[!DNL Snaplogic]、[!DNL Mulesoft]、[!DNL Informatica]等） |在ETL工具中執行複雜轉換，並使用標準Experience Platform來源API或連接器來擷取產生的資料。                                                                                                                                                               |

|查詢服務——資料準備                                  |將聯接、拆分、合併、轉換、查詢和篩選資料放入新資料集。 使用建立表作為選擇(CTAS)<br>[文檔](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=en#sql)                                                                       |
| XDM映射器和資料準備功能（流和批處理）     |在Experience Platform擷取期間，將CSV或JSON格式的來源屬性對應至XDM屬性。<br>在所吸收的資料上計算函式；即資料格式、拆分、串連等。<br>[檔案](https://experienceleague.adobe.com/docs/experience-platform/data-prep/home.html?lang=en) |

## 相關部落格文章

* [在Adobe Experience PlatformJourney Orchestration利用外部資料平台](https://medium.com/adobetech/leveraging-external-data-platforms-in-adobe-experience-platform-journey-orchestration-54fc6134fe17?source=your_stories_page-------------------------------------)
* [高吞吐量擷取（冰山）](https://medium.com/adobetech/high-throughput-ingestion-with-iceberg-ccf7877a413f?source=your_stories_page-------------------------------------)
* [Adobe Experience Platform查詢服務技巧（編寫查詢和儲存派生資料集）](https://medium.com/adobetech/query-service-tricks-in-adobe-experience-platform-writing-queries-and-storing-derived-datasets-eaee0d6d683e?source=your_stories_page-------------------------------------)
* [深入挖掘Adobe Experience Platform的體驗資料模型，更全面地瞭解即時客戶個人檔案的強大功能](https://medium.com/adobetech/digging-into-adobe-experience-platforms-experience-data-model-to-more-fully-understand-the-power-3e109271e04f?source=your_stories_page-------------------------------------)
* [Adobe Experience Platform探索性資料分析初探](https://medium.com/adobetech/an-introductory-look-at-exploratory-data-analysis-on-adobe-experience-platform-1bfce7501d9a?source=your_stories_page-------------------------------------)
* [在Adobe Experience Platform大規模資料科學中建模XDM資料](https://medium.com/adobetech/modeling-xdm-data-for-data-science-at-scale-on-adobe-experience-platform-222bb2a6dbf7?source=your_stories_page-------------------------------------)
