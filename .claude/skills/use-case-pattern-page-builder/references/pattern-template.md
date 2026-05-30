---
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 48%

---
# 使用案例模式範本

此檔案包含使用案例模式頁面的完整Markdown範本。 產生新模式時，以實際內容取代所有`{{placeholder}}`值。

&#x200B;---

## 範本

````markdown
---
title: {{Pattern Title}}
description: {{One-sentence description of what this pattern teaches}}
solution: {{Comma-separated Adobe solutions}}
exl-id: {{generate-uuid-placeholder}}
---
# {{Pattern title}}

This guide provides an overview of {{pattern name}} using {{solutions with [!DNL ...] formatting}}. It is designed for solution architects, marketing technologists, and implementation engineers who need to {{primary capability description}}.

## Use case pattern

**{{Pattern Name}}**

{{One-two sentence description of what the pattern does and enables.}}

**Execution plan:** {{Step 1}} > {{Step 2}} > {{Step 3}} > {{Step 4}} > {{Step 5}}

## Use case overview

{{Paragraph 1: Define the pattern. What does it do? How does it differ from related patterns? Provide a clear, specific definition.}}

{{Paragraph 2: Describe the typical trigger or starting condition. When does this pattern apply? What event, schedule, or condition initiates it?}}

{{Paragraph 3: Describe what the pattern delivers. What is the end result for the customer or business? What channels or touchpoints does it affect?}}

{{Paragraph 4: Clarify scope boundaries. What does this pattern NOT cover? What adjacent patterns handle those needs? Reference other patterns by name if relevant.}}

{{Paragraph 5 (optional): Identify typical stakeholders and teams involved in implementation. Who owns what?}}

## Key business objectives

The following business objectives are supported by this use case pattern.

**[{{Objective Name}}](../../business-objectives/{{category}}/{{objective-file}}.md)**

{{Brief description of how this pattern supports the objective -- 1-2 sentences.}}

| KPIs |
| --- |
| {{KPI1}}, {{KPI2}}, {{KPI3}} |

{{Repeat the above block for each supported business objective.}}

## Example tactical use cases

The following scenarios illustrate how {{pattern name}} can be applied across different business contexts.

- **{{Scenario name}}** -- {{Description of the scenario and how it uses this pattern}}
- **{{Scenario name}}** -- {{Description}}
- **{{Scenario name}}** -- {{Description}}
- **{{Scenario name}}** -- {{Description}}
- **{{Scenario name}}** -- {{Description}}
- **{{Scenario name}}** -- {{Description}}
{{Include 6-10 scenarios total}}

## Key performance indicators

| KPI | Description | Measurement |
| --- | --- | --- |
| {{KPI Name}} | {{What it measures}} | {{Formula or measurement approach}} |
| {{KPI Name}} | {{What it measures}} | {{Formula or measurement approach}} |
| {{KPI Name}} | {{What it measures}} | {{Formula or measurement approach}} |
| {{KPI Name}} | {{What it measures}} | {{Formula or measurement approach}} |
| {{KPI Name}} | {{What it measures}} | {{Formula or measurement approach}} |

## Applications

The following Adobe applications are used in this use case pattern.

- **[!DNL {{Application Name}}] ({{Abbreviation}})** -- {{Description of the application's role in this pattern}}
- **[!DNL {{Application Name}}] ({{Abbreviation}})** -- {{Description of the application's role in this pattern}}
- **[!DNL {{Application Name}}] ({{Abbreviation}})** -- {{Description of the application's role in this pattern}}

## Related documentation

The following resources provide additional detail on the capabilities used in this pattern. Group the reference links to primary Experience League documents under descriptive subheadings.

### {{Topic group}}

- [{{Link text}}]({{URL}})
- [{{Link text}}]({{URL}})

### {{Topic group}}

- [{{Link text}}]({{URL}})
- [{{Link text}}]({{URL}})
````

&#x200B;---

## 使用此範本的相關附註

- **YAML frontmatter：** `exl-id`應為預留位置UUID （例如，`xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx`）。 發佈管道會指定實際值。
- **區段順序：** `Use case pattern`區段緊接在開頭的簡介之後，在`Use case overview`之前。 它讓讀者擁有清晰的單行定義，以及預先的高階執行計畫。
- **Adobe產品名稱：**&#x200B;在正文和表格中，一律使用Adobe產品名稱的`[!DNL ...]`語法（例如`[!DNL Journey Optimizer]`）。 這是Experience League的慣例，可防止產品名稱的翻譯。
- **商業目標連結：**&#x200B;使用從模式檔案到商業目標目錄的相對路徑： `../../business-objectives/{{category}}/{{filename}}.md`。
- **Kebab-case檔案名稱：**&#x200B;模式檔案名稱必須是衍生自模式標題的Kebab-case。 範例：「事件觸發訊息」變成`event-triggered-messaging.md`。
- **執行計畫：**&#x200B;使用` > ` （空格、大於、空格）作為步驟之間的分隔符號。 保留標籤正好`**Execution plan:**`。
- **相關檔案：**&#x200B;描述性`###`子標題下的群組參考連結（例如，依應用程式或功能區域）。 這些是模式中所使用應用程式和功能的Experience League參考。
- **架構（選擇性）：**&#x200B;如果模式受益於參考架構圖表，則可以在`Applications`和`Related documentation`之間放置選擇性的`## Architecture`區段。
- **範圍：**&#x200B;此範本特意排除詳細的實作區段（基礎/支援/應用程式功能、先決條件、實作選項及分階段實作步驟）。 這些詳細資料已存在於從`Related documentation`連結的Experience League檔案中。