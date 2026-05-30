---
title: 對象Collaboration
description: 瞭解如何使用「區段比對」，跨沙箱或組織共用及比對受眾區段。
solution: Real-Time Customer Data Platform, Experience Platform
exl-id: 7014849c-5e32-4ec3-a531-c0e8ce896f44
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1351'
ht-degree: 3%

---

# 對象Collaboration

本指南說明對象共同作業使用案例模式，此模式使用[!DNL Real-Time CDP]和[!DNL Adobe Experience Platform]中的[!DNL Segment Match]，以隱私權安全的方式跨沙箱或組織共用及比對對象區段。 它專為需要瞭解此模式的功能、其支援的業務目標、其啟用的戰術使用案例以及所涉及的Adobe應用程式的解決方案架構師、行銷技術人員和實作工程師所設計。

[!DNL Segment Match]可讓兩個或更多[!DNL Experience Platform]組織（或組織內的沙箱）透過共用區段成員資格資訊來共同作業對象資料，而不會公開基礎的PII。 參與者可以估計重疊、共用受眾，以及將相符的設定檔啟動至下游目的地。

## 使用案例模式

此使用案例會遵循Audience Collaboration模式。

使用[!DNL Segment Match]在沙箱或組織間共用及比對對象區段。

**執行計畫：**&#x200B;區段選擇>比對設定>重疊估算>對象共用>啟用

## 使用案例概述

組織越來越需要與合作夥伴、子公司或跨業務單位就受眾資料進行共同作業，同時維持嚴格的隱私權控制。 受眾共同作業可透過[!DNL Segment Match]啟用安全的區段共用，滿足此需求 — [!DNL Real-Time CDP]中的一項功能，可讓兩個或更多[!DNL Experience Platform]組織（或沙箱）使用雜湊的隱私權安全識別碼交換受眾會籍資訊。

業務案例通常會涉及某個組織（傳送者），該組織建立了有價值的受眾區段，並想要與合作夥伴組織（接收者）共用該區段，以進行共同目標定位、隱藏或擴充。 在共用前，雙方都可預估對象重疊以評估值。 共用後，接收組織即可透過其目標啟用相符的對象。

此模式與標準受眾啟用不同，因為它會在組織或沙箱之間運作，而不是與外部廣告或行銷目的地運作。 它也不同於資料潔淨室或協力廠商共同作業平台，因為它使用[!DNL Experience Platform]識別基礎結構在Adobe生態系統中以原生方式運作。

## 主要業務目標

此使用案例模式支援下列業務目標。

### 贏取新客戶

透過鎖定目標的贏取促銷活動、相似對象和付費媒體最佳化，來擴大客戶基礎。 受眾共同作業可讓組織透過比對其區段與合作夥伴受眾、識別高價值重疊，以及透過共同啟用觸及淨新客戶來發現新的潛在客戶集區。

- **KPI：**&#x200B;新客戶、客戶贏取成本、潛在客戶/潛在客戶轉換
- [贏取新客戶](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

### 降低客戶贏取成本

提升目標定位效率、從贏取促銷活動中抑制現有客戶，並最佳化媒體支出。 透過跨組織或業務單位共用隱藏區段，團隊可以避免在已轉換的客戶上浪費支出，並將預算聚焦於真正的新潛在客戶。

- **KPI：**&#x200B;客戶贏取成本、每個潛在客戶的成本、效率
- [降低客戶贏取成本](/help/blueprints/business-objectives/cost-efficiency/reduce-customer-acquisition-cost.md)

### 最佳化行銷支出和ROI

透過更好的目標定位、歸因、對象抑制和預算分配，改善行銷投資報酬。 [!DNL Segment Match]可啟用跨組織對象隱藏和共同目標定位，以減少重複並改善精確度。

- **KPI：**&#x200B;成本節省、客戶贏取成本、遞增收入
- [最佳化行銷支出和ROI](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md)

## 戰術使用案例範例

- **發佈者 — 廣告商對象比對** — 品牌與媒體發佈者共用其高價值客戶區段，以估計重疊並以個人化廣告鎖定相符的使用者，改善行銷活動關聯性而不公開PII。
- **控股公司內的跨品牌抑制** — 父級組織下的多個品牌共用客戶區段，以抑制收購行銷活動中姐妹品牌的現有客戶，減少浪費的廣告支出。
- **零售媒體網路受眾擴充** — retailer與CPG品牌合作夥伴共用購買型區段，讓品牌能夠以較高的轉換率，鎖定在retailer媒體網路上的有效買家。
- **共同行銷合作夥伴對象探索** — 在啟動聯合行銷活動之前，兩個非競爭品牌會先評估對象重疊，以評估合作潛力，並使用重疊預估來驗證對象一致性。
- **資料合作區段共用** — 資料合作共用中的組織會雜湊受眾區段，以擴大鎖定目標範圍，同時維持隱私權法規遵循和資料控管控制。
- **多沙箱受眾同盟** — 全球企業可在各地區沙箱共用受眾區段，以便在各市場間提供一致的客戶目標定位，同時遵守地區資料常駐要求。
- **跨合作夥伴啟用的忠誠度方案** — 忠誠度聯盟與參與商戶共用忠誠度等級區段，讓每個合作夥伴都能向共用的客戶群提供適合等級的促銷活動。
- **測量與歸因共同作業** — 廣告商與媒體合作夥伴共用轉換區段，因此合作夥伴可以比對公開的使用者與轉換者，以測量促銷活動的成效。

## 關鍵績效指標

以下KPI有助於評估對象共同作業實施是否成功。

| KPI | 說明 | 測量方法 |
| --- | --- | --- |
| 對象重疊率 | 共用區段中符合傳送者與接收者的設定檔百分比 | [!DNL Segment Match]重疊預估報告 |
| 相符的受眾規模 | 已成功比對且可供啟用的設定檔數 | [!DNL Segment Match]個共用狀態和受眾母體計數 |
| 從相符受眾贏取新客戶 | 透過鎖定相符區段的促銷活動所贏取的淨新客戶 | 使用相符對象追蹤行銷活動的轉換 |
| 客戶贏取成本降低 | 使用相符對象與廣泛目標定位時，降低每次收購成本 | 比較相符與不相符對象績效的行銷活動成本分析 |
| 隱藏省錢 | 抑制贏取促銷活動的已知客戶，以節省媒體支出 | 前/後隱藏媒體支出比較 |
| 行銷活動效能提升 | 改善使用相符受眾之行銷活動的轉換率、點進率或參與 | A/B測試會比較相符的對象行銷活動與控制 |
| Collaboration時間 | 從區段共用啟動到啟用整備的經過時間 | [!DNL Segment Match]工作流程時間戳記 |

## 應用程式

在此使用案例模式中使用以下應用程式。

- **[!DNL Real-Time CDP]** — 提供[!DNL Segment Match]功能以進行隱私權保護的對象共用、區段建立的對象評估，以及順流使用相符對象的目的地啟用。
- **[!DNL Adobe Experience Platform]** — 提供基礎資料基礎架構，包括[!DNL Segment Match]所依賴的身分解析、設定檔統一、資料控管和同意強制執行。

## 相關文件

下列資源提供在此使用案例模式中所使用功能的其他詳細資料。

### [!DNL Segment Match]

- [區段比對概觀](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)
- [區段比對疑難排解](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/troubleshooting)

### 細分與對象

- [Segmentation Service概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [區段產生器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [對象構成概觀](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Profile Query Language參考](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)
- [串流區段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [邊緣分段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)

### 身分和設定檔

- [Identity Service總覽](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [身分名稱空間概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/identity/features/namespaces)
- [合併原則概觀](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [即時客戶個人檔案總覽](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)

### 資料控管和同意

- [資料控管概覽](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [資料使用標籤概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/labels/overview)
- [原則執行](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/enforcement/overview)
- [同意與偏好設定](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)
- [同意和偏好設定欄位群組](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)

### 目的地和啟用

- [目標概覽](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [目的地目錄](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)
- [監視目的地的資料流](https://experienceleague.adobe.com/en/docs/experience-platform/dataflows/ui/monitor-destinations)

### 資料模型與結構

- [XDM系統概覽](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [結構描述組合基本面](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)

### 管理和存取控制

- [存取控制總覽](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home)
- [沙箱概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sandbox/home)

### 監視和可觀察性

- [警報概觀](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [可觀察性深入分析概觀](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)

### 護欄

- [即時客戶個人檔案護欄](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [分段護欄](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/guardrails)
- [啟動護欄](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)

### 教學課程

- [建立方案](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/union-schema)
- [為設定檔啟用資料集](https://experienceleague.adobe.com/en/docs/experience-platform/catalog/datasets/enable-for-profile)
