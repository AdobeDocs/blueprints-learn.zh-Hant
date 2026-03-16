---
title: Brand Concierge對話體驗
description: 瞭解如何將數位屬性轉換為AI支援、品牌安全的對話體驗，以引導客戶探索。
solution: Experience Platform, Real-Time Customer Data Platform
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '7239'
ht-degree: 0%

---


# Brand Concierge對話體驗

本指南針對使用[!DNL Adobe Brand Concierge]、與[!DNL Adobe Experience Platform] (AEP)和[!DNL Real-Time Customer Data Platform] ([!DNL RT-CDP])整合的AI支援交談體驗，提供完整的實作參考。 它專為需要跨數位資產部署品牌安全對話代理程式的解決方案架構師、行銷技術人員和實作工程師所設計。

它涵蓋部署對話式體驗的所有可行方法，從產品諮詢聊天機器人到完整的網站導覽助理，並提供每個選項選擇時間的指引。 此計畫會處理代理程式設定、品牌控管、內容整合、部署策略、從交談訊號擴充設定檔，以及分析最佳化等問題。

[!DNL Brand Concierge]可讓品牌部署智慧型對話代理程式，瞭解品牌語調、存取核准的產品目錄和內容、根據即時設定檔資料提供個人化建議，以及將意圖和情緒訊號擷取回整合式客戶設定檔。 如此一來，對話式體驗不但能讓人感受到身臨其境的自然感，還能讓組織更加瞭解每位客戶。

## 使用案例概述

組織日益尋求將靜態數位體驗轉換為動態的AI支援對話，以引導客戶進行探索、產品選擇和購買決策。[!DNL Adobe Brand Concierge] 提供協調的交談AI層，位於現有數位屬性上方，由AEP Agent Orchestrator提供技術支援，以解決此問題。

此模式與傳統聊天機器人實作不同，因為其原生與AEP的統一設定檔整合，使用品牌控管護欄來確保每個回應都符合品牌標準，並將對話訊號傳回客戶資料平台，以進行下游個人化和啟用。

目標受眾包括數位體驗團隊、電子商務經理、內容策略師和行銷技術人員，他們需要部署可促進參與、轉換和豐富設定檔的智慧型對話體驗。

## 主要業務目標

此使用案例模式支援下列業務目標。

### 提供個人化的客戶體驗

根據個別偏好設定、行為和生命週期階段量身打造內容、選件和訊息。

**KPI：**&#x200B;參與度、轉換率、客戶滿意度(CSAT)

[深入瞭解如何提供個人化客戶體驗](/help/blueprints/business-objectives/customer-experience/deliver-personalized-customer-experiences.md)

### 改善客戶參與度

增加所有數位和實體接觸點的互動頻率和深度。

**KPI：**&#x200B;參與度、開啟時間（網頁）頁面、開啟率

[進一步瞭解如何提高客戶參與度](/help/blueprints/business-objectives/qualification-sales-b2b/improve-customer-engagement.md)

### 提高轉換率

提高完成所需動作（例如購買、註冊或提交表單）的訪客和潛在客戶的百分比。

**KPI：**&#x200B;轉換率、潛在客戶轉換、每個潛在客戶的成本

[進一步瞭解如何提高轉換率](/help/blueprints/business-objectives/revenue-monetization/increase-conversion-rates.md)

### 贏取新客戶

透過鎖定目標的贏取促銷活動、相似對象和付費媒體最佳化，來擴大客戶基礎。

**KPI：**&#x200B;向上銷售/交叉銷售%、遞增收入、客戶期限值

[進一步瞭解如何取得新客戶](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

## 戰術使用案例範例

以下案例說明此模式在實際中如何套用。

- **產品探索小幫手** — 在產品清單頁面上部署對話式代理程式，根據客戶需求、偏好和預算，詢問合格問題並縮小產品建議範圍
- **引導式比較建議程式** — 協助客戶透過自然對話來並排比較產品，強調與其指定優先順序相關的差異
- **大小與合身禮賓服務** — 使用對話式問答來引導服裝或鞋類購物者選擇大小，減少退貨並提高購買可信度
- **訂閱或計畫選擇器** — 根據使用模式和指定需求，透過個人化建議引導客戶完成服務層級或訂閱計畫選項
- **網站導覽小幫手** — 協助訪客根據自己所述的意圖，尋找相關內容、支援資源或產品類別，降低複雜網站的跳出率
- **購買前諮詢** — 透過針對建議建立的多回合對話，提供高考量的購買指導（例如電子產品、金融產品、保險）
- **忠誠計畫服務人員** — 透過對話式互動，協助忠誠會員發現獎勵、瞭解層級優惠，並尋找兌換機會
- **重新參與交談** — 根據先前的瀏覽記錄或捨棄的購物車專案，主動與再度訪問的訪客進行交談外聯
- **即時代理升級與內容** — 將複雜的查詢順暢地交給即時銷售或支援代理，同時保留完整的交談內容和客戶設定檔資料
- **購買後支援與追加銷售** — 透過對話管道，在購買後提供安裝協助、補充產品建議及滿意度簽到等服務，與客戶互動

## 關鍵績效指標

以下KPI可協助評估此使用案例模式的成功。

| KPI | 說明 | 測量方法 |
| --- | --- | --- |
| 交談參與率 | 啟動及維持交談的訪客百分比 | 已開始交談/符合資格的頁面檢視 |
| 交談完成率 | 達成有意義解析度的交談百分比 | 已完成的交談/交談已開始 |
| 轉換率 | 導致所需動作（購買、註冊、潛在客戶表單）的交談百分比 | 對話的轉換/對話總數 |
| 平均交談深度 | 每個交談的輪次數，表示參與品質 | 每個工作階段的平均訊息計數 |
| 客戶滿意度(CSAT) | 從體驗內回饋意見獲得交談後滿意度分數 | 意見調查回應或向上或向下縮放 |
| 建議接受率 | 已接受或已點按的產品推薦百分比 | 已執行建議/已提供建議 |
| 即時代理程式移交率 | 提升至即時代理的交談百分比 | 移交/對話總數 |
| 設定檔擴充率 | 產生新意圖或偏好設定訊號的交談百分比 | 擴充的設定檔/對話總數 |
| 受交談影響的收入 | [!DNL Brand Concierge]交談進行轉換前的購買收入 | 對話至購買歷程的歸因分析 |
| 解決方案時間 | 從交談開始到解決或移交的平均持續時間 | 跨交談事件的時間戳記分析 |

## 使用案例模式

**Brand Concierge對話體驗**

將數位屬性轉換為AI支援的品牌安全對話體驗，透過自然對話引導客戶探索，利用意圖和情緒訊號豐富設定檔，並提供個人化產品推薦。

**功能鏈：**&#x200B;代理程式設定>品牌控管設定>內容整合>對話式體驗部署>設定檔擴充>分析和最佳化

## 應用程式

以下應用程式可用來實作此使用案例模式。

- **[!DNL Brand Concierge]** — AI支援的對話式體驗應用程式，提供代理程式協調器、Product Advisor Agent、網站顧問代理程式、品牌控管和對話式分析
- **[!DNL Adobe Experience Platform] (AEP)** — 整合的資料基礎，提供對話式訊號的XDM結構描述、身分解析、即時客戶設定檔和資料收集基礎架構
- **[!DNL Real-Time CDP] ([!DNL RT-CDP])** — 客戶資料平台提供個人化對話的即時設定檔查閱、從對話訊號進行對象細分，以及擴充設定檔與意圖和情緒資料

## 基礎函式

下列基本功能必須為此使用案例模式準備就緒。 對於每個函式，狀態會指出它通常是必要的、假設為預先設定或不適用。

| 基礎函式 | 狀態 | 必須準備就緒的專案 | Experience League參考 |
| --- | --- | --- | --- |
| 管理與治理 | 必填 | 已布建[!DNL Brand Concierge]權益的沙箱；為對話式體驗管理員、內容管理員和分析使用者設定的角色；針對包含PII或敏感客戶訊號的對話式資料制定的ABAC原則 | [存取控制總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/access-control/home) |
| 資料模型與準備 | 必填 | 對話事件的XDM結構描述（ExperienceEvent類別具有對話特定欄位群組，可擷取意圖、情緒、產品互動和切換事件）；使用對話偏好設定和意圖屬性擴充的設定檔結構描述；接地建議的產品目錄查詢結構描述 | [XDM系統總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/xdm/home) |
| 資料來源與收集 | 必填 | [!DNL Web SDK]或[!DNL Mobile SDK]已設定將對話事件資料路由到AEP資料集的資料串流；[!DNL Edge Network]整合用於在對話期間即時事件擷取；透過來源聯結器或批次擷取所擷取的產品目錄資料 | [Web SDK 概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/web-sdk/home) |
| 身分和設定檔設定 | 必填 | 設定用於訪客身分識別（匿名ECID、驗證的CRM ID或電子郵件）的身分名稱空間；設定用於對話期間即時設定檔查詢的邊緣啟用的合併原則；用於跨裝置對話持續性的身分連結規則 | [身分識別服務總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/identity/home) |
| 對象定義與細分 | 已假設就位 | 核心交談部署不需要受眾，但個人化交談策略需要受眾（例如，高價值客戶區段接收不同的交談流程）；即時交談個人化建議使用串流或邊緣評估 | [分段服務總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/home) |

## 支援功能

以下功能可擴大此使用案例模式，但不是核心執行的必要功能。

| 支援功能 | 狀態 | 為什麼這很重要 | Experience League參考 |
| --- | --- | --- | --- |
| 計算/衍生屬性建立 | 推薦 | 將對話訊號彙總至設定檔層級屬性（例如，對話總數、產品主要興趣、平均情緒分數），以用於下游細分和個人化 | [計算屬性總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/computed-attributes/overview) |
| 資料生命週期管理 | 推薦 | 設定交談事件資料的保留原則、管理交談記錄和設定檔的同意，以及支援交談記錄檔的隱私權刪除請求 | [進階資料生命週期管理概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-lifecycle/home) |
| 資料使用標籤和實作 | 推薦 | 標示包含PII、情緒或意圖訊號的交談資料欄位；強制執行治理政策，防止敏感交談資料到達未經授權的目的地 | [資料控管概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/home) |
| 監控與可觀察性 | 推薦 | 監視交談事件擷取管道、追蹤設定檔擴充成功率，並警示可能影響交談個人化品質的資料流程失敗 | [可觀察性深入分析概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/observability/home) |
| 報告與分析 | 已包含 | 使用[!DNL Brand Concierge]內建分析和[!DNL CJA]進行跨管道交談影響分析，以分析交談績效、客戶意見回饋、轉換歸因和代理程式效率 | [CJA概觀](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-overview/cja-overview) |

## 應用程式函式

此計畫會從「應用程式功能目錄」中執行下列功能。 函式會對應至實作階段，而非編號步驟。

### [!DNL Brand Concierge]

| 函式 | 實作階段 | 說明 |
| --- | --- | --- |
| 代理程式設定 | 階段1：代理程式組態 | 使用代理程式專業（產品顧問、網站諮詢）和基本行為設定來設定[!DNL Brand Concierge]代理程式協調器 |
| 品牌控管設定 | 第2階段：品牌控管設定 | 定義品牌語調、語調、訊息護欄、核准的內容界限，以及可影響所有對話互動的禁止主題 |
| 內容整合 | 第3階段：內容整合 | 連線品牌核准的內容來源，包括AEM內容、產品目錄、知識庫和其他受信任的資料，以進行接地回應 |
| 產品顧問組態 | 第3階段：內容整合 | 設定Product Advisor Agent以提供個人化產品推薦、引導式比較和品牌一致回應傳遞 |
| 網站建議設定 | 第3階段：內容整合 | 設定網站建議代理程式，根據訪客行為和意圖訊號調整互動，以增強導覽 |
| 對話式體驗部署 | 第4階段：對話式體驗部署 | 跨支援的管道（網頁、行動應用程式、自訂SDK）部署對話式體驗，並支援文字和語音互動 |
| 低程式碼流程管理 | 第4階段：對話式體驗部署 | 讓行銷團隊使用低程式碼設定工具來更新對話語調、流程和內容 |
| 對話式設定檔擴充 | 階段5：設定檔擴充 | 透過對話期間擷取的意圖、情緒、產品相似性和行為訊號，豐富AEP客戶設定檔 |
| Conversational Analytics | 第6階段：分析與最佳化 | 透過內建的Analytics儀表板監控參與量度、客戶意見回饋、轉換資料和交談品質 |
| 即時代理程式移交 | 第4階段：對話式體驗部署 | 設定與現場銷售或支援代理商的無縫交接，同時保留完整的交談內容 |

### [!DNL Real-Time CDP]

| 函式 | 實作階段 | 說明 |
| --- | --- | --- |
| 即時設定檔查閱 | 第4階段：對話式體驗部署 | 存取即時客戶設定檔屬性和區段成員資格，以根據已知的客戶資料個人化對話回應 |
| 輪廓富集 | 階段5：設定檔擴充 | 使用衍生自對話式行為事件（意圖分數、情緒趨勢、產品相似性）的計算屬性豐富設定檔 |
| 對象評估 | 階段5：設定檔擴充 | 根據交談訊號評估對象會籍，以啟用參與交談區段的下游目標定位 |

## 先決條件

開始實作前，必須具備下列專案。

- 組織的[!DNL Adobe Brand Concierge]權益為使用中
- AEP和[!DNL RT-CDP]授權已布建足夠的設定檔和事件磁碟區權益
- 品牌指南檔案可用於定義語音、語調、核准的訊息和禁止的主題
- 為整合準備的產品目錄或內容存放庫（AEM資產、PIM資料或結構化產品摘要）
- 可識別對話式體驗部署的Web屬性，具有SDK整合的技術存取權
- 需要移交時可使用即時代理程式基礎架構（聯絡中心平台、CRM整合）
- 適用於對話式資料擷取和分析的同意管理架構
- 已在目標屬性上部署[!DNL Web SDK]或[!DNL Mobile SDK] （或計畫同時部署）
- 利害關係人在對話範圍上保持一致（僅限產品諮詢、網站導覽或兩者）
- AI支援的對話式資料擷取與使用隱私權與法律審查已完成

## 實作選項

以下小節說明實施此使用案例模式的不同方法。

### 選項A：產品建議程式部署

**最適合：**&#x200B;電子商務和零售組織，專注於引導式產品探索、比較和建議體驗，可促進轉換和平均訂單值。

**運作方式：**

Product Advisor Agent已設定為主要交談專業。 它會連線至產品目錄、瞭解產品屬性和關係，並透過自然對話引導客戶達成個人化建議。 代理程式會使用品牌治理護欄，以確保建議符合業務優先順序（例如，促銷庫存專案、強調有利利潤的產品）。

「產品顧問」會與即時客戶設定檔整合，以存取購買記錄、瀏覽行為和偏好設定資料，根據客戶的設定檔啟用可說明客戶已擁有、先前已考慮或可能需要的建議。 當體驗事件和意圖訊號傳回設定檔供下游使用時，就會擷取交談。

**主要考量事項：**

- 需要結構良好的產品目錄以及豐富的屬性資料，才能提供有效的建議
- 產品資料必須保持最新，以避免推薦無庫存或停產的專案
- 品牌治理必須定義代理商如何處理競爭產品提及和價格比較

**優點：**

- 透過引導式購買轉換，直接推動可衡量的收入影響
- 透過更明智的購買決策降低產品回訪率
- 擷取高價值產品相似性和意圖訊號，用於下游個人化
- 現有電子商務體驗的自然延伸

**限制：**

- 需要持續進行產品目錄維護和同步
- 僅限於以產品為中心的對話；網站導覽問題可能會無法解決
- 有效性取決於目錄資料品質和完整性

**Experience League：**

- [Brand Concierge概觀](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Brand Concierge產品顧問](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/product-advisor)

### 選項B：網站建議部署

**最適合：**&#x200B;擁有複雜數位屬性（媒體、金融服務、醫療保健、技術）的組織，訪客需要導覽協助來尋找相關內容、資源或自助服務工具。

**運作方式：**

網站顧問代理程式已設定為主要交談專業。 它會編制網站內容結構的索引、瞭解頁面關係和內容類別，並根據訪客行為訊號與所述的意圖調整其指引。 當訪客參與時，代理程式會解譯他們的需求，並將他們導向最相關的內容、工具或資源。

網站建議使用即時行為訊號（目前頁面、反向連結來源、導覽路徑）結合設定檔資料（先前的造訪、內容偏好設定、客戶階層），提供內容相關的導覽協助。 這在具有深層內容階層、多個產品線或複雜自助工作流程的網站上特別有用。

**主要考量事項：**

- 需要全面的內容索引，並隨著網站內容變更定期重新抓取
- 在訪客經常費力尋找所需內容且內容廣度的網站上最有效
- 品牌控管應定義範圍界限（代理程式可導覽至哪些網站區域）

**優點：**

- 降低跳出率並改善複雜網站上的內容可發現性
- 擷取顯示內容差距和使用者體驗問題的導覽意圖訊號
- 實作複雜性比Product Advisor低（不需要整合產品目錄）
- 提供訪客正在尋找但找不到之專案的分析深入分析

**限制：**

- 與以產品為重點的交談相比，與收入轉換關係較不直接
- 需要結構良好的內容並定期更新，以取得準確指引
- 隨著網站結構演變，可能需要經常進行重新訓練

**Experience League：**

- [Brand Concierge概觀](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Brand Concierge網站顧問](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/site-advisor)

### 選項C：結合產品顧問+網站建議部署

**最適合：**&#x200B;需要完整對話體驗的組織，涵蓋產品探索和網站導覽，通常是大型零售或B2C品牌，具有豐富的數位屬性和多樣化的訪客意圖。

**運作方式：**

Product Advisor Agent和網站建議代理程式都是在[!DNL Brand Concierge] Orchestrator中設定。 代理程式協調程式使用意圖偵測將對話路由至適當的專業 — 產品相關查詢會傳送至「產品顧問」，而導覽與內容尋找查詢會傳送至「網站建議」。 Orchestrator可管理單一交談中不同專業之間的無縫轉換。

此方法可提供最完整的對話式體驗，處理從「協助我尋找產品」到「我可以在哪裡檢查訂單狀態？」的完整訪客需求。 品牌治理護欄適用於所有專業領域，確保品牌聲音一致，無論對話主題為何。

**主要考量事項：**

- 更高的實作複雜性，需要產品目錄和內容整合
- 專業間的目的路由必須經過適當調整，以避免對話方向錯誤
- 品牌治理設定涵蓋更多產品和導覽內容

**優點：**

- 為訪客提供最完整的對話體驗
- 單一進入點可處理不同的訪客意圖，而不需要個別的介面
- 跨專業化的對話（例如，可導致支援導覽的產品問題）會自然處理
- 從多樣化的交談訊號中擴充最豐富的設定檔

**限制：**

- 最高的實作工作與持續維護作業
- 需要產品目錄和內容團隊之間的協調
- 更複雜的測試和品質保證需求
- 品牌治理設定的參與度更高

**Experience League：**

- [Brand Concierge概觀](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)

### 選項比較

| 條件 | 選項A：產品顧問 | 選項B：網站建議 | 選項C：組合 |
| --- | --- | --- | --- |
| 最適合 | 電子商務、產品導向轉換 | 大量內容的網站、自助式導覽 | 全方位數位體驗 |
| 複雜性 | 中 | 低Medium | 高 |
| 價值實現時間 | 4-6週 | 3-5週 | 6-10週 |
| 收入影響 | 高（直接轉換影響） | Medium （透過參與間接） | 最高（轉換和參與） |
| 內容需求 | 具有豐富屬性的產品目錄 | 網站內容索引 | 產品目錄和內容索引 |
| 輪廓擴充 | 產品相似性、購買意圖 | 導覽意圖，內容偏好設定 | 完整訊號頻譜 |
| 維護工作 | 產品目錄同步 | 內容重新索引 | 兩者皆持續進行 |

### 選擇正確的選項

首先評估您的主要業務目標和數位屬性特性：

1. **如果您的主要目標是推動產品轉換**，而您的數位屬性是以商業為中心，請選擇&#x200B;**選項A （產品顧問）**。 這是零售和電子商務品牌最常見的起點。

2. **如果您的主要目標是改善內容可發現性**，而您的網站具有深層內容階層或複雜的自助工作流程，請選擇&#x200B;**選項B （網站諮詢）**。 這非常適合媒體、金融服務、醫療保健及科技公司。

3. **如果您需要完整的涵蓋範圍**，並且同時具有產品商務和內容導覽需求，請選擇&#x200B;**選項C （合併）**。 考慮從一項專門化開始，並在第一個專門化穩定且最佳化後新增第二項。

建議大多陣列織採用分階段方法：先部署一個專門化、驗證效能並收集經驗教訓，然後展開至組合部署。

## 實作階段

下列階段概述建議的實作順序。

### 階段1：代理程式設定

**應用程式函式：** [!DNL Brand Concierge]：代理程式設定

設定核心[!DNL Brand Concierge]代理程式協調器，包括選取代理程式專業（產品顧問、網站諮詢或兩者）、設定基本代理程式行為，以及建立[!DNL Brand Concierge]與AEP之間的連線，以進行設定檔存取和事件擷取。

#### 決定：代理程式專業化選擇

決定應為此部署啟動哪些代理程式專業。

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 僅限產品顧問 | 以Commerce為中心的部署，鎖定產品的探索和轉換 | 需要產品目錄整合；影響收入的最快途徑 |
| 僅限網站建議 | 以內容和導覽為中心的部署 | 降低整合複雜性；最適合非商業網站 |
| 兩項專業 | 涵蓋各種產品和內容的全方位對話內容 | 複雜度較高；請考慮從一次開始分階段推出 |

#### 決定：交談起始模型

決定如何在數位屬性上開始交談。

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 訪客啟動（被動） | 提供聊天Widget但未主動參與的預設方法 | 降低中斷風險；依賴訪客對聊天選項的瞭解 |
| 主動參與（已觸發） | 代理程式會根據行為訊號來起始對話（例如，延長暫留時間、重複的頁面造訪、購物車猶豫） | 較高的參與率，但如果觸發器太積極，可能會讓訪客感到不快；需要行為觸發器調整 |
| 混合式（被動式，具有內容提示） | 聊天Widget是被動的，但會根據頁面內容或訪客行為顯示內容相關提示 | 平衡的方法；提示指南而不強制參與 |

#### 設定代理程式

**UI導覽：** [!DNL Experience Platform] > AI小幫手> [!DNL Brand Concierge] >代理程式設定

主要設定詳細資料：

- 定義將顯示在對話式介面中的代理程式名稱和說明
- 選取哪個AEP沙箱包含代理程式應存取的客戶設定檔和事件資料
- 設定代理程式協調程式以根據意圖偵測在專業之間路由查詢
- 設定交談工作階段引數（逾時期間、交談長度上限、並行工作階段限制）
- 啟用即時設定檔查詢整合，讓代理程式可以在交談期間存取訪客設定檔資料

**選項差異的位置：**

選項A （產品顧問）的&#x200B;**：**
啟用Product Advisor專業化並設定其與產品目錄資料來源的連線。 設定產品建議引數，包括每個回應的最大建議數、產品屬性顯示偏好設定和比較處理規則。

選項B的&#x200B;**（網站建議）：**
啟用「網站建議」專業化，並設定其與網站內容索引的連線。 設定導覽引數，包括內容範圍邊界、頁面類別處理和深層連結產生偏好設定。

選項C的&#x200B;**（組合）：**
啟用兩種專門化並設定Orchestrator的意圖路由邏輯。 定義路由規則，以決定何時應該由「產品顧問」與「網站建議」處理交談，以及如何在單一交談中管理專業之間的轉換。

**Experience League檔案：**

- [Brand Concierge概觀](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [AI助理總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/ai-assistant/home)
- [AEP Agent Orchestrator](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)

### 第2階段：品牌控管設定

**應用程式函式：** [!DNL Brand Concierge]：品牌治理設定

設定塑造所有對話互動的品牌控管護欄。 這包括品牌語調和語調定義、核准的內容範圍、禁止的主題、回應風格指南和向上呈報規則。 品牌治理可確保每個AI產生的回應都符合品牌標準。

#### 決定：治理嚴格層級

決定品牌控管護欄應限制對話回應的力度。

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 嚴格控管 | 高度法規化的產業（金融服務、醫療保健、保險）或需要精確音調控制的頂級品牌 | 限制對話彈性；可能會導致「我無法協助處理」回應更頻繁；最高品牌安全性 |
| 稽核治理 | 品牌語調一致性很重要，但某些交談彈性可以接受的大多數消費者品牌 | 在品牌安全性與交談自然度之間取得良好的平衡；建議您將大部分實作作為起點 |
| 彈性治理 | 以交談性格和參與度為優先考量的休閒或生活方式品牌 | 最自然的對話感覺；需要更持續監控品牌外的回應 |

#### 決定：主題外處理策略

決定代理程式應如何處理其設定範圍以外的問題。

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 重新導向至範圍 | 代理程式確認問題並重新導向至可協助處理的主題 | 維持參與，但可能會因合理的離主題需求而挫敗訪客 |
| 移交給即時代理程式 | 代理程式提供將訪客與人工代理程式連線以進行主題外問題的功能 | 最佳客戶體驗，但需要即時代理程式基礎架構和人員 |
| 資源使用率正常下降 | 代理程式說明它無法協助處理該主題，並提供相關資源或支援頻道的連結 | 低摩擦備援；不需要即時代理程式可用性 |

#### 設定品牌控管

**UI導覽：** [!DNL Experience Platform] > AI小幫手> [!DNL Brand Concierge] >品牌治理

主要設定詳細資料：

- 定義品牌屬性：品牌名稱、標語、使命、價值以及個人特質，以傳達對話語調
- 設定色調引數：形式等級、幽默容忍、同理心等級和產品推薦的主張性
- 設定核准的內容範圍：代理程式有權討論的主題和明確禁止的主題
- 定義回應格式准則：最大回應長度、使用清單與散文、表情符號原則及連結格式
- 設定向上呈報觸發程式：應自動將交談路由至即時代理程式的條件（例如，投訴偵測、重複的不滿訊號、高價值的客戶識別）
- 設定競爭提及處理：當訪客詢問競爭者產品時，代理程式應如何回應
- 定義免責宣告和法律通知要求：受規管行業的強制披露

**Experience League檔案：**

- [Brand Concierge品牌控管](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [AI助理操作深入分析](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/ai-assistant/home)

### 第3階段：內容整合

**應用程式功能：** [!DNL Brand Concierge]：內容整合、產品顧問組態、網站顧問組態

設定內容來源，以精確且品牌核准的資訊為基礎對話回應。 這包括產品目錄整合、AEM內容連線、知識庫匯入和內容重新整理排程。

#### 決定：產品目錄整合方法

決定應如何將產品資料提供給Product Advisor Agent。 （僅限選項A和C）

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| AEP資料集整合 | 產品目錄已透過來源聯結器內嵌至AEP作為查詢資料集 | 運用現有的資料基礎架構；讓產品資料與設定檔資料保持同步；需要基礎資料模型與收集以包含產品目錄 |
| 直接摘要整合 | 產品目錄存在於PIM或商務平台中，可提供結構化的摘要 | 可提供更多即時詳細目錄和定價資料；需要摘要設定和排程 |
| AEM內容整合 | 產品內容是在AEM中管理的，且應作為權威的產品資料來源 | 最適合以AEM為內容中樞的品牌；確保網頁內容與對話式回應之間的一致性 |

#### 決定：內容重新整理頻率

決定代理程式的內容知識庫更新頻率。

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 即時/近乎即時 | 產品可用性、定價或內容變更頻繁（例如，快閃銷售、庫存敏感零售） | 最高精確度但基礎建設負載較高；對於存貨敏感型建議而言至關重要 |
| 每日重新整理 | 已規劃和排程內容變更（例如編輯行事曆、每週促銷活動） | 在精確度和效能之間取得良好的平衡；適用於大多數的實作 |
| 隨選重新整理 | 內容變更不頻繁，可以在更新發生時手動觸發 | 最低的額外負荷；適用於靜態產品目錄或穩定的內容網站 |

#### 設定內容來源

**UI導覽：** [!DNL Experience Platform] > AI小幫手> [!DNL Brand Concierge] >內容來源

主要設定詳細資料：

- 將產品目錄資料來源與產品名稱、說明、屬性、定價、可用性、影像和類別階層的欄位對應連線
- 設定網站頁面、知識庫文章、常見問題集內容和支援檔案的內容索引
- 設定內容範圍邊界，定義代理可參考和排除的內容
- 設定代理程式找不到相關內容以回答問題時的內容遞補行為
- 設定內容品質規則：包含在回應、引文需求和來源歸因中的最低內容信賴臨界值

**選項差異的位置：**

選項A （產品顧問）的&#x200B;**：**
著重於產品目錄與豐富產品屬性對應的整合。 設定Product Advisor Agent的建議邏輯，包括要建議多少產品、如何處理缺貨專案、如何呈現產品比較，以及如何將客戶設定檔資料（購買記錄、瀏覽行為）併入建議排名。

選項B的&#x200B;**（網站建議）：**
著重於使用頁面階層對應建立網站內容索引。 設定Site Advisory代理程式的導覽邏輯，包括如何解譯訪客意圖、將哪些內容類別設定為優先順序、如何處理模稜兩可的導覽要求，以及如何根據訪客目前的頁面內容和工作階段行為調整建議。

選項C的&#x200B;**（組合）：**
設定產品目錄和網站內容來源。 確保內容路由邏輯將內容正確指派給適當的專門化，且產品內容與網站導覽內容之間的互動參照正確對應。

**Experience League檔案：**

- [Brand Concierge內容設定](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Brand Concierge產品顧問](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/product-advisor)
- [Brand Concierge網站顧問](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/site-advisor)
- [來源概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sources/home)

### 第4階段：對話式體驗部署

**應用程式功能：** [!DNL Brand Concierge]：對話式體驗部署、低程式碼流程管理、即時代理程式移交；[!DNL RT-CDP]：即時設定檔查閱

在目標數位屬性上部署對話式體驗，包括頻道設定、Widget自訂、個人化的設定檔查詢整合、即時代理程式移交規則，以及用於持續內容管理的低程式碼工具。

#### 決定：部署管道

決定應將對話式體驗部署至哪個管道。

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 網頁（內嵌Widget） | 主要Web屬性是主要客戶接觸點 | 最常見的起點；需要[!DNL Web SDK]整合；同時支援匿名與已驗證的訪客 |
| 行動應用程式（SDK整合） | 行動應用程式是重要的客戶參與管道 | 需要[!DNL Mobile SDK]整合；請考慮交談UI的熒幕空間限制 |
| 自訂SDK部署 | 對話式體驗需要內嵌在自訂應用程式、資訊站或非標準數位屬性中 | 最大彈性；需要更多開發工作；適用於店內資訊站或專屬平台 |
| 多頻道部署 | 需要同時跨網頁、行動裝置和其他管道的對話體驗 | 觸及率最高；需要跨管道一致的品牌控管；如有可能，跨管道的交談內容應持續存在 |

#### 決定：交談的Personalization深度

決定代理程式應該使用多少客戶設定檔資料來個人化交談。

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 僅限匿名（工作階段內容） | 隱私權優先方法或當大多數訪客無法識別時 | 僅使用工作階段中的行為訊號；不需要查詢設定檔；適用於匿名產品探索 |
| 設定檔感知（已驗證的訪客） | 訪客通常會登入，並根據歷史記錄新增值提供個人化建議 | 需要透過[!DNL RT-CDP]進行即時設定檔查詢；已知客戶的建議品質大幅提升 |
| Progressive個人化 | 對話期間將匿名與驗證與漸進式設定檔建立混合在一起 | 從工作階段內容開始；當訪客提供資訊或驗證時更加豐富；在隱私權和個人化之間取得平衡 |

#### 決定：即時代理程式移交設定

判斷對話是否應該呈報給現場的代理人員。

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 無移交（僅限自助服務） | AI代理程式可以處理所有預期的交談型別，或即時代理程式無法使用 | 最簡單的部署；可能會讓有複雜需求的訪客感到挫折；適用於低風險、瀏覽產品的情境 |
| 規則型移交 | 特定觸發程式應呈報給即時代理程式（例如，投訴偵測、高價值客戶、複雜查詢） | 可預測的向上呈報行為；需要定義向上呈報規則和觸發器；需要即時代理程式平台整合 |
| 訪客要求的移交 | 訪客可在對話的任何時間點要求即時代理 | 最佳客戶體驗；需要隨時可用的代理程式人員配置或佇列管理；交談內容必須轉移 |

#### 部署對話式體驗

**UI導覽：** [!DNL Experience Platform] > AI小幫手> [!DNL Brand Concierge] >部署

主要設定詳細資料：

- 設定對話式Widget外觀：位置、色彩配置、頭像、歡迎訊息和互動樣式（文字、語音或兩者）
- 與[!DNL Web SDK]或[!DNL Mobile SDK]整合，以進行事件擷取和設定檔解析
- 設定即時設定檔查詢，以存取客戶屬性、區段會籍，以及交談期間的最近活動
- 設定與聯絡中心平台的即時代理程式移交整合，包括內容傳輸通訊協定、佇列路由及代理程式通知
- 啟用低程式碼流程管理工具，讓行銷團隊無需開發人員介入即可更新對話起點、促銷訊息、季節性內容和流程變化
- 設定交談工作階段持續性規則：交談記錄會保留多長時間、交談是否可以跨工作階段繼續，以及跨裝置交談持續性

**Experience League檔案：**

- [Brand Concierge部署](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [網頁SDK概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/web-sdk/home)
- [Edge Network伺服器API總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/edge-network-server-api/overview)
- [設定檔API實體端點](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/api/entities)
- [即時客戶個人檔案總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/home)

### 階段5：設定檔擴充

**應用程式函式：** [!DNL Brand Concierge]：對話式設定檔擴充；[!DNL RT-CDP]：設定檔擴充、對象評估

設定擷取和擴充管道，將對話訊號傳回至AEP統一的客戶設定檔。 包括將交談事件對應至XDM、擷取意圖和情緒訊號、從交談資料建立計算屬性，以及根據交談行為建立對象。

#### 決定：對話式訊號擷取範圍

決定應該擷取哪些對話訊號並寫入客戶設定檔。

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 僅限核心參與訊號 | 最小化的設定檔擴充；擷取交談開始、結束、持續時間和完成狀態 | 最低資料量；足以進行基本分析；有限的個人化值 |
| 意圖和偏好設定訊號 | 擷取推斷的產品興趣、敘述的偏好設定和討論的主題類別 | 高個人化值；中等資料量；最常建議 |
| 完整訊號擷取 | 擷取意圖、情緒、產品互動、建議回應、移交事件和意見反應分數 | 最豐富的設定檔擴充；最高的資料量；啟用進階分析和ML驅動的個人化 |

#### 決定：從交談資料建立對象

決定是否應根據用於下游啟用的對話行為來建立對象。

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 無對話對象 | 對話資料僅用於分析，不用於對象啟用 | 最簡單的方法；如果對話是現有參與管道的補充，則適合 |
| 意圖型對象 | 根據敘述的產品興趣或對話中的導覽意圖建立對象 | 啟用重新定位有興趣但未轉換的訪客；商業價值高 |
| 行為對象 | 根據對話參與模式（例如高參與度、捨棄的對話、重複造訪）建立對象 | 啟用以交談為基礎的歷程協調與跨頻道追蹤 |

#### 設定設定檔擴充

**UI導覽：** [!DNL Experience Platform] >客戶>設定檔>計算屬性（針對衍生訊號）；客戶>對象>建立對象（針對對話對象）

主要設定詳細資料：

- 將對話事件對應至XDM ExperienceEvent結構描述欄位，擷取對話ID、訊息計數、討論的主題、引用的產品、情緒分數和解決狀態
- 設定[!DNL Brand Concierge]設定檔擴充，以將意圖和偏好設定訊號寫入統一設定檔
- 從交談事件資料建立運算屬性：交談總數（期限）、主要產品類別興趣（30天）、平均情緒分數（90天）、交談對購買的轉換率
- 根據下游啟用的對話訊號定義串流或批次對象區段（例如「過去7天內討論產品類別X但未購買的訪客」）
- 透過查詢範例設定檔以確認填入對話屬性來驗證設定檔擴充

**Experience League檔案：**

- [計算屬性概述](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/computed-attributes/overview)
- [計算屬性UI指南](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/computed-attributes/ui)
- [區段產生器UI指南](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/ui/segment-builder)
- [串流區段](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [即時客戶個人檔案總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/home)

### 階段6：分析和最佳化

**應用程式函式：** [!DNL Brand Concierge]：對話式分析

設定Analytics儀表板和報表，以測量對話式體驗效能、識別最佳化商機及追蹤KPI。 其中包括[!DNL Brand Concierge]內建分析、跨頻道交談影響分析的可選[!DNL CJA]整合，以及持續的最佳化工作流程。

#### 決定：分析深度

決定需要何種程度的對話分析。

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 內建[!DNL Brand Concierge]分析 | 只需提供交談數量、參與度、滿意度及轉換的標準報告即可 | 最快啟用；涵蓋核心KPI；有限的跨管道關聯 |
| [!DNL Brand Concierge] + [!DNL CJA]整合 | 需要跨管道分析，才能瞭解交談如何影響更廣泛的客戶歷程 | 需要[!DNL CJA]連線和資料檢視設定；啟用跨交談和其他管道的歸因分析 |
| 完整分析棧疊（[!DNL Brand Concierge] + [!DNL CJA] +自訂儀表板） | 執行層級報表、進階歸因模型，以及從Analytics深入分析建立自訂對象 | 最高的分析能力；需要[!DNL CJA]的專業知識；支援資料導向對話最佳化 |

#### 設定分析和最佳化

**UI導覽：** [!DNL Experience Platform] > AI小幫手> [!DNL Brand Concierge] > Analytics； [!DNL Analytics Platform] > Workspace （適用於[!DNL CJA]）

主要設定詳細資料：

- 檢閱[!DNL Brand Concierge]個內建分析控制面板：交談數量趨勢、參與率、完成率、CSAT分數、建議接受率和移交頻率
- 設定[!DNL CJA]連線以包含用於跨管道分析的對話式事件資料集（如果選擇[!DNL CJA]整合）
- 建立[!DNL CJA]工作區分析以取得交談至轉換歸因，找出與購買行為相關的交談主題
- 設定交談品質監控：追蹤代理程式掙扎的主題、常見的未回答問題以及一段時間內的情緒趨勢
- 定義最佳化工作流程：根據Analytics分析定期審查品牌控管更新、內容重新整理觸發器和交談流程改善的步調

**Experience League檔案：**

- [Brand Concierge分析](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [CJA Analysis Workspace概觀](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/home)
- [建立或編輯CJA連線](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-connections/create-connection)
- [建立或編輯CJA資料檢視](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dataviews/create-dataview)

## 實施考量

以下章節涵蓋實施期間需牢記的護欄、常見陷阱、最佳實務和取捨決定。

### 護欄和限制

- [!DNL Brand Concierge]個交談體驗受AI回應產生率限制的約束；同時交談容量取決於權益層級
- 對話期間的即時設定檔查詢受每個沙箱的設定檔API速率限制約束 — [即時客戶設定檔護欄](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/guardrails)
- 對話事件資料擷取遵循標準AEP串流擷取限制 — [擷取護欄](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/ingestion/guardrails)
- 產品目錄大小和內容索引數量受[!DNL Brand Concierge]個內容整合限制的約束
- 每個沙箱最多可套用25個計算屬性至對話式訊號彙總 — [計算屬性護欄](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/computed-attributes/overview)
- 每個沙箱最多4,000個區段定義適用於對話對象 — [分段護欄](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/guardrails)

### 常見陷阱

- **品牌治理定義不足：**&#x200B;若部署時未進行完整的品牌治理設定，會導致品牌外回應損害客戶信任。 在部署之前，請花大量時間在階段2中定義語氣、界限和升級規則。
- **過時的產品目錄資料：**&#x200B;產品顧問根據過時的存貨、定價或可用性資料提出的建議，會挫敗客戶並削弱信心。 使用驗證檢查建立自動內容重新整理管道。
- **過度積極主動的參與觸發程式：**&#x200B;過於積極設定行為觸發程式（例如，在頁面上3秒後觸發交談）會惹惱訪客，並提高跳出率。 從保守的觸發器開始，並根據參與資料進行調整。
- **忽略匿名訪客體驗：**&#x200B;只將個人化集中在已驗證的訪客上，會忽略大部分流量。 設計對話流程，使用工作階段內行為訊號為匿名訪客提供價值。
- **略過設定檔擴充組態：**&#x200B;部署對話時不會將訊號擷取回設定檔，會浪費寶貴的意圖和偏好設定資料。 設定設定檔擴充與部署同時進行，而非事後考量。
- **忽略即時代理程式移交體驗：**&#x200B;較差的移交體驗（遺失的內容、重複的問題、漫長的等待時間）會破壞整體的對話體驗，而不只是完全不提供移交體驗。 在啟動前測試完整的端對端移交流程。

### 最佳實務

- 從單一代理程式專業化（「產品顧問」或「網站建議」）開始，在建立基準效能後展開。
- 在設定護欄之前，與行銷、法律和客戶體驗利害關係人舉辦品牌治理工作坊。
- 使用漸進式個人化：透過工作階段內容型回應開始對話，並在訪客提供資訊或進行驗證時深化個人化。
- 使用低程式碼流程管理工具對交談起始者、提示和建議簡報格式實作A/B測試。
- 排程定期（每週或每兩週）的交談分析審查，以找出內容差距、常見失敗點和最佳化機會。
- 在對話分析和品牌控管更新之間建立回饋迴路 — 使用對話資料來調整語氣、新增核准的主題並調整向上呈報規則。
- 監控對話情緒趨勢，作為產品問題、網站問題或品牌認知轉變的預警系統。
- 設計交談流程，自然擷取豐富設定檔的訊號，而不會讓互動感覺像是在提問。

### 權衡決定

>[!NOTE]
>下列權衡決定應根據您組織的特定需求和限制進行評估。

**交談個人化深度與隱私權簡易性的比較**

更深入的設定檔整合可讓您進行更個人化且有效的交談，但會增加資料收集的複雜性、同意要求及隱私權法規遵循負擔。

- **深入的個人化優點：**&#x200B;轉換率較高、建議品質較佳、個人檔案更豐富，以及更吸引回頭客戶的對話
- **簡化隱私權的好處：**&#x200B;部署更快速、同意管理更簡單、監管風險更低，以及隱私權優先的品牌定位
- **建議：**&#x200B;從適用於匿名訪客的漸進式個人化開始，並為已驗證的工作階段新增設定檔式個人化。 這可在所有識別層級提供價值，同時確保隱私權合規性易於管理。 針對符合現有同意架構的對話式設定檔實作同意擷取。

**品牌控管嚴格性與對話自然性**

嚴格的品牌控管護欄可確保每個回應都符合品牌標準，但過於僵化的限制讓對話感覺像機械人一樣並減少參與度。

- **嚴格的治理偏好：**&#x200B;品牌安全、法規遵循、一致的訊息和可預測的代理程式行為
- **彈性治理偏好：**&#x200B;自然的交談流程、更高的參與度、更佳的客戶滿意度，以及處理更多查詢的能力
- **建議：**&#x200B;從適度治理開始，並根據交談分析而收緊或放鬆。 監視「我無法協助處理」回應的速率，以作為過度限制的指標。 使用低程式碼流程管理工具，無需開發人員介入即可快速迭代治理設定。

**即時內容重新整理與系統效能**

即時內容同步可確保代理程式一律擁有最新的產品和內容資料，但持續重新整理會消耗更多基礎建設資源，並可能造成延遲。

- **即時重新整理的好處：**&#x200B;庫存敏感建議、時間敏感促銷和快速變更內容的正確性
- **排程的重新整理優點：**&#x200B;系統穩定性、可預測的資源消耗，以及較低的基礎建設成本
- **建議：**&#x200B;使用每日內容重新整理作為預設值，僅針對庫存可用性及定價資料進行近乎即時的重新整理，這些資料會嚴重影響客戶體驗。 監視內容正確性度量，以判斷重新整理頻率是否足夠。

**完整的訊號擷取與資料管理負荷**

擷取每個對話訊號可提供最豐富的設定檔擴充和分析，但會增加資料量、儲存成本和治理複雜性。

- **完整訊號擷取偏好：**&#x200B;進階分析、ML模型訓練、完整的設定檔擴充，以及最大下游個人化值
- **選擇性擷取優點：**&#x200B;降低儲存成本、簡化資料控管、加快設定檔查詢效能，以及更輕鬆遵循資料最小化原則
- **建議：**&#x200B;開始使用意圖和偏好設定訊號擷取（中間位置），並在驗證其他資料建立可測量的下游值之後才展開至完整訊號擷取。 將資料集到期原則套用至對話式事件資料，以管理儲存空間的成長。

## 相關文件

以下資源提供實施此使用案例模式的其他資訊。

**[!DNL Brand Concierge]**

- [Brand Concierge概觀](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Brand Concierge產品顧問](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/product-advisor)
- [Brand Concierge網站顧問](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/site-advisor)
- [AI助理總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/ai-assistant/home)

**[!DNL Adobe Experience Platform]**

- [AEP概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/landing/home)
- [XDM系統概覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/xdm/home)
- [結構描述組合基本面](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/xdm/schema/composition)
- [即時客戶個人檔案總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/home)

**資料收集與整合**

- [網頁SDK概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/web-sdk/home)
- [行動SDK概觀](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [設定資料串流](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/datastreams/configure)
- [Edge Network伺服器API總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/edge-network-server-api/overview)
- [來源概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sources/home)

**身分和設定檔**

- [Identity Service總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/identity/home)
- [身分名稱空間概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/identity/features/namespaces)
- [合併原則概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/merge-policies/overview)
- [計算屬性概述](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/computed-attributes/overview)

**對象和細分**

- [Segmentation Service概述](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/home)
- [區段產生器UI指南](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/ui/segment-builder)
- [串流區段](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/methods/streaming-segmentation)

**資料控管和隱私權**

- [資料控管概覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/home)
- [同意和偏好設定欄位群組](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/xdm/field-groups/profile/consents)
- [Privacy Service概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/privacy/home)
- [進階資料生命週期管理概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-lifecycle/home)

**監視和可觀察性**

- [可觀察性深入分析概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/observability/home)
- [警報概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/observability/alerts/overview)

**分析和報告**

- [CJA概觀](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-overview/cja-overview)
- [CJA連線總覽](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-connections/overview)
- [CJA資料檢視總覽](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dataviews/data-views)
- [Analysis Workspace概觀](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/home)

**護欄**

- [即時客戶個人檔案護欄](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/guardrails)
- [擷取護欄](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/ingestion/guardrails)
- [分段護欄](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/guardrails)
