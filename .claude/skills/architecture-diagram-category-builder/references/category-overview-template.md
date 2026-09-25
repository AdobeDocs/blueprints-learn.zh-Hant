---
source-git-commit: e0ecfa4d74b8fcc0bbaf35d44c33c725a1b1a539
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%
---
# 類別overview.md範本

`help/blueprints/architecture-diagrams/`下的每個類別資料夾都需要看起來像其他五個的`overview.md`。 請使用此確切的結構。

## Frontmatter

```yaml
---
title: {Category Label}
description: {One-sentence summary of what this category covers.}
solution: {Primary Adobe solution(s), comma-separated}
doc-type: overview-page
---
```

不要在新頁面上包含`exl-id`、`product_v2`、`feature_v2`、`role_v2`、`topic_v2`、`TQID`、`kt`或`thumbnail` — 發佈管道會自動填入這些專案。

## 內文

```markdown
# {Category Label}

{1-3 paragraph intro describing what this category of diagrams covers and why it matters.}

| Diagram | Description |
| --- | --- |
| [{Page title}]({filename}.md) | {One-sentence description of the page} |
| [{Page title}]({filename}.md) | {One-sentence description of the page} |
```

規則：

- 列出類別中的每個頁面，其順序與在TOC.md中的順序相同。
- 連結目標是相對檔案名稱（無`/help/blueprints/...`首碼），因為概觀與其同層級頁面並存。
- 說明是一句話，如果讀起來像標籤，則不需要結尾句號。
- 如果類別有自然的子群組（例如，客戶歷程底下的「已棄用的圖表」），請以相同格式新增`## {Sub-group name}`標題，後面接著自己的兩欄表格 — 請勿在表格中混合圖表縮圖或額外的欄。
- 請勿在此資料表中內嵌`<img>`圖表縮圖。 保留為兩欄： `Diagram` （連結）和`Description` （文字）。 縮圖屬於個別內容頁面，而非類別概觀。
- 請勿在表格儲存格內使用巢狀`<ul><li>` HTML。 僅限純文字。

## 範例（客戶分析）

```markdown
---
title: Customer Insights
description: Unify and analyze data and customer behaviors from across the customer journey
solution: Customer Journey Analytics
doc-type: overview-page
---
# Customer Insights

Customer Journey Analytics shows how brands can unify customer data and behavior from various interaction channels and sources to create a journey-based view of all customer interactions.

| Diagram | Description |
| --- | --- |
| [Adobe Customer Journey Analytics](cja.md) | Core Customer Journey Analytics architecture, including B2B and audience-sharing derivations |
| [Adobe Customer Journey Analytics & Adobe Journey Optimizer integration](cja-ajo-integration.md) | Campaign and journey insights integration between Customer Journey Analytics and Journey Optimizer |
```
