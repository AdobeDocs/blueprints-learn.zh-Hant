---
name: architecture-diagram-page-builder
description: 為Adobe Experience Platform Blueprint存放庫建立新架構圖表頁面的指南。 新增新的頂層架構圖、整合架構頁面或應用程式架構概觀時，請使用此技能。 架構頁面涵蓋頂層AEP和應用程式架構以及主要整合點，而非深入的使用案例（屬於使用案例模式產生器）。 處理完整的工作流程：收集頁面資訊、產生Markdown檔案、將其放置在正確的主題資料夾中，以及更新TOC.md。
source-git-commit: 83e85d946e455cde46001af0a2112637b7fe24cc
workflow-type: tm+mt
source-wordcount: '1396'
ht-degree: 2%

---


# 架構圖表頁面產生器

此技能可指導您為Adobe Experience Platform Blueprint存放庫建立新的架構圖表頁面。 架構圖表頁面提供AEP和Adobe應用程式如何結合、它們之間的主要資料流，以及作者在設計解決方案時需要注意的整合點的最上層視覺參考。

## 範圍

架構圖表頁面為&#x200B;**焦點、參考樣式頁面** （通常為40到100行Markdown），包含：

- 一或多個架構圖表，每個圖表的用途有簡短說明
- 架構支援的使用案例模式連結（架構頁面不會複製該內容）
- 主要資料流程和整合點的簡短清單說明
- Experience League連結，以供進一步閱讀應用程式網域

它們&#x200B;**不是**&#x200B;深入使用案例內容的位置。 KPI、業務目標、戰術使用案例範例、功能鏈和角色敘述都屬於使用案例模式頁面 — 透過`use-case-pattern-builder`技能產生。 如需完整護欄，請參閱`references/scope-guardrails.md`。

## 開始前的必要讀取

請閱讀下列範本和規則的參考檔案：

- `references/diagram-template.md` — 具有預留位置值的完整Markdown範本
- `references/toc-placement.md` — TOC.md的子區段對應表格和專案格式
- `references/scope-guardrails.md` — 屬於架構頁面與使用案例模式頁面之專案的規則

## 階段1：資訊收集

在產生任何檔案之前，詢問使用者以收集所有必要的資訊。 在提供或明確延遲每個必要專案之前，請勿繼續產生內容。

### 必要資訊

1. **頁面標題** — 人類看得懂的標題（例如，`Adobe Journey Optimizer architecture diagrams`）。

2. **主題資料夾** — 頁面所在位置。 請根據圖表的主要網域挑選一個網域：
   - `experience-platform/` — 最上層AEP、多應用程式或平台層級的圖表
   - `customer-journeys/` — AJO、行銷活動、歷程協調
   - `customer-journey-analytics/` — CJA架構
   - `audience-activation/` — RTCDP、對象和設定檔啟用
   - `b2b/` — B2B專屬架構

3. **檔案名稱** — Kebab大小寫，衍生自頁面標題（例如，`Journey Optimizer architecture` -> `journey-optimizer-architecture.md`）。 向使用者確認。

4. **頁面目的** — 1-2個句子，說明圖表整體說明的內容。 用於`description`前端內容欄位和開頭的段落。

5. **Adobe解決方案** — 頁面中心的Adobe產品清單（以逗號分隔）。 用於`solution`前端內容欄位。 範例： `Experience Platform, Journey Optimizer, Customer Journey Analytics`。

6. **圖表** — 一或多個圖表。 針對每個圖表，收集：
   - **影像檔案名稱** （例如，`aep_data_flow.svg`）。 偏好使用SVG；可接受PNG。
   - **章節標題** — 成為圖表的H2標題（例如，`Data flow diagram`、`Detailed architecture diagram`）。
   - **用途說明** — 說明圖表顯示內容的1-2個句子。
   - **替代文字** — 可存取的簡短說明。

7. **支援的使用案例模式** — 此架構可啟用2-5個現有模式。

   **請先推薦候選人。** 在要求使用者提供模式之前，請掃描`/help/blueprints/use-case-patterns/`並根據上述收集的頁面標題、頁面目的和Adobe解決方案建議3-6個可能的相符專案。 對於每個建議，請提出：
   - 圖樣名稱（含連結的路徑）
   - 一句理由說明為什麼它適合這個架構

   將建議顯示為編號短清單，並要求使用者(a)接受任何專案，(b)拒絕任何專案，以及(c)新增您錯過的模式。 僅產生指向真實檔案的建議 — 在建議之前先執行glob/read確認。 請勿產生幻覺化圖樣名稱。

   對於每個接受的模式，擷取類別和檔案名稱。 產生之前，請先驗證`/help/blueprints/use-case-patterns/{category}/{pattern-file}.md`的每個檔案是否存在。

8. **主要資料流程/整合點** — 3-7專案符號，說明跨圖表顯示的關鍵流程與整合界限（例如，`Real-time event ingestion from Web SDK to Edge Network`、`Profile synchronization between Experience Platform Hub and Edge`）。

9. **Experience League連結** — 連結3至6個相關Experience League檔案以供進一步閱讀。 每個都必須以`https://experienceleague.adobe.com/zh-hant`開頭。

   **請先推薦候選人。** 根據Adobe解決方案和頁面用途，建議可信4-8頁的Experience League文章（例如，每個命名解決方案的canonical登陸或概觀頁面、重要整合指南、部署參考）。 對於每個建議，請提出：
   - 文章標題
   - URL
   - 適合本頁原因的一行理由

   將建議標示為&#x200B;**未驗證** （除非您實際擷取URL） — 使用者必須先確認或取代每個URL，它才能進入產生的檔案。 要求使用者(a)接受、(b)以他們已有的已驗證URL取代任何URL，以及(c)新增他們自己的URL。 切勿發明您尚未看到的URL；如果您不確定，則建議使用文章標題，並讓使用者提供URL。

### 可選

- **Related-content圖說文字** — 單一連結在頁面頂端附近呈現為`>[!MORELIKETHIS]`區塊。 當Experience League上有讀者應該注意的同層級整合或設定指南時，這個功能會很有用。

如果使用者未提供所有必要的專案，請先詢問遺失的專案，然後再繼續。 請勿製作圖表、圖樣或連結。

## 階段2：範圍檢查

在產生之前，請重新閱讀使用者的圖表說明、資料流程專案符號和任何草稿散文。 從`references/scope-guardrails.md`套用護欄。

如果計畫內容中出現下列任何一項，請警告使用者和選件，將該區段重新導向至使用案例模式頁面（或從架構頁面修剪它）：

- KPI或測量公式
- 業務目標或業務影響敘述
- 戰術使用案例範例（特定的個人化案例、行銷活動範例等）
- 函式鏈（`A > B > C > D`樣式）
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
- 如果架構圖表大量記錄&#x200B;*單一使用案例端對端* （包含KPI、業務目標、功能鏈），請將使用者重新導向至`use-case-pattern-builder` — 這不是架構頁面。
