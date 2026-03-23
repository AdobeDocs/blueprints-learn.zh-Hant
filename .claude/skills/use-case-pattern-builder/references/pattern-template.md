---
source-git-commit: ef1c207922c1079117d8bd255dbfa32a1527b014
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 100%

---
# 使用案例模式範本

此檔案包含使用案例模式頁面的完整Markdown範本。 產生新模式時，以實際內容取代所有`{{placeholder}}`值。

---

## 範本

````markdown
---
title: {{Pattern Title}}
description: {{One-sentence description of what this pattern teaches}}
solution: {{Comma-separated Adobe solutions}}
exl-id: {{generate-uuid-placeholder}}
---
# {{Pattern title}}

This guide provides a comprehensive implementation blueprint for {{pattern name}} using {{solutions with [!DNL ...] formatting}}. It is designed for solution architects, marketing technologists, and implementation engineers who need to {{primary capability description}}.

Use this guide to understand what to configure, where implementation choices exist, and what trade-offs drive each decision.

{{Optional: 1-2 additional introductory sentences about what the guide covers.}}

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

## Use case pattern

**{{Pattern Name}}**

{{One-sentence description of what the pattern does.}}

**Function Chain:** {{Step 1}} > {{Step 2}} > {{Step 3}} > {{Step 4}} > {{Step 5}}

## Applications

The following Adobe applications are used in this use case pattern.

- **[!DNL {{Application Name}}] ({{Abbreviation}})** -- {{Description of the application's role in this pattern}}
- **[!DNL {{Application Name}}] ({{Abbreviation}})** -- {{Description of the application's role in this pattern}}
- **[!DNL {{Application Name}}] ({{Abbreviation}})** -- {{Description of the application's role in this pattern}}

## Foundational functions

The following foundational capabilities must be configured before implementing this pattern. Each function represents a prerequisite or assumed platform capability.

| Foundational Function | Status | What Must Be in Place | Experience League Reference |
| --- | --- | --- | --- |
| {{Function name}} | {{Required / Assumed in Place / Not Applicable}} | {{Description of what must be configured or available}} | [{{Link text}}]({{URL}}) |
| {{Function name}} | {{Required / Assumed in Place / Not Applicable}} | {{Description}} | [{{Link text}}]({{URL}}) |
| {{Function name}} | {{Required / Assumed in Place / Not Applicable}} | {{Description}} | [{{Link text}}]({{URL}}) |
| {{Function name}} | {{Required / Assumed in Place / Not Applicable}} | {{Description}} | [{{Link text}}]({{URL}}) |

## Supporting functions

The following supporting capabilities enhance or extend the pattern but are not strictly required for a basic implementation.

| Supporting Function | Status | Why It Matters | Experience League Reference |
| --- | --- | --- | --- |
| {{Function name}} | {{Recommended / Included / Not Applicable}} | {{Description of why this function matters for this pattern}} | [{{Link text}}]({{URL}}) |
| {{Function name}} | {{Recommended / Included / Not Applicable}} | {{Description}} | [{{Link text}}]({{URL}}) |
| {{Function name}} | {{Recommended / Included / Not Applicable}} | {{Description}} | [{{Link text}}]({{URL}}) |

## Application functions

### [!DNL {{Application Name}}] ({{Abbreviation}})

| Function | Implementation Phase | Description |
| --- | --- | --- |
| {{Function name}} | {{Phase name (e.g., Setup, Configuration, Activation, Optimization)}} | {{Description of what this function does in context}} |
| {{Function name}} | {{Phase name}} | {{Description}} |
| {{Function name}} | {{Phase name}} | {{Description}} |

### [!DNL {{Application Name}}] ({{Abbreviation}})

| Function | Implementation Phase | Description |
| --- | --- | --- |
| {{Function name}} | {{Phase name}} | {{Description}} |
| {{Function name}} | {{Phase name}} | {{Description}} |
| {{Function name}} | {{Phase name}} | {{Description}} |

{{Repeat for each application listed in the Applications section.}}

## Prerequisites

Complete the following before beginning the implementation.

- [ ] {{Prerequisite item -- e.g., "XDM schemas for behavioral and profile data are defined and deployed"}}
- [ ] {{Prerequisite item -- e.g., "Datastreams are configured for web and/or mobile properties"}}
- [ ] {{Prerequisite item -- e.g., "Identity namespaces are defined and identity resolution rules are configured"}}
- [ ] {{Prerequisite item -- e.g., "Merge policies are configured for the target profile dataset"}}
- [ ] {{Prerequisite item -- e.g., "Required Adobe product licenses are provisioned and sandbox access is granted"}}
- [ ] {{Prerequisite item}}

## Implementation options

### Option A: {{Option name}}

**Best for:** {{One-sentence description of when to use this option}}

**How it works:**

{{Paragraph 1: Describe the overall approach and architecture of this option.}}

{{Paragraph 2: Describe the key configuration steps or workflow.}}

{{Paragraph 3 (optional): Describe any runtime behavior or execution model.}}

{{Paragraph 4 (optional): Describe monitoring, reporting, or optimization considerations.}}

**Key considerations:**

- {{Consideration about timing, latency, or throughput}}
- {{Consideration about data requirements or dependencies}}
- {{Consideration about channel support or limitations}}
- {{Consideration about governance or compliance}}

**Advantages:**

- {{Advantage of this approach}}
- {{Advantage of this approach}}
- {{Advantage of this approach}}

**Limitations:**

- {{Limitation or trade-off}}
- {{Limitation or trade-off}}
- {{Limitation or trade-off}}

**Experience League:**

- [{{Link text}}]({{URL}})
- [{{Link text}}]({{URL}})

### Option B: {{Option name}}

**Best for:** {{One-sentence description of when to use this option}}

**How it works:**

{{Paragraph 1: Describe the overall approach and architecture of this option.}}

{{Paragraph 2: Describe the key configuration steps or workflow.}}

**Key considerations:**

- {{Consideration}}
- {{Consideration}}

**Advantages:**

- {{Advantage}}
- {{Advantage}}

**Limitations:**

- {{Limitation}}
- {{Limitation}}

**Experience League:**

- [{{Link text}}]({{URL}})

{{Repeat for Options C, D as needed. Include 2-4 options total.}}

### Option comparison

| Criteria | Option A | Option B | Option C |
| --- | --- | --- | --- |
| Best for | {{description}} | {{description}} | {{description}} |
| Complexity | {{Low / Medium / High}} | {{Low / Medium / High}} | {{Low / Medium / High}} |
| Time to value | {{Fast / Moderate / Slow}} | {{Fast / Moderate / Slow}} | {{Fast / Moderate / Slow}} |
| Channel support | {{description}} | {{description}} | {{description}} |
| Personalization depth | {{description}} | {{description}} | {{description}} |
| Scalability | {{description}} | {{description}} | {{description}} |
````

---

## 使用此範本的相關附註

- **YAML frontmatter：** `exl-id`應為預留位置UUID （例如，`xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx`）。 發佈管道會指定實際值。
- **Adobe產品名稱：**&#x200B;在正文和表格中，一律使用Adobe產品名稱的`[!DNL ...]`語法（例如`[!DNL Journey Optimizer]`）。 這是Experience League的慣例，可防止產品名稱的翻譯。
- **商業目標連結：**&#x200B;使用從模式檔案到商業目標目錄的相對路徑： `../../business-objectives/{{category}}/{{filename}}.md`。
- **Kebab-case檔案名稱：**&#x200B;模式檔案名稱必須是衍生自模式標題的Kebab-case。 範例：「事件觸發訊息」變成`event-triggered-messaging.md`。
- **函式鏈：**&#x200B;使用` > ` （空格、大於空格）作為步驟之間的分隔符號。
- **狀態值：**&#x200B;基礎函式使用：必要、已假設就緒、不適用。 支援函式使用：建議、包含、不適用。
- **實作階段：**&#x200B;常用階段名稱包括：設定、設定、啟動、最佳化、監視。
- **先決條件：**&#x200B;每個專案使用`- [ ]`核取方塊語法。
