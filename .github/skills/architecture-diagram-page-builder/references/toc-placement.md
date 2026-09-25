---
source-git-commit: c766cd3153efce4635089d008daf3eb426eb7a24
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%
---
# TOC.md位置參考

當技能產生新的架構圖表頁面時，它必須新增專案到`/help/blueprints/TOC.md`，才能在網站導覽中找到該頁面。 本檔案會明確定義專案前往的位置和方式。

## 父區段

所有架構圖表頁面都位於TOC.md中的頂層`+ Architecture Diagrams and Blueprints{#architecture-diagrams}`區段下。 在該區段中，數個子區段會依主題將頁面分組。

這些子區段的資料夾名稱、TOC錨點和TOC標籤必須遵循`../../architecture-diagram-category-builder/references/naming-conventions.md`中的命名規則 — 如果需要新類別，請參閱該檔案（針對該類別使用`architecture-diagram-category-builder`技能，而非此類別）。

## 子區段對應

挑選符合新頁面主題資料夾的子區段：

| 主題資料夾 | 目錄子區段標題 |
| --- | --- |
| `architecture-diagrams/architecture-overviews/` | `+ Architecture overviews{#architecture-overviews}` |
| `architecture-diagrams/audience-profile-activation/` | `+ Audience & Profile Activation{#audience-profile-activation}` |
| `architecture-diagrams/b2b-activation-marketing/` | `+ B2B activation & marketing{#b2b-activation-marketing}` |
| `architecture-diagrams/customer-insights/` | `+ Customer Insights{#customer-insights}` |
| `architecture-diagrams/customer-journeys/` | `+ Customer journeys{#customer-journeys}` |

如果使用者建議的主題資料夾不在此表格中，請將其視為新的頂層子區段並暫停 — 要求使用者確認是否建立它。 請勿自動建立新的子區段。

## 專案格式

```
    + [{Page title}](/help/blueprints/{topic-folder}/{filename}.md)
```

規則：

- **縮排：**&#x200B;剛好四個空格，然後`+ `。 TOC剖析器會依據此專案而定；索引標籤或不同的間距會中斷導覽。
- **連結文字：**&#x200B;頁面標題，與`title`前置字元完全相符。 只有在相同子區段中的現有同層級使用它時才使用`[!DNL ...]` — 符合本機慣例。
- **連結目標：**&#x200B;以`/help/blueprints/`開頭的絕對路徑。 一律包含`.md`副檔名。
- **位置：**&#x200B;會附加為相符子區段中的最後一個專案，除非使用者指定不同的位置。 保留所有同級專案的現有順序。

## 巢狀子區段

`+ Architecture overviews{#architecture-overviews}`沒有巢狀群組 — `architecture-diagrams/architecture-overviews/`下的所有頁面（包括SDK部署頁面，例如`websdk.md`、`appsdk.md`）都位於相同的四空格縮排層級。 其他子區段（`Audience & Profile Activation`、`B2B activation & marketing`等） 仍可能包含巢狀群組 — 在放置專案前先檢查區段。 如果巢狀群組存在且新頁面屬於該群組，請縮排兩個額外的空格；否則將專案置於子區段的頂層。

## 有效範例

### 範例1 — 頂層AEP頁面

- 主題資料夾： `architecture-diagrams/architecture-overviews/`
- 檔案名稱： `mix-modeler-integration.md`
- 頁面標題： `Adobe Mix Modeler integration with Experience Platform`

登入：

```
    + [Adobe Mix Modeler integration with Experience Platform](/help/blueprints/architecture-diagrams/architecture-overviews/mix-modeler-integration.md)
```

放置在`+ Architecture overviews{#architecture-overviews}`下。

### 範例2 — AJO歷程架構

- 主題資料夾： `architecture-diagrams/customer-journeys/`
- 檔案名稱： `cross-channel-journey-architecture.md`
- 頁面標題： `Cross-channel journey architecture`

登入：

```
    + [Cross-channel journey architecture](/help/blueprints/architecture-diagrams/customer-journeys/cross-channel-journey-architecture.md)
```

放置在`+ Customer journeys{#customer-journeys}`下。

### 範例3 — SDK部署頁面

- 主題資料夾： `architecture-diagrams/architecture-overviews/`
- 檔案名稱： `mobile-sdk-architecture.md`
- 頁面標題： `Mobile SDK deployment architecture`

登入（與其他架構概觀頁面相同的四空格縮排）：

```
    + [Mobile SDK deployment architecture](/help/blueprints/architecture-diagrams/architecture-overviews/mobile-sdk-architecture.md)
```

放置在`+ Architecture overviews{#architecture-overviews}`下。

## 驗證

編輯TOC.md後，重新讀取受影響的子區段並確認：

1. 新專案只會使用四個縮排空格（如果巢狀位於子區段特定群組下，則為六個，例如`Audience & Profile Activation`的RTCDP群組）。
2. 連結目標符合磁碟上的檔案路徑 — 包括`.md`副檔名。
3. 專案會分組在正確的子區段中，而不是浮動在子區段之間。
4. 未重新排序或修改任何現有專案。
