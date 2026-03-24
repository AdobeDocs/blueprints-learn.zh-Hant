---
title: 具有決策的跨頻道歷程
description: 瞭解如何結合即時決策來協調多步驟歷程，以選取最佳頻道、內容或選件。
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: eabdd91f-bb7d-4de3-adb5-5940d3ca4a78
source-git-commit: e8185f348f926acab2ca2e0c3cd55c08c663cf41
workflow-type: tm+mt
source-wordcount: '9029'
ht-degree: 2%

---

# 具有決策的跨頻道歷程

本指南提供包含決策的跨管道歷程的完整實施參考。 它專為需要協調多步驟、多頻道歷程，並在一個或多個歷程節點納入即時決策的解決方案架構師、行銷技術人員和實施工程師所設計。

使用本指南來瞭解實作選擇的完整面貌、評估取捨，並導覽至相關的Experience League檔案以取得詳細的設定指示。

具有決策的跨頻道歷程是[!DNL Adobe Experience Platform]生態系統中最複雜的行銷活動協調模式。 透過結合即時決策（使用[!DNL AJO]決策評估設定檔的目前內容，並在歷程畫布內的一個或多個決策點動態選取最佳管道、內容或選件），來擴充多步驟協調歷程。

## 使用案例概述

組織越來越需要提供最適化、個人化的客戶歷程，這些歷程會動態回應每個人的即時內容，而不是遵循固定的預先決定順序。 客戶的偏好管道、參與記錄、忠誠度等級、預測期限值以及目前產品興趣，都會影響每個接觸點下的最佳動作。

具有決策的跨頻道歷程結合兩種強大的[!DNL AJO]功能來解決此需求：歷程協調（管理多步驟流程、時間、條件和頻道傳送）和決策（評估適用性規則、套用排名策略，並在每個決策點選取最佳優惠或內容變體）。

此模式適用於下列情況：

- 歷程必須動態地適應每個設定檔的即時狀態，而不是遵循固定的頻道或內容順序
- 多個選件、內容變體或管道為一個或多個歷程節點的候選專案，應根據設定檔內容選取最佳選項
- 需要AI輔助或公式型排名，才能在整個歷程中最佳化優惠選擇
- 企業想要將管道選擇邏輯和優惠方案管理整合至集中的決策架構，而非維持複雜的分支邏輯

目標受眾包括管理生命週期計畫、忠誠度歷程、回傳序列和上線流程的行銷人員，其中大規模個人化需要在每個接觸點進行自動化決策。

>[!NOTE]
>如果您的歷程不需要在個別節點進行動態決策，例如固定順序的Nurture或上線計畫，請參閱[多步驟協調歷程](multi-step-orchestrated-journey.md)。 該模式設定起來比較簡單，而且不需要AJO Decisioning。

## 主要業務目標

此使用案例模式支援下列業務目標。

**[提供個人化的客戶體驗](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**
根據個別偏好設定、行為和生命週期階段量身打造內容、選件和訊息。
**KPI：**&#x200B;參與度、轉換率、客戶滿意度(CSAT)

**[提高客戶忠誠度和期限值](../../business-objectives/revenue-monetization/increase-customer-loyalty-lifetime-value.md)**
透過忠誠計畫、獎勵和個人化參與，深化客戶關係並最大化長期價值。
**KPI：**&#x200B;客戶期限值、留存率、向上銷售/交叉銷售%

**[改善客戶保留率](../../business-objectives/customer-experience/improve-customer-retention.md)**
透過價值導向的體驗和持續培養的關係，讓現有客戶持續參與並更新。
**KPI：**&#x200B;保留率、客戶期限值、參與度

**[推動交叉銷售和追加銷售收入](../../business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)**
根據行為和購買記錄，向現有客戶推廣補充性和優質產品或服務。
**KPI：**&#x200B;向上銷售/交叉銷售%、遞增收入、客戶期限值

## 戰術使用案例範例

以下案例說明如何將具有決策的跨管道歷程應用於實踐。

- **最適化回饋歷程** — 多步驟歷程，決策會根據每個設定檔的參與歷史記錄選取頻道（電子郵件、推播或簡訊），並根據預測的期限值以動態方式選取最佳激勵優惠
- **次佳動作生命週期歷程** — 決定決定要在客戶生命週期的每個階段進行溝通，從入門內容、交叉銷售優惠、忠誠度獎勵或保留獎勵中進行選取
- **使用動態內容選擇進行個人化上線** — 新的客戶上線歷程，其中每個接觸點使用決策來選取最相關的產品教育內容、提示或啟用優惠
- **具有個人化獎勵的跨管道忠誠度方案歷程** — 忠誠度會員在歷程中取得進展，決策會根據層級、購買歷史記錄和類別相關性來選取個人化獎勵優惠
- **動態重新參與管道和獎勵最佳化** — 休眠客戶重新參與，其中動態選取外聯管道和獎勵以最大化回應機率
- **具有AI排名內容推薦的客戶生命週期Nurture** — 持續的Nurture歷程，其中AI排名決策會從每個接觸點選取最相關的內容或產品推薦

## 關鍵績效指標

使用下列KPI來評估此使用案例模式的成效。

| KPI | 說明 | 測量方法 |
| --- | --- | --- |
| 歷程完成率 | 完成完整歷程的設定檔百分比 | 歷程報告：已完成/已進入 |
| 優惠接受率 | 參與決策所選優惠方案的百分比（已點按、已贖回） | 決策報告：優惠點按數/優惠曝光數 |
| 管道參與率 | 在歷程中使用的每個管道的開啟和點按率 | 歷程報告中的每管道傳遞量度 |
| 轉換率 | 完成目標轉換動作的歷程參與者百分比 | 歷程退出事件追蹤或CJA funnel分析 |
| 遞補優惠率 | 傳回遞補優惠而非個人化優惠的決策請求百分比 | 決策報告：遞補選擇/選擇總數 |
| 客戶期限值影響 | 歷程參與者與控制組的CLV變更 | CJA同類群組分析搭配保留比較 |
| 交叉銷售/追加銷售收入 | 歸因於決策所選優惠的遞增收入 | 優惠方案導向轉換的CJA歸因分析 |
| 決策排名有效性 | AI排名選件與隨機/優先順序型選擇之間的效能差異 | A/B實驗比較排名策略 |

## 使用案例模式

**具有決策的跨頻道歷程**

協調多步驟、多頻道歷程，其整合一或多個節點的即時決策，以選取最佳頻道、內容或選件。

**函式鏈：**&#x200B;對象評估>歷程執行>決定節點>頻道選擇>訊息傳送>報告

## 應用程式

以下應用程式可用來實作此使用案例模式。

- **[!DNL Adobe Journey Optimizer] ([!DNL AJO])** — 歷程協調（多步驟畫布設計、進入條件、等待、條件、退出條件）、跨管道的訊息編寫、管道表面設定、衝突和優先順序管理
- **[!DNL Adobe Journey Optimizer]決策** — 優惠和內容專案管理、適用性規則、排名策略（優先順序、公式、AI）、決定原則、位置、遞補優惠
- **[!DNL Adobe Real-Time Customer Data Platform] ([!DNL RT-CDP])** — 歷程專案與優惠方案適用性區段的對象評估、使用運算屬性和傾向分數擴充設定檔、同意和治理強制執行
- **[!DNL Adobe Experience Platform] ([!DNL AEP])** — 即時客戶設定檔存放區、跨管道解析的身分服務、資料模型及擷取基礎結構

## 基礎函式

下列基本功能必須為此使用案例模式準備就緒。 對於每個函式，狀態會指出它通常是必要的、假設為預先設定或不適用。

| 基礎函式 | 狀態 | 必須準備就緒的專案 | Experience League參考 |
| --- | --- | --- | --- |
| 管理與治理 | 已假設就位 | [!DNL AJO]沙箱，已設定歷程、行銷活動和決策許可權。 所有可能傳遞頻道的頻道介面。 歷程設計者、決策管理員和內容作者的使用者角色。 | [沙箱總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sandbox/home)，[存取控制總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/access-control/home) |
| 資料模型與準備 | 必填 | 設定檔結構描述必須包括用於決策的屬性（例如，忠誠度等級、購買歷史記錄、管道偏好設定、參與分數）。 必須設定優惠目錄和決定專案結構描述。 ExperienceEvent結構描述必須擷取適用性規則和排名公式所使用的行為訊號。 | [XDM系統總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/xdm/home)，[結構描述組合基本概念](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/xdm/schema/composition) |
| 資料來源與收集 | 已假設就位 | 決策所使用的設定檔屬性和行為訊號必須是最新的。 如果歷程使用事件觸發的進入或退出條件，則需要即時事件串流。 網頁SDK、行動SDK或伺服器端集合必須適用於提供決策內容的管道。 | [網頁SDK概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/web-sdk/home)，[來源概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sources/home) |
| 身分和設定檔設定 | 必填 | 跨頻道身分解析至關重要 — 歷程必須跨電子郵件、推播、簡訊和網頁解析設定檔。 合併原則必須產生用於決策的統一設定檔。 必須設定所有客戶識別碼（CRM ID、電子郵件、ECID、電話）的識別名稱空間。 | [身分識別服務總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/identity/home)，[合併原則總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/merge-policies/overview) |
| 對象定義與細分 | 必填 | 歷程的進入對象定義。 歷程中用於優惠方案適用性規則和條件分支的其他區段。 評估方法必須符合延遲要求（即時輸入的串流，排程的批次）。 | [區段服務總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/home)，[區段產生器UI指南](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/ui/segment-builder) |

## 支援功能

以下功能可擴大此使用案例模式，但不是核心執行的必要功能。

| 支援功能 | 狀態 | 為什麼這很重要 | Experience League參考 |
| --- | --- | --- | --- |
| 計算/衍生屬性建立 | 推薦 | Customer AI傾向分數、參與分數、管道偏好分數和期限值計算等計算屬性可大幅改善決策品質。 這些豐富的設定檔屬性可啟用更複雜的適用性規則和排名公式。 | [計算屬性總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/computed-attributes/overview)，[Customer AI總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/intelligent-services/customer-ai/overview) |
| 資料生命週期管理 | 推薦 | 優惠歷史記錄和決定事件資料會隨著時間累積，應該有保留原則。 跨多個管道的同意實作是很重要的 — 未經該管道有效同意的設定檔必須從該管道的傳送路徑中排除。 | [進階資料生命週期管理概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-lifecycle/home)，[Journey Optimizer中的同意](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted) |
| 資料使用標籤和實作 | 推薦 | 當決策可能將設定檔路由到具有不同資料使用限制的不同管道時，跨多個管道和選件型別的治理實作很重要。 確保跨所有管道提供符合規定的優惠方案。 | [資料治理總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/home)，[原則執行](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/enforcement/overview) |
| 監控與可觀察性 | 已包含 | 歷程與決策監視對於生產作業至關重要。 歷程進入失敗、決策後援尖峰和傳送錯誤的警報可讓您快速解決問題。 | [警示概述](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/observability/alerts/overview)，[可觀察性深入分析概述](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/observability/home) |
| 報告與分析 | 已包含 | 報告階段涵蓋歷程和決定報告。 CJA針對決策成效、管道組合最佳化、優惠效能和歷程ROI的分析，提供完善排名策略及最佳化一段時間之歷程所需的深入分析。 | [CJA概觀](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-overview/cja-overview)，[AJO + CJA整合指南](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/reporting/channel-report/cja-ajo) |

## 應用程式函式

此計畫會從應用程式功能目錄中執行下列功能。 函式會對應至實作階段，而非編號步驟。

### [!DNL Journey Optimizer] ([!DNL AJO])

| 函式 | 實作階段 | 說明 |
| --- | --- | --- |
| 通道設定 | 階段2：通道設定 | 為決策可選取或歷程使用（電子郵件、簡訊、推播、應用程式內）的所有頻道設定頻道介面 |
| 訊息製作 | 階段4：訊息製作 | 為每個頻道製作訊息內容並整合決定輸出 — 優惠位置、動態內容區塊、來自選定優惠的個人化權杖 |
| 決策 | 階段3：決策設定 | 針對歷程中的每個決定點設定優惠專案、適用性規則、排名策略、決定政策和遞補優惠 |
| Journey Orchestration | 階段5：歷程設計與啟動 | 設計包含進入條件、決定節點、管道路由、等待步驟、訊息動作和退出條件的多步驟歷程畫布 |
| 衝突與優先順序管理 | 階段5：歷程設計與啟動 | 如果多個歷程可能同時鎖定相同的設定檔，請設定優先順序分數和衝突偵測 |
| 頻率與業務規則 | 階段5：歷程設計與啟動 | 跨頻道強制執行訊息頻率上限，以防止多頻道歷程中過度傳送訊息 |
| 報告與效能分析 | 第6階段：報告與監控 | 監控歷程和每個節點的傳遞量度、決策效能和管道參與 |

### [!DNL Real-Time CDP] ([!DNL RT-CDP])

| 函式 | 實作階段 | 說明 |
| --- | --- | --- |
| 對象評估 | 階段1：對象評估 | 定義並評估進入對象或合格進入事件；建立決策使用的資格區段 |
| 輪廓富集 | 先決條件/支援 | 使用計算的屬性和傾向分數豐富設定檔，以改善決策品質 |
| 同意與治理實施 | 階段2：通道設定 | 跨所有管道強制執行同意偏好設定；確保符合的優惠方案傳送 |

## 先決條件

開始實作前請先完成下列作業。

- [ ] [!DNL AJO]沙箱已布建歷程協調與決策功能已啟用
- [ ]所有目標頻道（電子郵件、簡訊、推播）皆有使用中、已驗證的頻道介面
- [ ]設定檔結構描述包含決策所需的屬性（忠誠度等級、購買記錄、管道偏好設定、參與分數）
- [ ]已設定跨管道身分解析 — 設定檔可以跨電子郵件、推播權杖、電話號碼和網頁識別碼解析
- [ 已定義]個專案對象，並使用非零母體進行評估
- [ ]優惠方案目錄內容（創意資產、復本、法律免責宣告）已核准並準備好進行設定
- [ 正在擷取]同意資料，且所有目標管道的同意強制都作用中
- [ 每個管道的]內容範本和片段均已設計和核准
- [ 如果組織具有跨行銷活動頻率原則，則會定義並部署]頻率限定規則
- [ ]如果使用AI排名決定，則模型訓練存在至少1,000個轉換事件

## 實作選項

檢閱下列選項，並選取最符合您需求的方法。

### 選項A：具有Offer Decisioning的歷程（固定頻道、動態內容）

**最適合：**&#x200B;頻道順序已預先決定，但每個接觸點上的內容或優惠應動態選取的歷程 — 提供個人化獎勵的忠誠度歷程、重新參與動態獎勵、以AI排名內容推薦的生命週期培養。

#### 運作方式

歷程畫布定義管道和時間的固定順序（例如，第0天：電子郵件、第3天：推播、第7天：簡訊）。 在每個訊息動作節點上，決定原則會從已設定的合格專案目錄中選取要納入訊息中的最佳優惠或內容。 優惠在[!DNL AJO]決定目錄中管理，其適用性規則會篩選哪個設定檔符合資格，而排名策略會決定哪個適用優惠最適合。

此方法會區分「何時與何處」（歷程協調）與「何處」（決策）。 歷程設計人員可控制管道流程，而決策管理員則可獨立控制優惠方案目錄、適用規則和排名邏輯。 這種關注點分離讓實施更具可維護性，並允許優惠方案目錄演化而不修改歷程畫布。

選件版位會使用電子郵件Designer或其他頻道編輯器，直接內嵌在訊息內容中。 在傳遞時轉譯訊息時，決策引擎會評估設定檔的資格和等級，以針對訊息中的每個位置選取最佳優惠方案。

#### 主要考量事項

- 管道順序是靜態的 — 所有設定檔都遵循相同的管道路徑，無論其偏好設定為何
- 決策複雜性較低，因為它只會選取內容/選件，不會選取管道
- 優惠方案目錄可與歷程分開管理
- 必須為每個位置設定遞補優惠，以處理沒有合格個人化優惠的設定檔

#### 優點

- 更簡單的歷程畫布 — 沒有用於頻道選擇的分支邏輯
- 歷程設計和優惠方案管理之間的關注點清楚區分
- 更容易測試和驗證 — 每個管道路徑都是確定性的
- 降低實作複雜度，縮短上市時間
- 優惠方案目錄變更會立即生效，無需修改歷程

#### 限制

- 無法根據個別設定檔行為或偏好設定調整頻道
- 偏好某一個管道而非另一個管道的設定檔仍會在預先決定的管道上接收訊息
- 未針對頻道層級的參與率最佳化

#### Experience League參考資料

- [在訊息中傳遞優惠方案](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [決策管理概觀](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)

### 選項B：選擇動態頻道的歷程（固定內容、動態頻道）

**最適合：**&#x200B;歷程，其中每個接觸點的內容都類似，但頻道應根據設定檔內容來動態選取 — 最適化回合（電子郵件與推播的比較，以及根據互動的簡訊），次佳動作程式，其中頻道最佳化為主要目標。

#### 運作方式

歷程使用由設定檔屬性（例如管道偏好設定分數、上次參與管道或同意狀態）或決策輸出通知的條件節點，將設定檔路由到不同的管道路徑。 每個路徑都會透過其訊息動作節點，提供通道專屬的內容。 決策邏輯會根據設定檔的行為記錄，判斷哪個頻道最有可能引發參與。

管道選擇可使用具有設定檔屬性評估的歷程條件節點來實施（例如，如果`channelPreference = "push"`路由到推送路徑），或使用具有管道特定專案的決策來實施，其中每個「優惠」代表一個管道，而排名策略會決定最佳管道。

此方法可最佳化傳遞管道，同時保持各管道內容相對一致。 它要求為每個可能的頻道編寫訊息內容，並且必須為所有候選頻道設定頻道介面。

#### 主要考量事項

- 需要每個候選頻道的訊息內容變體
- 所有可能的色版中，色版表面都必須為作用中
- 條件邏輯或決策設定必須說明同意 — 未取得SMS同意的設定檔無法路由至SMS路徑
- 歷程畫布對每個頻道具有分支路徑，因此較為複雜

#### 優點

- 最佳化每個個別設定檔的管道選擇
- 透過在偏好頻道上觸及設定檔來提高整體參與度
- 透過同意感知路由自動尊重通道特定同意
- 可將參與歷史記錄和管道偏好設定分數納入路由決策

#### 限制

- 包含多個管道分支的更複雜歷程畫布
- 每個管道都必須分別編寫內容（儘管訊息目的相同）
- 較難測試 — 必須驗證所有可能的管道路徑
- 每個管道中的內容個人化是靜態的（無Offer Decisioning）

#### Experience League參考資料

- [條件活動](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [建立歷程](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)

### 選項C：完整的最適化歷程（動態頻道+動態內容）

**最適合：**&#x200B;最大個人化 — 頻道和內容/選件都會在每個節點動態選取。 適用於高價值客戶區段、複雜的忠誠度計畫，以及具有成熟決策實務和豐富設定檔資料的組織。

#### 運作方式

此選項結合選項A和B。此歷程在兩個層級使用決策：第一，決定要用於每個接觸點的管道，第二，決定要在所選管道中傳送的內容或選件。 歷程中的每個決定點都會評估設定檔的目前內容，以進行頻道和內容選擇。

實作需要完整決策設定，以及通道選擇和內容/優惠選擇的決策政策。 管道選擇可能使用決定原則，其中每個專案代表一個具有根據同意和參與之適用性規則的管道，而內容選擇使用單獨的決定原則，優惠專案按相關性排名。

這是最複雜的變體，需要最深入的Journey Orchestration與Decisioning整合。 它提供最高度的個人化，但也要求最高的設定、測試和持續管理。

#### 主要考量事項

- 需要兩個決策層 — 頻道選擇和內容選擇
- 每個節點的巢狀分支和決策動作導致Journey Canvas複雜度最高
- 所有可能的管道內容組合都需要進行廣泛的測試
- 需要豐富的設定檔資料（參與歷史記錄、管道偏好設定、產品相似性、傾向分數）才能做出有效的決策
- AI排名決策的優點來自計算屬性

#### 優點

- 最大化的個人化 — 每個接觸點都針對頻道和內容進行最佳化
- 設定良好的實施的最佳參與度和轉換潛力
- 集中決策中的所有個人化邏輯，而非靜態歷程分支
- 可透過AI排名模型學習持續改善

#### 限制

- 最高的實作複雜度和上市時間
- 需要最廣泛的選件目錄和管道內容準備
- 發生傳遞問題時較難進行疑難排解
- 需要具備豐富設定檔屬性的成熟資料基礎架構
- AI排名需要足夠的轉換事件數量才能進行模型訓練

#### Experience League參考資料

- [決策管理概觀](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [排名策略](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### 選項比較

請使用下表來簡單比較三個實作選項。

| 條件 | 選項A：Offer Decisioning | 選項B：動態管道 | 選項C：完全最適化 |
| --- | --- | --- | --- |
| 最適合 | 固定管道順序，動態內容 | 管道最佳化、一致內容 | 兩個維度的最大個人化值 |
| 複雜性 | 中 | Medium — 高 | 高 |
| 歷程畫布 | 簡單（與動作節點上的決策呈線性） | 稽核（管道路徑的分支） | 複雜（含多級決策的巢狀分支） |
| 決策範圍 | 僅限內容/選件選取範圍 | 僅限頻道選擇 | 管道和內容選擇 |
| 內容需求 | 每個管道一組內容（包含優惠方案版位） | 每個候選管道的內容 | 每個候選頻道具有優惠方案版位的內容 |
| 設定檔資料需求 | 稽核（優惠資格屬性） | 稽核（頻道偏好設定、參與） | 高（頻道和選件屬性） |
| 上市時間 | 更快 | 稽核 | 最長 |
| 持續管理 | 優惠方案目錄管理 | 管道路由邏輯管理 | 優惠方案目錄和管道路由 |
| Personalization深度 | 內容各異，頻道固定 | 頻道不盡相同，內容類似 | 頻道和內容都不同 |

### 選擇正確的選項

請依照下列指引決定最適合您情況的選項。

- **如果您的頻道策略已定義（例如「我們一律先傳送電子郵件，然後推播，再傳送簡訊」），且主要的個人化需求是在每個接觸點選取正確的優惠方案或內容，請從選項A**&#x200B;開始。 這是剛開始決策的組織最常見的起點。

- **如果頻道最佳化是您的主要目標，請選擇選項B** — 您希望在每位客戶最有可能參與的頻道上與其取得聯絡，但各頻道間的訊息內容相對一致。 這需要設定檔上的管道偏好設定資料。

- **只有當您擁有成熟的決策基礎結構、豐富的設定檔資料（包括計算的屬性和傾向分數）、填入良好的優惠方案目錄以及管理複雜性的組織能力時，才選擇選項C**。 許多組織從選項A或B開始，隨著決策成熟度的提高而演化到選項C。

- **如果您不確定**，請從選項A開始。它以最低的複雜度提供有意義的個人化，而且如果您稍後改用選項C，您為選項A建立的選件目錄可直接重複使用。

## 實作階段

以下階段會逐步說明此使用案例模式的端對端實作。

### 階段1：對象評估

**應用程式函式：** [!DNL RT-CDP]：對象評估

此階段會設定進入對象，以判斷哪些設定檔進入歷程，以及用於歷程中優惠方案適用性規則或條件分支的任何其他區段。 對象定義是所有下游歷程和決定邏輯的基礎。

#### 決定：專案型別

設定檔應如何進入歷程 — 透過已排程的對象讀取或即時事件觸發器？

>[!NOTE]
>根據您的歷程時間和觸發要求，選取一個專案型別。

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 讀取對象（批次專案） | 生命週期方案、忠誠度歷程、排程的重新參與行銷活動 | 設定檔會在排程的時間批次輸入；在讀取時間評估對象；支援大型對象大小 |
| 對象資格（串流） | 設定檔進入或退出區段時，應該發生進入的行為觸發歷程 | 近乎即時登入；需要符合串流條件的區段定義；適用於里程碑式歷程 |
| 單一事件（事件觸發器） | 特定事件應觸發歷程（例如，購買、購物車放棄、註冊） | 事件的即時專案；需要事件結構描述設定；限製為每秒5,000個事件 |

#### 決定：對象評估方法

對象必須符合設定檔資格的速度？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 批次 | 每日或定期的對象更新便已足夠；已排程的行銷活動式歷程 | 每個工作最多可處理2400萬個設定檔；以排程為基礎；支援大部分的區段規則運算式 |
| 串流 | 事件觸發或資格型專案需要即時對象成員資格 | 近乎即時；區段規則函式集有限；沒有以時間為基礎的彙總 |
| Edge | 需要相同工作階段資格 | 毫秒延遲；僅限簡易屬性檢查；僅限邊緣設定檔屬性 |

#### 關鍵設定詳細資料

**UI導覽：**&#x200B;客戶>對象>建立對象>建置規則

- 使用區段產生器搭配以相關設定檔屬性和行為事件為目標的區段規則運算式，以定義登入對象
- 如果優惠適用性規則參考區段會籍（例如「高價值客戶」、「忠誠金級客戶」），請建立其他適用性區段
- 在繼續歷程設定之前，驗證對象母體為非零
- 選取產生決策所需統一設定檔檢視的合併原則

#### Experience League檔案

- [區段產生器UI指南](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/ui/segment-builder)
- [串流區段](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [邊緣分段](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Profile Query Language參考](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/pql/overview)

### 階段2：通道設定

**應用程式函式：** [!DNL AJO]：頻道設定

此階段會設定歷程可能用於訊息傳送之每個頻道的頻道介面。 在可以編寫訊息或發佈歷程之前，所有候選頻道都必須有已驗證的有效介面。 對於此模式，您通常會至少設定電子郵件、簡訊和推播的介面，如果決定可能選取這些管道，則可能會設定應用程式內或網頁。

#### 決定：要設定哪些管道

哪些頻道是歷程的候選頻道 — 作為固定歷程步驟（選項A/B）或作為可決策選取的頻道（選項B/C）？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 僅限電子郵件 | 具有Offer Decisioning的單一管道歷程（選項A，僅限電子郵件） | 最簡單的設定；需要子網域委派和IP熱身 |
| 電子郵件+推播 | 雙管道歷程；適用於以參與為中心的歷程 | 推播需要APN/FCM憑證；行動應用程式必須整合SDK |
| 電子郵件+簡訊+推播 | 完整的跨頻道歷程；最常見於選項B和C | SMS需要提供者憑證(Sinch、Twilio、Infobip)；每個頻道需要自己的介面 |
| 電子郵件+簡訊+推播+應用程式內 | 包括工作階段內介面的最大頻道涵蓋範圍 | 應用程式內需有行動SDK和應用程式表面設定 |

#### 決定：子網域委派方法（電子郵件）

應如何將傳送子網域委派給Adobe？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 完全委派 | 組織希望Adobe管理傳送子網域的所有DNS記錄 | 最簡單的設定；Adobe處理SPF、DKIM、DMARC；較少控制DNS |
| CNAME委派 | 組織需要維持DNS記錄的控制 | 更複雜的設定；客戶管理DNS；提供更大的彈性 |

#### 關鍵設定詳細資料

**UI導覽：**&#x200B;管理>管道>管道表面>建立表面

- 電子郵件：設定子網域、IP集區、寄件者名稱、回覆位址和取消訂閱處理
- SMS：設定SMS提供者認證和寄件者號碼
- 推送通知：設定iOS和Android的APNs和FCM認證
- 在繼續之前，請先確認每個曲面都處於「作用中」狀態
- 確認電子郵件傳送IP的IP熱身已完成

#### Experience League檔案

- [開始使用電子郵件設定](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [委派子網域](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [建立 IP 池](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [設定簡訊頻道](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [設定推播通知頻道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### 階段3：決策設定

**應用程式函式：** [!DNL AJO]：決策

此階段會設定完整的決定架構，包括位置、適用性規則、個人化優惠、遞補優惠、集合限定詞、集合、排名策略和決定政策。 此階段會建立將在歷程決策點叫用的決策邏輯。

#### 決定：決定範圍

決策應該選取什麼 — 選件/內容（選項A）、管道（選項B）或兩者（選項C）？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 僅限選件/內容選擇 | 管道順序已固定；內容中已包含個人化 | 決定原則會根據每個位置來鎖定具有內容表示的優惠方案專案 |
| 僅限頻道選擇 | 內容一致；最佳化在傳遞通道上 | 決策專案代表管道；資格包括同意檢查；排名使用參與資料 |
| 管道和內容 | 跨頻道和內容的完整適應性個人化 | 需要兩層的決策原則；最複雜但最高的個人化 |

#### 決定：排名策略

如何排名合格的優惠以選取最佳優惠方案？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 優先順序（手動） | 商業規則決定選件重要性的簡單排名 | 每個選件都有優先順序分數；最高優先順序的勝利；決定性的且易於理解 |
| 以公式為基礎（自訂運算式） | 排名應考慮到設定檔屬性（例如CLV、層級、相似性分數） | 自訂排名公式會評估設定檔內容；比優先順序更動態；不需要ML |
| AI排名（自動最佳化） | 應根據歷史轉換資料自動最佳化排名 | AI模型會從轉換事件學習；至少需要1,000個事件才能訓練；持續改善 |

#### 決定：優惠上限

選件的顯示次數是否應該有限制？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 每個設定檔上限 | 避免將相同的選件重複顯示至相同的設定檔 | 避免選件疲勞；在高輸送量下可能會發生計數器延遲 |
| 全域上限 | 限制所有設定檔的曝光總數（例如有限庫存促銷） | 控制總曝光率；適用於供給限制優惠方案 |
| 無上限 | 每個符合資格的曝光都應該顯示優惠 | 最簡單；適用於歷久不衰的內容或無限制的優惠 |

#### 關鍵設定詳細資料

**UI導覽：**&#x200B;元件>決定管理>位置/優惠/決定

- 為每個頻道和內容型別組合建立版位（例如電子郵件HTML橫幅、推播JSON、簡訊文字）
- 使用參考設定檔屬性或對象成員資格的區段規則運算式，定義適用性規則
- 建立個人化優惠方案，包含每個刊登版位的代表、指派適用性規則並設定優先順序
- 建立涵蓋所有刊登版位的遞補優惠 — 當沒有個人化優惠符合資格時，就會傳回此項
- 使用集合限定詞（標籤）將優惠方案組織成集合
- 設定排名策略 — 優先順序、公式或AI排名
- 建立將位置、集合、排名策略和遞補優惠繫結的決策原則
- 先核准所有優惠方案，再由決定加以選取

#### 選項差異之處

選項A (Offer Decisioning)的&#x200B;**：**
建立著重於每個頻道中內容個人化的版位和選件（例如電子郵件主圖橫幅選件、電子郵件頁尾選件、推播通知內文選件）。 決定原則會為訊息中的每個版位選取最佳內容。

選項B的&#x200B;**（動態頻道選擇）：**
建立代表每個管道的決策專案。 適用性規則包括同意檢查（例如，設定檔必須有SMS同意才能符合SMS專案的資格）。 排名會使用管道參與分數或公式型運算式。

選項C的&#x200B;**（完全最適化）：**
設定兩個決策層：一組用於頻道選擇的決策政策，另一組用於所選頻道內的內容/優惠選擇。 這兩個層級都需要位置、優惠方案、適用規則和排名策略。

#### Experience League檔案

- [決策管理概觀](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [建立產品建議放置環境](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [建立決定規則](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [建立個人化優惠方案](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [建立後備產品建議](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [建立集合](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [建立決定](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [排名策略](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### 階段4：訊息製作

**應用程式函式：** [!DNL AJO]：訊息製作

此階段會為歷程中的每個管道和接觸點設定訊息內容，並將決策輸出（選取的選件內容）整合到訊息範本中。 歷程中的每個訊息動作節點都需要編寫內容與適當的管道表面、個人化權杖和選件位置整合。

#### 決定：內容方法

應如何為每個頻道建立訊息內容？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 基於範本 | 組織已建立品牌範本；一致性很重要 | 更快速的撰寫；確保品牌一致性；可能會限制設計彈性 |
| 從頭開始設計 | 此歷程的唯一創意；無現有範本 | 完整的設計控制項；較長的撰寫時間；使用電子郵件Designer拖放 |
| 匯入HTML | Creative團隊會在外部產生HTML；匯入至[!DNL AJO] | 保留外部設計工作流程；需要HTML與Email Designer的相容性 |

#### 決定： Personalization範圍

除了決策輸出之外，訊息應該包含什麼等級的個人化？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 基本個人化（姓名、問候語） | 除了選件選擇以外的最小個人化需求 | 簡單Handlebars運算式；低複雜性 |
| 條件式內容區塊 | 不同區段或屬性的不同內容區段 | 使用動態內容規則；內容會因設定檔屬性或區段成員資格而異 |
| 透過決策整合實現完全個人化 | 內嵌在訊息中的優惠方案位置，並結合設定檔的個人化 | 將Offer Decisioning輸出與Handlebars個人化權杖結合；最豐富的體驗 |

#### 關鍵設定詳細資料

**使用者介面導覽：**&#x200B;選取行銷活動或歷程動作>編輯內容>傳送電子郵件給Designer /頻道編輯器

- 為歷程中使用的每個管道（電子郵件、簡訊、推播、應用程式內）編寫訊息內容
- 將優惠決定版位嵌入訊息內容，以決定選取的優惠應顯示於何處
- 使用設定檔屬性的Handlebars語法新增個人化運算式（例如，`{{profile.person.name.firstName}}`）
- 為區段特定的傳訊設定條件式內容區塊
- 為共用元素建立可重複使用的內容片段（頁首、頁尾、法律免責宣告）
- 使用範例設定檔進行預覽和測試，以驗證個人化轉譯器是否正確
- 傳送證明訊息以供利害關係人稽核

#### 選項差異之處

選項A (Offer Decisioning)的&#x200B;**：**
每則訊息都包含優惠方案位置，決策選取的內容會在此處顯示。 訊息版面配置一致，但選件區域會動態顯示每個設定檔的最佳選件。

選項B的&#x200B;**（動態頻道選擇）：**
每個頻道都有各自獨立撰寫的訊息內容。 各管道的內容類似，但因應管道限制（電子郵件HTML、簡訊與推播通知格式）而調整。

選項C的&#x200B;**（完全最適化）：**
每個頻道都有其本身的訊息內容，其中包含內嵌的選件位置。 該管道以及該管道中的優惠方案內容都會以動態方式選取。

#### Experience League檔案

- [設計電子郵件內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [新增個人化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [動態內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [在訊息中傳遞優惠方案](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [使用內容範本](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [使用內容片段](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [建立簡訊訊息](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/channels/sms/create-sms)
- [設計推播通知](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/channels/push/design-push)

### 階段5：歷程設計與啟動

**應用程式函式：** [!DNL AJO]：Journey Orchestration，[!DNL AJO]：衝突與優先順序管理，[!DNL AJO]：頻率與商業規則

此階段會設定完整的歷程畫布，包括登入設定、連結至已設定決策原則的決策節點、管道路由的條件分割（選項B/C）、每個管道路徑的訊息動作節點、接觸點之間的等待節點、退出條件、衝突/優先順序設定和頻率上限規則。 此階段會將所有先前設定的元件組合成協調的歷程流程並加以啟用。

#### 決定：重新進入原則

設定檔完成或退出後可以重新進入歷程嗎？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 允許重新進入（使用冷卻） | 設定檔可能再次符合資格的週期性歷程（例如，每季忠誠度續約） | 設定冷卻期間（最少5分鐘）以防止立即重新進入；設定檔會從頭開始 |
| 禁止重新進入 | 單次歷程，每個設定檔只能周遊一次（例如上線） | 設定檔完成或退出後無法重新進入；較簡單的行為 |

#### 決定：退出條件

在什麼情況下，應該將設定檔在完成前從歷程中移除？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 對象會籍變更 | 當設定檔離開登入對象或進入隱藏對象時，即應退出 | 區段變更時即時退出；對於「已轉換」或「已退出」退出很有用 |
| 事件發生 | 特定事件（例如，購買、取消訂閱）應觸發退出 | 事件即時退出；需要事件結構描述設定 |
| 逾時 | 歷程經過的最長持續時間 | 預設上限為91天，以防止設定檔無限期保留 |

#### 決定：歷程逾時

設定檔可以在歷程中保留的最大期間是多少？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 91天（最大值） | 透過延長的培養序列長時間執行生命週期歷程 | 允許的最長持續時間；設定檔會在91天後結束，無論如何 |
| 自訂較短的持續時間 | 有時限的行銷活動或季節性歷程 | 根據歷程商業邏輯設定；較短的逾時可減少過時設定檔 |

#### 決定：衝突與優先順序設定

此歷程是否應該有與其他歷程/行銷活動衝突解決的優先順序評分？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 高優先順序(70-100) | 應優先處理的關鍵客戶歷程（保留率、忠誠度） | 當多重通訊競爭時，優先順序較高者會獲勝；請謹慎使用 |
| Medium優先順序(30-69) | 標準生命週期歷程 | 優先順序平衡；可能被較高優先順序的通訊抑制 |
| 低優先順序(0-29) | 補充或資訊歷程 | 與更重要的通訊競爭時，將被抑制 |

#### 關鍵設定詳細資料

**UI導覽：**&#x200B;歷程>建立歷程

- 建立歷程及設定屬性（名稱、說明、時區、逾時）
- 設定專案：讀取對象（適用於批次）或事件觸發器（適用於即時）
- 新增從階段3連結到已設定決策原則的決策節點
- 根據決策輸出或設定檔屬性新增管道路由的條件分割（選項B/C）
- 為每個管道路徑新增訊息動作節點，連結至階段4的編寫內容
- 在接觸點之間新增等待節點（對象讀取歷程至少1小時）
- 定義退出條件（對象變更、事件、逾時）
- 指派衝突解決的優先順序分數
- 設定頻率限定，如果跨歷程頻率限制適用
- 在發佈之前使用測試設定檔在測試模式下測試歷程
- 發佈歷程以使其上線

#### 選項差異之處

選項A (Offer Decisioning)的&#x200B;**：**
歷程畫布與內嵌於每個訊息動作節點中的決定原則是線性的。 管道選取範圍沒有分支。 優惠決定是在動作節點內的訊息轉譯時做出的。

選項B的&#x200B;**（動態頻道選擇）：**
在每個等待步驟後，新增條件節點，以評估管道選擇標準（設定檔屬性、決策輸出或同意狀態）。 每個條件分支都會導向通道特定的訊息動作節點。 針對不符合任何條件的設定檔納入預設/其他路徑。

選項C的&#x200B;**（完全最適化）：**
結合管道選擇條件節點與決定原則內嵌訊息動作節點。 在每個接觸點：首先，條件或決定決定決定頻道；然後，在所選頻道的訊息動作中，決定原則會選取最佳優惠/內容。

#### Experience League檔案

- [建立歷程](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [歷程屬性](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [讀取對象活動](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [條件活動](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [等待活動](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [在歷程中新增訊息](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [退出條件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [歷程專案管理](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [測試您的歷程](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [發佈歷程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)
- [優先順序分數](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [衝突與優先順序管理概觀](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [頻率規則](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)

### 第6階段：報告與監控

**應用程式函式：** [!DNL AJO]：報表與效能分析

此階段會透過即時報告（在執行期間）和歷史報告（完成之後）來設定歷程和決策效能監控。 決策專用量度，包括優惠選擇分佈、遞補率和排名有效性。 可選擇使用CJA工作區分析，以進行深入的跨頻道歷程與決策ROI分析。

#### 決定：報告深度

需要何種層級的報表分析？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 僅[!DNL AJO]個原生報告 | 傳遞和參與量度的營運監控 | 內建即時和歷史報告；無其他設定；僅限[!DNL AJO]個量度 |
| [!DNL AJO] + CJA分析 | 深入跨管道分析、決策效益、歷程ROI、同類群組分析 | 需要CJA連線和資料檢視；提供歸因、funnel和同類群組分析功能 |

#### 關鍵設定詳細資料

**UI導覽：**&#x200B;歷程>選取歷程>即時報告/所有時間報告

- 在初始執行期間，針對登入、退出和每個節點量度監控歷程即時報告
- 檢閱決策效能：優惠選擇分配、遞補優惠率、排名有效性
- 歷程完成後，請檢閱歷史報表以進行端對端funnel分析
- 針對CJA分析：請確定CJA連線包含[!DNL AJO]個資料集（訊息回饋事件、電子郵件追蹤事件）
- 使用面板建置CJA工作區，以進行管道組合分析、選件效能比較和歷程轉換漏斗
- 建立歷程啟動日期和重大設定變更的註解

#### Experience League檔案

- [歷程即時報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [歷程全域報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [使用Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Analysis Workspace概觀](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/home)
- [AJO + CJA整合指南](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

## 實施考量

在實施之前和期間，檢閱下列護欄、常見陷阱、最佳實務和取捨決定。

### 護欄和限制

- 每個沙箱最多500個即時歷程 — [Journey Optimizer護欄](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/get-started/guardrails)
- 歷程持續時間上限為91天（全域逾時）
- 每個歷程畫布最多50個活動
- 讀取對象歷程每秒最多可處理20,000個設定檔
- 單一事件歷程支援每個沙箱每秒最多5,000個事件
- 每個沙箱最多10,000個核准的個人化優惠
- 每個決定最多30個位置
- 優惠方案傳送回應時間SLA：對於單一範圍請求，P95時間小於500毫秒
- AI排名模型需要至少1,000個轉換事件才能訓練
- 每個沙箱每個管道型別最多10個管道表面
- 對於受眾讀取的歷程，等待步驟的最短持續時間為1小時
- 歷程重新進入冷卻最短為5分鐘
- 每個沙箱最多4,000個區段定義 — [平台護欄](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/guardrails)

### 常見陷阱

**決定一律會傳回遞補優惠：**&#x200B;確認個人化優惠在其有效日期範圍內已核准（未處於草稿狀態），且適用性規則與目標設定檔的屬性相符。 檢查是否尚未達到優惠方案上限。 使用設定檔進行測試，該設定檔應明確符合個人化優惠的資格。

**歷程已發佈，但設定檔未進入：**&#x200B;對於對象已讀取的歷程，請確認對象已評估的母體大於零。 對於事件觸發的歷程，請驗證事件結構、觸發條件以及事件是否已傳送。 檢查進入對象合併原則是否符合歷程的預期合併原則。

**未正確套用排名公式：**&#x200B;請確認公式語法有效，並參考可存取的設定檔屬性。 公式錯誤會無訊息地回復到以優先順序為基礎的排名，而不會發出警告。 使用具有不同屬性值的設定檔測試排名，以確認公式產生預期順序。

**管道路由會忽略同意：**&#x200B;管道選取的條件節點必須包含同意檢查。 未經SMS同意的設定檔不得路由到SMS路徑。 使用管道選擇決策時，將同意建立至適用性規則中（選項B/C）。

**在高輸送量下提供上限計數器會延遲：**&#x200B;在高輸送量情況下，提供上限計數器可能會延遲幾秒。 如果精確上限很關鍵，請將全域上限與緩衝或頻率規則結合使用。

**歷程畫布超過50個活動的限制：**&#x200B;包含許多管道分支和決定節點的複雜選項C歷程可能會接近50個活動的限制。 透過合併條件邏輯、減少接觸點數量或分割為多個循序歷程來簡化。

**Edge決定傳回空白的個人化：**&#x200B;如果針對即時決定使用邊緣決定，請確定資料流已啟用[!DNL Adobe Journey Optimizer]服務，且決定範圍的格式正確。 Edge決定僅限於邊緣設定檔存放區中可用的設定檔屬性。

### 最佳實務

**開始簡單並改進：**&#x200B;從選項A （固定管道、動態優惠方案）開始驗證決策架構，然後隨著您的資料成熟度和組織容量增加，改進為選項B或C。

**投資於個人檔案擴充：**&#x200B;參與分數、管道偏好設定索引和Customer AI傾向分數等計算屬性可大幅改善決策品質。 在設定複雜的排名策略之前，請先建置這些擴充屬性。

**永遠設定遞補優惠：**&#x200B;每個決定原則都必須有遞補優惠。 將遞補優惠方案設計成真正寶貴的內容（而非空白的預留位置），因為它們提供的設定檔不符合任何個人化優惠方案的資格。

**使用不同的設定檔進行測試：**&#x200B;使用測試模式，讓設定檔代表不同的適用路徑、管道偏好設定和屬性組合。 在發佈之前，請確認每個可能的歷程路徑和決策結果都可正常運作。

**將遞補費率監控為健康狀態量度：**&#x200B;高遞補優惠費率表示適用性規則過於嚴格，或優惠方案目錄未涵蓋足夠的設定檔區段。 針對設定良好的決策，設定遞補率低於20%。

**使用內容片段實現跨管道一致性：**&#x200B;建立共用內容片段（頁首、頁尾、法律免責宣告、取消訂閱區塊），以維持歷程中電子郵件、簡訊和推播訊息的品牌一致性。

**主動設定退出條件：**&#x200B;定義轉換事件（例如購買、註冊）的退出條件，以便完成所需動作的設定檔會立即從歷程中移除，而非繼續接收訊息。

**指派有意義的優先順序分數：**&#x200B;執行多個歷程和行銷活動時，根據業務影響指派優先順序分數。 高價值保留歷程的優先順序應高於資訊通訊。

### 權衡決定

請檢閱下列權衡，以告知您的實施選擇。

#### 決策複雜性與上市時間

更複雜的決策（具有AI排名的選項C）可提供更高的個人化程度，但需要更多的設定、資料準備和測試時間。

- **選項A/B的好處：**&#x200B;部署更快、測試更簡單、持續管理開銷更低
- **選項C偏好：**&#x200B;最大個人化、持續的AI驅動最佳化、最高的參與潛力
- **建議：**&#x200B;以選項A或B開始進行初始啟動。 收集效能資料並平行建置設定檔擴充屬性。 如果您至少有1,000個AI排名培訓和填入豐富選件目錄的轉換事件，請改良為選項C。

#### 選擇管道的靜態分支與決策

管道選擇可透過簡單的歷程條件節點（直接評估設定檔屬性）或透過決策架構（其中管道會模型化為具有資格和排名的決策專案）實施。

- **靜態條件節點適合：**&#x200B;簡單、透明、易於疑難排解。 當管道選擇邏輯簡單明瞭（例如「如果推播權杖存在且上次推播在30天內開啟，請使用推播；否則請使用電子郵件」）時效果最佳。
- **以決策為基礎的管道選擇偏好：**&#x200B;集中管理、AI最佳化潛力、無需修改歷程畫布即可改進排名邏輯的能力。 當頻道選擇複雜時為最佳，並應隨時間改善。
- **建議：**&#x200B;當管道選取條件簡單且定義明確時，請使用選項B的靜態條件節點。 當您想要讓AI隨著時間最佳化管道選擇，或當管道選擇邏輯複雜到足以受益於集中資格和排名管理時，請使用決策式管道選擇。

#### 提供詳細程度vs.目錄管理功能

包含許多鎖定目標優惠方案的大型、精細優惠方案目錄，可產生更精確的個人化，但需要更多管理工作。 較小型且適用性較廣的目錄更容易管理，但較不個人化。

- **大型目錄（許多特定選件）的優點：**&#x200B;較高的個人化精確度、對不同對象更相關的選擇、較低的遞補率
- **小型目錄（較少廣泛優惠）優惠：**&#x200B;更輕鬆的管理、更快速的設定、更簡單的測試、更低孤立優惠的風險
- **建議：**&#x200B;從5到15個個人化優惠方案開始，再加上1個遞補決定。 新增更多優惠方案，因為您會觀察哪些區段最常收到遞補優惠方案。 使用集合限定詞，依類別、層級或產品線來組織優惠方案，以符合管理的成長。

#### 優先順序型與AI排名型決策

以優先順序為基礎的排名具有決定性和透明度。 AI排名決策會自動最佳化，但需要培訓資料，而且透明度較低。

- **優先順序排名優惠：**&#x200B;可預測性、透明度、立即部署、不需要訓練資料
- **AI排名決策優點：**&#x200B;持續最佳化、資料導向選擇、探索不明顯優惠方案設定檔相關性的能力
- **建議：**&#x200B;針對初始部署使用優先順序或公式排名。 一旦您累積至少1,000個轉換事件，並想要從規則型最佳化移至模型型最佳化，即可轉換至AI排名決策。

## 相關文件

下列資源提供在此使用案例模式中所使用功能的其他詳細資料。

### Journey orchestration

- [開始使用歷程](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [建立歷程](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [歷程屬性](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [讀取對象活動](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [一般事件](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [對象資格鑑定事件](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)
- [條件活動](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [等待活動](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [在歷程中新增訊息](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [退出條件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [歷程專案管理](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [測試您的歷程](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [發佈歷程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)

### 決定管理

- [決策管理概觀](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [建立產品建議放置環境](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [建立決定規則](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [建立個人化優惠方案](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [建立後備產品建議](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [建立集合](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [建立集合限定詞](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-tags)
- [建立決定](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [排名策略](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)
- [在訊息中傳遞優惠方案](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

### 管道設定

- [開始使用電子郵件設定](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [委派子網域](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [建立 IP 池](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [IP熱身計畫](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [電子郵件表面設定](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [設定簡訊頻道](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [設定推播通知頻道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### 訊息製作與個人化

- [建立電子郵件](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/channels/email/create-email)
- [設計電子郵件內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [新增個人化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization語法](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [動態內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [使用內容範本](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [使用內容片段](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [預覽和測試您的內容](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### 衝突、優先順序和頻率管理

- [衝突與優先順序管理概觀](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [優先順序分數](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [識別潛在衝突](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/conflict-prioritization/conflicts)
- [歷程上限和仲裁](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/conflict-prioritization/journey-capping)
- [頻率規則](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)

### 對象和細分

- [Segmentation Service概述](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/home)
- [區段產生器UI指南](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/ui/segment-builder)
- [串流區段](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [邊緣分段](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/methods/edge-segmentation)
- [對象構成](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/ui/audience-composition)
- [Profile Query Language參考](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/pql/overview)

### 報告與分析

- [歷程即時報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [歷程全域報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [使用Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [AJO + CJA整合指南](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [CJA概觀](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-overview/cja-overview)
- [Analysis Workspace概觀](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/home)

### 設定檔與身分

- [即時客戶個人檔案總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/home)
- [Identity Service總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/identity/home)
- [合併原則概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/merge-policies/overview)
- [計算屬性概述](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/computed-attributes/overview)
- [Customer AI概述](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/intelligent-services/customer-ai/overview)

### 資料控管和同意

- [資料控管概覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/home)
- [Journey Optimizer中的同意](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)
- [管理隱藏清單](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### 護欄

- [Journey Optimizer護欄](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/get-started/guardrails)
- [即時客戶個人檔案護欄](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/guardrails)
- [Identity Service護欄](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/identity/guardrails)
