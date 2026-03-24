---
title: Offer Decisioning
description: 瞭解如何使用集中式決定邏輯，跨頻道為設定檔選取次優優惠或內容。
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 8fd511b3-0200-41bf-aff1-e3f2a00a578e
source-git-commit: e8185f348f926acab2ca2e0c3cd55c08c663cf41
workflow-type: tm+mt
source-wordcount: '8026'
ht-degree: 2%

---

# Offer decisioning

本指南提供使用[!DNL Adobe Journey Optimizer] (AJO) Decisioning和[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)之Offer Decisioning的完整實作參考。 它專為需要實作集中式優惠選擇邏輯以決定跨管道每個客戶設定檔次佳優惠的解決方案架構師、行銷技術人員和實作工程師所設計。

使用本指南瞭解需要設定的專案、有哪些選擇，以及適用於每個決定的折衷方案。

此模式會將「要顯示的內容」決定與「顯示位置」頻道邏輯分離，以啟用跨電子郵件、網頁、行動應用程式和任何其他接觸點的一致最佳化優惠選擇。 AJO Decisioning會管理完整的優惠生命週期：優惠建立和目錄管理、適用性規則（誰可以看到每個優惠）、排名策略（如何在合格優惠中進行選取）、位置（優惠出現的位置）和決定策略（將所有內容繫結在一起）。

## 使用案例概述

組織經常需要在互動的時刻向每位客戶提供最相關的優惠方案、促銷活動或獎勵。 無論互動發生在電子郵件促銷活動、網站首頁、行動應用程式中，還是多步驟歷程中的決策點，挑戰都相同：根據客戶身分、客戶資格，以及最有可能帶來所要結果的選件，從可用選項的目錄中選取最佳選件。

Offer Decisioning可透過在AJO的決策管理引擎中集中所有優惠方案選擇邏輯來解決此問題。 決定引擎不會將優惠指派硬式編碼至個別行銷活動或管道，而是評估每個設定檔的屬性、對象成員資格和內容訊號，以即時決定最佳優惠。 這種集中化可確保同一個客戶無論透過哪個管道進行互動，都能獲得一致且最佳化的優惠方案。

此模式在範圍上與已知訪客的網頁/應用程式個人化不同 — offer decisioning不受通道限制，而且是集中式，而已知訪客的個人化著重於數位介面個人化。 它與目錄模型中的行為建議不同 — 當符合資格的專案集受商業規則、資格限制或法規要求（促銷活動、金融產品、獎勵）控管時，請使用Offer Decisioning。 當專案集很大、持續變更，且選擇是由行為相似度或相似性訊號（產品目錄、內容資料庫）驅動時，使用行為建議。

## 主要業務目標

此使用案例模式支援下列業務目標。

**[提供個人化的客戶體驗](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**
根據個別偏好設定、行為和生命週期階段量身打造內容、選件和訊息。
**KPI：**&#x200B;參與度、轉換率、客戶滿意度(CSAT)

**[推動交叉銷售和追加銷售收入](../../business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)**
根據行為和購買記錄，向現有客戶推廣補充性和優質產品或服務。
**KPI：**&#x200B;向上銷售/交叉銷售%、遞增收入、客戶期限值

**[提高客戶忠誠度和期限值](../../business-objectives/revenue-monetization/increase-customer-loyalty-lifetime-value.md)**
透過忠誠計畫、獎勵和個人化參與，深化客戶關係並最大化長期價值。
**KPI：**&#x200B;客戶期限值、留存率、向上銷售/交叉銷售%

## 戰術使用案例範例

下列案例說明如何在實務中套用Offer Decisioning。

- 電子郵件行銷活動中的下一個最佳優惠方案 — 選取傳送時每個收件者的最相關促銷活動
- 網站上的即時促銷橫幅 — 決策功能會根據訪客的設定檔，在頁面載入時選取優惠方案
- 個人化應用程式內卡，為使用者的生命週期階段提供最佳獎勵
- 跨頻道優惠方案一致性 — 相同的決策邏輯提供電子郵件、Web和推播，讓客戶看到統一的優惠方案體驗
- 根據客戶價值層級選擇動態優惠券或折扣（例如，高價值客戶會獲得優惠方案）
- 根據目前訂閱層級的產品升級或追加銷售選件選擇
- 根據層級和活動記錄的熟客獎勵優惠個人化

## 關鍵績效指標

下列KPI有助於評估Offer Decisioning實作的成效。

| KPI | 說明 | 測量方法 |
| --- | --- | --- |
| 優惠接受率 | 導致點選、贖回或轉換的已傳遞優惠方案的百分比 | 優惠點按或贖回/已傳遞的優惠總數 |
| 優惠選擇分佈 | 在所有決定中選取的每個優惠比例 | 每個優惠計數/呈現的決策總數 |
| 遞補率 | 未符合個人化優惠條件且未提供遞補優惠的決策百分比 | 遞補曝光次數/決定總數 |
| 轉換率 | 完成所需動作（購買、註冊、贖回）的優惠方案收件者百分比 | 轉換/選件曝光次數 |
| 遞增收入 | 歸因於決策所選優惠與控制組或遞補優惠的收入 | 個人化優惠方案收入 — 遞補/控制項收入 |
| 跨管道一致性分數 | 在定義的視窗內，跨多個管道接收相同優惠的個人檔案百分比 | 一致優惠/多頻道曝光總數 |
| 優惠點進率 | 導致點按的優惠方案曝光百分比 | 優惠點按數/優惠閱聽 |

## 使用案例模式

本節說明Offer Decisioning的函式鏈和模式定義。

**Offer Decisioning**

使用集中式決定邏輯，跨管道為設定檔選取次優優惠或內容。

**功能鏈：**&#x200B;對象評估>優惠資格>排名策略>決定執行>傳遞>報告

請參閱[實作選項](#implementation-options)一節，瞭解每個構成的具體形式。

## 應用程式

在此使用案例模式中使用以下Adobe應用程式。

- **[!DNL Adobe Journey Optimizer] (AJO)** — 優惠方案建立、適用性規則、排名策略、位置和決定政策的決定管理引擎；優惠方案傳遞的頻道設定和訊息編寫；行銷活動和歷程執行
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** — 優惠方案適用性區段的對象評估；適用性和排名中使用的設定檔資料和計算屬性
- **[!DNL Adobe Experience Platform] (AEP)** — 支援AJO和RT-CDP的統一設定檔存放區、身分解析和資料基礎

## 基礎函式

下列基本功能必須為此使用案例模式準備就緒。 對於每個函式，狀態會指出它通常是必要的、假設為預先設定或不適用。

| 基礎函式 | 狀態 | 必須準備就緒的專案 | Experience League參考 |
| --- | --- | --- | --- |
| 管理與治理 | 已假設就位 | 已啟用決策許可權的AJO沙箱。 指派給實作團隊的優惠方案管理角色（決定管理員、優惠方案核准者）。 | [沙箱總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sandbox/home)，[存取控制總覽](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| 資料模型與準備 | 必填 | 設定檔結構描述必須包含用於優惠方案適用性規則的屬性（例如，忠誠度等級、購買記錄、訂閱型別）。 追蹤優惠閱聽、點按和轉換的優惠回應/互動結構描述應已準備就緒。 | [XDM系統總覽](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)，[結構描述組合基本概念](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| 資料來源與收集 | 已假設就位 | 適用性規則中使用的設定檔屬性必須是最新的。 針對網頁傳送（選項B），網頁SDK的實作必須在資料流上啟用AJO服務。 對於電子郵件傳遞，設定檔屬性在傳送時必須是可解析的。 | [網頁SDK概觀](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)，[設定資料串流](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure) |
| 身分和設定檔設定 | 已假設就位 | 設定檔必須可跨所有提供優惠的管道解析。 為了跨管道選件一致性，統一的身分至關重要 — 相同的設定檔必須在電子郵件、網頁和行動內容中識別。 即時網路/應用程式傳遞需要邊緣主動合併原則。 | [身分識別服務總覽](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)，[合併原則總覽](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview) |
| 對象定義與細分 | 必填 | 用作優惠適用性標準的對象必須定義和評估（例如「高價值客戶」、「試用使用者」、「忠誠金級」）。 評估方法必須符合傳遞延遲 — 即時網頁/應用程式的邊緣評估、電子郵件促銷活動的批次或串流。 | [區段服務總覽](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)，[區段產生器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder) |

## 支援功能

以下功能可擴大此使用案例模式，但不是核心執行的必要功能。

| 支援功能 | 狀態 | 為什麼這很重要 | Experience League參考 |
| --- | --- | --- | --- |
| 計算/衍生屬性建立 | 推薦 | Customer AI傾向分數、期限值計算和參與量度可大幅改善排名策略的成效。 計算屬性（例如「上次購買間隔天數」或「90天總支出」）可啟用更精確的適用性規則和公式型排名。 | [計算屬性總覽](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)，[Customer AI總覽](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview) |
| 資料生命週期管理 | 推薦 | 優惠歷史記錄和決定事件資料會隨著時間累積。 保留原則（有效期）應設定為優惠互動事件資料集，以管理儲存空間並符合資料保留要求。 | [進階資料生命週期管理概觀](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)，[資料集有效期](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/ui/dataset-expiration) |
| 資料使用標籤和實作 | 推薦 | 治理標籤可確保具備敏感目標定位條件（例如財務狀態、健康狀況）的選件符合資料使用原則。 適用性規則中所使用欄位的標籤可防止不相容的優惠方案目標定位。 | [資料控管概觀](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)，[資料使用標籤概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/labels/overview) |
| 監控與可觀察性 | 推薦 | 應監控決策引擎效能、遞補率和選件傳遞健康狀況。 高遞補率的警報可能表示適用性規則設定錯誤或資料時效性問題。 | [警示概述](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)，[可觀察性深入分析概述](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| 報告與分析 | 已包含 | 選件效能報表是功能鏈（階段7）的一部分。 CJA分析可啟用跨管道優惠效果測量、收入影響歸因和最佳化機會識別。 | [CJA概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)，[Analysis Workspace概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home) |

## 應用程式函式

此計畫會從「應用程式功能目錄」中執行下列功能。 函式會對應至實作階段，而非編號步驟。

### [!DNL Journey Optimizer] (AJO)

下表列出AJO函式及其設定所在的實作階段。

| 函式 | 實作階段 | 說明 |
| --- | --- | --- |
| 決策 | 階段3：決策設定 | 建立優惠專案、定義適用性規則、設定排名策略、建立遞補優惠、定義刊登版位及建立決定政策 |
| 通道設定 | 階段4：通道與表面組態 | 設定電子郵件、網頁、應用程式內或程式碼型頻道介面，用於選件傳送 |
| 訊息製作 | 階段5：內容與傳遞設定 | 使用選件版位區域設計訊息範本；設定Web/應用程式傳送的程式碼型體驗 |
| 行銷活動執行 | 階段5：內容與傳遞設定 | 執行排程或API觸發的行銷活動，以叫用決定政策（選項A） |
| 內容實驗 | 階段5：內容與傳遞設定 | 可選擇使用A/B測試不同的排名策略或提供創意變體 |
| 報告與效能分析 | 第7階段：報告與效能監視 | 監視選件選擇分佈、接受率、遞補率和通路層級效能 |

### [!DNL Real-Time CDP] (RT-CDP)

下表列出RT-CDP函式及其設定所在的實作階段。

| 函式 | 實作階段 | 說明 |
| --- | --- | --- |
| 對象評估 | 第2階段：對象評估 | 定義並評估用於優惠方案適用性規則的對象；選取適當的評估方法（批次、串流或邊緣） |
| 輪廓富集 | 階段1 （支援）：計算屬性 | 使用計算的屬性和傾向分數豐富設定檔，以改善排名策略有效性 |

## 先決條件

開始實作之前，請先完成下列必要條件。

- [ 已啟用決定管理功能的]個AJO沙箱
- [ ]個具有決定管理許可權的使用者角色（建立/編輯優惠、位置、決定）
- [ ]設定檔結構描述包含優惠資格所需的屬性（例如，忠誠度等級、客戶區段、訂閱等級）
- [ ]設定檔資料為最新資料且已主動擷取，以取得適用性屬性新鮮度
- [ 選項A （電子郵件）的]：電子郵件通道表面已設定驗證的子網域和已預熱的IP集區
- [ 選項B （網頁/應用程式）的]：已在資料流上啟用AJO服務的情況下實作網頁SDK；已設定Edge-active合併原則
- [ 選項C （歷程）的]：歷程畫布許可權，以及至少設定一個歷程進入事件或對象
- [ ]針對每個優惠方案和版位組合準備的優惠方案創意資產（影像、復本、CTA）
- [ ]針對每個版位準備的遞補優惠內容
- [ 在RT-CDP中定義和評估的優惠方案適用性規則的]個對象

## 實作選項

本節說明Offer Decisioning的可用實作選項。 每個選項會提供不同的傳送通道和使用案例內容。

### 選項A：電子郵件Offer Decisioning

此選項最適合選取要包含在傳出電子郵件行銷活動的最佳優惠方案 — 促銷電子郵件、電子報個人化、生命週期電子郵件與動態優惠方案內容。 決定是在每個收件者的訊息轉譯時做出。

#### 運作方式

在電子郵件訊息呈現期間會叫用決定原則，以選取適合每個收件者的最佳優惠方案。 電子郵件範本包括優惠方案版位區域，決策引擎會在此插入所選優惠方案的內容表示（影像、HTML或文字）。 在傳送時，引擎會根據優惠方案適用性規則評估每個收件者的設定檔、套用排名策略，並將成功優惠方案的內容內嵌至電子郵件。

此方法適用於已排程的行銷活動（在行銷活動執行時評估）和歷程內嵌電子郵件（在設定檔達到訊息動作節點時評估）。 優惠內容（影像、標題、正文和CTA）會根據決定結果依每個收件者進行個人化。

#### 主要考量事項

- 在傳送時，會使用設定檔的目前狀態來評估優惠方案適用性
- 批次對象評估已足夠，因為決策會在訊息轉譯期間發生
- 每個選件都需要有HTML或影像內容呈現方式才能放入電子郵件
- 每個使用的電子郵件位置都必須有遞補優惠的內容

#### 優點

- 最簡單的實施路徑 — 使用標準行銷活動或歷程電子郵件傳遞
- 沒有使用者端SDK需求
- 使用現有的電子郵件基礎架構和通道介面
- 透過批次行銷活動執行支援大量受眾

#### 限制

- 決策是在傳送時作出；無法適應傳送後行為
- 傳送電子郵件後，選件內容為靜態內容（無即時更新）
- 僅限於中心設定檔存放區（非邊緣）中可用的設定檔屬性

#### Experience League資源

- [在訊息中傳遞優惠方案](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [建立行銷活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)

### 選項B：網頁/應用程式即時優惠決定

此選項最適合用於網頁或行動應用程式上的即時優惠方案選擇 — 首頁促銷橫幅、帳戶儀表板優惠方案Widget、應用程式內優惠方案卡片，或任何在頁面載入或畫面呈現時應該選擇優惠方案的數位介面。

#### 運作方式

透過Edge Decisioning網路或程式碼型體驗，在頁面載入或應用程式畫面轉譯時叫用決定原則。 當訪客載入頁面時，Web SDK會傳送請求給Edge Network，其會根據優惠方案適用性規則和排名策略評估訪客的邊緣設定檔。 選取的選件會在回應中傳回，並在數位介面的設定位置中轉譯。

針對程式碼型體驗，應用程式會擷取決定回應，並使用自訂前端邏輯呈現選件內容。 針對Web Channel體驗，AJO Web Channel可使用視覺化或程式碼式撰寫將選件內容直接插入頁面。

#### 主要考量事項

- 需要在資料流上啟用AJO服務的Web SDK或行動SDK實作
- 即時設定檔查詢需要Edge作用中的合併原則
- 用於資格的對象必須支援邊緣評估（簡單屬性檢查和區段成員資格）
- 優惠內容表示應使用JSON或影像URL格式在使用者端轉譯
- 必須實作曝光追蹤來擷取選件檢視和點按次數

#### 優點

- 根據訪客目前的設定檔狀態，即時選取工作階段內的選件
- 透過Edge Network的次秒決策延遲
- 選件會根據邊緣可用的最新設定檔資料進行調整
- 透過內容實驗支援優惠方案策略的A/B測試

#### 限制

- 需要使用者端SDK實施（Web SDK或Mobile SDK）
- Edge設定檔有一個完整中心設定檔屬性的子集 — 複雜的適用性規則可能無法正確評估
- Edge區段有區段規則複雜性限制（無時間序列查詢）
- 需要前端開發，才能在程式碼型體驗中自訂轉譯

#### Experience League資源

- [使用Edge Decisioning API傳遞優惠方案](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/edge-decisioning-api)
- [程式碼型體驗管道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based-experience/get-started-code-based)

**這與「已知訪客」網頁/應用程式個人化選項B有何不同：**

基礎架構相同 — 兩者都會使用邊緣的AJO Decisioning搭配網頁SDK，以及邊緣主動合併原則。 不同之處在於目錄治理模式。 此選項會以適用性規則、上限計數器及有效日期來控制限定優惠方案目錄 — 當業務或法規限制決定可以顯示哪些優惠方案及其顯示頻率時，請使用此選項。[已知訪客的Web/應用程式個人化](known-visitor-web-app-personalization.md)選項B會使用區段成員資格或排名策略從內容專案選取，而不使用選件生命週期管理。 如果您的專案集很大、持續變更，且不需要上限或資格治理，請改用已知訪客選項B。

### 選項C：歷程決定節點

此選項最適合用於多步驟歷程中的優惠方案選擇 — 在客戶歷程的決策點選取最佳優惠方案，然後透過下一個動作節點傳送。 當優惠決定是包含等待、條件和多個訊息動作的更廣泛協調流程的一部分時，請使用此選項。

#### 運作方式

從AJO歷程畫布中的決定節點叫用決定原則。 當設定檔達到決定節點時，引擎會評估優惠資格和等級，以選取最佳優惠。 選取的選件會通知下一個訊息動作，其中包括選件內容、要使用的頻道，或根據選件結果採取哪個歷程分支。

此方法會啟用最適化歷程，其中優惠決定會影響後續歷程步驟。 例如，歷程可能選取最佳選件、透過電子郵件傳送、等待參與，如果沒有開啟選件，則接著使用推播通知進行追蹤。

#### 主要考量事項

- 歷程必須設計為決策節點，後面接著一或多個訊息動作節點
- 在設定檔到達決定節點時，使用設定檔的狀態來評估優惠資格
- 決策和傳送之間的歷程等待步驟可能會導致設定檔狀態變更
- 可與歷程分支結合，根據選取的選件採取不同路徑

#### 優點

- 將優惠方案選擇整合至多步驟協調流程
- 啟用最適化歷程，其中選件選擇會影響後續步驟
- 支援相同歷程中的跨管道傳送（電子郵件、推播、簡訊）
- 可結合歷程條件以進行優惠方案後參與追蹤

#### 限制

- 設定比獨立行銷活動決策更複雜
- 套用歷程輸送量限制（每秒進入率5,000個設定檔）
- 決策繫結至歷程內容 — 變更需要歷程版本設定
- 必須重新發佈歷程，優惠目錄或決定原則更新才能生效

#### Experience League資源

- [在訊息中傳遞優惠方案](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [開始使用歷程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)

### 選項比較

下表比較各個關鍵條件的三個實作選項。

| 條件 | 選項A：電子郵件決策 | 選項B：網頁/應用程式即時 | 選項C：歷程決定節點 |
| --- | --- | --- | --- |
| 最適合 | 包含每個收件者優惠方案選擇的批次電子郵件行銷活動 | 網頁/應用程式表面的即時優惠橫幅 | 多步驟協調歷程中的優惠方案選擇 |
| 決定延遲 | 在傳送時間（批次轉譯期間每個收件者的秒數） | 次秒(Edge Network) | 在歷程節點執行時（秒） |
| 頻道 | 電子郵件 | 網頁、行動應用程式、程式碼型表面 | 歷程中的任何管道（電子郵件、推播、簡訊） |
| 需要SDK | 否 | 是（網頁SDK或行動SDK） | 否（適用於電子郵件/推播）；是（如果Web頻道是歷程動作） |
| 對象評估 | 批次或串流 | Edge | 批次、串流或邊緣（取決於歷程專案） |
| 設定檔資料範圍 | 完整中心設定檔 | Edge設定檔（子集） | 完整中心設定檔 |
| 複雜性 | 低 | Medium — 高 | 中 |
| 輸送量 | 高（批次行銷活動數量） | 高（Edge Network規模） | Medium （適用歷程輸送量限制） |

### 選擇正確的選項

使用下列指引，為您的使用案例選取最佳實作選項。

- **如果主要使用案例是在傳出電子郵件行銷活動中選取每位收件者的最佳優惠方案，而且沒有使用者端SDK可用，則選擇選項A**。 這是最簡單的實作方法，非常適用於促銷電子郵件、電子報和生命週期行銷活動。
- **如果訪客載入網頁或開啟行動應用程式時必須即時選取選件，請選擇選項B**。 這需要Web SDK或Mobile SDK以及邊緣主動式合併原則，但可提供最快、最情境式的選件選擇。
- **如果優惠決定是包含多個步驟、等待和條件式分支的更廣泛客戶歷程的一部分，請選擇選項C**。 當選取的優惠方案應影響下游歷程動作，或需要根據優惠方案參與的多通道後續追蹤時，這是正確的選擇。
- **合併選項** （選件必須跨管道一致傳遞）。 對全部三個選項使用相同的決定政策，以確保客戶在電子郵件（選項A）、網站（選項B）和歷程追蹤（選項C）中看到相同優惠。

## 實作階段

以下階段概述Offer Decisioning的端對端實作順序。

### 階段1：驗證基本必要條件

**應用程式函式：** AEP：資料模型化和準備、AEP：身分和設定檔組態

此階段會驗證基礎資料層是否支援Offer Decisioning。 設定檔結構描述必須包含優惠適用性規則中使用的屬性，身分設定必須啟用跨頻道設定檔解析。

#### 決定：適用性的設定檔屬性

決定要在優惠適用性規則中使用的設定檔屬性。

>[!NOTE]
>設定檔屬性的選擇會同時影響適用性規則設計和排名策略的有效性。 考慮計算的屬性和傾向分數以增強決策品質。

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 標準設定檔屬性（忠誠度等級、購買記錄） | 屬性已存在於設定檔結構描述中 | 不需要變更結構描述；驗證資料的時效性 |
| 計算的屬性（期限值、參與分數） | 適用性或排名取決於彙總的行為資料 | 需要S1設定；新增計算屬性重新整理步調的相依性 |
| Customer AI傾向分數 | 排名應運用ML型預測 | 需要足夠的訓練資料（超過10,000個設定檔與目標事件）；模型訓練時間 |

#### 關鍵設定詳細資料

- 驗證設定檔結構描述包含適用性規則中參考的欄位（例如，`_tenantId.loyaltyTier`、`_tenantId.subscriptionType`）
- 確認曝光、點選和轉換事件存在優惠互動追蹤結構
- 選項B：驗證是否已設定邊緣作用中合併原則，以及Web SDK資料流是否已啟用AJO服務

#### Experience League檔案

- [XDM系統概覽](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [啟用設定檔的結構描述](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/union-schema)
- [合併原則概觀](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

### 第2階段：設定對象評估

**應用程式函式：** RT-CDP：對象評估

此階段會定義並評估當作優惠方案適用性條件使用的對象。 這些受眾會決定哪些客戶區段符合特定優惠方案的資格（例如「高價值客戶」符合進階優惠方案的資格，「試用使用者」符合轉換優惠方案的資格）。

#### 決定：對象評估方法

決定對象會籍必須多久更新一次優惠資格。

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 批次評估 | 選項A （電子郵件行銷活動），在傳送時評估適用性 | 最簡單；支援所有區段規則運算式；每日或隨選重新整理 |
| 串流評估 | 若批次之間需要近乎即時的對象更新，則為選項A或C | 適用於合格區段的自動；有限的區段規則支援（單一事件、屬性比較） |
| 邊緣評估 | 選項B （Web/應用程式即時），其中資格必須在頁面載入時進行評估 | 次秒；即時Web/應用程式選件需要；僅限於簡單屬性檢查和區段會籍 |

**UI導覽：**&#x200B;客戶>對象>建立對象>建置規則

#### 關鍵設定詳細資料

- 定義優惠資格（例如「忠誠金級客戶」、「高價值客戶」、「試用使用者」）的目標對象
- 視需要定義隱藏對象（例如「最近收到的選件X」）
- 對於選項B：驗證資格對象是否符合邊緣評估的資格 — 避免時間序列查詢和區段規則運算式中的複雜彙總

#### 選項差異之處

選項A （電子郵件決策）的&#x200B;**：**
批次或串流評估就足夠了。 在行銷活動執行之前或期間評估對象。 完全支援複雜區段規則運算式，包括以時間為基礎的條件和事件彙總。

選項B的&#x200B;**（Web/應用程式即時）：**
需要Edge評估。 對象必須使用簡單的屬性檢查或區段成員資格條件。 驗證區段規則運算式符合邊緣細分資格，以測試邊緣適用性。

選項C （歷程決定節點）的&#x200B;**：**
任何評估方法的運作都取決於歷程進入條件。 如果歷程使用以受眾為基礎的專案，則受眾評估方法與歷程的需求相符。

#### Experience League檔案

- [Segmentation Service概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [區段產生器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [串流區段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [邊緣分段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)

### 階段3：設定決策

**應用程式函式：** AJO：決策

這是建立優惠方案目錄、適用性規則、排名策略和決定政策的核心階段。 此階段會建立所有傳送選項(A、B、C)共用的決定引擎設定。

#### 決定：刊登頻道和內容格式

決定選件出現的位置及格式。

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 電子郵件(HTML) | 選項A — 在電子郵件內文中呈現為HTML的優惠方案內容 | 支援豐富格式；必須與電子郵件使用者端相容 |
| 電子郵件（影像URL） | 選項A — 在電子郵件中呈現為託管影像的選件 | 更簡單；影像必須可託管和存取；無動態文字 |
| 網頁(HTML) | 選項B — 在網頁上呈現為HTML的優惠 | 完整版面控制項；支援互動式元素 |
| 網頁/行動(JSON) | 選項B — 針對自訂轉譯而以JSON傳回的選件資料 | 最大彈性；需要前端開發才能呈現 |
| 程式碼型(JSON) | 選項B — 提供程式碼型體驗表面的資料 | 應用程式控制項呈現；最具彈性 |

#### 決定：排名策略

決定應如何從符合資格的優惠方案中選擇最佳優惠方案。

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 優先順序（手動） | 小型優惠方案目錄；明確的業務規則以訂購優惠方案 | 設定最簡單；手動指派每個選件的優先順序值；確定性 |
| 以公式為基礎（自訂運算式） | 排名應考慮設定檔屬性（例如，忠誠度等級、造訪間隔） | 彈性；使用設定檔資料來計算排名分數；需要區段規則運算式設計 |
| AI排名（自動最佳化） | 大型優惠方案目錄；希望ML能隨著時間最佳化選擇 | 模型訓練需要至少1,000個轉換事件；從選件效能資料學習 |

#### 決定：優惠上限

決定是否應限制優惠的顯示次數。

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 每個設定檔上限 | 避免向單一客戶顯示相同優惠太多次 | 避免選件疲勞；在高輸送量的情況下，計數器會延遲幾秒鐘 |
| 全域上限 | 限制所有設定檔中的優惠方案總曝光數（例如，有限詳細目錄） | 控制優惠供應；達到上限後，決定就會排除優惠 |
| 無上限 | 優惠方案的可用性無限制 | 最簡單；適用於永遠啟動的促銷活動 |

**UI導覽：**&#x200B;元件>決定管理>位置/規則/優惠/決定

#### 關鍵設定詳細資料

1. **建立版位** — 指定每個版位的頻道型別和內容格式，以定義優惠出現的位置。
   - UI：元件>決定管理>版位
   - 為每個管道/格式組合建立一個版位（例如「電子郵件主圖橫幅 — HTML」、「網頁首頁 — JSON」、「行動應用程式卡片 — JSON」）

2. **定義適用性規則** — 使用參考設定檔屬性或對象成員資格的區段規則運算式建立規則。
   - UI：元件>決定管理>規則
   - 規則可參考對象會籍、設定檔屬性（忠誠度等級、訂閱型別）、日期限制或內容資料

3. **建立個人化優惠方案** — 為每個位置建立包含內容表示的每個優惠方案、指派適用性規則、設定優先順序及設定選擇性上限。
   - UI：元件>決定管理>優惠>建立優惠
   - 每個優惠方案都需要每個版位的內容表示（例如電子郵件需要HTML，網頁需要使用JSON）
   - 指派適用性規則，以控制哪些設定檔可以檢視每個優惠方案
   - 設定優惠方案有效日期（開始/結束）和選用的頻率上限
   - 核准每個優惠方案，以使其符合決策資格

4. **建立遞補優惠** — 為符合個人化優惠資格的每個版位建立預設優惠。
   - UI：元件>決定管理>優惠>建立遞補優惠
   - 遞補必須有表示用於決定中的每個位置

5. **建立集合限定詞和集合** — 使用限定詞標籤將優惠方案組織成集合。
   - UI：元件>決定管理>收集限定元
   - 用於決定範圍的群組相關優惠方案（例如「夏季促銷活動」、「忠誠度獎勵」）

6. **建立決定原則** — 將位置、集合、排名策略和遞補優惠繫結到可執行的決定。
   - UI：元件>決定管理>決定>建立決定
   - 每個決定範圍會將位置連結至集合，並指定排名方法

#### Experience League檔案

- [決策管理概觀](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [建立產品建議放置環境](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [建立決定規則](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [建立個人化優惠方案](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [建立後備產品建議](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [建立集合](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [建立集合限定詞](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-tags)
- [建立決定](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [排名策略](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### 階段4：設定通道和介面

**應用程式函式：** AJO：頻道設定

此階段會設定傳遞優惠的通道介面。 此設定取決於使用的實作選項。

#### 決定：頻道型別

決定使用案例所需的傳訊頻道。

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 電子郵件 | 包含電子郵件傳遞的選項A或選項C | 需要子網域委派、IP集區、寄件者設定 |
| Web | 網頁表面傳遞的選項B | 需要網站SDK和資料流設定 |
| 應用程式內 | 行動應用程式傳送的選項B | 需要Mobile SDK和推送憑證 |
| 程式碼型體驗 | 自訂彩現表面的選項B | 最具彈性；應用程式可處理轉譯 |

#### 選項差異之處

選項A （電子郵件決策）的&#x200B;**：**
- UI：管理>管道>管道表面>建立表面（電子郵件）
- 設定子網域、IP集區、寄件者姓名/電子郵件、回覆、取消訂閱設定
- 驗證傳送子網域的SPF、DKIM和DMARC記錄

選項B的&#x200B;**（Web/應用程式即時）：**
- UI：管理>管道>管道表面>建立表面（網頁或應用程式內）
- 針對Web：設定網頁表面URL模式
- 對於程式碼型體驗：定義應用程式的表面URI
- 驗證資料流是否已啟用AJO服務

選項C （歷程決定節點）的&#x200B;**：**
- 為歷程中使用的每個管道設定管道表面（電子郵件、推播、簡訊或網頁）
- 每個歷程訊息動作都需要對應的作用中頻道介面

#### Experience League檔案

- [開始使用電子郵件設定](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [電子郵件表面設定](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [委派子網域](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [設定推播通知頻道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### 階段5：設定內容與傳送

**應用程式函式：** AJO：訊息製作、AJO：行銷活動執行

此階段會設計訊息範本或體驗介面以顯示選取的選件，然後設定傳送機制（行銷活動、歷程或程式碼型體驗）。

#### 決定：優惠呈現的內容方法

決定應如何將選件內容整合至訊息或體驗。

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 電子郵件Designer中的優惠決定元件 | 選項A — 在電子郵件範本中內嵌優惠方案位置 | 拖放；優惠方案內容會根據決定結果自動呈現 |
| 使用決策原則的程式碼型體驗 | 選項B — 應用程式擷取並轉譯選件資料 | 對演算進行最大程度的控制；需要前端開發 |
| 包含內嵌決策的歷程訊息動作 | 選項C — 決定節點摘要提供歷程訊息的內容 | 選件選取和傳送是在歷程流程中協調 |

#### 決定：促銷活動型別（僅限選項A）

判斷這是已排程的行銷活動還是API觸發的行銷活動。

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 排程的行銷活動 | 一次性或循環批次傳送至已定義的對象 | 在執行時間評估的對象；設定日期/時間或週期 |
| API觸發的行銷活動 | 事件導向或系統觸發的傳送至指定的設定檔 | 在觸發裝載中指定的設定檔；每個請求支援最多20個收件者 |

#### 選項差異之處

選項A （電子郵件決策）的&#x200B;**：**

1. 使用電子郵件Designer編寫電子郵件訊息
   - UI：行銷活動>建立行銷活動>選取電子郵件>編輯內容
   - 將優惠決定元件插入電子郵件版面配置以定義版位區域
   - 為設定檔層級內容新增個人化權杖（名稱、忠誠度層級）
   - 使用選用的個人化設定主旨行和前置標題
2. 建立及設定行銷活動
   - UI：行銷活動>建立行銷活動>排程或API觸發
   - 繫結目標對象並選取頻道介面
   - 設定執行排程或API觸發程式設定
   - 檢閱及啟動行銷活動

選項B的&#x200B;**（Web/應用程式即時）：**

1. 設定程式碼型體驗或Web Channel
   - UI：行銷活動>建立行銷活動>程式碼型體驗（或網頁）
   - 將決定原則連結至體驗表面
   - 定義轉譯格式（程式碼型的JSON回應；Web Channel的視覺化編輯器）
2. 實作使用者端轉譯
   - 使用Web SDK `sendEvent`回應來擷取選取的選件
   - 在頁面的指定位置中轉譯選件內容
   - 實作曝光和點選追蹤

選項C （歷程決定節點）的&#x200B;**：**

1. 使用決定節點設計歷程
   - UI：歷程>建立歷程>新增決定節點
   - 設定決定節點以叫用階段3的決定原則
2. 在決定後新增訊息動作節點
   - 設定參考所選選件的電子郵件、推播或簡訊動作
   - 根據優惠方案參與新增等待步驟、條件或分支
3. 發佈歷程

#### Experience League檔案

- [在訊息中傳遞優惠方案](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [設計電子郵件內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [新增個人化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [建立行銷活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [開始使用歷程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [預覽和測試您的內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### 第6階段：測試與驗證

**應用程式功能：** AJO：決策、AJO：訊息製作

此階段會驗證決定引擎是否傳回測試設定檔的正確選件，以及選件內容是否會在每個傳遞管道中正確呈現。

#### 測試決策邏輯

使用具有已知屬性的測試設定檔，以確認根據資格和排名選取了正確的優惠。

- 建立符合不同資格條件（例如，Gold級、Silver級、試用使用者）的測試設定檔
- 驗證每個測試設定檔都會收到預期選件
- 確認符合資格規則的設定檔不會收到遞補優惠

#### 測試內容呈現

預覽每個傳遞管道中的優惠方案內容。

- 選項A：搭配測試設定檔使用電子郵件預覽，驗證選件內容是否正確呈現
- 選項B：在中繼環境中測試Edge決策回應
- 選項C：使用歷程測試模式，驗證決定節點是否正確選取

#### 驗證曝光追蹤

確認正在追蹤優惠閱聽、點按和轉換。

- 驗證追蹤資料集中是否顯示優惠方案互動事件
- 確認優惠閱聽和下游轉換之間的歸因

#### Experience League檔案

- [預覽和測試您的內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)
- [傳送電子郵件校樣](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/proofs)

### 階段7：設定報告和效能監視

**應用程式函式：** AJO：報表與效能分析

此階段設定報告以追蹤優惠方案選擇分佈、接受率、轉換影響和遞補率。 此階段涵蓋AJO原生報表和CJA型跨管道分析。

#### 決定：報告方法

決定選件效能分析所需的報表工具。

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 僅限AJO原生報表 | 對個別行銷活動或歷程的營運監控 | 快速存取；內建交付和參與量度；有限的跨實體分析 |
| CJA工作區分析 | 跨管道優惠方案成效、收入歸因、funnel分析 | 需要CJA連線和資料檢視；更深入的分析功能 |
| AJO和CJA | 完整的營運與分析涵蓋範圍 | 建議用於生產實作；AJO用於即時監控，CJA用於策略分析 |

#### 關鍵設定詳細資料

1. **AJO原生報告** — 使用內建報告監視行銷活動或歷程績效。
   - UI：行銷活動>選取行銷活動>所有時間報表（或即時報表）
   - 檢閱選件特定量度：每個選件的曝光數、每個選件的點進率、遞補率
   - 監視傳送funnel：已鎖定目標>已傳送>已傳送>已傳送>開啟>點按

2. **CJA analysis （建議）** — 建置跨管道優惠方案效能儀表板。
   - 設定CJA連線，包括AJO選件互動資料集
   - 使用優惠方案特定的維度（優惠方案名稱、位置、決定）和量度（曝光數、點按數、轉換），建立資料檢視
   - 建立工作區分析：選件選擇分佈、依區段的接受率、收入影響、跨管道選件一致性

#### Experience League檔案

- [行銷活動全域報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [歷程全域報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [使用Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Analysis Workspace概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)

## 實施考量

本節涵蓋Offer Decisioning實施的護欄、常見陷阱、最佳實務和取捨決策。

### 護欄和限制

規劃實施時，請注意下列平台護欄和限制。

- 每個沙箱最多10,000個核准的個人化優惠 — [決定管理護欄](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- 每個決定最多30個位置
- 每個決定請求最多30個集合範圍
- AI排名模型需要至少1,000個轉換事件才能訓練
- 在高輸送量的情況下，選件上限計數器可能會延遲數秒
- Edge決定僅限於邊緣設定檔存放區中可用的設定檔屬性
- 每個沙箱最多4,000個區段定義 — [平台護欄](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- 每個沙箱在Edge上只能有一個作用中的合併原則
- 每個沙箱最多500個使用中的即時行銷活動
- 歷程進入率限制：每秒5,000個設定檔
- 每個沙箱每個管道型別最多10個管道表面

### 常見陷阱

避免實施期間經常遇到這些問題。

- **決定一律會傳回遞補優惠：**&#x200B;這通常表示個人化優惠未核准、超出其有效日期範圍，或適用性規則不符合測試設定檔的屬性。 驗證每個條件：核准狀態、日期範圍和區段規則運算式準確性。 同時檢查是否未達到上限限制。
- **選件未出現在集合中：**&#x200B;請確定已使用正確的集合限定詞標籤選件，且集合篩選條件相符。 優惠方案必須同時經過標籤和核准，才能顯示在集合型決定範圍中。
- **未套用排名公式：**&#x200B;請確認公式語法有效，並參考可存取的設定檔屬性。 公式錯誤會自動回復到以優先順序為基礎的排名，而不會出現明顯錯誤。
- **Edge傳遞傳回空白的個人化：**&#x200B;請確定資料串流已設定為啟用[!DNL Adobe Journey Optimizer]服務，且決定範圍的格式正確。 驗證邊緣作用中合併原則是否存在。
- **跨管道的優惠方案不一致：**&#x200B;如果每個管道使用不同的決定原則，相同的設定檔可能會收到不同的優惠方案。 使用跨管道的單一決策原則來維持一致性，或根據管道特定的位置接受故意的分歧。
- **未在電子郵件中呈現的優惠方案內容：**&#x200B;請確認優惠方案的內容表示符合電子郵件版位格式（HTML或影像URL）。 缺少表示會導致空白放置區域。

### 最佳實務

若要成功實作Offer Decisioning，請遵循下列建議。

- **從小型優惠方案目錄開始並反複運算** — 從5到10個優惠方案開始，並在決策架構通過驗證時展開。 這可簡化疑難排解，並確保適用性規則在縮放之前正常運作。
- **策略性地使用集合限定詞** — 依類別標籤優惠方案（例如「贏取」、「保留」、「向上銷售」），以啟用可跨行銷活動和歷程重複使用的彈性集合型決定範圍。
- **一律建立有意義的遞補優惠** — 遞補優惠不僅是一個安全網；對不符合任何適用性規則的設定檔，它們也是預設體驗。 投資於提供價值的遞補內容，即使沒有個人化。
- **儘可能設計互斥的適用性規則** — 當多個優惠方案具有重疊的適用性時，排名策略就變得至關重要。 如果業務需求為特定區段指定特定優惠方案，請將適用性規則設為互斥，而非僅依賴排名。
- **使用選項B**&#x200B;的邊緣代表設定檔進行測試 — Edge設定檔包含中心設定檔屬性的子集。 使用具有邊緣可用屬性的設定檔進行測試，以確保資格在生產環境中正確評估。
- **將遞補率監視為健康狀態量度** — 高遞補率（超過20-30%）表示優惠方案目錄未涵蓋足夠的客戶區段。 展開優惠方案目錄或擴大適用性規則。
- **版本決定原則而非編輯即時原則** — 建立新的決定原則版本，而非修改使用中的決定原則版本。 這可以防止即時行銷活動的中斷，並可進行決策策略的A/B比較。

### 權衡決定

在做出架構和設定決策時，請考慮以下取捨。

#### 適用性精確度與優惠方案涵蓋範圍

嚴格的適用性規則可確保每個選件僅能觸及最相關的設定檔，但如果設定檔與任何選件不符，則可能會導致高遞補率。 廣泛的適用性規則可最大化優惠方案涵蓋範圍，但降低個人化精確度。

- **適用性偏好：**&#x200B;接受率較高、個人化較好、優惠疲勞程度較低
- **廣泛的適用性優惠：**&#x200B;較低的遞補率、更多設定檔會收到個人化優惠、更簡單的規則管理
- **建議：**&#x200B;從較廣泛的適用性規則開始，並根據績效資料加以收緊。 監控遞補率與接受率，以找出適當的平衡。 使用排名策略來區分廣泛符合資格的優惠。

#### 以優先順序為準vs. AI排名的排名

優先順序排名可讓企業完全控制要顯示哪些優惠方案，而AI排名排名可針對轉換最佳化，但會減少人為控制優惠方案選擇的方式。

- **優先順序型優惠：**&#x200B;業務控制、可預測性、不需要訓練資料、立即部署
- **AI排名優惠：**&#x200B;轉換最佳化、發現未預期的模式、自動適應不斷變化的客戶行為
- **建議：**&#x200B;針對初始啟動使用優先順序排名，並在業務控制最優先的情況下，使用法規敏感的優惠方案。 一旦足夠的轉換資料（1,000個以上的事件）可供使用，即可轉換至AI排名，用於大容量、效能最佳化的使用案例。

#### 單一決定原則與每個管道決定原則的比較

單一決策原則可確保所有管道之間的優惠一致性，但限制每個管道的最佳化。 每個管道政策允許管道特定的排名和資格，但可能會帶來客戶體驗不一致的風險。

- **單一原則的優點：**&#x200B;跨管道一致性、更簡單的管理、統一的報告
- **每個管道原則傾向於：**&#x200B;管道最佳化排名、管道特定資格（例如，僅限網頁的優惠）、獨立反複專案
- **建議：**&#x200B;從跨管道一致性的單一決定原則開始。 只有在業務需求需要通道特定的優惠策略（例如Web專屬快閃銷售）時，才建立每個通道的原則。

#### 中心決策（選項A/C）與邊緣決策（選項B）的比較

中心決策可存取完整設定檔，但會在傳送時運作。 Edge Decisioning會即時運作，延遲時間不到一秒，但僅限於邊緣可用的設定檔屬性。

- **中心決策偏好：**&#x200B;存取完整的設定檔資料、複雜的適用性規則、批次行銷活動數量
- **Edge決策偏好：**&#x200B;即時內容、工作階段中個人化、次秒回應
- **建議：**&#x200B;針對完整設定檔資料可改善選件相關性的傳出頻道（電子郵件、推播）使用中心決策。 對即時回應十分重要的傳入頻道（網頁、應用程式）使用邊緣決策。 確保邊緣的適用性規則僅使用邊緣可用的屬性。

## 相關文件

下列資源提供在此使用案例模式中使用的元件的其他詳細資料。

### 決策管理

- [決策管理概觀](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [建立產品建議放置環境](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [建立決定規則](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [建立個人化優惠方案](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [建立後備產品建議](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [建立集合](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [建立集合限定詞](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-tags)
- [建立決定](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [排名策略](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### 選件傳送

- [在訊息中傳遞優惠方案](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [使用Edge Decisioning API傳遞優惠方案](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/edge-decisioning-api)
- [使用Decisioning API傳遞優惠方案](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/decisioning-api)

### 管道設定

- [開始使用電子郵件設定](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [電子郵件表面設定](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [委派子網域](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [設定推播通知頻道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [設定簡訊頻道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)

### 訊息製作與個人化

- [設計電子郵件內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [新增個人化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization語法](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [動態內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [使用內容範本](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [預覽和測試您的內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### 行銷活動和歷程

- [開始使用行銷活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [建立行銷活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [開始使用歷程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)

### 內容實驗

- [開始使用內容實驗](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [建立內容實驗](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)

### 對象和細分

- [Segmentation Service概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [區段產生器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [串流區段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [邊緣分段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)

### 設定檔與身分

- [Identity Service總覽](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [合併原則概觀](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [計算屬性概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Customer AI概述](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview)

### 資料模式與收集

- [XDM系統概覽](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [網頁SDK概觀](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [設定資料串流](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)

### 報告與分析

- [行銷活動全域報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [歷程全域報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [使用Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [CJA概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Analysis Workspace概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)

### 資料控管和生命週期

- [資料控管概覽](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [資料使用標籤概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/labels/overview)
- [進階資料生命週期管理概觀](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)
- [Journey Optimizer中的同意](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)

### 護欄

- [Journey Optimizer護欄](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [即時客戶個人檔案護欄](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)

### 教學課程

- [決定管理API快速入門](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/getting-started)
