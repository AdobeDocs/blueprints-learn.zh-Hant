---
title: Customer Analytics與Insight開發
description: 瞭解如何建立跨管道分析工作區、計算量度和控制面板，以進行行為和效能分析。
solution: Customer Journey Analytics, Experience Platform
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '8947'
ht-degree: 1%

---


# Customer Analytics與insight開發

本指南提供Customer Analytics和insight產生的完整實施參考資料。 內容包括如何將[!DNL Adobe Experience Platform]資料集連線至[!DNL Customer Journey Analytics]、設定資料檢視、建立自由分析工作區、建立計算量度、發佈儀表板和行動計分卡，以及選擇性地將CJA定義的對象發佈回[!DNL Adobe Experience Platform]以供啟用。

它專為需要瞭解所有可行實作路徑、彼此間利弊及每個階段所需設定決策的解決方案架構師、行銷技術人員和實作工程師所設計。

與分類法中聚焦於啟用和參與（傳送訊息、個人化內容、啟用對象）的其他模式不同，此模式聚焦於瞭解 — 分析客戶行為、衡量行銷活動績效、識別趨勢，並產生為策略及最佳化決策提供資訊的見解。 這是最常構成的模式及配對，包含幾乎所有啟動或個人化模式。

## 使用案例概述

組織需要瞭解客戶跨管道的行為、行銷活動的表現、客戶在歷程中的流失位置、哪些內容引起共鳴，以及不同區段如何隨著時間保留。 Customer Analytics和insight產生將[!DNL Adobe Experience Platform]中的豐富跨管道資料連結至[!DNL Customer Journey Analytics]，因應此需求，分析師可以在其中建立自由格式工作區、建立自訂量度、設定歸因模型，以及發佈控制面板以供利害關係人使用。

此模式適用於多個受眾：需要深入探索分析的行銷分析師、需要效能儀表板的行銷活動經理、需要參與和保留率深入分析的產品經理，以及需要概覽KPI計分卡的高階主管。 實作方式會因主要分析重點而有所不同，例如行銷活動績效測量、跨管道歷程分析、分析導向型對象啟用或引導式產品深入分析。

## 主要業務目標

此使用案例模式支援下列業務目標。

**改善分析和報告**

增強報告功能，透過統一的儀表板和自助服務工具提供更快、更實際可行的行銷深入分析。

- **KPI：**&#x200B;效率、生產力

如需此業務目標的詳細資訊，請參閱[改善分析與報告](/help/blueprints/business-objectives/analytics-insights/improve-analytics-reporting.md)。

**啟用資料導向式決策**

為團隊提供自助分析、即時客戶見解和AI支援的預測以指導策略。

- **KPI：**&#x200B;效率、生產力

如需此業務目標的詳細資訊，請參閱[啟用資料導向式決策](/help/blueprints/business-objectives/analytics-insights/enable-data-driven-decision-making.md)。

**改善行銷歸因**

準確衡量行銷接觸點、管道和行銷活動對轉換和收入結果的影響。

- **KPI：**&#x200B;效率、遞增收入

如需此業務目標的詳細資訊，請參閱[改善行銷歸因](/help/blueprints/business-objectives/analytics-insights/improve-marketing-attribution.md)。

**最佳化行銷支出和ROI**

透過瞭解哪些管道和行銷活動產生最高回報，最佳化行銷預算分配。

- **KPI：**&#x200B;效率、遞增收入

如需此業務目標的詳細資訊，請參閱[最佳化行銷支出和ROI](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md)。

## 戰術使用案例範例

以下是可使用此模式實施的戰術使用案例範例。

- 行銷活動績效儀表板 — 跨電子郵件、簡訊、推播和付費媒體行銷活動的傳遞量度、參與率、轉換和收入歸因
- Customer Journey流失分析 — 識別客戶在購買、註冊或到職漏斗中的流失位置
- 同類群組保留分析 — 衡量不同贏取同類群組在數週、數月及數季中的保留程度
- 管道歸因模型 — 比較首次接觸、上次接觸、線性及時間衰減歸因，以瞭解哪些管道可促進轉換
- 內容效能分析 — 依區段、管道和生命週期階段找出最能引起共鳴的內容
- 產品使用與採用分析 — 追蹤功能採用、參與頻率和使用者成長趨勢
- 客戶生命週期階段分析 — 依生命週期階段（新增、作用中、有風險、已失效）劃分及分析客戶
- 行銷組合最佳化儀表板 — 比較管道投資與收入貢獻
- 跨頻道參與計分和報告 — 從網頁、應用程式、電子郵件和行銷活動互動建立複合參與分數

## 關鍵績效指標

以下KPI可協助評估此使用案例模式的成功。

| KPI | 說明 | 測量方法 |
| --- | --- | --- |
| 效率 | 縮短insight時間和手動報告工作 | 追蹤分析師在CJA實施前後建置報表所花費的時間 |
| 生產力 | 業務使用者建立的自助服務分析數目 | 監視Workspace專案建立和儀表板使用情況 |
| 遞增收入 | 歸因於見解驅動的最佳化決策的收入 | 衡量根據CJA分析最佳化之行銷活動的收入成長 |
| 轉換率 | 關鍵客戶歷程中的Funnel完成率 | 使用CJA流失視覺效果追蹤每個歷程步驟的流失率 |
| 參與度 | 跨管道的客戶互動深度和頻率 | 在CJA中建立參與計分的計算量度 |
| 保留 | 已定義期間內的客戶退貨率 | 使用CJA同類群組分析來測量保留率曲線 |

## 使用案例模式

**Customer Analytics與insight世代**

建立跨管道分析工作區、計算量度和儀表板，以瞭解客戶行為和行銷活動績效。

**函式鏈結：**&#x200B;資料連線>資料檢視設定> Workspace Analysis >計算度量建立>控制面板發佈

如需組合指南，請參閱[實作選項](#implementation-options)區段。

## 應用程式

在此使用案例模式中使用以下應用程式。

- **[!DNL Customer Journey Analytics](CJA)** — 連線、資料檢視、工作區分析、引導式分析、計算量度、控制面板、對象發佈和內容分析
- **[!DNL Adobe Experience Platform](AEP)** — 資料湖、資料集、XDM結構描述、設定檔和事件資料（用於提供CJA連線）

## 基礎函式

下列基本功能必須為此使用案例模式準備就緒。 對於每個函式，狀態會指出它通常是必要的、假設為預先設定或不適用。

| 基礎函式 | 狀態 | 必須準備就緒的專案 | Experience League參考 |
| --- | --- | --- | --- |
| 管理與治理 | 已假設就位 | 已布建工作區建立和資料檢視存取許可權的CJA產品設定檔。 CJA連線可存取的AEP資料集。 指派給適當CJA角色的使用者。 | [存取控制總覽](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| 資料模型與準備 | 必填 | 要連線到CJA的XDM結構描述和資料集必須存在於AEP中。 結構描述設計會直接影響CJA資料檢視中可用的維度和量度。 事件結構需要時間戳記欄位；查詢結構需要索引鍵欄位。 | [XDM系統總覽](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home) |
| 資料來源與收集 | 必填 | 資料必須流入AEP資料集 — 透過Web SDK的網頁事件、透過Mobile SDK的應用程式事件、AJO促銷活動事件，以及透過來源聯結器的CRM資料。 分析的豐富度取決於收集的資料範圍。 | [來源概觀](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home) |
| 身分和設定檔設定 | 必填 | CJA連線中的人員ID設定會決定如何在資料集中結合事件。 AEP中的跨裝置身分拼接可改善CJA建立完整客戶歷程的能力。 必須為人員ID欄位設定身分名稱空間。 | [身分識別服務總覽](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home) |
| 對象定義與細分 | 不適用 | CJA在分析內容中建置自己的篩選器和對象。 RT-CDP對象不是先決條件，但CJA可以透過對象發佈將對象發佈回AEP（選項C）。 | [分段服務總覽](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home) |

## 支援功能

以下功能可擴大此使用案例模式，但不是核心執行的必要功能。

| 支援功能 | 狀態 | 為什麼這很重要 | Experience League參考 |
| --- | --- | --- | --- |
| 計算/衍生屬性建立 | 推薦 | AEP計算屬性可以豐富連線至CJA的資料集，提供額外的維度和量度以供分析（例如期限購買計數、上次活動後間隔天數）。 這些設定檔層級彙總可在CJA資料檢視中作為維度使用。 | [計算屬性總覽](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| 資料生命週期管理 | 推薦 | 資料集保留原則會影響CJA中可用的歷史資料。 長期保留通常適合用於分析，以啟用逐年比較和長期趨勢分析。 設定資料集TTL以確保足夠的歷史深度。 | [進階資料生命週期管理概觀](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| 資料使用標籤和實作 | 推薦 | 敏感欄位上的治理標籤可以限制CJA資料檢視中顯示的內容。 如果PII或敏感資料包含在CJA連線中，資料控管標籤可確保遵循法規的存取，並防止在共用儀表板中未經授權的洩露。 | [資料控管概觀](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home) |
| 監控與可觀察性 | 推薦 | 應監控CJA連線健全狀況和資料的時效性。 設定來源資料流失敗和擷取問題的警報，以確保資料摘要CJA可靠且最新。 | [可觀察性深入分析概觀](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| 報告與分析 | 已包含 | 這是報表與分析實作。 當其他模式的參考計畫包含S5時，請針對分析實施使用此客戶分析和insight產生計畫。 | [CJA概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) |

## 應用程式函式

此計畫會從應用程式功能目錄中執行下列功能。 函式會對應至實作階段，而非編號步驟。

### [!DNL Customer Journey Analytics] (CJA)

下表列出在此模式中使用的CJA應用程式函式。

| 函式 | 實作階段 | 說明 |
| --- | --- | --- |
| 資料連線 | 階段1：資料連線 | 將AEP資料集繫結至CJA連線以進行跨管道分析，設定資料集型別和人員ID以進行跨資料集拼接 |
| 資料檢視設定 | 階段2：資料檢視設定 | 定義維度、量度、歸因模型、持續性設定、工作階段引數，以及影響分析透檢視的衍生欄位 |
| Workspace Analysis | 階段3：分析和量度建立 | 使用表格、視覺效果、篩選器、註解和維度劃分（選項A、B、C）建立自由格式分析專案 |
| 指導分析 | 階段3：分析和量度建立 | 使用結構化引導式工作流程進行funnel、趨勢、保留率、使用者成長和參與頻率分析（選項D） |
| 建立計算量度 | 階段3：分析和量度建立 | 使用公式、篩選器和函式來定義可重複使用KPI的計算量度，例如轉換率、參與分數和每次造訪收入 |
| 儀表板和計分卡發佈 | 第4階段：控制面板發佈 | 建立和共用互動式儀表板和行動計分卡，以供利害關係人報告 |
| 對象發佈 | 階段5：對象發佈（僅限選項C） | 將CJA定義的對象發佈回AEP即時客戶個人檔案，以供下游啟用 |
| Content Analytics | 階段3：分析和量度建立 | 分析數位屬性的內容效能趨勢、異常和疲勞（當內容分析成為焦點時） |

### [!DNL Adobe Experience Platform] (AEP)

下表列出在此模式中使用的AEP應用程式函式。

| 函式 | 實作階段 | 說明 |
| --- | --- | --- |
| 資料湖與資料集 | 先決條件(F2、F3) | 提供源事件、設定檔和查詢資料集，以饋送CJA連線 |
| Identity Service | 先決條件(F4) | 提供身分名稱空間設定，以便在CJA連線中的資料集之間拼接人員ID |

## 先決條件

實作此使用案例模式之前，必須滿足下列必要條件。

- 已為組織布建CJA產品權利
- CJA產品設定檔已設定適當的使用者存取權（工作區建立、資料檢視存取權）
- AEP沙箱包含具有資料流動的目標資料集（網頁事件、應用程式事件、行銷活動資料、CRM記錄）
- 已針對具有適當欄位群組的所有來源資料集定義XDM結構
- 識別人員ID欄位，並可在所有將連線的資料集中持續使用
- 身分識別名稱空間是在AEP中，針對CJA連線拼接中所使用的人員ID進行設定
- 利害關係人的要求會被記錄 — 哪些KPI、哪些對象會使用儀表板、哪些詳細程度
- 針對行動計分卡：利害關係人已安裝[!DNL Adobe Analytics]儀表板行動應用程式
- 選項C （對象發佈）：目標沙箱中已啟用AEP即時客戶設定檔
- 選項D （引導分析）： CJA SKU包含引導分析功能

## 實作選項

本節說明此使用案例模式的可用實作選項。

### 選項A：行銷活動績效分析

**最適合：**&#x200B;衡量及最佳化行銷活動和歷程成效 — 電子郵件行銷活動控制面板、歷程funnel分析、管道績效比較，以及行銷ROI報表。

**運作方式：**

此選項會將AJO行銷活動和歷程資料集連線至CJA、使用傳送和參與量度（傳送、傳送、開啟、點選、退回、取消訂閱）設定資料檢視、建立行銷活動績效儀表板，以及為行銷利害關係人發佈計分卡。 焦點在於瞭解行銷活動如何跨管道及隨著時間推移而執行。

資料檢視是使用行銷活動特定維度（行銷活動名稱、歷程名稱、頻道型別、訊息變體）和傳遞量度來設定。 計算量度是為衍生量度建立的，例如開啟率、點進率、轉換率和每則訊息收入。 控制面板會以趨勢分析的比較期間來顯示這些KPI。

**主要考量事項：**

- 需要AEP中的AJO行銷活動和歷程事件資料集
- 歸因模型應符合組織的行銷活動測量理念
- 考慮同時包含AJO原生報表（適用於營運傳遞量度）和CJA（適用於跨管道業務影響）

**優點：**

- 專為行銷活動測量和最佳化所打造
- 啟用跨行銷活動的比較和管道混合分析
- 計算量度提供所有行銷活動的標準化KPI定義
- 行動計分卡為行銷主管提供一目瞭然的效能

**限制：**

- 僅限於行銷活動和歷程資料；不提供完整的客戶歷程內容
- 不包含歷程路徑、流失或同類群組分析
- 歸因的適用範圍是促銷活動接觸點，而非完整的客戶歷程

**Experience League：**

- [AJO + CJA整合指南](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [Workspace概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)

### 選項B：Customer Journey Analytics

**最適合：**&#x200B;瞭解跨管道客戶歷程 — 流失分析、路徑分析、同類群組保留、歸因模型，以及跨網路、應用程式、電子郵件、CRM和離線接觸點的生命週期階段分析。

**運作方式：**

此選項可連線多個AEP資料集（網頁事件、應用程式事件、CRM資料、行銷活動互動、異動記錄），以建立客戶歷程的統一跨管道檢視。 資料檢視會使用跨所有管道的維度和量度來設定。 CJA的流量、流失、同類群組和歸因視覺效果可用來分析客戶如何移動歷程、客戶流失在哪裡、不同區段如何保留，以及哪些管道應該獲得轉換的評分。

這是最全面的分析選項，可深入提供insight給端對端客戶體驗。 此外也最複雜的實作方式，需要謹慎設定人員ID以進行跨資料集拼接，並採用周到的資料檢視設計，以公開正確的維度和量度。

**主要考量事項：**

- 需要所有連線資料集的人員ID一致，才能進行準確的跨管道分析
- AEP中的結構描述設計會直接影響CJA分析的品質和深度
- 連線中的資料集越多，表示分析越豐富，但回填時間越長
- 歸因模型需要清晰的轉換事件定義

**優點：**

- 完整跨頻道客戶歷程可見性
- 整套的CJA視覺效果：流量、流失、同類群組、歸因、自由表格
- 啟用在單一管道報表中隱藏的深入分析探索
- 支援有關客戶行為與生命週期的複雜分析問題

**限制：**

- 由於多資料集連線和跨管道拼接，導致更高的實作複雜性
- 需要更多資料檢視設定和衍生欄位的預先規劃
- 大型多資料集連線的回填作業可能需要數天時間
- 分析品質取決於基礎資料的完整性和一致性

**Experience League：**

- [連線總覽](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/overview)
- [流量視覺效果](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/flow/flow)
- [流失視覺效果](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/fallout/fallout-flow)
- [同類群組表格](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/cohort-table/cohort-analysis)
- [歸因面板](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/panels/attribution)

### 選項C：有對象發佈的Analytics

**最適合：**&#x200B;分析驅動啟動 — 透過CJA分析探索感興趣的區段，然後發佈回AEP以透過RT-CDP目的地、AJO行銷活動或AJO歷程啟動。

**運作方式：**

此選項可延伸選項A或選項B，並包含來自CJA的對象發佈。 分析人員使用跨管道行為資料和CJA篩選器的完整分析功能，在CJA中建立區段，然後將這些對象發佈到AEP即時客戶個人檔案，以供下游啟用。 這跨越了insight與動作之間的鴻溝 — 探索性分析期間發現的區段成為可操作的對象，無需在AEP區段產生器中手動重新建立。

已發佈受眾會顯示在具有原始「CJA」的AEP受眾入口網站中，並可啟用至任何RT-CDP目的地、在AJO中作為行銷活動目標或作為歷程進入條件。

**主要考量事項：**

- 需要在Target沙箱中啟用AEP即時客戶設定檔
- CJA連線必須具備可解析為AEP身分名稱空間的有效人員ID
- 已發佈的對象會計入組織的AEP對象權益
- 必須根據啟用需求（一次、每4小時、每天、每週）設定重新整理步調

**優點：**

- 關閉分析與啟動之間的回圈
- 使用CJA的跨管道行為資料來探索高價值區段
- CJA中定義的對象可運用AEP區段產生器中不提供的維度和篩選器
- 支援根據分析見解的反複細分對象條件

**限制：**

- 每個CJA客戶最多可發佈75個受眾
- 大型資料集的初始對象評估可能最多需要24小時
- CJA發佈的對象無法在AEP中編輯 — 必須在CJA中進行變更
- 需要基本分析以外的其他身分名稱空間和設定檔設定

**Experience League：**

- [受眾概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/audiences-overview)
- [建立及發佈對象](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/publish)

### 選項D：產品團隊的引導式分析

**最適合：**&#x200B;產品體驗深入分析 — 功能採用、使用者參與趨勢、保留率分析、funnel轉換，以及使用CJA的引導式分析工作流程的發行影響分析，無需複雜的Workspace專案設定。

**運作方式：**

此選項使用CJA引導式分析來產生結構化、樣板化的insight。 引導式分析提供預先建立的分析型別（funnel、趨勢、保留率、使用者成長、參與頻率、發行影響、首次使用和時間表），可引導分析師透過結構化工作流程回答特定產品和體驗問題。 產品經理和分析師若需要快速且重點的深入分析，而不需要從頭開始建立自由專案，這個模型非常合適。

此實作會將AEP資料集連線至CJA、使用事件層級的維度和量度來設定資料檢視，然後使用引導式分析工作流程來產生深入分析。 結果可儲存為Workspace專案內的面板，以供進一步自訂。

**主要考量事項：**

- 引導式分析需要包含引導式分析功能的CJA產品權益
- 最適合用於產品和體驗分析，而非行銷活動績效測量
- 提供非分析使用者更容易存取的結構化工作流程
- 可與自由格式Workspace分析結合，以進行更深入的探索

**優點：**

- 較低的進入門檻 — 結構化工作流程可引導使用者完成分析
- 專為產品體驗問題（funnel、保留率、成長率、影響）所打造
- 加速前往insight的時間，以解答常見分析問題
- 已儲存的分析可以和自由格式分析一起內嵌在Workspace專案中

**限制：**

- 比自由格式Workspace分析更缺乏彈性
- 僅限於預先建立的分析型別（funnel、趨勢、保留率、成長率、頻率、影響、時間表）
- 區段比較同時支援最多3個區段
- funnel分析支援最多15個步驟

**Experience League：**

- [引導式分析概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/overview)
- [funnel檢視](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/funnel/funnel)
- [保留檢視](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/retention/retention-rates)

### 選項比較

下表比較可用的實作選項。

| 條件 | 選項A：促銷活動績效 | 選項B：客戶歷程 | 選項C：Analytics +啟用 | 選項D：引導式分析 |
| --- | --- | --- | --- | --- |
| 最適合 | 行銷活動測量與最佳化 | 跨頻道歷程瞭解 | insight導向的對象啟用 | 產品體驗深入分析 |
| 複雜性 | 低Medium | 高 | 高 | 低 |
| 需要資料集 | AJO行銷活動/歷程事件 | 多個跨管道資料集 | 與A或B相同，加上設定檔身分 | 具有產品互動的事件資料集 |
| 重要視覺效果 | 自由表格、摘要數字、趨勢線 | 流量、流失、同類群組、歸因 | 與A或B相同，加上對象發佈 | funnel，趨勢，保留率，成長 |
| 啟用功能 | 否（僅報告） | 否（僅報告） | 是（將受眾發佈至AEP） | 否（僅報告） |
| 需要的對象 | 行銷分析師、行銷活動經理 | 資料分析師、歷程架構師 | 分析人員+啟用團隊 | 產品經理、成長分析師 |
| 使用的CJA函式 | 連線，資料檢視， Workspace，計算量度，控制面板 | 連線，資料檢視， Workspace，計算量度，控制面板 | 與A或B相同，加上對象發佈 | 連線、資料檢視、引導式分析、控制面板 |
| 首次insight的時間 | 天 | 周 | 周 | 小時 — 天 |

### 選擇正確的選項

請依照下列指引，選取最符合您需求的實作選項。

- **如果您的主要目標是衡量行銷活動的成效**，而且您有AJO行銷活動資料流入AEP，請從&#x200B;**選項A**&#x200B;開始。它提供最快的行銷績效報表價值實現時間。

- **如果您需要跨網路、應用程式、電子郵件和離線接觸點瞭解完整的客戶歷程**，而且您有多個資料集並具有一致的人員ID，請選擇&#x200B;**選項B**。它提供最深入的分析能力，但需要更多資料檢視設定的前期投資。

- **如果您想要透過將CJA發現的區段發佈回AEP以在RT-CDP或AJO中啟用，而根據深入分析採取行動**，請選擇&#x200B;**選項C**。這會延伸選項A或B與對象發佈的關聯，且需要AEP即時客戶個人檔案設定。

- **如果您的團隊需要快速、結構化的產品深入分析**，而不需要自由格式Workspace專案的複雜性，而且您的CJA SKU包含引導式分析，請選擇&#x200B;**選項D**。這是回答特定產品體驗問題的最快方式。

- **許多組織實作多個選項**：行銷團隊行銷活動儀表板的選項A、分析團隊的跨管道分析的選項B，以及產品團隊自助深入分析的選項D。 這些選項共用相同的CJA連線和資料檢視基礎架構。

## 實作階段

本節詳細說明此使用案例模式的逐步實作階段。

### 階段1：資料連線

**應用程式函式：** CJA：資料連線

此階段會設定CJA連線，將一或多個AEP資料集繫結至CJA進行分析。 連線會定義哪些資料集流入CJA、如何透過人員ID跨資料集拼接事件，以及如何擷取歷史資料和串流資料。 這是AEP的Data Lake與CJA之間的基礎連結。

#### 決定點

在此階段中必須做出以下決策。

>[!NOTE]
>**決定： AEP沙箱選擇**
>
>哪個AEP沙箱包含來源資料集？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 生產沙箱 | 生產報表的即時客戶資料 | 用於生產儀表板和利害關係人報告 |
>| 開發沙箱 | 生產部署之前的測試和反複專案 | 在提升至生產環境前，用於初始設定和驗證 |

>[!NOTE]
>**決定：資料集選取與型別指定**
>
>連線中應包含哪些AEP資料集，以及應指派每個資料集的型別？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 事件資料集 | 時間戳記行為資料（網頁互動、應用程式事件、行銷活動互動、交易） | 需要時間戳記欄位；形成大多數分析的核心 |
>| 查詢資料集 | 索引鍵值參考資料（產品目錄、行銷活動中繼資料、存放區位置） | 透過共用金鑰加入事件資料；僅使用最新狀態 |
>| 設定檔資料集 | 個人層級屬性（忠誠度層級、期限值、CRM屬性） | 在人員層級提供擴充；僅使用最新狀態 |

>[!NOTE]
>**決定：人員ID設定**
>
>哪個欄位可當作跨資料集彙整的人員ID？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| CRM ID | 組織跨管道具有一致的CRM識別碼 | 為已知客戶提供最精確的跨管道拼接 |
>| ECID (Experience Cloud ID) | 主要分析匿名Web/應用程式行為 | 裝置範圍；在沒有身分解析度的情況下，不會跨裝置彙整 |
>| 電子郵件（雜湊） | 電子郵件是資料集中的常見識別碼 | 在不同接觸點間持續擷取電子郵件時，這項功能便可正常運作 |
>| 自訂名稱空間 | 組織使用專有識別碼 | 必須符合用於發佈對象的AEP身分名稱空間（選項C） |

>[!NOTE]
>**決定：回填範圍**
>
>應該將多少歷史資料匯入連線？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 所有現有資料 | 逐年比較和長期趨勢所需的最大歷史深度 | 大型資料集（數十億筆記錄）的回填可能需要數天時間才能完成 |
>| 自訂日期範圍 | 只有最近的記錄才相關，或是需要考慮儲存最佳化 | 限制可用於分析的歷史深度 |
>| 無回填 | 只需要前瞻性分析 | 最快的連線設定；在新資料流入之前沒有可用的歷史資料 |

>[!NOTE]
>**決定：串流啟用**
>
>新資料是否應近乎即時流入CJA？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 啟用串流 | 需要近乎即時的報表（AEP擷取後約90分鐘內可提供資料） | 最常用於生產連線；可及時進行分析 |
>| 僅限批次 | 定期重新整理已足夠，且不需要串流 | 更簡單的設定；批次處理之後即可使用的資料 |

#### 設定資料連線

**使用者介面導覽：** CJA >連線>建立新連線

主要設定詳細資料：

- 連線名稱和說明應遵循組織命名慣例
- 用於CJA容量規劃的平均每日事件數
- 單一連線中的所有資料集必須來自相同的AEP沙箱
- 所有資料集的人員ID欄位必須一致，才能進行精確的跨資料集拼接
- 驗證人員ID欄位是否存在，並填入每個資料集中，然後再將其新增至連線

**Experience League檔案：**

- [連線總覽](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/overview)
- [建立或編輯連線](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/create-connection)
- [管理連線](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/manage-connections)
- [CJA護欄](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-admin/guardrails)

### 階段2：資料檢視設定

**應用程式函式：** CJA：資料檢視組態

此階段會設定資料檢視，定義連線資料在分析中的顯示方式。 資料檢視會決定要將哪些結構描述欄位公開為維度和量度、如何歸因和保留值、如何定義工作階段，以及哪些衍生欄位會將原始資料轉換為可分析的元件。 您可以從單一連線為不同的分析透檢視建立多個資料檢視。

#### 決定點

在此階段中必須做出以下決策。

>[!NOTE]
>**決定：容器命名**
>
>容器應使用哪些術語來比對業務網域？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 預設（人員/工作階段/事件） | 團隊瞭解標準分析術語 | 適用於大部分實作 |
>| 自訂名稱（例如購物者/造訪/互動） | 商務領域專用術語可改善使用者採用程度 | 協助非技術利害關係人瞭解分析範圍 |
>| B2B名稱（例如帳戶/參與/接觸點） | 聚焦帳戶層級分析的B2B分析 | 將容器範圍與B2B商業概念一致 |

>[!NOTE]
>**決定：工作階段逾時**
>
>閒置時間長短會定義工作階段界限？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 30分鐘（預設） | 標準網站分析工作階段定義 | 業界標準；與大部分分析基準一致 |
>| 15 分鐘 | 使用者可快速完成任務的短格式內容或交易式網站 | 建立更多工作階段；可能更適合擷取不同的使用者意圖 |
>| 60分鐘以上 | 長格式內容、複雜的B2B互動或研究密集型歷程 | 較少的工作階段；將長期研究擷取為單一工作階段 |
>| 使用新工作階段事件自訂 | 特定事件（例如應用程式啟動、促銷活動點進）應一律開始新的工作階段 | 提供商業邏輯驅動的工作階段界限 |

>[!NOTE]
>**決定：歸因模型預設值**
>
>什麼預設歸因模型應該套用至轉換量度？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 上次接觸（預設） | 點數應在轉換前移至最近的接觸點 | 簡單又直覺；可能低估了認知管道 |
>| 首次接觸 | 瞭解哪些管道可促進初始的認知和贏取 | 適合用於贏取分析；忽略培養接觸點 |
>| 線性 | 所有接觸點應共用相同的評分 | 公平分配；可能稀釋關鍵接觸點的影響 |
>| 時間耗損 | 最近的接觸點應該比遠處的接觸點獲得更多的評分 | 平衡造訪間隔與歷史貢獻 |
>| U形 | 第一個和最後一個接觸點應獲得最多評分 | 有助於瞭解贏取和關閉管道 |
>| 演算法 | 使用CJA的AI模型的資料導向歸因 | 最準確，但需要足夠的轉換資料量 |

>[!NOTE]
>**決定：衍生欄位邏輯**
>
>自訂商業規則是否必須將原始資料轉換為可分析的維度？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 行銷管道分類（案例時機） | 原始追蹤程式碼必須分類至管道群組 | 最常見的衍生欄位使用案例；對管道分析至關重要 |
>| 值分組 | 連續值需要分組到範圍（例如，順序值層） | 簡化連續量度的分析 |
>| 欄位合併 | 多個來源欄位應合併為單一維度 | 當跨資料集的不同結構描述路徑中存在相同的概念時，這非常有用 |
>| 規則運算式擷取 | 需要剖析結構化值（例如，從行銷活動代碼擷取行銷活動型別） | 功能強大，但需要謹慎的規則運算式模式設計 |

#### 設定資料檢視

**使用者介面導覽：** CJA >資料檢視>建立新資料檢視

主要設定詳細資料：

- 選取在階段1中建立的父連線
- 設定符合報告要求的時區和行事曆型別
- 將XDM結構描述欄位對應到具有適當持續性（配置和有效期）設定的維度
- 將XDM結構描述欄位對應到具有格式（十進位、整數、貨幣、百分比、時間）和歸因設定的量度
- 在維度上設定包含/排除規則，以篩選掉不相關的值
- 在必要時啟用量度重複資料刪除，以防止重複計數
- 建立行銷管道分類、值分組或欄位合併的衍生欄位
- 每個資料檢視最多5,000個維度和5,000個量度
- 每個資料檢視最多100個衍生欄位

#### 選項差異之處

選項A （行銷活動績效分析）的&#x200B;**：**

對應行銷活動的特定維度：行銷活動名稱、歷程名稱、管道型別、訊息變體、主旨行。 對應傳送量度：傳送、傳送、開啟、點選、退回、取消訂閱。 根據行銷活動測量原理設定轉換量度的歸因。

選項B (Customer Journey Analytics)的&#x200B;**：**

對應跨管道維度：頁面名稱、應用程式畫面、管道、促銷活動、產品、內容型別。 對應所有管道的參與和轉換量度。 設定多個歸因模型以進行比較分析。 建立管道分類和歷程階段識別的衍生欄位。

選項D （引導式分析）的&#x200B;**：**

對應產品體驗分析相關的事件層級維度和量度：功能名稱、使用者動作、參與型別。 專注於定義funnel步驟、保留標準和成長訊號的事件。

**Experience League檔案：**

- [資料檢視總覽](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/data-views)
- [建立或編輯資料檢視](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [元件設定概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/overview)
- [持續性設定](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/persistence)
- [歸因設定](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/attribution)
- [格式設定](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/format)
- [量度重複資料刪除](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/metric-deduplication)
- [包含/排除值](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/include-exclude-values)
- [工作階段設定](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/session-settings)
- [衍生欄位](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/derived-fields)

### 階段3：分析和量度建立

**應用程式函式：** CJA： Workspace Analysis， CJA：引導式分析， CJA：建立計算量度

此階段會建立分析工作區（自由格式專案或引導式分析）、衍生KPI的計算量度、分段分析的篩選器以及關鍵事件的註解。 這是實現分析價值的地方，即建立可回答業務問題的表格、視覺效果和量度。

#### 決定點

在此階段中必須做出以下決策。

>[!NOTE]
>**決定：分析方法**
>
>此分析應該使用自由格式Workspace專案還是引導式分析工作流程？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 自由格式Workspace （選項A、B、C） | 深入探索分析、自訂版面配置、複雜劃分、進階視覺效果 | 最大彈性；需要分析人員技能；支援所有視覺效果型別 |
>| 引導分析（選項D） | 結構化產品深入分析、特定問題快速解答、技術含量較低的使用者 | 更短的時間使用insight；僅限預先建立的分析型別；儲存至Workspace以供進一步自訂 |
>| 兩者 | 組織既需要深入分析，也需要快速結構化洞察 | 使用引導式分析來瞭解常見問題；使用Workspace來深入探索 |

>[!NOTE]
>**決定：視覺效果型別**
>
>哪些視覺效果能最好地傳達此使用案例的見解？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 自由格式表格 | 使用維度劃分進行詳細資料探索 | 大部分分析的基礎；支援最多10個劃分層級 |
>| 流量視覺效果 | 瞭解路徑分析行為（頁面流程、管道轉換） | 非常適合探索歷程路徑；可能因高基數而變得複雜 |
>| 流失視覺效果 | 透過定義的接觸點序列測量轉換 | 最適合funnel分析；清楚顯示每個步驟的流失率 |
>| 同類群組表格 | 根據贏取同類群組進行一段時間內的保留率分析 | 顯示不同群組保留的程度；對生命週期分析至關重要 |
>| 歸因面板 | 比較轉換量度的歸因模型 | 並排模型比較；需要明確的轉換事件定義 |
>| 摘要數字/變更 | 執行重要績效指標顯示與期間比較 | 簡潔的量度顯示一目瞭然；適用於儀表板標題 |

>[!NOTE]
>**決定：計算的量度公式**
>
>除了基本資料檢視量度以外，哪些業務KPI需要計算量度？
>
>| 量度模式 | 公式範例 | 使用時機 |
>| --- | --- | --- |
>| 比率/比率 | 訂購/造訪 | 轉換率、點進率、跳出率 |
>| 篩選量度 | 收入（頻道為「電子郵件」） | 特定管道或特定區段的測量 |
>| 每專案平均值 | 收入/訂單 | 平均訂購值、每次造訪帶來的收入 |
>| 複合公式 | （收入 — 成本） /收入 | 利潤百分比， ROI計算 |
>| 參與度分數 | 互動的加權總和 | 跨管道的複合參與計分 |

#### 設定分析和量度

**使用者介面導覽：**

- Workspace： CJA > Workspace >專案>建立專案>空白專案
- 引導式分析： CJA >首頁>引導式分析（或Workspace >建立>引導式分析）
- 計算量度： CJA >元件>計算量度>建立
- 篩選器：CJA >元件>篩選器>建立篩選器

主要設定詳細資料：

- 選取階段2中建立的資料檢視作為專案資料檢視
- 為分析設定適當的日期範圍和比較期間
- 將維度拖曳至列，將量度拖曳至欄，藉此建立自由表格
- 加入維度劃分，以探索更深層級的資料（例如依行銷活動的頻道、依產品的頁面）
- 建立可重複使用的篩選器（區段），用於對象特定分析（人員層級、工作階段層級或事件層級範圍）
- 新增註解以標籤關鍵業務事件（產品啟動、行銷活動、事件）
- 設定計算量度格式（小數、百分比、貨幣、時間）和極性（上升是好事/上升是壞事）
- 以檢視或編輯許可權與CJA使用者共用工作區專案

#### 選項差異之處

選項A （行銷活動績效分析）的&#x200B;**：**

使用依傳遞和參與量度劃分的行銷活動維度建立自由表格。 建立開啟率、點進率、轉換率、每則訊息收入與行銷活動ROI的計算量度。 新增趨勢視覺效果以追蹤一段時間內的行銷活動成效。 使用區段比較來比較行銷活動變體。

選項B (Customer Journey Analytics)的&#x200B;**：**

建立流失視覺效果以識別歷程還車點。 建立流量視覺效果以探索跨頻道的導覽模式。 建立同類群組表格，以透過贏取同類群組來測量保留率。 設定「歸因」面板，比較轉換量度的歸因模型。 建立歷程完成率、跨頻道參與分數和生命週期階段轉換的計算量度。

選項C的&#x200B;**（Analytics含對象發佈）：**

從選項A或B建立分析工作區，然後在分析期間識別高值或表現缺佳的區段。 建立可擷取這些區段以便在階段5中發佈的CJA篩選器。

選項D （引導式分析）的&#x200B;**：**

根據業務問題選取適當的引導式分析型別。 設定關鍵事件、日期範圍、計數方法和區段比較。 將完成的分析儲存為Workspace專案中的面板，以供進一步自訂。

**Experience League檔案：**

- [Workspace概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [建立專案](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/build-workspace-project/create-projects)
- [自由格式表格](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/freeform-table/freeform-table)
- [流量視覺效果](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/flow/flow)
- [流失視覺效果](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/fallout/fallout-flow)
- [同類群組表格](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/cohort-table/cohort-analysis)
- [歸因面板](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/panels/attribution)
- [劃分維度](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/components/dimensions/t-breakdown-fa)
- [篩選器概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-filters/filters-overview)
- [建立篩選器](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-filters/create-filters)
- [註解概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/annotations/overview)
- [計算量度概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)
- [建立計算量度](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-workflow/cm-build-metrics)
- [計算量度函式](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-functions)
- [引導式分析概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/overview)
- [funnel檢視](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/funnel/funnel)
- [趨勢檢視](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/trends/usage)
- [保留檢視](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/retention/retention-rates)
- [主動式成長檢視](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/user-growth/active)
- [參與頻率檢視](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/trends/frequency)
- [發行影響檢視](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/impact/release)
- [Content Analytics](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/content-analytics/content-analytics)

### 第4階段：控制面板發佈

**應用程式功能：** CJA：儀表板和計分卡發佈

此階段會建立互動式儀表板（Workspace專案）和行動計分卡，為利害關係人提供KPI可見度。 控制面板透過摘要數字、趨勢線、劃分和註解，提供執行與營運的可見度。 行動計分卡透過[!DNL Adobe Analytics]儀表板行動應用程式提供一目瞭然的效能資料。

#### 決定點

在此階段中必須做出以下決策。

>[!NOTE]
>**決定：儀表板型別**
>
>這是否為案頭Workspace控制面板、行動計分卡或兩者？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| Workspace專案（案頭） | 分析師和行銷人員適用的詳細互動式儀表板 | 完整的視覺化功能；支援面板、表格和複雜版面 |
>| 行動計分卡 | 適用於行動裝置上的主管和利害關係人的概覽KPI | 僅限16個圖磚；摘要數字含趨勢走勢圖；需要行動應用程式 |
>| 兩者 | 組織需要詳細分析和執行層級的行動報告 | 個別的人工因素，但可共用相同的資料檢視和計算量度 |

>[!NOTE]
>**決定：共用模型**
>
>誰應該收到控制面板以及如何收到？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 與特定使用者共用 | 具有特定存取需求的受眾限制 | 最精細的控制；需要個別使用者管理 |
>| 與產品設定檔群組共用 | 與組織角色一致的團隊層級存取 | 有效率地在團隊內發佈；透過CJA產品設定檔管理 |
>| 排程電子郵件傳遞 | 未登入CJA的利害關係人週期性PDF/CSV報告 | 自動化傳送；最高頻率為每小時；PDF和CSV格式 |

>[!NOTE]
>**決定：註解可見度**
>
>是否應在控制面板趨勢線上為重要事件加上註解？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 是 — 建立註解 | 主要行銷活動、產品啟動、網站事件或季節性事件可能會解釋資料趨勢 | 註解會線上圖與計分卡趨勢中顯示為標籤；提供資料尖峰或下降的情境 |
>| 否 | 儀表板對象熟悉業務內容，且註解會增加雜亂 | 更簡單的視覺化簡報 |

#### 設定儀表板

**使用者介面導覽：**

- Workspace控制面板： CJA > Workspace >建立專案
- 行動計分卡：CJA >專案>建立>行動計分卡
- 共用： CJA > Workspace >共用>與Workspace使用者共用
- 排程傳送： 「CJA > Workspace >共用>排程專案」

主要設定詳細資料：

- 針對行動計分卡，建立圖磚，顯示具有摘要數字和走勢圖趨勢的單一量度
- 設定預設日期範圍和比較期間（例如，過去30天與上一個期間或月同比期間）
- 新增受眾範圍篩選器，讓高階主管在行動計分卡上切換
- 設定定期PDF或CSV報告的排程電子郵件傳遞
- 每個行動計分卡最多16個圖磚；每個Workspace專案最多15個面板
- 每個資料檢視的註解限製為100個

**Experience League檔案：**

- [建立行動計分卡](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/create-scorecard)
- [設定及組織計分卡](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/curate)
- [Adobe Analytics控制面板 — 執行指南](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/set-up-execs)
- [共用專案](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/share-projects)
- [排程專案](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/send-schedule-files)
- [摘要數字視覺效果](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/summary-number-change)
- [日期範圍](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/date-ranges/overview)

### 階段5：對象發佈（僅限選項C）

**應用程式函式：** CJA：對象發佈

此階段會設定CJA對象發佈，將分析發現的區段推送回AEP即時客戶設定檔，以便在RT-CDP目的地、AJO促銷活動或AJO歷程中進行下游啟用。

#### 決定點

在此階段中必須做出以下決策。

>[!NOTE]
>**決定：重新整理步調**
>
>對象會籍的重新整理頻率為何？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 一次性（快照） | 不需要持續重新整理的行銷活動特定對象 | 沒有進行中的處理；必須重新發佈以取得更新 |
>| 每4小時 | 近乎即時的啟用需求 | 處理成本較高；最適合對時間敏感的對象 |
>| 每日 | 標準行銷啟動步調 | 兼顧新鮮度和成本；最常見的選擇 |
>| 每週 | 穩定、緩慢變化的對象 | 最低限度的處理能力；適用於長期區段 |

>[!NOTE]
>**決定：身分名稱空間**
>
>CJA應使用哪個身分名稱空間來解析受眾成員？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| CRM ID | 組織的主要客戶識別碼 | 已知客戶比對的最佳精確度 |
>| ECID | 主要是Web/應用程式型對象 | 裝置範圍；可能無法解析為所有的設定檔記錄 |
>| 電子郵件（雜湊） | 電子郵件是啟用的通用識別碼 | 必須符合AEP身分設定中使用的名稱空間 |
>| 自訂名稱空間 | 整個組織使用的專有識別碼 | 必須在AEP Identity Service中設定 |

#### 設定對象發佈

**UI導覽：** CJA >元件>對象>發佈對象

主要設定詳細資料：

- 使用CJA篩選器定義對象條件（人員、工作階段或事件容器範圍）
- 選取資料檢視並篩選以發佈
- 設定身分名稱空間以解析AEP設定檔
- 根據啟動需求設定重新整理步調
- 在CJA受眾清單（「元件>受眾>狀態」欄）中監視發佈狀態
- 驗證對象是否出現在AEP對象入口網站中（「對象>瀏覽>依來源「CJA」篩選）
- 每個CJA客戶最多可發佈75個對象（所有沙箱）
- 大型資料集的初始對象評估可能最多需要24小時

**Experience League檔案：**

- [受眾概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/audiences-overview)
- [建立及發佈對象](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/publish)
- [管理對象](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/manage)
- [Audience Portal概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-portal)

## 實施考量

本節涵蓋此使用案例模式的護欄、常見陷阱、最佳實務和取捨決定。

### 護欄和限制

以下護欄和限制適用於此實作。

- **連線限制：**&#x200B;每個組織的連線數目上限受到CJA SKU權益的限制。 單一連線只能包含來自一個AEP沙箱的資料集。 — [CJA護欄](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-admin/guardrails)
- **資料檢視限制：**&#x200B;每個資料檢視最多5,000個維度和5,000個量度。 每個資料檢視最多100個衍生欄位，包含最多5個層級的巢狀函式。
- **Workspace限制：**&#x200B;每個專案最多40個面板。 自由表格支援最多10個深入劃分維度。 每個報告請求最多50,000列。
- **計分卡限制：**&#x200B;每個行動計分卡最多16個圖磚。
- **串流延遲：**&#x200B;一般可在AEP擷取後90分鐘內於CJA中使用串流資料。
- **對象發佈限制：**&#x200B;每個CJA客戶最多可發佈75個對象。 最低重新整理步調是每4小時一次。
- **引導式分析限制：** Funnel分析支援最多15個步驟。 區段比較同時支援最多3個區段。

### 常見陷阱

實施此模式時，請注意下列常見問題。

- **跨資料集的人員ID不相符：**&#x200B;連線中的所有資料集必須使用一致的人員ID欄位進行跨資料集分析。 不相符的人員ID會導致客戶檢視不完整，同一個人員會出現在多個人身上。 在建立連線之前，請先驗證人員ID是否一致。

- **回填花費意外太長：**&#x200B;含有數十億筆記錄的大型資料集可能需要幾天的時間才能回填。 在實施時間表期間針對此進行規劃，並提早開始回填。 在連線詳細資料檢視中監視進度。

- **大多數維度值顯示「未指定」的資料檢視：**&#x200B;來源資料中可能會稀疏填入對應的結構描述欄位。 在假設發生設定錯誤之前，請檢查來源資料集的資料品質。 請考慮使用衍生欄位來處理null值。

- **工作階段計數似乎不正確：**&#x200B;工作階段逾時設定會大幅影響工作階段範圍的量度。 極短的逾時會產生更多工作階段；極長的逾時則會產生更少的工作階段。 新的工作階段開始事件也可能意外分割工作階段。 根據已知的使用者行為模式檢閱和測試工作階段設定。

- **歸因模型未如預期套用：**&#x200B;歸因模型僅適用於量度，不適用於維度。 確認回溯時段已針對業務週期適當地設定。 短回顧期間可能會錯過funnel早期的接觸點。

- **傳回零或未預期值的運算量度：**&#x200B;請確認公式中所參考的基本量度在所選日期範圍的目標資料檢視中有資料。 檢查比率量度中是否除以零。 擷取量度定義並驗證公式結構。

- **對象發佈失敗（選項C）：** CJA連線必須具有可解析為AEP身分名稱空間的有效人員ID。 驗證身分名稱空間設定，以及目標沙箱中已啟用AEP即時客戶設定檔。

### 最佳實務

請遵循這些最佳實務以成功實作。

- **從單一完整連線開始：**&#x200B;建立一個連線，其中包含所有相關的資料集，然後針對不同的分析觀點建立多個資料檢視。 如此可避免連線數量激增並簡化管理。

- **使用衍生欄位進行行銷管道分類：**&#x200B;不要依賴原始追蹤程式碼，而是使用「案例時間」邏輯建立衍生欄位，將流量分類至行銷管道。 這可確保跨所有分析的一致管道報告。

- **建立量度字典：**&#x200B;記錄所有計算的量度及其公式、預期用途和預期值範圍。 與分析團隊共用此字典以確保跨專案一致的量度使用情況。

- **為您的對象設計資料檢視：**&#x200B;為不同的利害關係人群組建立個別的資料檢視 — 具有以行銷活動為重點的維度和量度的行銷資料檢視，以及具有功能和參與維度的產品資料檢視。 這簡化了每個使用者群組的元件清單。

- **為一切加上註解：**&#x200B;為行銷活動啟動、網站變更、技術事件、季節性事件，以及任何可能說明資料趨勢的事件建立註解。 幾個月後檢閱儀表板時，註解可提供重要的內容。

- **針對手動計算測試運算量度：**&#x200B;在依賴儀表板的運算量度之前，請以運算量度及其基本元件並排執行報表。 驗證計算值與手動計算相符。

- **策略性地使用篩選器：**&#x200B;針對常見的分段模式（新區段與回訪區段、行動裝置與案頭區段、依地理位置區分等）建立可重複使用的篩選器。 將這些專案套用為面板層級篩選器，而非將其內嵌於每個自由表格。

- **定期監視連線狀況：**&#x200B;檢查連線詳細資料檢視是否有略過的記錄、失敗的批次和串流延遲。 連線層級的資料品質問題會影響所有下游分析。

### 權衡決定

規劃實施時，請考慮下列取捨。

>[!NOTE]
>**取捨：分析深度與insight上線時間的比較**
>
>選項B (Customer Journey Analytics)提供最深入的跨管道分析，但需要在連線設定、資料檢視設計和衍生欄位建立方面進行大量的前期投資。 選項D （引導式分析）透過結構化的工作流程，可加快前往insight的時間，但提供的分析彈性較少。
>
>- **選項B偏好：**&#x200B;全面瞭解、複雜的多管道分析、歸因模型、自訂KPI開發
>- **選項D偏好：**&#x200B;速度、非分析人員使用者的協助工具、結構化產品體驗問題
>- **建議：**&#x200B;從選項D開始，並行建置選項B基礎結構時可立即進行產品深入分析。 許多組織會針對不同的團隊同時執行這兩者。

>[!NOTE]
>**取捨：回填完整性與連線整備程度**
>
>匯入所有歷史資料可為逐年比較和長期趨勢分析提供最大分析深度，但大型資料集的回填作業可能需要數天時間。 將回填限制在最近時段，連線可更快地準備就緒，但會限制歷史分析。
>
>- **所有資料都偏好：**&#x200B;長期趨勢分析、逐年比較、具有長期記錄的同類群組分析
>- **有限的回填喜好：**&#x200B;連線準備速度更快、進入第一個儀表板的時間更短、儲存裝置最佳化
>- **建議：**&#x200B;針對支援策略分析的生產連線回填所有資料。 將有限的回填用於開發連線和概念證明實施。

>[!NOTE]
>**取捨：單一完整資料檢視與多個重點資料檢視的比較**
>
>包含所有維度和量度的單一資料檢視可提供統一的分析工作區，但元件清單會讓使用者不知所措。 多個重點資料檢視（每個團隊或使用案例一個）可簡化元件體驗，但需要維護多個設定。
>
>- **單一資料檢視更適合：**&#x200B;統一分析、跨網域劃分、更簡單的管理
>- **多個資料檢視有助於：**&#x200B;更乾淨的元件清單、特定團隊的術語、每個使用案例的不同工作階段定義
>- **建議：**&#x200B;從單一主要資料檢視開始，如果元件清單複雜性成為採用障礙，則建立其他重點資料檢視。 所有資料檢視都可以參照相同的連線。

>[!NOTE]
>**取捨：即時串流與僅批次擷取**
>
>在CJA連線上啟用串流功能可提供近乎即時的資料（AEP擷取後約90分鐘內），但會持續處理更多資料。 僅限批次的擷取會定期處理資料，且可能會造成延遲。
>
>- **串流優惠：**&#x200B;即時報告、監控作用中行銷活動、近乎即時儀表板
>- **僅批次優惠：**&#x200B;較簡單的設定、可預測的處理期間，足以每週或每月報告
>- **建議：**&#x200B;為生產連線啟用串流。 相較於作用中行銷活動監控和操作控制面板的及時資料價值，增量處理成本是最低的。

## 相關文件

下列資源提供此使用案例模式的其他資訊。

### [!DNL Customer Journey Analytics] — 快速入門

- [CJA概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [CJA護欄](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-admin/guardrails)

### 連線

- [連線總覽](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/overview)
- [建立或編輯連線](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/create-connection)
- [管理連線](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/manage-connections)

### 資料視圖

- [資料檢視總覽](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/data-views)
- [建立或編輯資料檢視](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [元件設定概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/overview)
- [持續性設定](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/persistence)
- [歸因設定](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/attribution)
- [格式設定](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/format)
- [量度重複資料刪除](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/metric-deduplication)
- [包含/排除值](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/include-exclude-values)
- [工作階段設定](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/session-settings)
- [衍生欄位](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/derived-fields)

### Workspace &amp; analysis

- [Workspace概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [建立專案](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/build-workspace-project/create-projects)
- [自由格式表格](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/freeform-table/freeform-table)
- [流量視覺效果](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/flow/flow)
- [流失視覺效果](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/fallout/fallout-flow)
- [同類群組表格](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/cohort-table/cohort-analysis)
- [歸因面板](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/panels/attribution)
- [劃分維度](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/components/dimensions/t-breakdown-fa)
- [共用專案](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/share-projects)
- [排程專案](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/send-schedule-files)
- [匯出概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/export/export-cloud)

### 引導式分析

- [引導式分析概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/overview)
- [funnel檢視](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/funnel/funnel)
- [趨勢檢視](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/trends/usage)
- [參與頻率檢視](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/trends/frequency)
- [保留檢視](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/retention/retention-rates)
- [主動式成長檢視](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/user-growth/active)
- [發行影響檢視](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/impact/release)
- [首次使用影響檢視](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/impact/first-use)
- [時間表檢視](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/streams/timeline)

### 元件

- [篩選器概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-filters/filters-overview)
- [建立篩選器](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-filters/create-filters)
- [計算量度概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)
- [建立計算量度](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-workflow/cm-build-metrics)
- [計算量度函式](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-functions)
- [註解概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/annotations/overview)
- [日期範圍](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/date-ranges/overview)
- [量度元件](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/apply-create-metrics)

### 對象發佈

- [受眾概述](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/audiences-overview)
- [建立及發佈對象](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/publish)
- [管理對象](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/manage)

### 內容分析

- [Content Analytics](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/content-analytics/content-analytics)
- [Content Analytics設定](https://experienceleague.adobe.com/en/docs/analytics-platform/using/content-analytics/config/configuration)

### 控制面板和計分卡

- [建立行動計分卡](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/create-scorecard)
- [設定及組織計分卡](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/curate)
- [Adobe Analytics控制面板 — 執行指南](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/set-up-execs)
- [摘要數字視覺效果](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/summary-number-change)

### AEP基礎

- [資料集總覽](https://experienceleague.adobe.com/en/docs/experience-platform/catalog/datasets/overview)
- [XDM系統概覽](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [來源概觀](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)
- [Identity Service總覽](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Audience Portal概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-portal)

### AJO報表整合

- [AJO + CJA整合指南](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [行銷活動電子郵件報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/reporting/campaign-global-report-cja-email)
- [歷程電子郵件報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/reporting/journey-global-report-cja-email)

### 教學課程與指南

- [結構描述組合基本面](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)
- [網頁SDK概觀](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [設定資料串流](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
