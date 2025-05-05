---
title: Experience Platform (AEP)和應用程式架構圖
description: 檢視顯示Adobe Experience Platform (AEP)與其他Experience Cloud應用程式和應用程式服務之關聯的架構圖。
solution: Experience Platform, Campaign, Analytics, Target, Customer Journey Analytics, Journey Orchestration, Real-Time Customer Data Platform
kt: 7199
thumbnail: null
exl-id: 9b12cd7a-5e5f-443a-91a1-44273cdabc2d
source-git-commit: 495a2480828e2c6b4caa41226f4fe67437b081c1
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 10%

---

# Adobe Experience Platform和應用程式架構圖

這些架構圖表顯示Experience Platform (AEP)與其他Experience Cloud應用程式和應用程式服務的關聯性。

>[!MORELIKETHIS]
>
>Experience Cloud應用程式整合的[整合設定](https://experienceleague.adobe.com/docs/integrations-learn/experience-cloud/overview.html?lang=zh-Hant)。


## 架構圖

此架構圖顯示 Adobe Experience Platform 如何與 Adobe Experience Cloud 應用程式及應用程式服務連結。

<img src="assets/aep+apps.svg" alt="Experience Platform 與應用程式" style="border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;" class="modal-image" />

## 概觀圖表

<img src="assets/aep+apps_overview.svg" alt="Experience Platform 與應用程式" style="border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;" class="modal-image" />

## 詳細的架構圖

<img src="assets/aep+apps_detailed.svg" alt="Experience Platform 與應用程式" style="border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;" class="modal-image" />

>[!VIDEO](https://video.tv.adobe.com/v/3422779/?quality=12&learn=on&captions=chi_hant)

## AEP與Experience Cloud應用程式整合

| 應用程式 | Experience Platform 到應用程式 | 應用程式到 Experience Platform |
|------------------------------|-----------------------------------|-----------------------------------|
| **Ad Cloud** |  — 透過Audience Manager，Real-time Customer Data Platform中定義的對象可以共用給Ad Cloud以便定位。 |  — 目前未整合 |
| **Analytics** |  — 透過Web/行動SDK收集的資料可轉送至Adobe Analytics。 | - Analytics收集的資料可以傳送至Experience Platform Data Lake和個人資料存放區。 [Analytics Data Connector](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html?lang=zh-Hant) |
| **Audience Manager** |  — 與Audience Manager共用Real-time Customer Data Platform中定義的對象，以啟用第三方Cookie目的地。 |  — 從Audience Manager收集並評估的資料以及對象成員資格，可共用至Experience Platform Data Lake和個人資料存放區。 [Audience Manager 來源連接器](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/audience-manager.html?lang=zh-Hant) |
| **Adobe Campaign** |  — 可與Campaign Classic共用Real-time Customer Data Platform中定義的對象，以啟動行銷活動。 | - Campaign收集的互動和行銷活動資料可擷取至Experience Platform，進一步用於對象建立、Customer Journey Analytics和查詢服務。 |
| **Campaign Standard** |  — 可與Campaign Standard共用Real-time Customer Data Platform中定義的對象，以啟動行銷活動。 |  — 可將Campaign收集的互動和行銷活動資料擷取至Experience Platform以供進一步使用。 |
| **Customer Journey Analytics** |  — 收集並擷取至Experience Platform Data Lake的資料，可在Customer Journey Analytics中處理。 <br> — 來自Real-time Customer Data Platform的設定檔和受眾資料可擷取到CJA。 [RTCDP與CJA整合](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/data-ingestion/ingest-aep-segments.html?lang=zh-Hant) |  — 在CJA中建立受眾，並將受眾結果分享至Real-time Customer Data Platform。 [CJA 對象發佈](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html?lang=zh-Hant) |
| **Experience Manager** |  — 可在伺服器端存取Experience Platform設定檔，以便在Experience Manager中提供個人化體驗。 |  — 目前沒有整合，而是透過Experience Platform網頁和Mobile SDK收集在Experience Manager網站上執行的互動。 |
| **Journey Optimizer** | - Journey Optimizer可使用擷取至Experience Platform的資料事件和設定檔。 | - Journey Optimizer產生的互動和行銷活動資料會收集到Experience Platform以供進一步使用。 |
| **Adobe Commerce** |  — 在Real-time Customer Data Platform中建置的設定檔和對象可用於Adobe Commerce中的個人化。 | -Adobe Commerce原生資料可以透過Adobe Commerce來源聯結器傳送至Experience Platform。 |
| **Marketo** |  — 可與Marketo共用Real-time Customer Data Platform中定義的對象，以啟動行銷活動並更新物件。 | - Marketo帳戶、聯絡人和行銷活動資料會擷取至Experience Platform以供進一步分析。 [Marketo Engage聯結器](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo.html?lang=zh-Hant) |
| **Real-Time CDP** |  — 內嵌至Experience Platform的資料是即時客戶個人檔案的來源，可支援Real-time Customer Data Platform。 |  — 對象和設定檔量度會傳送至Experience Platform Data Lake以供深入分析。 |
| **Target** |  — 可以將Real-time Customer Data Platform的對象和設定檔屬性共用給Target以進行個人化。 |  — 針對Target體驗收集的資料可傳送至Experience Platform，用於建立受眾及進行分析。 |
