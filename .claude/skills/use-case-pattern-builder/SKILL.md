---
name: use-case-pattern-builder
description: 為Adobe Experience Platform Blueprint存放庫建立新使用案例模式內容的指南。 在新增使用案例模式、建立實作指導內容，或使用者提及將模式新增到藍圖網站時，請使用此技能。 處理完整的工作流程：收集模式資訊、產生具有正確範本結構的Markdown檔案，以及更新所有互動參照頁面(TOC.md、overview.md)。
source-git-commit: ed8928687806b619e95d8d320478d27c13722a80
workflow-type: tm+mt
source-wordcount: '1096'
ht-degree: 100%

---


# 使用案例模式產生器

此技能可指導Adobe Experience Platform Blueprint存放庫建立新的使用案例模式。 它會處理完整的工作流程：從使用者收集模式資訊、產生具有正確範本結構的Markdown內容檔案，以及更新所有互動參照頁面，以便探索新模式。

開始之前，請閱讀以下參考檔案，以瞭解完整的範本結構和要更新的頁面檢查清單：

- `references/pattern-template.md` — 具有預留位置值的完整Markdown範本
- `references/pages-to-update.md` — 新增模式時必須更新的頁面檢查清單

## 階段1：資訊收集

在產生任何檔案之前，詢問使用者以收集所有必要的資訊。 詢問下列問題，並在提供或明確延遲每個專案之前，不要繼續產生內容。

### 必要資訊

1. **模式名稱** — 人類可讀的標題（例如「事件觸發的傳訊」）。

2. **類別** — 只有下列其中一項：
   - `audience-building-activation`
   - `personalization`
   - `campaign-management-orchestration`
   - `analysis`
   - `conversational-experience`

3. **主要功能說明** — 說明此模式的用途的單一句子（用於概觀表格和frontmatter說明）。

4. **核心Adobe解決方案** — 此模式的核心Adobe產品。 請視需要選擇：Journey Optimizer、Real-Time Customer Data Platform、Experience Platform、Customer Journey Analytics、Brand Concierge、Journey Optimizer B2B edition、Real-Time CDP B2B edition或其他選項。

5. **函式鏈步驟** — 描述模式執行流程的3-6個循序階段，以`>`分隔。 範例：「事件擷取>歷程登入>條件評估>訊息傳送>報告」。

6. **支援的業務目標** — `/help/blueprints/business-objectives/`下現有集合中的一或多個業務目標。 每個檔案夾都應包含目標名稱、類別子檔案夾和檔案名稱。 在產生內容之前，請確認參考的檔案存在。

7. **戰術使用案例範例** — 6至10個專案符號情境，說明如何在不同業務內容中套用此模式。 每個案例都應該有粗體案例名稱及後續說明。

8. **KPI** — 包含三欄的表格：KPI （名稱）、說明（測量專案）、測量（公式或方法）。

9. **實作選項** — 2-4實作選項。 針對每個選項，收集：
   - 選項名稱
   - 最適合（何時使用此選項）
   - 運作方式（2-4段）
   - 主要考量事項（專案符號清單）
   - 優點（專案符號清單）
   - 限制（專案符號清單）
   - Experience League連結（相關檔案的URL）

### 可選用，但建議使用

- 使用案例概述段落（3-5段；如果未提供，則從其他資訊草稿）
- 應用程式清單，其中包含每個Adobe應用程式的角色說明
- 基礎函式表格（函式、狀態、需就位專案、Experience League參考）
- 支援函式表格（函式、狀態、重要原因、Experience League參考）
- 應用程式函式表格（每個應用程式一個表格，具有「函式」、「實作階段」、「說明」）
- 先決條件檢查清單

如果使用者未提供選擇性專案，則根據模式類別、解決方案和功能鏈產生合理的預設值。

## 階段2：內容產生

在下列路徑產生模式Markdown檔案：

```
/help/blueprints/use-case-patterns/{category}/{kebab-case-pattern-name}.md
```

檔案名稱必須使用衍生自圖樣名稱的kebab大小寫。 例如，「事件觸發訊息」會變成`event-triggered-messaging.md`。

使用`references/pattern-template.md`中的範本，並將收集的資訊填入所有預留位置值。 產生的檔案必須包含範本中的每個區段：

1. **YAML frontmatter** — 標題、說明、解決方案（以逗號分隔）、exl-id （產生UUID預留位置，例如`xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx` — 發佈團隊將指派真正的預留位置）。

2. **開啟區段** — `# {Pattern name}`標題，後面是介紹性段落和「使用本指南瞭解……」 句子。

3. **使用案例概觀** — 3-5段落，說明模式範圍、適用時間、做和不做，以及典型利害關係人。

4. **關鍵業務目標** — 每個目標都作為連結標題，並附有簡短說明和KPI摘要列。

5. **戰術使用案例範例** — 6-10個案例的專案符號清單。

6. **關鍵績效指標** — 包含KPI、說明、測量欄的表格。

7. **使用案例模式** — 說明段落和函式鏈。

8. **應用程式** — 具有`[!DNL ...]`格式及說明的Adobe應用程式清單。

9. **基本函式** — 含資料行的表格：基本函式、狀態、必須放置的專案、Experience League參考。 狀態值：必要、已假設就位、不適用。

10. **支援函式** — 含資料行的表格：支援函式、狀態、其重要原因、Experience League參考。 狀態值：建議、已包含、不適用。

11. **應用程式函式** — 每個應用程式有一個資料表，資料行：函式、實作階段、說明。

12. **先決條件** — 使用`- [ ]`語法的檢查清單。

13. **實作選項** — 2-4個詳細選項，每個選項都有其最佳用途、運作方式、關鍵考量、優點、限制和Experience League連結。

14. **選項比較** — 末尾的摘要比較表。

## 階段3：對照參考更新

產生陣列檔案後，請更新下列檔案。 請閱讀`references/pages-to-update.md`以取得詳細的檢查清單。

### TOC.md

**檔案：** `/help/blueprints/TOC.md`

在正確的類別區段底下新增專案。 類別對應至這些TOC區段：

| 類別概要 | 目錄章節標題 |
| --- | --- |
| `audience-building-activation` | `+ Audience Building & Activation{#audience-building-activation}` |
| `personalization` | `+ Personalization{#personalization-patterns}` |
| `campaign-management-orchestration` | `+ Campaign Management & Orchestration{#campaign-orchestration-patterns}` |
| `analysis` | `+ Analysis{#analysis-patterns}` |
| `conversational-experience` | `+ Conversational Experience{#conversational-experience-patterns}` |

專案格式為：

```
    + [{{Pattern Title}}](/help/blueprints/use-case-patterns/{{category}}/{{filename}}.md)
```

在相符區段中最後一個現有專案之後新增專案。 保留確切的縮排（`+`前的四個空格）。

### 概觀頁面

**檔案：** `/help/blueprints/use-case-patterns/overview.md`

新增一列到正確的類別表格中。 格式為：

```
| [{{Pattern Title}}]({{category}}/{{filename}}.md) | {{Primary capability description}} | [!DNL {{Solution1}}], [!DNL {{Solution2}}] |
```

在相符類別表格中最後一個現有列之後新增新列。

## 階段4：驗證

建立及更新所有檔案後，請確認下列事項：

1. **商業目標連結** — 模式檔案中的每個商業目標連結都指向`/help/blueprints/business-objectives/`下的現有檔案。 使用glob或read來確認每個目標檔案都存在。

2. **目錄專案位置** — 新的TOC專案位於正確的類別區段中，並使用正確的縮排和路徑格式。

3. **概觀表格列** — 新的概觀列在正確的類別表格中，且遵循與現有列相同的欄格式。

4. **檔案命名** — 模式檔案名稱使用kebab大小寫，並符合TOC.md和overview.md中參照的路徑。

5. **Frontmatter完整性** — 模式檔的YAML frontmatter中包含標題、說明、解決方案和exl-id。

6. **Experience League連結** — 抽查任何Experience League URL是否可行（從`https://experienceleague.adobe.com/zh-hant`開始）。

向使用者報告任何驗證失敗，並在考慮任務完成之前修正它們。

## 附註

- 請一律遵循現有模式檔案的慣例，在表格和本文中，對Adobe產品名稱使用`[!DNL ...]`語法。
- frontmatter中的`exl-id`應為預留位置UUID。 發佈管道會指定實際值。
- 如果使用者想要一次建立多個模式，請重複每個模式的「階段2-4」，但在階段1中收集所有資訊。
- 如果需要上述清單中不存在的新的類別，請警告使用者TOC.md和overview.md需要建立新的區段，並將此作為個別步驟處理。
