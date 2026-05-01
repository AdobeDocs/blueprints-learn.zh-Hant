---
source-git-commit: 7511cc0e5c099d5d3ee1275a374cd9ffdc972335
workflow-type: tm+mt
source-wordcount: '3505'
ht-degree: 6%

---
# 藍圖稽核與建議

此稽核會將[評估規則](rubric.md)套用至下的每個檔案
[TOC.md](../help/blueprints/TOC.md) （第76-133行）的「架構圖表和藍圖」區段，以及
建議每個Blueprint是否應該成為使用案例&#x200B;**模式**，一種架構
**圖表**，兩者皆為（**分割**），或標籤為現有模式的&#x200B;**重複**。

這僅是稽核 — 未移動任何內容。 移轉待處理專案（批次A-D動作）
一經審查，將作為獨立的後續計畫起草。

## 摘要

**已稽核的檔案總數：** 43

| 建議 | 計數 | 動作 |
| --- | --- | --- |
| 圖樣 | 8 | 編寫新的使用案例模式；將原始內容修剪為圖表。 |
| 複製 | 9 | 現有模式涵蓋範圍；將Blueprint簡化為圖表和交叉連結。 |
| 分割 | 2 | 擷取模式內容；將原始內容簡化為圖表；將兩者交叉連結。 |
| 圖表 | 16 | 保留為架構圖；如有需要，可修剪敘述。 |
| 導覽 | 8 | 區段登陸頁面（overview.md或僅限連結）；移轉登陸後重新造訪。 |

### 控制組校準

所有6個`experience-platform/`檔案的評分模式=0，圖表=3→一致的&#x200B;**圖表**。
已校準規則；其他子區域的結果可視為已評分。

### 新使用案例模式類別：B2B啟用與行銷

新類別`use-case-patterns/b2b/` (顯示標籤&#x200B;**B2B啟用與行銷**，目錄錨點
建議的`{#b2b-patterns}`)將容納所有B2B特定模式。 標籤會映象現有的
[TOC.md](../help/blueprints/TOC.md)的架構圖表區域中的「B2B啟動與行銷」子區段，
讓讀者看到兩個區段之間的視覺對稱。

完全填入後，類別將包含&#x200B;**7模式**：

| 來源 | 動作 | 目標路徑 |
| --- | --- | --- |
| `use-case-patterns/audience-building-activation/b2b-audience-activation.md` | **重新定位**&#x200B;現有模式 | `use-case-patterns/b2b/account-audience-activation.md` |
| `use-case-patterns/campaign-management-orchestration/buying-group-based-marketing.md` | **重新定位**&#x200B;現有模式 | `use-case-patterns/b2b/buying-group-marketing.md` |
| `use-case-patterns/analysis/b2b-analytics.md` | **重新定位**&#x200B;現有模式 | `use-case-patterns/b2b/account-analytics.md` |
| `b2b/b2b-journeys-with-marketo.md` | **編寫新的** （稽核模式列） | `use-case-patterns/b2b/marketo-data-journeys.md` |
| `b2b/ajo-b2b-paid-media-controller.md` | **編寫新的** （稽核模式列） | `use-case-patterns/b2b/paid-media-orchestration.md` |
| `b2b/marketo-engage-and-workfront-integration-blueprint/intake-and-create.md` | **作者新** | `use-case-patterns/b2b/campaign-intake-and-creation.md` |
| `b2b/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint.md` | **作者新** | `use-case-patterns/b2b/campaign-review-and-approval.md` |

> **初始轉換狀態 — 寫入器協調閘道。** 現有的「B2B啟用與行銷」> [TOC.md](../help/blueprints/TOC.md) （第95-106行） **之架構圖表區域中的子區段保持不變> 轉換期間**。 每個藍圖轉換和現有圖樣重新定位都需要> 移轉內容之前，請先從擁有的寫入者登出。 新的`b2b/`使用案例模式> 移轉逐頁進行時，區段與現有Blueprint區段同時存在，具有> 兩者之間的交叉連結。

當重新定位與新圖樣都著陸時：

- [TOC.md](../help/blueprints/TOC.md) `Use Case Patterns`區段將獲得 `B2B Activation & Marketing{#b2b-patterns}`
子區段（置入方式待定，與編寫器搭配使用）。
- [use-case-patterns/overview.md](../help/blueprints/use-case-patterns/overview.md)將取得B2B類別表格。
- 重新定位的模式將會從`audience-building-activation`中移除，
  `campaign-management-orchestration`和`analysis`總覽表；保留其舊URL
透過[migration-redirects.csv](migration-redirects.csv)中的重新導向連線。

### 已識別的重複專案(9)

藍圖範圍已由現有使用案例模式涵蓋。 移轉動作為
**簡化為架構圖表+交叉連結**。

| 藍圖 | 現有圖樣 |
| --- | --- |
| `audience-activation/advertising-activation.md` | `use-case-patterns/audience-building-activation/audience-activation-to-destinations.md` |
| `audience-activation/segment-match.md` | `use-case-patterns/audience-building-activation/audience-collaboration-segment-match.md` |
| `b2b/b2bactivation.md` | `use-case-patterns/audience-building-activation/b2b-audience-activation.md` |
| `b2b/b2b-buying-group-journeys.md` | `use-case-patterns/campaign-management-orchestration/buying-group-based-marketing.md` |
| `customer-journey-analytics/b2b-cja.md` | `use-case-patterns/analysis/b2b-analytics.md` |
| `customer-journeys/journey-optimizer/journey-optimizer-journeys.md` | `use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md` |
| `customer-journeys/journey-optimizer/journey-optimizer-campaigns.md` | `use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md` |
| `customer-journeys/decision-management/decision-management-edge.md` | `use-case-patterns/personalization/offer-decisioning.md` |
| `customer-journeys/decision-management/decision-management-hub.md` | `use-case-patterns/personalization/offer-decisioning.md` |

> 注意： `decision-management-edge.md`和`decision-management-hub.md`都對應到相同專案> 現有`offer-decisioning.md`模式。 考慮將兩個Blueprint合併為單一> 部署 — 選項圖表，或使用edge-vs-hub部署來增強現有模式> 變體。 標幟以供寫入者稽核。

### 要編寫的模式（8個新的+ 2個來自分割=共10個）

| Source Blueprint | 建議的類別 | 建議的模式標題 |
| --- | --- | --- |
| `audience-activation/customer-activity.md` | audience-building-activation | 支援與銷售人員的即時設定檔查詢 |
| `audience-activation/data-science.md` | audience-building-activation | 個人檔案擴充的資料科學模型擷取 |
| `audience-activation/real-time-lookup.md` | 個人化 | 適用於Web/行動Personalization的Edge設定檔存取 |
| `b2b/b2b-journeys-with-marketo.md` | **b2b** （新） | 透過Marketo資料整合的B2B帳戶歷程 |
| `b2b/ajo-b2b-paid-media-controller.md` | **b2b** （新） | 透過Waterfall分割路徑邏輯的B2B付費媒體協調 |
| `b2b/marketo-engage-and-workfront-integration-blueprint/intake-and-create.md` | **b2b** （新） | Campaign要求接收和自動化程式建立 |
| `b2b/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint.md` | **b2b** （新） | 行銷活動資產檢閱與核准工作流程 |
| `customer-journeys/campaign-v8/campaign-v8-overview.md` | campaign-management-orchestration | Campaign v8批次協調流程和異動訊息 |
| `audience-activation/rtcdp-target.md` *（分割）* | 個人化 | 使用Adobe Target即時共用對象 |
| `customer-journeys/journey-optimizer/3rd-party-messaging.md` *（分割）* | campaign-management-orchestration | 第三方傳訊與Journey Optimizer整合 |

### 建議的新模式類別

- **`b2b/`** （顯示標籤&#x200B;**B2B啟用與行銷**） — 請參閱上方的專屬區段。 此
Marketo + Workfront模式(`intake-and-create`， `review-and-approve-blueprint`)已路由
此處而非個別的`marketing-resource-management`類別，因為它們代表
B2B行銷運作實務。 新類別總共彙總7個模式：3個已重新定位
以及從Blueprint新撰寫的4個類別。

### 移轉重新導向

此移轉引進的每個URL變更都會在標準中新增一列
存放庫根目錄上的[`redirects.csv`](../redirects.csv) （格式： `source,dest`）。 已確認
重新導向會分段至[migration-redirects.csv](migration-redirects.csv)，並合併至
標準檔案，因為每個對應的移動實際上都會發生。

**已確認（3個專案，已暫存）：**&#x200B;現有的模式重新定位到`b2b/`。 另請參閱
[migration-redirects.csv](migration-redirects.csv)。

**擱置中 — 當Blueprint為&#x200B;*已刪除*時新增（縮減為現成圖表時不會新增）：**，如果
模式、分割或複製列的藍圖稍後會完全移除，請從新增重新導向
標準模式URL的Blueprint URL。 預設移轉方法（簡化圖表）
讓Blueprint URL保持作用中，**不需要**&#x200B;這些重新導向。 以下列出
如果任何Blueprint已完全淘汰，則為完整性：

```
# Pattern blueprints — if deleted, redirect to the new pattern URL
# (slugs are placeholders; finalize when each pattern is authored)
/en/docs/blueprints-learn/architecture/architecture-diagrams/audience-activation/known-customer-audience-activation/customer-activity → use-case-patterns/audience-building-activation/<new-pattern-slug>
/en/docs/blueprints-learn/architecture/architecture-diagrams/audience-activation/known-customer-audience-activation/data-science → use-case-patterns/audience-building-activation/<new-pattern-slug>
/en/docs/blueprints-learn/architecture/architecture-diagrams/audience-activation/known-customer-audience-activation/real-time-lookup → use-case-patterns/personalization-patterns/<new-pattern-slug>
/en/docs/blueprints-learn/architecture/architecture-diagrams/b2b-activation/b2b-journeys-with-marketo → use-case-patterns/b2b-patterns/marketo-data-journeys
/en/docs/blueprints-learn/architecture/architecture-diagrams/b2b-activation/ajo-b2b-paid-media-controller → use-case-patterns/b2b-patterns/paid-media-orchestration
/en/docs/blueprints-learn/architecture/architecture-diagrams/b2b-activation/marketo-engage-and-workfront-integration-blueprint/intake-and-create → use-case-patterns/b2b-patterns/campaign-intake-and-creation
/en/docs/blueprints-learn/architecture/architecture-diagrams/b2b-activation/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint → use-case-patterns/b2b-patterns/campaign-review-and-approval
/en/docs/blueprints-learn/architecture/architecture-diagrams/customer-journeys/campaign-v8/campaign-v8-overview → use-case-patterns/campaign-orchestration-patterns/<new-pattern-slug>

# Duplicate blueprints — if deleted, redirect to the existing pattern URL
/en/docs/blueprints-learn/architecture/architecture-diagrams/audience-activation/known-customer-audience-activation/advertising-activation → use-case-patterns/audience-building-activation/audience-activation-to-destinations
/en/docs/blueprints-learn/architecture/architecture-diagrams/audience-activation/known-customer-audience-activation/segment-match → use-case-patterns/audience-building-activation/audience-collaboration-segment-match
/en/docs/blueprints-learn/architecture/architecture-diagrams/b2b-activation/b2bactivation → use-case-patterns/b2b-patterns/account-audience-activation  (after b2b/ relocation)
/en/docs/blueprints-learn/architecture/architecture-diagrams/b2b-activation/b2b-buying-group-journeys → use-case-patterns/b2b-patterns/buying-group-marketing  (after b2b/ relocation)
/en/docs/blueprints-learn/architecture/architecture-diagrams/customer-journey-analytics/b2b-cja → use-case-patterns/b2b-patterns/account-analytics  (after b2b/ relocation)
/en/docs/blueprints-learn/architecture/architecture-diagrams/customer-journeys/journey-optimizer/journey-optimizer-journeys → use-case-patterns/campaign-orchestration-patterns/event-triggered-messaging
/en/docs/blueprints-learn/architecture/architecture-diagrams/customer-journeys/journey-optimizer/journey-optimizer-campaigns → use-case-patterns/campaign-orchestration-patterns/batch-outbound-message-activation
/en/docs/blueprints-learn/architecture/architecture-diagrams/customer-journeys/decision-management/decision-management-edge → use-case-patterns/personalization-patterns/offer-decisioning
/en/docs/blueprints-learn/architecture/architecture-diagrams/customer-journeys/decision-management/decision-management-hub → use-case-patterns/personalization-patterns/offer-decisioning

# Optional one-off — if customer-journey-analytics/analysis.md is relocated to experience-platform/
/en/docs/blueprints-learn/architecture/architecture-diagrams/customer-journey-analytics/analysis → architecture-diagrams/architecture-overview/analysis
```

將以上任何專案轉換為作用中重新導向列時，請以逗號分隔格式 `source,dest`
具有完整`/en/docs/...`個路徑（無`.html`尾碼），符合中的現有模式
[`redirects.csv`](../redirects.csv).

### 重新導向建立原則（永續性規則）

請遵循下列每個移轉步驟中的規則：

1. **已移動或重新命名檔案**，→從舊URL重新導向至新URL。
2. **檔案已刪除** （藍圖已取代；未保留圖表）→從已刪除的URL新增重新導向至
標準取代URL。
3. **檔案已就地簡化** （URL未變更）→沒有重新導向。
4. **已重新命名TOC錨點** （例如，區段標題變更），→為每個頁面新增重新導向
這個錨點，因為URL會變更。

### 為作者開啟問題

1. **決策管理邊緣與集線器**&#x200B;的比較 — 兩者都對應到相同的現有 `offer-decisioning.md`
模式。 使用部署變體合併為單一圖表，或視為獨立的
兩個圖表會交叉連結至相同模式嗎？
2. **Journey Optimizer歷程與事件觸發訊息** — 代理程式已標幟此重複專案
分類不確定。 在減少Blueprint之前，請驗證範圍是否一致。
3. **`customer-journey-analytics/analysis.md`** — 內容實際上與Experience Platform有關
查詢服務，而非CJA。 請考慮重新放置到`experience-platform/`資料夾。 (一個重新導向
若是則會新增 — 請參閱[migration-redirects.csv](migration-redirects.csv)。)
4. **Campaign v7 （已棄用）** — 三個已棄用的v7檔案被分類為圖表/
導覽。 確認是否完全移轉、保持原樣或完全從目錄中移除。
5. **`customer-success-stories.md`** — 僅連結參考頁面（不是`overview.md`）。
已分類為導覽。 確認或重新分類。
6. **B2B區段TOC錨點** — 建議的`{#b2b-patterns}`。 其他模式子區段使用
   `-patterns`尾碼(`{#personalization-patterns}`， `{#analysis-patterns}`，
   `{#campaign-orchestration-patterns}`). 在編寫重新導向之前，請確認或挑選另一個錨點。
7. 在TOC **中的** B2B區段位置 — 建議位於`+ Use Case Patterns{#use-case-patterns}`下。
兄弟姐妹間的順序(對象建立和啟用、Personalization、行銷活動管理
與協調、分析、B2B啟動與行銷、對話體驗)是
寫入者的呼叫。
8. **擁有寫入者協調** — 每個藍圖轉換和現有模式重新定位
內容移動前需要寫入者簽核。 稽核表格是目標狀態，而非
排序計畫；排序會在協調後的後續移轉計畫中進行。

## 稽核表

| 路徑 | 標題 | 摘要 | dominant_type | 推薦 | proposed_pattern_category | proposed_pattern_title | proposed_diagram_title | duplicate_of | pattern_score | diagram_score | 附註 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| help/blueprints/experience-platform/experience-cloud.md | Adobe Experience Cloud 架構圖 | 顯示Experience Cloud應用程式和服務如何在AEP基礎上整合的企業架構。 | 圖表 | 圖表 |  |  | Experience Cloud架構概述 |  | 0 | 3 | 覆寫3 （無業務目標）。 三個補充圖表（市場結構、整合、企業環境）。 控制組：如預期。 |
| help/blueprints/experience-platform/platform-applications.md | Adobe Experience Platform和應用程式架構圖 | 顯示Experience Platform與其他Experience Cloud應用程式關聯的架構圖。 | 圖表 | 圖表 |  |  | AEP與應用程式架構 |  | 0 | 3 | 覆寫3。 兩種概觀/詳細圖表；無實施指引。 整合學習檔案的交叉連結。 控制組：如預期。 |
| help/blueprints/experience-platform/platform-data-flow.md | Adobe Experience Platform 資料流程架構圖 | 資料流程架構圖顯示Experience Platform的擷取和輸出路徑。 | 圖表 | 圖表 |  |  | AEP資料流程架構 |  | 0 | 3 | 覆寫3。 參考資料收集檔案的單一資料流程圖。 純粹的架構成品。 控制組：如預期。 |
| help/blueprints/experience-platform/guardrails.md | Experience Platform 和應用程式護欄 | AEP和應用程式的系統限制、效能預期和延遲護欄。 | 圖表 | 圖表 |  |  | AEP和應用程式護欄和延遲 |  | 0 | 3 | 覆寫3。 延遲圖表加上參考表格。 架構導向（邊緣與中樞）。 限制檔案，而非操作說明。 控制組：如預期。 |
| help/blueprints/experience-platform/deployment/websdk.md | Experience Platform Web SDK與Edge Network架構圖 | 顯示資料收集流程的網頁SDK和Edge Network部署架構。 | 圖表 | 圖表 |  |  | Web SDK和Edge Network部署 |  | 0 | 3 | 覆寫3。 兩個圖表（流程和順序）。 參考教學課程，但不提供檔案內的操作說明。 以架構者為中心。 控制組：如預期。 |
| help/blueprints/experience-platform/deployment/appsdk.md | 應用程式專用 SDK 部署架構圖 | 應用程式特定的SDK整合路徑和資料收集架構圖。 | 圖表 | 圖表 |  |  | 應用程式特定的SDK部署 |  | 0 | 3 | 覆寫3。 具有最少敘述的單一部署圖表。 純粹的架構成品。 控制組：如預期。 |
| help/blueprints/audience-activation/advertising-activation.md | Audience Activation至Social和Advertising目的地 | 透過身分設定和目的地設定，透過RTCDP啟用Facebook和Google廣告網路的受眾。 | 圖樣 | 複製 |  |  |  | help/blueprints/use-case-patterns/audience-building-activation/audience-activation-to-destinations.md | 4 | 1 | 現有模式涵蓋此範圍。 重複覆寫。 動作：簡化為純圖表和交叉連結。 |
| help/blueprints/audience-activation/audience-manager.md | 以裝置為基礎 — 使用Audience Manager鎖定匿名受眾 | 使用Audience Manager或RTCDP進行跨頻道以裝置為基礎的鎖定目標的匿名受眾啟用。 | 圖表 | 圖表 |  |  | 匿名裝置型對象目標定位 |  | 1 | 2 | 最低限度的敘述。 呈現架構圖，顯示系統拓朴。 無業務目標框架；部署SDK和中樞/邊緣概念。 |
| help/blueprints/audience-activation/customer-activity.md | 支援與銷售案例的即時設定檔存取 | 透過設定檔查詢API啟用支援和銷售代理程式即時客戶內容。 | 圖樣 | 圖樣 | audience-building-activation | 支援與銷售人員的即時設定檔查詢 |  |  | 3 | 1 | 框架業務結果（代理內容）。 有先決條件檢查清單；實作步驟>30行。 獨特使用案例：中心設定檔存取（而非邊緣個人化）。 與現有個人化模式不同。 |
| help/blueprints/audience-activation/data-science.md | 自訂 Profile Enrichment 藍圖的資料科學 | 將機器學習模型分數擷取至RTCDP，以豐富個人化和細分的設定檔。 | 圖樣 | 圖樣 | audience-building-activation | 個人檔案擴充的資料科學模型擷取 |  |  | 3 | 1 | 框架業務結果（個人化的擴充）。 具有使用案例和考量事項；實施考量事項>30行。 著重於資料科學工作流程，而非傳訊/啟用。 |
| help/blueprints/audience-activation/enterprise-destinations.md | 對象與個人資料啟用至企業目標 | 針對銷售、支援和分析，將雲端儲存空間和企業應用程式的資料流或批次設定檔和對象變更串流。 | 圖表 | 圖表 |  |  | Enterprise Audience and Profile Activation |  | 1 | 2 | 沒有業務目標框架。 稀疏實作指引。 雲端儲存空間/企業應用程式的架構圖+系統拓撲。 以視覺為主導。 |
| help/blueprints/audience-activation/real-time-lookup.md | 適用於Web和Mobile Personalization的即時Edge設定檔存取 | 存取邊緣的統一設定檔（以毫秒為單位），以進行即時網頁和行動個人化。 | 圖樣 | 圖樣 | 個人化 | 適用於Web/行動Personalization的Edge設定檔存取 |  |  | 5 | 2 | 強大的業務框架（低延遲的個人化）。 兩種實施模式（Web SDK與Edge API）。 廣泛的必要條件和步驟（30行以上）。 隱含的KPI （延遲、輸送量）。 |
| help/blueprints/audience-activation/rtcdp-target.md | 已知客戶Personalization與Target | 與Adobe Target共用RTCDP對象和設定檔，以進行已知訪客的網頁和行動個人化。 | 混合 | 分割 | 個人化 | 使用Adobe Target即時共用對象 | Target整合架構 | help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md | 3 | 2 | 與現有已知訪客模式重疊，但範圍較窄（僅限Target）。 三種整合模式。 架構圖+考量邊緣部署。 將內容+圖表圖案化→「分割」。 |
| help/blueprints/audience-activation/segment-match.md | 有區段比對的對象Collaboration | 透過具有隱私權控制的區段比對來啟用安全的合作夥伴受眾共同作業。 | 圖樣 | 複製 |  |  |  | help/blueprints/use-case-patterns/audience-building-activation/audience-collaboration-segment-match.md | 4 | 1 | 現有模式完全涵蓋這一點。 重複覆寫。 要在圖表中保留的獨特內容：詳細的RBAC/同意/治理設定以及程式化的廣告工作流程。 |
| help/blueprints/b2b/overview.md | B2B Analytics、啟用和行銷藍圖 | 導覽頁面列出B2B分析、對象啟用、購買群組、Marketo和Workfront藍圖。 | 導覽 | 導覽 |  |  |  |  |  |  | 覆寫1：名為overview.md的檔案。 已從移轉中排除。 |
| help/blueprints/b2b/b2bactivation.md | B2B 對象和個人資料啟用藍圖 | 使用帳戶和設定檔資料，跨網路、電子郵件和廣告頻道啟用以帳戶為基礎的B2B受眾。 | 圖樣 | 複製 |  |  |  | help/blueprints/use-case-patterns/audience-building-activation/b2b-audience-activation.md | 3 | 1 | 覆寫2：存在對等模式。 Blueprint是以架構為中心的子集較窄。 |
| help/blueprints/b2b/b2b-account-activation.md | Advertising目的地和檔案目的地的B2B帳戶啟用 | 透過LinkedIn及使用帳戶對象建立和啟用的雲端儲存目的地來目標B2B帳戶。 | 圖表 | 圖表 |  |  | B2B帳戶Audience Activation |  | 1 | 2 | 最低限度的業務框架、無KPI、最低限度的敘述。 呈現架構圖；說明LinkedIn/雲端儲存拓撲。 以圖表形式保留。 |
| help/blueprints/b2b/b2b-buying-group-journeys.md | 購買群組式行銷和歷程管理Blueprint | 設計客戶歷程，讓潛在客戶有資格購買具有已定義角色和解決方案興趣的群組。 | 圖樣 | 複製 |  |  |  | help/blueprints/use-case-patterns/campaign-management-orchestration/buying-group-based-marketing.md | 5 | 2 | 覆寫2：存在對等模式。 Blueprint有豐富的模式內容，但現有模式更全面。 |
| help/blueprints/b2b/b2b-journeys-with-marketo.md | 使用Marketo資料藍圖的B2B歷程 | 使用Marketo資料部署Journey Optimizer B2B edition，以協調購買團體歷程和帳戶參與。 | 圖樣 | 圖樣 | b2b | 透過Marketo資料整合的B2B帳戶歷程 |  |  | 4 | 1 | 強大的業務框架。 列出KPI；多個實作選項；廣泛的考量因素（>30行）。 透過Marketo資料整合深度（XDM設定、身分拼接、欄位封鎖）與現有模式不同。 路由至新的b2b/類別。 |
| help/blueprints/b2b/ajo-b2b-paid-media-controller.md | AJO B2B — 帳戶Journey Orchestration — 付費媒體控制者 | 使用Waterfall邏輯來協調B2B付費媒體行銷活動，將帳戶指派給行銷活動並啟用至目的地。 | 圖樣 | 圖樣 | b2b | 透過Waterfall分割路徑邏輯的B2B付費媒體協調 |  |  | 4 | 2 | 強大的業務框架。 明確KPI；多個實作選項；先決條件；>30行敘述。 不同於現有的購買群組模式（專注於付費媒體優先順序，而非培養）。 路由至新的b2b/類別。 |
| help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/overview.md | Marketo Engage與Workfront整合藍圖概觀 | 透過Fusion使用Marketo Engage和Workfront進行行銷活動規劃以自動化執行的概觀。 | 導覽 | 導覽 |  |  |  |  |  |  | 覆寫1：名為overview.md的檔案。 已從移轉中排除。 |
| help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/intake-and-create.md | 擷取並建立藍圖 | 使用Workfront表單和Marketo Engage方案範本自動化B2B行銷活動請求擷取以建立。 | 圖樣 | 圖樣 | b2b | Campaign要求接收和自動化程式建立 |  |  | 4 | 1 | 以行銷活動速度打造強大的業務框架。 隱含KPI （錯誤/減少重工）；工作流程步驟>30行；準備檢查清單。 路由至新的b2b/類別（Marketo+Workfront操作主要是B2B）。 |
| help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint.md | 檢閱和核准Blueprint | 使用Fusion自動化整合Workfront校訂和核准工作流程與Marketo Engage電子郵件資產。 | 圖樣 | 圖樣 | b2b | 行銷活動資產檢閱與核准工作流程 |  |  | 3 | 2 | 強大的業務框架，符合合規性和準確性；隱含的KPI （核准速度）；敘述>30行；工作流程規劃區段。 路由至新的b2b/類別。 |
| help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/customer-success-stories.md | 客戶成功案例 | 客戶個案研究和網路研討會的連結，展示Marketo和Workfront整合的成果。 | 導覽 | 導覽 |  |  |  |  |  |  | 最小內容（6個超連結）。 沒有業務框架、KPI、架構或敘述。 視為導覽。 寫入器應確認。 |
| help/blueprints/customer-journey-analytics/overview.md | Customer Journey Analytics藍圖 | 統一及分析來自各種管道的客戶資料和行為，以建立歷程型檢視。 | 導覽 | 導覽 |  |  |  |  |  |  | 覆寫1： overview.md。 TOC樣式登陸頁面。 已從移轉中排除。 |
| help/blueprints/customer-journey-analytics/b2b-cja.md | B2B Customer Journey Analytics Blueprint | 針對使用帳戶作為主要資料模型的B2B組織，以帳戶為基礎的CJA報表和分析。 | 圖樣 | 複製 |  |  |  | help/blueprints/use-case-patterns/analysis/b2b-analytics.md | 4 | 2 | 覆寫2：同等模式涵蓋使用CJA B2B edition的B2B帳戶層級分析。 動作：簡化成圖表、交叉連結。 |
| help/blueprints/customer-journey-analytics/cja-rtcdp.md | Customer Journey Analytics 搭配 Real-time Customer Data Platform 藍圖 | 從CJA建立對象並發佈到RTCDP，以進行目標定位和個人化。 | 圖表 | 圖表 |  |  | CJA對RTCDP對象發佈整合 |  | 1 | 3 | 強大的架構重點（系統間整合、部署形式）。 最低限度的敘述。 獨特內容： CJA對象發佈延遲護欄。 |
| help/blueprints/customer-journey-analytics/cja-ajo.md | Customer Journey Analytics 搭配 Journey Optimizer 藍圖 | 在CJA中分析AJO傳遞和互動資料；將CJA對象發佈至AJO。 | 圖表 | 圖表 |  |  | CJA與AJO的整合與分析 |  | 1 | 3 | 強大的架構焦點。 最低限度的敘述。 唯一內容：雙向CJA-AJO資料共用模式。 |
| help/blueprints/customer-journey-analytics/analysis.md | 資料分析與情報 Blueprint | 使用Experience Platform Query Service探索Data Lake資料。 | 圖表 | 圖表 |  |  | Experience Platform查詢服務與BI工具整合 |  | 1 | 3 | 涵蓋查詢服務，而非CJA專用。 在CJA資料夾中可能會發生錯誤；請考慮重新放置到experience-platform/ 。 強大的架構者對象（PostgreSQL、BI工具）。 |
| help/blueprints/customer-journeys/overview.md | 客戶歷程藍圖 | 現代行銷平台可支援事件導向的歷程，以及跨管道的品牌啟動行銷活動。 | 導覽 | 導覽 |  |  |  |  |  |  | 覆寫1： overview.md。 歷程子類別的目錄；說明Journey Optimizer和Campaign定位。 |
| help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-overview.md | Journey Optimizer藍圖 | 事件導向的1:1設定檔協調以及跨管道的對象型品牌通訊。 | 導覽 | 導覽 |  |  |  |  |  |  | 覆寫1： overview.md。 包含使用案例標籤和整合模式的登陸頁面。 |
| help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-journeys.md | Journey Optimizer — 觸發式傳訊和Adobe Experience Platform Blueprint | 即時事件導向工作流程，根據客戶行為提供個人化的多步驟體驗。 | 圖樣 | 複製 |  |  |  | help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md | 4 | 2 | 覆寫2但有警告：代理程式標籤為可能重複但不確定。 請先驗證範圍是否一致，然後再縮小。 架構考量事項可能是獨一無二的（設定檔新鮮度、區段資格計時），值得在圖表中儲存。 |
| help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-campaigns.md | Journey Optimizer — 行銷活動策劃 | 跨傳出頻道（電子郵件、簡訊、推播、直接郵件）的已排程受眾型多步驟通訊。 | 圖樣 | 複製 |  |  |  | help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md | 3 | 2 | 覆寫2：對等模式。 多重架構圖表；保留為圖表。 獨特內容：關聯式資料庫/對象入口網站/皮膚設定檔架構詳細資料。 |
| help/blueprints/customer-journeys/journey-optimizer/3rd-party-messaging.md | Journey Optimizer — 第三方傳訊藍圖 | 示範Journey Optimizer與協力廠商傳訊系統的整合，以進行協調的通訊。 | 混合 | 分割 | campaign-management-orchestration | 第三方傳訊與Journey Optimizer整合 | 協力廠商傳訊架構 |  | 2 | 2 | 平分的相→分數。 圖表（系統至系統拓撲）加上模式內容（實作步驟、整合限制：承載驗證、無靜態IP、速率限制）。 值得保留兩者。 |
| help/blueprints/customer-journeys/decision-management/decision-management-overview.md | 決策管理藍圖 | 透過集中式優惠資料庫和決定引擎，在客戶歷程中提供個人化優惠。 | 導覽 | 導覽 |  |  |  |  |  |  | 覆寫1： overview.md。 說明決策管理元件和邊緣與中樞部署方法的比較。 |
| help/blueprints/customer-journeys/decision-management/decision-management-edge.md | 邊緣上 Decision Management 藍圖 | 在邊緣網路上以次秒的延遲提供即時網路和行動體驗的個人化選件。 | 混合 | 複製 |  |  |  | help/blueprints/use-case-patterns/personalization/offer-decisioning.md | 2 | 3 | 覆寫2：對應至offer-decisioning。 Edge部署變體 — 考慮將和中樞Blueprint整合為單一部署選項圖表。 |
| help/blueprints/customer-journeys/decision-management/decision-management-hub.md | 中心上的決策管理藍圖 | 跨頻道提供個人化優惠方案，包括資訊站、代理程式協助的體驗和傳出傳遞。 | 混合 | 複製 |  |  |  | help/blueprints/use-case-patterns/personalization/offer-decisioning.md | 2 | 3 | 覆寫2：對應至offer-decisioning。 中心部署變體 — 考慮將與Edge Blueprint整合為單一部署選項圖表。 |
| help/blueprints/customer-journeys/campaign-v8/campaign-v8-overview.md | Campaign v8藍圖、Campaign和平台 | 次世代批次行銷活動管理平台，具備ETL、細分和異動訊息傳送功能。 | 圖樣 | 圖樣 | campaign-management-orchestration | Campaign v8批次協調流程和異動訊息 | Campaign v8架構部署模型 |  | 4 | 3 | 獨特的技術方法（Campaign v8原生，而非AJO）。 多重架構圖表；業務框架；護欄中隱含的KPI （每小時20百萬項訊息，即時1百萬項）。 現有圖樣目錄中沒有對等專案。 注意：分數也符合分割的條件 — 建議模式，但作者可能希望保留圖表。 |
| help/blueprints/customer-journeys/campaign-v8/rtcdp-and-campaign-v8.md | Real-Time CDP 與 Adobe Campaign v8 整合模式 | 展示RTCDP對象和設定檔與Campaign v8的整合，以進行個人化對話。 | 圖表 | 圖表 |  |  | RTCDP - Campaign v8對象和設定檔交換 |  | 1 | 2 | 整合聯結器藍圖，而非獨立使用案例。 圖表+簡短的先決條件/護欄。 架構導向。 |
| help/blueprints/customer-journeys/campaign-v8/ajo-and-campaign-v8.md | Journey Optimizer 搭配 Adobe Campaign v8 藍圖 | 使用Campaign v8交易訊息示範1:1體驗的AJO協調流程。 | 圖表 | 圖表 |  |  | Journey Optimizer - Campaign v8交易訊息整合 |  | 1 | 2 | 整合聯結器。 圖表+實作步驟+技術限制（4,000訊息/5分鐘節流閥，僅限事件起始）。 AJO和Campaign v8模式的交叉連結。 |
| help/blueprints/customer-journeys/campaign-v7/campaign-v7-overview.md | Campaign v7 藍圖 | 已棄用：批次式傳訊、入門、再行銷、直接郵件、簡單交易式傳訊。 | 導覽 | 導覽 |  |  |  |  |  |  | 已棄用的產品（v8的前端內容連結）。 最低限度的內容（僅限架構圖）。 請勿移轉。 |
| help/blueprints/customer-journeys/campaign-v7/rtcdp-and-campaign-v7.md | Real-Time CDP與Campaign v7和Campaign Standard整合模式 | 展示RTCDP和即時客戶個人檔案與Campaign v7/Standard的整合，以進行個人化對話。 | 圖表 | 圖表 |  |  | RTCDP - Campaign v7/Standard對象和設定檔交換 |  | 1 | 2 | 已棄用。 整合聯結器。 圖表+完整的實作步驟。 請勿移轉至新模式；請保持原樣。 |
| help/blueprints/customer-journeys/campaign-v7/ajo-and-campaign-v7.md | Journey Optimizer 搭配 Adobe Campaign v7 藍圖 | 使用Campaign v7交易訊息示範1:1體驗的AJO協調流程。 | 圖表 | 圖表 |  |  | Journey Optimizer - Campaign v7交易訊息整合 |  | 1 | 2 | 已棄用。 整合聯結器。 圖表+實作步驟+限制。 請勿移轉，請保持原樣。 |
