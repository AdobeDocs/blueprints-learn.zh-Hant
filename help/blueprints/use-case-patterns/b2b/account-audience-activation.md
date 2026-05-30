---
title: B2B Audience Activation
description: 瞭解如何跨網路、電子郵件和廣告頻道啟用以帳戶為基礎的B2B受眾。
solution: Real-Time Customer Data Platform
exl-id: 2b979159-37aa-41d4-a6b4-1105538f6546
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1540'
ht-degree: 2%

---

# B2B對象啟用

本指南說明B2B對象啟用使用案例模式，此模式使用[!DNL Adobe Real-Time Customer Data Platform] ([!DNL RT-CDP]) B2B edition來建置、評估及啟用跨網路、電子郵件、廣告及CRM管道的帳戶層級對象。 它專為需要瞭解此模式的功能、其支援的業務目標、其啟用的戰術使用案例以及所涉及的Adobe應用程式的解決方案架構師、行銷技術人員和實作工程師所設計。

此模式涵蓋整個生命週期，從帳戶設定檔統一到對象評估及啟用，再到特定於B2B的目的地，例如[!DNL Marketo Engage]、[!DNL LinkedIn]和CRM系統。

## 使用案例模式

**B2B對象啟用**

在網頁、電子郵件和廣告頻道中啟用以帳戶為基礎的B2B對象。

**執行計畫：**&#x200B;帳戶設定檔擴充>帳戶對象評估>目的地設定> Audience Activation >監視

## 使用案例概述

B2B行銷團隊需要在帳戶層級（而非個人層級）鎖定和啟用對象。 不同於B2C受眾啟用，鎖定目標是單一消費者個人檔案，B2B受眾啟用需要瞭解人們與其所屬帳戶之間的關係，根據帳戶層級的屬性並結合個人層級的參與訊號來評估受眾成員資格，並將這些受眾傳送至支援帳戶型鎖定目標的目的地。

[!DNL RT-CDP] B2B edition利用帳戶、商機和行銷活動的專用XDM類別，以及對應個人與帳戶關係的B2B身分解析，來擴充標準[!DNL Real-Time Customer Data Platform]。 這可讓行銷人員建立帳戶對象，結合與這些帳戶相關聯之人員的家庭資料（產業、收入、員工人數）、技術資料（技術棧疊、產品使用）和行為資料（網站造訪、電子郵件參與、事件出勤率）。

已啟用的帳戶對象在整個需求產生funnel中的主要使用案例：在[!DNL LinkedIn]上的funnel最上層認知行銷活動以及顯示廣告、[!DNL Marketo Engage]中的funnel中段培育計畫，以及透過CRM整合的底層funnel銷售啟用。 帳戶隱藏對象可藉由排除現有客戶、已關閉的遺失帳戶或已處於活躍銷售週期的帳戶，來防止浪費的支出。

>[!NOTE]
>如果您的使用案例涉及在人員層級(B2C)而不是帳戶層級啟用對象，請參閱[對目的地的對象啟用](../audience-building-activation/audience-activation-to-destinations.md)。 該模式使用標準RT-CDP資料模型，不需要B2B edition。

## 主要業務目標

此使用案例模式支援下列業務目標。

### 增加銷售機會開發

透過表單、事件、內容和多管道參與，為銷售管道產生更多合格銷售機會。

**KPI：**&#x200B;潛在客戶、每個潛在客戶的成本、潛在客戶轉換

[進一步瞭解如何增加銷售機會開發](/help/blueprints/business-objectives/acquisition-growth/increase-lead-generation.md)

### 改善銷售機會資格和轉換

透過評分、培育及個人化的後續追蹤，提高銷售機會品質並加速管道進度。

**KPI：**&#x200B;潛在客戶轉換、潛在客戶/潛在客戶轉換、效率

[進一步瞭解如何改善銷售機會資格和轉換](/help/blueprints/business-objectives/qualification-sales-b2b/improve-lead-qualification-conversion.md)

### 贏取新客戶

透過鎖定目標的贏取促銷活動、相似對象和付費媒體最佳化，來擴大客戶基礎。

**KPI：**&#x200B;新客戶、客戶贏取成本、潛在客戶/潛在客戶轉換

[進一步瞭解如何取得新客戶](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

### 最佳化行銷支出和ROI

透過更好的目標定位、歸因、對象抑制和預算分配，改善行銷投資報酬。

**KPI：**&#x200B;成本節省、客戶贏取成本、遞增收入

[進一步瞭解最佳化行銷支出和ROI](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md)

## 戰術使用案例範例

以下案例說明此模式在實際中如何套用。

- **在[!DNL LinkedIn]**&#x200B;上以帳戶為基礎的廣告 — 使用從[!DNL RT-CDP] B2B edition啟用的帳戶清單，將符合您理想客戶設定檔(ICP)的帳戶與贊助內容和[!DNL LinkedIn]上的InMail行銷活動鎖定在目標
- **[!DNL Marketo Engage]nurture program targeting** — 啟用帳戶對象至[!DNL Marketo Engage]，以根據帳戶層級的資格條件將相關的銷售機會和聯絡人註冊到目標的nurture資料流
- **CRM帳戶清單同步處理** — 將合格的帳戶清單推送至[!DNL Salesforce]或[!DNL Microsoft Dynamics]，以便銷售團隊能見度、地區指派及外站潛在客戶工作流程
- **付費媒體的帳戶隱藏** — 從付費贏取行銷活動中，隱藏現有客戶、已結束贏取帳戶，或處於有效銷售週期的帳戶，以減少浪費的支出
- **意圖型帳戶目標定位** — 在帳戶層級結合第三方意圖訊號與第一方參與資料，以識別並啟用市場內帳戶的對象
- **向現有帳戶進行產品交叉銷售** — 使用一條產品線而非另一條產品線來建立帳戶的對象，然後針對交叉銷售行銷活動啟用電子郵件和廣告管道
- **活動和網路研討會鎖定目標** — 啟用廣告和電子郵件通道的帳戶對象，以推動目標帳戶的事件註冊
- **競爭取代行銷活動** — 使用競爭者產品並透過廣告和電子郵件頻道啟用量身打造訊息的目標帳戶
- **階層式帳戶參與** — 根據彙總的個人層級活動，將帳戶細分為參與層級（高、中、低），並為每個層級啟用差異化行銷活動
- **合作夥伴共同行銷對象** — 透過雲端儲存空間目的地，與通路合作夥伴或共同行銷計畫共用帳戶對象區段

## 關鍵績效指標

以下KPI可協助評估此使用案例模式的成功。

| KPI | 說明 | 測量方法 |
| --- | --- | --- |
| 帳戶觸及 | 透過啟用通道達到的目標帳戶數量 | 追蹤每個目的地啟用的不重複帳戶 |
| 帳戶參與率 | 顯示參與訊號的已啟動帳戶百分比 | 衡量彙總至帳戶的個人層級參與度 |
| 管道影響 | 歸因到帳戶型啟用行銷活動的收入管道 | 追蹤從已啟用的帳戶對象建立的商機 |
| 每個參與帳戶的成本 | 行銷支出除以顯示參與度的帳戶數量 | 跨廣告和電子郵件頻道成本計算 |
| 潛在客戶轉換率 | 已啟動科目中轉換為商機的潛在客戶百分比 | 追蹤啟用的受眾的銷售線索到商機的轉換 |
| 對象隱藏省錢 | 透過從付費行銷活動中隱藏不符合資格的帳戶來避免成本 | 從隱藏對象測量支出減少 |
| 帳戶涵蓋範圍 | 啟用的受眾涵蓋的可定址市場(TAM)總數百分比 | 比較已啟用的帳戶與總ICP宇宙 |

## 應用程式

以下應用程式可用來實作此使用案例模式。

- **[!DNL Real-Time CDP]B2B edition** — 帳戶設定檔統一、B2B身分解析、帳戶對象評估、B2B專屬目的地設定和帳戶對象啟用的核心平台
- **[!DNL Adobe Experience Platform] (AEP)** — B2B XDM資料模型化、從CRM和行銷自動化來源擷取資料、身分服務和控管的基礎基礎架構
- **[!DNL Marketo Engage]** — 由啟用的帳戶對象提供的潛在客戶培養方案、評分和行銷活動執行的主要B2B行銷自動化目的地

## 相關文件

下列資源提供此使用案例模式中所使用功能的其他內容和詳細指引。

**[!DNL RT-CDP]B2B edition**

- [Real-Time CDP B2B edition概觀](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/overview#rtcdp-b2b)
- [Real-Time CDP中的B2B結構描述](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/rtcdp/schemas/b2b)
- [帳戶對象](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/types/account-audiences)
- [RT-CDP B2B edition產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/real-time-customer-data-platform-b2b-edition-prime-and-ultimate-packages.html)

**對象評估與細分**

- [Segmentation Service概述](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/home)
- [區段產生器UI指南](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/ui/segment-builder)
- [對象構成](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/ui/audience-composition)
- [串流區段](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [分段護欄](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/guardrails)

**目的地和啟用**

- [目標概覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/home)
- [目的地目錄](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/catalog/overview)
- [Marketo Engage目的地](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/catalog/adobe/marketo-engage)
- [LinkedIn符合的對象目的地](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/catalog/social/linkedin)
- [Salesforce CRM目的地](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/catalog/crm/salesforce)
- [Microsoft Dynamics 365目的地](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/catalog/crm/microsoft-dynamics-365)
- [Amazon S3目的地](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/catalog/cloud-storage/amazon-s3)
- [啟用串流目的地的對象](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [對批次目的地啟用對象](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [啟動護欄](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/guardrails)

**資料來源與聯結器**

- [來源概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sources/home)
- [Marketo Engage聯結器](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
- [Salesforce聯結器](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sources/connectors/crm/salesforce)

**資料模型與身分**

- [XDM系統概覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/xdm/home)
- [Identity Service總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/identity/home)
- [設定檔概述](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/home)
- [合併原則概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/merge-policies/overview)

**資料控管和隱私權**

- [資料控管概覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/home)
- [資料使用標籤概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/labels/overview)
- [同意與偏好設定](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)

**監視與可觀察性**

- [警報概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/observability/alerts/overview)
- [監視目的地資料流](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/dataflows/ui/monitor-destinations)
- [監視來源資料流](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sources/api-tutorials/monitor)
- [授權使用量儀表板](https://experienceleague.adobe.com/en/docs/experience-platform/landing/license-usage-and-guardrails/license-usage-dashboard)

**報告與分析**

- [CJA概觀](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-overview/cja-overview)
- [連線總覽](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-connections/overview)
- [資料檢視總覽](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dataviews/data-views)

**教學課程與指南**

- [Real-Time CDP B2B edition快速入門](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro)
- [建立B2B來源的結構描述](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/rtcdp/schemas/b2b)
- [沙箱工具](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sandbox/sandbox-tooling-api/overview)
