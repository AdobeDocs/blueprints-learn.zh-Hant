---
title: 已知訪客網頁/應用程式Personalization
description: 瞭解如何根據即時設定檔和區段會籍，將個人化內容、優惠或促銷活動傳遞給已識別的訪客。
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 585adc0e-f528-4a09-b931-ef6b45fa8ec8
source-git-commit: e8185f348f926acab2ca2e0c3cd55c08c663cf41
workflow-type: tm+mt
source-wordcount: '7968'
ht-degree: 2%

---

# 已知訪客的網頁/應用程式個人化

此參考計畫提供完整的實作指南，可讓您使用[!DNL Adobe Journey Optimizer] (AJO)和[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)，跨數位介面將個人化內容傳遞給已識別的訪客。 它專為需要瞭解所有可行實作方法、必須在每個階段作出的決定以及支援設定的Experience League檔案的解決方案架構師、行銷技術人員和實作工程師所設計。

已知訪客的網頁/應用程式個人化是已驗證數位體驗的主要個人化模式。 與只仰賴工作階段內行為訊號的匿名訪客個人化不同，此模式會利用完整的統一設定檔：歷史行為資料、區段會籍、忠誠度等級、購買歷史記錄、生命週期階段、運算屬性和傾向分數。 它支援跨網頁（透過AJO網路頻道）、行動應用程式內訊息和內容卡片的個人化。

本指南提供所有可行的實作選項（區段型、決定型和多介面）以及折衷方案、決定指引和[!DNL Adobe Experience League]檔案的參考資料。

## 使用案例概述

擁有已驗證數位屬性的組織（電子商務網站、銀行入口網站、訂閱服務、忠誠度計畫、行動應用程式）需要提供可反映每位客戶與品牌關係的個人化體驗。 當訪客登入或透過身分解析被識別時，平台可以存取其完整的統一設定檔，並根據其特定屬性、行為和偏好設定提供量身打造的內容。

此模式處理已識別訪客進入Web屬性或開啟行動應用程式的情況，系統必須根據即時設定檔資料和對象會籍，決定要顯示的最佳內容、選件或促銷活動。 個人化決策會在邊緣以毫秒為單位進行，啟用次秒內容傳送而不會出現可察覺的延遲。

此模式支援確定性個人化（其中特定內容對應至特定受眾區段）和動態決策（其中AJO決策會評估適用性規則和排名策略，以選取每個設定檔的最佳內容）。 它橫跨多個數位表面（網頁、行動應用程式內訊息和內容卡），實現客戶數位歷程中一致的個人化。

## 主要業務目標

此使用案例模式支援下列業務目標。

### 提供個人化的客戶體驗

根據個別偏好設定、行為和生命週期階段量身打造內容、選件和訊息。 如需詳細資訊，請參閱[提供個人化客戶體驗](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)。

**KPI：**&#x200B;參與度、轉換率、客戶滿意度(CSAT)

### 增加網站參與度

透過相關體驗，改善網站逗留時間、每個工作階段頁面數以及與網頁內容的互動。 如需詳細資訊，請參閱[增加網站參與度](../../business-objectives/acquisition-growth/increase-website-engagement.md)。

**KPI：**&#x200B;網頁逗留時間、參與度、轉換率

### 提高行動應用程式的參與度

透過個人化的應用程式內體驗，推動每日主動使用、功能採用和應用程式內轉換。

**KPI：**&#x200B;參與度、保留率、轉換率

## 戰術使用案例範例

以下是此模式的常見戰術實施：

- 依忠誠度等級或生命週期階段劃分的首頁主圖個人化 — 根據客戶是新客戶、活躍客戶、高風險客戶還是VIP客戶，顯示不同的主圖橫幅
- 根據購買歷史記錄的產品建議輪播 — 使用過去的購買資料和產品相似性分數來顯示相關的產品建議
- 依客戶細分的個人化促銷橫幅 — 針對高價值、高風險和新的客戶細分顯示不同的促銷活動
- 根據功能採用為行動使用者提供的應用程式內訊息 — 根據使用者的使用模式來引導使用者瞭解未充分利用的功能
- 在帳戶控制面板上具有個人化優惠的內容卡 — 根據客戶設定檔量身打造的持續、不允許的優惠
- 根據客戶層級顯示個人化定價或折扣 — 向熟客方案會員顯示層級特定定價或專屬折扣
- 根據擁有的產品的交叉銷售建議Widget — 根據目前的產品組合提出補充產品或服務的建議
- 根據興趣進行個人化導覽或內容排序 — 根據示範的偏好重新排序內容模組或導覽元素

## 關鍵績效指標

下列KPI有助於評估此使用案例模式的成效。

| KPI | 測量方法 | 基準指引 |
| --- | --- | --- |
| Personalization參與率 | 個人化內容元素的點選次數和互動除以曝光數 | 個人化內容的效能應比預設內容高20-50% |
| 轉換率提升 | 個人化體驗與控制/預設體驗的轉換率 | 目標比非個人化體驗提升10-30% |
| 點進率(CTR) | 個人化CTA、優惠和建議的點按次數除以曝光數 | 監視每個介面（網頁、應用程式內、內容卡）和每個區段 |
| 每次造訪帶來的收入 | 歸因於具有個人化體驗之工作階段的收入 | 比較個人化與非個人化訪客同類群組 |
| 內容卡互動率 | 與曝光數相關的內容卡點選數與關閉數 | 依卡片型別和對象區段追蹤 |
| 應用程式內訊息參與度 | 與曝光數相關的應用程式內訊息互動（CTA點選、解除） | 比較對象區段和訊息型別 |
| 頁面逗留時間 | 個人化內容與預設頁面平均逗留時間 | 個人化頁面應顯示增加的暫留時間 |
| 優惠接受率 | 導致轉換事件的決策選取優惠方案百分比 | 追蹤每個選件、每個位置和每個排名策略 |

## 使用案例模式

本節說明核心模式及其功能鏈。

**已知訪客的網頁/應用程式個人化**

根據跨網路、行動應用程式內和內容卡表面的即時設定檔和區段會籍，將個人化內容、優惠或促銷活動提供給已識別的訪客。

**功能鏈：**&#x200B;對象評估> Personalization Decisioning >表面/頻道設定>內容傳送>曝光追蹤>報告

## 應用程式

在此使用案例模式中使用以下應用程式。

- **[!DNL Adobe Journey Optimizer] (AJO)** — Web頻道設定、應用程式內頻道設定、內容卡片頻道設定、決策（優惠方案選擇和排名）、訊息製作（個人化內容建立）、行銷活動執行、內容實驗和報告
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** — 對象評估（邊緣、串流和批次）、透過Edge Network的即時設定檔查詢、使用運算屬性和傾向分數擴充設定檔
- **[!DNL Adobe Experience Platform] (AEP)** — 設定檔存放區、身分服務、Web SDK、行動SDK、資料流設定、邊緣網路傳遞

## 基礎函式

下列基本功能必須為此使用案例模式準備就緒。 對於每個函式，狀態會指出它通常是必要的、假設為預先設定或不適用。

| 基礎函式 | 狀態 | 必須準備就緒的專案 | Experience League參考 |
| --- | --- | --- | --- |
| 管理與治理 | 已假設就位 | 已設定Web管道、應用程式內管道和決策許可權的AJO沙箱。 布建了行銷人員和內容作者角色的使用者。 | [沙箱總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sandbox/home)，[存取控制總覽](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| 資料模型與準備 | 必填 | 設定檔結構描述必須包括用於個人化和分段的屬性（例如，忠誠度等級、購買記錄、產品興趣、生命週期階段）。 用於網頁/應用程式互動追蹤和轉換事件的體驗事件結構。 資料集已啟用[!DNL Real-Time Customer Profile]。 | [XDM系統總覽](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)，[結構描述組合基本概念](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| 資料來源與收集 | 必填 | 在Web屬性上實作的Web SDK，用於體驗傳送和曝光追蹤。 在行動應用程式上實施行動SDK，以進行應用程式內和內容卡傳送。 資料流已設定AJO服務並啟用Edge個人化。 邊緣可用於次秒個人化的即時設定檔資料。 | [網頁SDK概觀](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)，[行動SDK概觀](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)，[設定資料串流](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure) |
| 身分和設定檔設定 | 必填 | 已設定的已知身分名稱空間（CRM ID、電子郵件、已驗證的使用者ID）。 匿名與已驗證工作階段之間的身分拼接可運作，以順暢地從匿名轉換為已知訪客個人化。 使用`isActiveOnEdge: true`設定的Edge合併原則可在邊緣解析已驗證的設定檔。 | [身分識別服務總覽](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)，[合併原則總覽](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview) |
| 對象定義與細分 | 必填 | 使用設定檔屬性、行為資料和計算屬性定義的對象。 Edge或串流評估已啟用即時個人化資格。 用於區段型個人化的對象必須符合邊緣評估的資格。 | [細分服務總覽](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)，[Edge細分](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation) |

## 支援功能

以下功能可擴大此使用案例模式，但不是核心執行的必要功能。

| 支援功能 | 狀態 | 為什麼重要 | Experience League參考 |
| --- | --- | --- | --- |
| 計算/衍生屬性建立 | 推薦 | 運算屬性（例如[!DNL Customer AI]傾向分數、期限值、參與分數、產品相關性、上次購買間隔天數）可提供更豐富的對象定義和內容選擇訊號，大幅改善個人化品質。 | [計算屬性總覽](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)，[Customer AI總覽](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview) |
| 資料生命週期管理 | 推薦 | 設定檔和事件資料保留原則可確保全新、相關的資料為個人化決策提供支援。 同意執行可確保個人化遵循使用者偏好設定。 | [進階資料生命週期管理概觀](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)，[Journey Optimizer中的同意](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted) |
| 資料使用標籤和實作 | 推薦 | 用於個人化的設定檔屬性上的治理標籤（尤其是PII相鄰屬性，例如購買歷史記錄、位置、財務資料）可確保符合資料使用原則。 | [資料控管概觀](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)，[資料使用標籤概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/labels/overview) |
| 監控與可觀察性 | 推薦 | Edge傳遞與個人化效能監視有助於偵測延遲問題、傳遞失敗，或降低個人化體驗的資料時效性問題。 | [可觀察性深入分析概觀](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)，[警示概觀](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview) |
| 報告與分析 | 已包含 | Personalization效能報告是函式鏈步驟6的一部分。[!DNL Customer Journey Analytics] 分析可讓您深入調查個人化對各個訪客區段的轉換、參與和收入的影響。 | [CJA概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)，[AJO + CJA整合指南](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo) |

## 應用程式函式

此計畫會從「應用程式功能目錄」中執行下列功能。 函式會對應至實作階段，而非編號步驟。

### [!DNL Journey Optimizer] (AJO)

| 函式 | 實作階段 | 說明 |
| --- | --- | --- |
| 通道設定 | 介面和頻道設定 | 設定網頁、應用程式內和內容卡頻道介面，以進行個人化傳送 |
| 訊息製作 | 內容製作 | 為每個表面使用動態內容、個人化運算式和條件區塊來製作個人化內容變體 |
| 行銷活動執行 | Campaign設定與啟用 | 建立並啟用繫結對象、介面和內容的網路行銷活動（排程或API觸發） |
| 決策 | 決策設定（選項B/C） | 使用適用性規則、排名策略，以及動態個人化的優惠/內容專案來設定決定政策 |
| 內容實驗 | 最佳化（選擇性） | 對個人化內容變體執行A/B測試以最佳化效能 |
| 頻率與業務規則 | Campaign設定與啟用 | 強制執行曝光頻率上限以防止過度個人化疲勞 |
| 報告與效能分析 | 報告與最佳化 | 監視每個介面和區段的個人化傳遞、參與和轉換量度 |

### [!DNL Real-Time CDP] (RT-CDP)

| 函式 | 實作階段 | 說明 |
| --- | --- | --- |
| 對象評估 | 對象定義和評估 | 透過邊緣或串流評估，使用設定檔屬性、行為資料和計算屬性來定義及評估對象 |
| 即時設定檔查閱 | 內容傳送（執行階段） | 透過Edge Network存取即時設定檔屬性和區段會籍，以做出次秒個人化決策 |
| 輪廓富集 | 預先實作（支援） | 使用可改善個人化品質的計算屬性、[!DNL Customer AI]分數和彙總的行為訊號豐富設定檔 |

## 先決條件

在實作此使用案例模式之前，請先確定已具備下列條件：

- [ 在目標Web屬性上實作]個Web SDK，並將`alloy("sendEvent")`設定為頁面檢視和互動追蹤
- [ 在Target行動應用程式上實作了]行動SDK （如果使用應用程式內或內容卡表面）
- [ ]資料流已設定啟用[!DNL Adobe Journey Optimizer]服務
- [ ]設定檔結構描述包含用於個人化的屬性（忠誠度等級、購買記錄、產品興趣、生命週期階段）
- [ ]體驗事件結構描述已設定用於曝光和轉換追蹤
- [ ]已建立的已知身分名稱空間，匿名(ECID)與已驗證的身分之間可執行身分拼接作業
- [ ] Edge合併原則已設定為`isActiveOnEdge: true`
- [ ]個定義為符合Edge資格的即時個人化評估對象
- [ 為每個個人化變體準備的]內容資產（影像、復本、CTA）
- [ ] Personalization策略已記錄：哪些屬性會驅動哪些內容、針對哪些介面

## 實作選項

本節說明此使用案例模式的可用實作方法。

### 選項A：以區段為基礎的網頁個人化

**最適合：**&#x200B;決定式個人化，其中特定內容變體直接對應至對象區段 — 忠誠度等級特定主圖橫幅、生命週期階段訊息、客戶區段促銷內容。 內容至區段對應已妥善定義，且不需要動態排名或最佳化時的理想選擇。

**運作方式：**

區段型個人化會將內容變體直接對應至對象區段。 當在頁面載入時根據符合邊緣條件的對象評估已知訪客的設定檔時，系統會判斷訪客屬於哪些區段，並顯示對應的內容變體。 選取是以區段會籍優先順序為基礎 — 如果訪客符合多個區段的資格，則會顯示最高優先順序區段的內容。

此方法使用AJO Web Channel行銷活動（或應用程式內/內容卡行銷活動）搭配條件式內容規則或多種處理方式目標定位設定。 每個受眾區段都與特定內容體驗相關聯。 未涉及決策引擎 — 內容選擇邏輯完全由區段導向。

內容是使用AJO訊息製作介面搭配動態內容區塊來製作，該區塊會根據對象成員資格或設定檔屬性呈現不同內容。 Web SDK或Mobile SDK可透過Edge Network即時提供個人化體驗。

**主要考量事項：**

- 每個區段都必須預先編寫內容變體
- 區段定義必須符合即時資格的邊緣資格
- 新增區段或內容變體需要更新行銷活動設定
- 內容選擇是決定性的 — 相同的區段一律會看到相同的內容

**優點：**

- 透過清晰的內容至區段對應，可輕鬆實作及維護
- 易於向利害關係人理解和解釋個人化邏輯
- 無決策額外負荷 — 更快的內容解析度
- 完整控制每個區段接收哪些內容

**限制：**

- 區段和內容變體數量增加時，彈性有限
- 無法根據超出區段會籍的設定檔層級訊號，動態最佳化內容選擇
- 新增新內容變體需要手動行銷活動更新
- 不支援多個優惠方案競爭相同位置的優惠方案次序

**Experience League：**

- [開始使用網路頻道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [建立網站體驗](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [動態內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)

### 選項B：決策式個人化

**最適合：**&#x200B;動態個人化，其中必須使用適用性規則和排名策略為每個設定檔選取最佳內容或優惠 — 首頁上的次佳優惠、個人化產品推薦、動態促銷橫幅選擇。 當多個選件或內容專案競爭相同版位且系統必須選擇最佳選件時，這是理想之選。

**運作方式：**

決策型個人化使用AJO決策來根據內容專案或優惠方案目錄評估每位訪客的設定檔，套用適用性規則以判斷哪些專案符合資格，然後套用排名策略（優先順序、公式或AI排名）以選取每個位置的最佳專案。

實施包括建立版位（內容出現的位置）、使用適用性規則和內容表示定義優惠方案、將優惠方案組織到收藏集中，以及建立決策政策，使用排名策略將版位與收藏集繫結。 在執行階段中，當訪客載入頁面時，Edge Network會根據訪客的設定檔評估決定原則，並傳回選取的優惠內容。

此方法可支援複雜的個人化案例，包括次優優惠、具有上限的個人化促銷活動，以及AI最佳化的內容選擇。 優惠方案可以有每個設定檔和全域上限、有效日期範圍，以及結合設定檔屬性和對象會籍的複雜適用性條件。

**主要考量事項：**

- 需要更多預先設定（位置、優惠、適用性規則、集合、決定）
- 排名策略可以是優先順序（手動）、公式型（自訂運算式）或AI排名（自動最佳化）
- AI排名至少需要1,000個轉換事件才能進行模型訓練
- 在高輸送量的情況下，優惠方案上限計數器可能會稍微延遲
- 對於不符合個人化優惠條件的情況，必須設定遞補優惠

**優點：**

- 動態、個別設定檔的內容選擇，無硬式編碼區段對內容對應
- 支援複雜的資格條件和排名邏輯
- AI排名選項可啟用自動最佳化，無需手動介入
- 優惠方案上限可防止特定內容過度曝光
- 集中式優惠方案管理 — 優惠方案可跨行銷活動和管道重複使用

**限制：**

- 比區段式個人化更高的實作複雜性
- AI排名需要足夠的轉換事件數量才能訓練
- 決策評估相較於直接區段式內容傳遞，增加了輕微的延遲
- 公式式排名需要謹慎設計，以避免非預期的優先順序

**Experience League：**

- [決策管理概觀](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [建立個人化優惠方案](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [建立決定](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [排名策略](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

**這與Offer Decisioning選項B有何不同：**

基礎架構相同 — 兩者都會使用邊緣的AJO Decisioning搭配網頁SDK，以及邊緣主動合併原則。 差異在於選取的內容。 此選項可管理選擇標準適合個人化的內容專案（區段會籍、行為排名）。[Offer Decisioning](offer-decisioning.md)選項B會管理規範的優惠方案目錄，其中適用性規則、上限和有效性視窗是業務需求。 如果您的專案集需要每個設定檔曝光次數上限、法規適用性限制或優惠方案生命週期管理，請改用Offer Decisioning選項B。

### 選項C：多表面個人化（網頁+應用程式內+內容卡）

**最適合：**&#x200B;跨多個數位介面的一致個人化 — 在網頁、行動應用程式內訊息和內容卡上提供協調的個人化體驗。 適用於組織同時擁有網頁和行動應用程式屬性，且想要跨所有數位接觸點統一個人化邏輯的情況。

**運作方式：**

多表面個人化可延伸選項A （以區段為基礎）或選項B （以決策為基礎），以跨多個AJO表面型別提供個人化內容。 每個表面型別（網頁、應用程式內、內容卡）可能有不同的內容格式和傳送機制，但基礎的個人化邏輯（對象成員資格或決策）是共用的。

實作包括為每個表面型別設定管道表面、編寫表面特定內容（網頁表面的網頁HTML/CSS、應用程式內訊息的結構化內容、內容卡片的卡片配置），以及建立以適當表面為目標的行銷活動。 Web SDK處理Web介面傳送，行動SDK則處理應用程式內和內容卡傳送。

內容卡對於帳戶儀表板或應用程式首頁畫面上的持續性、可拒絕的個人化訊息特別有用。 應用程式內訊息適用於內容相關、工作階段特定的通訊。 網頁個人化可處理主圖橫幅、建議Widget和促銷內容。

**主要考量事項：**

- 每種介面型別都需要有自己的管道介面設定和內容製作
- Web SDK和Mobile SDK都必須實作和設定
- 必須為每種曲面格式（不同的尺寸、版面配置、互動圖樣）設計內容
- 共用的受眾和決策邏輯可確保介面間的一致性
- 測試必須涵蓋跨裝置的所有表面型別

**優點：**

- 跨所有數位接觸點的一致個人化體驗
- 共用的對象和決策邏輯可減少重複
- 內容卡片提供永久、非侵入式個人化表面
- 應用程式內訊息可在行動裝置上啟用情境式、工作階段專屬的個人化

**限制：**

- 最高的實作複雜性 — 需要針對每種表面型別進行設定
- 需要同時實作Web SDK和Mobile SDK
- 必須為每種表面格式設計和維護內容
- 測試範圍會隨著每個額外的曲面型別而增加

**Experience League：**

- [應用程式內頻道概觀](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/get-started-in-app)
- [內容卡頻道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/get-started-content-card)
- [開始使用網路頻道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)

### 選項比較

下表比較三個實作選項。

| 條件 | 選項A：以區段為基礎 | 選項B：決策型 | 選項C：多曲面 |
| --- | --- | --- | --- |
| 最適合 | 已知的區段對內容對應 | 每個設定檔的動態內容選擇 | 跨Web和行動裝置的一致個人化 |
| 複雜性 | 低 | Medium — 高 | 高（以A或B建置） |
| 延遲 | 最快（直接區段解析度） | 略高（決策評估） | 取決於基礎選項（A或B） |
| 彈性 | 僅限於預先定義的區段內容配對 | 高 — 動態排名和資格 | 最高 — 使用共用邏輯的多重介面 |
| 內容管理 | 手動區段對內容對應 | 具有適用性規則的集中式優惠資料庫 | 使用共用個人化邏輯的每一介面內容 |
| 最佳化 | 手動A/B測試 | 可使用AI排名自動最佳化 | 每個表面最佳化 |
| 需要 | 符合Edge資格的受眾，Web SDK | 位置、優惠、適用性規則、決定 | Web SDK + Mobile SDK，多重表面設定 |
| 支援的表面 | 網頁（主要） | 網頁（主要） | 網頁+應用程式內+內容卡 |

### 選擇正確的選項

從這些問題開始，選擇正確的實作方法：

1. **有多少表面？** 如果您需要在網頁和行動應用程式上進行個人化，請選擇選項C （這是以A或B為基礎的基礎邏輯）。 如果是Web版，請選擇A和B。

2. **您的內容選擇有多動態？** 如果您已妥善定義區段對應至內容變體（例如3-5忠誠度等級，各有特定主圖橫幅），請選擇選項A。如果您需要從具有複雜資格和排名的優惠方案目錄中選取，請選擇選項B。

3. **您需要AI最佳化的選擇嗎？** 如果您希望系統自動學習並最佳化哪些內容最適合每個設定檔，請選擇包含AI排名決策的選項B 。

4. **有多少種內容變體？** 如果您的內容變體少於10種，且具有清楚的區段對應，則選項A會比較簡單。 如果您的數十個優惠方案需要資格篩選和排名，則選項B的規模會比較好。

5. **您打算延伸至其他管道嗎？** 如果您的決策邏輯最終應跨電子郵件、網頁和其他管道提供優惠方案，則選項B可提供跨管道優惠方案決策的集中式基礎。

## 實作階段

本節將詳細介紹實作的每個階段。

### 階段1：定義對象並設定評估

**應用程式函式：** RT-CDP：對象評估

**您將要設定的專案：**&#x200B;定義可推動個人化內容選擇的對象。 這些受眾代表將接收個人化體驗的訪客區段 — 忠誠度等級、生命週期階段、行為同類群組或產品相似性群組。

此階段中的&#x200B;**決定點：**

>[!NOTE]
>**決定：對象評估方法**
>
>針對個人化解析對象會籍必須多久？ 這會直接影響個人化是否會在頁面載入時發生，或需要延遲。
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 邊緣評估 | 需要次秒資格的即時Web/應用程式個人化 | 僅限於簡單的設定檔屬性檢查和區段會籍。 沒有時間序列查詢或複雜的彙總。 已知訪客個人化的必要專案。 |
>| 串流評估 | 當設定檔根據行為事件進入/退出對象時，近乎即時資格 | 支援單一事件和有限的時間範圍查詢。 對象變更會在數分鐘內反映。 適用於可接受輕微延遲的應用程式內和內容卡表面。 |
>| 批次評估 | 根據複雜彙總或歷史模式的區段每日對象重新整理 | 完整的區段規則函式支援。 不適合即時個人化，但可以用複雜的預先計算區段來補充邊緣對象。 |

>[!NOTE]
>**決定： Personalization屬性**
>
>哪些設定檔屬性應該驅動對象定義和內容選擇？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 設定檔屬性（忠誠度等級、生命週期階段） | 根據已知客戶屬性的確定性個人化 | 定義良好的穩定屬性。 輕鬆對應至內容變體。 如果設定檔已正確設定，則可在邊緣使用。 |
>| 行為訊號（購買記錄、瀏覽模式） | 根據最近的行為和參與模式的Personalization | 需要運算屬性或串流區段。 更具動態性，但需要維護的流程更複雜。 |
>| 傾向分數([!DNL Customer AI]) | 根據轉換、流失或購買的可能性進行預測性個人化 | 需要運算屬性。 啟用複雜的個人化，但需要ML模型訓練資料。 |
>| 組合方法 | 大部分的生產實作 | 使用設定檔屬性進行主要細分，其中包含行為訊號和細分的傾向分數。 |

**UI導覽：**&#x200B;客戶>對象>建立對象>建置規則

**金鑰組態詳細資料：**

- 使用區段產生器定義對象，搭配參考設定檔屬性的區段規則運算式
- 確定區段規則運算式符合邊緣評估資格（簡單屬性檢查、區段成員資格）
- 針對即時個人化使用案例設定邊緣合格對象
- 請考慮使用隱藏受眾來排除最近轉換或退出的訪客

**Experience League檔案：**

- [區段產生器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [邊緣分段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [串流區段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Profile Query Language參考](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### 階段2：設定決策（僅限選項B和C）

**應用程式函式：** AJO：決策

**您要設定的專案：**&#x200B;設定決策基礎結構，以動態方式為每個訪客選取最佳內容或選件。 這包括版位（優惠方案出現的位置）、優惠方案（有哪些內容可用）、適用性規則（符合資格者）、排名策略（如何選擇最佳方案）和決定策略（一切如何連線）。

此階段中的&#x200B;**決定點：**

>[!NOTE]
>**決定：排名策略**
>
>應如何排名合格的優惠方案，以選取適合每位訪客的優惠方案？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 優先順序（手動） | 具有清晰優惠階層的簡單使用案例 | 每個選件都有手動優先順序值。 最高優先順序的合格優惠獲勝。 易於理解和控制。 |
>| 以公式為基礎（自訂運算式） | 排名何時應考慮設定檔屬性 | 自訂排名公式會參考設定檔資料（例如，依忠誠度層級+造訪間隔的分數）。 有彈性，但需要公式設計和測試。 |
>| AI排名（自動最佳化） | 您希望系統自動最佳化優惠選擇時 | ML模型會學習哪些選件對哪些設定檔的效能最佳。 訓練需要至少1,000個轉換事件。 最適合高流量的位置。 |

>[!NOTE]
>**決定：優惠上限**
>
>選件向訪客或所有訪客顯示的次數應該有限制嗎？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 每個設定檔上限 | 避免疲勞時重複看到相同的選件 | 限制一段時間內每位訪客的曝光數。 確保個人化體驗的多樣性。 |
>| 全域上限 | 限制促銷或可用性限制優惠的曝光總數 | 限制所有訪客的總曝光次數。 適用於數量有限的促銷活動。 |
>| 無上限 | 歷久不衰的內容或永遠相關的選件 | 沒有曝光限制。 適用於忠誠度等級橫幅等永續性內容。 |

**使用者介面導覽：** [!DNL Journey Optimizer] >元件>決定管理

**金鑰組態詳細資料：**

- 為將顯示選件的每個表面建立版位（網頁橫幅、應用程式內訊息區域、內容卡槽）
- 使用參考設定檔屬性和對象成員資格的區段規則運算式，定義適用性規則
- 建立個人化優惠方案，並針對每個版位提供內容表示
- 建立涵蓋所有刊登版位的遞補優惠（無個人化優惠符合資格時顯示）
- 使用集合限定詞（標籤）組織優惠方案，並將優惠方案分組為集合
- 使用選取的排名策略建立將位置與集合繫結的決定原則

**Experience League檔案：**

- [建立產品建議放置環境](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [建立決定規則](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [建立個人化優惠方案](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [建立後備產品建議](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [建立集合](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [建立決定](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [排名策略](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### 階段3：設定表面和通道

**應用程式函式：** AJO：頻道設定

**您的設定內容：**&#x200B;設定頻道介面，定義個人化內容的傳送位置。 每個表面型別（網頁、應用程式內、內容卡）都需要其專屬的設定，以指定表面URI、內容格式和傳送引數。

此階段中的&#x200B;**決定點：**

>[!NOTE]
>**決定：目標表面**
>
>哪些數位介面會接收個人化內容？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 僅限網路頻道 | Personalization著重於網頁屬性 | 需要使用Web SDK。 最簡單的實施。 涵蓋主圖橫幅、促銷區域、建議Widget。 |
>| 僅限應用程式內頻道 | Personalization著重於行動應用程式體驗 | 需要使用Mobile SDK。 涵蓋應用程式內的內容、工作階段特定訊息。 |
>| 僅限內容卡通道 | 永久性、可拒絕的個人化訊息 | 需要行動SDK或網頁SDK。 卡片會持續存在，直到被解除為止。 適用於控制面板和首頁熒幕。 |
>| 多個曲面（選項C） | 在網頁和行動裝置間持續提供個人化服務 | 需要使用Web SDK和Mobile SDK。 每個表面都需要個別的設定和內容。 |

>[!NOTE]
>**決定：網頁表面設定方法**
>
>應如何設定網頁介面以進行內容傳送？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 單頁應用程式(SPA) | 具有使用者端路由的現代網頁應用程式 | 在網頁SDK `sendEvent`呼叫中使用`renderDecisions: true`。 SDK自動轉譯的內容。 |
>| 多頁應用程式(MPA) | 傳統伺服器轉譯網頁 | 透過Edge Network回應在頁面載入時傳遞的內容。 可能需要頁面層級表面URI設定。 |

**UI導覽：** [!DNL Journey Optimizer] >管理>管道>管道表面

**金鑰組態詳細資料：**

- 針對網頁表面：設定與目標頁面相符的網頁表面URI
- 針對應用程式內表面：使用應用程式ID和表面型別設定行動應用程式表面
- 對於內容卡表面：使用應用程式ID或網頁內容設定內容卡表面
- 確保資料流已啟用AJO服務以進行邊緣個人化傳送

**Experience League檔案：**

- [開始使用網路頻道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [Web頻道設定](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/web-configuration)
- [應用程式內頻道必要條件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/inapp-configuration)
- [內容卡設定](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/content-card-configuration)

### 階段4：作者內容

**應用程式函式：** AJO：訊息製作

**您將要設定的專案：**&#x200B;為每個介面和區段或選件編寫個人化內容變體。 這包括設計視覺版面、新增參考設定檔屬性的個人化運算式、設定條件式內容區塊，以及建立可重複使用的內容片段。

此階段中的&#x200B;**決定點：**

>[!NOTE]
>**決定：內容方法**
>
>個人化內容應如何針對此使用案例而建構？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 條件式內容區塊 | 相同版面中的不同內容區段會因對象而異 | 具有條件規則的單一內容資產。 適用於次要變化（標題、CTA文字、影像交換）。 |
>| 根據處理方式區分內容變體 | 每個對象的版面或設計完全不同 | 多個完整內容資產。 更具彈性，但需要維護的更多。 內容實驗所需。 |
>| 決策驅動的內容 | 從優惠方案目錄動態選取的內容 | 優惠代表定義內容。 內容管理集中在選件程式庫中。 |

>[!NOTE]
>**決定： Personalization深度**
>
>應該個人化多少內容？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 表面層級個人化 | 只有特定元素會個人化（主圖影像、CTA、優惠橫幅） | 降低複雜性。 將個人化聚焦於高影響力的領域。 最常見的起點。 |
>| 全頁個人化 | 整頁版面配置或內容排序都會個人化 | 更高的複雜性。 需要廣泛的內容建立。 提供最自訂的體驗。 |
>| 權杖層級個人化 | 內嵌個人化權杖（名稱、階層、點數餘額） | 最簡單的形式。 將設定檔屬性值插入其他靜態內容中。 |

**使用者介面導覽：** [!DNL Journey Optimizer] >行銷活動>建立行銷活動>編輯內容

**選項差異的位置：**

選項A的&#x200B;**（以區段為基礎）：**

- 使用網頁設計工具或程式碼編輯器為每個受眾區段編寫內容變體
- 動態內容區塊搭配以受眾成員資格為基礎的條件使用
- 設定參考設定檔屬性的個人化運算式（例如，`{{profile.person.name.firstName}}`、`{{profile.loyalty.tier}}`）
- 設定條件規則，以根據區段成員資格顯示不同內容

選項B的&#x200B;**（決策型）：**

- 為階段2中定義的每個版位製作優惠方案內容表示
- 每個優惠方案都有一或多個與刊登版位相符的宣告（HTML、影像、JSON）
- 透過內嵌決策位置，將決策輸出整合到網頁或應用程式中
- 內容會在執行階段以動態方式選取 — 撰寫會聚焦於個別選件專案

選項C （多表面）的&#x200B;**：**

- 為每個目標表面製作表面專屬的內容（網頁HTML/CSS、應用程式內結構化訊息、內容卡版面配置）
- 在適應每個表面的格式限制時，維持跨表面一致的個人化邏輯
- 測試每種表面型別上的內容演算

**Experience League檔案：**

- [建立網站體驗](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [新增個人化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization語法](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [動態內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [輔助函式](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [在訊息中傳遞優惠方案](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [建立應用程式內訊息](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/create-in-app)
- [建立內容卡片](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/create-content-card)

### 階段5：設定並啟用行銷活動

**應用程式函式：** AJO：行銷活動執行

**您的設定內容：**&#x200B;建立並啟用AJO行銷活動，將對象、介面和內容繫結在一起以進行傳遞。 針對網頁個人化，行銷活動通常設定為立即或持續啟用，而非一次性排程傳送。

此階段中的&#x200B;**決定點：**

>[!NOTE]
>**決定：行銷活動型別**
>
>應如何觸發個人化行銷活動？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 已排程的行銷活動（永遠開啟） | 持續為所有合格訪客執行的持續個人化 | 將開始日期設為立即，無結束日期。 行銷活動會維持作用中狀態，直到手動停止為止。 最常用於網頁個人化。 |
>| 已排程的行銷活動（時間範圍） | 繫結至特定促銷期間的Personalization | 設定開始和結束日期。 行銷活動會在結束日期後自動停止。 適用於季節性促銷活動或限時優惠。 |
>| API觸發的行銷活動 | 由特定應用程式事件觸發的Personalization | 以程式設計方式觸發。 當個人化只應回應特定系統事件而出現時非常有用。 |

>[!NOTE]
>**決定：頻率上限**
>
>此個人化的曝光頻率是否應受到限制？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 套用頻率規則 | 可能使訪客疲憊的促銷或選件型個人化 | 防止相同的個人化出現太多次。 透過AJO商業規則設定。 |
>| 無頻率上限 | 歷久不衰的內容個人化（忠誠度等級橫幅、儀表板內容） | 不會造成疲勞的永遠相關內容。 不需要曝光限制。 |

**使用者介面導覽：** [!DNL Journey Optimizer] >行銷活動>建立行銷活動

**金鑰組態詳細資料：**

- 選取網頁、應用程式內或內容卡頻道，以及在階段3中設定的表面
- 繫結階段1中定義的目標對象
- 連結階段4中撰寫的內容
- 設定行銷活動排程（立即、日期範圍或由API觸發）
- 檢閱及啟動行銷活動
- 內容實驗：啟用實驗切換、定義處理、設定流量分配和成功量度，然後再啟用

**Experience League檔案：**

- [建立行銷活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [開始使用行銷活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [頻率規則](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [開始使用內容實驗](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [建立內容實驗](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)

### 階段6：追蹤曝光數並收集資料

**應用程式函式：** AEP：資料來源與集合

**您要設定的專案：**&#x200B;確保將個人化體驗的曝光、互動和轉換追蹤回平台，以進行報告、對象重新評估和決策最佳化。

**金鑰組態詳細資料：**

- 驗證在呈現個人化內容時Web SDK是否傳送`decisioning.propositionDisplay`個事件
- 確認當訪客與個人化內容（點按、取消）互動時，Web SDK正在傳送`decisioning.propositionInteract`個事件
- 對於Mobile SDK：確認已擷取應用程式內訊息和內容卡互動事件
- 設定下游成功量度（購買、註冊、功能採用）的轉換事件追蹤
- 確保事件包含歸因至特定個人化決定的主張ID

**Experience League檔案：**

- [網頁SDK概觀](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [使用Web SDK追蹤事件](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/commands/sendevent/overview)
- [行動SDK概觀](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)

### 第7階段：報告並最佳化

**應用程式功能：** AJO： Reporting &amp; Performance Analysis、Reporting &amp; Analysis

**您的設定專案：**&#x200B;設定效能監視和分析，以測量介面、區段和內容變體間的個人化成效。 使用AJO原生報表進行營運量度，並使用[!DNL Customer Journey Analytics]進行跨管道業務影響分析。

此階段中的&#x200B;**決定點：**

>[!NOTE]
>**決定：報告範圍**
>
>此個人化使用案例需要哪個分析層級？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 僅限AJO原生報表 | 傳遞和參與量度的營運監控 | 內建的行銷活動報告，包含曝光數、點選數和轉換資料。 設定速度最快。 |
>| CJA跨頻道分析 | 深入分析個人化對業務成果的影響 | 需要CJA連線和資料檢視。 跨管道啟用funnel分析、同類群組比較和歸因模型。 |
>| AJO + CJA | 完整的營運和分析可見度 | 使用AJO進行日常監控，使用CJA進行策略分析。 建議用於生產實作。 |

**使用者介面導覽：**

- AJO報表：促銷活動>選取促銷活動>檢視報表
- CJA：專案>建立新專案

**金鑰組態詳細資料：**

- 在作用中的個人化傳遞期間存取行銷活動即時報告
- 檢閱已完成行銷活動或定期分析的歷史報告
- CJA：設定包含AJO體驗事件資料集的連線，並使用個人化量度建立資料檢視
- 建立控制面板，追蹤個人化參與率、轉換提升度、優惠接受率和每次造訪帶來的收入
- 針對以決定為基礎的個人化（選項B）：按位置及排名策略有效性監控優惠方案績效

**Experience League檔案：**

- [行銷活動即時報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [行銷活動全域報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [內容實驗報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [Analysis Workspace概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [AJO + CJA整合指南](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

## 實施考量

本節涵蓋與此使用案例模式相關的護欄、常見陷阱、最佳實務和取捨決定。

### 護欄和限制

- 對於邊緣評估的區段，Edge Network查詢的回應時間SLA小於200毫秒 — [即時客戶設定檔護欄](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- 每個沙箱最多4,000個區段定義 — [分段護欄](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- Edge區段僅限於簡單屬性檢查和區段成員資格查詢 — 無時間序列查詢 — [Edge區段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- 每個沙箱在Edge上只能有一個作用中的合併原則 — [合併原則](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- 每個沙箱最多10,000個核准的個人化優惠 — [決定管理護欄](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- 每個決定最多30個位置 — [Journey Optimizer護欄](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- AI排名模型需要至少1,000個轉換事件才能訓練
- 單範圍要求的選件傳送回應時間SLA在P95小於500毫秒
- 每個沙箱最多500個作用中即時行銷活動 — [Journey Optimizer護欄](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- 每個沙箱最多25個使用中的計算屬性 — [計算屬性護欄](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)

### 常見陷阱

- **未設定Edge合併原則：**&#x200B;若沒有Edge-Active合併原則，Edge Network將無法解析已驗證的設定檔，導致個人化失敗或回覆為匿名行為。 請確定沙箱中只有一個合併原則具有`isActiveOnEdge: true`。
- **不符合Edge標準的對象：**&#x200B;如果對象區段規則運算式使用時間序列查詢、複雜彙總，或僅批次區段的`inSegment()`參考，則不符合邊緣評估的資格，且無法支援即時個人化。 在對象定義期間驗證邊緣適用性。
- **驗證期間身分拼接間隙：**&#x200B;當訪客從匿名轉換為已驗證時，可能會有短暫的時間尚未解析設定檔。 請確認身分拼接已正確設定，且Web SDK會在登入後立即透過`identityMap`傳送已驗證的身分識別。
- **決策中缺少遞補優惠：**&#x200B;如果未設定遞補優惠，且沒有符合訪客資格的個人化優惠，決策會傳回空白內容，造成體驗中斷。 一律設定涵蓋所有位置的遞補優惠。
- **Web SDK未傳送主張顯示事件：**&#x200B;如果`renderDecisions`設定為`true`但未傳送顯示事件，報告將不會反映實際的曝光數。 透過在瀏覽器開發人員工具中檢查網路請求來驗證事件追蹤。
- **頁面載入時內容忽隱忽現：**&#x200B;如果決策呼叫期間未預先隱藏個人化內容，則訪客在取代預設內容之前可能會短暫看到預設內容。 使用預先隱藏程式碼片段或以CSS為基礎的預先隱藏，可消除忽隱忽現情形。

### 最佳實務

- 從最初實作的區段型個人化（選項A）開始，然後隨著優惠方案目錄增長和最佳化需求增加，進化為決策型（選項B）
- 儘可能使用邊緣評估對象進行即時個人化；保留串流和批次對象以供補充使用案例
- 在個人化體驗上實作內容實驗，以驗證個人化是否可帶動預設內容的可測量提升度
- 設計具有優雅降級策略的個人化 — 如果無法在邊緣解析設定檔，會顯示設計良好的預設內容，而非損壞的體驗
- 使用運算屬性來建立高值的個人化訊號，例如參與分數、產品相似性和上次購買間隔天數，這會改善區段型和決策型個人化品質
- 維護內容控管程式，以確保個人化內容保持最新、符合品牌規範，並跨越所有表面
- 依區段監控個人化績效，以識別哪些對象最受益於個人化，以及提升度最強的位置

### 權衡決定

>[!NOTE]
>**取捨： Personalization詳細程度與內容管理複雜性**
>
>更細微的個人化（更多區段、更多內容變體、更多介面）提供日益客製化的體驗，但需要按比例更多內容建立、維護和治理工作。
>
>- **更高的詳細程度優先：**&#x200B;更好的客戶體驗、更高的參與度、更強的轉換提升度
>- **較低的詳細程度：**&#x200B;更快的實作、較低的內容維護負擔、更簡單的控管
>- **建議：**&#x200B;從3至5個具高度影響力的區段（例如，忠誠度等級或生命週期階段）開始，並清楚區分內容。 根據測量的效能提升度展開詳細程度。 使用決策（選項B）來擴展粒度，而不需要成比例的內容管理成長。

>[!NOTE]
>**取捨：即時決策與確定性內容控制**
>
>以決定為基礎的個人化（選項B）提供動態最佳化，但減少直接控制每位訪客看到的內容。 以區段為基礎的個人化（選項A）提供完整的確定性控制，但限制動態最佳化。
>
>- **決策優惠：**&#x200B;擴充性、自動最佳化、複雜適用性案例
>- **區段型優惠：**&#x200B;可預測性、法規遵循控制、利害關係人透明度
>- **建議：**&#x200B;針對需要精確控制的規範敏感內容（法規訊息、層級特定定價），使用區段式個人化。 針對動態最佳化可增加值的促銷內容、優惠和建議，使用決策。

>[!NOTE]
>**取捨： Edge資料可用性與個人化豐富度**
>
>Edge評估的個人化僅限於邊緣設定檔存放區中可用的屬性。 更豐富的個人化訊號（完整行為記錄、複雜的運算屬性）可能需要伺服器端查閱或預先計算。
>
>- **僅限Edge的好處：**&#x200B;次秒延遲，最簡單的架構
>- **預先計算的擴充偏好：**&#x200B;更豐富的個人化訊號、更複雜的對象定義
>- **建議：**&#x200B;使用運算屬性，將豐富行為訊號預先彙總到邊緣可用的設定檔屬性中。 這可提供豐富的行為資料與邊緣評估速度。

## 相關文件

下列資源提供本指南參考之技術和設定的其他詳細資訊。

### Web頻道個人化

- [開始使用網路頻道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [建立網站體驗](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [Web頻道設定](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/web-configuration)

### 應用程式內和內容卡頻道

- [應用程式內頻道概觀](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/get-started-in-app)
- [應用程式內頻道必要條件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/inapp-configuration)
- [建立應用程式內訊息](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/create-in-app)
- [內容卡頻道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/get-started-content-card)
- [內容卡設定](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/content-card-configuration)
- [建立內容卡片](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/create-content-card)

### 決定管理

- [決策管理概觀](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [建立產品建議放置環境](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [建立決定規則](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [建立個人化優惠方案](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [建立後備產品建議](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [建立集合](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [建立決定](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [排名策略](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)
- [在訊息中傳遞優惠方案](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

### Personalization與內容

- [新增個人化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization語法](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [輔助函式](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [動態內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [使用內容範本](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [使用內容片段](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)

### 對象和細分

- [Segmentation Service概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [區段產生器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [邊緣分段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [串流區段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Profile Query Language參考](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### 身分和設定檔

- [Identity Service總覽](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [身分名稱空間概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/identity/features/namespaces)
- [身分識別圖連結規則](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/identity-linking-logic)
- [設定檔概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [合併原則概觀](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

### 資料收集和SDK

- [網頁SDK概觀](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [安裝Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/install/overview)
- [行動SDK概觀](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [設定資料串流](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Edge Network伺服器API總覽](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)

### 行銷活動和實驗

- [開始使用行銷活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [建立行銷活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [開始使用內容實驗](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [建立內容實驗](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [內容實驗報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)

### 計算的屬性和擴充

- [計算屬性概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [計算屬性UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/ui)
- [Customer AI概述](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview)

### 報告與分析

- [行銷活動即時報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [行銷活動全域報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [AJO + CJA整合指南](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [CJA概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Analysis Workspace概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)

### 治理和隱私權

- [資料控管概覽](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Journey Optimizer中的同意](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)
- [進階資料生命週期管理概觀](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)

### 護欄

- [Journey Optimizer護欄](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [即時客戶個人檔案護欄](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Identity Service護欄](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)
