---
source-git-commit: 83e85d946e455cde46001af0a2112637b7fe24cc
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---
# 架構圖表頁面範本

這是架構圖表頁面的完整Markdown範本。 以技能工作流程階段1期間收集的值取代每`{placeholder}`。 移除任何不適用的選用區段（例如`>[!MORELIKETHIS]`區塊） — 請勿在產生的檔案中保留空白的預留位置。

&#x200B;---

```markdown
---
title: {Page title}
description: {1-2 sentence page purpose, used for search snippets and previews}
solution: {Comma-separated Adobe solutions, e.g. Experience Platform, Journey Optimizer, Customer Journey Analytics}
---
# {Page title}

{Opening paragraph -- 1-2 sentences describing what the diagrams collectively illustrate. Frame the page as a top-level architecture reference, not a use case walkthrough.}

>[!MORELIKETHIS]
>
>[{Related-content link text}]({Related-content URL}).

## {Diagram 1 section title}

{1-2 sentence explanation of what the diagram shows and why it matters.}

<img src="assets/{filename-1}" alt="{Alt text for diagram 1}" style="border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;" class="modal-image" />

## {Diagram 2 section title}

{1-2 sentence explanation.}

<img src="assets/{filename-2}" alt="{Alt text for diagram 2}" style="border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;" class="modal-image" />

## Primary data flows and integration points

- {Flow or integration 1 -- e.g., "Real-time event ingestion from [!DNL Web SDK] to [!DNL Edge Network]"}
- {Flow or integration 2 -- e.g., "Profile sync between [!DNL Experience Platform] Hub and Edge"}
- {Flow or integration 3}
- {Flow or integration 4}
- {Flow or integration 5}

## Use case patterns supported

The architecture above supports the following use case patterns:

- [{Pattern 1 name}](/help/blueprints/use-case-patterns/{category}/{pattern-1-file}.md) -- {1-line note on why this architecture enables the pattern}
- [{Pattern 2 name}](/help/blueprints/use-case-patterns/{category}/{pattern-2-file}.md) -- {1-line note}
- [{Pattern 3 name}](/help/blueprints/use-case-patterns/{category}/{pattern-3-file}.md) -- {1-line note}

## Further reading

- [{Article 1 title}]({Experience League URL 1})
- [{Article 2 title}]({Experience League URL 2})
- [{Article 3 title}]({Experience League URL 3})
```

&#x200B;---

## Frontmatter規則

- **必要欄位：** `title`、`description`、`solution`。
- **禁止的欄位** （發佈時自動指派）： `exl-id`、`product_v2`、`feature_v2`、`role_v2`、`topic_v2`、`TQID`、`kt`、`thumbnail`。 請勿將這些檔案納入新撰寫的檔案中。

## 內文慣例

- **一個H1** — 頁面標題。 完全符合`title`前置內容。
- **每個圖表一個H2。** 圖表區段內沒有H3；請將其保留為1-2句介紹加上影像。
- **`<img>`內嵌** — 需要內嵌樣式和`class="modal-image"`。 它們會驅動Experience League強制回應縮放互動。
- **影像路徑** — 一律為`assets/{filename}` （相對於頁面的主題資料夾）。 請勿使用絕對路徑。
- **Adobe產品名稱** — 內文和專案符號會以`[!DNL ...]`換行。 範例： `[!DNL Real-Time CDP]`、`[!DNL Journey Optimizer]`、`[!DNL Experience Platform]`。
- **使用案例模式連結** — 一律使用絕對`/help/blueprints/use-case-patterns/{category}/{file}.md`表單，因此連結會從任何可能包含此內容的頁面中解析。
- **Experience League連結** — 以`https://experienceleague.adobe.com/`開頭的絕對URL。 比起本地化的變體，偏好使用標準檔案URL。

## 區段順序

在所有架構頁面上維持一致順序，讓讀者可以依預期掃描：

1. Frontmatter
2. H1 +開啟段落
3. （選用） `>[!MORELIKETHIS]`圖說文字
4. 每個圖表一個H2 （依使用者指定的順序）
5. `## Use case patterns supported`
6. `## Primary data flows and integration points`
7. `## Further reading`

## 長度預期

標準配備40到100行Markdown。 如果頁面超過150行，內容可能會漂移到使用案例模式的區域 — 重新檢查`scope-guardrails.md`並考慮分割。
