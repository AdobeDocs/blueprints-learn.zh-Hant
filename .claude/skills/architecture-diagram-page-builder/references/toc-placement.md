---
source-git-commit: 83e85d946e455cde46001af0a2112637b7fe24cc
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---
# TOC.md位置參考

當技能產生新的架構圖表頁面時，它必須新增專案到`/help/blueprints/TOC.md`，才能在網站導覽中找到該頁面。 本檔案會明確定義專案前往的位置和方式。

## 父區段

所有架構圖表頁面都位於TOC.md中的頂層`+ Architecture Diagrams and Blueprints{#architecture-diagrams}`區段下。 在該區段中，數個子區段會依主題將頁面分組。

## 子區段對應

挑選符合新頁面主題資料夾的子區段：

| 主題資料夾 | 目錄子區段標題 |
| --- | --- |
| `experience-platform/` | `+ Architecture overviews{#architecture-overview}` |
| `experience-platform/deployment/` | `+ Deployment{#deployment}` （巢狀於`Architecture overviews`內的子子區段） |
| `audience-activation/` | `+ Audience & Profile Activation{#audience-activation}` |
| `b2b/` | `+ B2B activation & marketing{#b2b-activation}` |
| `customer-journey-analytics/` | `+ Customer Journey Analytics{#customer-journey-analytics}` |
| `customer-journeys/` | `+ Customer journeys{#customer-journeys}` |

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

`+ Architecture overviews{#architecture-overview}`包含SDK頁面的巢狀`+ Deployment{#deployment}`區塊。 如果新頁面位於`experience-platform/deployment/`下方，請將專案放在`Deployment`內，並有&#x200B;**6個**&#x200B;縮排的空格：

```
      + [{Page title}](/help/blueprints/experience-platform/deployment/{filename}.md)
```

其他子區段（`Audience & Profile Activation`、`B2B activation & marketing`等） 也可能包含巢狀群組 — 在放置專案之前先檢查區段。 如果巢狀群組存在且新頁面屬於該群組，請縮排兩個額外的空格；否則將專案置於子區段的頂層。

## 有效範例

### 範例1 — 頂層AEP頁面

- 主題資料夾： `experience-platform/`
- 檔案名稱： `mix-modeler-integration.md`
- 頁面標題： `Adobe Mix Modeler integration with Experience Platform`

登入：

```
    + [Adobe Mix Modeler integration with Experience Platform](/help/blueprints/experience-platform/mix-modeler-integration.md)
```

放置在`+ Architecture overviews{#architecture-overview}`下。

### 範例2 — AJO歷程架構

- 主題資料夾： `customer-journeys/`
- 檔案名稱： `cross-channel-journey-architecture.md`
- 頁面標題： `Cross-channel journey architecture`

登入：

```
    + [Cross-channel journey architecture](/help/blueprints/customer-journeys/cross-channel-journey-architecture.md)
```

放置在`+ Customer journeys{#customer-journeys}`下。

### 範例3 — 部署SDK頁面

- 主題資料夾： `experience-platform/deployment/`
- 檔案名稱： `mobile-sdk-architecture.md`
- 頁面標題： `Mobile SDK deployment architecture`

輸入（請注意六空格縮排）：

```
      + [Mobile SDK deployment architecture](/help/blueprints/experience-platform/deployment/mobile-sdk-architecture.md)
```

置於`+ Architecture overviews{#architecture-overview}`內的`+ Deployment{#deployment}`之下。

## 驗證

編輯TOC.md後，重新讀取受影響的子區段並確認：

1. 新專案僅使用四個縮排的空格（若巢狀位於`Deployment`下，則使用六個空格）。
2. 連結目標符合磁碟上的檔案路徑 — 包括`.md`副檔名。
3. 專案會分組在正確的子區段中，而不是浮動在子區段之間。
4. 未重新排序或修改任何現有專案。
