---
title: B2B Audience Activation
description: 瞭解如何跨網路、電子郵件和廣告頻道啟用以帳戶為基礎的B2B受眾。
solution: Real-Time Customer Data Platform
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '7567'
ht-degree: 0%

---


# B2B對象啟用

本指南提供使用[!DNL Adobe Real-Time Customer Data Platform] ([!DNL RT-CDP]) B2B edition啟用以帳戶為基礎的B2B對象的完整實作參考。 它專為需要跨網路、電子郵件、廣告和CRM頻道建立、評估及啟用帳戶層級受眾的解決方案架構師、行銷技術人員和實施工程師所設計。

它涵蓋了從帳戶設定檔統一到對象評估及啟用，再到特定B2B目的地（例如[!DNL Marketo Engage]、[!DNL LinkedIn]和CRM系統）的完整生命週期。 我們提供所有可行的實施方法，以及權衡和決定指引，協助您為組織選擇正確的路徑。

## 使用案例概述

B2B行銷團隊需要在帳戶層級（而非個人層級）鎖定和啟用對象。 不同於B2C受眾啟用，鎖定目標是單一消費者個人檔案，B2B受眾啟用需要瞭解人們與其所屬帳戶之間的關係，根據帳戶層級的屬性並結合個人層級的參與訊號來評估受眾成員資格，並將這些受眾傳送至支援帳戶型鎖定目標的目的地。

[!DNL RT-CDP] B2B edition利用帳戶、商機和行銷活動的專用XDM類別，以及對應個人與帳戶關係的B2B身分解析，來擴充標準[!DNL Real-Time Customer Data Platform]。 這可讓行銷人員建立帳戶對象，結合與這些帳戶相關聯之人員的家庭資料（產業、收入、員工人數）、技術資料（技術棧疊、產品使用）和行為資料（網站造訪、電子郵件參與、事件出勤率）。

已啟用的帳戶對象在整個需求產生funnel中的主要使用案例：在[!DNL LinkedIn]上的funnel最上層認知行銷活動以及顯示廣告、[!DNL Marketo Engage]中的funnel中段培育計畫，以及透過CRM整合的底層funnel銷售啟用。 帳戶隱藏對象可藉由排除現有客戶、已關閉的遺失帳戶或已處於活躍銷售週期的帳戶，來防止浪費的支出。

## 主要業務目標

此使用案例模式支援下列業務目標。

### 增加銷售機會開發

透過表單、事件、內容和多管道參與，為銷售管道產生更多合格銷售機會。

**KPI：**&#x200B;潛在客戶、每個潛在客戶的成本、潛在客戶轉換

[進一步瞭解如何增加銷售機會開發](/help/blueprints/business-objectives/acquisition-growth/increase-lead-generation.md)

### 改善銷售機會資格和轉換

透過評分、培育及個人化的後續追蹤，提高銷售機會品質並加速管道進度。

**KPI：**&#x200B;潛在客戶轉換、潛在客戶/潛在客戶轉換、效率

[進一步瞭解如何改善銷售機會資格和轉換](/help/blueprints/business-objectives/qualification-sales-b2b/improve-lead-qualification-conversion.md)

### 贏取新客戶

透過鎖定目標的贏取促銷活動、相似對象和付費媒體最佳化，來擴大客戶基礎。

**KPI：**&#x200B;新客戶、客戶贏取成本、潛在客戶/潛在客戶轉換

[進一步瞭解如何取得新客戶](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

### 最佳化行銷支出和ROI

透過更好的目標定位、歸因、對象抑制和預算分配，改善行銷投資報酬。

**KPI：**&#x200B;成本節省、客戶贏取成本、遞增收入

## 戰術使用案例範例

以下案例說明此模式在實際中如何套用。

- **在[!DNL LinkedIn]**&#x200B;上以帳戶為基礎的廣告 — 使用從[!DNL RT-CDP] B2B edition啟用的帳戶清單，將符合您理想客戶設定檔(ICP)的帳戶與贊助內容和[!DNL LinkedIn]上的InMail行銷活動鎖定在目標
- **[!DNL Marketo Engage]nurture program targeting** — 啟用帳戶對象至[!DNL Marketo Engage]，以根據帳戶層級的資格條件將相關的銷售機會和聯絡人註冊到目標的nurture資料流
- **CRM帳戶清單同步處理** — 將合格的帳戶清單推送至[!DNL Salesforce]或[!DNL Microsoft Dynamics]，以便銷售團隊能見度、地區指派及外站潛在客戶工作流程
- **付費媒體的帳戶隱藏** — 從付費贏取行銷活動中，隱藏現有客戶、已結束贏取帳戶，或處於有效銷售週期的帳戶，以減少浪費的支出
- **意圖型帳戶目標定位** — 在帳戶層級結合第三方意圖訊號與第一方參與資料，以識別並啟用市場內帳戶的對象
- **向現有帳戶進行產品交叉銷售** — 使用一條產品線而非另一條產品線來建立帳戶的對象，然後針對交叉銷售行銷活動啟用電子郵件和廣告管道
- **活動和網路研討會鎖定目標** — 啟用廣告和電子郵件通道的帳戶對象，以推動目標帳戶的事件註冊
- **競爭取代行銷活動** — 使用競爭者產品並透過廣告和電子郵件頻道啟用量身打造訊息的目標帳戶
- **階層式帳戶參與** — 根據彙總的個人層級活動，將帳戶細分為參與層級（高、中、低），並為每個層級啟用差異化行銷活動
- **合作夥伴共同行銷對象** — 透過雲端儲存空間目的地，與通路合作夥伴或共同行銷計畫共用帳戶對象區段

## 關鍵績效指標

以下KPI可協助評估此使用案例模式的成功。

| KPI | 說明 | 測量方法 |
| --- | --- | --- |
| 帳戶觸及 | 透過啟用通道達到的目標帳戶數量 | 追蹤每個目的地啟用的不重複帳戶 |
| 帳戶參與率 | 顯示參與訊號的已啟動帳戶百分比 | 衡量彙總至帳戶的個人層級參與度 |
| 管道影響 | 歸因到帳戶型啟用行銷活動的收入管道 | 追蹤從已啟用的帳戶對象建立的商機 |
| 每個參與帳戶的成本 | 行銷支出除以顯示參與度的帳戶數量 | 跨廣告和電子郵件頻道成本計算 |
| 潛在客戶轉換率 | 已啟動科目中轉換為商機的潛在客戶百分比 | 追蹤啟用的受眾的銷售線索到商機的轉換 |
| 對象隱藏省錢 | 透過從付費行銷活動中隱藏不符合資格的帳戶來避免成本 | 從隱藏對象測量支出減少 |
| 帳戶涵蓋範圍 | 啟用的受眾涵蓋的可定址市場(TAM)總數百分比 | 比較已啟用的帳戶與總ICP宇宙 |

## 使用案例模式

**B2B對象啟用**

在網頁、電子郵件和廣告頻道中啟用以帳戶為基礎的B2B對象。

**功能鏈：**&#x200B;帳戶設定檔擴充>帳戶對象評估>目的地設定> Audience Activation >監視

## 應用程式

以下應用程式可用來實作此使用案例模式。

- **[!DNL Real-Time CDP]B2B edition** — 帳戶設定檔統一、B2B身分解析、帳戶對象評估、B2B專屬目的地設定和帳戶對象啟用的核心平台
- **[!DNL Adobe Experience Platform](AEP)** — B2B XDM資料模型化、從CRM和行銷自動化來源擷取資料、身分服務和控管的基礎基礎架構
- **[!DNL Marketo Engage]** — 由啟用的帳戶對象提供的潛在客戶培養方案、評分和行銷活動執行的主要B2B行銷自動化目的地

## 基礎函式

下列基本功能必須為此使用案例模式準備就緒。 對於每個函式，狀態會指出它通常是必要的、假設為預先設定或不適用。

| 基礎函式 | 狀態 | 必須準備就緒的專案 | Experience League參考 |
| --- | --- | --- | --- |
| 管理與治理 | 必填 | 已布建[!DNL RT-CDP]個B2B edition的沙箱。 為B2B資料管理、對象建立和目的地啟用設定的角色。 如果帳戶資料包含受限制的欄位，則已實施ABAC原則。 | [沙箱總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sandbox/home)，[存取控制總覽](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| 資料模型與準備 | 必填 | 使用XDM商業帳戶、XDM商業機會、XDM商業活動和XDM個人資料類別設定的B2B XDM方案。 套用至帳戶屬性、人員 — 帳戶關係和機會資料的B2B欄位群組。 為每個B2B實體建立和啟用設定檔的資料集。 在帳戶、人員、機會和行銷活動實體之間定義的結構描述關係。 | 在Real-Time CDP中[XDM系統總覽](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)，[B2B結構描述](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b) |
| 資料來源與收集 | 必填 | Source聯結器已設定為CRM ([!DNL Salesforce]， [!DNL Microsoft Dynamics])和行銷自動化([!DNL Marketo Engage])以擷取帳戶、人員、商機和行銷活動資料。 批次或串流擷取管道作用中。 「資料準備」對應已設定為將來源資料轉換為B2B XDM結構描述。 | [來源總覽](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)，[Marketo Engage聯結器](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo) |
| 身分和設定檔設定 | 必填 | 針對帳戶識別碼（帳戶ID、CRM帳戶ID）和人員識別碼（電子郵件、CRM聯絡人ID、Marketo銷售機會ID）設定的B2B身分名稱空間。 透過B2B身分解析解析的個人與帳戶關係。 為帳戶設定檔統一設定的合併原則。 | [身分識別服務總覽](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)，[Real-Time CDP的B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/overview#rtcdp-b2b) |
| 對象定義與細分 | 必填 | 使用帳戶屬性、人員屬性和活動資料建立的帳戶層級對象定義。 為帳戶對象設定的評估排程。 定義用來排除不符合資格的帳戶的隱藏對象。 | [細分服務總覽](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)，[帳戶對象](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/types/account-audiences) |

## 支援功能

以下功能可擴大此使用案例模式，但不是核心執行的必要功能。

| 支援功能 | 狀態 | 為什麼這很重要 | Experience League參考 |
| --- | --- | --- | --- |
| 計算/衍生屬性建立 | 推薦 | 帳戶層級的彙總參與分數、期限值和活動量度可改善對象精確度。 計算屬性可將個人層級事件（電子郵件開啟、網頁造訪、內容下載）彙總至帳戶層級，以用於區段。 | [計算屬性總覽](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| 資料生命週期管理 | 推薦 | B2B資料保留原則可確保清除過時的帳戶和機會資料。 B2B聯絡人的同意管理可確保遵守電子郵件行銷法規。 資料集到期原則會防止累積過期的CRM同步資料。 | [進階資料生命週期管理概觀](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| 資料使用標籤和實作 | 已包含 | B2B帳戶資料通常包含合約限制（收入數字、來自第三方提供者的員工計數）。 資料使用標籤可防止將受限制的帳戶屬性啟用至未經授權的目的地。 治理原則可確保在啟用期間適當地處理連絡人記錄的PII欄位。 | [資料控管概觀](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home) |
| 監控與可觀察性 | 已包含 | 監視CRM和[!DNL Marketo Engage]來源聯結器資料流可確保帳戶資料保持最新。 目的地啟用監視確認對象已成功傳遞至[!DNL LinkedIn]、[!DNL Marketo]和CRM目標。 警報規則會攔截會導致過時帳戶資料的內嵌失敗。 | [警示概述](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)，[監視目的地資料流](https://experienceleague.adobe.com/en/docs/experience-platform/dataflows/ui/monitor-destinations) |
| 報告與分析 | 推薦 | [!DNL CJA] B2B edition提供帳戶層級的分析，包括對象觸及率、參與和管道影響。 帳戶型歸因有助於評估啟用行銷活動對機會進展和收入的影響。 | [CJA概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) |

## 應用程式函式

此計畫會從「應用程式功能目錄」中執行下列功能。 函式會對應至實作階段，而非編號步驟。

### [!DNL Real-Time CDP] B2B edition ([!DNL RT-CDP] B2B)

| 函式 | 實作階段 | 說明 |
| --- | --- | --- |
| 帳戶設定檔統一 | 階段1：帳戶設定檔擴充 | 使用B2B XDM結構描述類別將CRM、行銷自動化和第三方來源的帳戶資料整合到統一的帳戶設定檔中 |
| B2B身分解析 | 階段1：帳戶設定檔擴充 | 使用主要識別碼解決人員與帳戶的關係，將聯絡人和銷售機會對應至其關聯帳戶 |
| 帳戶對象評估 | 第2階段：帳戶對象評估 | 結合帳戶屬性、個人屬性和個人活動資料，以評估帳戶層級區段會籍 |
| 帳戶目的地設定 | 階段3：目的地組態 | 使用帳戶層級欄位對應來設定與B2B特定目的地（[!DNL Marketo Engage]、[!DNL LinkedIn]、CRM、雲端儲存空間）的連線 |
| 帳戶Audience Activation | 第4階段：Audience Activation | 將基於帳戶的對象發佈到已設定的目的地，以進行目標定位、隱藏或CRM同步 |
| [!DNL Marketo Engage]整合 | 階段3：目的地組態 | 使用原生B2B來源和目的地聯結器，設定與[!DNL Marketo Engage]的雙向資料流程 |
| B2B資料控管 | 第5階段：控管與監控 | 跨B2B帳戶資料啟用強制執行資料使用原則和同意，以防止未經授權的資料洩漏 |

### [!DNL Real-Time CDP] ([!DNL RT-CDP]) — 標準函式

| 函式 | 實作階段 | 說明 |
| --- | --- | --- |
| 對象評估 | 第2階段：帳戶對象評估 | 帳戶對象的基礎評估引擎，支援帳戶層級區段定義的批次評估 |
| 目的地設定 | 階段3：目的地組態 | B2B特定目的地設定所使用的核心目的地連線基礎架構 |
| Audience Activation | 第4階段：Audience Activation | 帳戶對象啟用所使用的核心啟用資料流基礎架構 |
| 同意與治理實施 | 第5階段：控管與監控 | 在啟動時強制執行同意偏好設定和資料使用原則 |

## 先決條件

開始實作前請先完成下列作業。

- [ ] [!DNL RT-CDP] B2B edition授權已布建並在組織上啟用
- [ ] CRM系統（[!DNL Salesforce]或[!DNL Microsoft Dynamics]）可使用來源聯結器設定的API認證進行存取
- [ 使用[!DNL Marketo]作為目的地時，] [!DNL Marketo Engage]執行個體已布建API存取（Munchkin ID、使用者端ID、使用者端密碼）
- [ 使用[!DNL LinkedIn]作為目的地時，具有相符對象功能的] [!DNL LinkedIn]行銷活動管理員帳戶
- [ 使用帳戶、人員、機會和行銷活動類別建立的]個B2B XDM結構描述(F2)
- [ 已設定]個Source聯結器，並主動擷取CRM和行銷自動化資料(F3)
- [ ]個人與帳戶身分關係已解析且帳戶設定檔已統一(F4)
- [ ]針對對象定義議定的帳戶命名慣例和分類法
- [ 針對帳戶層級資料敏感度分類定義的]資料治理原則

## 實作選項

以下選項說明實作此使用案例模式的不同方法。 檢閱每個選項，並選取最符合您需求的選項。

### 選項A：將受眾啟動串流至[!DNL Marketo Engage]

**最適合：**&#x200B;使用[!DNL Marketo Engage]作為主要B2B行銷自動化平台的組織，需要近乎即時的對象成員資格更新以觸發Nurture方案、更新潛在客戶分數，或修改行銷活動成員資格，因為帳戶符合資格或不符合資格。

**運作方式：**

此選項使用[!DNL RT-CDP]中的原生[!DNL Marketo Engage]目的地聯結器，將帳戶對象會籍變更直接串流到[!DNL Marketo Engage]。 當帳戶符合或退出對象區段時，[!DNL Marketo]中的關聯銷售機會和聯絡人會以區段成員資格屬性更新。[!DNL Marketo] 智慧型行銷活動就可以根據這些成員資格變更來觸發。

[!DNL Marketo Engage]目的地是串流目的地，這表示對象會籍變更會在發生時以遞增方式傳送，而非以排程批次傳送。 對於需要回應帳戶資格變更的行銷活動，這可提供更快速的動作時間。 欄位對應會將[!DNL RT-CDP]設定檔屬性連線至[!DNL Marketo]銷售機會/聯絡人欄位，以從[!DNL RT-CDP]的帳戶層級資料擴充[!DNL Marketo]記錄。

**主要考量事項：**

- 需要具有API存取權的有效[!DNL Marketo Engage]訂閱
- 串流啟用會傳送增量更新，而非完整受眾快照
- [!DNL Marketo]中的人員層級記錄已更新，而非直接更新帳戶層級記錄
- [!DNL Marketo]個智慧行銷活動必須設定為對區段會籍欄位更新採取行動

**優點：**

- [!DNL Marketo]中的幾近即時的對象會籍更新
- 原生雙向聯結器簡化了整合
- 增量更新將資料傳輸量減至最低
- [!DNL Marketo]可以根據對象變更立即觸發nurture計畫

**限制：**

- 限製為[!DNL Marketo Engage]作為啟用目標
- 串流評估資格限制適用於基礎受眾定義
- 需要在[!DNL RT-CDP]帳戶對象與[!DNL Marketo]潛在客戶/聯絡人記錄之間對應
- 可能需要複雜的[!DNL Marketo]程式邏輯，才能將人員層級的更新轉換為帳戶層級的動作

**Experience League：**

- [Marketo Engage目的地](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/adobe/marketo-engage)
- [對Marketo Engage目的地啟用對象](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/adobe/marketo-engage#activate)

### 選項B：批次啟用廣告平台的對象

**最適合：**&#x200B;在[!DNL LinkedIn]、顯示網路或其他廣告平台上以帳戶為基礎的廣告行銷活動，每日對象重新整理已足夠，主要目標是帳戶層級的觸及率和知名度，而非即時回應。

**運作方式：**

此選項會以排定的批次步調，將帳戶對象啟用至廣告平台目的地（[!DNL LinkedIn]個相符對象、[!DNL Google]個客戶相符對象、[!DNL Facebook]個自訂對象或[!DNL The Trade Desk]）。 啟用資料流會匯出帳戶對象成員，其中包含廣告平台用來比對其使用者群的對應身分欄位（通常是相關聯絡人的雜湊電子郵件地址）。

具體來說，針對[!DNL LinkedIn]，[!DNL LinkedIn]已比對對象目的地除了接受電子郵件比對外，還接受公司名稱和網域比對，以啟用真正的帳戶層級鎖定目標。 其他廣告平台通常要求與合格帳戶相關聯的聯絡人提供個人層級的識別碼（電子郵件、電話）。

批次啟動以可設定的排程執行（每天、每6小時等） 和會根據目的地型別匯出完整受眾快照或增量變更。 此方法非常適合持續性認知宣傳活動，其對象新鮮度需求是以小時而非分鐘測量。

**主要考量事項：**

- 對象新鮮度取決於批次排程（通常是每日）
- Advertising平台有其本身的符合率限制
- [!DNL LinkedIn]支援帳戶層級比對；其他平台需要人員層級識別碼
- 匯出檔案格式和身分要求會因目的地而異

**優點：**

- 同時支援多個廣告平台
- 批次處理能有效處理大量受眾
- 帳戶隱藏對象可減少浪費的廣告支出
- [!DNL LinkedIn]個相符的對象可啟用原生帳戶層級的鎖定目標

**限制：**

- 對象更新不是即時的；延遲取決於批次排程
- 匹配率因平台和可用的身分欄位而異
- 有些平台不支援真正的帳戶層級比對，僅支援人員層級
- 每個廣告平台需要個別的目的地設定

**Experience League：**

- [LinkedIn符合的對象目的地](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/social/linkedin)
- [Google Customer Match目的地](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/advertising/google-customer-match)
- [目的地目錄](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)

### 選項C：以檔案為基礎的雲端儲存啟用

**最適合：**&#x200B;需要在下游使用帳戶對象時具有最大彈性的組織，包括CRM匯入、資料倉儲擴充、合作夥伴資料共用，或是偏好檔案式移交的自訂整合。

**運作方式：**

此選項會依排程步調，將帳戶對象匯出為CSV、JSON或Parquet檔案至雲端儲存空間目標([!DNL Amazon S3]、[!DNL Azure Blob Storage]、[!DNL Google Cloud Storage]、SFTP)。 匯出包括帳戶屬性、關聯連絡人的個人層級欄位，以及對象成員資格中繼資料。 下游系統透過自己的匯入程式使用這些檔案。

檔案式啟動可提供對匯出格式、欄位選擇和排程的最大控制權。 它支援完整匯出（每次執行的完整對象快照）和增量匯出（僅自上次執行以來的變更）。 當目標系統沒有原生[!DNL RT-CDP]目的地聯結器，或當組織需要在將資料載入目標系統之前預先處理或轉換資料時，通常會使用此方法。

**主要考量事項：**

- 需要雲端儲存基礎結構（[!DNL S3]、[!DNL Azure Blob]、[!DNL GCS]或SFTP）
- 必須建置和維護下游匯入程式
- 檔案格式(CSV、JSON、Parquet)必須符合下游系統需求
- 匯出排程必須符合下游處理期間

**優點：**

- 以最大彈性使用受眾資料
- 支援任何可讀取檔案的下游系統
- 完整控制匯出格式、欄位和排程
- 可以從單一匯出為多個下游消費者提供服務
- 支援完整和增量匯出模式

**限制：**

- 所有選項的最高延遲（僅限批次）
- 需要建置和維護下游匯入工作流程
- 無原生整合 — 需要額外的開發工作
- 檔案管理（清理、封存）必須單獨處理

**Experience League：**

- [Amazon S3目的地](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/cloud-storage/amazon-s3)
- [Azure Blob儲存體目的地](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/cloud-storage/azure-blob)
- [對批次目的地啟用對象](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/api/connect-activate-batch-destinations)

### 選項D：串流啟用CRM系統

**最適合：**&#x200B;銷售與行銷協調使用案例，其中帳戶資格變更必須近乎即時地反映在CRM （[!DNL Salesforce]或[!DNL Dynamics]）中，才能顯示銷售團隊可見度、地區指派更新或自動化銷售工作流程。

**運作方式：**

此選項使用串流目的地聯結器([!DNL Salesforce] CRM， [!DNL Microsoft Dynamics])將帳戶對象會籍變更直接推送至CRM帳戶或連絡人記錄。 當帳戶符合或退出對象時，CRM記錄會以指出區段成員資格的自訂欄位更新。 然後，銷售團隊可以根據這些欄位建立CRM報表、檢視和警報。

當對象成員資格發生變更時，串流聯結器會傳送增量更新。 欄位對應會將[!DNL RT-CDP]帳戶和人員屬性連線至CRM欄位，以使用[!DNL RT-CDP]的統一資料擴充CRM記錄。 此方法可關閉行銷情報（帳戶資格）與銷售執行（CRM工作流程）之間的回圈。

**主要考量事項：**

- 需要具有適當寫入許可權的CRM API存取權
- 必須建立CRM自訂欄位，才能接收對象成員資格資料
- 串流磁碟區必須在CRM API速率限制內
- CRM工作流程自動化必須設定為對欄位更新採取行動

**優點：**

- 提供近乎即時CRM更新，讓銷售團隊一覽無遺
- 啟用由對象變更觸發的自動化CRM工作流程
- 使用[!DNL RT-CDP]的整合帳戶資料豐富CRM記錄
- 支援帳戶層級和連絡人層級的欄位更新

**限制：**

- CRM API速率限制可能會限制大量更新
- 需要CRM自訂（自訂欄位、工作流程）
- 僅限於[!DNL Salesforce]和[!DNL Microsoft Dynamics]作為原生聯結器
- 串流評估限制適用於基礎對象

**Experience League：**

- [Salesforce CRM目的地](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/crm/salesforce)
- [Microsoft Dynamics 365目的地](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/crm/microsoft-dynamics-365)

### 選項比較

下表比較每個實作選項的主要特性。

| 條件 | 選項A： [!DNL Marketo]串流 | 選項B：Advertising批次 | 選項C：雲端儲存空間 | 選項D：CRM串流 |
| --- | --- | --- | --- | --- |
| 最適合 | Nurture計畫啟用 | 帳戶型廣告 | 具彈性的下游整合 | 銷售與行銷的一致性 |
| 複雜性 | 低 | 中 | Medium — 高 | 中 |
| 延遲 | 近乎即時（分鐘） | 批次（小時） | 批次（小時） | 近乎即時（分鐘） |
| 彈性 | 低（僅限[!DNL Marketo]） | Medium （廣告平台） | 高（任何下游系統） | 低（僅限CRM） |
| 需要 | [!DNL Marketo Engage]授權 | Advertising平台帳戶 | 雲端儲存基礎結構 | CRM API存取 |
| 帳戶層級目標定位 | 透過個人記錄 | 僅[!DNL LinkedIn] （其他人層級） | 可設定 | 透過帳戶/連絡人記錄 |
| 維護工作 | 低 | 低Medium | 高 | 中 |

### 選擇正確的選項

使用下列決定指引來選取正確的啟用方法：

1. **如果您的主要目標是B2B潛在客戶培養，而且您使用[!DNL Marketo Engage]**，請選擇[選項A]。原生串流聯結器為行銷自動化工作流程提供最快的動作時間。

2. **如果您的主要目標是透過廣告以帳戶為基礎的認知和需求產生**，請選擇選項B。[!DNL LinkedIn] 相符的「對象」可提供最強的帳戶層級鎖定目標。 使用其他廣告平台以擴大觸及範圍。

3. **如果您需要將帳戶對象饋送至沒有原生[!DNL RT-CDP]聯結器的系統**，或者如果您需要最大程度地控制資料格式和下游處理，請選擇[選項C]。這也是合作夥伴資料共用或資料倉儲擴充的最佳選擇。

4. **如果您的主要目標是銷售賦權和CRM對符合行銷資格的帳戶的可見度**，請選擇選項D。這可透過以幾近即時的方式更新CRM記錄，關閉行銷與銷售交接回圈。

大部分B2B組織將同時實作多個選項，例如Option A （適用於Nurture程式）、 Option B （適用於[!DNL LinkedIn]廣告）和Option D （適用於CRM同步處理）。 這些選項並非互斥；相同的帳戶對象可同時啟用至多個目的地。

## 實作階段

以下階段說明實作此使用案例模式的逐步程式。

### 階段1：帳戶設定檔擴充

此階段透過合併CRM、行銷自動化和第三方來源的資料，建立統一的帳戶設定檔。

**應用程式函式：** [!DNL RT-CDP] B2B：帳戶設定檔統一，[!DNL RT-CDP] B2B： B2B身分解析

**您要設定的專案：**&#x200B;此階段會合併CRM、行銷自動化和協力廠商來源的資料，以建立統一的帳戶設定檔。 B2B身分解析會對應個人與帳戶的關係，以便個人層級的參與資料（電子郵件開啟、網頁造訪、內容下載）可以彙總，並用於帳戶層級的對象評估。 此階段的基礎函式F2、F3和F4必須已經到位。

此階段中的&#x200B;**決定點：**

>[!NOTE]
>**決定：帳戶識別碼策略**
>
>哪個識別碼可當作各系統的主要帳戶金鑰？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| CRM帳戶ID （例如[!DNL Salesforce]帳戶ID） | CRM是帳戶的記錄系統 | 最常見的方法。 確保[!DNL RT-CDP]與CRM對齊。 要求所有來源系統參考相同的CRM帳戶ID。 |
>| 自訂帳戶ID | 多個CRM執行個體或專有帳戶主機 | 來源系統ID和標準帳戶ID之間需要對應層。 更具彈性，但增加複雜性。 |
>| DUNS號碼或網域 | 第三方資料擴充是主要帳戶來源 | 當第一方資料提供者為主要來源時，就相當實用。 可能需要網域型解析度的模糊比對。 |

>[!NOTE]
>**決定：個人與帳戶關係模型**
>
>和帳戶相關聯的人員（銷售機會、聯絡人）為何？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 一對一（每個人都屬於一個帳戶） | 簡單B2B模型，具備乾淨的CRM資料 | 直截了當的解決方法。 最常見於中端市場B2B。 |
>| 多對多（人員可隸屬於多個帳戶） | 複雜的企業關係、顧問或合作夥伴網路 | [!DNL RT-CDP] B2B edition原生支援此功能。 增加對象複雜性，但準確反映真實世界的關係。 |

**使用者介面導覽：**&#x200B;平台>設定檔>瀏覽（驗證統一的帳戶設定檔）

**金鑰組態詳細資料：**

- 確認F2已提供B2B XDM結構描述（XDM商業帳戶、XDM商業個人帳戶）
- 確認CRM和[!DNL Marketo]來源聯結器正在從F3主動擷取帳戶和人員資料
- 驗證在F4的身分圖表中，人員與帳戶的關係是否已解析
- 瀏覽範例帳戶設定檔以檢閱帳戶設定檔完整性

**Experience League檔案：**

- [Real-Time CDP B2B edition概觀](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/overview#rtcdp-b2b)
- [Real-Time CDP中的B2B結構描述](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [Marketo Engage聯結器](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
- [Salesforce聯結器](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/crm/salesforce)

### 第2階段：帳戶對象評估

此階段會結合使用帳戶屬性、人員屬性和人員活動資料，以定義及評估帳戶層級的對象。

**應用程式函式：** [!DNL RT-CDP] B2B：帳戶對象評估，[!DNL RT-CDP]：對象評估

**您將要設定的專案：**&#x200B;此階段會使用帳戶屬性、人員屬性和人員活動資料的組合，定義並評估帳戶層級的對象。 [!DNL RT-CDP] B2B edition中的帳戶對象可讓您根據實體特徵（產業、收入、員工人數）以及與這些帳戶相關聯之人員的參與行為來劃分帳戶。

此階段中的&#x200B;**決定點：**

>[!NOTE]
>**決定：對象評估方法**
>
>帳戶對象會籍的更新速度必須多久？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 批次評估（每日） | Campaign對象會每天重新整理、檔案式啟用、廣告平台對象 | 大部分的帳戶對象都使用批次評估。 處理結合帳戶和個人屬性的複雜多實體查詢。 對於大多數B2B使用案例，只要每天重新整理一次便已足夠。 |
>| 串流評估 | 需要近乎即時資格的[!DNL Marketo]或CRM啟用 | 帳戶受眾的串流資格有限。 只有簡單的帳戶屬性條件才符合串流評估的資格。 個人層級的行為條件通常需要批次。 |

>[!NOTE]
>**決定：帳戶對象定義方法**
>
>您將如何定義帳戶對象條件？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 僅限帳戶屬性 | 簡單的第一線目標定位（產業、收入、地區） | 實施最快。 僅限於帳戶層級資料。 用於廣泛目標定位。 |
>| 帳戶+個人屬性 | 將關聯人員符合特定條件（職稱、部門）的帳戶定位 | 更精確的目標定位。 結合第一和人口統計資料。 |
>| 帳戶+個人屬性+個人活動 | 將目標定位為具有參與連絡人的帳戶（電子郵件開啟、網站造訪、內容下載） | 功能最強大，但最複雜。 需要來自F3的行為事件資料。 通常需要批次評估。 |
>| 對象構成 | 複雜的對象邏輯，需要排名、分割、排除或擴充作業 | 將視覺化對象構成畫布用於衍生帳戶對象。 僅限批次評估。 |

>[!NOTE]
>**決定：隱藏對象策略**
>
>哪些帳戶應排除在啟用之外？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 現有客戶隱藏 | 以全新帳戶為目標的贏取行銷活動 | 排除具有有效訂閱或已關閉已贏取商機的帳戶 |
>| 有效銷售週期抑制 | 避免干擾活躍銷售參與中的帳戶 | 排除具有高於特定階段之未完成商機的帳戶 |
>| 最近參與抑制 | 防止最近聯絡的帳戶過度傳訊 | 排除回顧期間內的參與帳戶（例如30天） |
>| 無隱藏 | 以所有合格帳戶為目標的品牌認知行銷活動 | 請謹慎使用；可能會導致在不合格帳戶上浪費支出 |

**UI導覽：**&#x200B;客戶>對象>建立對象>建置規則（選取「帳戶」作為對象型別）

**金鑰組態詳細資料：**

- 在「區段產生器」中建立新對象時，選取「帳戶」作為對象型別
- 帳戶屬性會顯示在「區段產生器」的「帳戶」區段下（產業、收入、帳戶狀態）
- 可以透過帳戶對象產生器中的「人員」關係新增人員屬性和活動
- 設定批次評估排程（如果沙箱尚不存在）
- 建立目標對象（要包含的帳戶）和隱藏對象（要排除的帳戶）

**Experience League檔案：**

- [帳戶對象](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/types/account-audiences)
- [區段產生器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [對象構成](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Segmentation Service概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)

### 階段3：目的地設定

此階段會建立已驗證的連線，以連線至將傳送帳戶對象的目標目的地。

**應用程式函式：** [!DNL RT-CDP] B2B：帳戶目的地組態，[!DNL RT-CDP] B2B： [!DNL Marketo Engage]整合，[!DNL RT-CDP]：目的地組態

**您的設定內容：**&#x200B;此階段會建立已驗證的連線，以連線至將傳送帳戶對象的目標目的地。 設定包括從目錄選取目的地、提供驗證認證、設定帳戶層級和人員層級的欄位對應，以及設定匯出排程。 每種目的地型別都有獨特的需求和功能。

此階段中的&#x200B;**決定點：**

>[!NOTE]
>**決定：目的地選擇**
>
>哪些目的地會接收啟用的帳戶對象？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| [!DNL Marketo Engage] | B2B潛在客戶培養、評分和行銷活動執行 | 原生串流聯結器。 更新銷售機會/聯絡人記錄。 需要[!DNL Marketo] API認證（Munchkin ID、使用者端識別碼、使用者端密碼）。 |
>| [!DNL LinkedIn]個相符的對象 | [!DNL LinkedIn]上的帳戶型廣告 | 支援公司名稱和網域比對帳戶層級目標定位。 批次啟用。 需要[!DNL LinkedIn]行銷活動管理員存取權。 |
>| [!DNL Salesforce] CRM | 銷售啟用與CRM帳戶清單同步 | 串流聯結器會更新帳戶或連絡人記錄。 需要[!DNL Salesforce]具有寫入許可權的API存取權。 |
>| [!DNL Microsoft Dynamics 365] | 以[!DNL Dynamics]為基礎的組織的銷售啟用 | 串流聯結器。 需要[!DNL Dynamics 365] API存取權。 |
>| 雲端儲存空間([!DNL S3]， [!DNL Azure Blob]， [!DNL GCS]， SFTP) | 自訂整合、Data Warehouse、合作夥伴分享 | 檔案式批次匯出。 最大彈性，但需要下游處理。 |
>| [!DNL Google]個客戶相符 | 搜尋和顯示廣告鎖定 | 透過雜湊電子郵件進行個人層級比對。 批次啟用。 |
>| [!DNL The Trade Desk] | 程式化顯示和視訊廣告 | 個人層級比對。 批次啟用。 |

>[!NOTE]
>**決定：欄位對應策略**
>
>哪些帳戶和人員欄位應該對應至目的地？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 僅限身分欄位 | 只需要比對識別碼的Advertising平台 | 最低限度的資料傳輸。 電子郵件或公司網域上的目的地相符。 |
>| 身分+核心帳戶屬性 | CRM或[!DNL Marketo]的帳戶內容可改善目標定位 | 包括產業、收入、員工人數、帳戶層級。 豐富下遊記錄。 |
>| 完整的屬性集 | 雲端儲存空間或資料倉儲匯出 | 包含所有相關帳戶和個人屬性。 最大匯出裝載。 |

**使用者介面導覽：**&#x200B;連線>目的地>目錄>搜尋目的地>設定

**金鑰組態詳細資料：**

- 導覽至目的地目錄，然後選取目標目的地
- 提供目的地型別的特定驗證認證
- 設定將[!DNL RT-CDP]個XDM欄位連線到目的地欄位的欄位對應
- 針對[!DNL Marketo Engage]：提供Munchkin ID、使用者端ID和使用者端密碼
- 針對[!DNL LinkedIn]：透過OAuth授權，並選取[!DNL LinkedIn]廣告帳戶
- 針對雲端儲存空間：提供貯體/容器名稱、路徑、檔案格式和認證
- CRM：提供執行個體URL、API認證，以及目標物件型別（帳戶或連絡人）

**選項差異的位置：**

選項A的&#x200B;**（[!DNL Marketo Engage]串流）：**

導覽至「目的地>目錄> Adobe > [!DNL Marketo Engage]」。 設定Munchkin ID和API認證。 將[!DNL RT-CDP]識別欄位（電子郵件）和設定檔屬性對應至[!DNL Marketo]潛在客戶欄位。 目的地會自動處理遞增的串流更新。

選項B （Advertising平台批次）的&#x200B;**：**

導覽至「目的地>目錄> Advertising/社交>選取平台」 。 透過OAuth授權。 設定匯出排程（建議：每日）。 對應雜湊電子郵件識別碼和任何支援的相符欄位。 對於[!DNL LinkedIn]，另外對應公司名稱和網域欄位以進行帳戶層級的比對。

選項C （以雲端儲存檔案為基礎）的&#x200B;**：**

導覽至「目的地>目錄>雲端儲存>選取提供者」 。 設定貯體/容器、檔案路徑範本和檔案格式（CSV、JSON或Parquet）。 設定匯出排程，並選擇完整或增量匯出。 對應所有需要的帳戶和人員屬性欄位。

選項D （CRM串流）的&#x200B;**：**

導覽至「目的地>目錄> CRM >選取[!DNL Salesforce]或[!DNL Dynamics]」。 提供API認證和執行個體URL。 將[!DNL RT-CDP]欄位對應到CRM帳戶或連絡人欄位。 確保CRM中存在自訂欄位，以接收對象成員資格資料。

**Experience League檔案：**

- [目標概覽](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [目的地目錄](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)
- [Marketo Engage目的地](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/adobe/marketo-engage)
- [LinkedIn符合的對象目的地](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/social/linkedin)
- [Salesforce CRM目的地](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/crm/salesforce)
- [Amazon S3目的地](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/cloud-storage/amazon-s3)

### 階段4：對象啟用

此階段會將評估的帳戶對象發佈至設定的目的地。

**應用程式函式：** [!DNL RT-CDP] B2B：帳戶Audience Activation，[!DNL RT-CDP]： Audience Activation

**您的設定內容：**&#x200B;此階段會將評估的帳戶對象發佈到設定的目的地。 啟用會建立資料流，將帳戶對象（來源）連線至外部目的地（目標）、套用屬性對應，並根據設定的排程或串流行為起始匯出。 您也會設定隱藏對象，將不符合資格的帳戶排除在啟用之外。

此階段中的&#x200B;**決定點：**

>[!NOTE]
>**決定：匯出型別**
>
>啟動應該匯出完整的對象快照還是隻匯出增量變更？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 增量匯出 | 串流目的地([!DNL Marketo]、CRM)或下游系統處理差異的批次目的地 | 每次匯出的資料量較小。 更快速的處理。 需要下游系統來管理狀態。 串流目的地的預設值。 |
>| 完全匯出 | 下游系統取代每次執行的完整受眾的批次目的地 | 資料量更大，但下游邏輯更簡單。 在下游系統無法維持狀態時非常有用。 適用於檔案型目的地。 |

>[!NOTE]
>**決定：啟用範圍**
>
>每個目的地應該啟用多少對象？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 每個資料流的單一對象 | 透過清楚的對象對目的地對應，輕鬆啟動 | 最容易進行監控和疑難排解。 一個對象失敗不會影響其他對象。 |
>| 每個資料流有多個對象 | 前往相同目的地的多個相關對象 | 更有效地使用目的地連線。 所有對象共用相同的欄位對應和排程。 |

**使用者介面導覽：**&#x200B;連線>目的地>瀏覽>選取目的地>啟用對象

**金鑰組態詳細資料：**

- 從對象清單中選取目標對象
- 檢閱並確認階段3中設定的欄位對應
- 針對批次目的地：設定匯出排程（時間、頻率）
- 針對串流目的地：啟用會在設定後立即開始
- 可選擇使用排除功能新增隱藏對象
- 觸發初始測試啟動回合以驗證資料流

**選項差異的位置：**

選項A的&#x200B;**（[!DNL Marketo Engage]串流）：**

選取要啟用的帳戶對象。 啟用會立即開始串流。 在[!DNL Marketo]中確認銷售機會/聯絡人記錄已更新為區段成員資格欄位。 設定[!DNL Marketo]智慧型行銷活動，以根據這些欄位變更觸發。

選項B （Advertising平台批次）的&#x200B;**：**

選取帳戶對象並設定每日匯出排程。 第一次匯出完成後，在Advertising平台中驗證對象是否出現且有填入的成員計數。 允許平台24到48小時處理初始對象檔案。

選項C （以雲端儲存檔案為基礎）的&#x200B;**：**

選取帳戶對象並設定匯出排程和檔案格式。 第一次匯出後，驗證檔案會以預期的格式和內容出現在目標儲存位置。 確認下游匯入程式已成功使用匯出的檔案。

選項D （CRM串流）的&#x200B;**：**

選取要啟用的帳戶對象。 啟用會立即開始串流。 在CRM中確認帳戶或連絡人記錄已使用對應的欄位進行更新。 設定CRM報表、清單檢視或工作流程自動化，對更新的欄位採取行動。

**Experience League檔案：**

- [啟用串流目的地的對象](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [對批次目的地啟用對象](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [啟動護欄](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)
- [目標概覽](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)

### 第5階段：控管與監控

此階段會確保帳戶對象啟用符合資料治理原則和同意偏好設定，並監控持續啟用的資料流程的健康狀況。

**應用程式函式：** [!DNL RT-CDP] B2B： B2B資料控管，[!DNL RT-CDP]：同意與控管強制執行

**您將要設定的專案：**&#x200B;此階段會確保帳戶對象啟用符合資料治理原則和同意偏好設定，並且持續監視啟用資料流程的健康狀況。 B2B資料控管會強制對敏感帳戶屬性（收入、來自協力廠商提供者的員工人數）加以限制，而同意執行會確保人員層級的通訊符合選擇退出偏好設定。 監視功能會確認啟用資料流是否成功完成。

此階段中的&#x200B;**決定點：**

>[!NOTE]
>**決定：治理執行層級**
>
>對B2B啟用應如何嚴格執行資料控管？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 全面執行（封鎖違規） | 具有敏感資料的生產啟用 | 防止任何違反治理原則的啟動。 可能需要反複調整欄位對應以解決違規。 |
>| 警告並繼續 | 開發或測試環境 | 允許繼續啟用，但記錄警告。 在初始設定期間識別潛在問題時非常有用。 |

>[!NOTE]
>**決定：監視方法**
>
>應如何監視啟用健康狀態？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 警示式監視 | 必須快速擷取失敗的生產環境 | 針對目的地啟用失敗、來源流程失敗和資料流程延遲設定警報。 需要設定警示訂閱。 |
>| 手動監視 | 開發或低流量啟用 | 定期檢閱目的地UI中的資料流執行。 減少管理費用，但延遲失敗偵測的風險。 |
>| 兩者 | 具有複雜多目的地啟用的生產環境 | 嚴重失敗的警示，以及趨勢的定期儀表板檢閱。 建議用於大多數B2B實作。 |

**UI導覽：**&#x200B;隱私權>原則（針對治理）、連線>目的地>瀏覽>選取目的地>資料流執行（針對監視）

**金鑰組態詳細資料：**

- 將資料使用標籤套用至包含受限制屬性的B2B資料集
- 透過評估目標行銷動作的啟動，驗證已執行治理原則
- 設定目的地啟用失敗和來源聯結器失敗的警示
- 在每個啟用週期後檢閱資料流執行量度（設定檔已匯出，記錄已失敗）
- 設定授權使用儀表板檢閱以根據權益追蹤帳戶設定檔數量

**Experience League檔案：**

- [資料控管概覽](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [同意與偏好設定](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)
- [監視目的地資料流](https://experienceleague.adobe.com/en/docs/experience-platform/dataflows/ui/monitor-destinations)
- [警報概觀](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [啟動護欄](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)

## 實施考量

下列章節提供成功實作的額外指引。

### 護欄和限制

檢閱以下適用於此使用案例模式的平台護欄和限制。

- 每個沙箱最多4,000個區段定義，包括帳戶對象 — [分段護欄](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- 帳戶對象主要是使用批次評估來評估；串流資格僅限於簡單帳戶屬性條件
- 每個目的地連線最多100個資料流 — [目的地護欄](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)
- 批次目的地每個檔案區段最多可匯出500萬個設定檔
- 串流目的地具有目的地合作夥伴設定的每秒輸送量限制（例如，[!DNL Marketo] API速率限制）
- 構成對象（來自對象構成）僅限於批次評估，且無法使用串流
- 每個對象構成畫布最多10個構成區塊
- [!DNL LinkedIn]個相符對象需要最小對象人數（通常為300名成員）才能啟用
- CRM串流目的地受CRM提供者的API速率限制（例如，[!DNL Salesforce]大量API每日限制）所限制
- [!DNL RT-CDP] B2B edition授權控制企業帳戶設定檔總數 — [RT-CDP產品說明](https://helpx.adobe.com/legal/product-descriptions/real-time-customer-data-platform-b2b-edition-prime-and-ultimate-packages.html)

### 常見陷阱

實施此使用案例模式時，請注意下列常見問題。

- **不完整的個人對帳戶對應：**&#x200B;如果個人記錄（潛在客戶、連絡人）未透過B2B身分解析正確連結至帳戶記錄，則相依於個人屬性或活動的帳戶對象會少計算合格帳戶。 在建立帳戶對象之前，請先在F4中驗證人員與帳戶的關係。

- **造成對象漂移的過時CRM資料：**&#x200B;如果CRM來源聯結器未依定期排程執行或無訊息失敗，則帳戶屬性（產業、收入、狀態）會過時。 這會導致受眾包含不再符合資格的帳戶，或排除應符合資格的帳戶。 監視來源聯結器資料流健康狀況。

- **Advertising平台符合率期望：**&#x200B;將帳戶對象啟用至[!DNL LinkedIn]以外的廣告平台時，符合率取決於與合格帳戶相關聯的連絡人是否具備有效的個人層級識別碼（雜湊電子郵件）。 沒有相關連絡人且電子郵件地址不符的帳戶。 監視匹配率，並考慮擴充聯絡資料。

- **[!DNL Marketo]欄位對應未對齊：**&#x200B;當串流至[!DNL Marketo Engage]時，[!DNL RT-CDP]欄位對應必須針對現有的[!DNL Marketo]潛在客戶或連絡人欄位。 如果對應的[!DNL Marketo]欄位不存在，則更新將會自動失敗。 設定目的地之前，先在[!DNL Marketo]中預先建立所有目標欄位。

- **封鎖啟用的治理原則：**&#x200B;帳戶屬性欄位上的資料使用標籤（尤其是協力廠商第一方資料）在啟用至廣告目的地時，可能會觸發治理違規。 在啟用之前評估治理合規性，並調整欄位對應以視需要排除受限制的欄位。

- **結合帳戶和人員資料與僅限批次評估的帳戶對象：**&#x200B;參考個人層級行為事件（例如「在過去30天內至少有一位聯絡人開啟電子郵件的帳戶」）的帳戶對象需要批次評估。 如果使用案例需要即時資格，此限制可能會導致非預期的延遲。

### 最佳實務

請遵循這些建議以獲得最佳結果。

- 從少數定義良好的客戶對象（ICP階層、垂直產業、參與階層）開始，再展開到複雜的多屬性定義
- 為現有客戶、活躍商機和最近參與的客戶建立專用的隱藏受眾，以避免浪費支出和管道衝突
- 使用對象構成，透過根據彙總參與分數的排名帳戶來建立階層式帳戶對象（高/中/低參與）
- 針對協調的多頻道行銷活動，同時將相同帳戶對象啟用至多個目的地（例如，[!DNL LinkedIn]適用於廣告，[!DNL Marketo]適用於電子郵件， CRM適用於銷售可見度）
- 對帳戶對象實作一致的命名慣例，包括目標定位條件和預期的管道（例如「B2B_ICP_Enterprise_Tech_LinkedIn」或「B2B_Suppression_ActiveOpps」）
- 將批次啟用排程在非尖峰時段，以將對下游系統的影響降至最低，並與廣告平台處理時段保持一致
- 監視初始啟用後每個目的地的符合率，並反複處理身分欄位對應以改善比對
- 與[!DNL Marketo Engage]保持雙向資料流程：將參與資料從[!DNL Marketo]擷取到[!DNL RT-CDP] （來源聯結器），並將對象啟用回封閉回圈系統的[!DNL Marketo] （目的地聯結器）

### 權衡決定

進行實作決策時，請考慮下列取捨。

>[!NOTE]
>**取捨：對象新鮮度與評估複雜性**
>
>結合帳戶屬性和個人層級行為資料的帳戶對象可提供最精確的目標定位，但僅限於批次評估（每日重新整理）。 單單以帳戶屬性為基礎的較簡單受眾，可能符合使用近乎即時更新的串流評估資格。
>
>- **批次（複雜條件）偏好：**&#x200B;目標定位精確度，結合第一和行為訊號，綜合帳戶評分
>- **串流（簡單條件）優點：**&#x200B;對象更新速度、帳戶變更的即時回應、[!DNL Marketo]和CRM中更快的行動時間
>- **建議：**&#x200B;對可接受每日重新整理的主要目標對象使用批次評估（大多數B2B使用案例）。 保留對時間敏感的觸發器的串流評估，例如帳戶狀態變更或高價值帳戶警報。

>[!NOTE]
>**取捨：集中啟動與目的地特定對象**
>
>您可以對多個目的地啟用單一統一帳戶對象，或建立針對每個管道功能和需求量身打造的目的地特定對象。
>
>- **集中式對象偏好：**&#x200B;跨管道的一致性、更簡單的對象管理、統一的報告
>- **目的地特定對象偏好：**&#x200B;每個頻道最佳化鎖定目標（例如[!DNL LinkedIn]公司層級屬性的優點，而[!DNL Marketo]需要潛在客戶層級詳細資料）、頻道特定隱藏規則
>- **建議：**&#x200B;從集中式對象開始，以保持一致性，然後僅在頻道需求明顯不同時（例如，廣告與電子郵件的隱藏視窗不同）建立目的地特定變體。

>[!NOTE]
>**取捨：即時CRM同步與批次CRM更新**
>
>串流至CRM可提供即時的銷售可見度，但會消耗CRM API配額。 批次檔案匯出更有效率，但會導致延遲。
>
>- **串流CRM同步的優點：**&#x200B;銷售回應能力、立即帳戶警示、即時管道可見度
>- **批次CRM更新有利：** API配額保留、大量更新效率、與CRM資料載入視窗一致
>- **建議：**&#x200B;使用串流CRM同步處理進行高優先順序的帳戶資格變更（例如，帳戶移至「銷售就緒」階層）。 使用批次檔案匯出進行大量更新，例如每月帳戶評分重新整理或區域重新指派清單。

## 相關文件

下列資源提供此使用案例模式中所使用功能的其他內容和詳細指引。

**[!DNL RT-CDP]B2B edition**

- [Real-Time CDP B2B edition概觀](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/overview#rtcdp-b2b)
- [Real-Time CDP中的B2B結構描述](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [帳戶對象](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/types/account-audiences)
- [RT-CDP B2B edition產品說明](https://helpx.adobe.com/legal/product-descriptions/real-time-customer-data-platform-b2b-edition-prime-and-ultimate-packages.html)

**對象評估與細分**

- [Segmentation Service概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [區段產生器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [對象構成](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [串流區段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [分段護欄](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)

**目的地和啟用**

- [目標概覽](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [目的地目錄](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)
- [Marketo Engage目的地](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/adobe/marketo-engage)
- [LinkedIn符合的對象目的地](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/social/linkedin)
- [Salesforce CRM目的地](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/crm/salesforce)
- [Microsoft Dynamics 365目的地](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/crm/microsoft-dynamics-365)
- [Amazon S3目的地](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/cloud-storage/amazon-s3)
- [啟用串流目的地的對象](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [對批次目的地啟用對象](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [啟動護欄](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)

**資料來源與聯結器**

- [來源概觀](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)
- [Marketo Engage聯結器](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
- [Salesforce聯結器](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/crm/salesforce)

**資料模型與身分**

- [XDM系統概覽](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Identity Service總覽](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [設定檔概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [合併原則概觀](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

**資料控管和隱私權**

- [資料控管概覽](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [資料使用標籤概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/labels/overview)
- [同意與偏好設定](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)

**監視與可觀察性**

- [警報概觀](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [監視目的地資料流](https://experienceleague.adobe.com/en/docs/experience-platform/dataflows/ui/monitor-destinations)
- [監視來源資料流](https://experienceleague.adobe.com/en/docs/experience-platform/sources/api-tutorials/monitor)
- [授權使用量儀表板](https://experienceleague.adobe.com/en/docs/experience-platform/landing/license-usage-and-guardrails/license-usage-dashboard)

**報告與分析**

- [CJA概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [連線總覽](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/overview)
- [資料檢視總覽](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/data-views)

**教學課程與指南**

- [Real-Time CDP B2B edition快速入門](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro)
- [建立B2B來源的結構描述](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [沙箱工具](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/sandbox-tooling-api/overview)
