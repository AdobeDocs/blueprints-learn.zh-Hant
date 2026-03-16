---
title: 購買群組式行銷與歷程管理
description: 瞭解如何開發符合潛在客戶購買群組資格的帳戶層級歷程，以改善B2B行銷效率。
solution: Journey Optimizer, Real-Time Customer Data Platform
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '7932'
ht-degree: 0%

---


# 購買群組式行銷和歷程管理

本指南提供購買群組式行銷和歷程管理的全面實作參考。 它是專為需要透過使用[!DNL Adobe Journey Optimizer B2B Edition]和[!DNL Real-Time CDP B2B Edition]的購買群組管理來實作帳戶層級歷程協調的解決方案架構師、行銷技術人員和實作工程師所設計。

運用本檔案瞭解應設定哪些專案、在哪裡有實作選擇，以及促成每項決策的利弊取捨。

與個人層級的歷程模式不同，此模式會在帳戶層級運作、將個人銷售機會限定於與解決方案興趣相關的購買群組、在購買群組層級評分參與度，以及編排多步驟帳戶歷程，將帳戶透過管道階段進展至銷售整備。

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

## 使用案例模式

**購買群組行銷與歷程管理**

開發符合潛在客戶購買群組資格的帳戶層級歷程，以改善B2B行銷效率。

**功能鏈：**&#x200B;帳戶識別>購買群組定義>潛在客戶資格>帳戶歷程執行>參與計分>報告

## 應用程式

在此使用案例模式中使用以下Adobe應用程式。

- **[!DNL Journey Optimizer B2B Edition]([!DNL AJO B2B])** — 協調帳戶層級的歷程、使用角色範本和解決方案興趣來管理購買群組、對個人和購買群組層級的參與評分、作者B2B電子郵件內容、傳送SMS訊息、設定銷售警示，以及提供B2B分析儀表板。
- **[!DNL Real-Time CDP B2B Edition]([!DNL RT-CDP B2B])** — 從跨來源B2B資料中統一帳戶設定檔、解析人員與帳戶的關係、評估帳戶層級的對象、設定B2B特定的目的地([!DNL Marketo Engage]、[!DNL LinkedIn]、CRM)，以及強制跨B2B資料進行資料控管。

## 基礎函式

下列基本功能必須為此使用案例模式準備就緒。 對於每個函式，狀態會指出它通常是必要的、假設為預先設定或不適用。

| 基礎函式 | 狀態 | 必須準備就緒的專案 | Experience League參考 |
| --- | --- | --- | --- |
| 管理與治理 | 必填 | 已啟用[!DNL AJO B2B Edition]和[!DNL RT-CDP B2B Edition]許可權的布建沙箱。 為B2B行銷人員、銷售作業和具有適當許可權以購買群組管理、帳戶歷程和CRM整合設定的Administrator設定的角色。 | [沙箱總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sandbox/home)，[存取控制總覽](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| 資料模型與準備 | 必填 | 使用B2B特定類別設定的B2B XDM結構描述：XDM商業帳戶、XDM商業機會、XDM商業人員（銷售機會/聯絡人）、XDM商業促銷活動和XDM商業行銷清單。 帳戶屬性、人員屬性和活動/參與資料的欄位群組必須準備就緒。 為每個結構描述建立和啟用設定檔的資料集。 | [XDM系統總覽](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)，[B2B結構描述類別](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| 資料來源與收集 | 必填 | 已建立B2B資料擷取管道，通常透過[!DNL Marketo Engage]來源聯結器或[!DNL Salesforce]/[!DNL Dynamics] CRM來源聯結器。 帳戶、人員、機會、行銷活動和行銷活動成員資料必須流入AEP資料集。 行為參與資料（網站造訪、電子郵件互動、內容下載）也必須擷取以進行參與計分。 | [來源總覽](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)，[Marketo Engage聯結器](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo) |
| 身分和設定檔設定 | 必填 | 已設定用來解析個人與帳戶關係的B2B身分解析。 B2B識別碼的身分名稱空間（[!DNL Marketo]個人ID、[!DNL Salesforce]銷售機會/聯絡人ID、帳戶ID）必須存在。 為B2B設定檔統一設定的合併原則。 帳戶設定檔必須從跨來源資料統一。 | [識別服務概述](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)，[B2B識別解析](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-overview) |
| 對象定義與細分 | 必填 | 使用帳戶屬性、人員屬性和活動資料建立的帳戶層級對象定義。 帳戶對象會識別哪些帳戶進入購買群組歷程。 批次評估通常足以用於B2B帳戶歷程，但串流評估可用於即時帳戶資格觸發器。 | [細分服務總覽](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)，[帳戶對象](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/types/account-audiences) |

## 支援功能

以下功能可擴大此使用案例模式，但不是核心執行的必要功能。

| 支援功能 | 狀態 | 為什麼這很重要 | Experience League參考 |
| --- | --- | --- | --- |
| 計算/衍生屬性建立 | 推薦 | 計算屬性可將個人層級的參與事件（電子郵件開啟、內容下載、網路研討會出席次數）彙總到帳戶層級的參與量度，以饋送購買團體評分和帳戶資格邏輯。 | [計算屬性總覽](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| 資料生命週期管理 | 推薦 | 同意管理對於B2B電子郵件和簡訊通訊至關重要。 資料集到期原則有助於管理暫時性參與資料的生命週期，並確保符合資料保留要求。 | [進階資料生命週期管理](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| 資料使用標籤和實作 | 推薦 | B2B資料通常包含敏感的公司資訊和商務聯絡人的個人資料。 資料控管原則可確保跨目的地合規使用B2B資料，尤其是在啟用至廣告平台或協力廠商系統時。 | [資料控管概觀](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home) |
| 監控與可觀察性 | 推薦 | 監視可確保B2B資料管道（CRM/[!DNL Marketo]同步）狀況良好、帳戶設定檔正在更新，以及帳戶歷程執行正在順利進行且沒有失敗。 針對來源資料流失敗發出警報對維護資料貨幣至關重要。 | [可觀察性深入分析概觀](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| 報告與分析 | 已包含 | [!DNL AJO B2B Edition]內的B2B分析儀表板提供購買群組參與度、帳戶歷程績效和管道量度。[!DNL CJA B2B Edition] 透過帳戶層級工作區分析、購買群組分析和機會關聯來延伸分析。 | [CJA概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) |

## 應用程式函式

此計畫會從應用程式功能目錄中執行下列功能。 函式會對應至實作階段，而非編號步驟。

### [!DNL Journey Optimizer B2B Edition] ([!DNL AJO B2B])

| 函式 | 實作階段 | 說明 |
| --- | --- | --- |
| 解決方案興趣設定 | 階段1：解決方案興趣與購買群組設定 | 定義將產品或服務對應至購買群組資格標準的解決方案興趣 |
| 購買群組管理 | 階段1：解決方案興趣與購買群組設定 | 使用角色範本、角色對應及解決方案興趣定義，建立及管理購買群組 |
| 帳戶Journey Orchestration | 階段3：帳戶歷程設計和執行 | 使用條件、動作和參與型分支來設計和管理多步驟帳戶歷程 |
| 參與分數 | 階段2：銷售機會資格和參與計分 | 對購買群組內的個人層級參與度評分，以測量購買群組的完整度和整備程度 |
| 帳戶資格 | 階段2：銷售機會資格和參與計分 | 使用AI支援的帳戶資格代理來評估帳戶整備和管道品質 |
| B2B電子郵件製作 | 階段3：帳戶歷程設計和執行 | 使用範本、視覺片段、品牌主題和AI輔助內容產生來建立B2B電子郵件內容 |
| SMS頻道管理 | 階段3：帳戶歷程設計和執行 | 設定和管理B2B帳戶歷程中的簡訊通訊 |
| 銷售警示設定 | 第4階段：銷售協調與CRM整合 | 設定銷售警報電子郵件，通知銷售團隊帳戶參與里程碑和購買訊號 |
| CRM銷售分析 | 第4階段：銷售協調與CRM整合 | 提供CRM內的可見度([!DNL Salesforce]， [!DNL Dynamics])，以取得購買群組狀態、參與資料和帳戶歷程進度 |
| B2B Analytics儀表板 | 階段5：報告與最佳化 | 透過智慧和參與儀表板，監控帳戶歷程績效、購買群組參與和管道量度 |

### [!DNL Real-Time CDP B2B Edition] ([!DNL RT-CDP B2B])

| 函式 | 實作階段 | 說明 |
| --- | --- | --- |
| 帳戶設定檔統一 | 階段0：B2B Data Foundation | 使用專門的XDM B2B結構描述類別和欄位群組，將跨來源B2B資料整合至統一的帳戶設定檔中 |
| B2B身分解析 | 階段0：B2B Data Foundation | 使用主要識別碼來解析人員與帳戶的關係，支援多重層次帳戶階層，以及多對多人員與帳戶的對應 |
| 帳戶對象評估 | 階段0：B2B Data Foundation | 評估結合帳戶屬性、個人屬性和活動資料的帳戶層級區段會籍 |
| 帳戶目的地設定 | 第4階段：銷售協調與CRM整合 | 使用帳戶層級欄位對應來設定與B2B特定目的地（[!DNL Marketo Engage]、[!DNL LinkedIn]、CRM系統）的連線 |
| 帳戶Audience Activation | 第4階段：銷售協調與CRM整合 | 將基於帳戶的對象發佈到目的地，以進行基於帳戶的定位和抑制 |
| [!DNL Marketo Engage]整合 | 階段0：B2B Data Foundation | 使用原生B2B來源和目的地聯結器，與[!DNL Marketo Engage]雙向擷取及啟用資料 |
| B2B資料控管 | 階段0：B2B Data Foundation | 跨B2B帳戶資料集中和啟用程式強制執行資料使用原則和同意 |

## 先決條件

開始實作前請先完成下列作業。

- 已在目標沙箱上布建及啟用[!DNL AJO B2B Edition]授權
- 已在目標沙箱上布建及啟用[!DNL RT-CDP B2B Edition]授權
- CRM系統（[!DNL Salesforce]或[!DNL Microsoft Dynamics 365]）可使用適當的API認證進行雙向資料同步處理
- 已連線[!DNL Marketo Engage]個執行個體（如果使用[!DNL Marketo]作為行銷自動化平台），並設定來源聯結器
- 已部署的B2B XDM結構描述：帳戶、人員、機會、促銷活動和具有必要欄位群組的促銷活動成員類別
- 已擷取到AEP中的帳戶和人員資料，並解決個人與帳戶的關係
- 已設定電子郵件頻道：委派子網域、IP集區已回暖，以及已為B2B電子郵件傳送建立頻道介面
- 已設定的SMS提供者（如果帳戶歷程中使用了SMS通道）： [!DNL Sinch]、[!DNL Twilio]或已布建的[!DNL Infobip]認證
- 銷售團隊已加入CRM銷售分析元件（已安裝[!DNL Salesforce]個AppExchange套件或是[!DNL Dynamics]個解決方案）
- 準備內容資產：培育和銷售警示電子郵件的B2B電子郵件範本、品牌主題和視覺片段
- 解決方案興趣分類法定義：將擁有相關購買群組的產品/服務清單
- 購買設計的群組角色範本：每個解決方案興趣所需的角色和角色（例如，經濟採購員、技術評估人員、冠軍）

## 實作選項

本節說明各種可用的實作方法，每種方法都根據不同的組織需求和成熟度層級量身打造。

### 選項A：單一解決方案興趣與線性帳戶歷程

**最適合：**&#x200B;剛開始購買群組管理的組織，想要從單一產品線或解決方案服務開始、驗證方法，並在擴展至多個解決方案興趣之前進行反複運算。

**運作方式：**

此方法著重於單一解決方案興趣（一種產品或服務）和一個購買群組範本。 線性帳戶歷程的設計包含循序階段：帳戶識別、購買群組形成、培養參與、參與分數臨界值和銷售移交。 歷程遵循簡單路徑，沒有複雜的分支或平行軌道。

潛在客戶是從CRM或[!DNL Marketo Engage]擷取的，因此有資格購買群組角色。 帳戶歷程會傳送培養電子郵件給參與不足的角色、監視參與分數，並在購買群組達到定義的完整度和參與臨界值時觸發銷售警報。 在引入複雜性之前，此方法可提供清晰、可衡量的概念證明。

**主要考量事項：**

- 實作與驗證更簡單，適用於首次部署
- 限制一次只能購買一項產品/服務
- 線性歷程結構可能無法容納複雜的多階段購買週期

**優點：**

- 以最少的設定複雜度快速實現價值
- 與單一解決方案興趣關聯的清晰成功量度
- 更容易解釋並獲得組織的認可
- 簡單明瞭的報告和KPI測量

**限制：**

- 不處理交叉銷售或多產品案例
- 對多個解決方案感興趣的帳戶需要單獨的、不協調的歷程
- 可能無法充分利用購買群組管理功能

**Experience League：**

- [AJO B2B edition概觀](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/guide-overview)
- [建立購買群組](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-overview)

### 選項B：具有分支帳戶歷程的多個解決方案興趣

**最適合：**&#x200B;擁有多個產品線或服務方案，且需要根據解決方案興趣管理不同購買群組的組織，其帳戶歷程會根據哪些解決方案興趣是活躍的，以及每個購買群組在資格認證過程中的時間長短。

**運作方式：**

定義多個解決方案興趣，每個都有自己的購買群組角色範本。 帳戶歷程從帳戶識別開始，並根據行為訊號、第一方資料或明確意圖，評估哪些解決方案興趣適用於每個帳戶。 歷程分支負責處理每個使用中的解決方案興趣，並為相同帳戶中不同的購買群組執行平行培養追蹤。

參與分數是每個購買群組獨立運作，允許一個購買群組達到銷售整備，而另一個購買群組仍在培育。 銷售警示是根據解決方案興趣而設定，因此當特定購買群組符合資格時，就會通知適當的銷售團隊或專家。 CRM分析會顯示帳戶的所有作用中購買群組，為銷售提供整體檢視。

**主要考量事項：**

- 需要明確定義的解決方案興趣分類法和不同的購買群組範本
- 歷程複雜性會隨著解決方案興趣的增加而提升
- 必須規劃跨購買群組協調（例如，在多個購買群組中擔任角色的共用聯絡人）

**優點：**

- 支援交叉銷售和多產品帳戶策略
- 每個購買群組的獨立評分可提供精細的管道可見度
- 銷售團隊會根據解決方案興趣收到目標式警示
- 將[!DNL AJO B2B Edition]購買群組管理功能最大化

**限制：**

- 更高的實作複雜度和更長的部署時間
- 需要更多內容資產（根據解決方案興趣個別追蹤電子郵件）
- 針對每個帳戶擁有多個購買群組，報告會較為複雜
- 屬於多個購買群組的聯絡人過度傳送訊息的風險（需要頻率管理）

**Experience League：**

- [解決方案興趣](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/solution-interests)
- [帳戶歷程](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-overview)

### 選項C：AI輔助的帳戶資格，具有自動化歷程進度

**最適合下列情況：**&#x200B;擁有大量歷史資料的成熟B2B組織，這些組織想要利用AI支援的帳戶資格代理程式，以自動化帳戶整備程度評估、減少手動資格工作，以及根據AI產生的整備程度分數動態調整歷程路徑。

**運作方式：**

此方法以Option B的多重解決方案興趣基礎為基礎，但新增AI支援的帳戶資格，以自動化歷程階段之間的轉換。 AI資格代理程式會使用更廣泛的訊號集（購買群組完整性、參與速度、首次符合、歷史轉換模式和意圖資料）來評估帳戶整備程度，而非僅依賴規則型參與分數臨界值。

帳戶歷程使用AI資格輸出來決定後續步驟：在整備程度高的帳戶會被快速追蹤到銷售警示，處於中間層的帳戶會獲得強化培養，而整備程度低的帳戶會被放置在長期認知度追蹤中。 AI代理程式會在新的參與資料到達時持續重新評估，啟用動態歷程進展而無需手動干預。

**主要考量事項：**

- 需要足夠的歷史資料來訓練有效的資格模型
- AI輸出應在完整部署之前根據實際管道結果驗證
- 與[!DNL CJA B2B Edition]完美結合，以分析資格精確度和管道關聯

**優點：**

- 減少手動資格鑑定工作，並消除任意的臨界值移交
- 以動態方式適應不斷變化的帳戶行為和參與模式
- 除了簡單的參與分數之外，還納入了多個訊號，從而提高了管道品質
- 持續重新評估可防止帳戶卡在不正確的歷程階段中

**限制：**

- 需要歷史轉換資料才能進行有意義的AI訓練
- 「黑匣子」資格決定可能讓銷售團隊在開始時更難理解和信任
- 當帳戶意外合格或完全不合格時，疑難排解會更複雜
- 取決於所有輸入訊號的資料品質和完整性

**Experience League：**

- [帳戶資格](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-group-stages)
- [AJO B2B中的AI助理](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/guide-overview)

### 選項比較

| 條件 | 選項A：單一解決方案興趣 | 選項B：多重解決方案興趣 | 選項C：AI輔助的資格 |
| --- | --- | --- | --- |
| 最適合 | 第一個部署，單一產品線 | 多產品組織 | 具有歷史資料的成熟組織 |
| 複雜性 | 低 | Medium — 高 | 高 |
| 價值實現時間 | 2-4週 | 4-8週 | 6-12週 |
| 解決方案興趣 | 1 | 多個 | 多個 |
| 歷程結構 | 線性 | 分支，平行軌道 | 動態、AI驅動漸進 |
| 評分方法 | 規則型臨界值 | 每個購買群組的規則型 | AI支援的資格+規則 |
| 內容需求 | 最小（一個培養軌跡） | 高（根據解決方案興趣） | 高+動態內容選擇 |
| 銷售調整 | 單一警報工作流程 | 依解決方案興趣的警報 | 已排定優先順序、AI評分的警報 |
| 需要 | 基本B2B資料基礎 | 定義良好的解決方案分類法 | 歷史轉換資料+分類法 |

### 選擇正確的選項

從這些問題開始，決定最佳實作方法：

1. **有多少不同的產品或服務擁有獨立的購買委員會？** 如果答案為一（或組織想要先證明這個概念），請從選項A開始。若有多個，請至問題2。

2. **是否有足夠的歷史資料顯示成功/失敗交易、購買委員會組合和參與模式？** 如果是，且組織想要將手動資格降至最低，則選項C可提供最自動化的方法。 如果沒有，選項B會以規則型評分提供多解決方案興趣支援。

3. **組織的變更管理容量是多少？** 選項B和C需要更多的組織協調（內容製作、銷售支援、跨職能協調）。 如果容量有限，請從選項A開始並展開。

一個常見的進展路徑是：從選項A開始，以一個解決方案興趣來證明概念，隨著信賴度增加新增解決方案興趣以擴展至選項B，然後在有足夠的歷史資料可用於有效訓練模型時，棧疊在選項C的AI資格中。

## 實作階段

以下階段會說明此使用案例模式的逐步實作程式。

### 階段0：B2B資料基礎

**應用程式功能：** [!DNL RT-CDP B2B]：帳戶設定檔統一、B2B身分解析、[!DNL Marketo Engage]整合、B2B資料控管、帳戶對象評估

此階段會在[!DNL RT-CDP B2B Edition]中建立B2B資料基礎架構。 您將來自CRM、行銷自動化和其他來源的帳戶資料整合為單一帳戶設定檔、解決個人與帳戶的關係、設定B2B資料控管，以及建立帳戶層級的對象，以饋送至[!DNL AJO B2B Edition]購買群組管理。

#### 決定： B2B資料來源策略

哪些系統是帳戶、人員和參與資料的主要來源？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| [!DNL Marketo Engage]作為主要來源 | [!DNL Marketo]是組織的行銷自動化平台，具有豐富的參與記錄 | 原生雙向聯結器簡化了設定；參與資料會自動流動；從[!DNL Marketo]繼承了人員與帳戶的關係 |
| CRM ([!DNL Salesforce]/[!DNL Dynamics])作為主要來源 | CRM是帳戶和連絡人的記錄系統；未使用[!DNL Marketo] | 需要CRM來源聯結器設定；參與資料可能需要補充來源；來自CRM帳戶與聯絡人關聯的人對帳戶關係 |
| 混合式：帳戶的CRM + [!DNL Marketo]參與專案 | CRM擁有帳戶/聯絡人主要資料，同時[!DNL Marketo]擷取行為參與 | 使用兩者的組織最常見的模式；需要謹慎的身分解析，才能將[!DNL Marketo]個人連結至CRM聯絡人 |

#### 決定：帳戶對象策略

應如何定義歷程進入的帳戶對象？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 以第一為基礎的帳戶對象 | 根據產業、公司規模、收入層級或地理位置來鎖定帳戶 | 適合ABM目標清單；不需要參與資料；範圍廣泛 |
| 參與型帳戶對象 | 將目標鎖定於人們已顯示行為意圖訊號的位置 | 需要參與資料流動；更精確的目標定位；可能會遺漏潛在感興趣的帳戶 |
| 結合第一方+參與 | 鎖定符合理想客戶設定檔並顯示參與度的客戶 | 最精確；需要兩種資料型別；建議用於產生合格的管道 |

**UI導覽：**&#x200B;平台>來源>目錄>選取來源（[!DNL Marketo Engage]、[!DNL Salesforce]等） >設定資料流

**金鑰組態詳細資料：**

- 使用必要欄位群組為每個B2B實體（帳戶、人員、機會、行銷活動、行銷活動成員）設定B2B XDM結構
- 使用適當的排程設定CRM和/或[!DNL Marketo Engage]的來源聯結器（B2B資料通常為1-4小時的間隔）
- 設定B2B識別碼的身分名稱空間（[!DNL Marketo]個人ID、SFDC銷售機會ID、SFDC聯絡人ID、帳戶ID）
- 啟用B2B身分解析以將人員連結至帳戶
- 使用[!DNL RT-CDP]中的帳戶對象功能建立帳戶層級對象

**Experience League檔案：**

- [RT-CDP B2B edition概述](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-overview)
- [Real-Time CDP中的B2B結構描述](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [Marketo Engage來源聯結器](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
- [帳戶對象](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/types/account-audiences)
- [B2B身分解析](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-overview)

### 第1階段：解決方案興趣與購買團體設定

**應用程式功能：** [!DNL AJO B2B]：方案興趣組態，購買群組管理

此階段定義解決方案興趣（產品/服務）和購買群組範本，這些範本構成了購買群組管理模型的核心。 您將建立解決方案興趣、根據角色需求定義角色範本，並設定潛在客戶購買群組角色的方式。

#### 決定：解決方案興趣粒度

應在哪個層級定義解決方案興趣？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 產品層級的解決方案興趣 | 每個不同的產品都有各自的購買群組 | 最精細；可啟用特定產品的購買群組範本；可能會導致每個帳戶擁有許多購買群組 |
| 解決方案類別層級的興趣 | 將相關產品分組至解決方案類別（例如「Marketing Cloud」而非個別產品） | 管理更簡單；購買群組更少；角色可能更通用；建議用於初始部署 |
| 使用案例層級的興趣 | 定義有關業務成果而非產品的興趣（例如「數位轉型」） | 與諮詢式銷售一致；購買群組角色可能橫跨多個產品；更難以對應至CRM管道階段 |

#### 決定：購買群組角色範本設計

每個購買群組內應該如何定義角色？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 標準角色範本 | 使用涵蓋所有解決方案興趣的共同角色集（例如，經濟採購員、技術評估員、達人、一般使用者） | 一致的評分和資格；更易於管理；可能無法擷取解決方案的特定角色 |
| 解決方案特定角色範本 | 根據該產品的實際購買委員會，根據解決方案興趣定義獨特角色 | 更精確的資格；需要更深入瞭解每個購買流程；更高的維護程度 |
| 階層式角色範本 | 定義必要的角色（資格必填）和選用的角色（增強完整性，但不必填） | 平衡精確性與彈性；防止過於嚴格的資格標準阻礙管道 |

**UI導覽：** [!DNL AJO B2B Edition] >購買群組>方案興趣>建立方案興趣

**UI導覽：** [!DNL AJO B2B Edition] >購買群組>角色範本>建立角色範本

**金鑰組態詳細資料：**

- 使用名稱、說明及其解決的業務結果來定義每個解決方案的興趣
- 建立角色範本，指定每個購買群組所需的角色（例如，「決策者」、「影響者」、「從業人員」、「執行贊助者」）
- 設定銷售線索與角色間的資格條件：系統如何決定銷售線索與哪個角色相對應（根據職稱、部門、資歷或自訂屬性）
- 設定完整度臨界值：定義必須填入哪些百分比的角色才能將購買群組視為「完整」
- 將解決方案興趣連結至帳戶對象或可顯示潛在興趣的帳戶屬性

**選項差異的位置：**

選項A的&#x200B;**（單一解決方案興趣）：**
建立一個解決方案興趣和一個角色範本。 專注於清晰、瞭解的組織主要產品或服務的購買行動。

選項B的&#x200B;**（多重解決方案興趣）：**
建立多個解決方案興趣，每個都有自己的角色範本。 將每個解決方案興趣對應到適當的CRM產品/機會型別，以便下游管道追蹤。

選項C （AI輔助資格）的&#x200B;**：**
設定解決方案興趣和角色範本，如選項B所示，但額外設定AI資格代理程式，其中包含有關成功購買群組構成和交易結果的歷史資料，以訓練資格模型。

**Experience League檔案：**

- [購買群組概觀](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-overview)
- [解決方案興趣](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/solution-interests)
- [角色範本](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-role-templates)
- [建立購買群組](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-create)

### 階段2：銷售機會資格和參與度評分

**應用程式功能：** [!DNL AJO B2B]：參與計分、帳戶資格

此階段會設定參與計分模型，以測量購買群組內之個人層級的參與，並將其累計至購買群組和帳戶層級的整備分數。 您將設定評分規則、定義資格的參與臨界值，並選擇性地啟用AI支援的帳戶資格。

#### 決定：參與評分模型

參與度在人員和購買群組層級上應該如何評分？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 活動型得分 | 將點值指派給特定動作（電子郵件開啟= 5點，內容下載= 15點，示範要求= 50點） | 透明且易於調整；需要隨著內容和管道的變更持續進行維護；[!DNL Marketo]使用者最熟悉 |
| 造訪間隔加權評分 | 將最近的活動加到比舊活動高的權重（降低分數模型） | 更清楚反映目前的意圖；避免陳舊的高分數誇大資格；設定更複雜 |
| 由AI支援的評分 | 使用[!DNL AJO B2B] AI資格代理程式，根據模式辨識產生整備分數 | 最複雜；會自動調整；需要歷史資料；一開始可能對銷售團隊不透明 |

#### 決定：資格臨界值方法

何時應將購買群組視為已準備好進行銷售移交？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 僅限分數臨界值 | 當彙總參與分數超過定義的值時，購買群組即符合資格 | 實作簡單；分數臨界值可能需要隨著時間調整；不考量角色組成 |
| 完整性+分數臨界值 | 當符合最低角色涵蓋範圍和分數臨界值時，購買群組即符合資格 | 更強大的資格；防止切換高分但缺少關鍵角色的購買群組 |
| AI決定的整備程度 | AI資格代理程式使用超過分數和完整度的多個訊號來判斷整備程度 | 最複雜；說明購買速度、競爭訊號和歷史模式；僅選項C |

**UI導覽：** [!DNL AJO B2B Edition] >購買群組>參與評分>設定評分規則

**金鑰組態詳細資料：**

- 定義參與計分規則：為行為事件（電子郵件開啟、點選、網頁瀏覽、內容下載、表單提交、網路研討會出席、示範請求）指派點數值
- 如果使用時效性評分，請設定評分衰減或造訪間隔加權
- 設定購買群組層級分數彙總：個人分數如何合併至購買群組分數（總和、加權平均或每個角色的最小臨界值）
- 定義資格臨界值：分數和完整度層級，可觸發轉換至下一個購買階段
- 設定AI資格代理程式（選項C）：訓練歷史交易資料、定義代理程式應考慮的訊號，以及設定信賴臨界值

**Experience League檔案：**

- [參與分數](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-group-stages)
- [購買群組階段](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-group-stages)
- [帳戶資格](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-group-stages)

### 階段3：帳戶歷程設計和執行

**應用程式功能：** [!DNL AJO B2B]：帳戶Journey Orchestration、B2B電子郵件製作、簡訊頻道管理

此階段會設計並部署協調與購買群組成員互動的帳戶歷程。 您將建立包含登入條件、動作節點（電子郵件、簡訊）、條件分支（根據購買群組階段、參與分數、角色涵蓋範圍）、等待步驟和退出條件的帳戶歷程。

#### 決定：歷程專案觸發器

什麼事件或條件會導致帳戶進入歷程？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 帳戶對象資格 | 帳戶在加入目標帳戶對象時輸入 | 批次導向；適合ABM清單式專案；對象必須預先定義 |
| 購買群組建立事件 | 首次為帳戶建立購買群組時輸入的帳戶 | 事件導向；由潛在客戶資格觸發購買群組角色；更即時 |
| 帳戶屬性變更 | 特定屬性變更時（例如意圖分數、帳戶層），帳戶會輸入 | 需要即時或近乎即時更新觸發屬性 |

#### 決定：B2B nurture的管道組合

帳戶歷程應該使用哪些管道來吸引購買小組成員？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 僅限電子郵件 | 大部分的B2B互動都是透過電子郵件進行；沒有簡訊選擇加入基礎結構 | 設定最簡單；最常見的B2B模式；可能遺漏行動優先連絡人 |
| 電子郵件+簡訊 | 組織有商務聯絡人的SMS選擇加入；需要緊急通知 | SMS對時效性警報（事件提醒、會議確認）有效；需要SMS提供者設定 |
| 電子郵件+簡訊+銷售警報 | 全方位：透過電子郵件/簡訊以及銷售團隊通知進行行銷培養 | 最全面；需要銷售團隊採用警示工作流程；協調行銷和銷售接觸點 |

#### 決定：歷程分支策略

歷程應該如何根據帳戶和購買群組狀態進行分支？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 階段型分支 | 根據購買群組階段（例如意識、考量、決定）的分支 | 與傳統funnel階段一致；內容對應至階段；清除進展路徑 |
| 角色型分支 | 分支將不同的內容傳送給不同的購買群組角色（技術內容給評估人員，ROI內容給經濟購買者） | 個人化程度更高；需要角色特定內容資產；內容製作工作量更高 |
| 參與型分支 | 根據參與分數臨界值的分支（低參與=重新參與，高=加速） | 動態且回應式的；因應實際行為；可建立複雜的分支樹 |

**使用者介面導覽：** [!DNL AJO B2B Edition] >帳戶歷程>建立歷程

**金鑰組態詳細資料：**

- 使用選取的進入條件建立帳戶歷程畫布
- 新增帳戶歷程節點：電子郵件動作、簡訊動作、等待步驟、條件分割和路徑分支
- 使用B2B Email Designer搭配品牌主題、視覺片段和AI輔助內容產生來編寫B2B電子郵件內容
- 設定參考帳戶屬性、個人屬性和購買群組資料的個人化權杖
- 設定接觸點之間的等待持續時間（B2B歷程通常使用更長的等待：電子郵件之間的3至7天）
- 定義退出條件：帳戶離開歷程的條件（購買群組達到資格閾值、在CRM中建立的機會、帳戶選擇退出）
- 若使用簡訊頻道，請設定簡訊動作（需要簡訊提供者設定和連絡人選擇加入）
- 發佈前使用測試帳戶測試歷程

**選項差異的位置：**

選項A的&#x200B;**（單一解決方案興趣）：**
設計具有循序階段的線性歷程。 輸入是以單一帳戶對象或購買群組建立事件為基礎。 一個電子郵件培養追蹤，內容愈來愈急迫和深入。

選項B的&#x200B;**（多重解決方案興趣）：**
根據解決方案興趣設計包含平行分支的歷程。 使用條件節點，根據購買群組存在，將帳戶路由至適當的培養軌跡。 每個分支都有專屬的內容和評分臨界值。

選項C （AI輔助資格）的&#x200B;**：**
設計歷程，其中條件節點會評估AI資格分數，而非（或除了）規則型臨界值。 包括動態路徑選擇，其中AI會決定是否加速、維護帳戶或取消帳戶的優先順序。

**Experience League檔案：**

- [帳戶歷程概觀](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-overview)
- [帳戶歷程節點](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-nodes)
- [B2B電子郵件製作](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/email-authoring)
- [AJO B2B中的SMS頻道](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/sms-authoring)
- [用於電子郵件製作的AI助理](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/ai-assistant-emails)

### 第4階段：銷售協調與CRM整合

**應用程式功能：** [!DNL AJO B2B]：銷售警示設定、CRM銷售分析；[!DNL RT-CDP B2B]：帳戶目的地設定、帳戶Audience Activation

此階段設定銷售警示電子郵件、部署CRM銷售分析以瞭解CRM中的可見度，以及選擇性地啟用帳戶對象至B2B目的地（[!DNL LinkedIn]、[!DNL Marketo]、CRM系統），從而在行銷和銷售之間架起橋樑。

#### 決定：銷售警示觸發策略

何時應該通知銷售有關帳戶購買群組狀態的資訊？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 里程碑式警報 | 當購買群組達到特定里程碑（合格、完整、高參與度）時通知銷售 | 清晰、分散的通知；避免警示疲勞；可能遺漏漸進參與趨勢 |
| 臨界值型警報 | 當參與分數超過定義的臨界值時通知銷售 | 持續監控；分數在臨界值附近波動時，可能會觸發多個警報 |
| 中繼轉換警報 | 當購買群組轉換到新階段（例如，從考量到決策）時通知銷售 | 與管線階段一致；最清楚的銷售動作訊號；需要定義良好的階段定義 |

#### 決定： CRM整合深度

CRM中應該顯示購買群組資料的深度為何？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 僅限銷售警示（沒有CRM內元件） | 組織未使用[!DNL Salesforce]或[!DNL Dynamics]，或CRM整合不可行 | 整合工作量最低；銷售人員會收到電子郵件通知，但沒有CRM儀表板；可見度有限 |
| CRM銷售分析儀表板 | 組織使用[!DNL Salesforce]或[!DNL Dynamics]，並想要在CRM中顯示購買群組狀態 | 需要安裝CRM銷售分析套件；提供豐富的帳戶層級智慧；建議用於大部分實作 |
| 完全雙向CRM同步 | 購買群組階段和分數會回寫CRM物件，影響CRM工作流程和報表 | 最高的整合複雜性；可啟用CRM原生管道報告；需要自訂CRM設定 |

**使用者介面導覽：** [!DNL AJO B2B Edition] >管理>銷售警示設定

**使用者介面導覽：** [!DNL AJO B2B Edition] >管理> CRM銷售分析>設定

**金鑰組態詳細資料：**

- 設定銷售警示電子郵件範本：包含購買群組狀態、參與角色、參與分數以及建議的後續動作
- 定義警示路由規則：哪些銷售代表或團隊會根據帳戶擁有權、區域或解決方案興趣收到警示
- 安裝並設定[!DNL Salesforce]或[!DNL Dynamics 365]的CRM銷售分析
- 將購買群組資料對應至CRM物件，讓銷售人員可以在其CRM工作流程中檢視購買群組構成、參與和歷程進度
- 可選擇設定帳戶目的地連線，以將帳戶對象啟用至[!DNL LinkedIn] （針對ABM廣告）、[!DNL Marketo Engage] （針對潛在客戶層級的後續追蹤）或其他B2B目的地

**Experience League檔案：**

- [銷售警示電子郵件](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/sales-alert-email)
- [CRM銷售分析](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/crm-sales-insights)
- [目標概覽](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [LinkedIn符合的對象目的地](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/social/linkedin)

### 階段5：報告與最佳化

**應用程式功能：** [!DNL AJO B2B]： B2B Analytics儀表板

此階段建立報告和分析架構，以測量購買群組績效、帳戶歷程有效性和管道影響。[!DNL AJO B2B Edition] 提供內建的analytics儀表板；[!DNL CJA B2B Edition] （如果授權）以更深入的跨管道帳戶層級深入分析來延伸分析。

#### 決定：報告方法

應該設定哪些分析工具來進行持續的效能監視？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 僅[!DNL AJO B2B]個儀表板 | [!DNL AJO B2B Edition]的內建儀表板足以購買群組和歷程量度 | 設定最快；涵蓋核心B2B量度；有限的自訂分析功能 |
| [!DNL AJO B2B]個儀表板+ [!DNL CJA B2B Edition] | 組織需要更深入的跨管道分析、購買群組分析、機會關聯和自訂歸因 | 需要[!DNL CJA B2B Edition]授權；最全面；支援帳戶層級的自由格式分析 |
| [!DNL AJO B2B]個儀表板+ CRM報表 | 組織偏好在CRM中集中管道報告，連同購買群組量度 | 需要CRM儀表板開發；將行銷和銷售量度結合在一個位置；僅限CRM報表功能 |

**UI導覽：** [!DNL AJO B2B Edition] >儀表板>參與概觀/智慧型儀表板

**金鑰組態詳細資料：**

- 存取[!DNL AJO B2B]參與儀表板，以監視購買群組參與分數、完整率和階段分佈
- 存取智慧型儀表板，以取得有關帳戶整備程度與管道品質的AI驅動深入分析
- 如果使用[!DNL CJA B2B Edition]：設定包含[!DNL AJO B2B]資料集的帳戶式CJA連線、使用「購買群組」和「帳戶」容器設定B2B資料檢視，以及建立購買群組進度、機會關聯和歸因的工作區分析
- 定義報告步調：每週購買群組績效審查、每月管道影響分析、每季方案最佳化
- 為重大事件（行銷活動啟動、內容重新整理、評分模型變更）建立註解，以與效能趨勢相互關聯

**Experience League檔案：**

- [B2B analytics儀表板](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/buying-groups-dashboard)
- [參與儀表板](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/engagement-dashboard)
- [智慧型儀表板](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/intelligent-dashboard)
- [CJA B2B edition概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)

## 實施考量

以下章節涵蓋實施期間需牢記的護欄、常見陷阱、最佳實務和取捨決定。

### 護欄和限制

- [!DNL AJO B2B Edition]帳戶歷程限制（包括並行歷程的最大值和每個歷程的最大帳戶數）遵循[!DNL AJO B2B Edition]產品護欄 — [AJO B2B護欄](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/guide-overview)
- [!DNL RT-CDP B2B Edition]支援最多50個B2B結構描述類別，並遵循標準設定檔和分段護欄 — [即時客戶設定檔護欄](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- 帳戶對象評估會依批次排程運作；並非所有區段型別都支援即時帳戶對象更新 — [分段護欄](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/guardrails)
- B2B來源聯結器擷取具有最小排程間隔（通常[!DNL Marketo]為15分鐘，CRM來源則有所不同） — [擷取護欄](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)
- 每個沙箱的電子郵件管道表面每個管道型別限製為10個 — [Journey Optimizer護欄](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)

### 常見陷阱

- **為每個購買群組定義太多角色：**&#x200B;過度指定角色（例如，需要8-10個不同的角色）會使購買群組幾乎不可能達到完整度臨界值。 從3-5個基本角色開始，並隨著模型成熟而擴展。
- **將參與分數臨界值設定得太高或太低：**&#x200B;如果臨界值太高，則沒有購買群組符合資格，導致管道無法運作。 如果太低，不合格的帳戶會淹沒銷售額。 從歷史資料分析（如果有的話）開始，並根據銷售回饋意見進行反複運算。
- **忽略個人對帳戶解析品質：**&#x200B;如果人員未正確連結至帳戶，即使正確的人參與購買，購買群組也會遺失成員。 在開始購買群組歷程之前，請先投資身分解析品質。
- **多個購買群組中的過度訊息連絡人：**&#x200B;單一連絡人可能擔任多個購買群組的角色（例如，同時擔任CRM和Data Platform購買的技術評估員的CTO）。 若沒有頻率管理，此人會收到每個使用中歷程的電子郵件。 實作跨歷程頻率規則。
- **忽略銷售啟用：**&#x200B;銷售團隊必須瞭解如何解讀購買群組資料、參與分數和銷售警示。 若沒有訓練和採用，無論資料品質如何，行銷與銷售交接都會失敗。
- **將帳戶歷程視為個人歷程：**&#x200B;帳戶歷程會在帳戶層級運作，傳送電子郵件給帳戶購買群組內的個人。 歷程設計必須考慮到每個帳戶節點執行會有多個人收到訊息，這基本上與個人層級[!DNL AJO]歷程不同。

### 最佳實務

- **從單一解決方案興趣開始，然後展開** — 在縮放至多個解決方案興趣之前，先證明此模型適用於單一購買動作。 這可讓團隊在增加複雜性之前調整角色範本、評分模型和內容。
- **將購買群組角色與CRM銷售程式保持一致** — 將購買群組角色對應至銷售團隊已辨識的角色。 使用相同的語言（經濟買家、Champion等） 因此切換是直覺式的。
- **與銷售人員實作回饋迴路** — 定期收集符合行銷資格之帳戶品質的銷售回饋。 使用此意見回饋調整參與評分臨界值和角色資格標準。
- **為角色設計內容，而不只是階段** — 不同的購買群組角色需要不同的內容：高階主管想要投資報酬率和策略影響、技術評估人員想要架構和整合細節、使用者想要易於使用的展示。 將內容資產對應至角色，以更有效率地培養。
- **提早設定CRM銷售深入分析** — 請勿等到完整歷程上線後再部署CRM可見度。 銷售團隊需要及早形成購買群組資料，以便就角色正確性和帳戶鎖定目標提供意見回饋。
- **策略性地使用等待步驟** — B2B購買週期很長。 帳戶歷程等待步驟應反映此實際情況（兩次接觸之間隔為5至14天），而非消費者式的急迫性（1至3天）。
- **監控參與速度，而不只是參與分數** — 在兩週內從分數從20增加到80的購買群組，會比六個月內達到80的購買群組發出更強烈的意圖。 設定評分和資格以說明速度。

### 權衡決定

應根據您組織的特定需求評估下列權衡。

#### 購買群組完整性與管道數量的比較

要求所有角色在購買團體取得資格之前都必須填滿，這會使管道品質達到最高，但可能會嚴重限制合格帳戶的數量，尤其是針對新產品或組織資料庫涵蓋範圍有限的市場而言。

- **較高的完整度臨界值有利於：**&#x200B;管線品質；銷售會收到完整形式的購買群組；每個帳戶較高的成功率
- **較低的完整度臨界值有利於：**&#x200B;管線數量；更多帳戶可達到銷售量；涵蓋範圍更廣；數量較多但品質可能較低
- **建議：**&#x200B;從中等臨界值（60-70%角色涵蓋範圍）開始，並根據實際獲勝率資料進行調整。 若是資料涵蓋範圍良好的成熟市場，請增加至80%以上。 針對新市場，一開始接受50-60%，並使用購買群組完整度促銷活動來填補差距。

#### 評分精細度與作業簡易性的比較

高精細的評分模型（包括數十種活動型別、造訪間隔加權和角色特定評分）可提供更精確的資格訊號，但較難維護、說明和疑難排解。

- **更高的詳細程度：**&#x200B;資格的精確度；帳戶之間的細微差異；更符合複雜的購買程式
- **較低的詳細程度：**&#x200B;簡化營運；更易於維護並向銷售人員說明；更快速的實作；較少的邊緣案例
- **建議：**&#x200B;從簡單的評分模型（10-15活動型別、統一點值）開始，並僅在簡單模型無法區分帳戶品質時增加複雜性。 完整記錄評分模型以進行銷售校準。

#### 單一歷程與多個專門歷程的比較

單一、完整的帳戶歷程，可在單一畫布中處理所有階段和解決方案興趣，提供統一的控制權，但可能會變得笨拙。 多個專門化的歷程（每個階段或解決方案各一個）比較簡單，但較難協調。

- **單一歷程偏好：**&#x200B;整體檢視；更容易確保一致的時間與訊息；更易於監視；一個位置用於所有邏輯
- **多個歷程優先：**&#x200B;模組化；更容易更新一個階段而不會影響其他階段；不同團隊可以擁有不同的歷程；更乾淨的畫布設計
- **建議：**&#x200B;選項A適合單一歷程。 若為選項B和C，請使用主要「協調」歷程，根據解決方案興趣或購買階段，將帳戶路由至專業化的子歷程。

## 相關文件

下列資源提供本指南所參考之應用程式和功能的其他詳細資料。

### [!DNL AJO B2B Edition]

- [AJO B2B edition檔案首頁](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/guide-overview)
- [購買群組概觀](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-overview)
- [解決方案興趣](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/solution-interests)
- [角色範本](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-role-templates)
- [建立購買群組](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-create)
- [購買群組階段](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-group-stages)
- [帳戶歷程概觀](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-overview)
- [帳戶歷程節點](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-nodes)
- [銷售警示電子郵件](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/sales-alert-email)
- [CRM銷售分析](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/crm-sales-insights)

### B2B電子郵件與內容

- [B2B電子郵件製作](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/email-authoring)
- [在AJO B2B中編寫SMS](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/sms-authoring)
- [用於電子郵件製作的AI助理](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/ai-assistant-emails)

### B2B analytics和儀表板

- [購買群組儀表板](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/buying-groups-dashboard)
- [參與儀表板](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/engagement-dashboard)
- [智慧型儀表板](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/intelligent-dashboard)
- [CJA B2B edition概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)

### [!DNL RT-CDP B2B Edition]

- [RT-CDP B2B edition概述](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-overview)
- [Real-Time CDP中的B2B結構描述](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [帳戶對象](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/types/account-audiences)
- [Marketo Engage來源聯結器](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)

### 資料基礎

- [XDM系統概覽](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Identity Service總覽](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [來源概觀](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)
- [Segmentation Service概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)

### 管道設定

- [開始使用電子郵件設定](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [設定簡訊頻道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)

### 資料控管與隱私權

- [資料控管概覽](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [進階資料生命週期管理](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)

### 目標

- [目標概覽](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [目的地目錄](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)
- [LinkedIn符合的對象目的地](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/social/linkedin)

### 護欄

- [即時客戶個人檔案護欄](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [分段護欄](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/guardrails)
- [擷取護欄](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)
- [Journey Optimizer護欄](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)

### 教學課程與快速入門

- [AJO B2B edition快速入門](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/guide-overview)
- [RT-CDP B2B edition教學課程](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-tutorial)
