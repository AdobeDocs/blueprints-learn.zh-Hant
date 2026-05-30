---
title: 匿名訪客網頁Personalization
description: 瞭解如何根據工作階段中的行為訊號，將個人化網頁內容傳遞給無法識別的訪客。
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: e2446801-ffce-40e6-bfe9-abec623c9201
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1739'
ht-degree: 4%

---

# 匿名訪客網頁個人化

本指南說明匿名訪客Web個人化使用案例模式，此模式使用[!DNL Adobe Journey Optimizer] (AJO)、[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)和[!DNL Adobe Experience Platform] (AEP)根據工作階段中的行為訊號，將個人化網頁內容傳送給匿名（未識別）訪客。 它專為需要瞭解此模式的功能、其支援的業務目標、其啟用的戰術使用案例以及所涉及的Adobe應用程式的解決方案架構師、行銷技術人員和實作工程師所設計。

此模式適用於有限的資料 — 只有可以在目前工作階段中觀察到的內容，以及透過相同裝置或Cookie的先前造訪累積的任何匿名邊緣設定檔。 這使其適用於funnel頂端個人化，其中訪客沒有帳戶或尚未驗證。

## 使用案例模式

以下說明此使用案例的核心模式和執行計畫。

**匿名訪客網頁Personalization**

透過AJO Web Channel，根據工作階段中的行為訊號，為無法識別的訪客提供個人化內容。

**執行計畫：**&#x200B;網頁介面設定>行為規則評估>內容傳送>曝光追蹤>報告

## 使用案例概述

匿名訪客Web Personalization滿足企業需求，將相關的個人化內容傳送給尚未識別的網站訪客 — 他們尚未登入、沒有已知的身分，且無法解析為統一的客戶設定檔。 儘管有此限制，使用工作階段中的行為訊號仍可達成有意義的個人化：已檢視頁面、網站逗留時間、捲動深度、轉介來源、地理位置、裝置型別和UTM促銷活動引數。

此模式使用AJO的Web Channel介面和程式碼型體驗來即時修改頁面內容。 Edge細分是主要的評估方法，因為當訪客瀏覽網站時，必須在次秒延遲的情況下做出決定。 [!DNL Web SDK]會收集行為訊號並將其傳送至[!DNL AEP Edge Network]，以邊緣評估的對象規則來決定要傳送的內容變體。

不同於已知訪客的網頁/應用程式個人化（會利用完整的統一設定檔和區段成員資格），此模式受限於目前工作階段中可觀察到的資料，以及與訪客的ECID ([!DNL Experience Cloud ID])相關聯的任何匿名邊緣設定檔。 這項區別對實作規劃至關重要：可用於個人化的行為訊號僅限[!DNL Web SDK]所擷取的內容，以及透過Cookie式ECID跨工作階段保留在邊緣設定檔存放區中的內容。

## 主要業務目標

此使用案例模式支援下列業務目標。

**[增加網站參與度](../../business-objectives/acquisition-growth/increase-website-engagement.md)**

透過為匿名訪客訊號量身打造的相關體驗，改善網站逗留時間、每個工作階段頁面數以及與網路內容的互動關係。

| KPI |
| --- |
| Time On （網頁）頁面 |
| 參與度 |
| 轉換率 |

**[提供個人化的客戶體驗](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**

根據個別偏好、行為和生命週期階段量身打造內容、選件和訊息，即使訪客尚未自我識別。

| KPI |
| --- |
| 參與度 |
| 轉換率 |
| 客戶滿意度(CSAT) |

**[提高轉換率](../../business-objectives/revenue-monetization/increase-conversion-rates.md)**

根據行為情境提供最相關的內容，藉此提高完成所需動作（例如購買、註冊或表單提交）的訪客和潛在客戶百分比。

| KPI |
| --- |
| 轉換率 |
| 潛在客戶轉換 |
| 每個潛在客戶的成本 |

## 戰術使用案例範例

下列範例說明可套用此模式的特定案例。

- **根據反向連結來源進行的登陸頁面標題A/B測試** — 針對來自Google、社群媒體或直接流量的訪客測試不同的標題，以透過贏取管道最佳化參與
- **以瀏覽行為為基礎的類別相關性建議** — 根據目前工作階段中檢視的頁面顯示產品或內容建議，以提高探索和轉換
- **即將離開的訪客退出意向優惠** — 當行為訊號指出訪客即將放棄網站時，提供促銷優惠或銷售機會擷取表單
- **地理目標促銷橫幅** — 根據訪客的地理位置，顯示特定位置的促銷活動、商店定位器內容或區域優惠方案
- **裝置特定內容版面最佳化** — 根據訪客使用桌上型電腦、平板電腦或行動裝置，調整內容版面、影像大小和CTA版面
- **新訪客與回訪訪客的歡迎訊息** — 區分首次訪客與使用ECID跨工作階段持續性的回訪匿名訪客體驗
- **根據目前工作階段中已檢視頁面內容推薦** — 根據訪客已檢視的頁面動態顯示相關文章、產品或資源
- **以UTM行銷活動引數為基礎的動態主圖橫幅** — 個人化主圖橫幅，以符合引用行銷活動的訊息或創意

## 關鍵績效指標

使用下列KPI來評估此使用案例模式的成效。

| KPI | 說明 | 測量方法 |
| --- | --- | --- |
| Personalization曝光率 | 合格頁面檢視中已傳遞個人化內容的百分比 | AJO行銷活動報告：曝光數/頁面檢視總數 |
| 點進率(CTR) | 導致點按的個人化內容曝光百分比 | AJO促銷活動報告：點按數/曝光數 |
| 參與提升度 | 增加個人化與預設內容的頁面時間、每個工作階段頁面或捲動深度 | CJA工作區比較：個人化同類群組與控制 |
| 轉換率 | 接觸到個人化內容並完成所需動作的訪客百分比 | CJA funnel analysis：曝光數>互動>轉換 |
| 跳出率降低 | 接收個人化內容之訪客的單頁工作階段減少 | CJA工作階段分析：個人化與預設的跳出率差異 |
| 實驗成功率 | 產生統計上顯著獲勝者的A/B測試百分比 | AJO實驗報告：實驗達到信賴臨界值 |

## 應用程式

在此使用案例模式中使用以下應用程式。

- **[!DNL Adobe Journey Optimizer] (AJO)** — Web頻道介面設定、內容製作（網頁和程式碼型體驗）、行銷活動執行、內容實驗（A/B測試）、決策（動態內容選擇）和報告
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** — 根據工作階段中行為訊號進行即時對象評估的Edge細分；匿名邊緣設定檔管理
- **[!DNL Adobe Experience Platform] (AEP)** — [!DNL Web SDK]用於行為訊號收集，[!DNL Edge Network]用於即時資料路由和個人化傳遞，資料流設定

## 架構

下列參考架構說明如何在邊緣收集匿名訪客訊號、根據對象規則進行評估，並用來提供個人化內容。

![匿名對象啟用和個人化的參考架構](/help/blueprints/audience-activation/assets/anonymous_activation.png)

## 相關文件

以下Experience League資源提供此使用案例模式中所使用功能的其他詳細資料。

**網路通道和程式碼型體驗**

- [開始使用網路頻道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [建立網站體驗](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [程式碼型體驗管道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/get-started-code-based)
- [程式碼型體驗設定](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/code-based-configuration)

**對象和細分**

- [Segmentation Service概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [區段產生器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [邊緣分段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [串流區段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Profile Query Language參考](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

**Personalization與內容**

- [新增個人化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization語法](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [動態內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [使用內容範本](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [使用內容片段](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)

**內容實驗**

- [開始使用內容實驗](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [建立內容實驗](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [內容實驗報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [統計計算](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-calculations)

**決定管理**

- [決策管理概觀](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [建立產品建議放置環境](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [建立決定規則](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [建立個人化優惠方案](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [建立後備產品建議](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [建立集合](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [建立決定](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [排名策略](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)
- [在訊息中傳遞優惠方案](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

**行銷活動**

- [開始使用行銷活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [建立行銷活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)

**[!DNL Web SDK]和資料彙集**

- [網頁SDK概觀](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [安裝Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/install/overview)
- [設定資料串流](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [標籤總覽](https://experienceleague.adobe.com/en/docs/experience-platform/tags/home)

**身分和設定檔**

- [Identity Service總覽](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [身分名稱空間概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/identity/features/namespaces)
- [合併原則概觀](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [即時客戶個人檔案總覽](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)

**資料模式**

- [XDM系統概覽](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [結構描述組合基本面](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)

**報告和分析**

- [行銷活動即時報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [行銷活動全域報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [使用Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Analysis Workspace概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [CJA概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)

**資料控管和隱私權**

- [資料控管概覽](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [進階資料生命週期管理概觀](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)
- [同意和偏好設定欄位群組](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)

**護欄**

- [Journey Optimizer護欄](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [即時客戶個人檔案護欄](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Identity Service護欄](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)
