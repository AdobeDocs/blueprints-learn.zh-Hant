---
name: architecture-diagram-category-builder
description: 在Adobe Experience Platform Blueprint存放庫中的架構圖表和Blueprint底下指導建立全新的頂層類別（子區段）。 當建議的架構圖不符合任何現有類別（架構概覽、對象和設定檔啟動、B2B啟動和行銷、客戶分析、客戶歷程）並需要新類別時，請使用此技能。 處理完整的工作流程：確認新類別確實有保證、強制資料夾/錨點命名慣例、建立資料夾結構和overview.md登陸頁面、新增TOC.md子區段，以及更新architecture-diagrams登陸頁面卡片格線。 若要將頁面新增至*existing*類別，請改用architecture-diagram-page-builder。
source-git-commit: c766cd3153efce4635089d008daf3eb426eb7a24
workflow-type: tm+mt
source-wordcount: '1062'
ht-degree: 0%
---

# 架構圖表類別產生器

此技能可指導在`/help/blueprints/TOC.md`中的`+ Architecture Diagrams and Blueprints{#architecture-diagrams}`下建立新的最上層類別。 類別是類似`customer-insights/`或`b2b-activation-marketing/`的資料夾 — 一組相關的架構圖表頁面，具有自己的`overview.md`登陸頁面和自己的TOC子區段。

**這是一項罕見的作業。** 今天有五個類別。 只有當真正的新架構內容網域不適合任何現有網域時，才應該新增第六個網域，而非作為避免將頁面組織到現有類別下的捷徑。

## 開始前的必要讀取

- `./references/naming-conventions.md` — 資料夾/錨點/標籤命名規則及其重要原因。 請詳閱本文；這是命名類別必須遵循的單一信任來源。
- `./references/category-overview-template.md` — 新類別的`overview.md`所需的確切結構。
- 如果沒有，也略過`../architecture-diagram-page-builder/SKILL.md` — 一旦類別存在，它會使用該技能新增個別頁面，而不是使用這個技能。

## 階段1：確認實際需要新類別

執行任何其他操作之前，請向使用者列出五個現有類別及其範圍：

| 類別 | 資料夾 | 範圍 |
| --- | --- | --- |
| 架構概述 | `architecture-overviews/` | 頂層Experience Cloud / Experience Platform架構、護欄、部署SDK |
| 對象與個人資料啟用 | `audience-profile-activation/` | 透過Real-Time CDP、Audience Manager建立及啟用對象/設定檔 |
| B2B啟用與行銷 | `b2b-activation-marketing/` | 帳戶型啟用、購買群組歷程、Marketo/Workfront |
| 客戶分析 | `customer-insights/` | Customer Journey Analytics及其整合 |
| 客戶歷程 | `customer-journeys/` | Journey Optimizer、決定管理、Campaign v7/v8 |

要求使用者確認建議的內容不符合其中任何一項。 如果它是特別適合的（例如，新的B2B圖表、新的個人化圖表），請針對該現有類別重新導向至`architecture-diagram-page-builder`，而非建立新的類別。 只有在使用者確認真正的新類別需要保證時，才會繼續階段2。

## 階段2：收集類別資訊

使用問題表單來收集，一次收集：

1. **類別標籤** — 完整、人類看得懂的TOC標籤（例如「Commerce架構」，不是縮寫）。 目前有2-3個建議的短語加上「其他」。
2. **單句說明** — 此類別涵蓋的內容（針對`overview.md`首頁和登陸頁面卡）。
3. **主要Adobe解決方案** — 適用於frontmatter `solution`欄位。
4. **初始頁面** — 使用者是否已有1個以上的頁面可放置在此類別中，或是這只是建構類別以供稍後遵循？

使用`./references/naming-conventions.md`中的概要(Slug)規則，從類別標籤衍生資料夾名稱和錨點（小寫、放置`&`、連字、無縮寫）。 向使用者顯示衍生資料夾/錨點，並在繼續前確認 — 這是日後修復成本高昂的一個細節。

## 階段3：建立檔案夾結構

```
help/blueprints/architecture-diagrams/{new-folder}/
help/blueprints/architecture-diagrams/{new-folder}/assets/
help/blueprints/architecture-diagrams/{new-folder}/overview.md
```

使用`./references/category-overview-template.md`產生`overview.md`。 如果使用者有準備好的初始頁面，請現在在表格中列出它們（使用`architecture-diagram-page-builder`自己產生這些頁面檔案 — 此技能只會建立類別支架及其概觀頁面，而不是個別的圖表頁面）。 如果還沒有任何頁面，表格可能會空白或省略，直到新增第一頁為止 — 請向使用者注意這一點，而不是發明預留位置列。

`assets/`資料夾在建立時可以是空的；因為資料夾存在，所以新增到類別的第一個圖表頁面會有放置影像的地方。

## 階段4：新增TOC.md子區段

將新類別插入為`+ Architecture Diagrams and Blueprints{#architecture-diagrams}`下的最上層專案，位置在最後一個現有類別之後，除非使用者另外指定：

```
  + {Category Label}{#{folder-slug}}
    + [Overview](/help/blueprints/architecture-diagrams/{new-folder}/overview.md)
    + [{Page title}](/help/blueprints/architecture-diagrams/{new-folder}/{filename}.md)
```

規則：

- 類別標題有2個空格縮排，與其他五個相符。
- 錨點`{#{folder-slug}}`必須完全等於資料夾名稱（請參閱naming-conventions.md）。
- `+ [Overview]`永遠是任何內容頁面之前的第一個專案，以4個空格縮排。
- 保留所有其他TOC.md專案的現有順序和內容 — 僅插入、從不重新排序或重寫不相關的區段。

## 階段5：更新架構圖表和藍圖登陸頁面

新增一張卡片至`help/blueprints/architecture-diagrams/overview.md`，並位於其他五張卡片所使用的`<table style="table-layout:fixed; width:100%;">`格線中。 新卡片：

- 連結至`{new-folder}/overview.md`。
- 使用來自`{new-folder}/assets/`的代表性圖表縮圖（或如果圖表尚不存在則使用中性預留位置備註 — 將此標籤給使用者，而不是發明影像路徑）。
- 使用與現有卡片完全相同的內嵌樣式區塊（`width:100%; height:160px; object-fit:contain; background-color:#ffffff; border:1px solid #d3d3d3; padding:10px; box-sizing:border-box;`在影像上，`min-height:100px;`在文字div）。

**重新計算格線配置。** 現有的五張卡片會填滿3欄的格線（兩列、一個尾端空白儲存格）。 新增第六張卡片會完全填滿該空白儲存格 — 不需要變更版面。 如果這是第7、8等類別，請以新卡片新增新的`<tr>`，並以空白`<td style="width:33%; ...;"></td>`元素填入該列中任何剩餘的空白儲存格，使該列不會呈現不規則狀。

## 階段6：驗證

確認並向使用者報告：

1. **命名一致性** — 資料夾名稱、目錄錨點和類別標籤slug相同（根據naming-conventions.md）。
2. **overview.md結構** — 符合`category-overview-template.md` （介紹+兩欄`Diagram | Description`表格，表格中沒有內嵌影像或巢狀清單）。
3. **TOC.md位置** — 新子區段位於[架構圖表和Blueprint]下，`+ [Overview]`是第一個，縮排正確，沒有其他專案被更改。
4. **登陸頁面卡片** — 新增到正確的格線位置，使用標準卡片樣式，連結到新`overview.md`。
5. **重新導向** — 如果此類別合併或重新命名先前在其他地方存在的內容（新類別很少使用，但請檢查），請依照先前架構圖表重新命名所使用的現有`source,dest`格式，將專案新增至`redirects.csv`。

在考量任務完成之前，請先修正任何驗證問題。

## 附註

- 如果使用者稍後重新命名類別（標籤、資料夾或錨點），也就是重新命名作業，而不是新類別作業 — 請遵循新名稱的naming-conventions.md規則、更新每個內部連結（TOC.md、兩個概觀頁面、同層級相對連結、技能檔案），並新增重新導向專案。 處理方式與先前在此存放庫處理類別重新命名的方式相同： `git mv`資料夾，然後在整個存放庫搜尋並取代舊路徑表單，永遠不要使用可能與不相關外部URL衝突的盲全域字串取代（例如`experienceleague.adobe.com/docs/experience-platform/...`產品檔案連結）。
- 保持此技能與`architecture-diagram-page-builder`同步：如果`architecture-diagram-page-builder`的`references/toc-placement.md`中的子區段對應資料表尚未列出新類別，請一併新增。
