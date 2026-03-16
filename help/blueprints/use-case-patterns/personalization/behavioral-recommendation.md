---
title: 行為建議
description: 瞭解如何使用選擇策略和排名模型來產生專案和內容推薦。
solution: Journey Optimizer, Real-Time Customer Data Platform
source-git-commit: 126dd712603494513b71a8a6e1c4b99bdb7ff212
workflow-type: tm+mt
source-wordcount: '7626'
ht-degree: 2%

---


# 行為建議

本指南涵蓋如何使用[!DNL Adobe Journey Optimizer] (AJO) Decisioning、[!DNL Real-Time Customer Data Platform] (RT-CDP)和[!DNL Adobe Experience Platform] (AEP)實作行為產品和內容建議。 它專為需要跨網路、行動應用程式和電子郵件通道提供個人化建議體驗的解決方案架構師、行銷技術人員和實作工程師所設計。

它提供所有可行的實作選項、每個階段的決定考量事項，以及[!DNL Adobe Experience League]檔案的連結。 行為建議使用行為訊號（產品檢視、購買、內容互動、搜尋查詢）與AJO Decisioning選擇策略和排名模型結合，產生專案層級或內容層級的建議。 Offer Decisioning會使用明確的適用性規則，從經過組織的行銷優惠方案集合中選取，此模式會在大型專案目錄（產品、文章、影片）上運作，並使用行為相似性訊號及ML型排名來呈現每位訪客最相關的專案。

## 使用案例概述

擁有產品目錄、內容庫或媒體庫的組織需要根據訪客的行為歷史記錄和工作階段中的活動，向每位訪客呈現最相關的專案。 無論是首頁上的「為您推薦」輪播、產品詳細資料頁面上的交叉銷售Widget，或內嵌在電子郵件促銷活動中的產品推薦，基本挑戰都相同：將每位訪客的行為設定檔與目錄中最相關的專案進行比對，然後在適當的時間在適當的管道中提供這些推薦。

此模式可透過[!DNL Web SDK]或[!DNL Mobile SDK]即時擷取行為訊號、透過AJO Decisioning選擇策略處理這些訊號（這些策略會將專案屬性與行為內容相結合），以及透過Web、應用程式內或電子郵件通道傳遞建議專案，藉此解決該挑戰。 排名模型可根據公式（例如依類別相關性分數排序）或AI排名（例如個人化推薦模型）。 此模式也會透過設定遞補建議來處理沒有行為歷史記錄的新訪客的冷啟動案例。

此模式的目標受眾包括電子商務銷售團隊、內容個人化團隊和數位體驗團隊，這些團隊尋求透過真實使用者行為驅動的個人化建議，改善參與度、轉換和平均訂單價值。

## 主要業務目標

此使用案例模式支援下列業務目標。

### [推動交叉銷售和追加銷售收入](../../business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)

根據行為和購買記錄，向現有客戶推廣補充性和優質產品或服務。

| KPI | 說明 |
| --- | --- |
| 追加銷售/交叉銷售% | 購買建議補充或優質專案的客戶百分比 |
| 遞增收入 | 因建議驅動型購買而產生的額外收入 |
| 客戶期限值 | 更深入的產品參與度帶來的長期價值提升 |

### [提高轉換率](../../business-objectives/revenue-monetization/increase-conversion-rates.md)

提高完成所需動作（例如購買、註冊或提交表單）的訪客和潛在客戶的百分比。

| KPI | 說明 |
| --- | --- |
| 轉換率 | 參與推薦後轉換的訪客百分比 |
| 潛在客戶轉換 | 參與推薦的訪客成為客戶的比率 |
| 每個潛在客戶的成本 | 透過有機建議參與來降低贏取成本 |

### [提供個人化的客戶體驗](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)

根據個別偏好設定、行為和生命週期階段量身打造內容、選件和訊息。

| KPI | 說明 |
| --- | --- |
| 參與度 | 與建議表面（點選、檢視、加入購物車）的互動頻率 |
| 轉換率 | 建議參與訪客與控制項的轉換率提升度 |
| 客戶滿意度(CSAT) | 從相關的個人化體驗提升客戶滿意度 |

## 戰術使用案例範例

以下是此模式的常見戰術實施：

- 產品詳細資料頁面上的產品交叉銷售Widget （「客戶也購買了」）
- 根據瀏覽歷史記錄，首頁上的「為您推薦」輪播
- 根據閱讀行為在媒體網站上提供內容建議
- 結合類似專案Widget的「最近檢視」
- 購買後補充產品推薦
- 根據行為相似性以電子郵件傳送產品建議
- 根據工作階段中瀏覽行為的類別特定建議
- 根據行為訊號重新排名的搜尋結果

## 關鍵績效指標

下列KPI有助於評估行為建議實作的效益。

| KPI | 測量方式 |
| --- | --- |
| 建議點進率(CTR) | 建議專案的點按次數除以建議曝光數 |
| 建議轉換率 | 建議點選數的購買或所需動作除以建議點選總數 |
| 受Recommendations影響的收入 | 來自至少包含一個建議導向產品的訂單的總收入 |
| 平均訂購值(AOV)提升度 | 參與建議工作階段與未參與工作階段的AOV增加 |
| 每個訂單的專案 | 建議參與工作階段的每張訂單專案數 |
| 建議涵蓋範圍 | 收到個人化（非備援）建議的合格頁面檢視或工作階段百分比 |
| 冷啟動後援率 | 因行為記錄不足而由遞補邏輯提供的建議要求百分比 |

## 使用案例模式

**行為建議**

使用AJO Decisioning選擇策略和排名模型，根據行為訊號產生專案層級或內容層級的建議，以提供內容相關內容。

**功能鏈：**&#x200B;行為訊號擷取>決策策略評估>建議傳送>報告

如需合併模式的指引，請參閱實作考量事項底下的模式組合一節。

## 應用程式

在此使用案例模式中使用以下應用程式。

- **[!DNL Adobe Journey Optimizer] (AJO)決策** — 選擇策略、排名模型、專案目錄和決策原則，用於評估行為訊號並傳回每個訪客最相關的專案
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** — 行為設定檔資料累積、建議範圍的對象評估，以及行為相似性評分的計算屬性
- **[!DNL Adobe Experience Platform] (AEP)** — 透過[!DNL Web SDK]和[!DNL Mobile SDK]的行為事件擷取，[!DNL Edge Network]處理，事件和目錄資料的XDM結構描述管理

## 基礎函式

下列基本功能必須為此使用案例模式準備就緒。 對於每個函式，狀態會指出它通常是必要的、假設為預先設定或不適用。

| 基礎函式 | 狀態 | 必須準備就緒的專案 | Experience League參考 |
| --- | --- | --- | --- |
| 管理與治理 | 已假設就位 | 已啟用決策許可權的AJO沙箱。 布建的使用者角色可存取專案目錄管理、選擇策略設定和管道表面管理。 | [沙箱總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sandbox/home)，[存取控制總覽](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| 資料模型與準備 | 必填 | 體驗事件結構描述會擷取具有專案/產品識別碼的行為訊號（產品檢視、加入購物車、購買、內容互動）。 建議專案集的專案目錄結構（產品屬性、類別、影像、價格）。 具有身分欄位的設定檔結構描述。 已為[!DNL Real-Time Customer Profile]啟用所有結構描述。 | [XDM系統總覽](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)，[結構描述組合基本概念](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)，[建立資料集](https://experienceleague.adobe.com/en/docs/experience-platform/catalog/datasets/create) |
| 資料來源與收集 | 必填 | 透過[!DNL Web SDK]或[!DNL Mobile SDK]的即時行為事件串流至關重要 — 建議品質取決於新的行為訊號。 必須擷取專案目錄資料（批次或串流）。 資料串流已針對Edge決策啟用AJO服務。 | [網頁SDK概觀](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)，[行動SDK概觀](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)，[設定資料串流](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure) |
| 身分和設定檔設定 | 必填 | 行為訊號必須與身分相關聯（透過ECID已知或匿名），以建立行為設定檔。 針對已知訪客的建議，必須設定已驗證的身分識別（CRM ID、電子郵件）。 Edge上生效的合併原則，用於即時建議傳遞。 | [身分識別服務總覽](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)，[合併原則總覽](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview) |
| 對象定義與細分 | 推薦 | 受眾可用於設定建議範圍（例如，僅向進階成員建議進階產品）或進行篩選。 如果建議是純行為，則非絕對必要。 以電子郵件為基礎的建議（選項C）需要定義目標對象。 | [區段服務總覽](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)，[區段產生器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder) |

## 支援功能

以下功能可擴大此使用案例模式，但不是核心執行的必要功能。

| 支援功能 | 狀態 | 為什麼重要 | Experience League參考 |
| --- | --- | --- | --- |
| 計算/衍生屬性建立 | 推薦 | 類別相關性分數、產品互動頻率、購買造訪間隔和總支出等運算屬性可改善建議排名品質。[!DNL Customer AI] 傾向分數可透過預測購買可能性來進一步增強關聯性。 | [計算屬性總覽](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)，[Customer AI總覽](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview) |
| 資料生命週期管理 | 推薦 | 行為事件資料應該有適當的到期原則 — 建議相關性會隨著過時資料而降低。 在行為事件資料集上設定資料集過期原則，可確保資料集的新鮮度並管理儲存空間。 同意實作可確保符合規範地使用行為資料。 | [資料集有效期](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/ui/dataset-expiration)，[進階資料生命週期管理概觀](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| 資料使用標籤和實作 | 推薦 | 行為資料上的治理標籤可確保針對建議合規使用互動歷史記錄。 當行為資料包含瀏覽模式、購買記錄或健康情況/金融產品興趣訊號時，尤其重要。 | [資料控管概觀](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)，[資料使用標籤概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/labels/overview) |
| 監控與可觀察性 | 推薦 | 應監控建議傳遞延遲、遞補率和專案目錄擷取健康狀態。 行為事件擷取失敗和決策錯誤的相關警示，有助於維持建議品質。 | [可觀察性深入分析概觀](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)，[警示概觀](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview) |
| 報告與分析 | 已包含 | 建議績效報表是函式鏈步驟4的一部分。[!DNL Customer Journey Analytics] 分析各表面和區段的建議成效、收入影響和專案層級績效，可提供最佳化深入分析。 | [CJA概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)，[Analysis Workspace概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home) |

## 應用程式函式

此計畫會從「應用程式功能目錄」中執行下列功能。 函式會對應至實作階段，而非編號步驟。

### [!DNL Journey Optimizer] (AJO)

| 函式 | 實作階段 | 說明 |
| --- | --- | --- |
| 決策 | 專案目錄與選擇策略設定 | 設定專案目錄（決定專案）、具有行為排名模型的選擇策略、篩選規則和遞補建議 |
| 通道設定 | 管道和表面設定 | 設定網頁（程式碼型體驗）、應用程式內、內容卡片或電子郵件頻道的傳送介面，以便呈現建議 |
| 訊息製作 | 內容與傳遞設定 | 設計建議呈現範本、專案顯示版面配置，以及建議專案的個人化運算式 |
| 報告與效能分析 | 報告與最佳化 | 透過AJO原生報告和[!DNL Customer Journey Analytics]整合，監視建議點進、轉換和收入量度 |

### [!DNL Real-Time CDP] (RT-CDP)

| 函式 | 實作階段 | 說明 |
| --- | --- | --- |
| 對象評估 | 對象範圍（選項C） | 評估用來設定建議範圍或定義電子郵件建議行銷活動目標母體的對象區段 |
| 輪廓富集 | 行為訊號擴充 | 使用可改善建議排名的運算屬性（類別相關性分數、互動頻率）讓設定檔更為豐富 |

## 先決條件

開始實作前請先完成下列作業：

- AJO Decisioning已在Target沙箱中布建及啟用
- 已部署[!DNL Web SDK]或[!DNL Mobile SDK]，並使用產品/內容識別碼收集行為事件
- 產品或內容目錄資料可用於內嵌（產品名稱、類別、價格、影像URL、可用性）
- 行為事件結構描述包含連結至目錄專案的專案/產品識別碼
- 資料流設定已啟用[!DNL Adobe Journey Optimizer]服務（Edge決策所需）
- 已設定與`isActiveOnEdge: true`的合併原則（即時Web/應用程式建議所需）
- 電子郵件建議（選項C）：電子郵件通道介面已設定並驗證
- 對於電子郵件建議（選項C）：已定義目標對象並評估

## 實作選項

下列選項說明實作行為建議的不同方法。 選擇最符合您的通路需求和技術限制的選項。

### 選項A：網頁即時建議

**最適合：**&#x200B;網頁上的產品或內容推薦 — 產品詳細資料頁面交叉銷售Widget、首頁推薦輪播、類別頁面個人化清單，以及搜尋結果個人化。

**運作方式：**

當訪客瀏覽網站時，會透過[!DNL Web SDK]即時收集行為訊號。 每個頁面檢視、產品互動或搜尋查詢都會串流至AEP，並與訪客的設定檔建立關聯（透過匿名訪客的ECID或已知訪客的已驗證身分識別）。 載入包含建議表面的頁面時，[!DNL Web SDK]會透過[!DNL Edge Network]向AJO要求決策評估。 決策引擎會根據選擇策略評估訪客的行為設定檔、套用排名邏輯、篩選出不合格專案（已購買、無庫存），並傳回建議專案。

透過程式碼型體驗或Web頻道介面，在頁面上轉譯建議。 轉譯可以是轉盤、格線、單一專案Widget，或推薦範本中定義的任何自訂配置。 曝光和點按事件會自動追蹤回AEP以進行效能報告。

**主要考量事項：**

- Edge決策需要合併原則在Edge上為作用中
- 建議延遲取決於[!DNL Edge Network]回應時間（單一範圍要求小於500毫秒的SLA）
- 匿名訪客會收到以工作階段內行為為基礎的建議；已知訪客會從跨工作階段行為記錄中受益
- 沒有行為記錄的冷啟動訪客會收到遞補建議

**優點：**

- 根據工作階段內行為的即時個人化
- 透過[!DNL Edge Network]傳送的次秒推薦傳遞
- 適用於匿名和已知訪客
- 自動曝光和點選追蹤
- 新建議不需要重新載入頁面

**限制：**

- Edge設定檔存放區包含完整設定檔屬性的子集
- 具有許多設定檔屬性的複雜排名模型可能需要中心端評估
- 需要具有行為事件追蹤的[!DNL Web SDK]部署

**Experience League：**

- [使用Edge Decisioning API傳遞優惠方案](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/edge-decisioning-api)
- [網頁SDK概觀](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)

### 選項B：行動應用程式建議

**最適合：**&#x200B;應用程式內產品建議、個人化內容摘要、通知導向建議，以及行動商務體驗。

**運作方式：**

使用者與應用程式互動時，會透過[!DNL Mobile SDK]收集行為訊號。 產品檢視、內容互動、搜尋和購買都會串流至AEP。 載入包含建議表面的畫面時，[!DNL Mobile SDK]會要求決策評估。 Recommendations會透過應用程式內訊息、內容卡片或行動應用程式內的程式碼型體驗來傳送。

內容卡特別適合行動應用程式的建議使用案例，因為它們會持續提供使用者方便瀏覽的摘要式體驗。 應用程式內訊息可用於由特定行為觸發的情境式建議（例如，將專案新增至購物車後顯示補充產品）。

**主要考量事項：**

- [!DNL Mobile SDK]必須設定相關互動的行為事件追蹤
- 內容卡提供永續性的建議表面；應用程式內訊息是暫時的
- 離線行為追蹤需要SDK佇列管理才能提交延遲的事件
- 應用程式商店更新週期會影響建議演算變更的部署速度

**優點：**

- 透過順暢的應用程式整合式建議呈現，提供原生行動體驗
- 內容卡提供持續性、可瀏覽的建議摘要
- 應用程式內訊息可啟用情境式、行為觸發的建議
- 運用裝置層級訊號（位置、應用程式使用模式）來增強關聯性

**限制：**

- 需要[!DNL Mobile SDK]整合和應用程式開發資源
- 轉譯變更需要應用程式更新（除非使用程式碼型體驗搭配伺服器導向版面）
- 離線期間會在行為訊號收集中建立間隙

**Experience League：**

- [行動SDK概觀](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [設定推播通知頻道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### 選項C：以電子郵件傳送行為建議

**最適合：**&#x200B;電子郵件行銷活動中的產品建議 — 放棄瀏覽含有已檢視產品建議的電子郵件、購買後交叉銷售電子郵件、定期「為您挑選」摘要，以及含有個人化產品建議的重新參與電子郵件。

**運作方式：**

從先前工作階段累積的行為設定檔資料會在電子郵件傳送時間或轉譯時間通知建議選擇。 會定義受眾來鎖定適當的收件者（例如瀏覽但未購買的訪客、最近購買的客戶）。 行銷活動或歷程已設定為傳送包含建議位置的電子郵件。 在傳送時，AJO Decisioning會根據選擇策略評估每個收件者的行為設定檔，並將建議專案注入電子郵件內容。

此選項取決於累積的行為歷程記錄，而非工作階段中的訊號。 計算屬性（類別相關性分數、最近產品檢視、購買頻率）可大幅改善電子郵件的建議品質，因為它們會將行為記錄擷取到選取策略可有效評估的設定檔層級訊號。

**主要考量事項：**

- 電子郵件建議是在傳送時評估，而不是在開啟時評估 — 傳送時的行為設定檔狀態會決定建議
- 強烈建議使用運算屬性來改善排名品質
- 電子郵件轉譯限制（無JavaScript、有限的CSS）會限制建議顯示格式
- 需要已設定及驗證的電子郵件通道表面

**優點：**

- 利用各工作階段的完整行為記錄，以實現更深入的個人化
- 整合現有的行銷活動和歷程工作流程
- 對無法使用Web/應用程式接觸點的重新參與和回饋方案有效
- 可以在單一電子郵件中包含多個建議版位

**限制：**

- 建議在傳送時為靜態 — 在電子郵件開啟時不會更新
- 電子郵件轉譯限制會限制建議顯示格式
- 需要對象評估和行銷活動/歷程協調基礎結構
- 由於額外的相依性（頻道設定、對象定義、行銷活動執行），導致更高的實作複雜性

**Experience League：**

- [建立電子郵件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [在訊息中傳遞優惠方案](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

### 選項比較

下表總結了實施選項之間的主要差異。

| 條件 | 選項A：Web即時 | 選項B：行動應用程式 | 選項C：電子郵件行為 |
| --- | --- | --- | --- |
| 最適合 | 網頁建議（PDP、首頁、類別） | 應用程式內建議和內容摘要 | 以電子郵件傳送行銷活動與產品推薦 |
| 行為訊號來源 | 工作階段內+跨工作階段([!DNL Web SDK]) | 應用程式內互動([!DNL Mobile SDK]) | 累積行為記錄（設定檔） |
| 建議延遲 | 子秒([!DNL Edge Network]) | 子秒([!DNL Edge Network]) | 傳送時（中心端評估） |
| 訪客型別 | 匿名和已知 | 已知（應用程式使用者） | 已知（電子郵件收件者） |
| 複雜性 | 中 | Medium — 高 | 高 |
| 管道相依性 | [!DNL Web SDK]，程式碼型體驗介面 | [!DNL Mobile SDK]，應用程式內/內容卡表面 | 電子郵件頻道介面、對象、行銷活動/歷程 |
| 需要 | [!DNL Web SDK]部署，Edge合併原則 | [!DNL Mobile SDK]部署，Edge合併原則 | 電子郵件表面、對象定義、行銷活動設定 |

### 選擇正確的選項

請遵循下列指引，針對您的情況選取最佳選項：

- 如果您的主要目標是網站上的即時產品推薦，請&#x200B;**從選項A**&#x200B;開始。 這是最常見的起點，以最低的實作複雜度提供立即的價值。
- **如果您的行動應用程式為主要參與管道，而且應用程式內推薦可帶來有意義的轉換提升度，請選擇選項B**。 選項B可使用相同的選取策略與料號目錄，與選項A並行執行。
- **當您想要將行為建議擴充至電子郵件行銷活動時，請新增選項C**。 這通常位於選項A或B上方，使用相同的專案目錄和選取策略，但搭配電子郵件特定的轉譯範本和以對象為基礎的鎖定目標。
- **結合選項A + C**&#x200B;以取得常見模式：對活躍訪客的即時Web建議，以及對離開但未轉換的訪客的放棄瀏覽或購買後電子郵件建議。

## 實作階段

以下階段會引導您完成行為建議的端對端實作。

### 階段1：設定行為事件綱要和資料收集

**應用程式函式：** AEP：資料模型與準備(F2)、AEP：資料來源與集合(F3)

此階段會建立XDM結構描述、資料集和資料收集機制，用於擷取行為訊號和專案目錄資料。 此資料基礎是所有建議邏輯所依賴的。

#### 決定：行為事件結構描述設計

哪些行為訊號應該驅動建議？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 僅限產品檢視 | 簡單的交叉銷售/追加銷售建議 | 最低的實作工作量；有限的訊號深度 |
| 產品檢視+購買 | 具有購買排除和交叉銷售邏輯的建議 | 適度付出；啟用「排除已購買」篩選條件 |
| 完整行為套裝（檢視、購買、加入購物車、搜尋、內容互動） | 具有多訊號排名的複雜建議 | 最高的訊號品質；需要完整的[!DNL Web SDK]/[!DNL Mobile SDK]檢測 |

#### 決定：專案目錄擷取方法

產品或內容目錄將如何內嵌至AEP？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 透過來源聯結器批次內嵌 | 定期更新目錄（每日/每週） | 設定更簡單；目錄變更未即時反映 |
| 串流擷取 | 目錄需要近乎即時的更新（價格變更、可用性） | 較複雜；可確保建議反映目前的詳細目錄 |
| 手動/API上傳 | 不常變更的小型目錄 | 最簡單的設定；無法針對大型或動態目錄進行擴充 |

**UI導覽：**&#x200B;資料管理>結構描述>建立結構描述；資料收集>資料串流>新增資料串流

**金鑰組態詳細資料：**

- 體驗事件結構描述必須在事件裝載中包含產品/專案識別碼（SKU、產品ID、內容ID）
- 專案目錄結構描述應包括用於篩選和排名的屬性：類別、價格、影像URL、可用性狀態、標籤
- 資料流必須為Edge決策啟用[!DNL Adobe Journey Optimizer]服務
- [!DNL Web SDK] `sendEvent`呼叫必須包含對應至XDM商務欄位的產品互動資料

**Experience League檔案：**

- [XDM系統概覽](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [結構描述組合基本面](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)
- [網頁SDK概觀](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [設定資料串流](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [定義兩個結構描述之間的關係](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/relationship-api)

### 階段2：設定身分和設定檔

**應用程式函式：** AEP：身分和設定檔組態(F4)

此階段會設定身分名稱空間、主要身分指定和合併原則，以確保行為訊號正確與訪客設定檔相關聯，並可用於即時建議傳送。

#### 決定：Edge決定的合併原則

建議使用案例需要即時Edge評估嗎？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 在Edge合併原則上啟用 | 選項A和B （網頁和行動即時建議） | 需要次秒推薦傳遞；每個沙箱只有一個Edge合併原則 |
| 標準合併原則（不在Edge上） | 僅限選項C （在傳送時評估的電子郵件建議） | 足以進行集線器端評估；不會耗用Edge合併原則槽 |

#### 決定：匿名與已知訪客身分識別

應如何處理來自匿名訪客的行為訊號？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 僅限ECID （匿名） | 主要根據工作階段中行為的匿名訪客建議 | 設定更簡單；除非訪客驗證，否則沒有跨工作階段連續性 |
| ECID +已驗證的身分（CRM ID、電子郵件） | 具有身分拼接的已知訪客的跨工作階段建議 | 更豐富的行為設定檔；需要驗證流程 |
| 兩者皆具有身分圖表連結 | 具有身分拼接的完整匿名 — 已知歷程 | 最全面；需要身分連結規則設定 |

**UI導覽：**&#x200B;身分>身分名稱空間；設定檔>合併原則

**金鑰組態詳細資料：**

- [!DNL Web SDK]和[!DNL Mobile SDK]已預先設定並自動使用ECID名稱空間
- 必須為已驗證的身分建立自訂身分名稱空間（CRM ID、熟客ID）
- 體驗事件方案上的主要身分應該是網頁/行動行為事件的ECID
- 合併原則必須使用私用裝置圖表進行裝置間的身分拼接

**Experience League檔案：**

- [Identity Service總覽](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [身分名稱空間概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/identity/features/namespaces)
- [合併原則概觀](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [身分識別圖連結規則](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/identity-linking-logic)

### 階段3：設定料號型錄與選取策略

**應用程式函式：** AJO： Decisioning

此階段會設定專案目錄（決定專案）、結合行為訊號與專案屬性進行排名的選擇策略、排除不合格專案的篩選規則，以及冷啟動設定檔的遞補建議。

#### 決定：專案目錄範圍

有哪些專案可供建議？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 產品目錄（電子商務） | 推薦實體或數位產品以供購買 | 料號屬性包括價格、類別、可用性、影像 |
| 內容目錄（媒體/出版） | 推薦文章、影片或教育內容 | 專案屬性包括主題、作者、發佈日期、內容型別 |
| 混合式目錄 | 推薦產品和內容 | 需要統一專案結構描述來容納這兩種型別 |

#### 決定：排名方法

合格專案應如何排名以決定最佳建議？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 公式型排名 | 清除排名的商業邏輯（例如，以類別相關性分數乘以專案熱門度來排序） | 透明、可稽核的排名；需要定義的排名公式 |
| AI排名（自動最佳化） | 機器學習應根據轉換資料決定最佳排名 | 模型訓練需要至少1,000個轉換事件；較不透明 |
| 優先順序（手動） | 簡單、手動組織的建議順序 | 最容易設定；無法因應個人行為 |

#### 決定：篩選規則

建議中應該排除哪些專案？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 排除已購買的專案 | 交叉銷售和探索建議 | 需要行為設定檔中的購買記錄 |
| 排除無庫存專案 | 使用動態詳細目錄的電子商務 | 需要即時或近乎即時目錄更新 |
| 排除先前已解除的專案 | 使用者可拒絕建議的內容建議 | 需要在行為事件中進行解除追蹤 |
| 類別範圍篩選 | 建議僅限於特定類別 | 使用專案屬性進行篩選 |

#### 決定：冷啟動策略

沒有行為記錄的新訪客應該顯示什麼？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 熱門專案（全球暢銷商品） | 一般用途遞補 | 維護簡單；未個人化 |
| 類別特定的熱門專案 | 訪客已到達類別頁面 | 內容相關的遞補；需要頁面內容 |
| 已組織的編輯精選 | 品牌想要編輯控制冷啟動體驗 | 需要手動組織和更新 |
| 趨勢專案（時間加權人氣） | 反映目前趨勢的動態遞補內容 | 需要趨勢訊號計算 |

**UI導覽：** [!DNL Journey Optimizer] >元件>決定管理>決定；[!DNL Journey Optimizer] >元件>決定管理>優惠；[!DNL Journey Optimizer] >元件>決定管理>位置

**金鑰組態詳細資料：**

- 使用屬性（類別、價格、影像URL、標籤）建立代表目錄中每個產品或內容專案的決定專案
- 定義結合專案目錄篩選與行為排名邏輯的選擇策略
- 設定排名模型 — 公式式運算式可參考設定檔屬性（例如，來自計算屬性的類別相關性分數）
- 建立作為冷啟動設定檔之預設建議的遞補選件/專案
- 使用邏輯分組的集合限定詞（標籤）將專案組織到集合中
- 在選擇策略內設定篩選規則，以強制執行商業規則（排除已購買、庫存）

**Experience League檔案：**

- [決策管理概觀](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [建立產品建議放置環境](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [建立決定規則](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [建立個人化優惠方案](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [建立後備產品建議](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [建立集合](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [建立決定](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [排名策略](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### 階段4：設定通道和介面

**應用程式函式：** AJO：頻道設定

此階段會設定要在其中轉譯建議的傳送介面。 此設定因實施選項而異。

#### 決定：傳遞表面型別

建議將顯示在何處？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 程式碼型體驗（網頁） | 使用自訂轉譯的網頁上的建議Widget | 呈現時的最大彈性；需要前端開發 |
| Web管道表面 | 標準網頁個人化表面 | 使用AJO Web設計工具；比程式碼型更不靈活 |
| 應用程式內訊息 | 應用程式行為觸發的情境式建議 | 短暫；互動或移除後消失 |
| 內容卡（行動） | 行動應用程式中的永續性建議摘要 | 持續到使用者執行動作為止；可瀏覽的摘要體驗 |
| 電子郵件 | 內嵌在電子郵件行銷活動中的產品推薦 | 傳送時為靜態；受電子郵件轉譯限制 |

**選項差異的位置：**

選項A （Web即時建議）的&#x200B;**：**
設定程式碼型體驗表面或Web頻道表面。 程式碼型體驗為自訂建議轉譯（輪播、格線、專案卡片）提供最大的彈性。 表面URI可識別建議出現在頁面上的位置。

選項B的&#x200B;**（行動應用程式建議）：**
設定應用程式內訊息或內容卡介面。 建議將內容卡用於持續性建議摘要。 應用程式內訊息適用於情境式、行為觸發的建議。

選項C （電子郵件行為建議）的&#x200B;**：**
使用子網域委派、IP集區指派和寄件者設定來設定電子郵件通道表面。 確認已驗證介面的傳遞能力。

**UI導覽：**&#x200B;管理>管道>管道表面>建立表面

**Experience League檔案：**

- [設定頻道介面](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [開始使用電子郵件設定](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [設定簡訊頻道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [設定推播通知頻道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### 階段5：設定內容與傳送

**應用程式函式：** AJO：訊息製作

此階段會定義建議演算範本，用以控制向訪客顯示建議專案的方式。 這包括專案版面設計、提取專案屬性（名稱、影像、價格、連結）的個人化運算式，以及整體建議體驗設計。

#### 決定：建議顯示格式

應如何呈現建議專案？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 輪播（水準捲動） | 垂直空間有限的首頁或類別頁面 | 熟悉的UX模式；以簡潔的空間顯示多個專案 |
| 格線（多列） | 具有充裕空間的專用建議區段 | 一次顯示更多專案；適用於「為您推薦」的部分 |
| 單一專案Widget | 特定頁面位置的內容推薦（例如側欄） | 佔用空間最少；高影響力的位置 |
| 內嵌電子郵件區塊 | 內嵌在電子郵件內文中的建議 | 受限於電子郵件HTML/CSS限制；通常為2-4個專案 |

#### 決定：要顯示的建議數量

每個位置應該傳回多少個決定專案？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 3-4個專案 | 標準建議Widget | 平衡關聯性與視覺密度 |
| 6-8個專案 | 具有捲動或格線版面配置的輪播 | 訪客有更多的選項；需要足夠的目錄深度 |
| 1個專案 | 內容單一產品推薦 | 最高的關聯性影響；最簡單的呈現 |
| 10個以上的專案 | 摘要樣式的建議體驗 | 大量內容的使用案例（媒體、發佈） |

**選項差異的位置：**

選項A （Web即時建議）的&#x200B;**：**
使用程式碼型體驗範本來設計推薦呈現。 使用HTML/CSS/JavaScript建立轉盤、格線或Widget版面。 Personalization運算式會參考決定回應屬性（專案名稱、影像URL、價格、產品URL）。 曝光和點選追蹤由[!DNL Web SDK]自動處理。

選項B的&#x200B;**（行動應用程式建議）：**
使用專案顯示邏輯設定內容卡片或應用程式內訊息範本。 使用行動應用程式原生轉譯的JSON型內容結構。 包含每個建議專案的深層連結。

選項C （電子郵件行為建議）的&#x200B;**：**
使用電子郵件Designer設計電子郵件內容。 使用決策支援的內容區塊插入建議版位。 設定電子郵件範本中專案屬性的個人化運算式。 主旨列個人化可參考排名最前的建議專案。

**使用者介面導覽：**&#x200B;內容管理>內容範本；行銷活動/歷程>編輯內容>電子郵件Designer

**金鑰組態詳細資料：**

- 每個建議位置都必須參考階段3中建立的決策
- Personalization運算式使用Handlebars語法來呈現專案屬性
- 針對Web：設定程式碼型體驗以呼叫決定並呈現回應
- 電子郵件：將決定內嵌於行銷活動或歷程的電子郵件動作中
- 使用具有已知行為記錄的測試設定檔來預覽建議

**Experience League檔案：**

- [設計電子郵件內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [新增個人化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization語法](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [動態內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [在訊息中傳遞優惠方案](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [預覽和測試您的內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)
- [使用內容範本](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)

### 階段6：設定對象範圍設定和行銷活動/歷程（僅限選項C）

**應用程式函式：** RT-CDP：對象評估、AJO：行銷活動執行或Journey Orchestration

針對電子郵件式建議（選項C），此階段會定義目標對象，並設定傳送建議電子郵件的行銷活動或歷程。 選項A和B會略過此階段，因為建議會在頁面/畫面載入時即時傳送。

#### 決定：對象評估方法

應如何評估建議電子郵件的目標對象？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 批次評估 | 排程建議電子郵件行銷活動（每日、每週摘要） | 可預測的傳送時間；在傳送前評估對象 |
| 串流評估 | 事件觸發的建議電子郵件（放棄的瀏覽、購買後） | 近乎即時的對象資格；與Journey Orchestration配對 |

#### 決定：傳遞機制

電子郵件應該透過行銷活動或歷程傳遞？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 排程的行銷活動 | 一次性或循環建議電子郵件爆炸給定義的對象 | 設定更簡單；批次對象評估和傳送 |
| 有受眾進入的歷程 | 受眾資格觸發的持續建議電子郵件 | 啟用多步驟流程（例如，建議電子郵件後跟提醒） |
| 事件觸發的歷程 | 特定事件觸發的建議電子郵件（瀏覽放棄、購買） | 即時觸發；需要事件型歷程專案 |

**UI導覽：**&#x200B;客戶>受眾>建立受眾>建置規則；行銷活動>建立行銷活動；歷程>建立歷程

**金鑰組態詳細資料：**

- 使用參考行為歷程記錄的區段規則運算式定義目標對象（例如「過去7天內檢視過產品但未購買」）
- 使用參考階段4頻道介面的電子郵件動作設定行銷活動或歷程
- 將階段3的決定內嵌在電子郵件內容中
- 設定排程和頻率規則以避免過度傳訊

**Experience League檔案：**

- [區段產生器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [串流區段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [行銷活動即時報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)

### 階段7：設定報告和最佳化

**應用程式功能：** AJO：報表與效能分析，S5：報表與分析

此階段會建立建議點進、轉換和收入量度的效能監視。 這會建立報告基礎架構，以評估建議成效並找出最佳化機會。

#### 決定：報告深度

需要何種層級的報表分析？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 僅限AJO原生報表 | 基本建議效能監視 | 快速設定；僅限AJO追蹤量度 |
| AJO + [!DNL Customer Journey Analytics]整合 | 跨管道建議影響分析和收入歸因 | 需要[!DNL Customer Journey Analytics]連線和資料檢視；提供更深入的見解 |
| 使用自訂儀表板的完整[!DNL Customer Journey Analytics]工作區 | 具有專案層級、區段層級和曲面層級分析的持續最佳化程式 | 最全面；需要[!DNL Customer Journey Analytics]專業知識及設定 |

**UI導覽：**&#x200B;行銷活動>選取行銷活動>所有時間報告；歷程>選取歷程>所有時間報告；[!DNL Customer Journey Analytics] >專案>建立新專案

**金鑰組態詳細資料：**

- 檢閱AJO行銷活動和歷程報告的傳遞和參與量度
- 針對[!DNL Customer Journey Analytics]整合，建立包含AJO體驗事件資料集的連線（訊息回饋、電子郵件追蹤、決策）
- 使用建議專用維度（專案名稱、專案類別、建議表面）和量度（曝光數、點按數、轉換、收入），建立[!DNL Customer Journey Analytics]資料檢視
- 為建議CTR、轉換率和每次曝光收入建立計算量度
- 建立[!DNL Customer Journey Analytics]工作區面板，比較跨介面、區段和時段的建議效能

**Experience League檔案：**

- [行銷活動全域報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [歷程全域報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [使用Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [建立或編輯連線](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/create-connection)
- [建立或編輯資料檢視](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [Analysis Workspace概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [計算量度概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)

## 實施考量

在實施之前和期間，請檢閱下列護欄、陷阱、最佳實務和權衡。

### 護欄和限制

- 每個沙箱最多10,000個核准的個人化優惠（決定專案） — [決定管理護欄](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- 每個決定最多30個位置
- 每個決定請求最多30個集合範圍
- 優惠方案傳送回應時間SLA：對於單一範圍Edge請求，P95時間小於500毫秒
- AI排名模型需要至少1,000個轉換事件才能訓練
- 在高輸送量的情況下，選件上限計數器可能會延遲數秒
- Edge決定僅限於邊緣設定檔存放區中可用的設定檔屬性
- 每個沙箱在Edge上只能有一個作用中的合併原則 — [設定檔護欄](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- 每個沙箱最多25個使用中的計算屬性 — [計算屬性護欄](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- 每個沙箱最多4,000個區段定義 — [分段護欄](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- 串流擷取：每個HTTP連線每秒最多20,000筆記錄 — [擷取護欄](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)

### 常見陷阱

- **決定僅傳回遞補專案：**&#x200B;確認個人化決定專案在其有效日期範圍內已核准，且適用性規則符合訪客的設定檔屬性。 檢查是否尚未達到上限限制。
- **Edge傳遞傳回空白的個人化：**&#x200B;請確定資料串流已設定為啟用[!DNL Adobe Journey Optimizer]服務，且[!DNL Web SDK]請求中的決定範圍格式正確。
- **未套用排名公式：**&#x200B;請確認公式語法有效，並參考可存取的設定檔屬性。 公式錯誤會自動回復到優先順序排名。
- **過時建議：**&#x200B;如果行為事件資料未即時流動，建議將會以過時的行為設定檔為基礎。 驗證[!DNL Web SDK]或[!DNL Mobile SDK]是否正在串流事件。
- **冷啟動備援比率太高：**&#x200B;如果大部分的訪客收到備援建議，請考慮使用內容訊號（目前頁面類別、轉介來源）豐富冷啟動策略，而非僅依賴行為記錄。
- **未在頁面上轉譯Recommendations：**&#x200B;請確認程式碼型體驗表面URI符合頁面URL模式，以及[!DNL Web SDK]是否正確要求及轉譯決定回應。
- **建議中遺漏的目錄專案：**&#x200B;請確定所有目錄專案都已擷取為決定專案、以正確的集合限定詞標籤，並包含在選取策略所參考的適當集合中。

### 最佳實務

- 在投資於AI排名模型之前，先從使用計算屬性（類別相關性、互動造訪間隔）的公式排名模型開始。 以公式為基礎的模型是透明的、可稽核的，並且可提供實體基準線以進行比較。
- 從第一天開始實施曝光和點選追蹤。 如果沒有互動資料，AI排名模型就無法訓練，而且您無法評估建議成效。
- 為不同的建議表面（首頁、PDP、電子郵件）建立個別的選擇策略，而不是在任何地方重複使用單一策略。 不同的表面會提供不同的使用者意圖。
- 使用計算屬性將行為歷史記錄擷取到排名訊號中。 原始事件資料太精細，無法進行有效的公式式排名；彙總訊號（例如「類別相關性分數」和「上次購買間隔天數」）會更有效率。
- 將備援建議與個人化建議分開測試。 確保遞補專案是高品質、符合品牌需求的預設值，可為新訪客提供良好的體驗。
- 監控冷啟動備援率，作為關鍵健康狀態量度。 隨時間遞減的遞補率表示行為涵蓋範圍不斷擴大。
- 對於電子郵件建議，排程會在行為設定檔最完整的時段傳送（例如，在尖峰瀏覽時段後傳送，而不是在其期間）。

### 權衡決定

應根據您的特定需求評估下列取捨。

#### 即時訊號與累積歷程記錄的比較

工作階段中的行為訊號提供立即的相關性，但深度有限。 累積的行為記錄提供了深度，但可能會過時。 這些來源之間的平衡會影響建議品質。

- **選項A偏好：**&#x200B;即時訊號提供立即關聯性，輔以已知訪客的累積歷程記錄
- **選項C偏好：**&#x200B;僅累計歷程記錄，因為電子郵件是以非同步方式傳送
- **建議：**&#x200B;針對網頁和行動裝置（選項A、B），將工作階段中的訊號與衍生自歷史行為的運算屬性結合。 對於電子郵件（選項C），請大量投資計算屬性，這些屬性將行為歷史記錄彙總為可操作的設定檔層級訊號。

#### 公式型與AI排名模型

公式式排名是透明且立即的。 AI排名模型會自動調整，但需要訓練資料，且排名決策的可見度較低。

- **以公式為基礎的偏好：**&#x200B;透明度、可稽核性、立即部署，以及對排名邏輯的精細商業控制
- **AI排名優惠：**&#x200B;自動最佳化、發現不明顯的模式，並減少手動調整工作
- **建議：**&#x200B;從公式式排名開始，以建立效能基準並累積轉換資料。 當您有足夠的訓練資料（1,000多個轉換事件），並且想要最佳化超過手動公式調整所能達到的程度，就可以轉換到AI排名模型。

#### 建議涵蓋範圍與關聯性

擴大專案目錄和放寬篩選規則，可增加收到個人化建議的請求百分比，但可能會降低每個建議的關聯性。

- **高涵蓋範圍偏好：**&#x200B;將看到個人化建議的訪客數量最大化；當主要目標是參與時非常有用
- **高關聯性偏好：**&#x200B;只顯示高關聯專案，即使這表示更多訪客會看到遞補建議；當主要目標是轉換時很有用
- **建議：**&#x200B;從適度篩選開始（排除已購買的專案、無庫存的專案），並監視遞補率和轉換率。 只有在轉換資料支援時，才應收緊篩選規則。

#### Personalization深度與實作複雜性的比較

更豐富的行為訊號和更複雜的排名模型可改善建議品質，但會增加實作的複雜度和維護負擔。

- **較簡單的實作優點：**&#x200B;更快的價值取得時間、更少的維護、更易於偵錯和反複運算
- **更深入的個人化優點：**&#x200B;更高的轉換提升度、更佳的客戶體驗、競爭差異化
- **建議：**&#x200B;分階段實作。 從產品檢視訊號和公式型排名（階段1）開始。 新增行為擴充的計算屬性（階段2）。 一旦基礎成熟並有足夠的訓練資料可用（第3階段），請評估AI排名模型。

## 相關文件

下列資源提供在此模式中使用的技術和功能的更多詳細資料。

### 決定管理

- [決策管理概觀](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [建立產品建議放置環境](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [建立決定規則](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [建立個人化優惠方案](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [建立後備產品建議](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [建立集合](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [建立集合限定詞](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-tags)
- [建立決定](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [排名策略](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)
- [在訊息中傳遞優惠方案](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [使用Edge Decisioning API傳遞優惠方案](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/edge-decisioning-api)

### 資料收集與網頁/行動SDK

- [網頁SDK概觀](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [安裝Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/install/overview)
- [行動SDK概觀](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [設定資料串流](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Edge Network伺服器API總覽](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)

### XDM和資料模型化

- [XDM系統概覽](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [結構描述組合基本面](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)
- [建立資料集](https://experienceleague.adobe.com/en/docs/experience-platform/catalog/datasets/create)
- [定義兩個結構描述之間的關係](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/relationship-api)

### 身分和設定檔

- [Identity Service總覽](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [身分名稱空間概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/identity/features/namespaces)
- [合併原則概觀](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [即時客戶個人檔案總覽](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)

### 對象和細分

- [Segmentation Service概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [區段產生器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [串流區段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [邊緣分段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)

### 計算的屬性和設定檔擴充

- [計算屬性概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [計算屬性UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/ui)
- [Customer AI概述](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview)

### 管道設定

- [開始使用電子郵件設定](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [設定頻道介面](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [委派子網域](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)

### 訊息製作與個人化

- [設計電子郵件內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [新增個人化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization語法](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [動態內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [使用內容範本](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)

### 報告與分析

- [行銷活動全域報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [歷程全域報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [使用Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [CJA概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Analysis Workspace概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [計算量度概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)

### 資料控管和生命週期

- [資料控管概覽](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [資料使用標籤概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/labels/overview)
- [進階資料生命週期管理概觀](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)
- [資料集有效期](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/ui/dataset-expiration)

### 監視和可觀察性

- [可觀察性深入分析概觀](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)
- [警報概觀](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)

### 護欄

- [Journey Optimizer護欄](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [即時客戶個人檔案護欄](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [擷取護欄](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)
- [Identity Service護欄](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)

### 教學課程與指南

- [來源概觀](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)
- [標籤總覽](https://experienceleague.adobe.com/en/docs/experience-platform/tags/home)
- [同意和偏好設定欄位群組](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)
