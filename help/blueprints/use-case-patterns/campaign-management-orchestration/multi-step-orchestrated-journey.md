---
title: 多步驟協調歷程
description: 瞭解如何透過分支和多點接觸歷程，隨時間推移使用等待、條件和多個訊息動作來引導設定檔。
solution: Journey Optimizer, Real-Time Customer Data Platform
source-git-commit: b2e496eb521fc3dd3290fccdd9a8203384934b88
workflow-type: tm+mt
source-wordcount: '8173'
ht-degree: 1%

---


# 多步驟協調歷程

本指南提供使用[!DNL Adobe Journey Optimizer] (AJO)和[!DNL Real-Time Customer Data Platform] (RT-CDP)建置多步驟協調歷程的完整實作藍圖。 它專為需要協調分支、多點觸控客戶歷程，以隨著時間推移傳送多則訊息的解決方案架構師、行銷技術人員和實作工程師所設計。

它會顯示所有可行的實作選項、每個設定點的決定考量事項，以及[!DNL Adobe Experience League]檔案的連結。 使用本指南來規劃、設定和驗證您的多步驟歷程實作。

## 使用案例概述

多步驟協調的歷程會處理單一訊息不足以達成所要客戶結果的業務案例。 歷程不會是一次性傳送，而是透過一系列接觸點（電子郵件、簡訊訊息、推播通知或應用程式內訊息）引導每個設定檔，間隔為數天或數週，並根據設定檔屬性、行為訊號或事件資料調整路徑的分支邏輯。

這些歷程是AJO中最複雜的行銷活動模式。 它們結合受眾型或事件型進入與動作節點（訊息）、條件節點（分支邏輯）、等待節點（時間延遲）和退出條件（轉換事件或逾時）的畫布。 每個設定檔會以自己的步調獨立地完成歷程，在每個步驟接收內容相關的內容。

此模式包含更簡單的模式 — 針對單一傳送行銷活動批次傳出訊息啟用，以及針對單一事件回應的事件觸發訊息。 當使用案例需要隨時間透過多次互動來培養輪廓時，請使用此模式。

## 主要業務目標

此使用案例模式支援下列業務目標。

### 提升客戶保留率

透過價值導向的體驗和持續培養的關係，讓現有客戶持續參與並更新。

**KPI：**&#x200B;保留率、客戶期限值、參與度

[進一步瞭解如何改善客戶保留率](/help/blueprints/business-objectives/customer-experience/improve-customer-retention.md)

### 改善客戶入門

透過簡化的個人化歡迎體驗和啟動歷程，加快新客戶的價值實現時間。

**KPI：**&#x200B;參與度、保留率、轉換率

[進一步瞭解如何改善客戶入門](/help/blueprints/business-objectives/customer-experience/improve-customer-onboarding.md)

### 與休眠客戶重新互動

使用根據行為訊號的目標重新啟用行銷活動，以贏回非作用中或失效的客戶。

**KPI：**&#x200B;參與度、保留率、轉換率

### 復原放棄的購物車和歷程

透過及時且個人化的後續追蹤，重新吸引在購買、應用程式或註冊流程中休假的使用者。

**KPI：**&#x200B;轉換率、遞增收入、參與

[進一步瞭解如何復原放棄的購物車和歷程](/help/blueprints/business-objectives/customer-experience/recover-abandoned-carts-journeys.md)

## 戰術使用案例範例

以下案例說明多步驟協調歷程模式的常見應用程式。

- **客戶入門系列** — 歡迎電子郵件，隨後是功能教育，然後在註冊後的前14天提供啟用提示
- **重新參與滴漏式行銷活動** — 先傳送提醒電子郵件，再傳送獎勵優惠方案，接著傳送逾期三週之失效客戶的最終通知
- **忠誠度里程碑歷程** — 層級升級通知，接著是專屬優惠，然後在會員資格週年臨近時收到續約提醒
- **贏回順序** — 「我們很想念您」電子郵件，接著透過電子郵件提供折扣優惠，然後是最後的SMS提醒，提醒買家購買失敗
- **產品採用歷程** — 試用歡迎、使用提示，然後隨著試用期進行而提示升級
- **訂閱續約順序** — 30天通知、7天提醒，然後是即將續約的到期日訊息
- **購買後的培養** — 感謝您電子郵件、使用指南、交叉銷售建議，然後在購買30天後提出檢閱要求

## 關鍵績效指標

使用下列KPI來評估您的多步驟協調歷程實作的成效。

| KPI | 說明 | 測量方法 |
| --- | --- | --- |
| 歷程完成率 | 完成完整歷程且未提早退出的設定檔百分比 | 歷程報告：已退出（完成）/已進入 |
| 步驟轉換率 | 從一個步驟進展到下一個步驟的設定檔百分比 | 歷程報告中的每節點量度 |
| 管道參與率 | 每個接觸點的開啟率、點進率和回應率 | 每則訊息的傳遞和參與量度 |
| 退出條件轉換率 | 在歷程逾時前觸發退出事件的設定檔百分比（例如，購買、註冊） | 退出條件點選計數/輸入的總數 |
| 轉換時間 | 從歷程進入到退出條件事件的平均持續時間 | Journey Analytics：從進入時間戳記到轉換事件時間戳記 |
| 歷程還車率 | 在每個步驟停止參與的設定檔百分比（流失分析） | 跨歷程步驟的CJA流失視覺效果 |
| 保留/重新參與率 | 目標設定檔返回作用中狀態的百分比 | CJA中的歷程後行為分析 |

## 使用案例模式

**多步驟協調歷程**

引導設定檔完成分支、多重接觸歷程，其中包含一段時間的等待、條件和多個訊息動作。

**函式鏈：**&#x200B;對象評估>歷程執行（多節點） >條件分支>訊息傳送(xN) >退出條件>報告

## 應用程式

以下應用程式可用來實作此使用案例模式。

- **[!DNL Adobe Journey Optimizer](AJO)** — Journey Orchestration引擎、訊息製作、頻道設定、內容實驗、頻率和衝突管理，以及報告
- **[!DNL Adobe Real-Time Customer Data Platform](RT-CDP)** — 歷程專案對象的對象評估和定義、個人化的設定檔資料和條件分支
- **[!DNL Adobe Experience Platform](AEP)** — 設定檔存放區、身分服務、事件資料擷取和基礎資料基礎架構

## 基礎函式

下列基本功能必須為此使用案例模式準備就緒。 對於每個函式，狀態會指出它通常是必要的、假設為預先設定或不適用。

| 基礎函式 | 狀態 | 必須準備就緒的專案 | Experience League參考 |
| --- | --- | --- | --- |
| 管理與治理 | 已假設就位 | 具有歷程建立和發佈許可權的AJO沙箱。 必須設定歷程中使用之所有頻道的頻道介面。 使用者必須擁有適當的角色（行銷人員、Journey Manager）以及歷程和行銷活動許可權。 | [沙箱總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sandbox/home)，[存取控制總覽](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| 資料模型與準備 | 必填 | XDM設定檔結構描述具有用於條件分支和跨多則訊息（例如忠誠度等級、產品興趣、參與分數）個人化的屬性。 用於轉換事件的體驗事件結構描述可促進退出條件和條件評估（例如購買事件、表單提交）。 | [XDM系統總覽](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)，[結構描述組合基本概念](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| 資料來源與收集 | 已假設就位 | 如果退出條件或條件取決於即時事件（例如，退出歷程的購買事件），則事件串流必須有效。 分支中使用的設定檔屬性的批次擷取。 適用於行為事件收集的網頁SDK或伺服器端API。 | [串流擷取總覽](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/streaming/overview)，[來源總覽](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home) |
| 身分和設定檔設定 | 已假設就位 | 設定檔必須在歷程中使用的所有管道（電子郵件、簡訊、推播）中可解析。 如果歷程橫跨網頁和行動接觸點，則必須設定跨裝置身分識別。 必須為沙箱設定合併原則。 | [身分識別服務總覽](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)，[合併原則總覽](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview) |
| 對象定義與細分 | 必填 | 必須為對象讀取的歷程定義進入對象。 區段也可在條件節點中用於分支。 評估方法（批次或串流）必須符合歷程輸入要求。 | [區段服務總覽](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)，[區段產生器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder) |

## 支援功能

以下功能可擴大此使用案例模式，但不是核心執行的必要功能。

| 支援功能 | 狀態 | 為什麼這很重要 | Experience League參考 |
| --- | --- | --- | --- |
| 計算/衍生屬性建立 | 推薦 | 參與分數、上次活動後間隔天數或期限購買值等運算屬性可改善條件分支邏輯，進而實現更智慧型的歷程路徑決策。 | [計算屬性總覽](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| 資料生命週期管理 | 推薦 | 歷程事件資料保留應設定資料集到期原則，以管理儲存並遵守資料保留法規。 同意實作可確保只有選擇加入的設定檔會在每個頻道接觸點接收訊息。 | [進階資料生命週期管理概觀](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)，[資料集有效期](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/ui/dataset-expiration) |
| 資料使用標籤和實作 | 推薦 | 治理標籤可確保跨多個訊息接觸點實現合規的個人化，尤其是當歷程使用PII或敏感資料跨頻道進行個人化時，這點尤為重要。 | [資料控管概觀](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)，[資料使用標籤概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/labels/overview) |
| 監控與可觀察性 | 已包含 | 歷程執行監控有關處理失敗、設定檔專案瓶頸和傳送問題的警報。 對於延遲或失敗會影響客戶體驗的生產歷程至關重要。 | [警示概述](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)，[可觀察性深入分析概述](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| 報告與分析 | 已包含 | CJA funnel和整個歷程的流失分析提供比單獨的AJO原生報表更深入的insight。 啟用逐步轉換分析、同類群組比較和歷程最佳化。 | [CJA概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)，[Analysis Workspace概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home) |

## 應用程式函式

此計畫會從「應用程式功能目錄」中執行下列功能。 函式會對應至實作階段，而非編號步驟。

### [!DNL Journey Optimizer] (AJO)

| 函式 | 實作階段 | 說明 |
| --- | --- | --- |
| 通道設定 | 階段1：管道設定 | 為歷程中的每個訊息接觸點設定頻道介面（電子郵件、簡訊、推播） |
| 訊息製作 | 階段2：建立訊息內容 | 為每個歷程動作節點使用個人化、動態內容和範本製作訊息內容 |
| Journey Orchestration | 階段3：歷程設計與啟動 | 設計包含進入、動作、條件、等待和退出節點的多步驟歷程畫布；測試並發佈 |
| 頻率與業務規則 | 第4階段：控管和最佳化 | 設定頻率上限，以防止在歷程接觸點和其他並行行銷活動間傳送過多訊息 |
| 衝突與優先順序管理 | 第4階段：控管和最佳化 | 為與其他作用中通訊競爭的歷程指派優先順序分數並設定衝突偵測 |
| 內容實驗 | 第4階段：控管和最佳化 | 對歷程動作節點內的訊息內容執行A/B測試以最佳化效能 |
| 報告與效能分析 | 第5階段：報告與監控 | 監視歷程執行、每一步傳遞量度和參與績效 |

### [!DNL Real-Time CDP] (RT-CDP)

| 函式 | 實作階段 | 說明 |
| --- | --- | --- |
| 對象評估 | 階段1：管道設定（先決條件） | 定義並評估對象讀取歷程的進入對象；定義分支的條件對象 |
| 同意與治理實施 | 第4階段：控管和最佳化 | 在歷程訊息動作中強制執行同意偏好設定和資料使用原則 |

## 先決條件

開始實作之前，請先完成下列必要條件。

- [ ] AJO沙箱已布建歷程建立和發佈許可權
- [ ]至少有一個管道表面（電子郵件、簡訊或推播）已設定且作用中
- [ ]設定檔結構描述包含條件分支和個人化所需的屬性
- [ ]體驗事件結構描述已針對退出條件中使用的轉換事件進行設定
- [ ]事件串流對用於退出條件或事件觸發的進入中的即時事件有效
- [ 已針對跨管道設定檔解析設定]個身分名稱空間和合併原則
- [ 為每個訊息接觸點準備]個內容資產（影像、復本、CTA）
- [ 定義並評估]進入對象（適用於對象讀取的歷程）
- [ ]已設定觸發事件結構描述（針對事件觸發的歷程）
- [ ]個測試設定檔可用於歷程測試模式驗證
- [ 已檢閱]隱藏清單，且所有使用的管道都已更新

## 實作選項

請檢閱下列選項，以決定多步驟協調歷程的最佳方法。

### 選項A：對象讀取協調歷程

**最適合：**&#x200B;已知對象進入歷程並透過排程的接觸點進行之時間型Nurture序列 — 上線序列、更新序列、重新參與點滴、忠誠度里程碑歷程。

**運作方式：**

在歷程專案讀取對象，無論為一次性讀取或定期排程。 所有符合資格的設定檔同時進入歷程，然後以自己的步調在畫布中前進，受等待持續時間和條件評估管理。 每個設定檔的歷程路徑都是獨立的 — 有些可能會採用「已參與」分支，有些會根據其行為或屬性採用「未參與」分支。

在讀取對象活動執行時評估對象。 對於循環歷程，會在每次循環時重新評估對象，新的合格設定檔會進入歷程，而已在歷程中的設定檔會繼續其路徑。 此方法提供可預測的進入時間，非常適合排程的生命週期方案。

**主要考量事項：**

- 在歷程啟動之前，必須定義並評估對象
- 循環讀取允許在每個週期輸入新的限定元
- 歷程中的設定檔不會重新讀取；後續讀取時只會輸入新限定詞
- 對於受眾讀取的歷程，等待步驟的最短持續時間為1小時

**優點：**

- 可預測的入門時間與業務排程一致
- 支援大型受眾數量（每秒最多20,000個設定檔的預設限制）
- 可輕鬆針對已知受眾人口進行測試和監控
- 可排程為週期性輸入（每日、每週、每月）

**限制：**

- 輸入以批次為基礎，而非即時 — 設定檔會在排程讀取時間輸入，而不是在符合資格時輸入
- 不適用於需要立即回應的行為起始序列
- 讀取之間的對象變更不會反映在歷程中的設定檔

**Experience League：**

- [讀取對象活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [建立歷程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)

### 選項B：事件觸發的協調歷程

**最適合：**&#x200B;即時事件開始歷程的行為起始順序 — 購物車放棄升級、購買後培養、里程碑觸發的忠誠度歷程、試用啟動順序。

**運作方式：**

單一事件（例如，購買、購物車放棄、表單提交或應用程式安裝）會即時觸發個別設定檔的歷程登入。 收到事件時，設定檔會進入歷程，然後隨著條件、等待和分支的接觸點序列前進。 此方法結合事件觸發訊息的即時性與完整歷程的多步驟協調。

觸發事件必須設定為歷程事件，並定義其結構和條件。 歷程會持續聆聽事件，並在事件到達時一次輸入一個設定檔。 後續歷程節點可評估設定檔的回應，以決定要遵循哪個分支。

**主要考量事項：**

- 需要即時事件串流才能生效
- 必須精確設定事件結構和條件，以避免誤觸發
- 重新進入規則是關鍵的 — 決定如果事件再次引發，設定檔是否可以重新進入
- 每個沙箱每秒最多可支援5,000個事件

**優點：**

- 以客戶行為為基礎的即時輸入 — 高度情境化
- 每個設定檔在事件發生時單獨進入，而不是按排程
- 適用於行為回應序列（放棄購買、購買後）的自然調整
- 可與設定檔資料結合，以便在輸入後進行個人化分支

**限制：**

- 需要串流事件基礎結構就位
- 事件結構描述設定和測試的更高複雜性
- 每個事件都會輸入一個設定檔 — 不適用於大量受眾啟用
- 偵錯需要追蹤個別設定檔歷程

**Experience League：**

- [一般事件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [對象資格鑑定事件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)

### 選項C：多通道協調歷程

**最適合：**&#x200B;在每個接觸點使用不同頻道的跨頻道順序 — 先傳送電子郵件再傳送SMS，接著再傳送推播向上呈報，或傳送電子郵件加上應用程式內補充訊息。 可使用對象讀取或事件觸發的專案。

**運作方式：**

此選項擴充選項A或選項B，在同一歷程中結合多個傳訊通道。 歷程中的每個動作節點都可以鎖定不同的管道（電子郵件、簡訊、推播、應用程式內或網頁），每個都需要個別的管道表面。 歷程設計者在每個步驟選取適當的管道，以啟用向上呈報模式（例如，電子郵件優先，如果沒有參與，則使用SMS）或補充模式（例如，具有應用程式內加強功能的電子郵件）。

跨管道歷程使用的每個管道都需要管道表面，且必須考慮管道特定的個人化、字元限制和選擇加入要求。 條件節點可檢查與先前訊息（例如「已開啟的電子郵件？」）的互動 作為分支條件)來決定下一個管道。

**主要考量事項：**

- 歷程中使用的每個管道都需要作用中的管道表面
- 每個管道都有不同的個人化功能和內容限制
- 必須為每個頻道驗證同意 — 設定檔可以選擇加入以接收電子郵件，但不選擇簡訊
- 應設定通道特定的頻率上限，以防止跨通道過度傳送訊息

**優點：**

- 透過在設定檔的偏好頻道中吸引設定檔，最大化觸及率
- 針對無回應的設定檔啟用向上呈報策略
- 支援跨管道的補充傳訊功能，以便強化
- 儘可能提供最複雜的客戶體驗

**限制：**

- 最高的實作複雜性 — 需要針對每個管道進行設定
- 必須在每個接觸點為每個管道製作內容
- 跨管道的同意和頻率管理越來越複雜
- 測試需要跨所有管道表面進行驗證

**Experience League：**

- [設定簡訊頻道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [設定推播通知頻道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### 選項比較

下表比較各個關鍵條件的三個實作選項。

| 條件 | 選項A：對象已讀取 | 選項B：事件觸發 | 選項C：多管道 |
| --- | --- | --- | --- |
| 最適合 | 排程的生命週期方案，Nurture系列 | 行為回應序列，購物車放棄 | 跨管道向上呈報，補充訊息 |
| 登入時間 | 已排程（批次） | 即時（事件導向） | 已排程或即時 |
| 複雜性 | 中 | Medium — 高 | 高 |
| 輸入量 | 每秒最多20,000個設定檔 | 每秒最多5,000個事件 | 與基礎輸入方法相同 |
| 頻道範圍 | 單一或多個管道 | 單一或多個管道 | 需要多個管道 |
| 需要 | 已定義的對象、評估排程 | 串流事件基礎結構 | 每個頻道的頻道介面 |
| 即時回應 | 否 — 批次專案 | 是 — 事件時立即 | 取決於輸入方法 |

### 選擇正確的選項

使用以下決定流程來選取正確的實作方法：

1. **歷程是否由客戶行為或事件起始？** 如果是，請選擇&#x200B;**選項B** （事件觸發）。 如果歷程是由排程的已讀取對象啟動，請選擇&#x200B;**選項A** （已讀取對象）。

2. **歷程是否使用多個傳訊通道（例如，電子郵件和簡訊）？** 如果是，請在您的輸入方法選擇（A或B）上套用&#x200B;**選項C** （多通道）。 如果歷程在整個過程中使用單一管道，僅選項A或B便已足夠。

3. **您是否需要根據參與升級至其他管道？** 如果是，請選擇&#x200B;**選項C**，其條件節點會檢查與先前訊息的互動，並分支至替代通道。

4. **對象是否預先知道並按排程處理？** 如果是，請選擇&#x200B;**選項A**。如果設定檔應在執行動作時進入歷程，請選擇&#x200B;**選項B**。

## 實作階段

以下階段會逐步進行多步驟協調歷程的端對端實作。

### 階段1：設定管道並準備對象

**應用程式函式：** AJO：頻道設定，RT-CDP：對象評估

在設計歷程之前，所有管道表面都必須是作用中，並且必須定義和評估進入對象（適用於選項A）。 此階段可確保基礎結構準備好進行訊息傳送。

#### 決定每個接觸點的管道型別

歷程將在每個接觸點使用哪些傳訊頻道？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 僅限電子郵件 | 歷程僅透過電子郵件通訊（入門、培養） | 最簡單的設定；需要電子郵件子網域和IP集區；受收件匣位置限制 |
| 僅限SMS | 有時效性的警示、約會提醒 | 需要SMS提供者憑證(Sinch、Twilio、Infobip)；每則訊息的成本較高；更嚴格的選擇退出規則 |
| 僅推送 | 行動使用者的應用程式內參與順序 | 需要APN/FCM認證；使用者必須安裝應用程式 |
| 多管道 | 跨管道的向上呈報或補充訊息 | 需要每個頻道的頻道介面；最複雜但最高觸及率 |

#### 決定對象評估方法（選項A）

設定檔必須多久才符合登入受眾的條件？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 批次評估 | 依排程讀取對象（每日、每週）；不需要即時輸入 | 設定簡單；在歷程讀取前評估對象；支援複雜的區段規則 |
| 串流評估 | 隨著屬性變更，設定檔應近乎即時符合資格 | 區段規則運算式必須符合串流資格；接近即時資格 |

#### 決定子網域委派方法（電子郵件頻道）

應如何將傳送子網域的電子郵件委派給Adobe？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 完全委派 | Adobe管理DNS記錄；最簡單的設定 | 設定最快；Adobe處理SPF、DKIM、DMARC |
| CNAME委派 | 組織保留DNS控制 | 需要DNS系統管理員的參與；必須設定CNAME記錄 |

#### UI導覽

- 色版表面：管理>色版>色版表面>建立表面
- 子網域：管理>管道>子網域
- SMS設定：管理>管道> SMS設定
- 推播設定：管理>管道>推播通知設定
- 受眾：客戶>受眾>建立受眾>建立規則

#### 關鍵設定詳細資料

- 確認電子郵件的IP集區暖機狀態 — 新的IP集區需要在2-4週內逐步進行暖機計畫
- 針對簡訊，設定提供者憑證並驗證寄件者號碼註冊
- 對於推送，上傳APNs憑證和FCM伺服器金鑰
- 使用區段產生器搭配涵蓋目標群體的區段規則來定義進入對象
- 在對象定義中包含隱藏規則（排除最近轉換的、全域取消訂閱的）

#### 選項差異之處

選項A的&#x200B;**（已讀取對象）：**
定義並評估進入對象。 確認對象具有非零母體。 決定歷程將使用一次性對象讀取還是循環讀取排程。

選項B的&#x200B;**（事件觸發）：**
確認已設定觸發事件結構，且事件已串流至平台。 不需要預先定義的對象 — 設定檔會在事件接收時個別輸入。

選項C （多通道）的&#x200B;**：**
為歷程中使用的每個頻道（電子郵件、簡訊、推播、應用程式內）設定頻道介面。 驗證目標母體的每個管道的同意狀態。

#### Experience League檔案

- [設定頻道介面](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [開始使用電子郵件設定](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [設定簡訊頻道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [設定推播通知頻道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [IP熱身計畫](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [區段產生器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)


### 階段2：建立訊息內容

**應用程式函式：** AJO：訊息製作

編寫歷程中每個接觸點的訊息內容。 每則訊息可能有不同的內容、個人化深度和頻道。 此階段會建立歷程動作節點將參考的所有交付專案內容。

#### 決定內容方法

每則訊息應該從範本開始、從頭開始設計或匯入HTML？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 現有內容範本 | 具有已建立版面的品牌一致訊息 | 最快；確保品牌法規遵循；範本必須存在且符合管道型別 |
| 從頭開始設計 | 每個接觸點的獨特自訂配置 | 最具彈性；建置時間更長；使用電子郵件Designer拖放 |
| 匯入HTML | 從外部設計工具預先建立的HTML | 需要乾淨的HTML；可能需要調整回應能力 |

#### 決定個人化深度

每則訊息應包含多少個人化？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 基本權杖插入 | 名字、城市、簡單設定檔屬性 | 低複雜性；搭配XDM路徑使用Handlebars語法 |
| 條件式內容區塊 | 根據區段或屬性顯示的不同內容 | Medium複雜性；需要動態內容規則 |
| 歷程情境式個人化 | 內容會因歷程路徑、先前的互動而有所不同 | 複雜度較高；運用歷程內容變數和事件資料 |

#### 決定片段策略

共用的內容區塊（頁首、頁尾、合法文字）是否應建立為可重複使用的片段？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 可重複使用的片段 | 多則訊息共用相同元素；需要品牌一致性 | 變更會傳播至使用該片段的所有訊息；每則訊息最多30個片段 |
| 內嵌內容 | 具有唯一版面的一次性訊息 | 單次使用內容的速度更快；無跨訊息一致性優勢 |

#### UI導覽

- 內容管理>內容範本>瀏覽
- 傳送Designer電子郵件（在行銷活動或歷程動作中）
- 內容管理>片段>建立片段

#### 關鍵設定詳細資料

- 編寫歷程中每個訊息動作的內容–4步驟歷程可能需要4個個別的訊息設計
- 使用參照XDM設定檔路徑的個人化運算式（例如，`{{profile.person.name.firstName}}`）
- 為區段特定變數設定動態內容區塊
- 使用測試設定檔預覽每則訊息，以驗證個人化呈現
- 傳送校樣給內部利害關係人進行內容審查
- 對於SMS，請遵循字元限制（標準GSM編碼為160個字元）
- 針對推播，設定標題、內文、影像和深層連結/URL動作

#### Experience League檔案

- [設計電子郵件內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [建立電子郵件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [新增個人化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization語法](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [動態內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [使用內容範本](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [使用內容片段](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [建立簡訊訊息](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/create-sms)
- [設計推播通知](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/design-push)
- [預覽和測試您的內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)


### 階段3：設計和啟用歷程

**應用程式函式：** AJO： Journey Orchestration

設計多步驟歷程畫布，包括進入節點、動作節點（訊息）、條件節點（分支）、等待節點（時間延遲）和退出條件。 然後使用測試設定檔進行測試並發佈。

#### 決定專案型別

設定檔應如何進入歷程？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 讀取對象 | 已排程的Nurture序列；已知對象以批次處理 | 在讀取時評估的對象；支援一次性或循環讀取；每秒最多20,000個設定檔 |
| 單一事件 | 即時行為觸發器（購買、購物車放棄） | 即時進入；需要事件串流；每秒最多5,000個事件 |
| 對象資格 | 設定檔近乎即時進入或退出對象時的登入 | 串流評估；由區段會籍變更觸發 |
| 業務事件 | 組織範圍內的事件會觸發對象的歷程 | 對產品啟動、天氣事件、系統警報相當實用 |

#### 決定重新進入原則

設定檔完成或退出後可以重新進入歷程嗎？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 允許重新進入（使用冷卻） | 設定檔可能需要重複歷程（循環購買、季節性重新參與） | 冷卻時間下限為5分鐘；避免在冷卻視窗中重複輸入專案 |
| 禁止重新進入 | 一次性歷程（上線、單一生命週期事件） | 設定檔完成或退出歷程，且無法再次進入 |

#### 決定接觸點之間的等待持續時間

歷程應該在每則訊息之間等候多久？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 固定期間（例如3天） | 一致的步調，無論設定檔行為為何 | 簡單；可預測的時間；對象閱讀歷程至少1小時 |
| 特定日期/時間 | 訊息必須在一個精確的時間送達（例如，續約日期） | 使用設定檔屬性或運算式來判斷確切的日期/時間 |
| 自訂運算式 | 根據設定檔資料或歷程內容進行動態等待 | 最具彈性；需要運算式製作 |

#### 決定分支條件

哪些條件決定了設定檔採用的路徑？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 設定檔屬性檢查 | 根據忠誠度等級、產品興趣、地理位置建立分支 | 使用評估時可用的設定檔資料 |
| 區塊會籍檢查 | 根據設定檔是否屬於特定對象進行分支 | 需要定義對象並進行評估 |
| 事件資料檢查 | 根據設定檔是否執行了動作（已開啟的電子郵件、已點按的連結）而建立分支 | 評估歷程範圍的事件資料；適用於參與型分支 |
| 百分比分割 | 跨路徑隨機分佈設定檔（用於A/B測試或控制的轉出） | 不使用設定檔資料；純隨機配置 |

#### 決定退出條件

什麼事件或條件會導致設定檔提早退出歷程？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 轉換事件 | 設定檔完成所需的動作（購買、註冊、表單提交） | 需要事件串流；最常見的退出條件 |
| 對象會籍退出 | 設定檔會離開登入對象或加入排除對象 | 近乎即時評估串流對象 |
| 逾時 | 已達到歷程持續時間上限（最多91天） | 預設安全網；可在歷程屬性中設定 |
| 無退出條件 | 設定檔會自然完成整個歷程路徑 | 最簡單；除非手動移除，否則所有設定檔都會周遊整個歷程 |

#### 決定歷程逾時

設定檔可以在歷程中保留的最大期間是多少？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 91天（最大值） | 長期歷程（每季續約、延長入門） | 允許的最大值；在逾時仍在歷程中的設定檔會自動退出 |
| 自訂較短的持續時間 | 歷程應在定義的期間內完成（7天、14天、30天） | 根據使用案例的自然生命週期設定 |

#### UI導覽

- 建立歷程：歷程>建立歷程
- 歷程屬性：歷程畫布>屬性面板
- 進入節點：歷程畫布>拖曳「讀取對象」或事件活動
- 動作節點：歷程畫布>拖曳頻道動作（電子郵件、簡訊、推播）
- 條件節點：歷程畫布>拖曳「條件」活動
- 等待節點：歷程畫布>拖曳「等待」活動
- 退出條件：歷程屬性>退出條件>設定
- 測試模式： 「歷程畫布>測試模式」切換
- 發佈：歷程畫布>發佈

#### 關鍵設定詳細資料

- 使用清楚的描述性慣例為歷程命名（例如「Onboarding_Series_Email_v1」）
- 設定歷程時區，以進行一致的等待步驟處理
- 使用適當的頻道介面設定每個動作節點，並連結至編寫的訊息內容
- 每個分支都必須以「結束」活動終止
- 設定適合使用案例的重新進入規則
- 使用測試模式搭配測試設定檔，在發佈前模擬完整的歷程路徑
- 驗證測試設定檔是否穿越預期路徑並接收正確的訊息

#### 選項差異之處

選項A的&#x200B;**（已讀取對象）：**

- 拖曳「讀取對象」活動作為登入節點
- 選取階段1中定義的目標對象
- 選擇性地設定週期性讀取排程（每日、每週）
- 設定讀取速率限制（如果擔心下游系統負載）

選項B的&#x200B;**（事件觸發）：**

- 將觸發事件拖曳為進入節點
- 設定事件綱要和輸入條件
- 請謹慎設定重新進入規則，以避免重複事件中重複的專案

選項C （多通道）的&#x200B;**：**

- 使用選項A或B的輸入方法
- 在每個動作節點上，選取該接觸點的適當管道表面
- 在管道之間新增條件節點以檢查參與（例如「設定檔是否開啟電子郵件？」） 並路由至替代通道

#### Experience League檔案

- [建立歷程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [歷程屬性](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [讀取對象活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [一般事件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [對象資格鑑定事件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)
- [在歷程中新增訊息](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [條件活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [等待活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [退出條件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [結束活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/end-activity)
- [歷程專案管理](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [測試您的歷程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [發佈歷程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)


### 階段4：設定治理和最佳化

**應用程式功能：** AJO：頻率與商業規則， AJO：衝突與優先順序管理， AJO：內容實驗， RT-CDP：同意與治理執行

套用頻率上限以防止過度傳訊、指派與其他作用中通訊衝突解決的優先順序分數、選擇性地在歷程訊息中設定A/B測試，以及驗證同意實施。

#### 決定頻率上限設定

歷程訊息是否應遵循全球頻率上限？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 套用頻率規則 | 歷程與其他行銷活動和歷程同時運作；設定檔不應過度傳訊 | 如果設定檔已經從其他通訊達到上限，則可能會隱藏訊息 |
| 免除上限 | 歷程訊息至關重要，必須一律傳送（異動、法規） | 謹慎使用；如果過度使用，可能會造成訊息疲勞 |

#### 決定優先順序分數指派

此歷程相對於其他作用中行銷活動和歷程應該如何？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 高優先順序(70-100) | 歷程訊息是關鍵的生命週期通訊（上線、續約） | 與其他通訊發生衝突時，優先順序較高的優先 |
| Medium優先順序(30-69) | 歷程訊息很重要，但並非緊急（培養、教育） | 可能被較高優先順序的通訊抑制 |
| 低優先順序(0-29) | 歷程訊息為補充或促銷 | 與較高優先順序的訊息競爭時，將被抑制 |

#### 決定內容實驗

歷程訊息是否應該包含A/B或多變數測試？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 是 — A/B測試 | 將主題行、CTA或內容版面配置最佳化於特定接觸點 | 每個變體需要足夠的容量以顯示統計顯著性；支援2-10個處理方式 |
| 無實驗 | 內容已完成或數量太低，無法進行有意義的測試 | 設定更簡單；不需要變體追蹤 |

#### UI導覽

- 頻率規則：管理>商業規則>建立規則
- 優先順序分數：歷程屬性>優先順序分數
- 衝突偵測：管理>商業規則>衝突與優先順序
- 內容實驗：歷程畫布>選取訊息動作>內容實驗切換
- 同意政策：隱私權>政策>同意政策

#### 關鍵設定詳細資料

- 設定特定頻道的頻率上限（例如，每週最多3封電子郵件、每天最多1個簡訊、每天最多2個推播）
- 將優先順序分數指派給歷程(0-100)，以反映其相對於其他作用中通訊的業務重要性
- 檢閱衝突偵測面板，以識別任何重疊的行銷活動或歷程
- 如果執行內容實驗，請定義處理變體、設定流量分配、選擇成功量度（開啟、點按或轉換），並設定信賴臨界值（通常為95%）
- 確認歷程中使用的每個管道的同意執行都有效

#### Experience League檔案

- [頻率規則](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [商業規則概觀](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [優先順序分數](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [識別潛在衝突](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)
- [歷程上限和仲裁](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)
- [開始使用內容實驗](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [建立內容實驗](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Journey Optimizer中的同意](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)


### 階段5：設定報告和監視

**應用程式功能：** AJO：報告及效能分析、監視及可觀察性、報告及分析

在啟動期間和之後監視歷程執行、檢閱每步驟傳送和參與量度、設定歷程處理失敗警示，以及選擇性地建置CJA工作區分析以實現深度funnel和流失視覺效果。

#### 決定報告方法

此歷程需要哪些報告工具？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 僅限AJO原生報表 | 基本傳遞和參與監控就足夠了 | 即時報告（在執行期間）和所有時間報告（執行後）；即時報表每60秒重新整理一次 |
| AJO + CJA分析 | 深層funnel分析、步驟轉換率、流失視覺化或跨歷程比較都是必要專案 | 需要CJA連線和連結至AJO資料集的資料檢視；最全面 |
| 僅限CJA | 組織使用CJA作為主要分析平台 | 需要CJA設定；AJO原生報表仍可作為備份 |

#### 決定警示組態

哪些歷程失敗應該觸發警報？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 歷程處理警報 | 一律建議用於生產歷程 | 設定檔專案失敗、動作節點錯誤和歷程停頓的警報 |
| 傳遞失敗警報 | 對於具有高價值通訊的歷程至關重要 | 超過臨界值的退回率、傳送失敗時發出警報 |

#### UI導覽

- 歷程即時報告：歷程>選取歷程>即時報告
- 歷程所有時間報表：歷程>選取歷程>所有時間報表
- 警報：警報>警報規則>訂閱
- CJA工作區：專案>建立新專案

#### 關鍵設定詳細資料

- 在歷程執行期間存取即時報告，以即時監控設定檔登入、退出和每個步驟的傳送量度
- 歷程完成後（或資料累積充足後），請檢閱「所有時間」報表以取得全面分析
- 針對歷程處理失敗和傳送問題設定平台警報
- 針對CJA分析，請確定CJA連線包含AJO體驗事件資料集（訊息回饋、電子郵件追蹤、歷程步驟事件）
- 使用以下專案建置CJA Workspace：
   - funnel視覺效果顯示每個歷程步驟的設定檔計數
   - 識別流失點的流失視覺效果
   - 步驟轉換率計算
   - 轉換時間分析
   - 管道層級參與劃分（適用於多管道歷程）

#### Experience League檔案

- [歷程即時報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [歷程全域報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [使用Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [警報概觀](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [Analysis Workspace概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [AJO + CJA整合指南](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

## 實施考量

在實施之前和期間，請檢閱下列護欄、陷阱、最佳實務和權衡。

### 護欄和限制

- 每個沙箱最多&#x200B;**500個即時歷程** — [Journey Optimizer護欄](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- **歷程持續時間的上限為91天** （全域逾時） — 在逾時時仍在歷程中的設定檔會自動退出
- 每個歷程畫布最多&#x200B;**50個活動**
- 每秒最多&#x200B;**20,000個設定檔的讀取對象歷程程式** （預設限制）
- 單一事件歷程支援每個沙箱每秒最多&#x200B;**5,000個事件**
- 對於對象已讀取的歷程，等待步驟具有&#x200B;**最短1小時的持續時間**
- 歷程&#x200B;**重新進入冷卻最少5分鐘**
- 每個沙箱每個管道型別&#x200B;**最多** 10個管道表面
- 建議將電子郵件大小上限設為&#x200B;**100 KB**，以獲得最佳傳遞能力
- 每則訊息最多&#x200B;**30個內容片段**
- 每個實驗最多&#x200B;**10個內容實驗處理** （變體）
- 每個沙箱最多&#x200B;**10個上限設定**
- 每個沙箱最多&#x200B;**4,000個區段定義**

### 常見陷阱

- **發佈而不測試：**&#x200B;發佈之前請一律使用測試模式搭配測試設定檔，以驗證完整的歷程路徑。 驗證設定檔是否周遊預期的分支、等待步驟是否正確推進，以及訊息是否正確呈現。
- **分支上缺少結束活動：**&#x200B;每個歷程分支都必須以End活動終止。 如果任何分支沒有終止節點，歷程將無法發佈。
- **過於寬泛的進入條件：**&#x200B;定義鬆散的進入對象或事件條件可能會使歷程充斥著非預期的設定檔。 使用特定的屬性檢查和隱藏規則來調整輸入條件。
- **忽略重新進入規則：**&#x200B;對於事件觸發的歷程，設定檔可能會多次觸發觸發事件。 如果沒有適當的重新進入設定（拒絕重新進入或縮短期間），設定檔可能會累積在歷程中，導致重複訊息。
- **等待步驟時區混淆：**&#x200B;會以UTC處理等待持續時間。 在歷程屬性中明確設定歷程時區，以確保等待步驟在預期的當地時間推進。
- **無法直接編輯即時歷程：**&#x200B;即時歷程。 若要進行變更、複製歷程、修改副本、停止原始版本並發佈新版本。 在上線之前規劃歷程版本設定。
- **未定義退出條件：**&#x200B;若沒有退出條件，轉換歷程中間之設定檔將繼續接收後續訊息 — 可能無關或自相矛盾。 一律設定轉換事件的退出條件。
- **管道同意未對齊：**&#x200B;個人資料可能會選擇加入電子郵件，但不會選擇簡訊。 多頻道歷程必須尊重每個頻道的同意。 確認同意欄位已填入並在每個管道表面強制執行。

### 最佳實務

- **開始簡單、重複：**&#x200B;在新增複雜分支之前，先以線性2-3步驟歷程開始。 在條件和管道中分層之前，驗證核心流程是否有效。
- **使用描述性命名慣例：**&#x200B;清楚地命名歷程節點、條件和等待步驟（例如「Wait_3_Days_After_Welcome」而非「Wait 1」）。 這可讓測試模式的偵錯和報表解譯更容易。
- **及早設定退出條件：**&#x200B;在設計歷程路徑之前，將轉換事件定義為退出條件。 這能確保轉換的設定檔會從歷程中移除，無論其是在哪個步驟中。
- **設定有意義的等候期間：**&#x200B;以客戶行為資料為基礎的等候期間 — 一般互動之間的時間、預期的回應視窗和適合頻道的步調（例如，電子郵件之間2-3天，簡訊之間1週）。
- **使用條件節點來檢查參與：**&#x200B;在訊息動作之後，新增條件來檢查設定檔是否參與（已開啟、已點按）。 將參與的設定檔路由到單一路徑，將未參與的設定檔路由到提升或替代頻道路徑。
- **利用計算屬性進行分支：**&#x200B;使用計算屬性（例如參與分數、購買頻率或上次活動後間隔天數）來進行以資料為導向的分支決定，而非任意。
- **反複監視和最佳化：**&#x200B;在初始執行期間每週檢閱歷程報告。 根據每一步的效能資料，識別流失點、調整等待期間、調整條件，以及最佳化訊息內容。
- **將您的歷程版本化：**&#x200B;進行變更時，請複製歷程以建立新版本。 維護版本變更記錄，以進行稽核和最佳化追蹤。

### 權衡決定

您應根據特定業務需求評估以下權衡。

#### 對象讀取專案與事件觸發專案的比較

受眾讀取專案提供可預測、批次式處理，更易於管理和測試。 事件觸發式輸入可提供即時回應，與情境的關聯性更強，但需要串流基礎結構和更細緻的重新輸入管理。

- **受眾讀取偏好：**&#x200B;可預測性、大量處理、排程的生命週期程式、較簡單的測試
- **事件觸發的偏好：**&#x200B;即時關聯性、行為內容、個別設定檔步調、立即回應客戶動作
- **建議：**&#x200B;針對時間受業務驅動的計畫生命週期方案（入門、續約），使用對象讀取。 若時間為客戶導向，針對行為回應順序（放棄購買、購買後）使用事件觸發。

#### 單一管道和多管道歷程

單通道歷程的實作、測試和管理都更為簡單。 多管道歷程提供更廣泛的觸及範圍和問題上報功能，但會增加內容建立、同意管理和頻率控管的複雜性。

- **單一管道的好處：**&#x200B;更快速的實作、更簡單的同意管理、更少的內容製作工作、更輕鬆的偵錯
- **多管道優惠：**&#x200B;較高的參與潛能、無回應設定檔的管道提升、更全面的客戶體驗
- **建議：**&#x200B;從單一管道歷程開始，並在展開至多管道之前驗證流程和業務影響。 以增量方式新增參與資料顯示主要管道未有效觸及對象的管道。

#### 歷程複雜性與可管理性

包含許多條件和路徑的高度分支歷程可以處理更多情境，但越來越難以測試、偵錯和最佳化。 使用較少分支的簡單歷程更容易管理，但可能會提供較不個人化的體驗。

- **複雜歷程優先：**&#x200B;精細個人化、區段特定路徑、完整情境涵蓋範圍
- **較簡單的歷程優先：**&#x200B;部署更快、測試更輕鬆、報告更清晰、維護負擔更輕
- **建議：**&#x200B;將歷程限製為3-5個主要分支和15-25個活動。 如果邏輯需要更多複雜性，請考慮使用跨歷程協調（而不是單一整體歷程）拆分為多個歷程。

#### 頻率上限嚴格性與歷程完成的比較

嚴格的頻率上限會防止過度傳訊，但可能會抑制歷程訊息，導致設定檔略過步驟並降低歷程完成率。 寬鬆的帽子可確保傳送歷程訊息，但存在頻道疲勞的風險。

- **嚴格上限優先：**&#x200B;客戶體驗保護、降低取消訂閱率、品牌信任
- **寬大字幕優先：**&#x200B;歷程完成率、完整訊息順序傳遞、行銷方案有效性
- **建議：**&#x200B;為關鍵歷程訊息（入門、續約）指派較高的優先順序分數，以便在達到上限時，優先於促銷活動。 只保留真正重要通訊的「劐免上限」。

## 相關文件

下列資源提供此實作中所使用功能的其他詳細資料。

### 歷程

- [開始使用歷程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [建立歷程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [歷程屬性](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [發佈歷程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)
- [測試您的歷程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)

### 歷程活動

- [讀取對象活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [一般事件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [對象資格鑑定事件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)
- [條件活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [等待活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [在歷程中新增訊息](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [結束活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/end-activity)
- [設定自訂動作](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/using-custom-actions)

### 登入與退出管理

- [歷程專案管理](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [退出條件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)

### 管道設定

- [開始使用電子郵件設定](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [設定頻道介面](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [委派子網域](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [建立 IP 池](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [IP熱身計畫](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [設定簡訊頻道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [設定推播通知頻道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### 訊息製作與個人化

- [建立電子郵件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [設計電子郵件內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [使用電子郵件Designer內容元件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/content-components)
- [新增個人化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization語法](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [輔助函式](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [動態內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [使用內容範本](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [使用內容片段](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [預覽和測試您的內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### 內容實驗

- [開始使用內容實驗](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [建立內容實驗](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [內容實驗報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [統計計算](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-calculations)

### 頻率、衝突和優先順序

- [頻率規則](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [商業規則概觀](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [開始使用衝突與優先順序管理](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [優先順序分數](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [歷程上限和仲裁](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)
- [識別潛在衝突](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)

### 對象和細分

- [Segmentation Service概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [區段產生器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Profile Query Language參考](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)
- [串流區段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/api/streaming-segmentation)
- [邊緣分段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/api/edge-segmentation)

### 報告與分析

- [歷程即時報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [歷程全域報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [使用Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [AJO + CJA整合指南](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [Analysis Workspace概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [CJA概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)

### 同意與治理

- [Journey Optimizer中的同意](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)
- [資料控管概覽](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [管理隱藏清單](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### 資料基礎

- [XDM系統概覽](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Identity Service總覽](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [設定檔概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [計算屬性概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
