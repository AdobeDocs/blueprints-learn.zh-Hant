---
title: 對象Collaboration
description: 瞭解如何使用「區段比對」，跨沙箱或組織共用及比對受眾區段。
solution: Real-Time Customer Data Platform, Experience Platform
exl-id: 7014849c-5e32-4ec3-a531-c0e8ce896f44
source-git-commit: 27f7e230982807ec70ca96af7f737944a6588f27
workflow-type: tm+mt
source-wordcount: '6232'
ht-degree: 1%

---

# 對象Collaboration

本指南提供在[!DNL Real-Time CDP]和[!DNL Adobe Experience Platform]中使用[!DNL Segment Match]的對象共同作業的完整實作參考。 它專為需要以隱私安全方式跨沙箱或組織共用及比對受眾區段的解決方案架構師、行銷技術人員和實施工程師所設計。

使用此計畫來瞭解可用的方法、評估折衷方案，並瀏覽[!DNL Adobe Experience League]以取得詳細的設定指示。

[!DNL Segment Match]可讓兩個或更多[!DNL Experience Platform]組織（或組織內的沙箱）透過共用區段成員資格資訊來共同作業對象資料，而不會公開基礎的PII。 參與者可以估計重疊、共用受眾，以及將相符的設定檔啟動至下游目的地。

## 使用案例概述

組織越來越需要與合作夥伴、子公司或跨業務單位就受眾資料進行共同作業，同時維持嚴格的隱私權控制。 受眾共同作業可透過[!DNL Segment Match]啟用安全的區段共用，滿足此需求 — [!DNL Real-Time CDP]中的一項功能，可讓兩個或更多[!DNL Experience Platform]組織（或沙箱）使用雜湊的隱私權安全識別碼交換受眾會籍資訊。

業務案例通常會涉及某個組織（傳送者），該組織建立了有價值的受眾區段，並想要與合作夥伴組織（接收者）共用該區段，以進行共同目標定位、隱藏或擴充。 在共用前，雙方都可預估對象重疊以評估值。 共用後，接收組織即可透過其目標啟用相符的對象。

此模式與標準受眾啟用不同，因為它會在組織或沙箱之間運作，而不是與外部廣告或行銷目的地運作。 它也不同於資料潔淨室或協力廠商共同作業平台，因為它使用[!DNL Experience Platform]識別基礎結構在Adobe生態系統中以原生方式運作。

## 主要業務目標

此使用案例模式支援下列業務目標。

### 贏取新客戶

透過鎖定目標的贏取促銷活動、相似對象和付費媒體最佳化，來擴大客戶基礎。 受眾共同作業可讓組織透過比對其區段與合作夥伴受眾、識別高價值重疊，以及透過共同啟用觸及淨新客戶來發現新的潛在客戶集區。

- **KPI：**&#x200B;新客戶、客戶贏取成本、潛在客戶/潛在客戶轉換
- [贏取新客戶](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

### 降低客戶贏取成本

提升目標定位效率、從贏取促銷活動中抑制現有客戶，並最佳化媒體支出。 透過跨組織或業務單位共用隱藏區段，團隊可以避免在已轉換的客戶上浪費支出，並將預算聚焦於真正的新潛在客戶。

- **KPI：**&#x200B;客戶贏取成本、每個潛在客戶的成本、效率
- [降低客戶贏取成本](/help/blueprints/business-objectives/cost-efficiency/reduce-customer-acquisition-cost.md)

### 最佳化行銷支出和ROI

透過更好的目標定位、歸因、對象抑制和預算分配，改善行銷投資報酬。[!DNL Segment Match] 可啟用跨組織對象隱藏和共同目標定位，減少重複並提升精確度。

- **KPI：**&#x200B;成本節省、客戶贏取成本、遞增收入
- [最佳化行銷支出和ROI](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md)

## 戰術使用案例範例

- **發佈者 — 廣告商對象比對** — 品牌與媒體發佈者共用其高價值客戶區段，以估計重疊並以個人化廣告鎖定相符的使用者，改善行銷活動關聯性而不公開PII。
- **控股公司內的跨品牌抑制** — 父級組織下的多個品牌共用客戶區段，以抑制收購行銷活動中姐妹品牌的現有客戶，減少浪費的廣告支出。
- **零售媒體網路受眾擴充** — retailer與CPG品牌合作夥伴共用購買型區段，讓品牌能夠以較高的轉換率，鎖定在retailer媒體網路上的有效買家。
- **共同行銷合作夥伴對象探索** — 在啟動聯合行銷活動之前，兩個非競爭品牌會先評估對象重疊，以評估合作潛力，並使用重疊預估來驗證對象一致性。
- **資料合作區段共用** — 資料合作共用中的組織會雜湊受眾區段，以擴大鎖定目標範圍，同時維持隱私權法規遵循和資料控管控制。
- **多沙箱受眾同盟** — 全球企業可在各地區沙箱共用受眾區段，以便在各市場間提供一致的客戶目標定位，同時遵守地區資料常駐要求。
- **跨合作夥伴啟用的忠誠度方案** — 忠誠度聯盟與參與商戶共用忠誠度等級區段，讓每個合作夥伴都能向共用的客戶群提供適合等級的促銷活動。
- **測量與歸因共同作業** — 廣告商與媒體合作夥伴共用轉換區段，因此合作夥伴可以比對公開的使用者與轉換者，以測量促銷活動的成效。

## 關鍵績效指標

以下KPI有助於評估對象共同作業實施是否成功。

| KPI | 說明 | 測量方法 |
| --- | --- | --- |
| 對象重疊率 | 共用區段中符合傳送者與接收者的設定檔百分比 | [!DNL Segment Match]重疊預估報告 |
| 相符的受眾規模 | 已成功比對且可供啟用的設定檔數 | [!DNL Segment Match]個共用狀態和受眾母體計數 |
| 從相符受眾贏取新客戶 | 透過鎖定相符區段的促銷活動所贏取的淨新客戶 | 使用相符對象追蹤行銷活動的轉換 |
| 客戶贏取成本降低 | 使用相符對象與廣泛目標定位時，降低每次收購成本 | 比較相符與不相符對象績效的行銷活動成本分析 |
| 隱藏省錢 | 抑制贏取促銷活動的已知客戶，以節省媒體支出 | 前/後隱藏媒體支出比較 |
| 行銷活動效能提升 | 改善使用相符受眾之行銷活動的轉換率、點進率或參與 | A/B測試會比較相符的對象行銷活動與控制 |
| Collaboration時間 | 從區段共用啟動到啟用整備的經過時間 | [!DNL Segment Match]工作流程時間戳記 |

## 使用案例模式

此使用案例會遵循Audience Collaboration模式。

使用[!DNL Segment Match]在沙箱或組織間共用及比對對象區段。

**函式鏈：**&#x200B;區段選擇>比對設定>重疊估算>對象共用>啟用

## 應用程式

在此使用案例模式中使用以下應用程式。

- **[!DNL Real-Time CDP]** — 提供[!DNL Segment Match]功能以進行隱私權保護的對象共用、區段建立的對象評估，以及順流使用相符對象的目的地啟用。
- **[!DNL Adobe Experience Platform]** — 提供基礎資料基礎架構，包括[!DNL Segment Match]所依賴的身分解析、設定檔統一、資料控管和同意強制執行。

## 基礎函式

下列基本功能必須為此使用案例模式準備就緒。 對於每個函式，狀態會指出它通常是必要的、假設為預先設定或不適用。

| 基礎函式 | 狀態 | 必須準備就緒的專案 | Experience League參考 |
| --- | --- | --- | --- |
| 管理與治理 | 必填 | 傳送者與接收者組織都必須布建沙箱，並提供適當的角色與許可權。 管理[!DNL Segment Match]的使用者必須擁有檢視和共用區段、設定連線以及管理合作夥伴摘要的許可權。 ABAC原則應設定為控制哪些使用者可以起始和接受區段共用。 | [存取控制總覽](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| 資料模型與準備 | 已假設就位 | 設定檔和事件的XDM結構描述必須與必要的欄位群組同時存在。 必須建立並啟用[!DNL Real-Time Customer Profile]的設定檔和事件資料集。 資料模型必須支援用於區段比對的身分名稱空間（通常是雜湊電子郵件或雜湊電話）。 | [XDM系統總覽](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home) |
| 資料來源與收集 | 已假設就位 | 客戶資料必須透過已設定的資料來源（SDK、來源聯結器、批次擷取），主動流入[!DNL Experience Platform]。 設定檔必須填入用於[!DNL Segment Match]的身分型別（例如雜湊電子郵件）。 | [來源概觀](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home) |
| 身分和設定檔設定 | 必填 | 必須為用於區段比對的識別碼設定身分名稱空間。 傳送者與接收者都必須使用相容的身分名稱空間。 必須設定合併原則以正確統一設定檔。 應建立身分連結規則，以確保正確的設定檔解析度。 | [身分識別服務總覽](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home) |
| 對象定義與細分 | 必填 | 必須定義並評估Source對象，才能透過[!DNL Segment Match]共用。 應使用[!DNL Segment Builder]或[!DNL Audience Composition]建立對象，並完成批次評估。 只有批次評估的對象符合[!DNL Segment Match]共用的條件。 | [分段服務總覽](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home) |

## 支援功能

以下功能可擴大此使用案例模式，但不是核心執行的必要功能。

| 支援功能 | 狀態 | 為什麼這很重要 | Experience League參考 |
| --- | --- | --- | --- |
| 計算/衍生屬性建立 | 推薦 | 計算出的屬性（例如期限購買值、參與分數或產品相似性）可建立更精確的區段以進行共用。 品質較高的輸入區段可帶來更有價值的受眾共同作業。 | [計算屬性總覽](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| 資料生命週期管理 | 推薦 | 同意和資料保留政策可確保共用區段遵守隱私權法規。 資料集到期原則有助於管理接收對象資料的生命週期。 同意執行可防止共用已選擇退出的設定檔。 | [進階資料生命週期管理概觀](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| 資料使用標籤和實作 | 已包含 | 共用區段之前，必須先評估資料治理原則，以確保法規遵循。 身分欄位和設定檔屬性上的標籤決定了可以共用的內容。 執行治理可防止將未授權的資料納入區段共用中。 | [資料控管概觀](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home) |
| 監控與可觀察性 | 推薦 | 監視[!DNL Segment Match]共用程式、重疊預估工作及啟動資料流程，有助於及早偵測失敗。 可針對共用失敗或意外地低匹配率來設定警報。 | [可觀察性深入分析概觀](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| 報告與分析 | 推薦 | 測量使用相符對象之行銷活動的績效可驗證共同作業的價值。[!DNL Customer Journey Analytics] 分析可比較相符的對象行銷活動與控制組的效能。 | [CJA概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) |

## 應用程式函式

此計畫會從應用程式功能目錄中執行下列功能。 函式會對應至實作階段，而非編號步驟。

### [!DNL Real-Time CDP]

| 函式 | 實作階段 | 說明 |
| --- | --- | --- |
| 對象評估 | 階段1：區段選擇與準備 | 使用批次評估來評估區段成員資格，以產生將透過[!DNL Segment Match]共用的對象 |
| 對象構成 | 階段1：區段選擇與準備 | 選擇性地撰寫衍生的對象（排名、分割、排除、擴充），以建立更多目標區段以供共用 |
| 同意與治理實施 | 第2階段：符合設定與控管 | 在共用區段前強制執行資料使用原則和同意偏好設定以確保法規遵循 |
| Audience Activation | 階段5：相符的Audience Activation | 將透過[!DNL Segment Match]收到的相符對象發佈到外部目的地以進行目標定位或隱藏 |
| 目的地設定 | 階段5：相符的Audience Activation | 設定將啟動相符對象的外部目的地的連線 |

## 先決條件

- 寄件者和接收者組織皆有[!DNL Real-Time CDP]已布建[!DNL Segment Match]權益
- [!DNL Segment Match]已針對參與共同作業的組織或沙箱啟用
- 已在[!DNL Segment Match] UI中的寄件者和接收者組織之間建立合作夥伴連線
- 兩個組織都使用相容的身分名稱空間（例如，兩個組織都設定了雜湊電子郵件）
- 已使用非零母體定義及評估Source對象
- 資料治理原則已設定，資料使用標籤已套用至相關資料集和欄位
- 雙方的使用者都有管理[!DNL Segment Match]連線、共用和摘要的必要許可權
- 在設定檔中填入同意欄位，以在共用前啟用同意型篩選

## 實作選項

下列選項說明使用[!DNL Segment Match]實作對象共同作業的不同方法。 選取最適合您的組織結構和共同作業需求的選項。

### 選項A：直接區段共用（一對一）

此選項最適合用於兩個特定組織之間的雙邊合作關係，例如廣告商和發佈商，或共同行銷安排中的兩個品牌。

**運作方式：**

在直接的一對一區段共用中，傳送者組織會選取一或多個評估過的受眾、與特定合作夥伴組織起始共用，而接收者會接受共用。 重疊預估會自動執行，以在共用完成之前向雙方顯示相符設定檔的百分比和數量。

寄件者定義用於比對的身分名稱空間，並選取要共用的區段。 接收者會檢閱傳入的共用，接受共用，然後相符的對象會出現在下游啟用的對象清單中。 只交換雜湊身分重疊 — 底層PII或設定檔屬性資料不會跨越組織界限。

此方法簡單明瞭，而且能讓雙方完全掌控。 傳送者會確切選擇要分享的內容以及與誰分享，而接收者可選擇接受或拒絕每個分享。

**主要考量事項：**

- 需要兩個組織之間的明確合作夥伴連線設定
- 兩個組織必須同意身分名稱空間以進行比對
- 重疊預估可提供承諾前的透明度
- 每個共用都必須個別管理及監控

**優點：**

- 簡單、容易理解的雙邊工作流程
- 在共用前透過重疊估算實現完全透明
- 精細控制 — 傳送者會精確選擇要共用的區段
- Privacy-safe — 僅使用雜湊識別碼來比對
- 接收者可以選擇接受或拒絕股份

**限制：**

- 與許多合作夥伴同時合作時，無法有效擴展
- 每個合作關係都需要個別的連線設定和管理
- 每個新區段必須重複共用設定

**Experience League：**

- [區段比對概觀](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)
- [區段比對疑難排解](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/troubleshooting)

### 選項B：多合作夥伴區段分佈（一對多）

此選項最適合需要同時與多個合作夥伴共用區段的組織，例如零售媒體網路與多個品牌廣告商共用購買型區段，或控股公司將區段分送至附屬品牌。

**運作方式：**

在一對多分佈模式中，傳送者組織與多個夥伴組織建立[!DNL Segment Match]連線，並與每個夥伴組織共用相同或不同的區段。 傳送者管理合作夥伴關係組合，並可根據關係和使用案例選擇性地與不同合作夥伴分享不同受眾區段。

每個合作夥伴連線都獨立運作 — 重疊估算、共用接受和啟用都由每個合作夥伴管理。 傳送者可控制每個合作夥伴接收哪些區段，進而啟用差異化的共同作業策略（例如，高階合作夥伴接收更細微的區段，標準合作夥伴接收更廣的區段）。

此方法使用與選項A相同的基礎[!DNL Segment Match]機制，但大規模套用它並搭配操作架構來管理多個同時存在的合作關係。

**主要考量事項：**

- 需要強大的營運流程來管理多個合作關係
- 治理政策必須考慮與多個外部當事方共用相同的區段
- 每個合作夥伴可能會使用不同的身分名稱空間，需要彈性設定
- 重疊率依合作夥伴而異，需要依合作夥伴進行評估

**優點：**

- 調整合作夥伴生態系統的受眾共同作業
- 各合作夥伴的差異化共用策略
- 集中管理一個組織的所有傳出區段共用
- 每個合作關係會維持獨立的治理和同意控制

**限制：**

- 每增加一個合作夥伴，營運複雜性就會增加
- 監視和疑難排解必須依每個合作夥伴執行
- 每個新合作夥伴連線都需要進行治理審查
- 合作夥伴不會看到彼此的資料或共用狀態

**Experience League：**

- [區段比對概觀](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)

### 選項C：跨沙箱對象同盟

此選項最適合擁有多個[!DNL Experience Platform]沙箱（例如區域沙箱、品牌特定沙箱或環境特定沙箱）且需要跨內部邊界共用受眾區段而不移動原始資料的大型企業。

**運作方式：**

跨沙箱對象同盟使用[!DNL Segment Match]，而不是在個別組織之間共用，以便在相同組織中的沙箱之間共用對象區段。 這可讓全球行銷團隊在中央沙箱中建立區段，並與區域沙箱共用，或讓品牌特定的沙箱彼此共用隱藏清單。

工作流程會反映直接區段共用（選項A），但在組織界限內運作。 沙箱到沙箱的連線是透過[!DNL Segment Match]建立的，而且區段是使用相同的隱私權安全比對程式來共用。 接收沙箱會將相符的受眾視為新受眾，可透過其本身本機設定的目的地啟用。

當資料駐留要求禁止在地區之間移動原始客戶資料，但允許受眾層級的共同作業時，此方法尤其有用。

**主要考量事項：**

- 需要支援跨沙箱共用的[!DNL Segment Match]權益
- 身分名稱空間必須在沙箱中保持一致
- 每個沙箱中的合併原則可能會以不同方式解析設定檔，這可能會影響匹配率
- 治理原則可依每個沙箱獨立套用

**優點：**

- 啟用對象共同作業，而不需跨沙箱界限移動原始資料
- 支援資料常駐和地區法規遵循需求
- 運用現有的組織身分基礎結構
- 由於共用發生在相同的組織內，因此可簡化治理檢閱

**限制：**

- 需要跨沙箱一致的身分名稱空間設定
- 匹配率取決於沙箱之間的合併原則一致性
- 無法滿足跨組織的共同作業需求
- 可能需要沙箱工具來同步架構和設定

**Experience League：**

- [區段比對概觀](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)
- [沙箱概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sandbox/home)

### 選項比較

下表比較各個關鍵條件的三個實作選項。

| 條件 | 選項A：直接區段共用 | 選項B：多夥伴分銷 | 選項C：跨沙箱同盟 |
| --- | --- | --- | --- |
| 最適合 | 雙邊合作關係 | 生態系統規模的協同合作 | 內部跨沙箱共用 |
| 複雜性 | 低 | 高 | 中 |
| 合作夥伴數量 | 1 | 許多 | 內部沙箱 |
| 治理額外負荷 | 低 | 高（每個合作夥伴審查） | Medium （組織內） |
| 營運管理 | 簡單 | 需要合作夥伴管理架構 | 稽核 |
| 資料常駐支援 | 不適用 | 取決於合作夥伴位置 | 強 |
| 需要 | 合作夥伴連線設定 | 多個合作夥伴連線 | 跨沙箱[!DNL Segment Match] |

### 選擇正確的選項

使用下列決定指引，選取適當的實作方法：

1. **您是否與外部組織或您自己的組織合作？**
   - 外部組織：繼續到問題2。
   - 在您自己的組織內（跨沙箱）：選擇&#x200B;**選項C** （跨沙箱同盟）。

2. **您將與多少外部合作夥伴共同作業？**
   - 單一夥伴：選擇&#x200B;**選項A** （直接區段共用）。
   - 多重夥伴：選擇&#x200B;**選項B** （多重夥伴分配）。

3. **您是否有資料駐留限制，無法跨地區移動原始資料？**
   - 是：選擇&#x200B;**選項C**，無論合作夥伴是內部還是外部 — 使用跨沙箱共用來維護資料位置。

## 實作階段

下列階段說明使用[!DNL Segment Match]進行對象共同作業的端對端實作程式。

### 階段1：選取並準備區段

**應用程式函式：** [!DNL Real-Time CDP]：對象評估，[!DNL Real-Time CDP]：對象構成

此階段涉及定義及評估將透過[!DNL Segment Match]共用的對象區段。 來源區段必須以非零母體完全評估，才能選取它們進行共用。 此階段也涵蓋可選的對象構成，以在共用前調整區段。

此階段中的&#x200B;**決定點：**

>[!NOTE]
>
>**決定：對象定義方法**
>
>應該如何建立共用的來源對象？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 區段產生器（區段規則） | 根據設定檔屬性、事件或區段成員資格的標準受眾定義 | 支援批次、串流和邊緣評估；定義條件時最具彈性 |
>| 對象構成 | 需要在現有區段上進行排名、分割、排除或擴充作業的衍生對象 | 僅支援批次評估；每個沙箱限製為10個構成畫布 |
>| 同盟對象構成 | 從外部Data Warehouse查詢建置的對象，不會將資料擷取到[!DNL Experience Platform] | 需要[!DNL Federated Audience Composition]權益；資料保留在倉儲中 |

>[!NOTE]
>
>**決定：對象評估方法**
>
>[!DNL Segment Match]需要批次評估的對象。 應如何排程評估？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 排定的批次（每日） | 每日對象重新整理已夠的標準使用案例 | 預設評估排程；最容易管理 |
>| 隨選批次 | 您想要立即共用最新受眾的臨時共用需求 | 需要手動觸發；適用於對時間敏感的合作 |
>| 自訂排程 | 與合作夥伴啟用期間相符的特定計時需求 | 設定自訂cron排程；更複雜但精確 |

**UI導覽：**&#x200B;客戶>對象>建立對象>建置規則（針對[!DNL Segment Builder]）或撰寫對象（針對[!DNL Audience Composition]）

**金鑰組態詳細資料：**

- 使用設定檔屬性、行為事件和/或區段成員資格來定義對象條件
- 確定對象使用的合併原則與用於[!DNL Segment Match]的身分名稱空間相容
- 評估後驗證對象母體是否非零
- 套用隱藏規則以排除不應共用的設定檔（例如已選擇退出資料共用的設定檔）

**選項差異的位置：**

選項A的&#x200B;**（直接區段共用）：**
準備您要與單一合作夥伴共用的特定區段。 注重品質而非數量 — 組織區段，為合作關係提供明確的價值。

選項B （多夥伴分配）的&#x200B;**：**
準備可與不同合作夥伴共用的區段組合。 如果不同的合作夥伴需要不同的受眾定義，請考慮建立合作夥伴專用區段。 使用一致的命名慣例來管理跨夥伴關係的區段。

選項C （跨沙箱同盟）的&#x200B;**：**
確保傳送沙箱中的來源對象使用接收沙箱中存在的身分名稱空間。 確認合併原則已跨沙箱對齊。

**Experience League檔案：**

- [區段產生器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [對象構成概觀](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [評估方式](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home#evaluation-methods)
- [Profile Query Language參考](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### 階段2：設定比對和治理

**應用程式函式：** [!DNL Real-Time CDP]：同意與治理強制執行

此階段會在組織或沙箱之間建立[!DNL Segment Match]連線，設定用於比對的身分名稱空間，並確保資料治理原則允許共用。 治理執行作為原則閘道，必須在共用任何區段資料之前清除。

此階段中的&#x200B;**決定點：**

>[!NOTE]
>
>**決定：符合的身分名稱空間**
>
>哪一個身分名稱空間可用來比對傳送者與接收者之間的設定檔？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 雜湊電子郵件(SHA-256) | 兩個組織都會收集電子郵件地址，且可一致地雜湊這些地址 | 最常見的比對索引鍵；消費者使用案例的高比對率；雙方必須使用相同的雜湊演演算法 |
>| 雜湊電話號碼 | 電子郵件不一定能使用，但電話號碼卻能使用 | 在許多市場中，涵蓋範圍低於電子郵件；適合行動優先的對象 |
>| 自訂名稱空間（例如雜湊熟客ID） | 組織共用共同的忠誠度或會員方案ID | 已知共用客戶群的最高匹配率；需要預先存在的共用ID基礎結構 |
>| 多個名稱空間 | 匹配率最大化至關重要，兩個組織都有多個一致的識別碼 | 增加匹配率但增加複雜性；每個名稱空間必須獨立設定 |

>[!NOTE]
>
>**決定：資料控管評論**
>
>共用前必須完成哪些治理檢查？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 標準治理評估 | 標準資料使用標籤和原則的典型使用案例 | 針對資料集標籤評估行銷動作「匯出至第三方」；解決任何違規後再共用 |
>| 使用同意篩選功能加強治理 | 與外部合作夥伴共用，其中必須明確驗證同意 | 新增同意型篩選以排除未分享同意的設定檔（例如consent.share.val = &#39;n&#39;）；較嚴格但較安全 |
>| 內部治理審查 | 相同組織中的跨沙箱共用 | 減輕控管需求，因為資料會保留在組織界限內；仍可驗證資料使用標籤 |

**UI導覽：**&#x200B;客戶>對象>區段比對>合作夥伴連線

**金鑰組態詳細資料：**

- 透過在傳送者與接收者組織之間交換連線識別碼來建立合作夥伴連線
- 設定用於兩側比對的身分名稱空間
- 針對與區段共用相關的行銷動作，執行資料治理原則評估
- 確認同意欄位已填入設定檔中，且未分享同意的設定檔已排除
- 檢閱共用中包含的資料集和結構描述欄位上的資料使用標籤

**選項差異的位置：**

選項A的&#x200B;**（直接區段共用）：**
建立單一合作夥伴連線。 使用您的特定合作夥伴設定身分識別名稱空間。 治理審查聚焦於雙邊關係。

選項B （多夥伴分配）的&#x200B;**：**
建立並管理多個合作夥伴連線。 每個合作夥伴可能需要個別的治理審查。 記錄每個合夥關係的治理核准。 考慮建立治理檢查清單，以簡化合作夥伴上線。

選項C （跨沙箱同盟）的&#x200B;**：**
在組織內建立沙箱到沙箱連線。 治理通常比較簡單，因為共用是在內部進行。 確保各個沙箱中的身分名稱空間保持一致。

**Experience League檔案：**

- [區段比對概觀](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)
- [資料控管概覽](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [原則執行](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/enforcement/overview)
- [同意與偏好設定](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)

### 階段3：預估重疊

**應用程式函式：** [!DNL Real-Time CDP]：對象評估（用於預估重疊）

此階段會執行傳送者的區段與接收者的設定檔基底之間的重疊估算。 重疊預估可在確認完整區段份額之前，為雙方提供預期的相符量及百分比，以針對共同作業的價值做出明智的決策。

此階段中的&#x200B;**決定點：**

>[!NOTE]
>
>**決定：要繼續的重疊臨界值**
>
>何謂最低重疊率值得繼續使用完整區段共用的理由？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 沒有最低臨界值 | 探索合作關係或任何重疊可提供價值時 | 適用於您測試關係的初始共同作業 |
>| 低臨界值(1-5%) | 大規模受眾共同作業，即使很小的重疊也代表大量的流量 | 對於具有大量受眾群的發佈者 — 廣告商關係而言，這是很常見的現象 |
>| Medium臨界值(5-20%) | 預期會有有意義的重疊的標準合作關係 | 適用於共同行銷或同產業共同作業的典型方式 |
>| 高臨界值(20%+) | 建立合作關係，必須具備強大的受眾一致性 | 常用於忠誠度聯盟或緊密整合的品牌合作關係 |

**UI導覽：**&#x200B;客戶>受眾>區段比對>共用>估計重疊

**金鑰組態詳細資料：**

- 選取要包含在重疊預估中的區段
- 檢閱顯示相符設定檔計數和百分比的重疊報表
- 與兩邊的利害關係人共用重疊預估結果以供核准
- 記錄重疊量度，作為衡量共同作業成效的基準
- 如果重疊低於可接受的臨界值，請考慮在繼續之前調整區段定義或身分比對設定

**Experience League檔案：**

- [區段比對概觀](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)

### 第4階段：共用對象

**應用程式函式：** [!DNL Real-Time CDP]：對象評估（共用執行）

此階段會執行從傳送者到接收者的實際區段共用。 傳送者會為選取的區段起始共用，而接收者則接受傳入的共用。 接受後，相符的對象就會出現在接收者的對象清單中，成為可用於下游啟用的新對象。

此階段中的&#x200B;**決定點：**

>[!NOTE]
>
>**決定：共用方向**
>
>此共同作業的共用模式為何？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 單向共用（傳送者至接收者） | 不對稱合作關係，僅一方提供受眾資料 | 最簡單的模型；傳送者共用，接收者啟用；常見於廣告商 — 發佈者關係 |
>| 雙向共用 | 雙方都受益於彼此共用受眾 | 兩個組織同時作為傳送者與接收者；需要兩種共用設定；在共同行銷合作夥伴中很常見 |

>[!NOTE]
>
>**決定：共用重新整理步調**
>
>共用的對象多久更新一次區段會籍？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 一次性共用 | 測試共同作業或使用固定對象的特定行銷活動 | 最簡單；不需持續維護；對象會隨著時間逐漸過時 |
>| 循環共用（與批次評估一致） | 持續的合作關係，受眾會籍會有所變更，需要保持最新狀態 | 需要監控重新整理狀態；最常見於生產共同作業 |

**UI導覽：**&#x200B;客戶>受眾>區段比對>共用>建立共用（寄件者）或接受共用（接收者）

**金鑰組態詳細資料：**

- 傳送者選取要共用的區段，並與已設定的合作夥伴起始共用
- 接收者會檢閱傳入的共用詳細資訊（區段名稱、預估大小、使用的身分名稱空間）
- 接收者接受共用，以便在其沙箱中建立相符的受眾
- 驗證相符的對象是否顯示在接收者的對象清單中，以及預期母體是否存在
- 確認相符的對象已正確標示為治理追蹤

**選項差異的位置：**

選項A的&#x200B;**（直接區段共用）：**
與您的合作夥伴執行單一共用。 監視共用狀態，並在接收者端驗證相符的閱聽眾。

選項B （多夥伴分配）的&#x200B;**：**
獨立執行每個合作夥伴的共用。 追蹤所有合作關係中的共用狀態。 請考慮錯開共用啟動以管理處理負載。

選項C （跨沙箱同盟）的&#x200B;**：**
執行跨沙箱共用。 相符的對象會出現在接收沙箱的對象清單中。 確認接收沙箱具有用於下游啟用的必要目的地設定。

**Experience League檔案：**

- [區段比對概觀](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)
- [區段比對疑難排解](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/troubleshooting)

### 階段5：啟用相符的對象

**應用程式函式：** [!DNL Real-Time CDP]：目的地組態，[!DNL Real-Time CDP]： Audience Activation

此階段會將相符的受眾（在接收者端）啟動至外部目的地，以用於鎖定目標、隱藏或下游用途。 系統會將相符的對象視為接收器沙箱中的其他任何對象處理，並可透過標準目的地啟用工作流程啟用。

此階段中的&#x200B;**決定點：**

>[!NOTE]
>
>**決定：相符對象的目的地型別**
>
>應在何處啟用相符的對象？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| Advertising目的地（Google、Meta、交易台） | 使用相符的對象進行廣告目標定位或隱藏 | 需要目的地連線和驗證；需受目的地特定的速率限制和格式要求的約束 |
>| 雲端儲存空間目標(S3、Azure、GCS) | 將相符的對象匯出為檔案以用於外部系統 | 支援檔案格式自訂；需要批次匯出排程；下游處理靈活 |
>| CRM/行銷自動化目的地 | 擴充CRM記錄，或透過相符的受眾資料觸發自動化行銷工作流程 | 需要欄位對應到CRM結構描述；這對銷售與行銷對應很有用 |
>| Personalization目的地（網頁、應用程式） | 針對站上個人化使用相符的對象成員資格 | 需要邊緣評估相符的對象或串流啟用；延遲因目的地而異 |

>[!NOTE]
>
>**決定：啟用排程**
>
>相符對象匯出至目的地的頻率為何？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 每日增量匯出 | 透過定期對象更新進行標準啟用 | 僅匯出已變更的設定檔；資料量較低；最常見於進行中的行銷活動 |
>| 每日完整匯出 | 每次都需要完整受眾檔案的目的地 | 較高的資料量；確保目的地擁有完整的對象狀態；有些目的地需要完整匯出 |
>| 隨選啟用 | 臨機行銷活動啟動或時效性高的啟用 | 手動觸發；略過排程步調；僅適用於批次目的地 |

**使用者介面導覽：**&#x200B;連線>目的地>目錄（目的地設定）或瀏覽>選取目的地>啟用對象（啟用）

**金鑰組態詳細資料：**

- 使用適當的驗證認證設定目的地連線
- 將相符對象的設定檔屬性對應至目的地欄位（身分欄位、設定檔屬性、區段會籍）
- 設定匯出排程（增量與完整、每日與自訂）
- 監視啟動資料流，以確認已成功匯出相符的受眾設定檔
- 驗證目的地監視檢視中的啟用量度（已匯出設定檔、記錄失敗）

**選項差異的位置：**

選項A的&#x200B;**（直接區段共用）：**
接收者會透過其標準目的地工作流程啟用相符的對象。 在正常目的地啟用後，不需要特殊設定。

選項B （多夥伴分配）的&#x200B;**：**
每個接收者組織會透過其各自的目的地，獨立啟用相符的受眾。 傳送者無法看到接收者端啟用。

選項C （跨沙箱同盟）的&#x200B;**：**
接收沙箱必須具有自己的目的地設定。 目的地無法在沙箱之間共用。 確定接收沙箱已建立必要的目的地連線。

**Experience League檔案：**

- [目標概覽](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [目的地目錄](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)
- [監視目的地的資料流](https://experienceleague.adobe.com/en/docs/experience-platform/dataflows/ui/monitor-destinations)
- [啟動護欄](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)

## 實施考量

在實施之前和期間請檢閱下列考量事項，以避免常見問題並最佳化您的對象共同作業。

### 護欄和限制

- [!DNL Segment Match]使用雜湊識別碼來比對 — 沒有PII跨越組織界限。 請參閱[區段比對總覽](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)。
- 只有批次評估的對象可以透過[!DNL Segment Match]共用。 串流和邊緣評估的區段必須先轉換為批次評估，才能共用。
- 每個沙箱最多4,000個區段定義適用於來源和已接收的區段。 請參閱[分段護欄](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)。
- 重疊預估準確度取決於相符識別碼的數量。 較小的對象可能會顯示較不精確的估計。
- 啟用護欄會套用至相符的對象，就像任何其他對象一樣 — 每個目的地最多100個資料流。 請參閱[啟動護欄](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)。
- 構成對象會根據批次排程進行評估，每個沙箱限製為10個構成畫布。 請參閱[對象構成護欄](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/guardrails)。

### 常見陷阱

- **傳送者與接收者之間的身分雜湊不一致：**&#x200B;如果兩個組織都使用雜湊電子郵件地址，但使用不同的雜湊演演算法、標準化規則或Salt值，符合率將接近零。 雙方在建立連線之前，必須同意確切的雜湊規格（例如，小寫、修剪後之電子郵件的SHA-256）。
- **共用對象而不進行治理檢閱：**&#x200B;起始區段共用而不評估資料使用原則，可能會導致遵循性違規。 在與外部組織共用區段之前，請一律針對「匯出至第三方」行銷動作執行治理原則評估。
- **由於身分涵蓋範圍差距，符合率很低：**&#x200B;如果寄件者的對象主要由ECID （匿名Cookie）識別，但相符的名稱空間是雜湊電子郵件，則符合率會非常低，因為匿名設定檔沒有電子郵件地址。 確認來源對象有足夠的涵蓋範圍來設定相符的身分名稱空間。
- **在接收者端忘記接受共用：**&#x200B;在明確接受共用之前，共用的對象不會出現在接收者的對象清單中。 與接收者協調以確保及時被接受，尤其是對於時效性強的行銷活動。
- **由於評估排程未正確對齊，所以已過時的相符對象：**&#x200B;如果寄件者的來源對象每天進行評估，但[!DNL Segment Match]重新整理每週執行，則接收者端的相符對象可能不會反映最新的成員資格。 對齊評估並共用重新整理步調。

### 最佳實務

- 在設定[!DNL Segment Match]之前，在組織間建立正式的資料共用協定。 這應涵蓋允許的使用案例、資料治理要求、同意義務及終止程式。
- 使用重疊預估作為每個主要行銷活動的驗證工具 — 在認可之前執行預估以確保符合的對象符合最小大小和品質臨界值。
- 將描述性命名慣例套用至包含合作夥伴名稱、使用案例和日期的共用區段（例如「PartnerX_HighValue_Suppression_2026Q1」），以維持組織間的清晰度。
- 監視一段時間內的匹配率。 降低的符合率可能表示身分涵蓋範圍惡化、資料品質問題或合作夥伴客戶群發生變化。
- 區隔來源對象，以排除未填入相符身分名稱空間的設定檔。 這麼做可改善匹配率百分比，並提供更準確的重疊預估值。
- 對於雙向共用合作關係，請指定區段維護和重新整理排程的明確所有權，以避免混淆負責更新的組織。

### 權衡決定

>[!NOTE]
>
>**取捨：符合率與隱私權控制的比較**
>
>使用更多身分識別名稱空間（雜湊電子郵件、雜湊手機、裝置ID）進行比對，可提高匹配率，但會擴大表面區域，以利重新識別。 使用較少的名稱空間（僅限雜湊電子郵件）可提供較強大的隱私權保護，但可能會減少相符的對象人數。
>
>- **多個名稱空間優先：**&#x200B;較高的匹配率、較大的匹配對象，對行銷活動目標定位更有價值
>- **單一名稱空間偏好：**&#x200B;更強大的隱私權狀態、更簡單的控管檢閱、更低的規範遵循風險
>- **建議：**&#x200B;從單一名稱空間開始（雜湊電子郵件是最常見的），只有在符合率不足以符合使用案例時才新增其他名稱空間。 記錄每個新增名稱空間的隱私權影響評估。

>[!NOTE]
>
>**取捨：區段精細度與作業簡易度**
>
>與合作夥伴共用許多精細、高針對性的區段，可提供更多彈性來針對行銷活動進行目標定位，但會增加傳送者與接收者的作業複雜性。 共用較少、範圍較廣的區段可簡化管理，但會降低目標定位精確度。
>
>- **細微區段偏好：**&#x200B;精準目標定位、差異化的行銷活動、較高的關聯性
>- **廣泛區段偏好：**&#x200B;更簡單的管理、更少的共用可監視、更少的營運負荷
>- **建議：**&#x200B;從少數高值區段(2-5)開始，以建立新的合作關係。 隨著合作夥伴關係的成熟和運作程式的建立，提高精細度。 使用命名慣例和檔案來管理隨著區段計數增加的複雜性。

>[!NOTE]
>
>**取捨：重新整理頻率與處理成本**
>
>更頻繁地重新整理共用對象可讓相符對象保持最新狀態，但會增加處理負載，並可能耗用更多授權容量。 減少重新整理的頻率可降低成本，但讓相符的對象變得過時。
>
>- **經常重新整理偏好：**&#x200B;目前的對象會籍、更高的行銷活動關聯性、更好的隱藏正確性
>- **不常重新整理的好處：**&#x200B;處理成本較低、監控較簡單、授權消耗較少
>- **建議：**&#x200B;每日重新整理適用於大部分的生產共同作業。 若為時間敏感型使用案例（例如快閃銷售、事件型行銷活動），請考慮在行銷活動啟動前立即進行隨選重新評估和共用。

## 相關文件

下列資源提供在此使用案例模式中所使用功能的其他詳細資料。

### [!DNL Segment Match]

- [區段比對概觀](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)
- [區段比對疑難排解](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/troubleshooting)

### 細分與對象

- [Segmentation Service概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [區段產生器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [對象構成概觀](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Profile Query Language參考](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)
- [串流區段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [邊緣分段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)

### 身分和設定檔

- [Identity Service總覽](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [身分名稱空間概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/identity/features/namespaces)
- [合併原則概觀](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [即時客戶個人檔案總覽](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)

### 資料控管和同意

- [資料控管概覽](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [資料使用標籤概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/labels/overview)
- [原則執行](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/enforcement/overview)
- [同意與偏好設定](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)
- [同意和偏好設定欄位群組](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)

### 目的地和啟用

- [目標概覽](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [目的地目錄](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)
- [監視目的地的資料流](https://experienceleague.adobe.com/en/docs/experience-platform/dataflows/ui/monitor-destinations)

### 資料模型與結構

- [XDM系統概覽](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [結構描述組合基本面](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)

### 管理和存取控制

- [存取控制總覽](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home)
- [沙箱概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sandbox/home)

### 監視和可觀察性

- [警報概觀](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [可觀察性深入分析概觀](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)

### 護欄

- [即時客戶個人檔案護欄](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [分段護欄](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/guardrails)
- [啟動護欄](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)

### 教學課程

- [建立方案](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/union-schema)
- [為設定檔啟用資料集](https://experienceleague.adobe.com/en/docs/experience-platform/catalog/datasets/enable-for-profile)
