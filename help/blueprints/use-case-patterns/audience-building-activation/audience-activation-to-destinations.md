---
title: 目的地的Audience啟用
description: 瞭解如何使用Adobe Real-Time CDP評估對象區段並將其發佈到外部目的地以進行定位或抑制。
solution: Real-Time Customer Data Platform, Experience Platform
source-git-commit: b2e496eb521fc3dd3290fccdd9a8203384934b88
workflow-type: tm+mt
source-wordcount: '7005'
ht-degree: 1%

---


# 目的地的Audience啟用

本指南提供從Adobe [!DNL Real-Time Customer Data Platform] (RT-CDP)啟用對象至外部目的地的完整實作參考。 它專為需要評估對象區段並將其發佈至廣告平台、雲端儲存空間、CRM系統或資料合作夥伴以進行目標定位、隱藏、相似對象建模或分析擴充的解決方案架構師、行銷技術人員和實作工程師所設計。

它提供所有可行的實作選項，以及權衡分析、決定指引、UI導覽路徑和Experience League檔案參考。

指南涵蓋對象啟動的整個生命週期，從定義及評估對象區段（透過設定目的地連線和發佈對象），到監控啟動健康狀況和強制實行控管合規性。

## 使用案例概述

組織需要將受眾資料傳送至外部系統，以支援付費媒體行銷活動、豐富CRM記錄、與合作夥伴共用資料，或提供下游分析。 Audience Activation to Destinations是RT-CDP中的基本啟用模式：它會評估哪些設定檔符合目標對象的資格、連線到一個或多個外部目的地、將設定檔屬性對應到目的地特定欄位，以及發佈對象以供下游使用。

每當目標是在適當的時間以適當的格式將對象資料取得至外部系統時，此模式即適用。 它不涉及訊息傳送、網站上的個人化或分析。 這是RT-CDP實作最常見的起點，並作為其他模式在上方所構成的建置區塊。

典型的利害關係人包括管理付費媒體的數位行銷團隊、豐富倉儲的資料團隊、為行銷活動準備聯絡名單的CRM團隊，以及確保傳出資料流程符合治理規範的隱私權團隊。

## 主要業務目標

此使用案例模式致力於達成下列業務目標。

### 贏取新客戶

透過鎖定目標的贏取促銷活動、相似對象和付費媒體最佳化，來擴大客戶基礎。

**KPI：**&#x200B;新客戶、客戶贏取成本、潛在客戶/潛在客戶轉換

[進一步瞭解如何取得新客戶](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

### 降低客戶贏取成本

提升目標定位效率、從贏取促銷活動中抑制現有客戶，並最佳化媒體支出。

**KPI：**&#x200B;客戶贏取成本、每個潛在客戶的成本、效率

[深入瞭解如何降低客戶贏取成本](/help/blueprints/business-objectives/cost-efficiency/reduce-customer-acquisition-cost.md)

### 最佳化行銷支出和ROI

透過更好的目標定位、歸因、對象抑制和預算分配，改善行銷投資報酬。

**KPI：**&#x200B;成本節省、客戶贏取成本、遞增收入

[進一步瞭解最佳化行銷支出和ROI](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md)

## 戰術使用案例範例

- **廣告平台對象目標定位** — 將合格的區段推送至付費媒體平台，以利行銷活動目標定位
- **現有客戶的付費媒體隱藏** — 將已知客戶排除在廣告平台的贏取行銷活動中，以避免浪費支出
- **相似種子對象** — 將高價值客戶區段推送至Facebook、Google Ads或交易台，作為相似對象擴展的種子對象
- **銷售啟用的CRM同步** — 啟用高意圖或高價值對象，讓銷售團隊可以優先處理外展工作
- **資料合作夥伴對象共用** — 與資料合作夥伴共用合格的對象區段，以進行Co-op目標定位或測量
- **匯出雲端儲存空間以擴充資料倉儲** — 將對象成員資格和設定檔屬性匯出至Amazon S3、Azure Blob、Google雲端儲存空間或SFTP，以供下游分析使用
- **重新目標定位對象啟用** — 啟用未轉換為重新目標定位平台的網站訪客
- **連絡人清單同步處理至電子郵件服務提供者** — 將對象會籍推送至協力廠商電子郵件平台，以協調外展工作

## 關鍵績效指標

| KPI | 說明 | 測量指引 |
| --- | --- | --- |
| 客戶贏取成本(CAC) | 透過已啟用的受眾取得新客戶的成本 | 歸因於已啟用的受眾的媒體總支出/新客戶 |
| 對象符合率 | 已在目的地成功比對的已啟動設定檔百分比 | 符合目的地/從RT-CDP匯出的設定檔的設定檔 |
| 隱藏省錢 | 抑制贏取促銷活動的現有客戶，以節省媒體支出 | 預估的CPM x受眾人數 |
| 啟用傳送率 | 成功傳送到目的地的設定檔百分比 | 來源對象中已傳送的設定檔/設定檔 |
| 啟動時間 | 從對象定義到目的地第一次傳遞的經過時間 | 從區段建立到首次確認資料流執行的測量 |
| 對象母體準確度 | 目標處的預期和實際受眾規模的對齊方式 | 目的地受眾規模/RT-CDP受眾規模 |

## 使用案例模式

**Audience Activation至目的地** — 評估對象區段並發佈至外部目的地，以進行目標定位或隱藏。

**功能鏈：**&#x200B;對象評估>目的地設定> Audience Activation >監視

## 應用程式

- **Adobe [!DNL Real-Time Customer Data Platform] (RT-CDP)** — 對象評估、目的地管理、對象啟用、同意和治理執行
- **Adobe [!DNL Experience Platform] (AEP)** — 設定檔存放區、身分服務、細分引擎、資料控管

## 基礎函式

下列基本功能必須為此使用案例模式準備就緒。 對於每個函式，狀態會指出它通常是必要的、假設為預先設定或不適用。

| 基礎函式 | 狀態 | 必須準備就緒的專案 | Experience League參考 |
| --- | --- | --- | --- |
| 管理與治理 | 已假設就位 | RT-CDP沙箱已布建並啟用。 指派給實作角色的目的地管理和啟用許可權。 目標平台可用的目的地帳戶認證。 | [沙箱總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sandbox/home)，[存取控制總覽](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| 資料模型與準備 | 必填 | 設定檔結構描述必須包含將對應至目的地欄位的屬性（例如電子郵件、電話、雜湊識別碼、人口統計屬性）。 結構描述必須已啟用設定檔，且資料集正在接收資料。 | [XDM系統總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/xdm/home)，[結構描述組合基本概念](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/xdm/schema/composition) |
| 資料來源與收集 | 已假設就位 | 支援對象評估的設定檔資料必須擷取且為最新狀態。 批次和/或串流擷取管道可正常運作。 網頁SDK、來源聯結器或批次擷取，將資料傳送到已啟用設定檔的資料集。 | [來源概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sources/home)，[網頁SDK概觀](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home) |
| 身分和設定檔設定 | 必填 | 必須設定目的地比對的身分名稱空間（例如Facebook自訂對象、Google Ads客戶比對的雜湊電子郵件）。 合併原則必須產生具有啟動所需所有屬性的統一設定檔。 | [身分識別服務總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/identity/home)，[合併原則總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/merge-policies/overview) |
| 對象定義與細分 | 必填 | 使用區段產生器、對象構成或同盟對象構成所定義的目標對象。 根據啟動延遲需求選取的評估方法（批次、串流或邊緣）。 此函式在此計畫的階段1中執行。 | [區段服務總覽](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)，[區段產生器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder) |

## 支援功能

以下功能可擴大此使用案例模式，但不是核心執行的必要功能。

| 支援功能 | 狀態 | 為什麼這很重要 | Experience League參考 |
| --- | --- | --- | --- |
| 計算/衍生屬性建立 | 推薦 | 期限值、參與分數或傾向分數等計算屬性可改善對象精確度，並提供擴充屬性以對應至目的地。 當目的地受益於值型或分數型對象細分時，特別有用。 | [計算屬性總覽](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| 資料生命週期管理 | 推薦 | 資料集和設定檔到期原則可確保資料的時效性和合規性。 同意結構描述設定可確保僅啟用同意的設定檔。 將資料匯出至外部系統時，對於法規合規性而言至關重要。 | [進階資料生命週期管理概觀](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| 資料使用標籤和實作 | 推薦 | 控管標籤和原則會防止將受限制的資料啟用至未經授權的目的地（例如，廣告平台的PII、資料合作夥伴的敏感區段）。 對於外部協力廠商系統的對象啟用尤其重要。 | [資料控管概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/home)，[資料使用標籤概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/labels/overview) |
| 監控與可觀察性 | 已包含 | 啟動監視是功能鏈（階段5）的一部分。 涵蓋資料流執行監控、傳送狀態警示、對象母體追蹤和授權使用可見度。 | [監視目的地資料流](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/dataflows/ui/monitor-destinations)，[警示概述](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview) |
| 報告與分析 | 推薦 | CJA對對象啟用效能的分析，可測量啟用對象的效能（例如，來自隱藏的轉換提升度，來自相似對象的ROAS）。 | [CJA概觀](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-overview/cja-overview) |

## 應用程式函式

此計畫會從「應用程式功能目錄」中執行下列功能。 函式會對應至實作階段，而非編號步驟。

### [!DNL Real-Time CDP] (RT-CDP)

| 函式 | 實作階段 | 說明 |
| --- | --- | --- |
| 對象評估 | 階段1：對象評估 | 定義對象規則，並使用批次、串流或邊緣評估方法評估區段會籍 |
| 對象構成 | 階段1：對象評估 | 選擇性地針對複雜的對象邏輯，透過擴充、排名、分割、排除和聯結作業來撰寫衍生對象 |
| 目的地設定 | 階段2：目的地組態 | 使用欄位對應和排程引數設定與外部目的地的已驗證連線 |
| Audience Activation | 階段3：Audience Activation | 使用屬性對應和匯出排程將評估對象發佈到已設定的目的地 |
| 同意與治理實施 | 階段4：治理驗證 | 在外部系統的受眾啟用之前和期間，強制執行同意偏好設定和資料使用原則 |

## 先決條件

- [ ] RT-CDP授權正在使用受眾啟用權益
- [ ] Target沙箱已布建並可供實作團隊存取
- [ ]個使用者角色包含目的地管理和對象啟用許可權
- [ 每個目標目的地都有]驗證認證（OAuth權杖、API金鑰、S3存取金鑰或服務帳戶認證）
- [ ]設定檔結構描述包含需要對應到目的地欄位的所有屬性
- [ 已設定目的地比對所需的]個身分識別名稱空間（例如雜湊電子郵件、電話、裝置ID）
- [ ]資料擷取管道正在運作，設定檔正在填入設定檔存放區
- [ ]已針對啟用的屬性（尤其是外部目的地）檢閱資料控管標籤和原則
- [ 若需要同義式篩選，則在設定檔中填入]同意欄位

## 實作選項

以下實施選項適用於此使用案例模式。 檢閱每個選項和比較表，以決定符合需求的最佳方法。

### 選項A：串流目的地啟用

**最適合：**&#x200B;廣告平台或合作夥伴系統的即時對象成員資格更新 — Facebook自訂對象、Google廣告客戶比對、LinkedIn比對對象、Trade Desk和類似的串流API型目的地。

**運作方式：**

當設定檔符合或取消符合區段的資格時，串流目的地啟用可近乎即時地將對象會籍變更傳送到目的地。 當設定檔屬性變更或發生行為事件導致設定檔進入或退出對象時，成員資格更新會在數分鐘內串流到目的地。

此方法需要串流目的地聯結器（大部分的主要廣告平台都支援此方法）以及串流或邊緣對象評估方法。 對象評估會持續監控合格設定檔變更，而啟動資料流會在發生更新時推送更新。 目的地會收到遞增的成員資格變更，而非完整對象快照。

串流啟用是RT-CDP目錄大多數廣告平台目的地的預設值。 目的地聯結器會自動處理API驗證、速率限制和重試邏輯。

**主要考量事項：**

- 對象評估必須使用串流或邊緣評估（僅限批次的對象無法即時饋送串流目的地）
- 並非所有區段運算式都符合串流評估的資格 — 複雜的彙總、多實體查詢和某些以時間為基礎的函式都需要批次
- 目的地合作夥伴API速率限制可能會在大型對象資格事件期間影響輸送量
- 設定檔屬性更新會與成員資格變更一併傳送，讓目的地資料保持最新狀態

**優點：**

- 目的地近乎即時的對象新鮮度（分鐘而非小時）
- 相較於完整匯出，增量更新可減少資料傳輸量
- 自動處理資格和取消資格事件
- 大部分的廣告平台目的地都原生支援串流

**限制：**

- 需要符合串流條件的區段定義（有限的區段功能集）
- 無法控制檔案格式或匯出結構 — 由目的地聯結器決定的資料格式
- 無法匯出至檔案式儲存目的地(S3、Azure Blob、SFTP)
- 目的地API速率限制可能會限制大量變更

**Experience League：**

- [啟用串流目的地的對象](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [串流目的地目錄](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/catalog/overview)

### 選項B：批次目的地啟用（檔案匯出）

**最適合：**&#x200B;排程對象匯出至雲端儲存空間、資料倉儲，或使用檔案式匯入的系統 — Amazon S3、Azure Blob儲存空間、Google雲端儲存空間、SFTP、資料登陸區域。

**運作方式：**

批次目的地啟用會依排程的步調評估對象，並將結果匯出為檔案（CSV、JSON或Parquet）至已設定的儲存體目的地。 匯出可包含完整對象快照或增量變更（自上次匯出以來的新資格和取消資格）。

實施作業包括使用儲存憑證、檔案格式偏好設定（分隔符號、壓縮、命名慣例）和匯出排程（每日、每3小時、每6小時等）來設定檔案型目的地連線。 每次匯出執行都會產生包含對象成員資格及任何對應設定檔屬性的檔案。

此方法支援範圍最廣的下游使用者，因為一般都支援檔案式資料交換。 這也是雲端儲存和資料倉儲擴充使用案例的唯一選項。

**主要考量事項：**

- 對象評估可以使用任何方法（批次、串流或邊緣） — 匯出本身會依排程執行，無論如何
- 檔案格式、壓縮和命名慣例可根據目的地設定
- 支援增量匯出（僅限變更）和完整匯出（完整受眾快照）
- 匯出排程詳細程度的範圍從每3小時到每日

**優點：**

- 完整控制匯出檔案格式(CSV、JSON、Parquet)、壓縮和命名
- 與任何可使用檔案的下游系統相容
- 支援增量與完整匯出模式
- 可使用任何評估方法匯出對象（包括含有複雜分段邏輯的批次區段）
- 支援在常規排程之外執行臨機（隨選）匯出

**限制：**

- 延遲較高 — 對象資料會依排程抵達目的地，而非即時
- 檔案式匯出需要目標系統處理和擷取檔案
- 匯出檔案的目的地的儲存成本
- 與漸進式串流更新相比，每次匯出的資料量更大

**Experience League：**

- [啟用對象以批次設定檔匯出目的地](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [以檔案為基礎的目的地目錄](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/cloud-storage)

### 選項C：多目的地啟用

**最適合：**&#x200B;同時將相同對象啟用至多個目的地 — 例如，將隱藏清單推送至所有廣告平台、將高值區段同步至CRM和廣告平台，或協調多個媒體合作夥伴的對象觸及率。

**運作方式：**

多目的地啟用不是個別的技術機制，而是選項A和B的組合，可跨多個目的地連線套用至相同對象。 相同的對象會啟用到兩個或多個目的地，每個目的地都有自己的連線設定、欄位對應和排程。

每個目的地連線都獨立運作 — Facebook的串流啟動和匯出至S3的批次可同時從相同的來源受眾執行。 欄位對應是按目的地設定的，因此可以根據每個目的地的要求以及治理原則允許的內容，將不同的屬性傳送至不同的系統。

這是跨多個廣告平台運作、在媒體啟動時維護CRM同步，或需要將對象資料發佈到營運和分析系統的組織通用的生產模式。

**主要考量事項：**

- 每個目的地都有獨立的欄位對應、排程和治理評估
- 每個目的地都會強制實行治理原則 — 不同的目的地型別可能允許不同的屬性
- 單一受眾可同時啟用串流和批次目的地的混合
- 新增目的地不需要變更現有的啟用

**優點：**

- 透過單一受眾定義，協調所有外部系統的受眾分佈
- 每個目的地的獨立設定允許最佳化的對應和排程
- 針對每個目的地執行治理，可確保不同目的地型別間的合規性
- 集中受眾管理，同時支援分散式啟用

**限制：**

- 設定、驗證和維護更多目的地連線
- 監視複雜性會隨著每個目的地而增加 — 必須為每個目的地追蹤啟用失敗
- 授權使用（啟用的設定檔）可能依許可權計入每個目的地
- 跨多個目的地的欄位對應維護需要協調

**Experience League：**

- [目標概覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/home)
- [目的地目錄](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/catalog/overview)

### 選項比較

| 條件 | 選項A：串流 | 選項B：批次（檔案匯出） | 選項C：多目的地 |
| --- | --- | --- | --- |
| 最適合 | 即時廣告平台目標定位和抑制 | 資料倉儲擴充、檔案式系統整合 | 協調的跨平台受眾分佈 |
| 複雜性 | 低 | 中 | 高 |
| 延遲 | 分鐘（近乎即時） | 小時（已排程） | 每個目的地分鐘和小時的組合 |
| 檔案格式控制項 | 無（目的地決定格式） | 完整（CSV、JSON、Parquet、壓縮、命名） | 每個目的地 |
| 對象評估 | 需要串流或邊緣 | 任何方法（批次、串流、邊緣） | 依目的地需求 |
| 需要 | 串流目的地聯結器，符合串流條件的區段 | 以檔案為基礎的目的地聯結器、儲存憑證 | 多個目的地聯結器和認證 |
| 治理 | 單一目的地評估 | 單一目的地評估 | 每個目的地評估 |

### 選擇正確的選項

使用以下決定邏輯來選取正確的實作方法：

1. **您需要多少目的地？** 如果您需要在兩個或多個目的地啟用相同的對象，則需實作選項C （針對每個目的地構成選項A和B）。 針對每個目的地繼續進行問題2和3。

2. **目的地是否支援串流？** 如果目的地是廣告平台(Facebook、Google Ads、LinkedIn、The Trade Desk)或透過串流API進行合作夥伴整合，請針對該目的地使用選項A。 如果目的地是雲端儲存空間(S3、Azure Blob、GCS、SFTP)或使用檔案的系統，請使用選項B。

3. **對象必須以多快的速度到達目的地？** 如果對象成員資格必須在數分鐘內反映在目的地（例如，在作用中行銷活動期間的即時隱藏），請使用選項A。如果每日或多小時傳送次數已足夠（例如每週資料倉儲重新整理、CRM批次同步），請使用選項B。

4. **您的對象是否使用複雜的分段邏輯？** 如果對象定義包含多事件彙總、大型時段，或不符合串流評估資格的函式，請使用選項B （批次目的地），或確保選項A目的地也會依排程接收批次評估的對象。

## 實作階段

實施會遵循這些階段。 每個階段都包含設定詳細資料、決策點，以及Experience League檔案的連結。

### 階段1：對象評估

**應用程式函式：** RT-CDP：對象評估，RT-CDP：對象構成

**您將設定的專案：**&#x200B;定義將啟動至目的地的目標對象。 這包括指定對象條件（哪些設定檔符合資格）、選取評估方法（成員資格更新的速度）並驗證對象母體。 這是所有啟用的起點 — 如果沒有已定義和已評估的對象，就沒有要啟用的內容。

此階段中的&#x200B;**決定點：**

>[!NOTE]
>
>**決定：對象建立方法**
>
>應如何定義目標對象？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 區段產生器（規則型） | 使用設定檔屬性、行為事件和區段會籍條件的標準對象定義 | 最彈性的規則定義；支援適用於合格運算式的串流和邊緣評估；適用於單一條件或中等複雜的受眾 |
>| 對象構成 | 對象需要合併、排名、分割或排除現有對象 | 循序作業的視覺畫布；結果僅供批次評估；每個畫布最多10個構成區塊 |
>| 同盟對象構成 | 必須根據外部資料倉儲中的資料評估對象條件，才能將其擷取至AEP | 直接查詢外部資料庫；避免資料重複；需要同盟對象組合授權 |

>[!NOTE]
>
>**決定：評估方法**
>
>設定檔必須多久進入和退出對象？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 批次 | 不符合串流資格的已排程行銷活動、每日對象重新整理或複雜分段邏輯 | 每個工作最多可處理2,400萬個設定檔；支援所有細分功能；依排程執行（每日預設或自訂cron排程） |
>| 串流 | 串流目的地啟用或事件觸發的使用案例所需的即時對象會籍變更 | 近乎即時（秒到分鐘）；分段函式集有限 — 僅限簡單事件、屬性比較和有限的時間範圍；無多實體查詢 |
>| Edge | 邊緣所需的相同頁面個人化或即時對象資格 | 毫秒延遲；限制最嚴格的規則集 — 僅設定檔屬性和簡單區段成員資格檢查；主要用於站上個人化（不常用於目的地啟用） |

>[!NOTE]
>
>**決定：合併原則**
>
>對象評估應該使用哪個合併原則？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 時間戳記已排序（預設） | 大部分的使用案例 — 當設定檔片段衝突時，最近的資料應優先處理 | 最常見；使用最近更新的屬性值 |
>| 資料集優先順序 | 無論時間戳記為何，特定資料來源都應覆寫其他資料來源 | 需要定義資料集優先順序；當CRM記錄系統應一律覆寫網頁收集的資料時，這非常有用 |

**UI導覽：**&#x200B;客戶>受眾>建立受眾>建置規則（適用於區段產生器）或撰寫受眾（適用於受眾構成）

**金鑰組態詳細資料：**

- 根據使用案例定義對象條件 — 設定檔屬性、行為事件、區段成員資格或時間型條件
- 套用隱藏規則以排除不應啟用的設定檔（例如，最近轉換、全域取消訂閱）
- 在繼續啟用之前驗證對象母體大小
- 確認評估方法與階段2中選取的目的地型別一致

**選項差異的位置：**

選項A （串流目的地啟用）的&#x200B;**：**
對象必須使用串流或邊緣評估，以提供即時成員資格更新。 驗證區段規則運算式符合串流評估的資格 — 避免以時間為基礎的彙總函式、多實體查詢，以及`inSegment()`僅批次區段的參考。

選項B （批次目的地啟用）的&#x200B;**：**
任何評估方法皆可運作。 批次評估是最常見的選擇，因為匯出本身會依排程執行。 確認批次評估排程存在於沙箱中，或建立一個。

選項C （多目的地啟用）的&#x200B;**：**
評估方法應該適用於要求最嚴格的目的地。 如果任何目的地需要串流，對象應該使用串流評估。 如果所有目的地都是批次，則批次評估就足夠了。

**Experience League檔案：**

- [Segmentation Service概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [區段產生器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Profile Query Language參考](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)
- [串流區段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [邊緣分段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [對象構成概觀](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [評估方式](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home#evaluation-methods)


### 階段2：目的地設定

**應用程式函式：** RT-CDP：目的地組態

**您的設定內容：**&#x200B;建立已驗證連線到將發佈對象的外部目的地。 這包括從目錄選取目的地、提供驗證認證，以及設定目的地特定引數，例如檔案格式、儲存位置和匯出排程。 每個目的地都需要自己的連線設定。

此階段中的&#x200B;**決定點：**

>[!NOTE]
>
>**決定：目的地型別**
>
>應該將對象傳送至何處？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| Advertising目的地（串流） | 在廣告平台（Facebook、Google Ads、LinkedIn、The Trade Desk等）上鎖定目標或隱藏目標 | 串流聯結器；近乎即時更新會籍；透過雜湊電子郵件、電話或裝置ID進行身分比對 |
>| 雲端儲存空間目的地（批次） | 匯出至S3、Azure Blob、GCS、SFTP或資料登陸區域，以擴充資料倉儲 | 檔案式匯出；可設定的格式(CSV、JSON、Parquet)；排程步調 |
>| CRM目的地 | 將受眾同步至Salesforce、Microsoft Dynamics或HubSpot以啟用銷售 | 通常為串流；需要CRM特定的欄位對應；可能需要CRM管理員許可權 |
>| 資料合作夥伴目的地 | 與測量或目標定位合作夥伴共用受眾資料 | 因合作夥伴而異；請檢閱外部共用資料的治理影響 |
>| 自訂目的地(Destination SDK) | 目錄中沒有目標系統 | 需要使用Destination SDK建立自訂目的地；實作工作量較高 |

>[!NOTE]
>
>**決定：驗證方法**
>
>目的地需要什麼認證？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| OAuth 2.0 | 廣告平台和SaaS目的地(Facebook、Google、Salesforce) | 需要初始授權流程；權杖會自動重新整理；最常用於串流目的地 |
>| 存取金鑰/秘密金鑰 | 雲端儲存空間(S3、Azure Blob) | 靜態認證；應規劃輪換；適用於以檔案為基礎的目的地 |
>| 服務帳戶/API金鑰 | 合作夥伴API與自訂整合 | 需要目的地合作夥伴提供認證 |
>| 連線字串 | 以Azure為基礎的目的地 | 包含所有連線引數的單一字串 |

>[!NOTE]
>
>**決定：匯出型別（僅限批次目的地）**
>
>應如何封裝受眾資料以供匯出？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 增量匯出 | 僅自上次匯出以來的新資格和取消資格 | 檔案大小較小；目的地處理速度較快；需要目的地系統來維持狀態 |
>| 完全匯出 | 每次執行時完成對象快照 | 大型檔案；目的地每次都能呈現完整畫面；對於進行完整取代的系統，則更為簡單 |

**使用者介面導覽：**&#x200B;連線>目的地>目錄> [選取目的地] >設定

**金鑰組態詳細資料：**

- 瀏覽目的地目錄並選取目標目的地
- 提供驗證認證並測試連線
- 針對批次目的地：設定檔案格式(CSV、JSON、Parquet)、壓縮、檔案命名範本和匯出排程
- 針對串流目的地：連線通常透過OAuth授權流程建立
- 在繼續啟用之前，請確認目的地連線狀態是否顯示為「作用中」

**選項差異的位置：**

選項A （串流目的地啟用）的&#x200B;**：**
從目錄（Advertising或Social類別）中選取串流目的地。 完成OAuth授權流程。 在確認授權後，連線已準備好啟動。

選項B （批次目的地啟用）的&#x200B;**：**
從目錄（雲端儲存空間類別）中選取以檔案為基礎的目的地。 設定儲存路徑、檔案格式、壓縮、命名慣例和匯出排程。 透過驗證對儲存位置的寫入存取權來測試連線。

選項C （多目的地啟用）的&#x200B;**：**
對每個目的地重複此階段。 每個連線都是獨立的 — 您可能混合了串流和批次目的地。 記錄每個連線的驗證和設定，以供作業參考。

**Experience League檔案：**

- [目的地目錄](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/catalog/overview)
- [目標概覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/home)
- [啟用對象以批次設定檔匯出目的地](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [啟用串流目的地的對象](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [Destination SDK概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/destination-sdk/overview)
- [Destination SDK設定選項](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/destination-sdk/functionality/configuration-options)


### 階段3：對象啟用

**應用程式函式：** RT-CDP： Audience Activation

**您要設定的專案：**&#x200B;建立啟動資料流，將評估過的對象發佈到設定的目的地。 這涉及選取要啟動的對象、將設定檔屬性對應至目的地欄位，以及設定匯出排程。 啟動資料流會將來源對象連線至目標目的地，並管理正在進行的資料傳送。

此階段中的&#x200B;**決定點：**

>[!NOTE]
>
>**決定：屬性對應**
>
>啟動時應包含哪些設定檔屬性？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 僅限身分欄位 | 目的地只需要符合設定檔（例如，廣告平台中的對象成員資格） | 最低限度的資料傳輸；最安全的隱私權；廣告平台目標定位和抑制的典型用法 |
>| 身分+設定檔屬性 | 目的地需要個人化或分段的擴充屬性（例如CRM同步、合作夥伴共用） | 已傳輸更多資料；需要每個屬性的控管審查；根據目的地行銷動作檢查資料使用標籤 |
>| 身分+計算屬性 | 目的地從衍生分數或彙總（例如期限值階層、合作夥伴定位的傾向分數）中獲益 | 需要設定計算屬性；下游系統的高值擴充 |

>[!NOTE]
>
>**決定：匯出排程（僅限批次目的地）**
>
>對象資料的匯出頻率為何？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 每日 | 標準重新整理步調；大部分批次使用案例 | 平衡新鮮度與處理成本；最常見的預設值 |
>| 每3-6小時 | 頻率較高的使用案例，例如當日行銷活動最佳化 | 更頻繁的檔案產生；在目的地有更高的儲存和處理負載 |
>| 隨選（臨機） | 一次性匯出或緊急非週期啟動 | 手動觸發可略過排程；適合測試或緊急行銷活動需求 |

**使用者介面導覽：**&#x200B;連線>目的地>瀏覽> [選取目的地] >啟用對象

**金鑰組態詳細資料：**

- 選取一或多個要啟用至目的地的對象
- 將設定檔屬性和身分欄位對應到目的地特定欄位
- 針對串流目的地：確認身分名稱空間對應（例如將雜湊電子郵件傳送至Facebook的extern_id）
- 針對批次目的地：設定匯出排程、選取增量或完整匯出模式，並設定第一個匯出日期
- 在發佈之前，先檢閱啟用摘要，以確認所有對應和排程

**選項差異的位置：**

選項A （串流目的地啟用）的&#x200B;**：**
選取對象並將身分名稱空間對應至目的地身分欄位。 發佈後立即開始啟用 — 對象會幾乎即時地將資料流變更為目的地。 不需要匯出排程；啟動是連續的。

選項B （批次目的地啟用）的&#x200B;**：**
選取對象、對應設定檔屬性，並設定匯出排程。 選擇增量與完整匯出模式。 選擇性地觸發臨機匯出，以在一般排程之外立即傳送。

選項C （多目的地啟用）的&#x200B;**：**
對每個目的地重複啟動工作流程。 相同對象可啟用至多個目的地，每個目的地各有不同的屬性對應。 例如，僅傳送雜湊電子郵件至廣告平台，但包含人口統計屬性至CRM。

**Experience League檔案：**

- [啟用串流目的地的對象](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [啟用對象以批次設定檔匯出目的地](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [對批次目的地啟用隨選對象](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/api/ad-hoc-activation-api)
- [監視目的地的資料流](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/dataflows/ui/monitor-destinations)


### 第4階段：治理驗證

**應用程式功能：** RT-CDP：同意與治理強制執行

**您要設定的專案：**&#x200B;驗證在啟動之前和啟動期間，治理原則和同意偏好設定是否正確執行。 此階段會確保受限制的資料（PII、敏感屬性）不會傳送至未經授權的目的地，且未經有效同意的設定檔會排除在啟用之外。 在啟動時自動執行治理，但主動驗證可防止封鎖的啟動和合規性違規。

此階段中的&#x200B;**決定點：**

>[!NOTE]
>
>**決定：治理執行方式**
>
>何時應驗證治理法規遵循？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 主動（預先啟用） | 建議用於所有實作，尤其是啟用至外部第三方系統時 | 在設定欄位對應之前，先檢閱資料使用標籤和原則；防止啟用失敗，並確保從一開始就遵守規定 |
>| 反應式（啟動時） | 當治理政策已建立妥當，且團隊對合規充滿信心時 | Platform會在啟動時自動執行原則；違規會封鎖啟動或排除受限制的屬性；如果未妥善瞭解原則，可能會導致意外失敗 |

>[!NOTE]
>
>**決定：同意篩選**
>
>同意偏好設定應該如何影響啟用？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 已啟用同意執行 | 在法律要求同意的情況下，針對廣告或行銷目的地進行啟用時需要使用 | 未經有效同意的設定檔(consent.marketing.{channel}.val = &#39;y&#39;)會自動從啟用中排除；需要內嵌同意資料 |
>| 無同意篩選 | 同意不適用於資料傳輸的內部使用目的地或分析匯出 | 只有當資料使用不構成需要同意的行銷動作時才適用；請諮詢法律/隱私權團隊 |

**UI導覽：**&#x200B;隱私權>原則>同意原則（供同意檢閱）；資料治理>原則（供資料使用原則檢閱）

**金鑰組態詳細資料：**

- 檢閱套用到正在啟用的資料集和結構描述欄位的資料使用標籤
- 驗證與目的地相關聯的行銷動作（例如，針對廣告平台的「匯出至第三方」）的治理原則是否有效
- 確認同意欄位已填入設定檔中，且相關管道已啟用同意實作
- 如果偵測到原則違規，請從目的地對應移除限制欄位或選取替代目的地來解決

**Experience League檔案：**

- [資料控管概覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/home)
- [原則執行](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/enforcement/overview)
- [資料使用標籤概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/labels/overview)
- [同意與偏好設定](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)
- [同意原則執行](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/policies/user-guide)


### 階段5：監控與驗證

**應用程式功能：**&#x200B;監視與可觀察性

**您的設定內容：**&#x200B;設定持續監視啟動資料流程、設定失敗警示、驗證目的地的對象母體，以及追蹤授權使用情況。 監控在生產啟動中至關重要，因為傳送失敗會直接影響行銷活動效能和媒體支出。

**金鑰組態詳細資料：**

- 檢閱每個作用中目的地的資料流執行狀態，以確認對象已成功傳遞
- 針對目的地啟用失敗、資料流延遲和受眾母體異常設定警報
- 追蹤已匯出的設定檔與每次資料流執行失敗的設定檔
- 監視目的地（可提供目的地報表的位置）的對象符合率
- 檢閱授權使用情況，以根據許可權追蹤已啟用的設定檔數量

**使用者介面導覽：**&#x200B;連線>目的地>瀏覽> [選取目的地] >資料流執行（針對啟用監視）；警示>警示規則>訂閱（針對警示設定）；管理>授權使用情況（針對授權追蹤）

**Experience League檔案：**

- [監視目的地的資料流](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/dataflows/ui/monitor-destinations)
- [警報概觀](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [可觀察性深入分析概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/observability/home)
- [授權使用量儀表板](https://experienceleague.adobe.com/en/docs/experience-platform/landing/license-usage-and-guardrails/license-usage-dashboard)

## 實施考量

在實施之前和期間，請檢閱下列考量事項。

### 護欄和限制

- **區段定義限制：**&#x200B;每個沙箱最多4,000個區段定義 — [分段護欄](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- 每個目的地的&#x200B;**資料流：**&#x200B;每個目的地連線最多100個資料流 — [目的地護欄](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/guardrails)
- **批次匯出檔案大小：**&#x200B;以檔案為基礎的目的地有匯出檔案大小上限；大型對象會自動分割到多個檔案
- **串流目的地輸送量：**&#x200B;每個目的地合作夥伴都設定了每秒輸送量限制；可能會限制大量對象變更
- **批次評估容量：**&#x200B;依預設，每個區段評估工作最多2,400萬個設定檔
- **對象構成：**&#x200B;每個畫布最多10個構成區塊；構成的對象僅供批次評估
- **身分圖表：**&#x200B;每個圖表最多50個身分 — [身分服務護欄](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)
- **計算屬性：**&#x200B;每個沙箱最多25個計算屬性 — [計算屬性護欄](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview#guardrails)
- **啟動護欄概述：** [啟動護欄](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/guardrails)

### 常見陷阱

- **具有不合格的規則邏輯的串流區段：**&#x200B;定義具有複雜彙總函式或多實體查詢的對象，並預期串流評估。 這些區段會無訊息地回復到批次評估，導致非預期的延遲。 預防：在定義對象之前，先檢閱串流資格要求。

- **由於同意篩選而匯出的零個設定檔：**&#x200B;對象中的所有設定檔都缺少有效的同意值，導致在啟動時會篩選出整個對象。 預防：驗證同意資料擷取是否可運作，以及在啟用前是否已填入同意欄位。

- **治理原則意外封鎖啟用：**&#x200B;結構描述欄位上的資料使用標籤觸發原則違規，導致無法啟用。 預防：在設定欄位對應之前，主動評估治理合規性（階段4）。 檢閱從結構描述繼承的標籤。

- **目的地認證過期：** OAuth權杖或API金鑰過期，導致啟用失敗，不會立即發出警示。 預防：針對目的地啟用失敗設定警示，並建立認證輪換排程。

- **不相符的身分名稱空間：**&#x200B;啟用對應中設定的身分名稱空間不符合目的地的預期（例如，當目的地需要SHA-256雜湊電子郵件時，傳送純文字電子郵件）。 預防：在設定對應之前，請先檢閱目的地檔案以取得必要的身分格式。

- **欄位對應錯誤導致匯出失敗：**&#x200B;將設定檔屬性對應到具有不相容資料型別或格式的目的地欄位。 預防：先以小型對象測試啟動，並在縮放至生產對象之前，檢閱資料流執行詳細資料以對應錯誤。

- **RT-CDP與目的地之間的對象母體漂移：** RT-CDP中的受眾規模與目的地的計數不符，因為身分比對差異、目的地重複資料刪除邏輯或時間。 這是預期行為 — 預防：記錄每個目的地的預期符合率基準，並監控重大偏差。

### 最佳實務

- **從測試對象開始：**&#x200B;在啟用生產對象之前，先對每個新的目的地啟用一個小型、容易理解的測試對象。 透過測試對象驗證欄位對應、身分比對和傳送量度。

- **提早進行圖層治理：**&#x200B;在設定目的地啟用之前，先套用資料使用標籤並設定治理原則。 如此可防止封鎖的啟動，並確保從一開始的合規性。

- **使用批次目的地的增量匯出：**&#x200B;增量匯出會減少檔案大小、加快目的地的處理速度，以及將儲存成本降至最低。 只有在目的地系統需要完全取代受眾時，才使用完整匯出。

- **標準化命名慣例：**&#x200B;為整個組織的對象、目的地連線和資料流建立一致的命名。 在名稱中包含使用案例、目的地和評估方法（例如「Suppression_ExistingCustomers_Facebook_Streaming」）。

- **監視器符合率：**&#x200B;追蹤從RT-CDP匯出的設定檔與每個目的地符合的設定檔比率。 符合率大幅下降可能表示身分解析問題、認證問題或目的地API變更。

- **協調跨目的地的隱藏：**&#x200B;使用隱藏對象（例如，將現有客戶排除在贏取行銷活動之外）時，請同時啟用所有相關廣告平台的隱藏對象，以維持一致性。

- **檢閱並刪減非作用中的啟用：**&#x200B;定期檢閱目的地資料流，並停用不再需要的對象。 非作用中啟用會消耗授權容量並增加監控負荷。

### 權衡決定

>[!NOTE]
>
>**取捨：對象新鮮度與分段彈性**
>
>串流評估提供近乎即時的對象更新，但限制您可以使用的區段規則功能。 批次評估支援完整的區段規則函式集，但會導致延遲（小時而非分鐘）。
>
>- **串流優惠：**&#x200B;對象會籍必須在數分鐘內反映於目的地的即時使用案例（作用中行銷活動隱藏、即時重新目標定位）
>- **批次偏好：**&#x200B;需要彙總函式、多實體查詢或大型時間視窗條件（期限值階層、多重接觸行為區段）的複雜對象邏輯
>- **建議：**&#x200B;針對啟用串流目的地的受眾，使用串流評估，即時新鮮度可提升業務價值。 對複雜對象使用批次評估，這些對象已啟用至檔案型目的地或每日重新整理已足夠。 針對同時需要這兩個版本的對象，請考慮建立兩個版本：用於即時啟用的簡化串流區段，以及用於定期擴充的完整批次區段。

>[!NOTE]
>
>**取捨：最小資料匯出與豐富屬性對應**
>
>僅匯出身分欄位（雜湊電子郵件、裝置ID）可儘量減少資料洩露並簡化控管。 匯出其他設定檔屬性（人口統計、價值層、參與分數）可豐富目的地，但會增加治理複雜度和資料責任。
>
>- **最低限度的匯出好處：**&#x200B;隱私權優先方法；較低的治理風險；較簡單的欄位對應；足以用於大多數廣告平台目標定位和隱藏的使用案例
>- **豐富匯出偏好：**&#x200B;目的地的下游個人化；CRM擴充；需要屬性層級詳細資料的合作夥伴資料共用
>- **建議：**&#x200B;預設為廣告目的地的僅限身分匯出最小值。 只有在目的地使用案例明確需要設定檔屬性時，才新增設定檔屬性，且治理檢閱會確認相容。 使用運算屬性來提供彙總、較不敏感的擴充值，而非原始PII。

>[!NOTE]
>
>**取捨：每個目的地的單一對象與合併的多對象資料流**
>
>將每個對象啟用為個別的資料流可提供隔離和精細的監控。 透過單一資料流啟用多個對象至目的地，可簡化管理並減少隔離。
>
>- **個別資料流優先：**&#x200B;獨立監視、更輕鬆的疑難排解、能夠暫停個別對象啟用而不會影響其他對象
>- **整合的資料流優先：**&#x200B;維護的連線較少、簡化認證管理、減少營運負荷
>- **建議：**&#x200B;針對相同目的地啟用多個相關對象時（例如，Facebook的所有隱藏區段），請使用合併的資料流程。 當受眾有不同的SLA、不同的屬性對應或故障隔離很重要時，請使用單獨的資料流。

## 相關文件

**目的地**

- [目標概覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/home)
- [目的地目錄](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/catalog/overview)
- [啟用串流目的地的對象](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [啟用對象以批次設定檔匯出目的地](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [對批次目的地啟用隨選對象](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/api/ad-hoc-activation-api)
- [目的地護欄](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/guardrails)
- [Destination SDK概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/destination-sdk/overview)

**對象和細分**

- [Segmentation Service概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [區段產生器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Profile Query Language參考](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)
- [串流區段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [邊緣分段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [對象構成概觀](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [分段護欄](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)

**身分和設定檔**

- [Identity Service總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/identity/home)
- [身分名稱空間概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/identity/features/namespaces)
- [身分識別圖連結規則](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/identity/features/identity-linking-logic)
- [設定檔概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [合併原則概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/merge-policies/overview)

**資料模型與結構描述**

- [XDM系統概覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/xdm/home)
- [結構描述組合基本面](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/xdm/schema/composition)

**資料控管**

- [資料控管概覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/home)
- [資料使用標籤概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/labels/overview)
- [資料治理原則](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/policies/overview)
- [原則執行](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/enforcement/overview)
- [同意與偏好設定](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)

**監視和可觀察性**

- [監視目的地的資料流](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/dataflows/ui/monitor-destinations)
- [警報概觀](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [可觀察性深入分析概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/observability/home)
- [授權使用量儀表板](https://experienceleague.adobe.com/en/docs/experience-platform/landing/license-usage-and-guardrails/license-usage-dashboard)

**計算屬性**

- [計算屬性概述](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [計算屬性UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/ui)

**資料收集和來源**

- [來源概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sources/home)
- [網頁SDK概觀](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [設定資料串流](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/datastreams/configure)

**管理**

- [沙箱概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sandbox/home)
- [存取控制總覽](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home)
- [以屬性為基礎的存取控制](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/abac/overview)

**護欄**

- [即時客戶個人檔案護欄](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Identity Service護欄](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)
- [啟動護欄](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/guardrails)
- [擷取護欄](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/ingestion/guardrails)
