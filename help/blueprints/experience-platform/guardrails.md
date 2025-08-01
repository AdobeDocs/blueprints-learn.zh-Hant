---
title: Experience Platform 和應用程式護欄
description: 護欄定義了對 Adobe Experience Platform 和應用程式中的元件和服務的效能期望和影響
solution: Experience Platform
thumbnail: null
exl-id: b64cf3e4-cc5d-4984-8a0f-4736d432b8e1
source-git-commit: 75a0f2a77f39a4320dc4c4b0db918879be099dd3
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 11%

---


# 護欄

護欄可反映系統限制、預期延遲和效能期望，以最佳化客戶架構和使用案例效能，並有助於確保穩定性、避免錯誤或意外結果。

## 護欄型別

| 護欄型別 | 說明 |
|---|---|
| 效能護欄（軟性限制） | 效能護欄是與使用案例範圍相關的使用限制，並概述正常條件下的預期效能。 超過上限時，您可能會遇到效能降低和延遲的狀況。 效能護欄記錄在Experience League檔案中，每個解決方案的護欄區段下，如下所述。 |
| 靜態限制（硬限制） | 這些是系統強制的限制，不能超過。 靜態限制通常以合約方式繫結，並在客戶合約和[產品說明](https://helpx.adobe.com/legal/product-descriptions.html)中概述。 |

>[!NOTE]
>
> 護欄並非服務等級協定，而是最佳設定與預期系統行為的指引。 任何屬於系統或合約限制或服務等級合約的護欄，都會在客戶合約及產品說明中詳細記錄。 如果您有興趣瞭解自訂限制，請聯絡客戶服務代表。

>[!NOTE]
>
> 若使用案例具有嚴格的延遲或效能需求，Adobe建議您與您的Adobe客戶團隊和實作合作夥伴討論詳細資訊。 每個客戶設定可能會因資料擷取模式、設定檔計數和豐富度、區段規則和啟用管道而異。 因此，架構及測試您的使用案例以最佳化其效能並完全瞭解預期的效能特性非常重要。

## Adobe Experience Platform和應用程式的護欄參考檔案

下列頁面提供Adobe Experience Platform功能、服務和應用程式護欄的相關資訊：

**Experience Platform應用程式**

* [Real-Time CDP護欄總覽](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/guardrails/overview.html)
* [Customer Journey Analytics對象共用護欄](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html#latency)
* [Customer Journey Analytics資料擷取護欄](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html#what-is-the-expected-latency-for-analytics-data-on-platform%3F)
* [Journey Optimizer護欄](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/guardrails.html)

**Experience Platform服務**

* [資料擷取護欄](https://experienceleague.adobe.com/docs/experience-platform/ingestion/guardrails.html)
* [[!DNL Edge Network] API護欄](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/guardrails.html)
* [即時客戶設定檔和細分護欄](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hant)
* [身分護欄](https://experienceleague.adobe.com/docs/experience-platform/identity/guardrails.html?lang=zh-Hant)
* [Query Service 護欄](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html?lang=zh-Hant)
* [目標啟用護欄](https://experienceleague.adobe.com/docs/experience-platform/destinations/guardrails.html?lang=zh-Hant)

## 端到端延遲圖表 {#end-to-end-latency}

### Experience Platform Edge Network與中心主要觀察延遲 {#edge-hub-latencies}

下圖說明在Experience Platform和應用程式上建構使用案例時應注意的主要邊緣和中樞觀察延遲。

![Experience Platform [!DNL Edge Network]和中心主要觀察延遲。](/help/blueprints/experience-platform/assets/aep_edge_hub_latency_v1.svg "Experience Platform Edge Network與中心主要觀察延遲"){width="1000" zoomable="yes"}