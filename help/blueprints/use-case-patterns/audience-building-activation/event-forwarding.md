---
title: 事件轉送
description: 瞭解如何將透過Edge Network收集的即時事件資料轉送至分析、儲存或廣告的非Adobe目的地。
solution: Experience Platform
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '6342'
ht-degree: 0%

---


# 事件轉送

本指南涵蓋使用[!DNL Adobe Experience Platform] Edge Network實作伺服器端事件轉送。 它專為需要透過Edge Network將收集的即時事件資料發佈到非Adobe目的地（例如協力廠商分析平台、雲端儲存端點、廣告網路或自訂Webhook）的解決方案架構師、行銷技術人員和實施工程師所設計。

它提供設定事件轉送的所有可行方法、說明它們之間的利弊，以及連至[!DNL Adobe Experience League]檔案的連結，以取得詳細的程式指引。

## 使用案例概述

透過[!DNL Adobe Experience Platform]網頁SDK、Mobile SDK或伺服器API收集行為資料的組織，通常需要與非Adobe系統（例如[!DNL Google Analytics]或[!DNL Snowflake]等分析平台、轉換追蹤的廣告網路、長期儲存的資料倉儲或自訂內部服務）共用相同的事件資料流。 傳統上，這需要使用者端標籤大量增加，這會增加頁面重量、造成延遲，並產生隱私權和治理風險。

事件轉送可透過在Edge Network上操作伺服器端來解決此問題。 當訪客互動透過網頁SDK或伺服器API觸發事件時，該事件會透過資料流路由傳送至Edge Network。 事件轉送規則（在專用事件轉送屬性中設定）會評估傳入事件資料，並選擇性地將其轉送至一或多個已設定的目的地。 伺服器端方法可減少使用者端標籤膨脹、改善頁面效能、集中資料控管，並讓組織能夠確切控制哪些資料離開Adobe生態系統。

此模式的目標對象包括已部署（或計畫部署）用於資料收集的[!DNL Adobe Experience Platform] Web SDK或伺服器API，並想要透過將事件資料分發到非Adobe端點來擴大該投資的組織，而不新增使用者端JavaScript標籤。

## 主要業務目標

此使用案例模式支援下列業務目標。

### 改善資料品質和管理

確保資料乾淨、完整且合規，以實現準確定位、減少浪費及可靠分析。 事件轉送可在伺服器端集中處理資料分佈，為組織提供與外部系統共用資料的單一控制點，降低資料洩漏的風險，並確保在資料離開[!DNL Adobe] Edge Network之前套用治理原則。

**KPI：**&#x200B;效率、成本節省

如需詳細資訊，請參閱[改善資料品質和控管](../../business-objectives/cost-efficiency/improve-data-quality-governance.md)。

### 整合併更新行銷技術

遷移至統一、可擴充的平台，減少工具分散和技術負債。 事件轉送可讓組織使用單一伺服器端資料發佈機制來取代多個使用者端廠商標籤，減少頁面載入開銷並簡化技術棧疊。

**KPI：**&#x200B;節省成本、效率、上市速度

如需詳細資訊，請參閱[整合併更新行銷技術](../../business-objectives/cost-efficiency/consolidate-modernize-marketing-technology.md)。

## 戰術使用案例範例

以下是適用於此使用案例模式的常見戰術情境。

- **協力廠商分析擴充** — 即時將頁面檢視、點按和轉換事件轉寄給[!DNL Google Analytics]、[!DNL Snowflake]或其他分析平台，而不新增使用者端標籤
- **Advertising轉換追蹤** — 將購買和銷售機會產生事件傳送至[!DNL Meta]轉換API、[!DNL Google Ads]、[!DNL TikTok]或[!DNL Snap]，以用於伺服器端轉換測量和最佳化
- **資料倉儲串流** — 將原始事件資料路由到雲端資料倉儲([!DNL Google BigQuery]、[!DNL Amazon S3]、[!DNL Azure Event Hubs])，以進行長期儲存和離線分析
- **自訂webhook整合** — 透過HTTP端點將經過篩選或轉換的事件資料轉送至內部微服務、CRM系統或合作夥伴平台
- **減少標籤與改善頁面效能** — 以單一Web SDK實作以及伺服器端事件轉送規則，取代多個使用者端廠商JavaScript標籤，減輕頁面重量並改善Core Web Vitals
- **符合隱私權規範的資料共用** — 在與協力廠商共用事件資料之前，先在伺服器端套用資料篩選和欄位層級密文規則，確保PII在到達外部系統之前被清除或雜湊
- **多雲端事件分佈** — 從單一伺服器端規則集同時將相同的事件資料流轉送至多個目的地（例如，分析、廣告和資料倉儲）
- **即時詐騙訊號轉送** — 將高價值交易事件轉送至詐騙偵測系統，以便即時取得風險評分和警示

## 關鍵績效指標

以下KPI可協助評估此使用案例模式的成功。

- **減少頁面載入時間** — 測量到將使用者端標籤移轉至伺服器端事件轉送後，頁面載入速度和Core Web Vitals的改善
- **資料傳送成功率** — 成功轉送至目的地端點的事件百分比，且沒有錯誤或逾時
- **標籤計數減少** — 實作伺服器端對等項後移除的使用者端廠商標籤數目
- **資料新鮮度/延遲** — 使用者端上發生事件與事件到達目的地端點之間的時間（目標：次秒至秒）
- **治理合規率** — 通過伺服器端篩選規則的傳出資料共用百分比，可確保沒有PII或受限制的資料到達未經授權的目的地
- **營運效率** — 減少開發人員管理使用者端標籤部署和疑難排解標籤衝突所花費的時間

## 使用案例模式

本節說明用於實作事件轉送的模式與函式鏈。

**事件轉送** — 將透過Edge Network收集的即時事件資料轉送至非Adobe目的地，以用於分析、儲存或廣告。

**函式鏈：**&#x200B;資料流設定>事件規則定義>目的地對應>轉送執行>監視

## 應用程式

在此使用案例模式中使用以下應用程式。

- **[!DNL Adobe Experience Platform] (Edge Network)** — 透過已設定的資料串流，從Web SDK、Mobile SDK或伺服器API接收及路由即時事件資料
- **[!DNL Adobe Experience Platform]（事件轉送）** — 提供伺服器端規則引擎，用於評估、篩選、轉換事件資料並將資料轉送至外部目的地
- **[!DNL Adobe Experience Platform]（標籤/資料集合）** — 管理事件轉送屬性生命週期、擴充功能、規則和發佈工作流程

## 基礎函式

下列基本功能必須為此使用案例模式準備就緒。 對於每個函式，狀態會指出它通常是必要的、假設為預先設定或不適用。

| 基礎函式 | 狀態 | 必須準備就緒的專案 | Experience League參考 |
| --- | --- | --- | --- |
| 管理與治理 | 必填 | 沙箱必須在作用中並設定適當的使用者角色和許可權。 管理事件轉送的使用者需要[!DNL Adobe Admin Console]中的資料收集許可權，包括管理事件轉送屬性、擴充功能和規則的許可權。 | [存取控制總覽](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| 資料模型與準備 | 必填 | 必須為流經Edge Network的事件資料定義XDM結構描述。 資料流必須參考有效的XDM ExperienceEvent結構描述，才能讓事件轉送規則存取結構化欄位，以進行篩選、轉換和對應。 | [XDM系統總覽](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home) |
| 資料來源與收集 | 必填 | 資料收集機制必須是作用中的 — Web SDK、Mobile SDK或Edge Network Server API — 透過已設定的資料流傳送事件。 資料串流是連線使用者端集合與伺服器端事件轉送的基本路由層。 | [設定資料串流](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure) |
| 身分和設定檔設定 | 不適用 | 事件轉送會在身分解析或設定檔統一發生之前，對Edge Network層的原始事件資料進行操作。 除非轉送的事件也需要協助至Real-Time Customer Profile （這是獨立的資料流服務設定，而不是事件轉送問題），否則不需要身分名稱空間和合併原則。 | |
| 對象定義與細分 | 不適用 | 事件轉送會即時處理個別事件，不會評估對象成員資格。 對象型篩選不屬於事件轉送功能鏈。 如需以對象為基礎的啟用，請參閱Audience Activation至目的地參考計畫。 | |

## 支援功能

以下功能可擴大此使用案例模式，但不是核心執行的必要功能。

| 支援功能 | 狀態 | 為什麼重要 | Experience League參考 |
| --- | --- | --- | --- |
| 計算/衍生屬性建立 | 不適用 | 事件轉送會操作原始事件資料，而非設定檔層級的運算屬性。 運算屬性在事件轉送內容中無法使用。 | |
| 資料生命週期管理 | 推薦 | 如果事件資料也正在被擷取到AEP資料集（透過相同的資料流），則應為這些資料集設定資料保留原則（有效期），以管理儲存成本和法規遵循。 事件轉送本身不會儲存資料，但平行的AEP擷取路徑會儲存。 | [進階資料生命週期管理概觀](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| 資料使用標籤和實作 | 推薦 | 雖然事件轉送規則提供欄位層級篩選（可讓您從轉送的有效負載中排除敏感資料），將資料使用標籤套用至基礎結構和資料集可確保當相同的資料用於對象啟用或個人化時，會強制執行治理原則。 | [資料控管概觀](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home) |
| 監控與可觀察性 | 已包含 | 監視是事件轉送的必要條件。 「事件轉送監控」控制面板提供轉送成功率、錯誤率和目的地回應代碼的可見度。 應該針對目的地失敗設定警示。 | [事件轉送監視](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/monitoring) |
| 報告與分析 | 推薦 | 如果轉送的事件摘要給協力廠商分析平台，請考慮將相同的AEP事件資料集連線至CJA，以取得統一的跨管道檢視。 如此可讓您比較Adobe端與協力廠商的分析。 | [CJA概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) |

## 應用程式函式

此計畫會從「應用程式功能目錄」中執行下列功能。 函式會對應至實作階段，而非編號步驟。

### [!DNL Adobe Experience Platform] (AEP)

| 函式 | 實作階段 | 說明 |
| --- | --- | --- |
| 資料流設定 | 階段1：資料流設定 | 設定資料串流以接收Edge Network事件並啟用事件轉送服務 |
| 事件轉送屬性設定 | 階段2：事件轉送屬性和擴充功能 | 建立事件轉送屬性並安裝目的地專用擴充功能 |
| 事件規則定義 | 階段3：事件規則定義 | 定義規則以評估傳入的事件資料，並決定要轉送的內容和位置 |
| 目的地對應 | 階段3：事件規則定義 | 將事件資料元素對應至轉送規則中的目的地特定裝載格式 |
| 轉寄執行 | 第4階段：發佈與啟用 | 將事件轉送設定發佈到Edge Network以即時執行 |
| 監控 | 階段5：監控與驗證 | 監視轉送成功率、錯誤碼和目的地健康狀況 |

## 先決條件

在開始實作之前，請確定已具備下列專案。

- [ 具有Edge Network和事件轉送權益的] [!DNL Adobe Experience Platform]授權
- [ 在[!DNL Adobe Admin Console]中設定的]資料收集許可權（管理屬性、擴充功能、規則，以及事件轉送的發佈）
- [ ]至少一個使用中的資料收集機制（網頁SDK、行動SDK或伺服器API）會透過資料流傳送事件
- [ 針對正在收集的事件資料定義了]個XDM ExperienceEvent結構描述
- [ ]資料串流已建立並連結至收集機制
- [ ]可用的目的地端點認證和檔案（例如，[!DNL Meta]轉換API存取權杖、[!DNL Google Analytics]測量ID、webhook URL、雲端儲存空間認證）
- [ ]瞭解事件資料模型，以及每個目的地需要哪些欄位/事件

## 實作選項

本節說明實施事件轉送的可用方法，並提供選擇正確選項的指南。

### 選項A：擴充功能型事件轉送

**最適合：**&#x200B;個使用支援良好的目的地平台（[!DNL Meta]、[!DNL Google]、[!DNL AWS]、[!DNL Azure]、[!DNL Snowflake]等）的團隊 在資料收集目錄中有可用的預先建立事件轉送擴充功能。

**運作方式：**

擴充功能型事件轉送可運用Adobe或協力廠商合作夥伴維護的預先建立整合功能。 每個擴充功能都是為特定目的地專門建置，可處理驗證、裝載格式和端點通訊。 實作人員會在事件轉送屬性中安裝擴充功能、設定驗證認證，以及建置將XDM資料元素對應至擴充功能動作欄位的規則。

此方法可儘量減少自訂開發，因為擴充功能會抽象化目的地的API需求。 例如，[!DNL Meta] Conversions API擴充功能會將XDM商務事件轉譯為[!DNL Meta]預期的格式，處理PII欄位的雜湊處理、重複資料刪除引數，以及存取權杖管理。 同樣地，[!DNL Google Cloud Platform]或[!DNL AWS]擴充功能會處理其個別雲端服務的驗證和裝載格式。

擴充功能的可用性會決定要支援哪些目的地，這是取捨的取捨。 如果目標目的地沒有副檔名，則必須改用選項B （自訂Webhook）。

**主要考量事項：**

- 擴充功能可用性不盡相同 — 在規劃前先檢查[資料收集擴充功能目錄](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/overview)
- 擴充功能由Adobe或合作夥伴進行維護；更新可能會帶來重大變更，需要調整規則
- 有些擴充功能僅支援特定事件型別或需要特定XDM欄位對應
- 擴充功能在其設定UI中處理驗證和認證管理

**優點：**

- 受支援目的地的實作時間最短
- 預先建立的裝載格式可減少對應錯誤
- 由擴充功能處理的驗證和認證管理
- 由Adobe或認證合作夥伴維護和更新
- 減少自訂程式碼並降低維護負擔

**限制：**

- 僅限於具有可用擴充功能的目的地
- 與自訂Webhook相比，裝載自訂的彈性較低
- 擴充功能更新可能需要重新設定規則
- 有些擴充功能可能不支援所有目的地API功能

**Experience League：**

- [事件轉送擴充功能目錄](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/overview)
- [Meta Conversions API擴充功能](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/meta/overview)
- [Google Cloud Platform擴充功能](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/google-cloud-platform/overview)
- [AWS擴充功能](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/aws/overview)
- [Snowflake擴充功能](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/tags/extensions/server/snowflake/overview)

### 選項B：自訂webhook （擷取API）事件轉送

**最適合：**&#x200B;需要轉送事件到未預先建立擴充功能的目的地，或需要完全控制HTTP要求承載、標頭和驗證機制的團隊。

**運作方式：**

自訂webhook型事件轉送使用[!DNL Adobe Cloud Connector]延伸（預設包含）向任何端點提出任意HTTP要求。 實作人員會定義資料元素，以從傳入的XDM事件擷取和轉換值，然後使用雲端聯結器的「進行擷取呼叫」動作型別來設定規則動作。 此動作可讓您完全控制HTTP方法、URL、標頭和要求內文。

要求內文通常使用資料元素和自訂程式碼來建構，以根據目的地的API規格來格式化裝載。 此方法支援任何可透過HTTP存取的端點（REST API、webhook、雲端函式或內部服務），使其成為最靈活的選項。

取捨是投入更多實作工作與持續性維護。 實作人員必須瞭解目的地API、手動處理驗證（例如設定Authorization標頭、管理Token重新整理）並維護裝載格式（如果目的地API不斷演變）。

**主要考量事項：**

- 需要瞭解目的地API規格（HTTP方法、URL結構、裝載格式、驗證）
- 資料元素或密碼中的驗證認證必須手動管理
- 承載轉換（雜湊、編碼、重新調整）可能需要自訂程式碼
- 目的地API變更時沒有自動更新 — 需要手動維護
- 資料收集的秘密功能可以安全地儲存API金鑰和權杖

**優點：**

- 支援任何HTTP可存取的端點 — 無擴充功能相依性
- 完整控制請求承載、標題和驗證
- 可轉送至內部服務、自訂API或利基平台
- 使用自訂程式碼啟用複雜的裝載轉換
- 可以在自訂程式碼中實作重試邏輯和錯誤處理

**限制：**

- 更高的初始實施工作量
- 承載格式和驗證的持續維護責任
- 沒有預先建立的錯誤處理或認證輪換 — 必須手動實作
- 需要開發人員的HTTP通訊協定和目的地API詳細資訊

**Experience League：**

- [Adobe Cloud Connector擴充功能](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/cloud-connector/overview)
- [事件轉送密碼](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/secrets)

### 選項C：混合式（擴充功能+自訂Webhook）

**最適合：**&#x200B;組織會將事件轉送至多個目的地，其中有些會預先建立擴充功能，有些則需要自訂整合。

**運作方式：**

混合方法結合支援良好的目的地的擴充功能型轉送，以及缺少擴充功能的目的地的自訂webhook動作。 單一事件轉送屬性包含多個規則 — 有些使用擴充功能動作（例如，[!DNL Meta]廣告轉換追蹤的轉換API擴充功能），有些則使用Cloud Connector擷取動作（例如，轉送至內部資料湖端點）。

此方法可最大化涵蓋範圍，同時儘量減少不必要的自訂開發。 每個規則都獨立運作，因此擴充功能型規則可受益於預先建立的裝載格式，而自訂規則則可維持完整的彈性。

**主要考量事項：**

- 屬性複雜度會隨著規則和目的地的數量而增加
- 針對擴充功能與自訂規則，測試與偵錯可能需要不同的方法
- 發佈變更會影響屬性中的所有規則 — 使用程式庫和環境安全地暫存變更
- 請考慮使用明確的命名慣例來組織規則，以區分擴充功能型動作和自訂動作

**優點：**

- 各種目的地型別的最佳涵蓋範圍
- 儘可能運用預先建立的擴充功能，減少工作量
- 維持自訂目的地的彈性
- 單一事件轉送屬性會管理所有轉送邏輯

**限制：**

- 多種規則型別擁有更高的屬性複雜性
- 混合維護模式 — 有些規則會透過擴充功能自動更新，有些則需手動維護
- 除錯需要熟悉擴充功能設定和自訂擷取呼叫模式

**Experience League：**

- [事件轉送概觀](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/overview)
- [事件轉送快速入門](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/tags/event-forwarding/getting-started)

### 選項比較

下表比較三個實作選項。

| 條件 | 選項A：以擴充功能為基礎 | 選項B：自訂Webhook | 選項C：混合式 |
| --- | --- | --- | --- |
| 最適合 | 支援的目標（[!DNL Meta]、[!DNL Google]、[!DNL AWS]等） | 自訂端點、利基平台、內部服務 | 支援混合的多個目的地 |
| 複雜性 | 低 | Medium — 高 | 中 |
| 實作時間 | 天 | 日 — 周 | 因目的地組合而異 |
| 彈性 | 僅限擴充功能 | 完全控制 | 視需要完全控制 |
| 維護 | 低（擴充功能管理） | 高（手動維護） | 混合 |
| 需要 | 適用於目的地的擴充功能 | 目的地API檔案 | 兩者皆有，視目的地而定 |
| 需要自訂程式碼 | 最小 | 中等 — 重大 | 因情況而異 |

### 選擇正確的選項

首先，清查您的目標目的地，並檢查每個目的地是否存在預先建立的事件轉送擴充功能。

1. **如果所有目的地都有副檔名** — 選擇選項A。這可讓您以最低的維護負擔，獲得最快的實作速度。 擴充功能可處理驗證、裝載格式及API版本管理。

2. **如果沒有目的地具有擴充功能，或您需要完整裝載控制項** — 請選擇選項B。使用Cloud Connector擴充功能，對任何端點提出自訂HTTP要求。 這也正是您需要套用複雜轉換、自訂雜湊或傳送至內部服務時的正確選擇。

3. **如果您同時有支援和不支援的目的地** — 請選擇[選項C]。將擴充功能用於[!DNL Meta]、[!DNL Google]和[!DNL AWS]等平台，並將自訂Webhook用於其他所有功能。 這是具有各種分析和廣告棧疊的組織最常見的生產案例。

## 實作階段

以下階段說明事件轉送的端對端實作程式。

### 階段1：資料流設定

**應用程式函式：** AEP：資料流設定

**您要設定的專案：**&#x200B;接收來自網頁SDK、Mobile SDK或伺服器API實作之事件的資料流，並將它們路由至Edge Network，以便事件轉送規則可以處理。 如果要將事件轉送新增到現有的資料收集部署，您將在現有的資料流上啟用事件轉送。

此階段中的&#x200B;**決定點：**

>[!NOTE]
>
>**決定：新資料串流與現有資料串流**
>
>您應該為事件轉送建立新的資料流，還是在現有資料流上啟用事件轉送？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 使用現有的資料流 | 您已經有網頁SDK或伺服器API透過資料流傳送事件 | 最常見的情況；事件轉送只是作為資料流上的額外服務來啟用。 不需要使用者端變更。 |
>| 建立新資料流 | 這是沒有現有資料收集的Greenfield實作，或者您需要針對特定事件型別的個別資料流程 | 需要使用者端SDK設定來指向新的資料串流ID。 允許隔離的設定。 |

>[!NOTE]
>
>**決定：要啟用哪些AEP服務以及事件轉送**
>
>資料流可同時將事件路由至多個AEP服務。 事件轉送是一種服務；其他（AEP資料擷取、[!DNL Target]、[!DNL Analytics]）可以並行執行。
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 僅限事件轉送 | 您只需要將事件轉送至非Adobe目的地，而不需要AEP資料集中的資料 | 將資料處理成本降至最低。 事件會透過Edge Network轉送規則，但未擷取至AEP資料湖。 |
>| 事件轉送+ AEP擷取 | 您需要在AEP （用於設定檔、對象、歷程）中且轉送至外部系統的相同事件 | 對於搭配協力廠商分析使用[!DNL RT-CDP]或[!DNL AJO]的組織而言，最常使用。 資料流會將事件傳送至AEP資料集和事件轉送規則。 |
>| 事件轉送+多個Adobe服務 | 您需要同時路由至AEP、[!DNL Target]、[!DNL Analytics]和外部目的地的事件 | 啟用資料流上的所有必要服務。 每個服務會分別接收事件。 |

**使用者介面導覽：** [!DNL Experience Platform] >資料收集>資料串流>選取或建立資料串流

**金鑰組態詳細資料：**

- 資料流必須在其進階設定或服務設定下啟用事件轉送
- 將事件轉送屬性（在階段2建立）連結到資料流
- 確認指派給資料流的XDM結構描述符合收集機制所傳送的事件結構

**Experience League檔案：**

- [設定資料串流](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [資料串流概觀](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/overview)
- [事件轉送概觀](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/overview)

### 階段2：事件轉送屬性和擴充功能

**應用程式函式：** AEP：事件轉送屬性設定

**您的設定專案：**&#x200B;資料收集UI中的事件轉送屬性，以及目標目的地所需的擴充功能。 事件轉送屬性是定義伺服器端轉送邏輯之所有規則、資料元素和擴充功能的容器。

此階段中的&#x200B;**決定點：**

>[!NOTE]
>
>**決定：單一屬性與多個屬性的比較**
>
>您應針對所有目的地或個別屬性使用一個事件轉送屬性嗎？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 單一屬性 | 大部分實施；所有轉送規則共用相同的事件資料流 | 管理起來更簡單，只需單一發佈工作流程，所有規則都會針對每個事件進行評估。 使用規則條件來篩選哪些事件移至哪些目的地。 |
>| 多個屬性 | 您需要不同的團隊來獨立管理不同的目的地整合，或您有嚴格的環境隔離要求 | 每個屬性都有自己的發佈工作流程，並可連結至不同的資料串流。 增加管理負荷，但改善存取控制界限。 |

>[!NOTE]
>
>**決定：要安裝哪些擴充功能**
>
>根據您的目標目的地和已選擇的實施選項（以上的A、B或C）選取擴充功能。
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 目的地特定延伸模組（[!DNL Meta]、[!DNL Google]、[!DNL AWS]等） | 目的地有預先建立的擴充功能，而您想要最低限度的自訂設定（選項A或C） | 每個擴充功能都需要目的地特定的憑證（API權杖、測量ID、帳戶ID）。 檢閱擴充功能檔案，瞭解支援的事件型別和必填欄位。 |
>| 僅限Cloud Connector擴充功能 | 所有目的地都將使用自訂HTTP請求（選項B） | 依預設會安裝Cloud Connector擴充功能。 使用「秘密」功能安全地儲存API金鑰和驗證權杖。 |
>| 目的地專屬和雲端聯結器 | 您同時擁有支援和自訂目的地（選項C） | 為支援良好的目標安裝特定擴充功能，並在其餘情況下使用Cloud Connector 。 |

**使用者介面導覽：** [!DNL Experience Platform] >資料收集>事件轉送>建立屬性（或選取現有）

**金鑰組態詳細資料：**

- 使用明確的慣例為屬性命名（例如「Event Forwarding - Production」或「EF - Analytics &amp; Advertising」）
- 安裝[!DNL Adobe Cloud Connector]擴充功能（預設包含於自訂webhook動作中）
- 安裝目的地特定擴充功能並設定其認證
- 使用「秘密」功能（「資料收集>事件轉送>秘密」）安全地儲存API金鑰、權杖和認證
- 設定環境（開發、預備、生產）以利安全發佈工作流程

**Experience League檔案：**

- [事件轉送快速入門](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/tags/event-forwarding/getting-started)
- [事件轉送擴充功能目錄](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/overview)
- [事件轉送密碼](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/secrets)
- [Adobe Cloud Connector擴充功能](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/cloud-connector/overview)

### 階段3：事件規則定義

**應用程式函式：** AEP：事件規則定義，AEP：目的地對應

**您要設定的專案：**&#x200B;規則會評估傳入的事件資料、套用條件以篩選應轉送的事件，以及定義將資料傳送到目的地端點的動作。 每個規則都包含條件（何時引發）和動作（該做什麼）。 資料元素會從XDM事件裝載擷取和轉換值，以用於規則條件和動作設定。

此階段中的&#x200B;**決定點：**

>[!NOTE]
>
>**決定：事件篩選策略**
>
>如何判斷哪些事件會轉送至每個目的地？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 轉寄所有事件 | 目的地需要完整的事件資料流（例如，原始事件儲存的Data Warehouse） | 最簡單的組態 — 不需要任何條件。 目的地的資料量很高。 考量目的地成本與費率限制。 |
>| 依事件型別篩選 | 不同的目的地需要不同的事件型別（例如，廣告的購買、分析的頁面檢視） | 根據`arc.event.xdm.eventType`或類似的XDM欄位使用條件。 減少目的地不必要的資料。 |
>| 依事件屬性篩選 | 只應轉送符合特定條件的特定事件（例如，高於臨界值的購買、特定頁面路徑的事件） | 在規則條件中使用資料元素值。 更複雜，但可減少目的地的雜訊。 |

>[!NOTE]
>
>**決定：資料轉換方法**
>
>如何轉換目的地裝載的XDM事件資料？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 透過資料元素進行直接XDM欄位對應 | 目的地欄位會完全對應至XDM欄位（常見於擴充功能轉送） | 建立參照XDM路徑的資料元素（例如，`arc.event.xdm.commerce.order.priceTotal`）。 擴充功能通常提供對應UI。 |
>| 自訂程式碼轉換 | 目的地需要與XDM截然不同的裝載格式，或欄位需要雜湊、串連或重組 | 使用自訂程式碼資料元素或動作層級自訂程式碼來轉換裝載。 彈性較強，但較難維護。 |
>| 資料元素和自訂程式碼的組合 | 有些欄位會直接對應，有些則需要轉換 | 將資料元素用於簡單對應，並將自訂程式碼區塊用於複雜轉換。 平衡可維護性與彈性。 |

>[!NOTE]
>
>**決定：轉送資料中的PII處理**
>
>在轉送前應該如何處理個人識別資訊？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 完全排除PII欄位 | 目的地不需要PII，且治理原則會限制共用 | 設定規則，忽略轉送裝載中的PII欄位。 最簡單的隱私權合規方法。 |
>| 轉送前的雜湊PII欄位 | 目的地需要雜湊識別碼（例如，[!DNL Meta]需要用於轉換API的SHA-256雜湊電子郵件） | 使用自訂程式碼資料元素套用SHA-256雜湊處理。 有些擴充功能會自動處理雜湊處理。 |
>| 以合約基礎轉送PII | 目的地具有資料處理協定，且共用PII的法律基礎已存在 | 確保資料使用標籤和治理原則(S3)允許共用。 記錄法律基礎。 |

**UI導覽：** [!DNL Experience Platform] >資料收集>事件轉送>選取屬性>資料元素/規則

**金鑰組態詳細資料：**

- **資料元素**&#x200B;使用路徑前置詞`arc.event.xdm.`參考傳入XDM事件（例如，頁面URL的`arc.event.xdm.web.webPageDetails.URL`）
- **規則條件**&#x200B;會評估資料元素值，以判斷是否應該引發規則
- **規則動作**&#x200B;使用擴充功能特有的動作（適用於選項A）或雲端聯結器「發出擷取呼叫」動作（適用於選項B）將資料傳送至目的地
- 每個規則可以有多個動作，可將單一事件轉送至多個目的地
- 同一事件可能觸發多個規則時，可使用規則排序來控制評估順序
- 先在開發環境中徹底測試規則，然後再發佈至生產環境

**選項差異的位置：**

選項A的&#x200B;**（以副檔名為基礎）：**

使用目的地擴充功能的預先建立動作型別來設定規則動作。 例如，[!DNL Meta]轉換API擴充功能提供「傳送事件」動作，讓您將XDM欄位對應至[!DNL Meta]事件引數(event_name、event_time、user_data、custom_data)。 此擴充功能會處理裝載格式、雜湊和API通訊。

選項B （自訂Webhook）的&#x200B;**：**

使用Cloud Connector擴充功能的「發出擷取呼叫」動作來設定規則動作。 指定目的地URL、HTTP方法（通常是POST）、請求標頭（包括授權），並使用資料元素和/或自訂程式碼來建構請求內文。 您必須負責將目的地API的預期裝載格式完全比對。

選項C （混合式）的&#x200B;**：**

為每個目的地建立個別規則。 擴充功能型規則使用擴充功能的動作型別；自訂規則使用雲端聯結器擷取呼叫。 所有規則都共存於相同的屬性中，並針對每個傳入的事件獨立評估。

**Experience League檔案：**

- [事件轉送規則](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/overview)
- [事件轉送中的資料元素](https://experienceleague.adobe.com/en/docs/experience-platform/tags/ui/data-elements)
- [資料彙集中的規則](https://experienceleague.adobe.com/en/docs/experience-platform/tags/ui/rules)
- [Adobe Cloud Connector擴充功能](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/cloud-connector/overview)

### 第4階段：發佈與啟用

**應用程式函式：** AEP：轉送執行

**您要設定的專案：**&#x200B;會提升您的事件轉送規則（從開發到測試，再到生產）的發佈工作流程。 事件轉送會使用與標籤相同的程式庫型發佈模型，搭配環境和建置成品，以控制Edge Network中啟用的設定。

此階段中的&#x200B;**決定點：**

>[!NOTE]
>
>**決定：發佈工作流程嚴格**
>
>發佈程式應該有多嚴格？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 直接到生產（開發>生產） | 小型團隊、低風險目的地或概念驗證實作 | 部署速度更快，但發生生產問題的風險也更高。 適合用於非關鍵目的地的初始測試。 |
>| 完整環境進度（開發>預備>生產） | 重要目的地（廣告平台、資料倉儲）的生產實作 | 建議用於所有生產使用案例。 中繼功能可讓您在生產部署之前使用真實流量進行驗證。 |

**使用者介面導覽：** [!DNL Experience Platform] >資料收集>事件轉送>選取屬性>發佈流程

**金鑰組態詳細資料：**

- 建立程式庫，其中包含要發佈的所有規則、資料元素和擴充功能設定
- 先使用事件轉送監視工具在開發環境中進行建置和測試，以驗證事件已正確轉送
- 提升至測試環境，以使用即時流量進行生產前驗證
- 只有在測試中確認成功事件傳送後才會發佈至生產環境
- 使用程式庫版本設定來追蹤變更，並視需要啟用回覆

**Experience League檔案：**

- [發佈概觀](https://experienceleague.adobe.com/en/docs/experience-platform/tags/publish/overview)
- [資料庫](https://experienceleague.adobe.com/en/docs/experience-platform/tags/publish/libraries)
- [環境](https://experienceleague.adobe.com/en/docs/experience-platform/tags/publish/environments)
- [組建](https://experienceleague.adobe.com/en/docs/experience-platform/tags/publish/builds)

### 階段5：監控與驗證

**應用程式函式：** AEP：監視

**您要設定的專案：**&#x200B;監視儀表板和驗證程式，以確認事件轉送成功、診斷失敗並維護事件轉送部署的運作狀況。

此階段中的&#x200B;**決定點：**

>[!NOTE]
>
>**決定：監視深度**
>
>事件轉送的監控深度為何？
>
>| 選項 | 何時選擇 | 考量事項 |
>| --- | --- | --- |
>| 僅限事件轉送監視儀表板 | 對非關鍵目的地或初始部署進行基本監控 | 提供轉送成功/失敗率和目的地回應代碼的概觀。 足以進行大部分的實作。 |
>| 事件轉送監控+目的地端驗證 | 資料完整度直接影響業務成果的關鍵目的地（廣告轉換追蹤、資料倉儲完整性） | 互動參照Adobe端轉送量度與目的地端回條確認。 擷取目標接受請求但無法處理資料的邊緣案例。 |
>| 完整可觀察性棧疊（事件轉送監控+目的地驗證+ AEP警報） | 具備SLA資料傳送需求的企業級部署 | 結合事件轉送監控與AEP平台警報，以提供全面檢視。 設定轉送失敗臨界值的警示通知。 |

**使用者介面導覽：** [!DNL Experience Platform] >資料收集>事件轉送>選取屬性>監視

**金鑰組態詳細資料：**

- 「事件轉送監視」工具會顯示每個規則和每個目的地的事件數量、成功率和錯誤詳細資料
- 監視目的地的HTTP回應代碼 — 2xx表示成功，4xx表示使用者端錯誤（可能是承載或驗證問題），5xx表示目的地端失敗
- 使用[!DNL Adobe Experience Platform Debugger]瀏覽器擴充功能來檢查從使用者端透過Edge Network流向事件轉送規則的事件
- 檢查轉送的事件是否出現在目的地系統中（例如，檢查[!DNL Google Analytics]即時報表、[!DNL Meta]事件管理員或資料倉儲表格），以端對端驗證
- 針對來源和資料流失敗設定AEP警報，以擷取可能會阻止事件到達事件轉送規則的上游問題

**Experience League檔案：**

- [事件轉送監控](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/monitoring)
- [Adobe Experience Platform Debugger](https://experienceleague.adobe.com/en/docs/experience-platform/debugger/home)
- [警報概觀](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)

## 實施考量

本節涵蓋在整個實施中牢記的護欄、常見陷阱、最佳實務和取捨決定。

### 護欄和限制

- 事件轉送會在Edge Network即時處理事件 — 預設情況下，失敗的傳送沒有批次模式或重試佇列
- Edge Network速率限制適用於每個資料流處理的事件數量總計 — [Edge Network護欄](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/guardrails)
- 事件轉送規則執行伺服器端且無法存取使用者端資源(DOM、Cookie、localStorage)
- 事件轉送規則中的自訂程式碼在沙箱化環境中執行 — 並非所有瀏覽器JavaScript API都可用
- 雲端聯結器擷取呼叫具有逾時限制 — 回應緩慢的目的地可能會導致逾時
- 事件轉送須遵循Edge Network地理路由，事件會於最近的Edge位置處理
- 轉送請求的裝載大小上限受Edge Network限制所規範

### 常見陷阱

- **轉送所有XDM欄位而不篩選：**&#x200B;將整個XDM事件裝載傳送到只需要幾個欄位的目的地，會浪費頻寬、增加目的地成本，而且可能會不慎共用PII。 永遠只對應轉送規則中的必要欄位。

- **未使用密碼保護認證：**&#x200B;資料元素或規則動作中的硬式編碼API金鑰或權杖會產生安全性風險。 請一律使用資料收集機密功能，以安全地儲存認證，並在規則中參照。

- **忽略目的地速率限制：**&#x200B;協力廠商目的地通常有API速率限制。 如果您的事件數量超過目的地的容量，可能會捨棄事件或限制您的API存取權。 檢閱目的地檔案以瞭解速率限制，並視需要實施篩選以減少事件量。

- **直接發佈至生產環境而不進行暫存：**&#x200B;略過暫存環境表示只在生產環境中發現錯誤，可能會導致重要目的地的資料遺失。 一律在測試環境中先使用即時流量進行驗證。

- **未監視HTTP回應代碼：**&#x200B;引發無錯誤的規則，無法保證目的地成功處理資料。 監視目的地回應代碼（可在「事件轉送監視」工具中使用），並調查任何非2xx的回應。

- **設定錯誤的XDM路徑參考：**&#x200B;資料元素使用`arc.event.xdm.`首碼來參考傳入的事件欄位。 不正確的路徑（例如，遺漏某個層級的巢狀）會無訊息地產生null值，而不會擲回錯誤。 使用Debugger驗證資料元素值。

### 最佳實務

- **從單一目的地開始，然後逐步展開** — 在新增其他規則和目的地之前，先驗證單一目的地的端對端事件轉送。 這可簡化除錯作業，並建立對基礎結構的信心。

- **使用一致的命名慣例** — 使用可識別目的地、事件型別和環境的明確慣例來命名資料元素、規則和程式庫（例如「規則：Meta — 購買事件」、「DE：訂購總計」）。

- **針對隱私權實作欄位層級篩選** — 即使目的地聲稱已適當處理PII，仍可套用伺服器端篩選，以在欄位離開Edge Network前移除或雜湊敏感欄位。 這是事件轉送勝過使用者端標籤的主要控管優勢。

- **設定版本** — 使用程式庫發佈工作流程來維護事件轉送設定的版本化快照。 記錄每個程式庫版本包含的內容，以供稽核和復原之用。

- **使用Platform Debugger進行測試** — [!DNL Adobe Experience Platform Debugger]擴充功能可讓您從使用者端SDK透過Edge Network處理檢視事件生命週期。 在開發和疑難排解期間使用。

- **將事件轉送規則與您的XDM結構描述設計對齊** — 如果事件轉送是已知的需求，請設計您的XDM結構描述和事件分類以包含目的地所需的欄位。 部署後更新結構描述變更更具破壞性。

### 權衡決定

>[!NOTE]
>
>**取捨：擴充簡單與webhook彈性**
>
>預先建立的擴充功能可將實作工作和維護作業降至最低，但僅限於您使用擴充功能支援的功能和裝載格式。 自訂Webhook提供完整控制，但需要更多開發和持續維護。
>
>- **以延伸功能為基礎的（選項A）優點：**&#x200B;上市速度快、減少開發人員相依性、自動認證管理、降低維護成本
>- **以Webhook為基礎的（選項B）偏好：**&#x200B;完整裝載控制、支援任何HTTP端點、自訂轉換邏輯、獨立於擴充功能發行週期
>- **建議：**&#x200B;當可用且足夠時，請使用副檔名。 只有在目的地缺少擴充功能或擴充功能不支援您所需的特定API功能時，才能回覆為自訂Webhook。 混合式方法（選項C）是大多陣列織務實的選擇。

>[!NOTE]
>
>**取捨：轉寄所有事件與選擇性篩選**
>
>將所有事件轉送至目的地，可確保完整性，但會增加資料量、目的地成本和隱私權風險。 選擇性篩選可減少雜訊，但可能遺漏有價值的事件。
>
>- **轉寄所有事件均有利於：**&#x200B;資料完整性、簡潔性、可保證未來性（日後需要時資料會存在）
>- **選擇性篩選偏好：**&#x200B;成本效益、降低隱私權風險、清除目的地資料、遵循資料最小化原則
>- **建議：**&#x200B;預設為根據事件型別和業務關聯性進行選擇性篩選。 僅轉送每個目的地實際需要的事件和欄位。 這符合資料最小化的原則（GDPR第5條），並降低了營運成本。

>[!NOTE]
>
>**取捨：單一屬性與多個屬性**
>
>單一事件轉送屬性更易於管理，但表示所有規則共用一個發佈工作流程。 多個屬性提供隔離功能，但會增加管理負荷。
>
>- **單一屬性偏好：**&#x200B;簡單性、統一發佈、共用資料元素、更易於偵錯
>- **多個屬性偏好：**&#x200B;團隊層級存取控制、獨立發佈步調、隔離目的地失敗
>- **建議：**&#x200B;對於大多數實作以單一屬性開始。 只有當不同的團隊擁有不同的目的地整合，並且需要獨立的發行週期，或是法規要求必須在資料流程之間嚴格隔離時，才會分割為多個屬性。

## 相關文件

下列資源提供本指南涵蓋主題的額外詳細資料。

**事件轉送**

- [事件轉送概觀](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/overview)
- [事件轉送快速入門](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/tags/event-forwarding/getting-started)
- [事件轉送監控](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/monitoring)
- [事件轉送密碼](https://experienceleague.adobe.com/en/docs/experience-platform/tags/event-forwarding/secrets)

**事件轉送延伸模組**

- [伺服器端擴充功能目錄](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/overview)
- [Adobe Cloud Connector擴充功能](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/cloud-connector/overview)
- [Meta Conversions API擴充功能](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/meta/overview)
- [Google Cloud Platform擴充功能](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/google-cloud-platform/overview)
- [AWS擴充功能](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/aws/overview)
- [Snowflake擴充功能](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/tags/extensions/server/snowflake/overview)
- [Google Ads增強型轉換延伸功能](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/google-ads-enhanced-conversions/overview)
- [Mailchimp擴充功能](https://experienceleague.adobe.com/en/docs/experience-platform/tags/extensions/server/mailchimp/overview)

**資料收集和Edge Network**

- [設定資料串流](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [資料串流概觀](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/overview)
- [網頁SDK概觀](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Edge Network伺服器API總覽](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)
- [標籤總覽](https://experienceleague.adobe.com/en/docs/experience-platform/tags/home)
