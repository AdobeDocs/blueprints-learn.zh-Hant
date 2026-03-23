---
name: industry-use-case-builder
description: 為Adobe Experience Platform Blueprint存放庫建立新產業使用案例指南。 當使用者想要將商業案例新增到產業頁面，或更新使用案例目錄時，請使用這項技能，將新使用案例新增到垂直產業（零售、汽車、醫療保健、金融服務、保險、媒體與娛樂、電信、旅遊與酒店、B2B）。 處理完整的工作流程：收集使用案例詳細資訊、評估成熟度等級、產生內容、更新產業概觀頁面和使用案例目錄，以及叫用使用案例圖示產生器技能來建立圖示。
source-git-commit: ed8928687806b619e95d8d320478d27c13722a80
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 100%

---


# 產業使用案例產生器

此技能可指導Adobe Experience Platform Blueprint存放庫建立新的產業使用案例。 循序漸進地遵循每個階段。 在開始之前讀取參考檔案：

- `references/use-case-template.md` — 使用案例區段的確切範本
- `references/catalog-row-template.md` — 目錄表格列的確切格式
- `references/maturity-criteria.md` — 成熟度評估的詳細規則

## 階段1：資訊收集

在產生任何內容之前，詢問使用者以收集所有必要的詳細資訊。

### 必填欄位

1. **垂直產業** — 必須為其中一項：
   - 汽車
   - b2b
   - 金融服務
   - 醫療保健
   - 保險
   - 媒體 — 娛樂
   - 零售
   - 電信
   - 旅遊 — 旅館業

2. **使用案例名稱** — 清楚的描述性標題（例如「放棄購物車電子郵件回覆」、「藥物遵守行銷活動」）。

3. **描述** — 1-2個句子，說明業務案例及其重要原因。

4. **業務影響** — 以特定量度量化結果（例如「點進率增加20-30%」、「重新填入率改善15-25%」）。

5. **使用案例模式** — 必須正好對應到下列現有模式之一：
   - Audience Activation至目的地
   - 有區段比對的對象Collaboration
   - 事件轉送
   - B2B Audience Activation
   - 匿名訪客網頁Personalization
   - 已知訪客網頁/應用程式Personalization
   - Offer Decisioning
   - 行為建議
   - 批次傳出訊息啟用
   - 事件觸發式傳訊
   - 多步驟協調歷程
   - 具有決策的跨頻道歷程
   - 購買群組式行銷與歷程管理
   - Customer Analytics與Insight開發
   - B2B分析
   - Brand Concierge對話體驗

6. **技術考量** — 4-8專案要點，涵蓋資料需求、整合、法規/法規需求、效能考量及架構注意事項。

繼續前請先詢問任何遺漏的欄位。 請勿假設或虛構細節。

## 第2階段：成熟度評估

閱讀`references/maturity-criteria.md`以取得完整規則。 指定下列三個成熟度層級之一：

- **基礎** `[!BADGE Foundational]{type=Neutral}` — 單一步驟或事件觸發的模式（事件觸發的傳訊、批次輸出）、直接的資料需求、最低限度的AI/ML、標準整合。
- **新興** `[!BADGE Emerging]{type=Informative}` — 多步驟歷程、行為資料、建議模型、已知訪客個人化、中等整合複雜性。
- **進階** `[!BADGE Advanced]{type=Caution}` — 跨頻道決策、AI支援的預測、優惠決策、複雜的協調流程、多重系統整合。

### 評估工作流程

1. 識別使用案例對應的使用案例模式。
2. 請檢視成熟度條件中的「典型模式」清單，以快速比對。
3. 如果模式未清楚表示成熟度，請評估資料複雜性、AI/ML需求和整合範圍。
4. 以推理方式向使用者呈現評量：「根據模式對應({pattern})和{key factors}，我會將此分類為{level}，因為{reasoning}。」
5. 在繼續產生內容之前，請等待使用者確認或覆寫。

## 階段3：內容產生

在兩個檔案中產生或更新內容。

### A.產業概觀檔案

**檔案路徑：** `/help/blueprints/industry-use-cases/{industry}/{industry}-overview.md`

請先閱讀現有檔案以瞭解目前結構和內容。 然後，在來自`references/use-case-template.md`的完全相同的範本後新增區段：

```markdown
## {Use Case Title}

{1-2 sentence description of the business scenario and why it matters}

### Business impact

{Quantified business outcomes, e.g., "Retailers typically see a 20-30% increase in click-through rates..."}

### How to implement

Use the [{Pattern Name}](/help/blueprints/use-case-patterns/{category}/{pattern-file}.md) pattern. {1-2 sentence explanation of why this pattern applies}

### Technical considerations

- {4-8 bullet points covering data integration, regulatory, performance, or architectural considerations}
```

將新區段放置在現有使用案例區段之後，並保持一致的格式。

### B.使用案例目錄

**檔案路徑：** `/help/blueprints/industry-use-cases/use-case-catalog.md`

請先讀取現有的目錄檔案。 在正確的產業索引標籤中新增一列。 目錄使用含有`>[!TAB {Industry}]`標籤的索引標籤結構。 每個索引標籤都包含一個表格，內含下列資料欄：

| 欄 | 內容 |
| --- | --- |
| 圖示 | `<img src="assets/use-case-icons/{industry}/icon-{kebab-name}.png" alt="{Alt Text}" width="40">` （如果還沒有圖示則保留空白） |
| 使用案例 | `[{Use Case Title}]({industry}/{industry}-overview.md#{anchor})`，其中錨點為索引鍵大小寫的標題 |
| 說明 | 單句摘要 |
| 成熟度 | 指派層級的徽章語法 |
| 圖樣 | `[{Pattern Name}](/help/blueprints/use-case-patterns/{category}/{pattern-file}.md)` |

**位置規則：**&#x200B;在每個產業標籤中，資料列會依成熟度依此順序分組：基礎優先，然後是新興，然後是進階。 將新列放置在正確的成熟度群組結尾。

模式檔案路徑為：
- `audience-building-activation/audience-activation-to-destinations.md`
- `audience-building-activation/audience-collaboration-segment-match.md`
- `audience-building-activation/event-forwarding.md`
- `audience-building-activation/b2b-audience-activation.md`
- `personalization/anonymous-visitor-web-personalization.md`
- `personalization/known-visitor-web-app-personalization.md`
- `personalization/offer-decisioning.md`
- `personalization/behavioral-recommendation.md`
- `campaign-management-orchestration/batch-outbound-message-activation.md`
- `campaign-management-orchestration/event-triggered-messaging.md`
- `campaign-management-orchestration/multi-step-orchestrated-journey.md`
- `campaign-management-orchestration/cross-channel-journey-with-decisioning.md`
- `campaign-management-orchestration/buying-group-based-marketing.md`
- `analysis/customer-analytics-insight-generation.md`
- `analysis/b2b-analytics.md`
- `conversational-experience/brand-concierge-conversational-experience.md`

## 階段4：圖示產生

內容建立後，叫用`use-case-icon-generator`技能以產生新使用案例的圖示規格。 提供下列技能：
- 使用案例名稱
- 垂直產業
- 使用案例的簡短說明

當使用者擁有產生的圖示檔案後，請更新目錄列以包含圖示參考：

```
<img src="assets/use-case-icons/{industry}/icon-{kebab-name}.png" alt="{Alt Text}" width="40">
```

## 階段5：驗證

完成之前，請先確認下列所有事項：

1. **範本合規性** — 產業概觀區段完全遵循範本（##標題、說明、###業務影響、###如何實作、###技術考量）。
2. **目錄位置** — 目錄列在正確的產業索引標籤中，而且處於正確的成熟度群組中（依序為「基礎」、「新興」和「進階」）。
3. **模式連結有效性** — 概觀和目錄中的模式連結使用上述清單中的有效模式檔案路徑。
4. **錨點一致性** — 目錄連結中的錨點（例如`#abandoned-cart-email-recovery`）符合轉換成Kebab大小寫的總覽檔案中的`##`標題。
5. **圖示路徑慣例** — 圖示路徑遵循`assets/use-case-icons/{industry}/icon-{kebab-name}.png`。

報告驗證期間發現的任何問題，並在完成之前修正。
