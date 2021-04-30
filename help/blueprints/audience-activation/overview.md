---
title: 受眾與個人檔案啟動
description: 透過即時客戶資料平台，提供受眾已啟用和以個人資料為中心的客戶體驗。
solution: Experience Platform, Real-time Customer Data Platform
kt: null
thumbnail: null
exl-id: eeeb4325-d0e8-4fd8-86ab-0b8afdd0b69f
translation-type: tm+mt
source-git-commit: 9e0954334e8b8a8c5bf52651611e7afa165f6d21
workflow-type: tm+mt
source-wordcount: '1249'
ht-degree: 15%

---


# 受眾與個人檔案啟動

在資料導向式行銷世界中，受眾和個人檔案啟動是成功的關鍵。 但許多品牌仍將精力集中於以通道優先的啟用，這通常會導致不一致的觸及和個人化。

採用以通道為優先的方法時，每個通道皆是孤島，個人化工作僅強調在該通道上與品牌互動的客戶。此方法無法反映客戶透過很多不同的接觸點與品牌互動的現實情況。受眾和個人檔案啟動可讓品牌跨多個通道連接客戶互動，以便提供集中的個人檔案和受眾，並可以啟動至所有通道。

| Blueprint | 說明 | Experience Cloud 應用程式 |
|---|---|---|
| **[匿名 Audience Activation](anonymous.md)** | <ul><li>為匿名和行為客戶資料定位網路及廣告通道上的對象。</li><li>整合協力廠商對象資料以增強個人化。</li></ul> | <ul><li>Adobe Audience Manager</li></ul> |
| **[線上/離線 Audience Activation](online-offline.md)** | <ul><li>啟動至已知的基於個人檔案的目的地，例如電子郵件提供者、社交網路和廣告目的地。 </li><li>使用離線屬性和事件，例如離線訂單、交易、CRM或忠誠度資料，以及線上行為，以進行線上鎖定和個人化。</li></ul> | <ul><li>Adobe Experience Platform</li><li> [!UICONTROL 即時客戶資料平台]</li><li>Adobe Audience Manager (可選)</li></ul> |
| **[受眾和個人檔案啟動至企業目標](enterprise-destinations.md)** | <ul><li>複製和更新企業資料儲存區的個人檔案和讀者變更，以利啟動和報告使用案例。 </li></ul><ul><li>通過從[!UICONTROL 即時客戶資料平台]到企業系統和應用程式的客戶操作通知，向客戶發起銷售或支援操作。</li></ul> | <ul><li>Adobe Experience Platform</li><li>[!UICONTROL 即時客戶資料平台]</li><li>Experience Platform啟動</li><li>Adobe Audience Manager (可選)</li></ul> |
| **[客戶活動中樞](customer-activity.md)** | <ul><li>為代理支援的互動提供更深入的消費者背景，例如支援和銷售經驗。使用Experience Platform的描述檔查閱，工程師可以接收更多有關消費者的內容，例如最近購買、促銷活動互動、傾向、受眾會籍，以及儲存在即時客戶描述檔中的其他屬性和見解。</li></ul> | <ul><li>Adobe Experience Platform</li></ul> |

## 受眾和個人檔案啟動藍圖的保障

* [個人資料與細分準則](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hant)

### 區段評估與啟用的護欄

|分段類型 |頻率 |吞吐量 |延遲（區段評估） |延遲（區段啟動） |啟動裝載 |
|-|-|-|-|-|-|
|邊緣區隔 | Edge分段目前為測試版，可讓Experience Platform邊緣網路上評估有效的即時分段，以便透過Adobe Target和AdobeJourney Optimizer進行即時、相同的頁面決策。 |  |約100毫秒 |可立即在Adobe Target個人化、在Edge Profile中查閱個人檔案，以及透過Cookie型目的地啟動。 | Edge提供的觀眾會籍，適用於個人檔案查閱和Cookie型目的地。<br>Adobe Target和Journey Optimizer提供「對象會籍」和「個人檔案」屬性。|
|串流區段 |每次新的串流事件或記錄被收錄到即時客戶個人檔案中，且區段定義是有效的串流區段。 <br>如需串流區 [段準](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=zh-Hant) 則的指引，請參閱區段檔案 |每秒最多1500個事件。| ~ p95 &lt; 5分鐘 |串流目標：串流觀眾會籍會在約10分鐘內啟動，或根據目的地的需求進行微批次啟動。<br>計畫目標：串流觀眾會籍會根據排程的目的地傳送時間，以批次方式啟動。|串流目標：對象會籍變更、身分值和描述檔屬性。<br>計畫目標：對象會籍變更、身分值和描述檔屬性。|
|增量分段 |自上次增量或批次區段評估後，每小時一次新資料已納入即時客戶個人檔案。 |  |  |串流目標：增量觀眾會籍會在約10分鐘內啟動，或根據目的地需求進行微批。<br>計畫目標：增量觀眾會籍會根據排程的目的地傳送時間，以批次方式啟動。|串流目標：受眾會籍僅會變更和識別值。<br>計畫目標：對象會籍變更、身分值和描述檔屬性。|
|批次劃分 |根據預定的系統集排程，或透過API手動啟動臨機，每天一次。 |  |每份工作大約1小時，最多10 TB的配置式儲存大小，每份工作2小時，10 TB到100 TB的配置式儲存大小。 批次區段工作效能取決於設定檔數目、設定檔大小和評估的區段數目。 |串流目標：根據目的地的需求，在區段評估或微批處理完成約10個內啟動批次觀眾會籍。<br>計畫目標：批次觀眾會籍會根據排程的目的地傳送時間來啟用。|串流目標：受眾會籍僅會變更和識別值。<br>計畫目標：對象會籍變更、身分值和描述檔屬性。 |

### 跨應用程式觀眾分享的護欄

|觀眾應用程式整合 |頻率 |吞吐量／卷 |延遲（區段評估） |延遲（區段啟動） |
|-|-|-|-|-|
|即時客戶資料平台以進行Audience Manager |視區段類型而定——請參閱上述區段護欄表格。 |視區段類型而定——請參閱上述區段護欄表格。 |視區段類型而定——請參閱上述區段護欄表格。 |完成區段評估後幾分鐘內完成。<br>即時客戶資料平台與Audience Manager之間的初始觀眾設定同步大約需要4小時。<br>在4小時期間實現的任何讀者會籍都會寫入後續批次分段工作的Audience Manager，成為「現有」讀者會籍。|
|即時客戶資料平台到Ad Cloud |請注意，從即時客戶資料平台分享受眾至Adobe Advertising Cloud需要Audience Manager。 適用於Audience Manger即時客戶資料平台分享的保證，將適用於整合即時客戶資料平台受眾至Advertising Cloud。 | - |-  | - |
|Adobe Analytics到即時客戶資料平台 |目前不提供 |目前不提供 |目前不提供 |目前不提供 |
|Adobe Analytics到Audience Manager |-  |依預設，每個Adobe Analytics報表套裝最多可共用75個觀眾。 如果使用Audience Manager授權，Adobe Analytics與Adobe Target或Adobe Audience Manager與Adobe Target之間可共用的觀眾數目沒有限制。 | - |-  |


### 用於激活屬性和標識的護欄

* [!UICONTROL 即時客戶資料平台可啟] 用觀眾會籍，以及針對選取要啟動之區段成員的個人檔案所發生的屬性和身分變更。如果您的目標是啟用屬性或身分識別，您必須定義全域區段，其中包含所有要傳送屬性和身分更新的描述檔。 此時，您可以選取要在目標設定中啟動的區段和所需屬性。
* 請注意，批次目標不支援啟動僅限屬性的變更事件。 完整或增加的觀眾會籍可隨選取的屬性一起傳送，以進行啟動，但您無法透過批次目的地啟用僅限屬性的變更事件。

將批次區段啟用至串流目的地

* 支援「串流目的地的批次區段啟動」。 當區段工作完成以進行串流啟動時，批次區段工作會將訊息置於管道上

啟動串流區段至批次目的地

* 支援將串流區段啟動至批次目的地。 批目標計畫根據批目標計畫導出配置檔案段成員資格。 這包括透過串流和批次方法所決定的區段成員資格。

啟動體驗事件

* 不支援啟動原始體驗事件。 若要針對體驗事件啟動，必須使用包含或排除體驗事件邏輯的必要規則來建立區段。 這會建立根據體驗事件定義的區段，而且區段成員資格可以啟動為原始體驗事件的代理。 另請考慮使用[!UICONTROL 啟動伺服器端]來啟動透過SDK收集的原始體驗事件。


## 相關部落格貼文

* [[!DNL Blueprints for Audience Activation in Adobe Experience Platform]](https://medium.com/adobetech/a-blueprint-for-audience-activation-in-adobe-experience-platform-b2b30fae90fd)
* [[!DNL How Adobe Experience Platform Predictive Audiences improves Personalized Experiences]](https://medium.com/adobetech/how-adobe-experience-platform-predictive-audiences-improves-personalized-experiences-1f75a60cb7a3)
* [[!DNL Adobe Experience Platform Web SDK for Audience Management]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
