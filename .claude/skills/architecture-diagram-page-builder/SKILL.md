---
name: architecture-diagram-page-builder
description: 為Adobe Experience Platform Blueprint存放庫建立新架構圖表頁面的指南。 新增新的頂層架構圖、整合架構頁面或應用程式架構概觀時，請使用此技能。 架構頁面涵蓋頂層AEP和應用程式架構以及主要整合點，而非深入的使用案例（屬於使用案例模式產生器）。 處理完整的工作流程：收集頁面資訊、產生Markdown檔案、將其放置在正確的主題資料夾中，以及更新TOC.md。
source-git-commit: 4d236750286c28a8b8eb53a5bdec0645cc0e3e91
workflow-type: tm+mt
source-wordcount: '1556'
ht-degree: 1%

---


# 架構圖表頁面產生器

此技能可指導您為Adobe Experience Platform Blueprint存放庫建立新的架構圖表頁面。 架構圖表頁面提供AEP和Adobe應用程式如何結合、它們之間的主要資料流，以及作者在設計解決方案時需要注意的整合點的最上層視覺參考。

## 範圍

架構圖表頁面為&#x200B;**焦點、參考樣式頁面** （通常為40到100行Markdown），包含：

- 一或多個架構圖表，每個圖表的用途有簡短說明
- 架構支援的使用案例模式連結（架構頁面不會複製該內容）
- 主要資料流程和整合點的簡短清單說明
- Experience League連結，以供進一步閱讀應用程式網域

它們&#x200B;**不是**&#x200B;深入使用案例內容的位置。 KPI、業務目標、戰術使用案例範例、功能和角色敘述都屬於使用案例模式頁面 — 透過`use-case-pattern-builder`技能產生。 如需完整護欄，請參閱`references/scope-guardrails.md`。

## 開始前的必要讀取

請閱讀下列範本和規則的參考檔案：

- `references/diagram-template.md` — 具有預留位置值的完整Markdown範本
- `references/toc-placement.md` — TOC.md的子區段對應表格和專案格式
- `references/scope-guardrails.md` — 屬於架構頁面與使用案例模式頁面之專案的規則

## 階段1：資訊收集

**使用表單，而非線性面試。** 透過以邏輯批次化回合呈現`AskUserQuestion`表單，而不是一次詢問一個問題來收集所有必要資訊。 這可讓使用者快速且快速地進行瀏覽。

### AskUserQuestion限制

- 每個`AskUserQuestion`呼叫最多&#x200B;**4個問題**。
- 每個問題最多&#x200B;**4個選項**。
- 如果問題的可能選項超過4個，請將其分割為兩個呼叫（例如，詢問前4個選項，然後在第五個選項中輸入「是/否」）。
- 針對套用多個答案（解決方案、模式、資料流程）的問題，請使用`multiSelect: true`。

### 第1回合 — 核心頁面資訊（一個AskUserQuestion呼叫，最多4個問題）

請以單一表單要求下列所有專案：

1. **頁面標題** — 顯示2-3個建議變體，衍生自使用者已告訴您的內容，加上一個「其他」逸出影格。
2. **主題資料夾** — 將5個有效的資料夾顯示為選項；根據使用者的輸入建議最有可能的資料夾。
3. **Adobe解決方案** — 多選；根據頁面主題建議最可能的候選人。
4. **圖表計數** — 頁面將包含多少圖表(1 / 2 / 3 / 4+)。

### 第2回合 — 圖表詳細資料（一個AskUserQuestion呼叫，最多4個問題）

以單一形式詢問每個圖表的影像檔案名稱和頁面用途：

- 對於每個圖表（單一表單圓圈最多2個），詢問&#x200B;**影像檔案名稱**&#x200B;的問題包含2-3個建議的檔案名稱（衍生自頁面標題）加上「其他」選項。
- 詢問&#x200B;**頁面目的** （1-2句描述）為帶有2-3個建議短語加上「其他」的問題。
- 詢問是否需要&#x200B;**`>[!MORELIKETHIS]`圖說文字** （是/否）。 如果是「是」，則收集URL並在後續訊息中連結文字。

> **區段標題和替代文字：**&#x200B;當影像檔案名稱是描述性的（例如，`fac-architecture.svg`、`fac-dataflow.svg`）時，從其中推斷H2區段標題和替代文字 — 您不需要詢問使用者。 使用檔案名稱主體、標題化及人性化，作為章節標題（例如，`Architecture diagram`、`Data flow diagram`）。 只詢問檔案名稱是否模稜兩可。

### 第3回合 — 使用案例模式（掃描後詢問使用者問題）

在展示此表單之前，**glob`/help/blueprints/use-case-patterns/`**&#x200B;會根據頁面標題、用途和解決方案，識別3-5個可能的相符模式。 建議檔案之前，請先確認每個檔案都存在。

將前4名候選人列為`multiSelect`個問題。 如果第五個候選者較強，請針對該候選者另外提出「是/否」問題。 同時邀請使用者為您遺漏的任何模式命名。

僅包含已確認存在檔案的模式。 請勿產生幻覺化圖樣名稱。

### 第4回合 — 資料流程和Experience League連結（一個AskUserQuestion呼叫）

**資料流程：**&#x200B;建議3-5個預先寫入的資料流程專案符號做為`multiSelect`個問題（衍生自頁面主題）。 使用者選擇適用的專案。 將每個選項保留為一個簡潔的句子。 如果使用者需要不在您清單中的自訂流程，他們可以在後續中提供這些流程。

**Experience League連結：**&#x200B;在表單之後，呈現包含4-6個建議連結的Markdown表格，內含文章標題、URL和單行基本原則。 將每個URL標籤為&#x200B;**未驗證**。 要求使用者(a)接受、(b)取代為已驗證的URL，或(c)新增他們自己的URL。 如果清單很長，請使用最多4個選項的後續追蹤`AskUserQuestion`；否則請接受純文字的確認。

切勿建立您尚未擷取的URL。 如果不確定，則建議文章標題，並讓使用者提供URL。

### 完成所有倒圓角時

在產生任何檔案之前，請確認與使用者設定的完整資訊。 如果仍然遺失任何必要專案或將其標示為「其他」但沒有值，請先詢問該專案，然後再繼續。 請勿製作圖表、圖樣或連結。

## 階段2：範圍檢查

在產生之前，請重新閱讀使用者的圖表說明、資料流程專案符號和任何草稿散文。 從`references/scope-guardrails.md`套用護欄。

如果計畫內容中出現下列任何一項，請警告使用者和選件，將該區段重新導向至使用案例模式頁面（或從架構頁面修剪它）：

- KPI或測量公式
- 業務目標或業務影響敘述
- 戰術使用案例範例（特定的個人化案例、行銷活動範例等）
- 功能（`A > B > C > D`樣式）
- 角色導向的storytelling

如果規劃的內容仍在架構頁面範圍內（頂層架構、系統資料流程、整合點、部署拓撲、邊緣與中樞），請與使用者確認並繼續進行階段3。

## 階段3：內容產生

產生頁面於：

```
/help/blueprints/{topic-folder}/{kebab-filename}.md
```

使用`references/diagram-template.md`做為來源範本。 使用收集的資訊填入所有預留位置值。 產生的檔案必須包括：

1. **YAML frontmatter** — 僅限`title`、`description`、`solution`。
   - **不包括`exl-id`** — 發佈管道會自動指派它。
   - **不包含** `product_v2`、`feature_v2`、`role_v2`、`topic_v2`、`TQID`、`kt`或`thumbnail` — 這些也會自動填入。

2. **H1標題** — 頁面標題。

3. **開啟段落** — 從頁面目的輸入衍生出1-2個句子。

4. **選擇性`>[!MORELIKETHIS]`區塊** — 只有在使用者提供相關內容連結時。

5. **每個圖表一個H2區段** — 依使用者提供的順序排列。 每個區段都包含：
   - 區段標題作為H2標題
   - 說明圖表用途的1-2個句子
   - 使用標準慣例嵌入影像：

     ```html
     <img src="assets/{filename}" alt="{Alt Text}" style="border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;" class="modal-image" />
     ```

6. **`## Use case patterns supported`** — 專案符號清單。 每個專案符號：

   ```
   - [{Pattern name}](/help/blueprints/use-case-patterns/{category}/{pattern-file}.md) -- {1-line note on why this architecture enables the pattern}
   ```

7. **`## Primary data flows and integration points`** — 3-7個流量/整合專案的專案符號清單。

8. **`## Further reading`** — Experience League連結的專案符號清單：

   ```
   - [{Article title}]({Experience League URL})
   ```

在內文和專案符號中使用`[!DNL ...]`語法作為Adobe產品名稱，符合現有頁面的慣例。

## 階段4：對照參考更新

更新&#x200B;**`/help/blueprints/TOC.md`**&#x200B;以將新頁面加入導覽。 這是唯一要更新的互動參照頁面。

讀取完整子區段對應表格和規則的`references/toc-placement.md`。 摘要：

| 主題資料夾 | TOC子區段 |
| --- | --- |
| `experience-platform/` | `+ Architecture overviews{#architecture-overview}` |
| `experience-platform/deployment/` | `+ Deployment{#deployment}` （架構概觀的子區段） |
| `audience-activation/` | `+ Audience & Profile Activation{#audience-activation}` |
| `b2b/` | `+ B2B activation & marketing{#b2b-activation}` |
| `customer-journey-analytics/` | `+ Customer Journey Analytics{#customer-journey-analytics}` |
| `customer-journeys/` | `+ Customer journeys{#customer-journeys}` |

專案格式（4空格縮排+ `+`）：

```
    + [{Page title}](/help/blueprints/{topic-folder}/{filename}.md)
```

除非使用者指定不同的位置，否則將新專案附加為相符子區段中的最後一個專案。 保留精確的4空格縮排 — 目錄剖析取決於此縮排。

**放置之前先檢查巢狀子群組。** 某些子區段（尤其是`Audience & Profile Activation`）包含巢狀群組（例如，`Real-Time Customer Data Platform (RTCDP) {#known-customer-audience-activation}`）。 編輯前請先閱讀TOC.md中受影響的子區段。 新的頂層架構頁面屬於子區段的4空格縮排層級 — **not**&#x200B;在巢狀子群組內（使用6空格縮排）。 將新專案放在最後一個巢狀子群組專案的後面，並放在下一個頂層子區段標題之前。

## 階段5：驗證

建立並更新所有檔案後，請確認下列事項，並向使用者報告任何失敗情況：

1. **影像資產是否存在** — 請檢查每個圖表是否存在`/help/blueprints/{topic-folder}/assets/{filename}`。 **如果遺失則警告**；請勿封鎖（使用者可能正在與圖表設計並行撰寫）。 顯示清晰的遺失檔案清單，讓使用者知道要新增什麼。

2. **使用案例模式連結** — 檔案中的每個模式連結都指向`/help/blueprints/use-case-patterns/`下的現有Markdown檔案。 使用`Read`或glob確認每個目標都存在。

3. **Experience League連結** — 抽查`## Further reading`區段中的每個URL是否都以`https://experienceleague.adobe.com/zh-hant`開頭。

4. **TOC專案位置** — 新專案位於正確的子區段中，使用4個空格縮排，而且路徑與產生的檔案位置完全相符。

5. **檔案命名** — 頁面檔案名稱為大寫，並符合TOC.md中參照的路徑。

6. **Frontmatter完整性** — 頁面包含`title`、`description`和`solution`。 它必須&#x200B;**不**&#x200B;包含`exl-id`、`product_v2`、`feature_v2`、`role_v2`、`topic_v2`、`TQID`、`kt`或`thumbnail`。

在考量任務完成之前，請先修正任何驗證問題。

## 附註

- 請一律遵循現有頁面的慣例，在內文和專案符號中使用`[!DNL ...]`語法作為Adobe產品名稱。
- 架構圖表通常是SVG （偏好使用清晰度和縮放功能），但點陣來源圖稿可以接受PNG。
- 需要`<img>`內嵌內嵌樣式字串(`border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;`)和`class="modal-image"` — 它們會啟用Experience League強制回應縮放互動。
- 如果使用者正在建立全新主題資料夾尚不存在的頁面，請警告他們TOC.md在`+ Architecture Diagrams and Blueprints{#architecture-diagrams}`下需要新的頂層子區段。 將此作為單獨的步驟處理，並取得使用者的明確核准。
- 如果架構圖表大量記錄&#x200B;*單一使用案例端對端* （包含KPI、業務目標、功能），請將使用者重新導向至`use-case-pattern-builder` — 這不是架構頁面。
