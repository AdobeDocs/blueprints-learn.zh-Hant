---
source-git-commit: 7511cc0e5c099d5d3ee1275a374cd9ffdc972335
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 0%

---
# Blueprint評估規則

此規則會套用至「架構圖表和藍圖」區段下的每個檔案
/ [TOC.md](../help/blueprints/TOC.md) （第76到133行），以建議每個藍圖是否應成為
**使用案例模式**、**架構圖表** (兩者皆有（**分割**）)，或標籤為已選取
現有模式的**重複**。

套用此規則的輸出為[blueprint-audit.md](blueprint-audit.md)。

## 定義

- **使用案例模式** — 說明特定業務或技術目標與相關資訊的檔案
概述達成該目標時可採用的實施方法及考量事項。
標準形狀： `.claude/skills/use-case-pattern-builder/references/pattern-template.md`。
- **架構圖** — 代表系統功能的視覺化圖表，
整合和資料流程。 最簡單的敘述；圖表是成品。
標準範例： [platform-data-flow.md](../help/blueprints/experience-platform/platform-data-flow.md)。

## 得分

每個Blueprint都是端對端讀取，並根據8個二進位訊號評分。 每個訊號都會貢獻
+1代表模式分數或圖表分數。

### 圖樣訊號（每個= +1圖樣）

1. **業務目標框架** — 框架收入、保留率、贏取、潛在客戶開發、成本
減少、客戶體驗或類似的業務成果。
2. **KPI或成功量度** — 明確指定量度、轉換率、匹配率、ROI或
類似的結果測量。
3. **多個實作選項或成熟度等級** — 提供選項A /選項B，基本與
進階或可供讀者選擇的替代方案。
4. **先決條件或整備檢查清單** — 列出實施之前必須準備好的專案。
5. **敘述式實作步驟>~30行** — 實質性的實作指引，而不是
只是簡短的總覽。

### 圖表訊號（每個= +1圖表）

6. **架構/資料流程影像出現** — `.svg`、`.png`或`.jpg`顯示系統拓撲，
資料流程或整合箭頭。
7. **系統間整合拓撲、部署圖形或護欄** — 說明如何進行
元件連線，資料存留於此處、部署模式（邊緣與中樞）或容量限制。
8. **對象是解決方案架構師** — 框架使用部署、SDK、edge、hub或類似專案
架構導向的術語而非行銷人員導向的框架(行銷活動、歷程、
對象)。

## 建議邏輯

先套用覆寫規則。 如果未觸發覆寫，則從分數衍生建議。

### 覆寫規則（最高優先順序）

1. **檔案名稱為`overview.md`** →建議= `Navigation`。 已排除在移轉之外；
頁面是TOC樣式的登陸頁面，會在子檔案結算後進行修訂。
2. **`help/blueprints/use-case-patterns/`**中已經存在對等模式→
建議= `Duplicate`。 移轉動作是將藍圖簡化為純粹的
架構圖並在現有模式中新增「參閱使用案例模式」交叉連結。
在`duplicate_of`欄中記錄現有的模式路徑。
3. **檔案在`experience-platform/`中，沒有業務目標訊號(#1)**→預設為
   `Diagram` （無論其他分數為何）。 此資料夾是架構概觀層。

### 以分數為基礎的建議（未觸發覆寫時）

| 圖樣分數 | 圖表分數 | 建議 | 推理 |
| --- | --- | --- | --- |
| ≥ 3 | ≤ 1 | `Pattern` | 強模式訊號、弱圖表訊號→移轉至模式。 |
| ≤ 1 | ≥ 2 | `Diagram` | 弱圖樣訊號，主視覺/拓撲焦點→保持為圖表。 |
| ≥ 3 | ≥ 2 | `Split` | 豐富的模式內容和有意義的圖表都→擷取模式，將原始內容簡化為圖表、交叉連結。 |
| 2 | 2 | `Split` | 以中等強度繫結→分割。 |
| 2 | ≤ 1 | `Pattern` | 圖樣傾斜，沒有顯著的圖表值。 |
| ≤ 1 | ≤ 1 | `Diagram` | 整體精簡 — 可能是現有的最低架構頁面。 |

## 如何套用規則

對於範圍內的每個Blueprint Markdown檔案：

1. 端對端讀取完整檔案。
2. 標示八個訊號中的每一個存在/不存在。
3. 依序套用覆寫規則。 如果觸發，則為建議。
4. 否則，請計算模式分數和圖表分數，並查閱建議。
5. 針對`Pattern`和`Split`建議，建議：
   - `proposed_pattern_category` — 其中之一：
     `audience-building-activation`, `personalization`, `campaign-management-orchestration`,
     `analysis`、`conversational-experience`或標示為`(new) <name>`的新類別。
   - `proposed_pattern_title` — 遵循現有模式的簡短動作導向標題
命名樣式。
6. 針對`Diagram`和`Split`建議，建議：
   - `proposed_diagram_title` — 通常是商業框架裁剪的現有標題。
7. 透過比較Blueprint的範圍與現有的模式目錄來擷取找到的任何重複專案
在`duplicate_of`中。
8. 在`notes`中記錄未完成的問題、值得保留的獨特技術內容或移轉風險。

## 現有使用案例模式目錄（用於重複資料偵測）

| 類別 | 模式 |
| --- | --- |
| audience-building-activation | audience-activation-to-destinations， audience-collaboration-segment-match， b2b-audience-activation，事件轉送 |
| 個人化 | anonymous-visitor-web-personalization， known-visitor-web-app-personalization， offer-decisioning， behavioral-recommendation |
| campaign-management-orchestration | 批次 — 傳出 — 訊息啟用、事件觸發訊息、多步驟協調歷程、跨管道歷程與決策、購買群組型行銷 |
| 分析 | customer-analytics-insight-generation、b2b-analytics |
| 對話式體驗 | 品牌關懷對話體驗 |
