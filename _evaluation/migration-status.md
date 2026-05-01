---
source-git-commit: 7511cc0e5c099d5d3ee1275a374cd9ffdc972335
workflow-type: tm+mt
source-wordcount: '820'
ht-degree: 2%

---
# 移轉狀態 — 使用案例模式的藍圖

本檔案會擷取藍圖重組工作的狀態，以便在不同工作階段間乾淨地繼續。

**上次更新日期：** 2026-04-29

## 我們目前的處境

**目前暫停於：** `b2b/overview.md` （B2B區段Blueprint#1為10） — 正在等候決定是否保持原狀、新增互動參照至新的B2B啟動和行銷模式區段，或更新表格以列出所有Blueprint +新增互動參照。

**若要繼續：**&#x200B;以&#x200B;**A** （建議保留原狀）、**B** （新增互動參照）或&#x200B;**C** （更新資料表+新增互動參照）回應。 然後繼續使用Blueprint #2 (`b2b/b2bactivation.md`)。

## 工作方法

目前的工作模式（在此會議中商定）是：

1. **讓Blueprint保持作用中** — 不棄用。 每個Blueprint都會作為以架構為中心的頁面保留原位。
2. **在H1之後立即將交叉連結提示**&#x200B;新增至具有相關/重疊使用案例模式的每個Blueprint：

   ```
   >[!TIP]
   >This blueprint is also available as a [use case pattern](<absolute path>) under <Category>.
   ```

3. **移轉圖表** — 如果藍圖具有相關模式缺少的架構圖表，請透過絕對路徑將`## Architecture`區段新增至參照相同SVG的模式。 資產會保留在其原始位置（無檔案副本）。
4. 從Blueprint中&#x200B;**修剪實作步驟** （在模式中）。 要移除的區段通常包括： `## Implementation steps`、`## Implementation patterns`、`## Implementation considerations`，有時是`## Prerequisites`。 根據藍圖使用判斷。
5. **逐一瀏覽** — 針對每個Blueprint提出變更、取得使用者核准，然後套用。

### 通用規則

- 交叉連結提示用語一致： `>This blueprint is also available as a [use case pattern](...) under <Category>.`
- 新檔案（移轉期間建立的使用案例模式） **不包含`exl-id`** — Adobe出版物會指派這些檔案。
- 新撰寫檔案中的影像參考使用絕對路徑(`/help/blueprints/...`)，而非相對路徑。
- 保留現有頁面上的現有`exl-id`值。
- `redirects.csv`中的重新導向會以`/en/docs/...`個路徑（無`.html`）遵循格式`source,dest`。

## 階段A-E （初始結構工作） — 完成

| 階段 | 結果 |
| --- | --- |
| A | 已建立`B2B Activation & Marketing`個使用案例模式類別。 已重新定位3個現有模式(`b2b-audience-activation` → `b2b/account-audience-activation`， `buying-group-based-marketing` → `b2b/buying-group-marketing`， `b2b-analytics` → `b2b/account-analytics`)。 新增3個重新導向。 |
| B | 已將4個B2B Blueprint複製到`use-case-patterns/b2b/` (`marketo-data-journeys`， `paid-media-orchestration`， `campaign-intake-and-creation`， `campaign-review-and-approval`)。 |
| C | 已複製4個非B2B Blueprint (`real-time-profile-lookup`、`data-science-profile-enrichment`、`edge-profile-access`、`campaign-v8-orchestration`)。 |
| D | 已複製2個分割Blueprint (`audience-sharing-with-target`， `third-party-messaging`)。 |
| E | 在9個重複分類的Blueprint中新增交叉連結提示。 |

A-E之後的使用案例模式總數：6個類別中的&#x200B;**26個模式**。

## 逐節逐步解說（進行中）

本節逐步解說會將跨連結/圖表移轉/實作內嵌方法套用至使用者檢閱的每個藍圖。

### ✅對象和設定檔啟用 — 8/8完成

| # | 藍圖 | 已執行動作 |
| --- | --- | --- |
| 1 | `audience-manager.md` | 交叉連結提示+圖表已移轉至模式(`anonymous-visitor-web-personalization`) + RTCDP實作步驟已移除 |
| 2 | `enterprise-destinations.md` | 交叉連結提示+圖表已移轉至模式(`audience-activation-to-destinations`) |
| 3 | `advertising-activation.md` | 移除實作步驟（99→35行） |
| 4 | `customer-activity.md` | 移除實作步驟（51→40行） |
| 5 | `data-science.md` | 移除實作考量（46→40行） |
| 6 | `real-time-lookup.md` | 先決條件+實作模式/步驟/考量已移除（156→73行） |
| 7 | `segment-match.md` | **沒有變更** （使用者選擇保持原狀） |
| 8 | `rtcdp-target.md` | 實作模式+移除考量事項（99→74行） |

### 🟡 B2B啟用與行銷 — 1/10正在進行中

| # | 藍圖 | 狀態 |
| --- | --- | --- |
| 1 | `b2b/overview.md` | **已暫停** — 等待決定A/B/C （請參閱上方的「我們目前的狀況」） |
| 2 | `b2b/b2bactivation.md` | 擱置中 — 階段E重複；新增交叉連結；需要檢閱圖表+實作修剪 |
| 3 | `b2b/b2b-account-activation.md` | 擱置中 — 圖表分類；需要交叉連結至`b2b/account-audience-activation.md` +圖表移轉考量 |
| 4 | `b2b/b2b-buying-group-journeys.md` | 擱置中 — 階段E重複；新增交叉連結；需要檢閱 |
| 5 | `b2b/b2b-journeys-with-marketo.md` | 擱置中 — 階段B複製；模式為複製；需要實作步驟修剪 |
| 6 | `b2b/ajo-b2b-paid-media-controller.md` | 擱置中 — 階段B複製；需要實作步驟修剪 |
| 7 | `b2b/marketo-engage-and-workfront-integration-blueprint/overview.md` | 擱置中 — 區段登陸頁面 |
| 8 | `b2b/marketo-engage-and-workfront-integration-blueprint/intake-and-create.md` | 擱置中 — 階段B複製；需要實作步驟修剪 |
| 9 | `b2b/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint.md` | 擱置中 — 階段B複製；需要實作步驟修剪 |
| 10 | `b2b/marketo-engage-and-workfront-integration-blueprint/customer-success-stories.md` | 擱置中 — 僅連結頁面（標籤為瀏覽的稽核） |

### ⚪ Customer Journey Analytics — 尚未開始0/5

檔案： `overview.md`、`b2b-cja.md` （階段E重複，已新增交叉連結）、`cja-rtcdp.md` （群組2 — 建議交叉連結至`customer-analytics-insight-generation`）、`cja-ajo.md` （群組2 — 相同）、`analysis.md` （群組3，可能重新定位至experience-platform/）。

### ⚪客戶歷程 — 0/14尚未開始

檔案： `overview.md`；`journey-optimizer/` （4個檔案：總覽、歷程[階段E]、行銷活動[階段E]、第三方傳訊[階段D]）；`decision-management/` （3個檔案：總覽、邊緣[階段E]、中心[階段E]）；`campaign-v8/` （3個檔案：總覽[階段C]、rtcdp-and-v8、ajo-and-v8）；`campaign-v7/` （3個已棄用的檔案）。

### ⚪ Experience Platform — 尚未開始0/6

檔案： `experience-cloud.md`、`platform-applications.md`、`platform-data-flow.md`、`guardrails.md`、`deployment/websdk.md`、`deployment/appsdk.md`。 全部在稽核中以0模式訊號僅圖表方式評分。 **可能全都是「沒有變更」** — 它們是不會與使用案例模式重疊的基本架構。

## 參考檔案

| 檔案 | 用途 |
| --- | --- |
| [blueprint-audit.md](blueprint-audit.md) | 具有建議的每個Blueprint稽核表（43列） |
| [rubric.md](rubric.md) | 用於分類藍圖的評分規則 |
| [migration-redirects.csv](migration-redirects.csv) | 從移轉分段重新導向 |
| [重新導向.csv](../redirects.csv) | 標準重新導向檔案（階段A新增3列） |

## 仍未解決的問題（來自稽核）

1. **決定管理Edge +中心** — 目前兩者都交叉連結至`offer-decisioning`。 考慮合併成單一部署選項圖表？
2. **`journey-optimizer-journeys.md`** — 標示為不明確的`event-triggered-messaging`重複專案；修剪前請先驗證範圍。
3. **`customer-journey-analytics/analysis.md`** — 內容與Experience Platform查詢服務有關，而非CJA；請考慮重新定位至`experience-platform/`。
4. **Campaign v7 （3個已棄用的檔案）** — 要移轉、離開或從TOC移除嗎？
5. **`customer-success-stories.md`** — 僅連結頁面；確認導覽分類。
6. 新B2B區段的&#x200B;**TOC錨點**&#x200B;為`{#b2b-patterns}` — 在任何生產重新導向建立之前先確認。

## 如何繼續

在此存放庫中開啟新的Claude程式碼工作階段，並說：

> 讓我們繼續Blueprint移轉。 閱讀`_evaluation/migration-status.md`以取得我們中斷的時間。

下一個具體步驟：回應`b2b/overview.md`決定(A/B/C)。 然後繼續使用Blueprint #2 (`b2b/b2bactivation.md`)並完成B2B區段，然後完成Customer Journey Analytics、客戶歷程和Experience Platform。
