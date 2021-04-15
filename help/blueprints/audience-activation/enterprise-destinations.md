---
title: 企業目標受眾與個人檔案啟動藍圖
description: 受眾和個人檔案啟動至企業目標
solution: Experience Platform,Real-time Customer Data Platform
kt: 7475
exl-id: 32133174-eb28-44ce-ab2a-63fcb5b51cb5,None
translation-type: tm+mt
source-git-commit: b0664edc3d29d693d33eefc3b3c6da8bf7308224
workflow-type: tm+mt
source-wordcount: '660'
ht-degree: 0%

---

# 企業目標受眾與個人檔案啟動藍圖

以串流或批次方式從[!UICONTROL 即時客戶資料平台]分享個人檔案和觀眾變更和事件至企業資料存放區和應用程式。 這些描述檔和受眾事件可用於啟動客戶的銷售或支援活動，例如跟蹤放棄的應用程式流程或網路研討會註冊，或用[!UICONTROL 即時客戶資料平台]的最新客戶屬性和智慧更新企業應用程式。

## 使用案例

* 針對雲端儲存目的地或串流目的地的個人檔案和受眾啟動，以進行企業追蹤、儲存、分析和啟動客戶資料和見解。

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
每天一次，或透過API手動啟動臨機。

* 每個工作大約1小時，最多10 TB配置檔案儲存大小
* 每個作業大約2小時，10 TB到100 TB配置檔案儲存大小

## 實施步驟

1. 建立要收錄的資料結構。
1. 建立資料集以供收錄。
1. 在架構上設定正確的身分和身分名稱空間，以確保所擷取的資料可接合到統一的描述檔中。
1. 啟用結構描述檔和資料集以進行描述檔處理。
1. 設定任何資料擷取來源。
1. 在Experience Platform中編寫區段，以批次或串流方式評估。 系統會自動判斷區段是評估為批次還是串流。
1. 設定目標，以便將描述檔屬性和觀眾成員資格共用至所需目標。

## 實作考量

啟用屬性和身分

* [!UICONTROL 即時客戶資料平台可啟] 用觀眾會籍，以及針對選取要啟動之區段成員的個人檔案所發生的屬性和身分變更。如果您的目標是啟用屬性或身分識別，您必須定義全域區段，其中包含所有要傳送屬性和身分更新的描述檔。 此時，您可以選取要在目標設定中啟動的區段和所需屬性。
* 請注意，批次目標不支援啟動僅限屬性的變更事件。 完整或增加的觀眾會籍可隨選取的屬性一起傳送，以進行啟動，但您無法透過批次目的地啟用僅限屬性的變更事件。

將批次區段啟用至串流目的地

* 支援「串流目的地的批次區段啟動」。 當區段工作完成以進行串流啟動時，批次區段工作會將訊息置於管道上

啟動串流區段至批次目的地

* 支援將串流區段啟動至批次目的地。 批目標計畫根據批目標計畫導出配置檔案段成員資格。 這包括透過串流和批次方法所決定的區段成員資格。

啟動體驗事件

* 不支援啟動原始體驗事件。 若要針對體驗事件啟動，必須使用包含或排除體驗事件邏輯的必要規則來建立區段。 這會建立根據體驗事件定義的區段，而且區段成員資格可以啟動為原始體驗事件的代理。 另請考慮使用[!UICONTROL 啟動伺服器端]來啟動透過SDK收集的原始體驗事件。

## 相關檔案

* [目標檔案](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html)
* [雲端儲存空間目標概觀](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/cloud-storage/overview.html?lang=en#catalog)
* [HTTP目標](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/http-destination.html?lang=en#overview)
* [[!UICONTROL 即時客戶資料平台產] 品說明](https://helpx.adobe.com/legal/product-descriptions/real-time-customer-data-platform.html)
* [描述檔與區段指南](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* [區段檔案](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)

## 相關影片與Tutorials

* [[!UICONTROL 即時客戶資料平] 台](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html)
* [即時客 [!UICONTROL 戶資料平台示範]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html)
* [建立區段](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html)
