---
source-git-commit: 2ed15399073fce5ebd1c2ba07b1cf70ec706452c
workflow-type: tm+mt
source-wordcount: '790'
ht-degree: 2%
---
# 移轉狀態a€」使用案例模式的Blueprint

本檔案會擷取藍圖重組工作的狀態，以便在不同工作階段間乾淨地繼續。

**上次更新日期：** 2026-09-24

## 我們目前的處境

B2B區段不再暫停。 其已發佈的架構範圍現在僅限於對象/設定檔和帳戶啟動頁面，而淘汰的頁面會重新導向至類別概觀。

**目前狀態：** B2B架構清理已完成。 對象/設定檔和帳戶啟動頁面仍會保留在架構圖表類別中；其他B2B架構頁面則已淘汰，並重新導向至類別概觀。

## 工作方法

> 以下的工作方法是歷史性的；B2B區段之後已停止位置，如上所述。

目前的工作模式（在此會議中商定）是：

1. **讓Blueprint保持運作** a€」不棄用。 每個Blueprint都會作為以架構為中心的頁面保留原位。
2. **在H1之後立即將交叉連結提示**&#x200B;新增至具有相關/重疊使用案例模式的每個Blueprint：

   ```
   >[!TIP]
   >This blueprint is also available as a [use case pattern](<absolute path>) under <Category>.
   ```

3. **移轉圖表** a€」如果藍圖有相關模式缺少的架構圖表，請透過絕對路徑將`## Architecture`區段新增至參照相同SVG的模式。 資產會保留在其原始位置（無檔案副本）。
4. 從Blueprint中&#x200B;**修剪實作步驟** （在模式中）。 要移除的區段通常包括： `## Implementation steps`、`## Implementation patterns`、`## Implementation considerations`，有時是`## Prerequisites`。 根據藍圖使用判斷。
5. **逐一進行** a €根據藍圖提出變更，取得使用者核准，然後套用。

### 通用規則

- 交叉連結提示用語一致： `>This blueprint is also available as a [use case pattern](...) under <Category>.`
- 新檔案（移轉期間建立的使用案例模式） **不包含`exl-id`** a€」Adobe出版物指派這些檔案。
- 新撰寫檔案中的影像參考使用絕對路徑(`/help/blueprints/...`)，而非相對路徑。
- 保留現有頁面上的現有`exl-id`值。
- `redirects.csv`中的重新導向會以`/en/docs/...`個路徑（無`.html`）遵循格式`source,dest`。

## 階段Aa€「E （初始結構工作） a€」完成

| 階段 | 結果 |
| --- | --- |
| A | 已建立`B2B Activation & Marketing`個使用案例模式類別。 已重新定位3個現有模式(`b2b-audience-activation` a†&#39; `b2b/account-audience-activation`，`buying-group-based-marketing` a†&#39; `b2b/buying-group-marketing`，`b2b-analytics` a†&#39; `b2b/account-analytics`)。 新增3個重新導向。 |
| B | 已將4個B2B Blueprint複製到`use-case-patterns/b2b/` (`marketo-data-journeys`， `paid-media-orchestration`， `campaign-intake-and-creation`， `campaign-review-and-approval`)。 |
| C | 已複製4個非B2B Blueprint (`real-time-profile-lookup`、`data-science-profile-enrichment`、`edge-profile-access`、`campaign-v8-orchestration`)。 |
| D | 已複製2個分割Blueprint (`audience-sharing-with-target`， `third-party-messaging`)。 |
| E | 在9個重複分類的Blueprint中新增交叉連結提示。 |

Aa€&quot;E之後的使用案例模式總數：6個類別中的&#x200B;**26個模式**。

## 逐節逐步解說（進行中）

本節逐步解說會將跨連結/圖表移轉/實作內嵌方法套用至使用者檢閱的每個藍圖。

### aoe... Audience &amp; Profile Activation a€&quot; 8/8完成

| # | 藍圖 | 已執行動作 |
| --- | --- | --- |
| 1 | `audience-manager.md` | 交叉連結提示+圖表已移轉至模式(`anonymous-visitor-web-personalization`) + RTCDP實作步驟已移除 |
| 2 | `enterprise-destinations.md` | 交叉連結提示+圖表已移轉至模式(`audience-activation-to-destinations`) |
| 3 | `advertising-activation.md` | 移除實作步驟（99 a†&#39; 35行） |
| 4 | `customer-activity.md` | 移除實作步驟（51a†&#39; 40行） |
| 5 | `data-science.md` | 移除實作考量（46個a†&grave; 40行） |
| 6 | `real-time-lookup.md` | 先決條件+實作模式/步驟/考量已移除（156 a†&#39; 73行） |
| 7 | `segment-match.md` | **沒有變更** （使用者選擇保持原狀） |
| 8 | `rtcdp-target.md` | 實作模式+已移除考量事項（99 a†&#39; 74行） |

### oÿ ¡B2B啟動與行銷a€&quot; 1/10正在進行中

| # | 藍圖 | 狀態 |
| --- | --- | --- |
| 1 | `b2b/overview.md` | 已完成 — B2B類別概觀已更新 |
| 2 | `b2b/b2bactivation.md` | 已淘汰 — 由架構圖對象/設定檔頁面取代 |
| 3 | `b2b/b2b-account-activation.md` | 保留 — 已移轉至架構圖表B2B類別 |
| 4 | `b2b/b2b-buying-group-journeys.md` | 已淘汰 |
| 5 | `b2b/b2b-journeys-with-marketo.md` | 已淘汰 |
| 6 | `b2b/ajo-b2b-paid-media-controller.md` | 已淘汰 |
| 7 | `b2b/marketo-engage-and-workfront-integration-blueprint/overview.md` | 已淘汰 |
| 8 | `b2b/marketo-engage-and-workfront-integration-blueprint/intake-and-create.md` | 已淘汰 |
| 9 | `b2b/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint.md` | 已淘汰 |
| 10 | `b2b/marketo-engage-and-workfront-integration-blueprint/customer-success-stories.md` | 已淘汰 |

### asCustomer Journey Analytics a€」 0/5尚未開始

檔案： `overview.md`、`b2b-cja.md` （階段E重複，交叉連結已新增）、`cja-rtcdp.md` （群組2 a €建議交叉連結至`customer-analytics-insight-generation`）、`cja-ajo.md` （群組2 a €相同）、`analysis.md` （群組3，可能重新定位至experience-platform/）。

### asªCustomer Journeys a€」退休清理完成；保留頁面移轉擱置中

檔案： `overview.md`； `journey-optimizer/` （4個檔案：總覽、歷程[階段E]、行銷活動[階段E]、第三方傳訊[階段D]）； `campaign-v8/` （3個檔案：總覽[階段C]、rtcdp-and-v8、ajo-and-v8）。 `decision-management/`和`campaign-v7/`已完全淘汰；其歷史專案仍保留在稽核中，其URL重新導向到核准的總覽頁面。

### asExperience Platform a€」 0/6尚未開始

檔案： `experience-cloud.md`、`platform-applications.md`、`platform-data-flow.md`、`guardrails.md`、`deployment/websdk.md`、`deployment/appsdk.md`。 全部在稽核中以0模式訊號僅圖表方式評分。 **可能所有「沒有變更」** a€」都是基礎架構，沒有使用案例模式與重疊。

「決定管理」和「Campaign v7」淘汰決定已完成。 他們的相關未完成問題
僅供歷史使用，不會阻礙其餘的移轉工作。

## 參考檔案

| 檔案 | 用途 |
| --- | --- |
| [blueprint-audit.md](blueprint-audit.md) | 具有建議的每個Blueprint稽核表（43列） |
| [rubric.md](rubric.md) | 用於分類藍圖的評分規則 |
| [migration-redirects.csv](migration-redirects.csv) | 從移轉分段重新導向 |
| [重新導向.csv](../redirects.csv) | 標準重新導向檔案（階段A新增3列） |

## 仍未解決的問題（來自稽核）

&#x200B;2. 「**`journey-optimizer-journeys.md`** a€」標籤為不確定的`event-triggered-messaging`重複專案；修剪前請先驗證範圍。
&#x200B;3. 「**`customer-journey-analytics/analysis.md`** a€」內容與Experience Platform查詢服務有關，而非CJA；請考慮重新定位至`experience-platform/`。
&#x200B;4. **`customer-success-stories.md`** a€」僅限連結的頁面；確認導覽分類。
&#x200B;5. 由已完成的B2B架構配置取代的歷史TOC錨點問題。

## 如何繼續

在此存放庫中開啟新的Claude程式碼工作階段，並說：

> 讓我們繼續Blueprint移轉。 閱讀`_evaluation/migration-status.md`以取得我們中斷的時間。

B2B架構清理已完成。 在驗證後，繼續下一個計畫的架構類別。
