---
title: 購買群組式行銷與歷程管理
description: 瞭解如何開發符合潛在客戶購買群組資格的帳戶層級歷程，以改善B2B行銷效率。
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 2bf57f67-80c8-4368-98d2-05706427772d
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1563'
ht-degree: 1%

---

# 購買群組式行銷和歷程管理

本指南說明購買群組型行銷和歷程管理使用案例模式，此模式使用[!DNL Adobe Journey Optimizer B2B Edition]和[!DNL Real-Time CDP B2B Edition]來透過購買群組管理實作帳戶層級的歷程協調。 它專為需要瞭解此模式的功能、其支援的業務目標、其啟用的戰術使用案例以及所涉及的Adobe應用程式的解決方案架構師、行銷技術人員和實作工程師所設計。

與個人層級的歷程模式不同，此模式會在帳戶層級運作、將個人銷售機會限定於與解決方案興趣相關的購買群組、在購買群組層級評分參與度，以及編排多步驟帳戶歷程，將帳戶透過管道階段進展至銷售整備。

## 使用案例模式

**購買群組行銷與歷程管理**

開發符合潛在客戶購買群組資格的帳戶層級歷程，以改善B2B行銷效率。

**執行計畫：**&#x200B;帳戶識別>購買群組定義>潛在客戶資格>帳戶歷程執行>參與計分>報告

## 使用案例概述

B2B組織面臨根本性的挑戰：購買決策很少由單一個人做出。 複雜的B2B購買涉及多個利害關係人 — 決策者、影響者、支持者、預算持有人和技術評估人員 — 他們共同組成「購買群組」。 傳統的銷售機會型行銷會個別對待每個人，忽略帳戶中適當的角色組合是否參與並準備購買的關鍵訊號。

購買群組型行銷和歷程管理可透過將協調單位從個人銷售機會轉移到帳戶和購買群組來解決此問題。 此模式可讓B2B行銷人員定義解決方案興趣（所銷售的產品或服務）、建立購買群組範本，以指定購買決定所需的角色、針對這些角色來限定傳入的潛在客戶、在購買群組層級為參與評分，以及協調回應購買群組完整度和整備程度訊號的帳戶歷程。

期望的結果是改善管道品質和速度：只有當帳戶中的適當人員參與且購買群組已充分完成時，行銷才會提供帳戶給銷售，減少浪費的銷售工作並加快交易進度。

## 主要業務目標

此使用案例模式支援下列業務目標。

### 改善銷售機會資格和轉換

透過評分、培育及個人化的後續追蹤，提高銷售機會品質並加速管道進度。

**KPI：**&#x200B;潛在客戶轉換、潛在客戶/潛在客戶轉換、效率

[進一步瞭解如何改善銷售機會資格和轉換](/help/blueprints/business-objectives/qualification-sales-b2b/improve-lead-qualification-conversion.md)

### 增加銷售機會開發

透過表單、事件、內容和多管道參與，為銷售管道產生更多合格銷售機會。

**KPI：**&#x200B;潛在客戶、每個潛在客戶的成本、潛在客戶轉換

[進一步瞭解如何增加銷售機會開發](/help/blueprints/business-objectives/acquisition-growth/increase-lead-generation.md)

### 增加收入與銷售

透過最佳化的數位頻道、行銷活動和客戶歷程，推動營收增長。

**KPI：**&#x200B;收入成長、管線速度、交易完成率

[進一步瞭解如何增加收入和銷售](/help/blueprints/business-objectives/revenue-monetization/increase-revenue-sales.md)

## 戰術使用案例範例

以下是可套用此模式的特定案例。

- **特定解決方案的購買群組資格** — 定義每個產品線的購買群組（例如，「企業CRM」、「資料平台」、「安全性套裝」），並使用角色範本指定所需角色（經濟購買者、技術評估者、冠軍、一般使用者），以及讓CRM和行銷自動化系統的潛在客戶符合這些角色的資格。
- **管道加速的帳戶歷程** — 協調多步驟帳戶歷程，將目標培養電子郵件傳送給購買群組中參與不足的角色，當達到參與臨界值時觸發銷售警報，並將帳戶轉換為銷售就緒階段。
- **購買群組完整性行銷活動** — 識別購買群組缺少角色的帳戶（例如，未識別經濟購買者），並啟動目標性的贏取行銷活動，以與這些帳戶中的正確角色進行互動。
- **交叉銷售帳戶歷程** — 在初始交易完成後，建立新的購買群組以補充解決方案興趣，並協調帳戶歷程，以培育擴充的購買委員會。
- **重新參與擱置的交易** — 偵測購買群組參與分數遭到拒絕的帳戶，並透過新內容、高階主管外聯或活動邀請觸發重新參與歷程。
- **透過CRM深入分析進行銷售和行銷協調** — 直接在[!DNL Salesforce]或[!DNL Dynamics 365]中呈現購買群組狀態、參與資料和帳戶歷程進度，讓銷售代表可即時檢視行銷合格帳戶。
- **事件導向購買群組更新** — 當潛在客戶參加網路研討會、下載白皮書、造訪定價頁面或要求示範時，自動更新購買群組成員資格和參與分數。
- **多區域帳戶協調** — 管理全球帳戶中的購買群組，其中不同的區域聯絡人擔任不同的角色，統一不同地理位置的參與分數。

## 關鍵績效指標

下列KPI有助於評估此使用案例模式的成效。

| KPI | 說明 | 測量方法 |
| --- | --- | --- |
| 購買群組完整率 | 已完成所有必要角色的購買群組的百分比 | [!DNL AJO B2B] Analytics儀表板：追蹤每個購買群組的角色涵蓋範圍 |
| 購買群組參與分數 | 購買群組所有成員的彙總參與分數 | [!DNL AJO B2B]參與分數：個人層級分數累積到購買群組 |
| 行銷合格帳戶(MQA)比率 | 達到行銷合格臨界值的帳戶百分比 | 帳戶歷程退出條件：帳戶正在轉換為銷售就緒階段 |
| 管線速度 | 從建立購買群組到銷售合格商機的平均時間 | CRM整合：追蹤從[!DNL AJO B2B]到CRM管道的階段轉換 |
| 採購線索群組資格率 | 成功取得購買群組角色資格的潛在客戶百分比 | [!DNL AJO B2B]購買群組管理：合格與不合格的潛在客戶比率 |
| 銷售警示回應率 | 導致銷售後續追蹤活動的銷售警示百分比 | CRM銷售分析：追蹤警示到活動的轉換 |
| 帳戶歷程完成率 | 完成預期歷程路徑的帳戶百分比 | [!DNL AJO B2B] Analytics儀表板：歷程完成量度 |
| 電子郵件參與率(B2B) | B2B Nurture電子郵件的開啟和點進率 | [!DNL AJO B2B]報告：電子郵件傳遞和參與量度 |

## 應用程式

在此使用案例模式中使用以下Adobe應用程式。

- **[!DNL Journey Optimizer B2B Edition] ([!DNL AJO B2B])** — 協調帳戶層級的歷程、使用角色範本和解決方案興趣來管理購買群組、對個人和購買群組層級的參與評分、作者B2B電子郵件內容、傳送SMS訊息、設定銷售警示，以及提供B2B分析儀表板。
- **[!DNL Real-Time CDP B2B Edition] ([!DNL RT-CDP B2B])** — 從跨來源B2B資料中統一帳戶設定檔、解析人員與帳戶的關係、評估帳戶層級的對象、設定B2B特定的目的地([!DNL Marketo Engage]、[!DNL LinkedIn]、CRM)，以及強制跨B2B資料進行資料控管。

## 相關文件

下列資源提供本指南所參考之應用程式和功能的其他詳細資料。

### [!DNL AJO B2B Edition]

- [AJO B2B edition檔案首頁](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer-b2b/user/guide-overview)
- [購買群組概觀](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-overview)
- [解決方案興趣](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer-b2b/user/buying-groups/solution-interests)
- [角色範本](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-role-templates)
- [建立購買群組](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-create)
- [購買群組階段](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-group-stages)
- [帳戶歷程概觀](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer-b2b/user/account-journeys/journey-overview)
- [帳戶歷程節點](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer-b2b/user/account-journeys/journey-nodes)
- [銷售警示電子郵件](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/sales-alert-email)
- [CRM銷售分析](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/crm-sales-insights)

### B2B電子郵件與內容

- [B2B電子郵件製作](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/email-authoring)
- [在AJO B2B中編寫SMS](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/sms-authoring)
- [用於電子郵件製作的AI助理](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/ai-assistant-emails)

### B2B analytics和儀表板

- [購買群組儀表板](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer-b2b/user/dashboards/buying-groups-dashboard)
- [參與儀表板](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer-b2b/user/dashboards/engagement-dashboard)
- [智慧型儀表板](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer-b2b/user/dashboards/intelligent-dashboard)
- [CJA B2B edition概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)

### [!DNL RT-CDP B2B Edition]

- [RT-CDP B2B edition概述](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-overview)
- [Real-Time CDP中的B2B結構描述](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/rtcdp/schemas/b2b)
- [帳戶對象](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/types/account-audiences)
- [Marketo Engage來源聯結器](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)

### 資料基礎

- [XDM系統概覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/xdm/home)
- [Identity Service總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/identity/home)
- [來源概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sources/home)
- [Segmentation Service概述](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/home)

### 管道設定

- [開始使用電子郵件設定](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [設定簡訊頻道](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)

### 資料控管與隱私權

- [資料控管概覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/home)
- [進階資料生命週期管理](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-lifecycle/home)

### 目標

- [目標概覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/home)
- [目的地目錄](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)
- [LinkedIn符合的對象目的地](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/catalog/social/linkedin)

### 護欄

- [即時客戶個人檔案護欄](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/guardrails)
- [分段護欄](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/guardrails)
- [擷取護欄](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)
- [Journey Optimizer護欄](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/get-started/guardrails)

### 教學課程與快速入門

- [AJO B2B edition快速入門](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer-b2b/user/guide-overview)
- [RT-CDP B2B edition教學課程](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-tutorial)
