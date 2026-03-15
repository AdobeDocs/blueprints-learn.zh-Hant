---
source-git-commit: a632042b3a7434dd88f52804e15e30fa06057e3b
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 1%

---
# Adobe Experience League — 核准的中繼資料欄位參考

*來源為Adobe ExL Authoring Guide （抓取日期：2026年2月） + blueprint-learn.en*

---

## 中繼資料階層

中繼資料會依此順序層疊（文章會覆寫TOC，TOC會覆寫存放庫）：
1. 文章正文（最高優先順序）
2. 使用手冊中的TOC.md
3. 存放庫根目錄下的metadata.md （最低優先順序）

---

## 文章層級欄位

### 必填

| 欄位 | 說明 | 格式/限制 |
|-------|-------------|----------------------|
| `title` | SEO頁面標題。 出現在搜尋結果中。 | 最多~60個字元；字首大寫；使用`[!DNL Product]`作為產品名稱；除非有意，否則請勿完全重複H1 |
| `description` | 搜尋引擎和ExL建議的Meta說明。 | 150-160個字元；最好是從「學習如何……」開始 或「瞭解……」；如果缺少/為空，驗證會失敗 |
| `exl-id` | 系統指派的唯一識別碼。 用於內容追蹤。 | UUID格式（例如`70573eb9-cd69-4fe6-b2ae-dae81665a308`）；**複製檔案時刪除** — 將會自動指派；永遠不跨檔案複製 |

### 強烈建議

| 欄位 | 說明 | 有效值 |
|-------|-------------|--------------|
| `solution` | 文章涵蓋Adobe產品。 用於ExL搜尋/篩選及內容建議。 | 以逗號分隔；區分大小寫；必須符合核准的列舉（請參閱下面的有效解決方案值） |

### 選擇性 — 一般

| 欄位 | 說明 | 有效值/備註 |
|-------|-------------|----------------------|
| `kt` | 舊版知識文章JIRA號碼。 用於分析追蹤。 | 整數（例如`7207`）；可接受空白；`null`可接受 |
| `thumbnail` | recommendations/analytics的縮圖影像參考。 | 檔案名稱字串、`null`或空白 |
| `version` | 產品版本篩選器。 主要用於AEM和Campaign藍圖。 | E.g. `Campaign v8`，`Campaign v8 Client Console`；必須符合version.yml |
| `doc-type` | 用於存放庫/分析的內容分類。 | `blueprint`、`overview-page`、`Video`、`Tutorial`、`Troubleshooting` （偏好使用小寫） |
| `feature` | 在ExL頁面上顯示為「主題」的主題標籤。 | 每篇文章1-2；標題大小寫；必須符合feature.yml；逗號分隔 |
| `feature-set` | 用於功能驗證的父項應用程式。 | 必須符合feature.yml值 |
| `role` | 目標對象角色。 在ExL上顯示為「建立對象」。 | `Admin`, `Architect`, `Data Architect`, `Data Engineer`, `Developer`, `Leader`, `User` |
| `level` | 使用者體驗層級。 在ExL上顯示為「建立對象」。 | `Beginner`， `Intermediate`， `Experienced` （字首大寫） |
| `topic` | 搜尋/篩選的跨產品主題。 | 字首大寫；必須符合topic.yml；逗號分隔 |
| `type` | 指南分類。 | `Documentation` （預設），`Tutorial`，`Troubleshooting` |
| `last-substantial-update` | 在「新增功能」Widget中顯示內容。 | 格式： `YYYY-MM-DD` |
| `hide` | 將頁面從所有搜尋和建議中排除；也將索引設定為no。 | `yes`或`no` |
| `hidefromtoc` | 從目錄導覽中移除，但仍可透過直接連結存取頁面。 | `yes`或`no` |
| `index` | 控制頁面是否出現在外部搜尋/網站地圖中。 | `yes`/`no`或`y`/`n`；預設值： `no` （已編制索引） |
| `recommendations` | 控制「此功能的其他說明」Widget行為。 | `noDisplay` （防止Widget顯示）、`noCatalog` （從建議集區排除） |
| `internal` | 將頁面標籤為僅限Adobe內部。 防止內部連結標幟。 | `yes` |
| `short-description` | ExL登陸頁面的精簡說明。 若省略，則使用`description`。 | 一個句子；最多~20個字 |
| `activity` | 頁面使用分類。 | `understand`， `implement`， `troubleshoot` （小寫） |
| `sub-product` | 產品子元件。 請與解決方案團隊合作以獲得有效的列舉。 | 小寫；例如`search`、`assets`、`sites` |
| `team` | 分析團隊指派。 | E.g. `TM` |
| `landing-page-name` | 階層連結的登陸頁面連結。 | E.g. `experience-manager` |
| `landing-page-breadcrumb-title` | 登陸頁面連結的階層連結文字。 | E.g. `AEM` |
| `auto-video-transcripts` | 依預設啟用視訊記錄。 | `true` |
| `badgeType` | 內容狀態的徽章。 | 視情況而定；例如`informative`、`positive` |
| `badgePremium` | Premium徽章指標。 | 根據Adobe徽章規格 |
| `badgeLabel` | 徽章標籤文字。 | 短字串 |
| `source-git-url` | Source存放庫URL。 | 完整GitHub URL |
| `cloud` | 文章層級的雲端類別覆寫。 | 字首大寫；必須符合cloud.yml |

---

## TOC.md欄位

| 欄位 | 說明 | 附註 |
|-------|-------------|-------|
| `user-guide-title` | ExL階層連結和登入頁面中顯示的指南名稱。 | 目錄檔案所需 |
| `breadcrumb-title` | 使用手冊標題太長時，使用手冊的瀏覽路徑會縮短。 | 可選 |
| `user-guide-description` | ExL登陸頁面的指南摘要。 | 一個句子；最多建議20個字 |
| `product` | 指南的Analytics追蹤。 僅限單一值。 | 必須與product.yml相符（請參閱有效的產品值） |
| `mini-toc-levels` | 以右導覽迷你目錄顯示的標題層級數目。 | 整數1-6；預設值2 |
| `role` | 指南的預設受眾角色。 | 與文章`role`的值相同；以逗號分隔 |
| `index` | 是否將指南編制索引。 | `yes`/`no` |

---

## 存放庫層級metadata.md欄位

| 欄位 | 附註 |
|-------|-------|
| `cloud` | 存放庫中所有文章的預設雲端類別 |
| `solution` | 所有文章的預設解決方案 |
| `product` | 分析追蹤的預設產品 |
| `type` | 預設參考線型別 |
| `doc-type` | 預設檔案型別 |
| `mini-toc-levels` | 預設迷你目錄層級 |
| `git-repo` | GitHub存放庫URL；啟用「編輯此頁面」和「記錄問題」按鈕 |
| `index` | 預設索引設定 |

---

## 有效的解決方案值（區分大小寫）

此存放庫中使用的通用值：
- `Experience Platform`
- `Real-Time Customer Data Platform`
- `Journey Optimizer`
- `Journey Optimizer B2B Edition`
- `Customer Journey Analytics`
- `Campaign`
- `Campaign v8`
- `Campaign Classic v7`
- `Campaign Standard`
- `Audience Manager`
- `Target`
- `Analytics`
- `Data Collection`
- `Commerce`
- `Marketo Engage`
- `Experience Cloud`
- `Journey Orchestration`

多個值：逗號分隔，如`Real-Time Customer Data Platform, Campaign`

---

## 有效的產品值（`product`欄位 — 分析追蹤）

請參閱系統提示以取得完整清單。 索引鍵值：
- `adobe experience platform` / `experience platform` / `aem`
- `adobe analytics` / `analytics` / `aa`
- `adobe journey optimizer` / `journey optimizer` / `jo`
- `adobe customer journey analytics` / `customer journey analytics` / `cja`
- `adobe real time customer data platform` / `real time cdp` / `rtcdp`
- `adobe marketo` / `marketo` / `amk`
- `adobe campaign` / `campaign` / `ac`
- `adobe target` / `target` / `at`

---

## 有效的角色值

- `Admin`
- `Architect`
- `Data Architect`
- `Data Engineer`
- `Developer`
- `Leader`
- `User`

---

## 金鑰驗證規則

1. 切勿在複製的檔案中保留具有相同UUID的`exl-id` — 刪除它並讓系統指派新的UUID。
2. 可接受空白/空值`thumbnail`和`kt`；這些是舊版欄位。
3. `solution`值必須與核准的列舉完全相符 — 區分大小寫。
4. 如果遺失或null，`description`驗證會失敗；請一律提供有意義的值。
5. 如果`title`值包含冒號、方括弧或前導特殊字元，請用引號括住。
6. 多個`solution`值在單一字串值中以逗號分隔。
7. `product`僅是單一值（用於analytics追蹤）；請勿使用逗號分隔值。
8. 若要請求新的列舉值，請歸檔具有「內容標籤」元件的UGP JIRA票證。
