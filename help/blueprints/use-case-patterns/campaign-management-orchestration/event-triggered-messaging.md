---
title: 事件觸發式傳訊
description: 瞭解如何傳遞情境式即時訊息來回應行為或系統事件。
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 75137990-9848-40c0-abf3-adbd21d2de52
source-git-commit: e8185f348f926acab2ca2e0c3cd55c08c663cf41
workflow-type: tm+mt
source-wordcount: '9040'
ht-degree: 1%

---

# 事件觸發式傳訊

本指南針對使用[!DNL Adobe Journey Optimizer] (AJO)、[!DNL Real-Time Customer Data Platform] (RT-CDP)和[!DNL Adobe Experience Platform] (AEP)的事件觸發傳訊提供完整的實作藍圖。 它專為需要傳送情境式即時訊息以回應行為或系統事件的解決方案架構師、行銷技術人員和實施工程師所設計。

使用本指南來瞭解應設定哪些專案、在哪裡有實施選擇，以及促成每個決策的利弊取捨。

該指南涵蓋從事件擷取到建立歷程，再到訊息傳送和效能報告的完整生命週期，並針對三個不同的實施選項提供詳細決策指引。

## 使用案例概述

事件觸發的傳訊功能會傳送內容式訊息來回應即時行為或系統事件。 批次傳出訊息啟動會依排程傳送給預先評估的對象，不同於批次傳出訊息啟動，此模式會監聽合格事件（例如購物車放棄、瀏覽工作階段、表單提交或系統狀態變更），並立即將觸發設定檔輸入歷程，以評估條件並傳送訊息。

此模式仰賴串流至AEP的即時事件（透過網頁SDK、Mobile SDK或伺服器端API）、在AJO中具有單一事件專案的歷程，以及決定是否要傳送及傳送何種內容的條件評估邏輯。 訊息通常會在觸發事件後的數分鐘內傳送，因此這種模式非常適合時間敏感型與情境相關的通訊。

與排程的批次通訊相比，組織可利用此模式即時回應客戶動作、提高關聯性，並提高參與度和轉換率。 常見的情況包括放棄的購物車復原、購買後的後續追蹤、註冊後的歡迎訊息，以及付款失敗或價格下降警示等時效性很強的通知。

## 主要業務目標

此使用案例模式支援下列業務目標。

**[復原放棄的購物車與歷程](../../business-objectives/customer-experience/recover-abandoned-carts-journeys.md)**

透過及時且個人化的後續追蹤，重新吸引在購買、應用程式或註冊流程中休假的使用者。

| KPI |
| --- |
| 轉換率、遞增收入、參與 |

**[提高轉換率](../../business-objectives/revenue-monetization/increase-conversion-rates.md)**

提高完成所需動作（例如購買、註冊或提交表單）的訪客和潛在客戶的百分比。

| KPI |
| --- |
| 轉換率、銷售機會轉換、每個銷售機會的成本 |

**[提供個人化的客戶體驗](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**

根據個別偏好設定、行為和生命週期階段量身打造內容、選件和訊息。

| KPI |
| --- |
| 參與度、轉換率、客戶滿意度(CSAT) |

**[改善客戶上線](../../business-objectives/customer-experience/improve-customer-onboarding.md)**

透過簡化的個人化歡迎體驗和啟動歷程，加快新客戶的價值實現時間。

| KPI |
| --- |
| 參與度、保留率、轉換率 |

## 戰術使用案例範例

下列案例說明如何將事件觸發式訊息套用至不同的業務內容。

- **購物車放棄電子郵件或簡訊** — 當客戶新增商品到購物車但未在定義的時間範圍內完成購買時，傳送提醒訊息
- **瀏覽放棄後續追蹤** — 重新與檢視過產品或內容但未採取轉換動作的訪客互動
- **購買後感謝您或交叉銷售** — 在購買事件後立即提供確認和交叉銷售建議
- **試用到期提醒** — 通知即將結束免費試用且提供續約或轉換訊息的使用者
- **註冊後的歡迎訊息** — 當新使用者註冊或建立帳戶時，立即傳送上線訊息
- **表單提交確認** — 以內容式確認來確認表單提交（連絡人要求、申請、註冊）
- **付款失敗通知** — 當定期付款失敗時提醒客戶，提示他們更新付款資訊
- **應用程式解除安裝回呼推播通知** — 當使用者解除安裝行動應用程式時觸發回呼訊息
- **預約或約會確認** — 在排程預訂、預約或約會後，立即傳送確認
- **願望清單專案的價格下降警報** — 當願望清單上的產品降價時通知客戶

## 關鍵績效指標

下列KPI可協助評估事件觸發訊息實作的效能。

| KPI | 說明 | 測量方法 |
| --- | --- | --- |
| 轉換率 | 完成所需動作（購買、註冊、續約）的觸發訊息收件者百分比 | 轉換/傳遞的訊息* 100 |
| 遞增收入 | 與不傳送控制組相比，由事件觸發的訊息所產生的額外收入 | 來自觸發傳送的收入 — 控制組基準 |
| 開啟率 | 收件者開啟的傳遞訊息百分比 | 開啟/傳送* 100 |
| 點進率(CTR) | 至少產生一次點按的傳遞訊息百分比 | 點按數/送達* 100 |
| 轉換時間 | 訊息傳遞和轉換事件之間的平均經過時間 | Avg（轉換時間戳記 — 傳遞時間戳記） |
| 歷程完成率 | 進入歷程並到達訊息傳送步驟的設定檔百分比（不會因條件或退出而捨棄） | 到達傳送的設定檔/進入歷程的設定檔* 100 |
| 訊息隱藏率 | 由於頻率上限、同意或條件評估而抑制的合格設定檔百分比 | 隱藏的設定檔/符合資格的設定檔總數* 100 |
| 跳出率 | 因硬退信或軟退信而無法傳遞的訊息百分比 | 彈回數/已傳送* 100 |

## 使用案例模式

本節說明驅動事件觸發式傳訊的核心模式及功能鏈。

**事件觸發訊息**

接聽即時行為或系統事件，然後將內容相關訊息傳遞至觸發的設定檔。

**函式鏈：**&#x200B;事件擷取>歷程專案>條件評估>訊息傳送>報告

## 應用程式

在此使用案例模式中使用以下Adobe應用程式。

- **[!DNL Adobe Journey Optimizer] (AJO)** — 具有單一事件專案、條件評估、等待步驟、訊息編寫、頻道設定、頻率控管和傳遞報告的歷程協調
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** — 歷程中條件式篩選的對象評估、同意和治理實施、設定檔擴充
- **[!DNL Adobe Experience Platform] (AEP)** — 透過Web SDK、Mobile SDK或伺服器端API的即時事件擷取；資料模式；身分解析；Edge Network

## 基礎函式

下列基本功能必須為此使用案例模式準備就緒。 對於每個函式，狀態會指出它通常是必要的、假設為預先設定或不適用。

| 基礎函式 | 狀態 | 必須準備就緒的專案 | Experience League參考 |
| --- | --- | --- | --- |
| 管理與治理 | 已假設就位 | 已布建使用中管道設定的AJO沙箱。 指派給實作團隊的歷程建立和發佈許可權。 為歷程管理、內容製作和管道管理設定的使用者角色。 | [沙箱總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sandbox/home)，[存取控制總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/access-control/home) |
| 資料模型與準備 | 必填 | XDM ExperienceEvent結構描述必須擷取觸發事件，其中包含條件評估與訊息個人化所需的所有內容欄位（例如，購物車事件、產品詳細資料、購物車值所需的`commerce.productListAdds`）。 結構描述必須針對即時客戶個人檔案啟用。 必須建立對應的資料集並啟用設定檔。 | [XDM系統總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/xdm/home)，[結構描述組合基本概念](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/xdm/schema/composition) |
| 資料來源與收集 | 必填 | 必須設定即時事件串流 — 適用於Web事件的Web SDK、適用於應用程式事件的Mobile SDK或適用於系統事件的Edge Network伺服器API。 資料流必須設定為啟用AEP和AJO服務，將事件路由至正確的資料集。 這是重要的相依性，因為模式取決於即時事件擷取。 | [網頁SDK概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/web-sdk/home)，[設定資料串流](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/datastreams/configure) |
| 身分和設定檔設定 | 必填 | 觸發事件必須與已知身分識別（電子郵件、CRM ID或驗證的工作階段）相關聯，以便歷程可以解析設定檔並傳遞訊息。 觸發事件使用的識別碼必須有身分名稱空間。 匿名事件需要在傳遞訊息之前透過身分圖表進行身分拼接。 必須設定合併原則。 | [身分識別服務總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/identity/home)，[合併原則總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/merge-policies/overview) |
| 對象定義與細分 | 推薦 | 雖然事件觸發的歷程並非絕對必要（專案是事件型，而非受眾型），但受眾區段可用於歷程中的條件評估（例如，僅當設定檔位於「高價值客戶」區段時傳送，或當設定檔位於「最近聯絡」區段時隱藏）。 針對歷程中的即時區段會籍檢查，建議使用串流評估。 | [分段服務總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/home)，[串流分段](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/methods/streaming-segmentation) |

## 支援功能

以下功能可擴大此使用案例模式，但不是核心執行的必要功能。

| 支援功能 | 狀態 | 為什麼重要 | Experience League參考 |
| --- | --- | --- | --- |
| 計算/衍生屬性建立 | 推薦 | 計算屬性（例如購物車放棄計數、上次購買間隔天數、平均訂單值和期限購買總計）可改善觸發歷程中的條件評估和個人化。 這些行為彙總可讓目標定位決策更精確（例如，區分首次放棄者和重複放棄者）。 | [計算屬性總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/computed-attributes/overview) |
| 資料生命週期管理 | 推薦 | 應該針對暫時性行為事件（頁面檢視、搜尋、點按）設定事件資料過期時間，以管理儲存成本和法規遵循。 在訊息傳送期間，通道特定的選擇加入/選擇退出執行必須有同意結構描述欄位。 | [進階資料生命週期管理概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-lifecycle/home)，[資料集有效期](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-lifecycle/ui/dataset-expiration) |
| 資料使用標籤和實作 | 推薦 | 事件和設定檔欄位上的治理標籤可確保符合標準的個人化。 如果觸發的訊息包含使用PII或行為資料的個人化內容，則應審查資料使用標籤和治理政策，以防止訊息內容中出現未經授權的資料使用。 | [資料控管概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/home)，[資料使用標籤概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/labels/overview) |
| 監控與可觀察性 | 已包含 | 歷程執行監視是報告階段的一部分。 此外，針對事件擷取失敗或歷程處理延遲設定警報，以偵測會阻止傳送觸發訊息的管道問題。 | [警示概述](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/observability/alerts/overview)，[可觀察性深入分析概述](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/observability/home) |
| 報告與分析 | 已包含 | 報告階段涵蓋歷程績效報告。 若要更深入地分析跨頻道及一段時間內的觸發式傳訊成效，請設定CJA連線和工作區，以分析轉換歸因、轉換時間和頻道效能。 | [CJA概觀](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-overview/cja-overview)，[AJO + CJA整合指南](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/reporting/channel-report/cja-ajo) |

## 應用程式函式

此計畫會從「應用程式功能目錄」中執行下列功能。 函式會對應至實作階段，而非編號步驟。

### [!DNL Journey Optimizer] (AJO)

| 函式 | 實作階段 | 說明 |
| --- | --- | --- |
| Journey Orchestration | 歷程建立與設定 | 建立包含單一事件登入的歷程、設定符合條件的事件、新增條件節點、等待步驟、訊息動作、退出條件和重新登入規則 |
| 通道設定 | 管道表面設定 | 設定或驗證管道表面（電子郵件、簡訊、推播），包括子網域委派、IP集區、寄件者設定和隱藏清單管理 |
| 訊息製作 | 訊息內容建立 | 使用事件導向的個人化、條件內容區塊和可重複使用的片段，製作內容相關的訊息內容 |
| 頻率與業務規則 | 歷程建立與設定（選項C） | 設定頻率上限和重複資料刪除規則，以防止來自高頻事件來源的過度傳訊 |
| 衝突與優先順序管理 | 歷程建立與設定 | 為競爭相同設定檔的歷程指派優先順序分數並設定衝突偵測 |
| 報告與效能分析 | 報告與監控 | 透過即時和歷史報告監控歷程傳遞量度；透過CJA存取程式化績效資料 |

### [!DNL Real-Time CDP] (RT-CDP)

| 函式 | 實作階段 | 說明 |
| --- | --- | --- |
| 對象評估 | 基礎設定(F5) | 評估用於歷程中條件式篩選的對象區段（例如，高價值客戶區段、隱藏區段） |
| 同意與治理實施 | 基礎設定(S2/S3) | 在訊息傳送期間強制執行同意偏好設定和資料使用治理原則，以確保符合規範的通訊 |

## 先決條件

開始實作前請先完成下列作業。

- [ ]個AJO沙箱已布建歷程建立和發佈許可權(F1)
- [ ] XDM ExperienceEvent結構描述會擷取具有內容欄位的觸發事件，並已為即時客戶個人檔案啟用(F2)
- [ ]即時事件串流已透過Web SDK、Mobile SDK或Edge Network伺服器API設定，並具有資料流路由事件，可傳送到正確的AEP資料集(F3)
- [ 為觸發事件上的識別碼設定的]識別名稱空間；已設定識別連結規則(F4)
- [ ]管道表面（電子郵件、簡訊或推播）已設定並驗證為成功的測試傳送
- [ ]訊息內容使用範例設定檔編寫、稽核和測試
- [ ]個同意欄位已填入目標頻道的設定檔中（例如，`consents.marketing.email.val`）
- [ ]如果使用條件型對象篩選（選項B/C），則定義串流評估對象區段並主動評估

## 實作選項

本節說明三個用於事件觸發訊息的實作選項。 每個選項都以上一個選項為基礎，並新增其他功能。

### 選項A：簡單事件觸發訊息

**最適合：**&#x200B;不需要延遲或條件式邏輯的立即單一訊息回應 — 訂單確認、歡迎電子郵件、表單提交確認、預約確認。

**運作方式：**

歷程透過單一事件登入節點監聽合格事件。 收到事件時，設定檔會進入歷程、通過最低條件評估（同意檢查、設定檔存在驗證），並透過設定的頻道動作節點立即收到單一訊息。

這是最簡單的實作變體。 歷程畫布包含事件專案節點、基本資格檢查的選用條件節點、單一訊息動作節點及結束節點。 沒有等待步驟、沒有複雜的分支，也沒有轉換檢查。 訊息通常會在觸發事件後的數秒到數分鐘內傳送。

來自觸發事件的事件資料（產品名稱、訂單總計、表單詳細資料）可透過個人化編輯器中的內容屬性，用於訊息個人化。 此方法可最大化交付速度並最小化歷程複雜性。

**主要考量事項：**

- 無論客戶在事件後是否自行轉換（無轉換檢查），都會傳送訊息
- 最適合本身需要立即回應的事件（確認、確認）
- 重新進入規則應謹慎設定 — 對於確認式訊息，允許重新進入，以便每個事件產生訊息；對於歡迎式訊息，防止重新進入

**優點：**

- 傳送時間最短（事件後幾秒到幾分鐘）
- 最簡單的歷程設定，只需最少的移動部分
- 歷程失敗或停滯設定檔的風險最低
- 易於測試和維護

**限制：**

- 無法檢查客戶在傳送前是否自行轉換
- 無法併入時間延遲的條件邏輯
- 如果事件頻繁發生而沒有頻率控管，則可能會產生不必要的訊息

**Experience League：**

- [建立歷程](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [一般事件](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)

### 選項B：等待的條件式事件觸發訊息

**最適合：**&#x200B;延遲、條件式回應，客戶應在收到訊息前有時間自行轉換 — 放棄購買（等待1-4小時，然後檢查購物車是否仍被放棄）、瀏覽放棄購買（等待24小時，檢查是否已完成購買）、試用期到期（等到到期日接近）。

**運作方式：**

歷程會監聽合格事件、進入設定檔，並引入評估條件之前的等待時間。 等待後，條件節點會檢查客戶是否已自行轉換（例如，完成購買、續訂訂閱），或原始內容是否仍然有效。 只有在符合條件時（例如，購物車仍遭捨棄），歷程才會繼續傳送訊息。

歷程畫布包含事件進入節點、等待節點（可設定的持續時間或特定日期/時間）、檢查轉換事件或設定檔狀態變更的條件節點、分支路徑（傳送訊息與退出而不傳送）、合格路徑上的訊息動作節點，以及每個分支上的結束節點。 如果轉換事件發生在等待期間，您可以將退出條件設定為自動從歷程中移除設定檔，而不需要明確檢查條件。

此方法可讓客戶有時間自行轉換、改善客戶體驗，並提升所傳送訊息的感知相關性，藉此減少不必要的傳訊。

**主要考量事項：**

- 等待時間會顯著影響轉換率：較短的等待（1-2小時）會產生較高的緊急程度，但較不必要的傳送次數；較長的等待（24-48小時）會減少傳送量，但可能會錯過相關視窗
- 條件評估需要在AEP中擷取轉換事件，並與相同的設定檔身分相關聯
- 退出條件為轉換檢查的明確條件節點提供更乾淨的替代方案
- 重新進入規則必須考慮等待期間 — 設定檔在等待時不應重新進入歷程

**優點：**

- 透過檢查自我轉換來減少不必要的傳訊
- 產生更高品質、更相關的通訊
- 透過可設定的延遲視窗支援時效性使用案例
- 退出條件可在轉換時啟用自動移除歷程

**限制：**

- 使用等待和條件節點增加歷程複雜性
- 設定檔在等待期間會佔用歷程位置（以91天歷程逾時為限）
- 需要在等待視窗內將轉換事件擷取到AEP，才能進行準確的條件評估
- 與選項A相比，更長的傳送時間

**Experience League：**

- [等待活動](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [條件活動](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [退出條件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)

### 選項C：頻率控管觸發的事件

**最適合：**&#x200B;需要注意訊息疲勞的高頻率事件來源 — 頁面檢視、產品檢視、搜尋查詢、重複購物車新增。 可作為覆蓋套用在選項A或選項B上方。

**運作方式：**

此選項將頻率控管新增至選項A或選項B，以防止過度傳訊。 高頻行為事件（例如產品檢視或重複新增購物車）可能會在短時間內多次觸發歷程。 若沒有頻率控管，設定檔可能會收到重複或過多的訊息。

頻率控管透過兩個補充機制實作：AJO商業規則（頻率上限），其會限制設定檔在每個時段每個管道接收到多少訊息，以及歷程層級的重新進入規則，其會定義設定檔可重新進入相同歷程之前的冷卻期間。 商業規則在組織層級運作，並對所有行銷活動和歷程強制執行上限（例如每週最多3封電子郵件），而重新進入冷卻則在個別歷程層級運作（例如，設定檔無法在上次進入後72小時內重新進入此特定歷程）。

此外，可以設定衝突和優先順序管理以將優先順序分數指派給觸發的歷程，確保當多個歷程或行銷活動競爭相同的設定檔，最高優先順序的通訊會獲勝。

**主要考量事項：**

- 頻率上限必須在防止疲勞和確保傳送重要觸發訊息之間取得平衡
- 建議使用通道特定的上限 — 電子郵件、簡訊和推播有不同的疲勞臨界值
- 歷程重新進入冷卻和組織層級的頻率上限可搭配運作；兩者皆應設定
- 優先順序分數會決定達到上限時哪些通訊優先 — 應為優先順序較高的歷程指派較高的分數

**優點：**

- 防止來自高頻事件來源的訊息疲勞
- 維持品牌信譽和訂閱者滿意度
- 組織層級上限可為所有行銷活動和歷程提供安全網
- 優先順序評分可確保最重要的訊息在達到上限時傳送

**限制：**

- 將會抑制部分合格設定檔，可能會遺失相關訊息
- 頻率上限設定增加了管理複雜性
- 大寫字可能會與其他使用中的行銷活動和共用相同頻道的歷程意外互動
- 需要隨著傳訊服務組合變更持續進行監控和調整

**Experience League：**

- [頻率規則](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [商業規則概觀](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [優先順序分數](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [歷程專案管理](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)

### 選項比較

下表比較各個關鍵條件的三個實作選項。

| 條件 | 選項A：簡單事件觸發 | 選項B：有條件且等待 | 選項C：頻率控管 |
| --- | --- | --- | --- |
| 最適合 | 立即確認、確認 | 放棄復原，延遲的條件回應 | 高頻事件來源、多歷程環境 |
| 複雜性 | 低 | 中 | Medium高（新增A或B） |
| 訊息延遲 | 秒到分鐘 | 分鐘到小時/天（可設定的等待） | 與基礎選項（A或B）相同 |
| 自我轉換檢查 | 否 | 是（透過條件或退出條件） | 取決於基礎選項 |
| 頻率保護 | 無（除非與C結合） | 無（除非與C結合） | 是 — 頻道上限與重新進入冷卻 |
| Journey Canvas節點 | 3-4 （事件、選用條件、動作、結束） | 5-7 （事件、等待、條件、分支、動作、結束） | 與A或B相同，加上商業規則設定 |
| 需要 | 事件結構、頻道介面、訊息內容 | 所有選項A +轉換事件擷取 | 所有選項A或B +頻率規則設定 |

### 選擇正確的選項

使用以下決定指引，選取正確的實施選項。

1. **訊息需要立即傳送且無延遲嗎？** 如果是，則以&#x200B;**選項A**&#x200B;開始。確認訊息、歡迎電子郵件和確認通常不需要等待時間。

2. **客戶在收到訊息之前是否有時間自行轉換？** 如果是，請選擇&#x200B;**選項B**。購物車放棄、瀏覽放棄和試用到期使用案例受益於允許客戶自行完成動作的等待期。

3. **觸發事件是否為高頻率（相同設定檔的每個工作階段或每天發生多次）？** 如果是，請在選項A或B上方新增&#x200B;**選項C**&#x200B;作為覆蓋。產品檢視、頁面檢視和搜尋事件可能會產生大量需要頻率保護的觸發器。

4. **沙箱中是否有多個觸發的歷程和行銷活動？** 如果是，無論事件頻率為何，都新增&#x200B;**選項C**&#x200B;以管理跨歷程通訊負載並防止頻道疲勞。

實際上，大部分的生產實作都會針對丟棄式使用案例使用選項B + C （頻率控管的條件等待），針對確認式使用案例使用選項A + C （頻率控管的立即傳送作為安全網）。

## 實作階段

以下階段會逐步進行事件觸發訊息傳送的端對端實作。

### 階段1：設定事件結構描述和資料收集

**應用程式函式：** AEP：資料模型(F2)、AEP：資料來源與集合(F3)

**您的設定專案：**&#x200B;擷取觸發事件的XDM ExperienceEvent結構描述、儲存這些事件的資料集，以及可將事件串流至AEP的即時資料收集管道（Web SDK、Mobile SDK或伺服器API）。 此階段會建立歷程將監聽的資料基礎。

此階段中的&#x200B;**決定點：**

>[!NOTE]
>
>**決定：觸發事件型別**
>
>哪個事件會觸發訊息？ 事件型別會決定所需的結構描述欄位和收集方法。
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| Commerce事件（購物車新增、購買、結帳） | 電子商務使用案例 — 放棄購買、購買後 | 需要具有`productListItems`、`cart`、`order`欄位的Commerce欄位群組 |
>| 網頁互動事件（頁面檢視、產品檢視） | 瀏覽放棄、內容參與觸發程式 | 需要`webPageDetails`，`webInteraction`欄位的Web詳細資料欄位群組 |
>| 應用程式事件（應用程式安裝、解除安裝、應用程式內動作） | 行動參與觸發器 | 需要行動SDK實作和應用程式欄位群組 |
>| 系統事件（付款失敗、訂閱變更、狀態更新） | 操作通知 | 需要伺服器端API或來源聯結器來擷取系統事件 |
>| 表單提交事件 | 銷售機會開發、註冊確認 | 需要自訂欄位群組擷取表單資料欄位 |

>[!NOTE]
>
>**決定：集合方法**
>
>如何擷取觸發事件並串流至AEP？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| Web SDK | 網路型行為事件（購物車新增、頁面檢視、表單提交） | 需要在網站上安裝Web SDK；事件會透過Edge Network即時串流 |
>| Mobile SDK | 行動應用程式事件（應用程式開啟、應用程式內動作、推播權杖註冊） | 需要在原生應用程式或React Native包裝函式中整合Mobile SDK |
>| Edge Network伺服器API | 伺服器端系統事件（付款處理、訂閱管理、後端觸發器） | 無使用者端相依性；從組織的後端系統傳送的事件 |
>| Source聯結器 | 來自外部系統的事件（CRM、行銷自動化、舊版平台） | 通常以批次為基礎；可能不支援即時觸發，除非具有串流功能 |

**UI導覽：**&#x200B;資料收集>資料串流>新增資料串流（針對資料串流設定）；結構描述>建立結構描述（針對事件結構描述）；資料集>從結構描述建立資料集（針對資料集建立）

**金鑰組態詳細資料：**

- 事件結構描述必須包含歷程條件評估和訊息個人化所需的所有欄位
- 資料流必須同時啟用[!DNL Adobe Experience Platform]和[!DNL Adobe Journey Optimizer]服務
- 必須為即時客戶個人檔案啟用資料集，以便事件與統一個人檔案相關聯
- 事件資料必須包含可解析為已知設定檔的身分欄位（電子郵件、CRM ID、ECID）

**Experience League檔案：**

- [XDM系統概覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/xdm/home)
- [設定資料串流](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/datastreams/configure)
- [網頁SDK概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/web-sdk/home)
- [Edge Network伺服器API總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/edge-network-server-api/overview)
- [串流擷取概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/ingestion/streaming/overview)

### 階段2：設定身分和設定檔

**應用程式函式：** AEP：身分和設定檔組態(F4)

**您要設定的專案：**&#x200B;觸發事件識別碼的身分名稱空間、事件結構描述的主要身分指定、跨裝置解析的身分連結規則，以及設定檔統一的合併原則。 這可確保觸發事件與統一客戶設定檔相關聯，以便歷程解決聯絡資訊並傳遞訊息。

此階段中的&#x200B;**決定點：**

>[!NOTE]
>
>**決定：事件結構描述**&#x200B;的主要身分
>
>觸發事件上的哪個身分欄位應作為設定檔解析的主要身分識別？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 電子郵件地址 | 來自已驗證Web工作階段或擷取電子郵件的表單的事件 | 直接解析可聯絡的身分；傳送電子郵件的最簡單路徑 |
>| CRM ID | 來自驗證系統的事件，其中CRM ID是主要識別碼 | 需要建立CRM ID名稱空間；設定檔必須有連結的電子郵件或電話才能傳送訊息 |
>| ECID (Experience Cloud ID) | 無可用已驗證身分的匿名Web或應用程式事件 | 需要身分拼接才能將ECID連結到已知的身分；訊息無法單獨傳送給ECID |
>| 電話號碼 | 來自行動或客服中心互動的事件 | 支援簡訊傳送；需要電話名稱空間 |

**UI導覽：**&#x200B;身分>建立身分名稱空間；結構描述>選取結構描述>選取欄位>身分>設定為主要身分；設定檔>合併原則

**金鑰組態詳細資料：**

- 在ECID透過身分圖表連結至已知的可聯絡身分（電子郵件、電話）之前，匿名事件（僅限ECID）無法觸發訊息傳送
- AJO使用的合併原則必須符合用於對象評估的合併原則
- 針對網頁觸發式傳訊，請確定身分圖表會透過登入事件將ECID連結至已驗證的身分

**Experience League檔案：**

- [身分名稱空間概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/identity/features/namespaces)
- [身分識別圖連結規則](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/identity/features/identity-linking-logic)
- [合併原則概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/merge-policies/overview)

### 階段3：設定管道表面

**應用程式函式：** AJO：頻道設定

**您要設定的專案：**&#x200B;定義觸發訊息之傳送基礎結構的頻道介面（預設集） — 子網域委派、IP集區、寄件者身分、回覆位址、取消訂閱處理和頻道特定認證（簡訊提供者、推播憑證）。 在建立訊息內容或發佈歷程之前，必須存在有效的管道表面。

此階段中的&#x200B;**決定點：**

>[!NOTE]
>
>**決定：訊息頻道**
>
>觸發訊息會使用哪個頻道？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 電子郵件 | 最常觸發的傳訊使用案例 — 放棄復原、確認、入門 | 需要子網域委派、IP集區、傳送者設定；支援豐富的HTML內容和個人化 |
>| 簡訊 | 時效性高的通知、簡潔的警示、具有高SMS參與度的對象 | 需要SMS提供者整合(Sinch、Twilio、Infobip)；受字元限制和較嚴格的同意要求約束 |
>| 推播通知 | 行動應用程式參與度，應用程式使用者重新參與 | 需要推播認證設定（iOS的APN、Android的FCM）；使用者必須安裝應用程式並啟用推播 |
>| 多個管道 | 使用管道偏好設定或遞補邏輯的全方位參與策略 | 需要多個管道表面；管道選擇可透過歷程條件節點管理 |

>[!NOTE]
>
>**決定：子網域委派方法（電子郵件）**
>
>應如何將傳送子網域的電子郵件委派給Adobe？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 完全委派 | 組織希望Adobe管理傳送子網域的所有DNS記錄 | 最簡單的設定；Adobe會自動管理SPF、DKIM、DMARC記錄 |
>| CNAME委派 | 組織想要在指向Adobe基礎架構時維持DNS控制 | 需要手動DNS記錄管理；提供對DNS的更多組織控制 |

**UI導覽：**&#x200B;管理>管道>子網域（用於子網域設定）；管理>管道> IP集區（用於IP集區設定）；管理>管道>管道表面>建立表面（用於表面建立）

**金鑰組態詳細資料：**

- 子網域驗證和DNS傳播最多可能需要48小時
- 新的IP集區需要熱身計畫（逐步增加2-4週的磁碟區）
- 設定一鍵式list-unsubscribe標頭以符合電子郵件規範
- 針對SMS，在建立SMS頻道介面之前設定提供者憑證
- 針對推播，請在建立推播頻道介面之前設定APN和FCM認證

**Experience League檔案：**

- [開始使用電子郵件設定](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [委派子網域](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [建立 IP 池](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [設定頻道介面](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [設定簡訊頻道](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [設定推播通知頻道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### 階段4：建立訊息內容

**應用程式函式：** AJO：訊息製作

**您的設定內容：**&#x200B;歷程將傳送的訊息內容，包括版面設計、使用設定檔和事件屬性的個人化權杖、條件式內容區塊、可重複使用的片段（頁首、頁尾、法律免責宣告），以及內容預覽和測試。

此階段中的&#x200B;**決定點：**

>[!NOTE]
>
>**決定：內容方法**
>
>應如何建立訊息內容？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 從現有範本開始 | 存在組織範本且需要品牌一致性 | 最快的內容建立途徑；確保品牌法規遵循；範本變更會傳播至新訊息 |
>| 在電子郵件Designer中從草稿開始設計 | 此特定觸發訊息所需的自訂配置 | 完整的創意控制；拖放式視覺編輯器；速度較慢但更具彈性 |
>| 匯入HTML | 內容由外部團隊或機構設計，並以HTML的形式提供 | 需要HTML編碼專業知識；可能未完全支援所有電子郵件Designer功能 |

>[!NOTE]
>
>**決定：事件個人化**
>
>訊息內容應使用哪些事件資料？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 事件內容屬性 | 訊息應包含觸發事件的詳細資料（產品名稱、購物車值、表單欄位） | 在個人化編輯器中使用內容事件屬性；資料來自觸發事件裝載 |
>| 輪廓屬性 | 訊息應包含設定檔層級的資料（名字、忠誠度等級、位置） | 透過XDM路徑使用設定檔屬性（例如`profile.person.name.firstName`）；資料來自統一的設定檔 |
>| 事件和設定檔屬性 | 訊息應結合事件內容與設定檔個人化 | 觸發訊息最常見的方法；確保相關性（事件）和個人化（設定檔） |

**UI導覽：**&#x200B;內容管理>內容範本>瀏覽（針對範本選擇）；行銷活動或歷程動作>編輯內容>電子郵件Designer （針對內容設計）；選取文字元件> Personalization圖示（針對新增個人化）

**金鑰組態詳細資料：**

- 使用內容屬性來個人化觸發事件的資料（例如產品名稱、購物車值）
- 對名稱、偏好設定和忠誠度資料使用設定檔屬性
- 設定條件式內容區塊，以依設定檔區段或屬性來變更內容（例如，忠誠會員可透過不同的CTA）
- 為觸發訊息間共用的頁首、頁尾和法律免責宣告建立可重複使用的片段
- 使用多個測試設定檔預覽，以驗證個人化轉譯器正確
- 在發佈歷程之前傳送校樣給內部利害關係人

**Experience League檔案：**

- [設計電子郵件內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [新增個人化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization語法](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [動態內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [使用內容範本](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [使用內容片段](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [預覽和測試您的內容](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### 階段5：建立並設定歷程

**應用程式功能：** AJO： Journey Orchestration、AJO：頻率與商業規則（選項C）、AJO：衝突與優先順序管理

**您將要設定的專案：**&#x200B;監聽觸發事件並協調訊息傳遞的歷程。 這是核心實作階段，其中的歷程畫布的設計包含事件進入節點、條件節點、等待步驟（適用於選項B）、訊息動作節點和退出條件。 此階段也涵蓋頻率治理（選項C）和衝突/優先順序設定。

此階段中的&#x200B;**決定點：**

>[!NOTE]
>
>**決定：重新進入規則**
>
>如果觸發事件再次發生，設定檔可以重新進入此歷程嗎？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 允許重新進入（使用冷卻） | 事件可以合法地重複發生，每次發生事件時都需要傳送訊息（例如，每次放棄購物車都應觸發復原訊息） | 設定冷卻期間（最少5分鐘）以防止重複事件快速重新進入；一般冷卻範圍為1小時到72小時 |
>| 不重新進入 | 無論事件是否重複發生（例如，首次註冊後的歡迎訊息），每個設定檔只應傳送一次訊息 | 設定檔會在首次歷程完成後永久排除；適用於一次性生命週期訊息 |

>[!NOTE]
>
>**決定：等待期間（僅限選項B）**
>
>歷程應等待多久才評估條件並傳送訊息？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 短時間等待（1-4小時） | 緊急使用案例，例如放棄購物車，即時後續追蹤有效 | 較高的訊息量；可能會遇到一些自我轉換者；最適合高價值的購物車復原 |
>| Medium等待（12-24小時） | 中度緊急使用案例，例如瀏覽放棄或內容參與 | 平衡的方法；減少不必要的傳送，同時保持關聯性 |
>| 長時間等待（2-7天） | 低急迫性的使用案例，例如試用到期提醒或定期簽到 | 訊息量較低；喪失內容關聯性的風險較高 |
>| 自訂日期/時間 | 與特定日期相連結的使用案例（例如，在試用到期日前3天傳送） | 等到計算的日期/時間為止；使用自訂運算式編輯器 |

>[!NOTE]
>
>**決定：退出條件**
>
>在什麼條件下，應該先從歷程中移除設定檔，才能到達訊息動作？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 轉換事件（例如完成購買） | 目標為轉換的購物車或瀏覽放棄率 | 偵測到轉換事件時，設定檔會自動退出；選項B會採取最乾淨的方法 |
>| 對象會籍變更 | 如果設定檔離開合格區段，則應退出 | 需要近乎即時更新的串流評估對象 |
>| 歷程逾時（最長91天） | 預設行為 — 設定檔在歷程持續時間上限之後結束 | 安全網；不應是短期觸發歷程的主要退出機制 |
>| 沒有明確的退出條件 | 簡單確認（選項A），每個合格設定檔都應該收到訊息 | 設定檔會在訊息動作和結束節點後自然結束 |

>[!NOTE]
>
>**決定：頻率控管（選項C）**
>
>每個時段設定檔應該收到多少個觸發訊息？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 頻道特定上限（例如，每週3封電子郵件、每日1則簡訊） | 不同的管道具有不同的疲勞臨界值 | 建議的方法；尊重每個頻道的入侵等級 |
>| 全域上限（例如，所有管道每週5則訊息） | 簡化所有通訊型別的控管 | 更易於管理，但較不精細；可能會過度限制侵入性較低的管道 |
>| 僅限歷程層級重新進入冷卻 | 此特定歷程所需的頻率控管，但不適用於整個組織 | 最簡單的實施；無法避免跨歷程疲勞 |

**UI導覽：**&#x200B;歷程>建立歷程（用於建立歷程）；歷程畫布>拖曳事件活動（用於事件輸入）；歷程畫布>拖曳「等待」活動（用於等待設定）；歷程畫布>拖曳「條件」活動（用於條件分支）；歷程屬性>退出條件（用於退出設定）；管理>商業規則>建立規則（用於頻率上限）

**金鑰組態詳細資料：**

- 選取事件結構並定義資格條件，以設定歷程事件
- 若為選項B，在事件專案之後、任何條件評估之前，立即新增等待節點
- 使用設定檔屬性、事件資料或對象成員資格檢查來設定條件節點
- 將訊息動作節點連結至頻道介面，並從第3階段和第4階段編寫內容
- 將歷程逾時設為適當的持續時間（觸發的歷程短於91天）
- 針對選項C，在發佈歷程之前透過管理>商業規則建立頻率規則
- 如果其他行銷活動或歷程鎖定重疊的對象，則為歷程指派優先順序分數

**選項差異的位置：**

選項A的&#x200B;**（簡單事件觸發）：**
歷程畫布最小：事件輸入>選擇性同意/資格條件>訊息動作>結束。 沒有等待步驟或轉換檢查。 根據事件是否應在每次發生時產生訊息來設定重新進入規則。

選項B的&#x200B;**條件（等待條件）：**
在事件專案後新增等待節點。 在等待後，新增條件節點以檢查轉換（例如，檢查是否在歷程進入後發生`commerce.purchases`事件）或使用退出條件自動移除轉換的設定檔。 「未轉換」路徑上的訊息動作分支和「已轉換」路徑上的結束節點。

選項C （頻率控管）的&#x200B;**：**
在發佈之前透過「管理>商業規則」設定組織層級的頻率上限。 在歷程屬性中設定歷程層級重新進入冷卻。 或者透過歷程屬性指派優先順序分數，以控制達到上限時哪些通訊會獲勝。 這可在選項A或選項B之上套用。

**Experience League檔案：**

- [建立歷程](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [歷程屬性](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [一般事件](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [條件活動](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [等待活動](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [在歷程中新增訊息](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [退出條件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [歷程專案管理](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [頻率規則](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [優先順序分數](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [識別潛在衝突](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/conflict-prioritization/conflicts)

### 階段6：測試並部署歷程

**應用程式函式：** AJO： Journey Orchestration

**您將會設定的專案：**&#x200B;測試模式驗證，以驗證歷程在測試設定檔中的運作是否如預期，接著發佈歷程使其上線。

**UI導覽：**&#x200B;歷程畫布>測試模式切換（用於測試）；歷程畫布>發佈（用於部署）

**金鑰組態詳細資料：**

- 在歷程畫布上啟用測試模式，以使用測試設定檔模擬事件觸發器
- 選取具有有效管道聯絡資訊（電子郵件地址、電話號碼）的測試設定檔
- 觸發測試事件並驗證測試設定檔是否周遊預期路徑
- 對於選項B，請確認等待步驟的行為是否正確，以及條件評估是否產生預期的分支
- 確認個人化權杖在測試訊息中正確呈現
- 成功測試後，發佈歷程以使其上線
- 監視發佈後的歷程狀態和初始設定檔專案量度

**Experience League檔案：**

- [測試您的歷程](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [發佈歷程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)

### 階段7：效能的監控和報告

**應用程式功能：** AJO：報告及效能分析，S4：監視及可觀察性，S5：報告及分析

**您的設定專案：**&#x200B;傳遞和參與監視的即時和歷史歷程報告、事件擷取和歷程處理失敗的平台警示，以及更深入跨管道分析觸發式訊息有效性的CJA工作區。

此階段中的&#x200B;**決定點：**

>[!NOTE]
>
>**決定：報告深度**
>
>此使用案例需要多少報告分析？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 僅限AJO原生報表 | 傳送量度的作業監控就足夠了 | 立即可用；封面已傳送、已傳送、已退回、已開啟、已點按；無需額外設定 |
>| AJO原生+ CJA整合 | 需要跨管道分析、轉換歸因和趨勢分析 | 需要CJA連線和連結至AJO資料集的資料檢視；提供更深入的分析功能 |

**UI導覽：**&#x200B;歷程>選取歷程>即時報告（供即時監視使用）；歷程>選取歷程>所有時間報告（供歷史分析使用）；警報>警報規則>訂閱（供警報設定使用）

**金鑰組態詳細資料：**

- 在活動執行期間存取歷程即時報告，以監控設定檔登入、退出和傳送量度
- 歷程啟動足夠的時間來累積有意義的資料後，請檢閱歷史報表
- 設定來源資料流執行失敗（事件擷取）和歷程處理延遲的警報
- 針對CJA整合，請確定CJA連線包含AJO體驗事件資料集（訊息回饋事件資料集、電子郵件追蹤體驗事件資料集）

**Experience League檔案：**

- [歷程即時報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [歷程全域報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [使用Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [警報概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/observability/alerts/overview)
- [AJO + CJA整合指南](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

## 實施考量

本節涵蓋事件觸發訊息實作的護欄、常見陷阱、最佳實務和取捨決策。

### 護欄和限制

以下平台護欄和限制適用於事件觸發的訊息實施。

- **單一事件輸送量：**&#x200B;單一事件歷程的每個沙箱每秒最多5,000個事件 — [Journey Optimizer護欄](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/get-started/guardrails)
- **即時歷程限制：**&#x200B;每個沙箱最多500個即時歷程 — [Journey Optimizer護欄](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/get-started/guardrails)
- **歷程畫布限制：**&#x200B;每個歷程畫布最多50個活動
- **歷程逾時：**&#x200B;歷程持續時間上限為91天（全域逾時）
- **重新進入冷卻：**&#x200B;最少重新進入冷卻為5分鐘
- **頻率上限設定：**&#x200B;每個沙箱最多10個上限設定
- **管道表面：**&#x200B;每個沙箱每個管道型別最多10個管道表面
- **串流擷取：**&#x200B;每個HTTP連線每秒最多20,000筆記錄 — [擷取護欄](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/ingestion/guardrails)
- **計算屬性：**&#x200B;每個沙箱最多25個計算屬性 — [計算屬性護欄](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/computed-attributes/overview#guardrails)
- **內容片段：**&#x200B;每則訊息最多30個內容片段
- **即時報告重新整理：**&#x200B;即時報告每60秒重新整理一次，並顯示過去24小時的資料
- **歷史報告延遲：**&#x200B;歷史（所有時間）報告最多可能需要2小時，才能在執行結束後完整填入

### 常見陷阱

實施事件觸發的訊息傳送時，請注意下列常見問題。

- **未解析身分的匿名事件：**&#x200B;觸發事件時，只包含ECID （匿名Cookie識別碼），無法解析為可連絡的設定檔以進行訊息傳遞。 確保觸發事件包含已驗證的身分或身分圖表將ECID連結至已知連絡人。 如果沒有身分解析，設定檔會進入歷程，但在訊息傳送步驟失敗。

- **遺失選項B條件檢查的轉換事件：**&#x200B;如果轉換事件（例如，購買）未擷取到AEP中，或未與觸發事件相同的設定檔身分相關聯，則條件檢查將會錯誤評估為「未轉換」，並傳送不必要的訊息。 確認轉換事件即時流入AEP，並與觸發事件共用身分。

- **過於寬鬆的重新進入規則：**&#x200B;允許重新進入，而高頻事件來源沒有冷卻期間，可能會導致相同的設定檔在幾分鐘內收到多則訊息。 一律設定符合業務內容的重新進入降溫（例如，放棄購物車的4小時降溫、放棄瀏覽的24小時降溫）。

- **等待步驟時區未對齊：**&#x200B;預設會以UTC處理等待步驟。 如果歷程定位多個時區的設定檔，且等待應與收件者的當地時間一致，請相應地設定歷程的時區設定。

- **與其他行銷活動相衝突的頻率上限：**&#x200B;組織層級的頻率上限適用於所有行銷活動和歷程。 如果設定檔已從其他作用中行銷活動達到上限，則可能會隱藏新的觸發歷程。 監視隱藏率並調整優先順序分數，以確保重要觸發訊息有優先順序。

- **由於遺失相依性而導致歷程發佈失敗：**&#x200B;歷程畫布中的每個分支都必須以結束活動終止。 所有動作節點都必須參照具有作用中訊息內容的有效管道表面。 請先驗證所有相依性，然後再發佈。

### 最佳實務

請遵循這些建議，以成功實施事件觸發的訊息傳送。

- **開始簡單，然後重複：**&#x200B;對於新的觸發式傳訊使用案例，從選項A開始。 只有在驗證事件管道和訊息傳送後，才新增等待和條件邏輯（選項B）。 當多個觸發的歷程處於作用中狀態時，新增頻率治理（選項C）。

- **使用退出條件而非條件節點進行轉換檢查：**&#x200B;當發生合格事件（例如購買）時，退出條件會自動從歷程中移除設定檔，消除在等待步驟後需要明確條件節點的情形。 這樣可產生更乾淨的歷程畫布和更快速的轉換偵測。

- **在開發沙箱中使用真實事件資料進行測試：**&#x200B;使用測試模式搭配實際事件裝載（不僅僅是測試設定檔），以驗證事件結構描述欄位、個人化權杖和條件運算式能否正確搭配生產資料運作。

- **設定事件特定重新進入的降級：**&#x200B;將降級期間與觸發事件的業務內容比對。 放棄購物車歷程通常會使用4-24小時的降溫；確認歷程可以允許立即重新進入；上線歷程應該阻止完全重新進入。

- **以健康狀態量度來監視隱藏率：**&#x200B;如果隱藏率（設定檔符合資格，但因頻率上限或條件而未收到訊息）超過30-40%，請檢閱上限是否太嚴格，或觸發事件的定義是否過於寬泛。

- **版本歷程而非編輯即時歷程：**&#x200B;無法直接編輯即時歷程。 複製歷程、進行變更，然後停止舊版本並發佈新版本，藉此建立新版本。 這可避免中斷目前歷程中的設定檔。

- **在條件節點中包含遞補/預設路徑：**&#x200B;永遠在條件節點中設定預設（其他）路徑，以處理非預期的設定檔狀態。 不符合任何條件分支的設定檔應正常結束，而不是維持卡住。

### 權衡決定

設計事件觸發的訊息實作時，請考慮下列取捨。

>[!NOTE]
>
>**取捨：訊息速度與訊息關聯性**
>
>立即傳送訊息（選項A）可加快傳送速度，但可能傳送訊息給可自行轉換的客戶。 延遲條件式傳遞（選項B）透過篩選掉自我轉換程式而改善關聯性，但會引入延遲，以降低急迫性。
>
>- **選項A的優點：**&#x200B;快速、簡單、確認式使用案例，每個事件都需要訊息
>- **選項B偏好：**&#x200B;關聯性、減少訊息疲勞、丟棄型使用案例（自我轉換很常見）
>- **建議：**&#x200B;對於速度為主要值的交易式訊息和確認訊息，請使用選項A。 在關聯性超過速度的情況下，使用選項B來復原和重新參與訊息。 嘗試等待持續時間，以找出每個使用案例的最佳平衡。

>[!NOTE]
>
>**取捨：頻率保護與訊息涵蓋範圍**
>
>嚴格的頻率上限（選項C）可防止疲勞，但當設定檔接近其上限時，可能會抑制重要的觸發訊息。 允許或無上限將涵蓋範圍最大化，但存在過度傳送訊息和頻道疲勞的風險。
>
>- **嚴格上限優先：**&#x200B;客戶體驗、品牌信譽、傳遞能力（垃圾郵件投訴較少）
>- **允許的上限優先：**&#x200B;訊息涵蓋範圍，轉換機會，避免錯過的觸發程式
>- **建議：**&#x200B;從業界標準上限（每週3-5封電子郵件、每週1-2封簡訊、每週2-3個推播/天）開始，並根據參與量度和取消訂閱率進行調整。 將較高的優先順序分數指派給觸發訊息，以便在達到上限時贏得批次行銷活動。

>[!NOTE]
>
>**取捨：歷程簡單與歷程複雜**
>
>簡單的歷程（少數節點，無分支）較容易建立、測試和維護，但提供的情境適應有限。 複雜的歷程（多個條件、分支路徑、區段檢查）可帶來更細微的回應，但會增加複雜性和錯誤風險。
>
>- **簡單歷程的好處：**&#x200B;實作更快、偵錯更容易、維護負擔更輕
>- **精緻的歷程受到青睞：**&#x200B;更精確的目標定位、更佳的個人化、減少不必要的傳送
>- **建議：**&#x200B;從符合業務需求的最簡單歷程開始。 根據效能資料以增量方式增加複雜性。 運作可靠的簡單歷程，比未偵測到錯誤的複雜歷程更有價值。

## 相關文件

下列資源提供此實作中所使用功能的其他詳細資料。

### Journey orchestration

- [開始使用歷程](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [建立歷程](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [歷程屬性](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [一般事件](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [對象資格鑑定事件](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)
- [條件活動](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [等待活動](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [在歷程中新增訊息](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [退出條件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [歷程專案管理](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [測試您的歷程](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [發佈歷程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)

### 管道設定

- [開始使用電子郵件設定](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [委派子網域](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [建立 IP 池](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [IP熱身計畫](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [電子郵件表面設定](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [設定簡訊頻道](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [設定推播通知頻道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [管理隱藏清單](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### 訊息製作與個人化

- [建立電子郵件](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/channels/email/create-email)
- [設計電子郵件內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [新增個人化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization語法](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [輔助函式](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [動態內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [使用內容範本](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [使用內容片段](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [預覽和測試您的內容](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/content-management/preview-test/preview-test)
- [建立簡訊訊息](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/channels/sms/create-sms)
- [設計推播通知](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/channels/push/design-push)

### 頻率與商業規則

- [頻率規則](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [商業規則概觀](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [設定API上限](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/channel-surfaces/capping)

### 衝突與優先順序管理

- [開始使用衝突與優先順序管理](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [識別潛在衝突](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/conflict-prioritization/conflicts)
- [優先順序分數](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [歷程上限和仲裁](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/conflict-prioritization/journey-capping)

### 報告與效能

- [歷程即時報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [歷程全域報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [AJO + CJA整合指南](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

### 資料收集與擷取

- [網頁SDK概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/web-sdk/home)
- [行動SDK概觀](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [Edge Network伺服器API總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/edge-network-server-api/overview)
- [設定資料串流](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/datastreams/configure)
- [串流擷取概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/ingestion/streaming/overview)

### 資料模型與結構描述

- [XDM系統概覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/xdm/home)
- [結構描述組合基本面](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/xdm/schema/composition)

### 身分和設定檔

- [Identity Service總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/identity/home)
- [身分名稱空間概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/identity/features/namespaces)
- [身分識別圖連結規則](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/identity/features/identity-linking-logic)
- [設定檔概述](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/home)
- [合併原則概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/merge-policies/overview)

### 細分與對象

- [Segmentation Service概述](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/home)
- [區段產生器UI指南](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/ui/segment-builder)
- [串流區段](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/methods/streaming-segmentation)

### 資料控管和同意

- [資料控管概覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/home)
- [資料使用標籤概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/labels/overview)
- [同意和偏好設定欄位群組](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/xdm/field-groups/profile/consents)
- [Journey Optimizer中的同意](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)

### 計算的屬性

- [計算屬性概述](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/computed-attributes/overview)
- [計算屬性UI指南](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/computed-attributes/ui)

### 監視和可觀察性

- [警報概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/observability/alerts/overview)
- [可觀察性深入分析概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/observability/home)

### 護欄

- [Journey Optimizer護欄](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/get-started/guardrails)
- [即時客戶個人檔案護欄](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/guardrails)
- [擷取護欄](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/ingestion/guardrails)

### 教學課程與指南

- [建立歷程教學課程](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [安裝Web SDK](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/web-sdk/install/overview)
