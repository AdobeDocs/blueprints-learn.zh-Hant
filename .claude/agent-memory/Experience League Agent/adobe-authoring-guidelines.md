---
name: Adobe Experience League Authoring Guidelines
description: Adobe Experience League Markdown撰寫規則的完整參考，於2026年3月從官方撰寫指南抓取。
type: reference
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '1664'
ht-degree: 0%

---


# Adobe Experience League編寫指南

Source： https://experienceleague.adobe.com/en/docs/authoring-guide/using/home
已抓取：2026-03-15

&#x200B;---

## &#x200B;1. 中繼資料/正面內容

### 必填欄位
| 欄位 | 需求 | 規則 |
|---|---|---|
| `title` | 必填 | 最多60個字元（英文）。 字首大寫。 除非為了清楚起見，否則不要使用產品名稱。 系統附加» | 「ProductName」自動建立。 如果包含冒號或括弧，請用引號括住。 |
| `description` | 必填 | 最多150-160個字元 不得空白/空值。 概念會從「瞭解……」開始 任務開始「瞭解如何……」 或命令式動詞。 |

### 選擇性但經常使用的欄位
| 欄位 | 有效值 | 附註 |
|---|---|---|
| `feature` | 必須符合功能YAML值；標題大小寫有空格（例如「Content Fragment」） | 每篇文章1-2；顯示在主題中 |
| `feature-set` | 必須針對功能YAML進行驗證 | 功能的父項應用程式 |
| `role` | 使用者、開發人員、負責人、管理員、架構師、資料架構師、資料工程師 | 區分大小寫；顯示為「Created for」 |
| `level` | 初學者，中級，經驗豐富 | 如果未指定，則預設為初學者 |
| `solution` | 必須符合解決方案YAML （例如「Campaign、Campaign Standard v7」） | 允許多個值；用於搜尋篩選 |
| `topic` | 必須符合主題YAML；標題大小寫含空格 | 適用於跨產品篩選（例如「整合」） |
| `type` | 檔案，教學課程，疑難排解 | 存放庫層級；預設為檔案 |
| `short-description` | 一個句子，最多20個字 | 適用於說明太長的ExL登陸頁面 |
| `badgePremium` | `label="Premium" type="Positive" url="..."` | 頁面層級徽章 |
| `mini-toc-levels` | 1-6 （預設值2） | 控制右導覽標題顯示深度 |
| `hidefromtoc` | true/false | 從左側導覽中排除，但可存取URL |

### 中繼資料位置
- 文章層級：Markdown檔案頂端，作為YAML前置專案
- TOC層級： TOC.md檔案中
- 存放庫層級：在metadata.md檔案中

### 關鍵格式規則
- 以引號括住包含逗號或方括弧的值
- 多個值，以逗號分隔
- 區分大小寫，符合YAML定義
- 空白/空白標籤值會導致驗證失敗

### 已棄用的欄位
seo-title， seo-description，對象，難度， uuid （來自移轉時代）

&#x200B;---

## &#x200B;2. MARKDOWN語法（ADOBE風格）

### 文字格式
- 粗體： `**text**`
- 斜體： `*text*`
- 粗體+斜體： `***text***`
- 逸出特殊字元：在`# { } [ ] * + - . !`之前使用反斜線`\`
- HTML實體： `&lt;` `&gt;` `&amp;` `&mdash;` `&ndash;`

### 標題
- 使用ATX樣式（僅限`#`語法，請勿加底線/文字樣式）
- 每個檔案一個H1 （通常是頁面標題符合中繼資料`title`）
- 所有後續標題H2 (`##`)或以下
- 標題前後所需的空白行（第一個標題除外）
- 最多69個字元（英文） / 120個字元（當地語系化）
- 最多可選擇5個字
- 所有標題的句子大小寫（僅首字大寫和專有名詞）
- 只有`title`中繼資料欄位的字首大寫
- 無結尾標點符號（常見問答集標題允許問號）
- 自訂錨點ID： `## Title {#custom-id}` — 使用連字型大小，而非句點
- 檔案中沒有重複的標題錨點ID
- 避免保留的錨點名稱：搜尋、結果、多面向、分頁、排序、查詢、搜尋方塊、內容、頁首、頁尾、主要、導覽、側欄、頁面、容器、包裝函式
- 每個標題後面至少要有一個內文段落（請勿將清單/表格直接放在標題後面）
- 概念標題：名詞/名詞片語
- 任務標題：命令式動詞（非動名詞 — 「建立區段」而非「建立區段」）
- 橫跨標題層級的平行結構

### 清單
- 專案符號（未排序）： `*`、`-`或`+` — 在檔案中使用方式一致
- 已訂購：每個專案（自動編號）有`1.`
- 清單前後的空白行
- 縮排巢狀編號專案3個空格；巢狀專案符號2個空格
- 專案符號標點：在結尾省略分號/逗號/連結；僅為完整句子新增句號
- 如果所有專案都是≤3個單字或UI標籤/標題，請勿新增句號

### 連結
- 外部： `[text](https://url.com)`
- 相對（相同層級）： `[text](file.md)`
- 根相對： `[text](/help/path/file.md)` — 必須以`/`開頭
- 深層連結（相同頁面）： `[text](#heading-anchor)`
- 跨檔案深層連結： `[text](file.md#heading-id)`
- 強制新標籤： `[text](url){target="_blank"}`
- 空的URL：以角括弧`<https://example.com>`括住，使其可點選
- 參考連結：只有絕對連結才能用於參考樣式連結
- 請勿透過相對連結將相同檔案包含在多個TOC位置中
- Windows使用者：將路徑中的反斜線轉換為正斜線

### 影像
- 基本： `![alt text](image.png "hover tooltip")`
- 調整大小： `{width="300"}`
- 對齊： `{align="center"}`或`{align="right"}`
- 可縮放： `{zoomable="yes"}`或`{modal="regular"}`
- 檔案大小上限：100 MB （建議在5 MB以下）
- 所有影像都需要替代文字（針對SEO和協助工具）
- 影像檔案名稱：小寫搭配連字型大小
- 將影像儲存在指定的資產資料夾中

### 程式碼片段
- 內嵌：反引號`` `code` ``
- 用於：檔案名稱、URL、使用者定義的術語、命令
- 包圍型程式碼區塊：具有語言識別碼的三重反引號

  ```
  ```javascript

  code here

  ```

  ```

  
  
- 選項： `{line-numbers="true"}`、`{start-line="7"}`、`{highlight="11-13, 16"}`
- 在包圍型程式碼區塊中一律包含語言識別碼

### 表格
- 分隔符號列的每欄至少需要3個連字型大小： `|---|---|---|`
- 對齊：左`|---|`，中`|:---:|`，右`|---:|`
- 逸出常值管道： `\|`或使用`&vert;`
- 允許HTML資料表；使用`<table style="table-layout:auto">`或`table-layout:fixed`
- HTML資料表對齊方式： `<td align="left|center|right">`
- 避免HTML表格內的Markdown語法（例如`[!NOTE]`在HTML表格中無法運作）
- 移除框線： `<tr style="border: 0;">`
- Markdown表格版面配置選項：在表格後面新增`{style="table-layout:auto"}` （含空白行）
- 避免出現非常寬/高的表格，因為水準卷軸可見度有問題

&#x200B;---

## &#x200B;3. 特殊ADOBE語法擴充功能

### 圖說文字/警告

```
>[!NOTE]
>
>Text here.

>[!TIP]
>
>Text here.

>[!IMPORTANT]
>
>Text here.

>[!WARNING]
>
>Text here.

>[!CAUTION]
>
>Text here.

>[!ADMIN]
>[!AVAILABILITY]
>[!PREREQUISITES]
>[!INFO]
>[!ERROR]
>[!SUCCESS]
```

- 嚴重： `>`與`[ !`之間沒有空格 — 使用`>[!NOTE]`，而不是`> [!NOTE]`
- 在`>[!NOTE]`與內文文字行之間新增空白行

### 索引標籤

```
>[!BEGINTABS]

>[!TAB iOS]
Content here

>[!TAB Android]
Content here

>[!ENDTABS]
```

### 可摺疊區段（摺疊式面板）

```
+++Click to expand
Content inside
+++
```

注意：不支援巢狀可摺疊區段。

### 陰影方塊

```
>[!BEGINSHADEBOX "Optional Title"]
Content here
>[!ENDSHADEBOX]
```

### 視訊

```
>[!VIDEO](https://video.tv.adobe.com/v/ID/?quality=12&learn=on)
```

新增成績單的`{transcript=true}`。

### 更多相關資訊

```
>[!MORELIKETHIS]
>* [Article 1](url)
>* [Article 2](url)
```

### 內容說明

```
>[!CONTEXTUALHELP]
>id="..."
>title="..."
>abstract="..."
>additional-url="..."
```

### 徽章（內嵌）

```
[!BADGE Label]{type=Informative url="https://example.com" tooltip="text"}
```

型別： `Informative` （藍色）、`Positive` （綠色）、`Negative` （紅色）、`Neutral` （灰色）、`Caution` （黃色）

### 文字反白顯示（預覽）

```html
<span class="preview">highlighted text</span>
```

### 包含和代碼片段
- 包含整個檔案： `{{$include /help/_includes/legal-blurb.md}}`
- 程式碼片段（無標題）： `{{snippet-id}}`
- 將可重複使用的檔案儲存在`help > _includes/`資料夾中
- 儲存在`help > _includes/snippets.md`中的程式碼片段
- 包含可以有標題；代碼片段不能
- 僅適用於相同存放庫（而非跨存放庫）
- 在非參照檔案中逸出`{{`或`}}`個字元

### DNL （不要本地化）標籤
- `[!DNL ProductName]` — 包裝不應翻譯的產品/品牌名稱
- 用於頁面中的第一個或顯著提及

### UICONTROL標籤
- `[!UICONTROL Button Label]` — 包裝UI元素文字（按鈕、功能表、欄位名稱）
- 確保從產品資料庫而不是機器翻譯中提取UI字串
- UICONTROL標籤內沒有撇號、引號或標點符號
- 對步驟中參考的UI元素使用粗體格式

### 不支援的功能
- 工作清單（核取方塊）
- 表情符號
- 水準規則
- 巢狀可摺疊區段

&#x200B;---

## &#x200B;4. 檔案命名和資料夾結構

### 檔案命名規則
- 小寫檔案名稱（僅含連字型大小）
- 沒有大寫、底線、句號或空格
- 描述性、SEO易記的名稱（例如，`calculated-metric-overview.md`不是`cmo.md`）
- 避免使用檔案名稱中的數字；使用描述性字詞
- 避免保留/衝突名稱： `metadata.md`， `search.md`
- 重新命名即時檔案需要重新導向管理（URL變更）

### 資料夾結構
- 目錄/資料夾名稱不會影響URL （只有存放庫名稱和檔案名稱會影響URL）
- TOC.md會控制導覽階層，而非Git資料夾位置
- 將影像/資產儲存在指定的資產資料夾中
- 儲存在`help/_includes/`中的可重複使用的包含
- 儲存在`help/_includes/snippets.md`中的程式碼片段

### TOC.md規則
- 每篇文章都必須列在TOC.md中，才能在Experience League上呈現
- H1格式： `# Guide Title {#anchor-id}` — 錨點產生基底URL路徑
- 章節標題必須有錨點ID： `+ Section Name {#section-id}`
- 章節標題（父專案）不能是連結本身
- 文章連結： `+ [Title](path/file.md)`
- 變更區段錨點ID會變更所有巢狀文章URL （需要重新導向）
- 在整個（`+`、`*`或`-`）中使用一致的專案符號樣式
- TOC中繼資料： `user-guide-description`，選擇性`breadcrumb-title`
- `mini-toc-levels`：控制右方導覽標題顯示（1-6，預設2）

&#x200B;---

## &#x200B;5. 內容品質和編輯標準

### 語音與音調
- 主動式語音優先於被動式
- 現在時態對未來時態
- 第二人（「您」），負責教學內容
- 35字以下的句子
- 強而精確的動詞 — 避免使用弱副詞（「非常」、「極其」）

### 步驟/程式
- 每個步驟都是單一且簡潔的命令（一個句子）
- 額外的資訊會顯示在下一行（在步驟下方縮排）
- 以命令式動詞開始每個步驟
- 將程式限制在約7個步驟內（最多為10個步驟再分成子任務）
- 在步驟之前放置概念資訊
- 在相關步驟後放置熒幕擷取畫面
- 重複頁面/標簽名稱以取得讀取器方向
- 步驟中UI元素的粗體UICONTROL格式

### 介面術語
- **開啟/關閉**：應用程式和程式
- **移至**：功能表、索引標籤或UI位置
- **選取**：文字、儲存格或清單中的選項
- **按一下**：滑鼠動作（除非必要，否則請避免指定控制項型別）
- **下拉式功能表** （不是「下拉式清單」）

### 產品名稱
- 請勿在標題/標題中新增產品名稱，除非內容需清楚明瞭
- 在產品名稱前省略
- 在指南層級第一次提及時加入「Adobe」（商標要求）
- 除非法律要求，否則在次要提及中捨棄「Adobe」
- 對產品名稱使用DNL標籤以防止誤譯

### 強調與格式
- 粗體：UI元素和鍵盤動作
- 斜體：錯誤訊息、外來字、強調
- 代碼（反引號）：檔案名稱、URL、使用者定義的辭彙
- UI元素周圍沒有引號（請改用UICONTROL標籤）

### 大寫
- 標題、導覽、副標題的句子大小寫
- 只有`title`中繼資料欄位的字首大寫
- 專有名詞一律大寫

&#x200B;---

## &#x200B;6. SEO最佳作法

- 每頁一個H1 — 必須簡明扼要、描述清楚，並告知使用者頁面內容
- 循序標題階層（h1 → h2 → h3，永不略過層級）
- 在H1、內文和中繼資料中包含關鍵字（不是`keywords`中繼標籤 — Google會忽略它）
- 避免關鍵字填滿（意圖>頻率）
- 標題：最多50-60個字元；系統會自動附加「| Adobe ProductName」
- 說明： 150-160個字元；應該是call to action，而不是內容的重複
- 新增描述性替代文字至所有影像
- 包含視訊稿（搜尋引擎只能讀取文字）
- 策略性地連結至相關頁面（避免孤立頁面）
- 包含結構化元素：編號清單、副標題、程式碼區塊
- 使用AnswerThePublic、Google Trends等工具來研究關鍵字
- 內容應展示E-E-A-T （經驗、專業知識、授權、可信度）

&#x200B;---

## &#x200B;7. 本地化

### 機器翻譯優先
- 英文來源內容會自動產生當地語系化版本
- 支援的語言：德文、法文、日文、義大利文、西班牙文、巴西葡萄牙文、簡體中文、繁體中文、韓文、荷蘭文、瑞典文

### 撰寫以供本地化
- 整個網站使用一致的術語
- 簡短句子和主動語態
- 標準英文單字順序（主旨→動詞→物件）
- 使用相對代詞(&quot;that&quot;、&quot;which&quot;)
- 避免：幽默、成語、行話、地區片語、隱喻、不必要的字詞

### 本地化標籤
- `[!UICONTROL Label]` — 確保從產品DB提取UI字串，而不是機器翻譯
- `[!DNL ProductName]` — 防止翻譯產品/品牌名稱
- 「不要本地化」資料夾中的影像會排除在本地化之外

&#x200B;---

## &#x200B;8. 內容型別

- **指南**：目錄中所參考頁面的線上集合；涵蓋官方最佳實務
- **教學課程**：特定使用案例的教學內容（影片或文字）；發佈在學習存放庫中
- **參考指南**：開發人員API/SDK；通常是表格格式；已發佈至developer.adobe.com
- **課程**：以特定使用者角色為目標的專家策劃課程集合
- **知識庫文章**：簡短、暫時相關的疑難排解內容
- **登陸頁面/首頁**：獨立管理(SCCM)

&#x200B;---

## &#x200B;9. 要避免的常見驗證錯誤

- 遺失或空白`title`或`description`中繼資料
- `description`開頭不是「瞭解……」 或「瞭解如何……」
- 編號說明語法中`>`和`[ !`之間的空格（`> [!NOTE]`而非`>[!NOTE]`）
- 粗體標籤中的空格： `**text **` （結尾空格會破斷粗體）
- HTML表格內的Markdown語法（例如圖說文字無法在該處運作）
- 複製檔案中的標題錨點ID
- 包含句號的錨點ID （請改用連字型大小）
- 使用保留的錨點名稱（搜尋、結果、頁首、頁尾等）
- 不符合YAML定義的`role`、`level`、`feature`、`topic`值
- 棧疊式標題，中間沒有內文
- H1每個檔案使用多次
- 略過的標題層級（例如，H1→H3）
- 以大寫、底線或空格命名檔案
- 影像上遺失替代文字
- 實際工作標題(「建立……」 ，而非「建立……」)
