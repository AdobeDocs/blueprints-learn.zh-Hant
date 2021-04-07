---
title: 線上／離線Audience Activation藍圖
description: 線上／離線Audience Activation。
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7086
exl-id: 011f4909-b208-46db-ac1c-55b3671ee48c
translation-type: tm+mt
source-git-commit: 844fff1cefe367575beb5c03aa0f0d026eb9f39b
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 0%

---

# 線上／離線Audience Activation藍圖

使用離線屬性和事件，例如離線訂單、交易、CRM或忠誠度資料，以及線上行為，以進行線上鎖定和個人化。

將受眾激活至已知的個人檔案型目標，例如電子郵件提供者、社交網路和廣告目標。

## 使用案例

* 針對社交和廣告目的地的已知受眾鎖定受眾。
* 具有線上和離線屬性的線上個人化。
* 將受眾吸引到已知通道，例如電子郵件和簡訊。

## 應用程式

* Adobe Experience Platform
* 即時客戶資料平台

## 建築

<img src="assets/onoff.svg" alt="線上／離線Audience Activation情境的參考架構" style="border:1px solid #4a4a4a" />

## 瓜德賴爾

* [描述檔與區段指南](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* 根據預先決定的排程，每日執行一次批次區段工作。 然後，區段匯出工作會在排程的目的地傳送之前執行。 請注意，批次區段作業和目標傳送作業會分開執行。 批處理段作業和導出作業效能取決於配置檔案數、配置檔案大小和要評估的段數。
* 在串流資料到達描述檔並立即將區段成員資格寫入描述檔並傳送事件供應用程式訂閱時，會在幾分鐘內評估串流區段工作。
* 串流區段會籍會立即用於串流目的地，並以單一區段會籍事件或根據目的地的擷取模式而微批次的多個描述檔事件傳送。 對於透過排程批次區段傳送的串流評估的任何區段，排程目的地會在傳送前，從描述檔啟動區段匯出工作。
* 若要將RTCDP區段會籍共用給Audience Manager，流式區段會在幾分鐘內發生，批次區段的批次區段評估完成幾分鐘內發生。
* 從Experience Platform到Audience Manager共用的區段在區段實現後幾分鐘內即可共用——不論是透過串流或批次評估方法。 在AEP之間有初始區段設定同步AAM，一旦初次建立區段後，約4小時後，AEP區段成員資格便可開始在設定檔中AAM實現。 在設定Experience Platform和Audience Manager對象共用或將觀眾中繼資料從Experience Platform同步至Audience Manager之前，在共用「現有」區段會籍的下列區段工作之前，不會在Audience Manager中實現觀眾會籍。
* 來自批次區段工作的批次或串流目標工作可共用描述檔屬性更新以及區段成員資格。
* 串流區段工作至串流目的地僅會共用區段會籍更新。

## 實施步驟

1. 在Experience Platform中配置方案和資料集。
1. 在架構上設定正確的身分和身分名稱空間，以確保所擷取的資料可接合到統一的描述檔中。
1. 為配置檔案啟用模式和資料集。
1. 將資料內嵌至平台。
1. 布建即時客戶資料平台區段，以在Experience Platform和Audience Manager之間共用，讓Experience Platform中定義的對象共用給Audience Manager。
1. Experience Platform中的作者區段，以批次或串流方式評估。 系統會自動判斷區段是評估為批次還是串流。
1. 設定目標，以便將描述檔屬性和觀眾成員資格共用至所需目標。

## 實作考量

* 要將描述檔資料共用至目標，您必須在目標裝載中包含目標使用的特定識別值。 目標目標所需的任何身份都必須被收錄到平台中，並配置為即時客戶配置檔案的身份。

* 對於將觀眾從Experience Platform共用至Audience Manager的啟動案例，[!UICONTROL 即時客戶設定檔]中包含的所有身分都會共用至Audience Manager。 當所需目標身份被包括在[!UICONTROL 即時客戶配置檔案]中時，可以通過Audience Manager目標來共用來自Audience Manager的觀眾，或者其中，[!UICONTROL 即時客戶配置檔案]中的身份可以與在Experience Platform中連結的所需目標身份相關。

## 相關檔案

* [即時客戶資料平台產品說明](https://helpx.adobe.com/legal/product-descriptions/real-time-customer-data-platform.html)
* [描述檔與區段指南](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* [區段檔案](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)
* [目標檔案](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html)

## 相關影片與Tutorials

* [即時客戶資料平台概觀](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html)
* [即時客戶資料平台示範](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html)
* [建立區段](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html)
