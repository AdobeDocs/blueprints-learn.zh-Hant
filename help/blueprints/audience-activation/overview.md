---
title: 受眾與個人檔案啟動
description: 透過即時客戶資料平台，提供受眾已啟用和以個人資料為中心的客戶體驗。
solution: Experience Platform, Real-time Customer Data Platform
kt: null
thumbnail: null
exl-id: eeeb4325-d0e8-4fd8-86ab-0b8afdd0b69f
translation-type: tm+mt
source-git-commit: 5471d9c0f6fdef6fbac72d5d35f32353ea5a5ee8
workflow-type: tm+mt
source-wordcount: '678'
ht-degree: 28%

---


# 受眾與個人檔案啟動

在資料導向式行銷世界中，受眾和個人檔案啟動是成功的關鍵。 但許多品牌仍將精力集中於以通道優先的啟用，這通常會導致不一致的觸及和個人化。

採用以通道為優先的方法時，每個通道皆是孤島，個人化工作僅強調在該通道上與品牌互動的客戶。此方法無法反映客戶透過很多不同的接觸點與品牌互動的現實情況。受眾和個人檔案啟動可讓品牌跨多個通道連接客戶互動，以便提供集中的個人檔案和受眾，並可以啟動至所有通道。

| Blueprint | 說明 | Experience Cloud 應用程式 |
|---|---|---|
| **[匿名 Audience Activation](anonymous.md)** | <ul><li>為匿名和行為客戶資料定位網路及廣告通道上的對象。</li><li>整合協力廠商對象資料以增強個人化。</li></ul> | <ul><li>Adobe Audience Manager</li></ul> |
| **[線上/離線 Audience Activation](online-offline.md)** | <ul><li>啟動至已知的基於個人檔案的目的地，例如電子郵件提供者、社交網路和廣告目的地。 </li><li>使用離線屬性和事件，例如離線訂單、交易、CRM或忠誠度資料，以及線上行為，以進行線上鎖定和個人化。</li></ul> | <ul><li>Adobe Experience Platform</li><li> [!UICONTROL 即時客戶資料平台]</li><li>Adobe Audience Manager (可選)</li></ul> |
| **[受眾和個人檔案啟動至企業目標](enterprise-destinations.md)** | <ul><li>複製和更新企業資料儲存區的個人檔案和讀者變更，以利啟動和報告使用案例。 </li></ul><ul><li>通過從[!UICONTROL 即時客戶資料平台]到企業系統和應用程式的客戶操作通知，向客戶發起銷售或支援操作。</li></ul> | <ul><li>Adobe Experience Platform</li><li>[!UICONTROL 即時客戶資料平台]</li><li>Experience Platform啟動</li><li>Adobe Audience Manager (可選)</li></ul> |
| **[使用Experience Cloud應用程式啟動受眾和個人檔案](platform-and-applications.md)** | </ul><li>在Experience Platform中管理個人檔案和受眾，並與Experience Cloud應用程式共用</li><li>建立並分享豐富的Experience Platform客戶細分和見解，並與Experience Cloud應用程式分享</li></ul> | <ul><li>Adobe Experience Platform</li><li>[!UICONTROL 即時客戶資料平台]</li><li>Experience Platform啟動</li><li>Experience Cloud 應用程式</li></ul> |
| **[客戶活動中樞](customer-activity.md)** | <ul><li>為代理支援的互動提供更深入的消費者背景，例如支援和銷售經驗。使用Experience Platform的描述檔查閱，工程師可以接收更多有關消費者的內容，例如最近購買、促銷活動互動、傾向、受眾會籍，以及儲存在即時客戶描述檔中的其他屬性和見解。</li></ul> | <ul><li>Adobe Experience Platform</li></ul> |



## 受眾和個人檔案啟動藍圖的保障

* [個人資料與細分準則](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hant)


### 啟用屬性和身分

* [!UICONTROL 即時客戶資料平台可啟] 用觀眾會籍，以及針對選取要啟動之區段成員的個人檔案所發生的屬性和身分變更。如果您的目標是啟用屬性或身分識別，您必須定義全域區段，其中包含所有要傳送屬性和身分更新的描述檔。 此時，您可以選取要在目標設定中啟動的區段和所需屬性。
* 請注意，批次目標不支援啟動僅限屬性的變更事件。 完整或增加的觀眾會籍可隨選取的屬性一起傳送，以進行啟動，但您無法透過批次目的地啟用僅限屬性的變更事件。

### 將批次區段啟用至串流目的地

* 支援「串流目的地的批次區段啟動」。 當區段工作完成以進行串流啟動時，批次區段工作會將訊息置於管道上

### 啟動串流區段至批次目的地

* 支援將串流區段啟動至批次目的地。 批目標計畫根據批目標計畫導出配置檔案段成員資格。 這包括透過串流和批次方法所決定的區段成員資格。

### 啟動體驗事件

* 不支援啟動原始體驗事件。 若要針對體驗事件啟動，必須使用包含或排除體驗事件邏輯的必要規則來建立區段。 這會建立根據體驗事件定義的區段，而且區段成員資格可以啟動為原始體驗事件的代理。 另請考慮使用[!UICONTROL 啟動伺服器端]來啟動透過SDK收集的原始體驗事件。


## 相關部落格貼文

* [[!DNL Blueprints for Audience Activation in Adobe Experience Platform]](https://medium.com/adobetech/a-blueprint-for-audience-activation-in-adobe-experience-platform-b2b30fae90fd)
* [[!DNL How Adobe Experience Platform Predictive Audiences improves Personalized Experiences]](https://medium.com/adobetech/how-adobe-experience-platform-predictive-audiences-improves-personalized-experiences-1f75a60cb7a3)
* [[!DNL Adobe Experience Platform Web SDK for Audience Management]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
