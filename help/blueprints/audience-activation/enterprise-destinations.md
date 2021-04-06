---
title: 個人檔案與企業目標Audience Activation
description: 個人檔案與企業目標Audience Activation
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7086
translation-type: tm+mt
source-git-commit: f48f7e6d712db97e94d9b60309e15539f3ec4c9e
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 0%

---


# 企業目標的設定檔和Audience Activation方案

複製並更新企業資料儲存區的設定檔變更，以利啟動和報告使用案例。

透過客戶從即時客戶資料平台到企業系統和應用程式的動作通知，向客戶發起銷售或支援動作。

## 使用案例

* 針對雲端儲存目的地或串流目的地的個人檔案和受眾啟動，以便企業追蹤、儲存、分析和啟動客戶資料和見解。

## 應用程式

* Adobe Experience Platform啟動

## 建築

<img src="assets/enterprise_destination.svg" alt="企業啟動方案的參考架構" style="border:1px solid #4a4a4a" />

## 瓜德賴爾

[描述檔與區段指南](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)

延遲和吞吐量閾值：

串流區段：

* 串流區段最多需要5分鐘，每秒最多需要1500個事件
* 串流啟動最多11分鐘

批次分段：
每天一次，或透過API手動啟動臨機

* 每個工作大約1小時，最多10 TB配置檔案儲存大小
* 每個作業大約2小時，10 TB到100 TB配置檔案儲存大小

## 實施步驟

1. 建立要收錄的資料結構
1. 建立資料集以供收錄
1. 在架構上設定正確的身分和身分名稱空間，以確保所擷取的資料可接合到統一的描述檔中。
1. 啟用結構描述檔和資料集以進行描述檔處理。
1. 設定任何資料擷取來源
1. Experience Platform中的作者區段，以批次或串流方式評估。 系統會自動判斷區段是評估為批次還是串流。
1. 設定目標，以便將描述檔屬性和觀眾成員資格共用至所需目標。

## 實作考量

啟動屬性和身分

* 即時客戶資料平台可啟用觀眾會籍，以及針對已選取要啟動之區段成員的個人檔案所發生的屬性和身分變更。 因此，如果使用案例是要啟用屬性和／或身分識別，則必須定義全域區段，其中必須包含所有要傳送屬性／身分更新的描述檔。 在定位區段後，即可選取要啟動的區段和所需屬性作為目標設定的一部分。
* 請注意，批次目標不支援僅啟動屬性變更事件。 觀眾會籍完整或增量可隨選取的屬性一起傳送，以進行啟動，但僅屬性變更事件無法透過批次目標啟動。

批次區段啟動至串流目標

* 支援「串流目的地的批次區段啟動」。 當區段工作完成以進行串流啟動時，批次區段工作會將訊息置於管道上

將串流區段啟動至批次目標

* 支援將串流區段啟動至批次目的地。 批目標計畫將根據批處理目標計畫導出配置檔案的段成員資格。 這包括透過串流和批次方法所決定的區段成員資格。

啟動體驗事件

* 目前不支援啟動原始體驗事件。 若要針對體驗事件啟動，必須使用必要規則建立區段，其中包含／排除要啟動的體驗事件邏輯。 這會建立根據體驗事件定義的區段——而區段成員資格可以啟動為原始體驗事件的代理。 另請考慮運用Launch Server Side來啟動透過SDK收集的原始體驗事件。

## 相關檔案

* [即時客戶資料平台產品說明](https://helpx.adobe.com/legal/product-descriptions/real-time-customer-data-platform.html)
* [描述檔與區段指南](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* [區段檔案](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)
* [目標檔案](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html)

## 相關影片與Tutorials

* [即時客戶資料平台概觀](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html)
* [即時客戶資料平台示範](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html)
* [建立區段](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html)