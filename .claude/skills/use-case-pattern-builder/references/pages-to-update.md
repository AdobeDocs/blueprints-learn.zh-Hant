---
source-git-commit: ef1c207922c1079117d8bd255dbfa32a1527b014
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 100%

---
# 新增使用案例模式時要更新的頁面

建立新的使用案例模式時，必須更新以下頁面，以確保模式可發現且正確連結。

## 必要的更新

### 1. TOC.md
- **檔案：** `/help/blueprints/TOC.md`
- **動作：**&#x200B;在正確的類別區段底下新增專案
- **格式：** `    + [{{Pattern Title}}](/help/blueprints/use-case-patterns/{{category}}/{{filename}}.md)`
- **位置（依類別）：**
   - 對象建立和啟動：在第47行之後（在該區段中的現有專案之後）
   - Personalization：第52行之後
   - 行銷活動管理與協調：第58行之後
   - 分析：在第61行之後
   - 對話體驗：第63行之後

#### 類別到目錄的對應

| 類別概要 | 目錄章節標題 | 錨點 |
| --- | --- | --- |
| `audience-building-activation` | `+ Audience Building & Activation` | `{#audience-building-activation}` |
| `personalization` | `+ Personalization` | `{#personalization-patterns}` |
| `campaign-management-orchestration` | `+ Campaign Management & Orchestration` | `{#campaign-orchestration-patterns}` |
| `analysis` | `+ Analysis` | `{#analysis-patterns}` |
| `conversational-experience` | `+ Conversational Experience` | `{#conversational-experience-patterns}` |

#### 縮排規則

- 類別標題使用兩個空格+ `+` （例如， `  + Personalization{#personalization-patterns}`）
- 模式專案使用四個空格+ `+` （例如， `    + [Pattern Title](path)`）

### &#x200B;2. 使用案例模式概觀
- **檔案：** `/help/blueprints/use-case-patterns/overview.md`
- **動作：**&#x200B;新增資料列至正確的類別資料表
- **格式：** `| [{{Pattern Title}}]({{category}}/{{filename}}.md) | {{Primary capability description}} | [!DNL {{Solution1}}], [!DNL {{Solution2}}] |`
- 總覽中的&#x200B;**類別：**
   - 對象建立和啟用（第18行以下）
   - Personalization （第29行）
   - 行銷活動管理與協調（第40行以下）
   - 分析（第52行）
   - 交談體驗（第~61行）

#### 列格式範例

```
| [Event-Triggered Messaging](campaign-management-orchestration/event-triggered-messaging.md) | Listen for a real-time behavioral or system event, then deliver a contextual message to the triggering profile | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
```

## 驗證檢查清單

- [ 在正確的類別目錄中建立]模式Markdown檔案
- [ ] Frontmatter包含標題、說明、解決方案和exl-id
- [ ] TOC.md專案已新增至正確的類別下
- [ 在正確的類別下新增] Overview.md表格列
- [ ]所有商業目標連結都指向現有檔案
- [ ]檔案使用kebab大小寫命名慣例
- [ ]所有Experience League連結都是有效的URL
- [ ] Adobe產品名稱使用`[!DNL ...]`語法
- [ ]函式鏈使用` > `分隔符號格式
- [ ]圖樣檔包含所有必要的區段（請參閱pattern-template.md）
