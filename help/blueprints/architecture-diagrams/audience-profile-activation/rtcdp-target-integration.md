---
title: Adobe Real-Time CDP與Adobe Target整合
description: 瞭解Real-Time Customer Data Platform對象和設定檔內容如何透過Edge Network與Adobe Target整合。
landing-page-description: 瞭解Real-Time Customer Data Platform對象和設定檔內容如何透過Edge Network與Adobe Target整合。
short-description: 瞭解Real-Time Customer Data Platform對象和設定檔內容如何透過Edge Network與Adobe Target整合。
solution: Real-Time Customer Data Platform, Target, Experience Platform
kt: 7194
thumbnail: thumb-web-personalization-scenario2.jpg
exl-id: 29667c0e-bb79-432e-af3a-45bd0b3b43bb
TQID: https://experienceleague.adobe.com/1ti2SqfAFOgnKbaJ70xwGI-xHDE1WXJ7-oTStcJJy1E
product_v2:
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
    internal-label: Target
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
  - id: fdddec33-c9cb-4459-b8b6-2664395a6f10
    internal-label: Real-Time Customer Data Platform
feature_v2:
  - id: a37e4ecd-c740-426a-addf-cb1b483c5c5a
    internal-label: Segmentation
  - id: adee20bd-51f4-461d-b9db-d215f8756eeb
    internal-label: Audiences
  - id: ba929a52-9339-4154-9487-317dc875a3c7
    internal-label: Use cases
  - id: c132d929-fa62-4271-803e-b823be07b914
    internal-label: Profile
  - id: c93393a4-e558-47e1-992e-c91ed4d480ce
    internal-label: Implementation
  - id: daec7ead-f475-492a-a3b3-02ae08565d6f
    internal-label: Implementation
subfeature_v2:
  - id: cbd4a8d8-97a6-4ac9-b8d6-b6c1f28d3342
    internal-label: Segments
  - id: cdd3e38b-fec2-4f39-8b10-83ddaab1ac16
    internal-label: B2B
  - id: d1823595-9241-4128-8a33-e4ac3bf08773
    internal-label: Audiences
  - id: ee602049-8a18-43df-9299-a689a025a371
    internal-label: Use cases
  - id: fd0ff162-b6d3-4a11-8aeb-e165a01c0f0a
    internal-label: at.js
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: c2be0313-b3ae-45e0-b454-d20bf54b23f2
    internal-label: Measurement
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
    internal-label: Optimization
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
    internal-label: Insights
source-git-commit: ce7331f279a6e59db95ca3b763148440598cde84
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 17%
---
# Adobe Real-Time CDP與Adobe Target整合

此架構顯示[!DNL Real-Time Customer Data Platform]與[!DNL Adobe Target]如何透過Edge Network整合。 它可協助您在邊緣的即時受眾評估與使用Target共用串流或批次受眾之間選擇。

## 應用程式

* [!DNL Real-Time Customer Data Platform]
* [!DNL Adobe Target]
* [!DNL Experience Platform] Edge Network
* Experience Platform Web SDK或Edge Network伺服器API

## 選擇整合方法

### 邊緣的即時受眾評估

當[!DNL Adobe Target]需要邊緣評估對象和設定檔屬性以進行相同頁面或下一頁個人化時，請使用此方法。 實作Web SDK或Edge Network伺服器API，並設定啟用[!DNL Adobe Target]和[!DNL Experience Platform]服務的資料流。

### 串流和批次對象分享至Target

當在[!DNL Real-Time Customer Data Platform]中評估的對象需要在[!DNL Adobe Target]中可用而沒有即時邊緣評估時，請使用此方法。 在預設的生產沙箱中設定[!DNL Adobe Target]目的地。 只有在即時邊緣評估或自訂身分名稱空間查詢時，才需要實作網頁SDK或Edge Network伺服器API。

## 架構圖

此圖表顯示資料收集、 Edge Network、[!DNL Real-Time Customer Data Platform]和[!DNL Adobe Target]之間的主要整合點。

![Real-Time Customer Data Platform與Adobe Target整合的架構](assets/real_time_cdp_target.png){zoomable="yes"}

## 資料流程圖

此序列顯示使用者端要求到達Edge Network、評估對象和設定檔內容、傳送個人化要求給[!DNL Adobe Target]，以及將產生的體驗傳回使用者端的方式。

![Real-Time Customer Data Platform與Adobe Target整合的資料流程](assets/real_time_cdp_target_data_flow_detail.png){zoomable="yes"}

## 實施考量

* [!DNL Adobe Target]和[!DNL Real-Time Customer Data Platform]必須使用相同的IMS組織。
* [!DNL Adobe Target]目的地支援[!DNL Real-Time Customer Data Platform]中的預設生產沙箱。
* 若要在邊緣進行自訂身分名稱空間查閱，請使用網頁SDK或Edge Network伺服器API ，並在身分對應中包含每個身分。
* 如果使用at.js，設定檔整合僅支援ECID身分名稱空間。

## 相關文件

### 設定整合

* [適用於即時客戶資料平台的Adobe Target連線](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=zh-Hant)
* [Edge資料流設定](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=zh-Hant)

### 在邊緣實作

* [Experience Platform Web SDK檔案](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html?lang=zh-Hant)
* [Experience Platform標籤檔案](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=zh-Hant)
* [Experience Cloud ID服務檔案](https://experienceleague.adobe.com/docs/id-service/using/home.html?lang=zh-Hant)

### 評估客群

* [Experience Platform區段概觀](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=zh-Hant)
* [即時分段](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/edge-segmentation.html?lang=zh-Hant)
* [串流區段](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=zh-Hant)
* [合併原則設定](https://experienceleague.adobe.com/docs/experience-platform/profile/merge-policies/ui-guide.html?lang=zh-Hant#create-a-merge-policy)
