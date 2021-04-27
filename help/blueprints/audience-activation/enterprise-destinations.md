---
title: 企業目標受眾與個人檔案啟動藍圖
description: 受眾和個人檔案啟動至企業目標
solution: Experience Platform,Real-time Customer Data Platform
kt: 7475
exl-id: 32133174-eb28-44ce-ab2a-63fcb5b51cb5,None
translation-type: tm+mt
source-git-commit: 2f35195b875d85033993f31c8cef0f85a7f6cccc
workflow-type: tm+mt
source-wordcount: '1003'
ht-degree: 15%

---

# 企業目標受眾與個人檔案啟動藍圖

以串流或批次方式從[!UICONTROL 即時客戶資料平台]分享個人檔案和觀眾變更和事件至企業資料存放區和應用程式。 這些描述檔和受眾事件可用於啟動客戶的銷售或支援活動，例如跟蹤放棄的應用程式流程或網路研討會註冊，或用[!UICONTROL 即時客戶資料平台]的最新客戶屬性和智慧更新企業應用程式。

## 使用案例

* 針對雲端儲存目的地或串流目的地的個人檔案和受眾啟動，以進行企業追蹤、儲存、分析和啟動客戶資料和見解。

## 應用程式

* Adobe Experience Platform 啟動

## 架構

<img src="assets/enterprise_destination.svg" alt="企業啟動方案的參考架構" style="border:1px solid #4a4a4a" />

## 護欄

[個人資料與細分準則](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hant)

### 區段評估與啟用的護欄

|分段類型 |頻率 |吞吐量 |延遲（區段評估） |延遲（區段啟動） |啟動裝載 |
|-|-|-|-|-|-|
|邊緣區隔 | Edge分段目前為測試版，可讓Experience Platform邊緣網路上評估有效的即時分段，以便透過Adobe Target和AdobeJourney Optimizer進行即時、相同的頁面決策。 |  |約100毫秒 |可立即在Adobe Target個人化、在Edge Profile中查閱個人檔案，以及透過Cookie型目的地啟動。 | Edge提供的觀眾會籍，適用於個人檔案查閱和Cookie型目的地。<br>Adobe Target和Journey Optimizer提供「對象會籍」和「個人檔案」屬性。|
|串流區段 |每次將新串流事件或記錄擷取至即時客戶個人檔案，且區段定義為有效的串流區段時。 <br>如需串流區 [段準](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=zh-Hant) 則的指引，請參閱區段檔案 |每秒最多1500個事件。| ~ p95 &lt;5分鐘 |串流目標：串流觀眾會籍會在約10分鐘內啟動，或根據目的地的需求進行微批次啟動。<br>計畫目標：串流觀眾會籍會根據排程的目的地傳送時間，以批次方式啟動。|串流目標：對象會籍變更、身分值和描述檔屬性。<br>計畫目標：對象會籍變更、身分值和描述檔屬性。|
|增量分段 |自上次增量或批次區段評估後，每小時一次新資料已納入即時客戶個人檔案。 |  |  |串流目標：增量觀眾會籍會在約10分鐘內啟動，或根據目的地需求進行微批。<br>計畫目標：增量觀眾會籍會根據排程的目的地傳送時間，以批次方式啟用。|串流目標：受眾會籍僅會變更和識別值。<br>計畫目標：對象會籍變更、身分值和描述檔屬性。|
|批次劃分 |根據預定的系統集排程，或透過API手動啟動臨機，每天一次。 |  |每個作業大約1小時（最多10 TB配置檔案儲存大小），每個作業2小時（10 TB到100 TB配置檔案儲存大小）。 批次區段工作效能取決於設定檔數目、設定檔大小和評估的區段數目。 |串流目標：根據目的地的需求，在區段評估或微批處理完成約10個內啟動批次觀眾會籍。<br>計畫目標：批次觀眾會籍會根據排程的目的地傳送時間來啟用。|串流目標：受眾會籍僅會變更和識別值。<br>計畫目標：對象會籍變更、身分值和描述檔屬性。 |



## 實施步驟

1. 建立要收錄的資料結構。
1. 建立資料集以供收錄。
1. 在方案上設定正確的身份和身份命名空間，以確保擷取的資料可以嵌入統一的設定檔。
1. 啟用結構描述檔和資料集以進行描述檔處理。
1. 設定任何資料擷取來源。
1. 在Experience Platform中編寫區段，以批次或串流方式評估。 系統會自動確定區段是作為批次還是串流評估。
1. 將用於設定檔屬性和對象會籍分享的目標設定為所需的目標。

## 實施考量

啟用屬性和身分

* [!UICONTROL 即時客戶資料平台可啟] 用觀眾會籍，以及針對選取要啟動之區段成員的個人檔案所發生的屬性和身分變更。如果您的目標是啟用屬性或身分識別，您必須定義全域區段，其中包含所有要傳送屬性和身分更新的描述檔。 此時，您可以選取要在目標設定中啟動的區段和所需屬性。
* 請注意，批次目標不支援啟動僅限屬性的變更事件。 完整或增加的觀眾會籍可隨選取的屬性一起傳送，以進行啟動，但您無法透過批次目的地啟用僅限屬性的變更事件。

將批次區段啟用至串流目的地

* 支援「串流目的地的批次區段啟動」。 當區段工作完成以進行串流啟動時，批次區段工作會將訊息置於管道上

啟動串流區段至批次目的地

* 支援將串流區段啟動至批次目的地。 批目標計畫根據批目標計畫導出配置檔案段成員資格。 這包括透過串流和批次方法所決定的區段成員資格。

啟動體驗事件

* 不支援啟動原始體驗事件。 若要針對體驗事件啟動，必須使用包含或排除體驗事件邏輯的必要規則來建立區段。 這會建立根據體驗事件定義的區段，而且區段成員資格可以啟動為原始體驗事件的代理。 另請考慮使用[!UICONTROL 啟動伺服器端]來啟動透過SDK收集的原始體驗事件。

## 相關文件

* [目標文件](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=zh-Hant)
* [雲端儲存空間目標概觀](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/cloud-storage/overview.html?lang=en#catalog)
* [HTTP目標](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/http-destination.html?lang=en#overview)
* [即時客戶資料平台產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/real-time-customer-data-platform.html)
* [描述檔與區段指南](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* [細分文件](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)

## 相關視訊與教學課程

* [即時客戶資料平台概覽](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=zh-Hant)
* [[!UICONTROL 即時客戶資料平台示範]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=zh-Hant)
* [建立區段](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=zh-Hant)
