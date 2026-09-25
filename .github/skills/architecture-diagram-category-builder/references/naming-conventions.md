---
source-git-commit: c766cd3153efce4635089d008daf3eb426eb7a24
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%
---
# 命名慣例：架構圖表和藍圖

此檔案是`+ Architecture Diagrams and Blueprints{#architecture-diagrams}`下類別命名方式的真實來源。 `architecture-diagram-category-builder`技能（新類別）和`architecture-diagram-page-builder`技能（現有類別中的新頁面）都必須遵循這些規則。

## 規則

**資料夾名稱= TOC錨點slug =完整TOC標籤的kebab大小寫。** 所有三個都必須完全相符，沒有縮寫或截斷。

| TOC標籤 | 錨點 | 資料夾 |
| --- | --- | --- |
| 架構概述 | `#architecture-overviews` | `architecture-overviews/` |
| 對象與個人資料啟用 | `#audience-profile-activation` | `audience-profile-activation/` |
| B2B啟用與行銷 | `#b2b-activation-marketing` | `b2b-activation-marketing/` |
| 客戶分析 | `#customer-insights` | `customer-insights/` |
| 客戶歷程 | `#customer-journeys` | `customer-journeys/` |

這是所有五個類別（截至2026-09-16）的目前修正狀態。 在此存放庫歷史記錄的前面，有些是縮寫的(`architecture-overview`、`audience-activation`、`b2b-activation`)，不一致已修正。 請勿為新類別或現有類別重新引入縮寫的資料夾/錨點名稱。

## 這很重要的原因

- **可預測性。** 投稿人（人或代理）應該能夠從TOC標籤猜測資料夾路徑，反之亦然，而無需開啟TOC.md。
- **安全自動化。** 從標籤（或來自路徑的標籤）產生路徑的技巧和指令碼只有在對應精確且機械化（kebab大小寫，無縮寫）時才能可靠運作。
- **重新導向衛生。** 每次重新命名都需要`redirects.csv`中的新專案。 從一開始就保持名稱穩定且具有完整描述性，可避免重複重新命名流失。

## 如何從標籤衍生概要

1. 標籤變為小寫。
2. 將`&`完全拖放並用連字型大小連線周圍的單字（例如`Audience & Profile Activation` -> `audience-profile-activation`）。
3. 以連字型大小取代空格。
4. 請去除連字型大小以外的標點符號。
5. 請勿從標籤縮寫、截斷或捨棄文字（「B2B啟動與行銷」無`b2b-activation` — 使用`b2b-activation-marketing`）。

## 每個類別的必要資產

`help/blueprints/architecture-diagrams/`下的每個類別資料夾都必須包含：

1. **`overview.md`** — 類別的登陸頁面。 如需必要的結構，請參閱`./category-overview-template.md`。 每個類別概觀頁面看起來都必須相同：介紹段落，然後單一`| Diagram | Description |`表格列出類別中的每個頁面（依目錄順序）。 請勿使用巢狀`<ul><li>`儲存格、內嵌圖表影像或第三欄 — 與現有的五個類別完全相符。
2. **`assets/`** — 圖表影像的資料夾，即使在建立時是空的（在新增第一個圖表後建立它）。

## TOC.md需求

- 類別的`+ [Overview](/help/blueprints/architecture-diagrams/{folder}/overview.md)`專案永遠是類別標題底下的&#x200B;**第一個**&#x200B;專案，在任何內容頁面之前。
- 類別標題及其錨點會直接位於`+ Architecture Diagrams and Blueprints{#architecture-diagrams}`下方，與其他五個類別位於相同的2空格縮排層級。
- 內容頁面會縮排4個空格（`+`加上四個前置空格）。 巢狀子群組（例如「對象和設定檔啟動」下的RTCDP群組）會縮排6個空格。

## 登陸頁面需求

`help/blueprints/architecture-diagrams/overview.md` （最上層架構圖表和Blueprint登陸頁面）在每個類別中必須有一個卡片（以目錄順序）。 每張卡片：

- 類別的`overview.md`連結（不是內容頁面）。
- 使用該類別`assets/`資料夾中的代表性圖表影像做為縮圖，樣式為標準卡片CSS （`background-color:#ffffff; border:1px solid #d3d3d3;`加上檔案中已存在的共用大小/邊框間距規則）。
- 包括類別名稱（粗體/強）和與類別概觀簡介相符的一句說明。

當類別的數目是3的倍數時，表格會呈現為乾淨的完整列（3欄，`table-layout:fixed`，每個儲存格`width:33%`）。 如果不是3的倍數，請在最後一列為每個遺失的槽新增一個空的`<td>` （不要讓表格變得不整齊/沒有樣式）。
