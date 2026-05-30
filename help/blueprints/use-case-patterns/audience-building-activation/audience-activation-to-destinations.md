---
title: 目的地的Audience啟用
description: 瞭解如何使用Adobe Real-Time CDP評估對象區段並將其發佈到外部目的地以進行定位或抑制。
solution: Real-Time Customer Data Platform, Experience Platform
exl-id: b0b9d937-45d2-48f9-ac4c-3611c6e35f58
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1365'
ht-degree: 4%

---

# 目的地的Audience啟用

本指南說明目的地使用案例模式的對象啟用，該模式會評估Adobe [!DNL Real-Time Customer Data Platform] (RT-CDP)中的對象區段，並將其發佈至廣告平台、雲端儲存空間、CRM系統或資料合作夥伴，以進行目標定位、隱藏、相似對象建模或分析擴充。 它專為需要瞭解此模式的功能、其支援的業務目標、其啟用的戰術使用案例以及所涉及的Adobe應用程式的解決方案架構師、行銷技術人員和實作工程師所設計。

此模式涵蓋對象啟動的整個生命週期，從定義及評估對象區段（透過設定目的地連線和發佈對象），到監控啟動健康狀況和強制實行控管合規性。

## 使用案例模式

**Audience Activation至目的地** — 評估對象區段並發佈至外部目的地，以進行目標定位或隱藏。

**執行計畫：**&#x200B;對象評估>目的地設定> Audience Activation >監視

## 使用案例概述

組織需要將受眾資料傳送至外部系統，以支援付費媒體行銷活動、豐富CRM記錄、與合作夥伴共用資料，或提供下游分析。 Audience Activation to Destinations是RT-CDP中的基本啟用模式：它會評估哪些設定檔符合目標對象的資格、連線到一個或多個外部目的地、將設定檔屬性對應到目的地特定欄位，以及發佈對象以供下游使用。

每當目標是在適當的時間以適當的格式將對象資料取得至外部系統時，此模式即適用。 它不涉及訊息傳送、網站上的個人化或分析。 這是RT-CDP實作最常見的起點，並作為其他模式在上方所構成的建置區塊。

典型的利害關係人包括管理付費媒體的數位行銷團隊、豐富倉儲的資料團隊、為行銷活動準備聯絡名單的CRM團隊，以及確保傳出資料流程符合治理規範的隱私權團隊。

>[!NOTE]
>如果您的組織使用[!DNL Real-Time CDP] B2B edition並啟用至以帳戶為基礎的目的地，請參閱[B2B對象啟用](../b2b/account-audience-activation.md)。 該模式共用相同的啟動機制，但使用B2B帳戶和人員資料模型，並需要B2B edition授權。

## 主要業務目標

此使用案例模式支援下列業務目標。

### 贏取新客戶

透過鎖定目標的贏取促銷活動、相似對象和付費媒體最佳化，來擴大客戶基礎。

**KPI：**&#x200B;新客戶、客戶贏取成本、潛在客戶/潛在客戶轉換

[進一步瞭解如何取得新客戶](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

### 降低客戶贏取成本

提升目標定位效率、從贏取促銷活動中抑制現有客戶，並最佳化媒體支出。

**KPI：**&#x200B;客戶贏取成本、每個潛在客戶的成本、效率

[深入瞭解如何降低客戶贏取成本](/help/blueprints/business-objectives/cost-efficiency/reduce-customer-acquisition-cost.md)

### 最佳化行銷支出和ROI

透過更好的目標定位、歸因、對象抑制和預算分配，改善行銷投資報酬。

**KPI：**&#x200B;成本節省、客戶贏取成本、遞增收入

[進一步瞭解最佳化行銷支出和ROI](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md)

## 戰術使用案例範例

- **廣告平台對象目標定位** — 將合格的區段推送至付費媒體平台，以利行銷活動目標定位
- **現有客戶的付費媒體隱藏** — 將已知客戶排除在廣告平台的贏取行銷活動中，以避免浪費支出
- **相似種子對象** — 將高價值客戶區段推送至Facebook、Google Ads或交易台，作為相似對象擴展的種子對象
- **銷售啟用的CRM同步** — 啟用高意圖或高價值對象，讓銷售團隊可以優先處理外展工作
- **資料合作夥伴對象共用** — 與資料合作夥伴共用合格的對象區段，以進行Co-op目標定位或測量
- **匯出雲端儲存空間以擴充資料倉儲** — 將對象成員資格和設定檔屬性匯出至Amazon S3、Azure Blob、Google雲端儲存空間或SFTP，以供下游分析使用
- **重新目標定位對象啟用** — 啟用未轉換為重新目標定位平台的網站訪客
- **連絡人清單同步處理至電子郵件服務提供者** — 將對象會籍推送至協力廠商電子郵件平台，以協調外展工作

## 關鍵績效指標

| KPI | 說明 | 測量方法 |
| --- | --- | --- |
| 客戶贏取成本(CAC) | 透過已啟用的受眾取得新客戶的成本 | 歸因於已啟用的受眾的媒體總支出/新客戶 |
| 對象符合率 | 已在目的地成功比對的已啟動設定檔百分比 | 符合目的地/從RT-CDP匯出的設定檔的設定檔 |
| 隱藏省錢 | 抑制贏取促銷活動的現有客戶，以節省媒體支出 | 預估的CPM x受眾人數 |
| 啟用傳送率 | 成功傳送到目的地的設定檔百分比 | 來源對象中已傳送的設定檔/設定檔 |
| 啟動時間 | 從對象定義到目的地第一次傳遞的經過時間 | 從區段建立到首次確認資料流執行的測量 |
| 對象母體準確度 | 目標處的預期和實際受眾規模的對齊方式 | 目的地受眾規模/RT-CDP受眾規模 |

## 應用程式

- **Adobe [!DNL Real-Time Customer Data Platform] (RT-CDP)** — 對象評估、目的地管理、對象啟用、同意和治理執行
- **Adobe [!DNL Experience Platform] (AEP)** — 設定檔存放區、身分服務、細分引擎、資料控管

## 架構

下列參考架構說明對象和設定檔資料如何從Real-Time CDP流向企業目的地，包括雲端儲存空間、串流端點和SaaS應用程式。

![企業目的地的對象和設定檔啟用的參考架構](/help/blueprints/audience-activation/assets/known_activation.png)

## 相關文件

**目的地**

- [目標概覽](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [目的地目錄](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)
- [啟用串流目的地的對象](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [啟用對象以批次設定檔匯出目的地](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [對批次目的地啟用隨選對象](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/api/ad-hoc-activation-api)
- [目的地護欄](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)
- [Destination SDK概觀](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/destination-sdk/overview)

**對象和細分**

- [Segmentation Service概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [區段產生器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Profile Query Language參考](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)
- [串流區段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [邊緣分段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [對象構成概觀](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [分段護欄](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)

**身分和設定檔**

- [Identity Service總覽](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [身分名稱空間概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/identity/features/namespaces)
- [身分識別圖連結規則](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/identity-linking-logic)
- [設定檔概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [合併原則概觀](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

**資料模型與結構描述**

- [XDM系統概覽](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [結構描述組合基本面](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)

**資料控管**

- [資料控管概覽](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [資料使用標籤概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/labels/overview)
- [資料治理原則](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/policies/overview)
- [原則執行](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/enforcement/overview)
- [同意與偏好設定](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)

**監視和可觀察性**

- [監視目的地的資料流](https://experienceleague.adobe.com/en/docs/experience-platform/dataflows/ui/monitor-destinations)
- [警報概觀](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [可觀察性深入分析概觀](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)
- [授權使用量儀表板](https://experienceleague.adobe.com/en/docs/experience-platform/landing/license-usage-and-guardrails/license-usage-dashboard)

**計算屬性**

- [計算屬性概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [計算屬性UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/ui)

**資料收集和來源**

- [來源概觀](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)
- [網頁SDK概觀](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [設定資料串流](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)

**管理**

- [沙箱概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sandbox/home)
- [存取控制總覽](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home)
- [以屬性為基礎的存取控制](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/abac/overview)

**護欄**

- [即時客戶個人檔案護欄](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Identity Service護欄](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)
- [啟動護欄](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)
- [擷取護欄](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)
