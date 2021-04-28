---
title: 線上／離線Audience Activation藍圖
description: 線上 / 離線 Audience Activation。
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7086
exl-id: 011f4909-b208-46db-ac1c-55b3671ee48c
translation-type: tm+mt
source-git-commit: 24b6ffe3021389d33e84688a8f1a90711ca4b772
workflow-type: tm+mt
source-wordcount: '990'
ht-degree: 35%

---

# 線上／離線Audience Activation藍圖

使用離線屬性和事件，例如離線訂單、事務、CRM 或忠誠度資料，與線上行為一起進行線上目標定位和個人化。

啟用對象至基於已知個人資料的目標，例如電子郵件供應商、社交網路及廣告目標。

## 使用案例

* 對社交及廣告目標上已知對象的對象目標定位。
* 使用線上和離線屬性的線上個人化。
* 啟用對象至已知通道，例如電子郵件和簡訊。

## 應用程式

* Adobe Experience Platform
* [!UICONTROL 即時客戶資料平台]

## 架構

<img src="assets/onoff.svg" alt="線上／離線Audience Activation藍圖的參考架構" style="border:1px solid #4a4a4a" />

## 護欄

* [個人資料與細分準則](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hant)

### 區段評估與啟用的護欄

| 區段類型 | 頻率 | 吞吐量 | 延遲（區段評估） | 延遲（區段啟動） | 啟動裝載 |
|---|---|---|---|---|---|
| 邊緣分段 | 邊緣分割目前是測試版，可讓Experience Platform邊緣網路上評估有效的即時分割，以便透過Adobe Target和AdobeJourney Optimizer進行即時、相同的頁面決策。 |  | ~100 ms | 可立即在Adobe Target個人化、在Edge Profile中查閱個人檔案，以及透過Cookie型目的地啟動。 | Edge上提供的「對象會籍」，可用於描述檔查閱和Cookie型目的地。<br>Adobe Target和Journey Optimizer提供「對象會籍」和「個人檔案」屬性。 |
| 串流細分 | 每當新的串流事件或記錄被收錄到即時客戶個人檔案中，且區段定義是有效的串流區段。 <br>如需串流區 [段準](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=zh-Hant) 則的指引，請參閱區段檔案 | 每秒最多1500個事件。 | ~ p95 &lt;5分鐘 | 串流目標：串流觀眾會籍會在約10分鐘內啟動，或根據目的地的需求進行微批次啟動。<br>計畫目標：串流觀眾會籍會根據排程的目的地傳送時間，以批次方式啟動。 | 串流目標：對象會籍變更、身分值和描述檔屬性。<br>計畫目標：對象會籍變更、身分值和描述檔屬性。 |
| 增量分段 | 針對自上次增量或批次區段評估以來已納入即時客戶個人檔案的新資料，每小時一次。 |  |  | 串流目標：增量觀眾會籍會在約10分鐘內啟動，或根據目的地需求進行微批。<br>計畫目標：增量觀眾會籍會根據排程的目的地傳送時間，以批次方式啟用。 | 串流目標：受眾會籍僅會變更和識別值。<br>計畫目標：對象會籍變更、身分值和描述檔屬性。 |
| 批次分段 | 每天根據預定的系統集排程一次，或透過API手動啟動臨機。 |  | 每個作業大約1小時（最多10 TB配置檔案儲存大小），每個作業2小時（10 TB到100 TB配置檔案儲存大小）。 批次區段工作效能取決於設定檔數目、設定檔大小和評估的區段數目。 | 串流目標：根據目的地的需求，在區段評估或微批處理完成約10個內啟動批次觀眾會籍。<br>計畫目標：批次觀眾會籍會根據排程的目的地傳送時間來啟用。 | 串流目標：受眾會籍僅會變更和識別值。<br>計畫目標：對象會籍變更、身分值和描述檔屬性。 |

### 跨應用程式觀眾分享的護欄

| 受眾應用程式整合 | 頻率 | 吞吐量／卷 | 延遲（區段評估） | 延遲（區段啟動） |
|---|---|---|---|---|
| 即時客戶資料平台以Audience Manager | 依據分段類型——請參閱上述分段護欄表格。 | 依據分段類型——請參閱上述分段護欄表格。 | 依據分段類型——請參閱上述分段護欄表格。 | 分部評估完成後幾分鐘內完成。<br>即時客戶資料平台與Audience Manager之間的初始觀眾設定同步大約需要4小時。<br>在4小時期間實現的任何讀者會籍都會寫入後續批次分段工作的Audience Manager，成為「現有」讀者會籍。 |
| Adobe Analytics到Audience Manager |  | 依預設，每個Adobe Analytics報表套裝最多可共用75個觀眾。 如果使用Audience Manager授權，Adobe Analytics與Adobe Target或Adobe Audience Manager與Adobe Target之間可共用的觀眾數目沒有限制。 |  |  |
| Adobe Analytics客戶即時資料平台 | 目前不提供 | 目前不提供 | 目前不提供 | 目前不提供 |





## 實施步驟

1. 在 Experience Platform 中設定方案和資料集。
1. 在方案上設定正確的身份和身份命名空間，以確保擷取的資料可以嵌入統一的設定檔。
1. 為設定檔啟用方案和資料集。
1. 擷取資料至 Platform。
1. 為要與Audience Manager共用的Experience Platform中定義的受眾，在Audience Manager和Experience Platform之間設定即時客戶資料平台。
1. Experience Platform 中要在批次或串流中評估的作者區段。系統會自動確定區段是作為批次還是串流評估。
1. 將用於設定檔屬性和對象會籍分享的目標設定為所需的目標。

## 實施考量

* 分享設定檔資料到目標需要您在目標負載中包含目標使用的特定身份值。目標目標所需的任何身份都必須被收錄到平台中，並配置為[!UICONTROL 即時客戶概要檔案]的身份。

* 對於其中對象從 Experience Platform 分享至 Audience Manager 的啟用狀況，[!UICONTROL 即時客戶設定檔]中包含的所有身份將分享至 Audience Manager。當所需的目標身份包含在[!UICONTROL 即時客戶設定檔]中時，或者[!UICONTROL 即時客戶設定檔]中的身份可以關聯至 Audience Manager 中連結的所需目標身份時，Experience Platform 中的對象可透過 Audience Manager 目標分享。

## 相關文件

* [即時客戶資料平台產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/real-time-customer-data-platform.html)
* [描述檔與區段指南](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* [細分文件](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)
* [目標文件](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=zh-Hant)

## 相關視訊與教學課程

* [即時客戶資料平台概覽](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=zh-Hant)
* [[!UICONTROL 即時客戶資料平台示範]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=zh-Hant)
* [建立區段](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=zh-Hant)
