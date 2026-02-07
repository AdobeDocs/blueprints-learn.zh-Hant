---
source-git-commit: dfa21942ecf2a1db06df6f6cc945f5572811ca93
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 1%

---
# Blueprint檔案參考 — 詳細指南

## 檔案型別

| 型別 | 用途 | 位置/範例 |
|------|---------|--------------------|
| **總覽/集線器** | 介紹產品或區域；情境藍圖的連結 | 例如`overview.md`， `journey-optimizer-overview.md` |
| **情境藍圖** | 單一使用案例：架構、步驟、護欄 | 例如`real-time-lookup.md`， `journey-optimizer-journeys.md` |
| **目錄** | 導覽；請勿作為內容範本使用 | `help/blueprints/TOC.md` |

---

## 完整章節參考資料

### 標題和說明（前置內容）

- **title**：簡短且具體。 使用`[!DNL Product Name]`作為產品名稱（例如`[!DNL Journey Optimizer]`）。
- **描述**：一句話。 說明藍圖顯示的內容和結果（例如「在邊緣存取即時客戶個人檔案，以進行網頁和行動個人化」）。

### 內文區段

| 章節 | 何時加入 | 內容指引 |
|---------|-----------------|-------------------|
| **應用程式** | 永遠用於情境Blueprint | 相關的Adobe產品/解決方案專案符號清單（例如Real-time Customer Data Platform、資料收集）。 |
| **使用案例** | 一直 | 此Blueprint支援的業務/技術使用案例專案符號清單。 |
| **必要條件** | 需要設定時 | 產品、子網域、SDK、設定必須到位。 連結至Experience League以取得設定步驟。 |
| **架構圖** | 一直 | 單一主要圖表(偏好使用SVG)。 使用一致的樣式： `style="width:90%; border:1px solid #4a4a4a" class="modal-image"`。 提供有意義的`alt`文字。 |
| **護欄** | 產品有護欄時一律如此 | 連結至官方Experience League護欄頁面。 將Blueprint的特定限制（例如TTL、速率限制）新增為專案符號。 |
| **實作模式** | 存在多個方法時 | 命名每個模式(例如「模式1：以網頁SDK為基礎的對象成員資格」)；使用專案符號來表示何時使用和取捨。 |
| **實作步驟** | 適用於已定義路徑的情境Blueprint | 編號清單。 每個步驟：動作+程式所在的Experience League連結。 請勿複製完整程式。 |
| **實作考量事項** | 當有重要警告時 | 子區段（例如身分考量、以屬性為基礎的個人化）。 專案符號或簡短段落；連結以取得深度。 |
| **相關檔案** | 一直 | Experience League的群組連結(以及選用的developer.adobe.com)。 請參閱下方的「Experience League連結群組」。 |

### 概觀/中心頁面

- 從有關產品/區域以及Blueprint涵蓋內容的1-2個段落開始。
- **使用案例**：可以針對多個類別使用`>[!BEGINTABS]` / `>[!TAB ...]` / `>[!ENDTABS]`。
- **架構**：一個主要圖表。
- **藍圖藍圖**&#x200B;或&#x200B;**整合模式**：包含藍圖藍圖的藍圖名稱、簡短說明和連結的表格。
- **必要條件**，**護欄**，**相關檔案**：與上述內容相同；請保持簡潔。

---

## Adobe Experience League — 代理程式指引

### 何時參照Experience League

- **產品檔案**：產品的運作方式、UI流程、概念。
- **API**：端點、引數、範例(Experience Platform、Edge等)。
- **護欄**：產品或服務的官方護欄頁面。
- **教學課程**：逐步指南（例如建立結構描述、啟用目的地）。
- **設定**：資料串流、目的地、合併原則、身分等等。

請勿將Experience League中的長時間程式貼到Blueprint中。 摘要並連結。

### URL模式

| 內容類型 | 基礎URL | 範例路徑 |
|--------------|----------|--------------|
| Experience Platform檔案 | `https://experienceleague.adobe.com/docs/experience-platform/` | `.../profile/home.html`，`.../destinations/catalog/...` |
| Experience League (en) | `https://experienceleague.adobe.com/en/docs/` | 與`/en/`的上述結構相同。 |
| Journey Optimizer | `https://experienceleague.adobe.com/docs/journey-optimizer/` | `.../using/get-started/guardrails.html` |
| Web SDK | `https://experienceleague.adobe.com/docs/experience-platform/web-sdk/` | `.../home.html`，`.../commands/command-responses.html` |
| Edge Network伺服器API | `https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/` | `.../overview.html`，`.../guardrails.html` |
| Mobile SDK | `https://developer.adobe.com/client-sdks/` | `.../home/`，`.../edge/adobe-journey-optimizer-decisioning/` |
| 標記 | `https://experienceleague.adobe.com/docs/experience-platform/tags/` | `.../home.html` |
| 平台教學課程 | `https://experienceleague.adobe.com/docs/platform-learn/tutorials/` | `.../profiles/create-merge-policies.html` |

使用與目前Experience League網站相符的規範路徑（已知英文路徑時偏好使用`/en/docs/`）。

### Markdown中的連結格式

- **描述性連結文字**： `[Create schemas](https://experienceleague.adobe.com/...)`不是「按一下這裡」。
- **文字中的產品名稱**：使用每個Adobe樣式的`[!DNL Product Name]` （例如`[!DNL Real-time Customer Profile]`）。
- **外部連結**：只有在範本或管道需要時才新增`{target="_blank"}` （檢查存放庫中的現有Blueprint）。

### 相關檔案 — 建議的群組

套用時請使用這些群組：

1. **目的地設定** （用於啟用/邊緣個人化藍圖）
2. **SDK檔案** (網頁SDK、行動SDK、Edge Network伺服器API、標籤)
3. **設定檔和區段** （即時客戶設定檔、合併原則、區段）
4. **教學課程** （平台學習或產品特定逐步指南）
5. **產品檔案** （主要產品檔案首頁或主要子區段）
6. **護欄** （若尚未在護欄區段中）

範例：

```markdown
## Related documentation

### Destination configurations
* [Custom Personalization Connection](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/custom-personalization)
* [Activate audiences to edge personalization destinations](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations)

### SDK documentation
* [Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/home.html)
* [Edge Network Server API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html)

### Profile and segmentation
* [Real-time Customer Profile](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html)
* [Profile Guardrails](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html)
```

---

## 存放庫與目錄

- **Blueprint內容路徑**： `help/blueprints/` （具有依區域的子資料夾，例如`audience-activation/`、`customer-journeys/journey-optimizer/`）。
- **Assets**：與Blueprint共同找到（例如`assets/`、`images/`）或在共用資料夾中（例如`experience-platform/assets/`）。
- **目錄**：新增、重新命名或移動Blueprint頁面時編輯`help/blueprints/TOC.md`。 保留frontmatter (`user-guide-title`， `breadcrumb-title`， `user-guide-description`， `product`， `mini-toc-levels`， `role`)和`+`階層。

---

## 此存放庫中的參考範例

- **情境藍圖（長格式）**： `help/blueprints/audience-activation/real-time-lookup.md`
- **索引標籤和資料表的概觀/中心**： `help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-overview.md`
- **以護欄為中心**： `help/blueprints/experience-platform/guardrails.md`
- **導覽**： `help/blueprints/TOC.md`，`help/blueprints/overview.md`

使用這些做為區段順序、Frontmatter、圖表放置和Experience League連結使用方式的模式。
