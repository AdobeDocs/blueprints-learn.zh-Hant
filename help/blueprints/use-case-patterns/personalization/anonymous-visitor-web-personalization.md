---
title: 匿名訪客網頁Personalization
description: 瞭解如何根據工作階段中的行為訊號，將個人化網頁內容傳遞給無法識別的訪客。
solution: Journey Optimizer, Real-Time Customer Data Platform
source-git-commit: 126dd712603494513b71a8a6e1c4b99bdb7ff212
workflow-type: tm+mt
source-wordcount: '8076'
ht-degree: 1%

---


# 匿名訪客網頁個人化

此參考計畫提供實施指引，可讓您根據工作階段行為訊號，將個人化網頁內容提供給匿名（無法識別）訪客。 它涵蓋完整的實作生命週期（從[!DNL Web SDK]設定和邊緣對象定義，到內容傳遞和效能報告），是專為使用[!DNL Adobe Journey Optimizer] (AJO)、[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)和[!DNL Adobe Experience Platform] (AEP)的解決方案架構師、行銷技術人員和實作工程師所設計。

使用此計畫來瞭解架構、評估實作選項、做出明智的設定決策，並找出每個實作階段的相關Experience League檔案。

此模式適用於有限的資料 — 只有可以在目前工作階段中觀察到的內容，以及透過相同裝置或Cookie的先前造訪累積的任何匿名邊緣設定檔。 這使其適用於funnel頂端個人化，其中訪客沒有帳戶或尚未驗證。

## 使用案例概述

匿名訪客Web Personalization滿足企業需求，將相關的個人化內容傳送給尚未識別的網站訪客 — 他們尚未登入、沒有已知的身分，且無法解析為統一的客戶設定檔。 儘管有此限制，使用工作階段中的行為訊號仍可達成有意義的個人化：已檢視頁面、網站逗留時間、捲動深度、轉介來源、地理位置、裝置型別和UTM促銷活動引數。

此模式使用AJO的Web Channel介面和程式碼型體驗來即時修改頁面內容。 Edge細分是主要的評估方法，因為當訪客瀏覽網站時，必須在次秒延遲的情況下做出決定。 [!DNL Web SDK]會收集行為訊號並將其傳送至[!DNL AEP Edge Network]，以邊緣評估的對象規則來決定要傳送的內容變體。

不同於已知訪客的網頁/應用程式個人化（會利用完整的統一設定檔和區段成員資格），此模式受限於目前工作階段中可觀察到的資料，以及與訪客的ECID ([!DNL Experience Cloud ID])相關聯的任何匿名邊緣設定檔。 這項區別對實作規劃至關重要：可用於個人化的行為訊號僅限[!DNL Web SDK]所擷取的內容，以及透過Cookie式ECID跨工作階段保留在邊緣設定檔存放區中的內容。

## 主要業務目標

此使用案例模式支援下列業務目標。

**[增加網站參與度](../../business-objectives/acquisition-growth/increase-website-engagement.md)**

透過為匿名訪客訊號量身打造的相關體驗，改善網站逗留時間、每個工作階段頁面數以及與網路內容的互動關係。

| KPI |
| --- |
| Time On （網頁）頁面 |
| 參與度 |
| 轉換率 |

**[提供個人化的客戶體驗](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**

根據個別偏好、行為和生命週期階段量身打造內容、選件和訊息，即使訪客尚未自我識別。

| KPI |
| --- |
| 參與度 |
| 轉換率 |
| 客戶滿意度(CSAT) |

**[提高轉換率](../../business-objectives/revenue-monetization/increase-conversion-rates.md)**

根據行為情境提供最相關的內容，藉此提高完成所需動作（例如購買、註冊或表單提交）的訪客和潛在客戶百分比。

| KPI |
| --- |
| 轉換率 |
| 潛在客戶轉換 |
| 每個潛在客戶的成本 |

## 戰術使用案例範例

下列範例說明可套用此模式的特定案例。

- **根據反向連結來源進行的登陸頁面標題A/B測試** — 針對來自Google、社群媒體或直接流量的訪客測試不同的標題，以透過贏取管道最佳化參與
- **以瀏覽行為為基礎的類別相關性建議** — 根據目前工作階段中檢視的頁面顯示產品或內容建議，以提高探索和轉換
- **即將離開的訪客退出意向優惠** — 當行為訊號指出訪客即將放棄網站時，提供促銷優惠或銷售機會擷取表單
- **地理目標促銷橫幅** — 根據訪客的地理位置，顯示特定位置的促銷活動、商店定位器內容或區域優惠方案
- **裝置特定內容版面最佳化** — 根據訪客使用桌上型電腦、平板電腦或行動裝置，調整內容版面、影像大小和CTA版面
- **新訪客與回訪訪客的歡迎訊息** — 區分首次訪客與使用ECID跨工作階段持續性的回訪匿名訪客體驗
- **根據目前工作階段中已檢視頁面內容推薦** — 根據訪客已檢視的頁面動態顯示相關文章、產品或資源
- **以UTM行銷活動引數為基礎的動態主圖橫幅** — 個人化主圖橫幅，以符合引用行銷活動的訊息或創意

## 關鍵績效指標

使用下列KPI來評估此使用案例模式的成效。

| KPI | 說明 | 測量方法 |
| --- | --- | --- |
| Personalization曝光率 | 合格頁面檢視中已傳遞個人化內容的百分比 | AJO行銷活動報告：曝光數/頁面檢視總數 |
| 點進率(CTR) | 導致點按的個人化內容曝光百分比 | AJO促銷活動報告：點按數/曝光數 |
| 參與提升度 | 增加個人化與預設內容的頁面時間、每個工作階段頁面或捲動深度 | CJA工作區比較：個人化同類群組與控制 |
| 轉換率 | 接觸到個人化內容並完成所需動作的訪客百分比 | CJA funnel analysis：曝光數>互動>轉換 |
| 跳出率降低 | 接收個人化內容之訪客的單頁工作階段減少 | CJA工作階段分析：個人化與預設的跳出率差異 |
| 實驗成功率 | 產生統計上顯著獲勝者的A/B測試百分比 | AJO實驗報告：實驗達到信賴臨界值 |

## 使用案例模式

以下說明此使用案例的核心模式與功能鏈。

**匿名訪客網頁Personalization**

透過AJO Web Channel，根據工作階段中的行為訊號，為無法識別的訪客提供個人化內容。

**函式鏈：**&#x200B;網頁介面設定>行為規則評估>內容傳送>曝光追蹤>報告

## 應用程式

在此使用案例模式中使用以下應用程式。

- **[!DNL Adobe Journey Optimizer] (AJO)** — Web頻道介面設定、內容製作（網頁和程式碼型體驗）、行銷活動執行、內容實驗（A/B測試）、決策（動態內容選擇）和報告
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** — 根據工作階段中行為訊號進行即時對象評估的Edge細分；匿名邊緣設定檔管理
- **[!DNL Adobe Experience Platform] (AEP)** — [!DNL Web SDK]用於行為訊號收集，[!DNL Edge Network]用於即時資料路由和個人化傳遞，資料流設定

## 基礎函式

下列基本功能必須為此使用案例模式準備就緒。 對於每個函式，狀態會指出它通常是必要的、假設為預先設定或不適用。

| 基礎函式 | 狀態 | 必須準備就緒的專案 | Experience League參考 |
| --- | --- | --- | --- |
| 管理與治理 | 已假設就位 | 已設定Web Channel許可權的AJO沙箱。[!DNL Web SDK] 授予實作團隊的實作許可權和資料流存取權。 為使用者布建了允許Web通路設定、受眾管理和行銷活動執行的角色。 | [存取控制總覽](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| 資料模型與準備 | 必填 | 體驗事件結構描述擷取網頁行為訊號（頁面檢視、點選、捲動深度、轉介資料、UTM引數）。 結構描述必須包含標準Web互動欄位群組，並啟用邊緣設定檔以支援即時評估。 必須建立對應的資料集並啟用設定檔。 | [XDM系統總覽](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home) |
| 資料來源與收集 | 必填 | 必須在所有目標Web屬性上實作[!DNL Web SDK]，且資料流設定為將資料路由至[!DNL AEP Edge Network]。 資料流必須啟用[!DNL Adobe Experience Platform]和[!DNL Adobe Journey Optimizer]服務。 這是關鍵相依性 — 如果沒有[!DNL Web SDK]，就無法進行行為訊號收集或體驗傳送。 | [Web SDK 概觀](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home) |
| 身分和設定檔設定 | 必填 | ECID ([!DNL Experience Cloud ID])已設定為匿名訪客的主要身分名稱空間。 必須使用`isActiveOnEdge: true`設定Edge合併原則，才能解析邊緣的匿名設定檔資料。 每個沙箱的Edge上只能有一個作用中的合併原則。 | [身分識別服務總覽](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home) |
| 對象定義與細分 | 必填 | 根據工作階段內行為訊號定義的Edge評估對象區段。 必須設定Edge區段，才能進行次秒的評估延遲。 區段規則只能使用符合邊緣的區段規則運算式（簡單屬性檢查和區段成員資格 — 沒有時間序列查詢或複雜彙總）。 | [Edge區段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation) |

## 支援功能

以下功能可擴大此使用案例模式，但不是核心執行的必要功能。

| 支援功能 | 狀態 | 為什麼這很重要 | Experience League參考 |
| --- | --- | --- | --- |
| 計算/衍生屬性建立 | 不適用 | 匿名訪客的值有限，因為有最低的歷史設定檔資料需要彙總。 如果邊緣設定檔累積來自先前跨多個工作階段匿名造訪的有意義行為資料，則可能變得適用。 | [計算屬性總覽](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| 資料生命週期管理 | 推薦 | 匿名邊緣設定檔的匿名設定檔過期時間應已設定，以管理儲存空間並遵守隱私權要求。 僅限ECID的設定檔可設為在14到365天之間過期。 應為行為資料收集強制執行Cookie同意原則。 | [進階資料生命週期管理概觀](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| 資料使用標籤和實作 | 推薦 | 行為資料上的控管標籤可確保法規遵循，尤其是針對地理定位（S2敏感地理標籤）和以裝置為基礎的個人化。 標籤可防止在未經授權的個人化內容中使用受限制的行為資料。 | [資料控管概觀](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home) |
| 監控與可觀察性 | 推薦 | [!DNL Edge Network]和[!DNL Web SDK]資料流程監視可協助偵測個人化傳遞問題。 設定資料流失敗、擷取錯誤和邊緣傳送異常的警報。 在生產部署中，個人化失敗會降低訪客體驗，因此至關重要。 | [可觀察性深入分析概觀](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| 報告與分析 | 已包含 | Personalization效能報告是功能鏈（階段5）的一部分。 CJA對匿名訪客個人化成效的分析可讓您進行深入的funnel分析、同類群組比較，以及轉換影響測量，超出AJO原生報表所能提供的範圍。 | [CJA概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) |

## 應用程式函式

此計畫會從「應用程式功能目錄」中執行下列功能。 函式會對應至實作階段，而非編號步驟。

### [!DNL Journey Optimizer] (AJO)

| 函式 | 實作階段 | 說明 |
| --- | --- | --- |
| 通道設定 | 階段1：網頁表面設定 | 設定Web頻道介面，定義將在目標Web屬性上傳送個人化內容的位置 |
| 訊息製作 | 階段3：內容製作和變體建立 | 使用網頁設計工具、程式碼型體驗編輯器或內容範本，製作網頁介面的個人化內容變體 |
| 行銷活動執行 | 階段4：行銷活動和傳遞設定 | 建立並啟用繫結對象、內容和傳遞設定的網頁行銷活動 |
| 決策 | 階段3：內容製作與變體建立（選項C） | 根據行為訊號設定動態內容選擇的決定政策、適用規則和排名策略 |
| 內容實驗 | 階段3：內容製作和變體建立（選項B） | 使用流量分配、成功量度和信賴度臨界值設定A/B和多變數內容實驗 |
| 報告與效能分析 | 第5階段：報告與效能分析 | 監控個人化傳遞量度、變異有效性、實驗結果和轉換影響 |

### [!DNL Real-Time CDP] (RT-CDP)

| 函式 | 實作階段 | 說明 |
| --- | --- | --- |
| 對象評估 | 階段2：行為對象定義 | 使用工作階段中的行為訊號來定義及評估邊緣型受眾區段，以利即時個人化目標定位 |

## 先決條件

開始實作前請先完成下列作業。

- [ 已在所有目標Web屬性上實作] [!DNL Web SDK]，其中`sendEvent`個呼叫會擷取頁面檢視、點按和相關行為互動
- [ 已在資料收集UI中設定]資料串流，並啟用[!DNL Adobe Experience Platform]和[!DNL Adobe Journey Optimizer]服務
- [ ]體驗事件結構描述與網頁互動欄位群組（頁面檢視、轉介資料、UTM引數、裝置內容）同時存在，且已為設定檔啟用
- [ ] ECID身分名稱空間已設定並在網頁行為事件結構描述上指定為主要身分
- [ ] Edge合併原則已使用`isActiveOnEdge: true`在目標沙箱中設定
- [ ] AJO Web Channel已布建並可在目標沙箱中存取
- [ 針對每個個人化使用案例設計和核准]個內容變體（復本、影像、CTA）
- [ 已定義]個成功量度（構成測量的轉換或參與事件）
- [ 在收集行為資料之前，已在網站上實作] Cookie同意機制以符合隱私權法規

## 實作選項

本節說明三種實作方法。 選取最符合您個人化需求的選項。

### 選項A：規則型網頁個人化

**最適合：**&#x200B;簡單、決定性的個人化 — 地理定位橫幅、參照來源專屬標題、裝置專屬配置、新造訪與回訪訪客訊息。 當內容變體可由直接的條件邏輯判斷時（如果條件X是顯示內容Y），請選擇此選項。

**運作方式：**

規則型個人化使用邊緣評估的對象區段，以判斷訪客看到哪個內容變體。 每個受眾區段會透過行銷活動中定義的條件規則，對應至特定內容變體。 當訪客載入頁面時，[!DNL Web SDK]會將行為訊號傳送至[!DNL Edge Network]，其會根據定義的對象規則（以毫秒為單位）評估訪客的邊緣設定檔。 相符的內容變體會在[!DNL Edge Network]回應中傳回，並在頁面上呈現。

此方法需要在RT-CDP中定義不同的受眾區段（例如「來自Google搜尋的訪客」、「加利福尼亞的訪客」、「行動裝置訪客」），並在AJO中建立對應的內容變體。 行銷活動會使用條件式內容規則或每個區段的個別行銷活動，將每個對象繫結至其內容變體。 不涉及AI排名或流量分割 — 對象與內容之間的關係是決定性的。

**主要考量事項：**

- 需要定義良好的對象條件，可表示為符合邊緣條件的區段規則運算式
- 每個受眾區段都必須預先編寫內容變體
- 新增個人化規則需要建立新的受眾區段和內容變體
- 不提供內容變體有效性的統計測量

**優點：**

- 最容易實作和瞭解 — 清楚對象與內容之間的因果關係
- 不需要實驗性開銷或流量分割
- 確定性行為可讓測試和QA變得簡單明瞭
- 低延遲，因為邊緣評估純粹以規則為基礎
- 當企業已知道哪些內容最適合每個區段時，就可有效運作

**限制：**

- 沒有內建機制可測量個人化是否比預設內容改善結果
- 需要手動決定要顯示每個區段哪些內容
- 不會隨時間調整或最佳化 — 靜態規則，直到手動變更為止
- 縮放至許多區段和變體會增加設定的複雜性

**Experience League：**

- [開始使用網路頻道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [邊緣分段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)

### 選項B：實驗型網頁個人化

**最適合：** A/B和多變數測試 — 測試標題變體、CTA按鈕顏色、版面選擇、促銷優惠 — 具有統計顯著性測量。 當您需要在認可永久個人化規則之前驗證哪個內容變體表現最佳時，請選擇此選項。

**運作方式：**

實驗型個人化使用AJO內容實驗來隨機將訪客分配給內容處理群組，並測量哪個變體對於定義的成功量度執行得最好。 流量會分割成不同的變體（例如A/B為50/50，A/B/C為33/33/34），而且會追蹤效能，直到達到統計顯著性為止。

實驗內嵌於AJO網路行銷活動中。 當訪客載入頁面時，[!DNL Edge Network]會根據設定的流量分配，將頁面指派給處理群組。 訪客在實驗期間持續看到相同的處理方式（工作階段層級或訪客層級的持續性取決於設定）。 成功量度（點按數、轉換、參與事件）會透過[!DNL Web SDK]進行追蹤，並在AJO實驗報告中回報。

此選項不需要預先定義的對象區段來鎖定目標 — 所有訪客（或目標子集）都會參與實驗。 目標是找出哪些內容執行效果最佳，而非以預先決定的內容鎖定已知區段。

**主要考量事項：**

- 需要足夠的流量以在合理的時間範圍內達到統計顯著性
- 實驗使用具有隨時有效信賴區間的貝葉斯統計模型
- 建議使用保留群組（不接收任何個人化內容）來測量遞增提升度
- 一次每個行銷活動只能有一個實驗處於作用中
- 實驗修改需要停止和重新啟動行銷活動

**優點：**

- 提供對內容變體有效性的統計上嚴格測量
- 從個人化決定中移除猜測 — 資料導向內容選擇
- 支援保留群組以進行真正的增量提升度測量
- 內建實驗報告，包含信賴區間和獲勝者宣告
- 識別成功變體可為未來規則型個人化（選項A）提供資訊

**限制：**

- 需要有意義的流量 — 低流量頁面可能需要數週才能顯效
- 流量分割表示有些訪客在測試期間看到次優內容
- 在實驗期間無法依區段進行個人化（所有訪客或子集平等參與）
- 每個實驗最多10個處理變體
- 沒有持續最佳化 — 實驗是離散的，有開始和結束

**Experience League：**

- [開始使用內容實驗](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [建立內容實驗](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [內容實驗報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)

### 選項C：決策式網頁個人化

**最適合：**&#x200B;動態內容選擇 — 類別相關性建議、退出意圖選件、行為建議 — 決策原則會評估工作階段訊號並從合格專案的目錄中選取最佳內容。 當內容選擇邏輯對於簡單規則而言太複雜、您想要以AI排名最佳化，或符合資格的內容專案集龐大且動態時，請選擇此選項。

**運作方式：**

決策型個人化使用AJO決策來評估行為訊號，並從受管理的內容專案（選件）目錄中為每個訪客選取最佳內容變體。 每個內容專案都有適用性規則（符合者）、表示（內容在每個版位中看起來是什麼樣子）和選用的上限限制（顯示的頻率）。 決策原則會將位置（內容會顯示在頁面上）連結至內容專案集合，並套用排名策略以選取最佳選項。

當訪客載入頁面時，[!DNL Web SDK]會傳送包含決定範圍的[!DNL Edge Network]要求。 決策引擎會根據內容專案適用性規則評估訪客的邊緣設定檔、套用排名策略（優先順序、公式或AI排名），並傳回成功的內容專案。 這會發生在邊緣，延遲時間為亞秒。

排名策略會決定如何訂購符合資格的內容專案。 以優先順序為基礎的排名會使用手動指派的優先順序值。 公式式排名使用自訂運算式（例如，加權頁面檢視的造訪間隔）。 AI排名排名使用的機器學習模型會隨著時間針對所選的成功量度進行最佳化，但訓練至少需要1,000個轉換事件。

**主要考量事項：**

- 需要設定決定元件：位置、適用性規則、內容專案、遞補專案、集合和決定原則
- AI排名策略需要足夠的轉換量（1,000+個事件）來訓練模型
- Edge決定僅限於邊緣設定檔存放區中可用的設定檔屬性
- 內容專案必須在決策程式庫中管理和維護
- 必須在沒有個人化專案符合資格的情況下定義遞補內容

**優點：**

- 可擴充至大型內容目錄，無需個別對象對內容的對應
- AI排名策略會根據觀察到的效能，持續最佳化內容選擇
- 適用性規則和上限限制可提供對內容傳送的精細控制
- 支援難以表達為受眾區段的複雜商業邏輯
- 跨管道可重複使用 — 相同的決策原則可支援網頁、電子郵件和行動個人化

**限制：**

- 更高的實作複雜性 — 需要設定完整的決定元件棧疊
- AI排名需要大量的轉換量，以及有效訓練的時間
- Edge設定檔資料限制會限制匿名訪客的適用性規則複雜性
- 內容專案管理負荷 — 每個專案都需要表示方式、適用性規則及維護
- 偵錯決策邏輯比規則型方法更複雜

**Experience League：**

- [決策管理概觀](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [建立產品建議放置環境](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [建立個人化優惠方案](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [建立決定](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)

### 選項比較

下表比較各個關鍵條件的三個實作選項。

| 條件 | 選項A：規則型 | 選項B：實驗 | 選項C：決策 |
| --- | --- | --- | --- |
| 最適合 | 已知的區段對內容對應 | 探索哪些內容效果最佳 | 從大型目錄選取動態內容 |
| 複雜性 | 低 | 中 | 高 |
| 延遲 | 次秒（邊緣） | 次秒（邊緣） | 次秒（邊緣） |
| Personalization精確度 | 區段層級（對象規則） | 訪客層級（隨機指派） | 訪客層級（資格+排名） |
| 內容最佳化 | 手動（無測量） | 統計測試(A/B) | 連續（AI排名）或手動（優先順序） |
| 需要對象區段 | 是（邊緣評估） | 否（流量分割） | 選擇性（適用性規則） |
| 測量功能 | 無內建（需要CJA） | 內建實驗報告 | 內建決策報告 |
| 內容目錄大小 | 小（1:1區段對內容） | 小型（2-10種變體） | 大型（不限數量的合格專案） |
| 需要 | Edge對象，內容變體 | 已啟用實驗的行銷活動 | 決策元件（位置、優惠、原則） |

### 選擇正確的選項

使用下列決定邏輯來選取適當的實施選項：

1. **您已經知道應該向每個訪客區段顯示哪些內容嗎？**
   - 是：以&#x200B;**選項A （規則型）**&#x200B;開始。 您已為每個區段建立內容策略，且需要確定性傳遞。
   - 否：繼續問題2。

2. **您是否需要測試少量內容變體來尋找績效最佳者？**
   - 是：選擇&#x200B;**選項B （實驗）**。 您想要在認可內容策略之前進行統計驗證。
   - 否：繼續問題3。

3. **您是否有大型的內容專案目錄具有複雜的資格和排名需求？**
   - 是：選擇&#x200B;**選項C （決策）**。 您需要可調整範圍超過簡單規則的動態內容選擇。
   - 否：從簡單的&#x200B;**選項A （規則型）**&#x200B;開始，然後隨著需求增長演化至選項B或C。

**組合選項：**&#x200B;這些選項不是互斥的。 常見的進展是從選項B （實驗）開始以探索成功內容，然後使用選項A （規則型）部署成功者以進行持續傳送。 選項C （決策）可以依序棧疊在需要動態目錄型選擇的使用案例上，而選項A則可處理較簡單的確定性規則。

## 實作階段

下列階段說明端對端實作工作流程。

### 階段1：設定網頁介面

**應用程式函式：** AJO：頻道設定

定義Web Channel介面，指定將傳送個人化內容於您網站上的哪個位置。 網頁表面可識別特定頁面URL或URL模式，以及AJO可插入或取代內容的頁面位置（CSS選擇器或程式碼型體驗表面）。

此階段中的&#x200B;**決定點：**

>[!NOTE]
>**決定：表面型別** — 應該如何將個人化內容傳遞至頁面？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 網頁管道（視覺化編輯器） | 個人化涉及使用拖放視覺編輯器來修改可見的頁面元素（橫幅、標題、影像、CTA） | 需要網頁設計工具瀏覽器擴充功能。 最適合行銷導向的內容變更。 僅限於現有頁面元素的視覺化修改。 |
| 程式碼型體驗 | 個人化需要插入網站應用程式程式碼使用和轉譯的結構化資料(JSON) | 需要開發人員實作才能使用JSON裝載。 為複雜的個人化提供最大彈性。 最適合SPA、動態元件和程式化轉譯。 |
| 兩者（混合） | 相同網站上的不同個人化需要不同的傳遞機制 | 使用Web Channel進行簡單的視覺變更，並使用程式碼型體驗進行程式化轉譯。 增加實作的複雜性，但將涵蓋範圍最大化。 |

>[!NOTE]
>**決定：介面範圍** — 網頁介面應該涵蓋哪個URL範圍？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 完全URL相符 | Personalization鎖定特定頁面（例如首頁、登陸頁面） | 最精確的目標定位。 每個頁面都需要個別的表面。 |
| 包含萬用字元的URL模式 | Personalization適用於某個頁面類別（例如，所有產品頁面、所有部落格） | 減少表面管理額外負荷。 內容變體必須設計為可在所有相符頁面中使用。 |
| 單頁應用程式(SPA)表面 | 網站是SPA，其URL變更不會觸發完整頁面重新載入 | 檢視變更需要SPA感知[!DNL Web SDK]設定和`sendEvent`呼叫。 表面定義使用SPA檢視名稱，而非URL。 |

**使用者介面導覽：** [!DNL Journey Optimizer] >管理>管道> Web設定

**金鑰組態詳細資料：**

- 定義表面的頁面URL或URL模式
- 指定內容放置的CSS選取器或表面URI
- 針對程式碼型體驗，定義應用程式程式碼將參照的曲面名稱
- 將表面與將建立行銷活動的AJO沙箱建立關聯

**Experience League檔案：**

- [開始使用網路頻道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [建立網站體驗](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [程式碼型體驗管道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/get-started-code-based)
- [程式碼型體驗設定](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/code-based-configuration)

### 第2階段：定義行為對象

**應用程式函式：** RT-CDP：對象評估

根據推動個人化鎖定的工作階段內行為訊號，定義邊緣評估的受眾區段。 這些對象會決定哪些訪客符合每個個人化體驗的資格。 此模式強制進行Edge評估，因為訪客導覽網站時，必須在次秒的時間範圍內做出個人化決策。

此階段中的&#x200B;**決定點：**

>[!NOTE]
>**決定：行為訊號選擇** — 哪個工作階段中的訊號應該推動個人化目標定位？

| 訊號 | 使用時機 | Edge資格 |
| --- | --- | --- |
| 轉介來源/UTM引數 | 促銷活動專屬登陸頁面個人化 | 合格 — 目前事件的簡單屬性檢查 |
| 地理位置（國家/地區、城市） | 地區促銷活動、特定語言內容、商店定位程式 | 合格 — 設定檔屬性檢查 |
| 裝置型別（桌上型電腦、行動裝置、平板電腦） | 裝置最佳化的內容版面配置和CTA | 合格 — 設定檔屬性檢查 |
| 在工作階段中檢視的頁面 | 類別相關性，內容推薦 | 符合條件且具有限制 — 僅進行簡單事件計數檢查 |
| 新訪客與回訪訪客 | 歡迎訊息、漸進式參與 | 合格 — ECID持續性表示回訪訪客 |
| 網站逗留時間/捲動深度 | 退出意圖、參與型優惠方案 | 可能需要自訂實作 — 不符合原生邊緣資格 |

>[!NOTE]
>**決定：對象評估方法** — 此模式的所有對象都必須使用邊緣評估。 定義區段之前，請先確認適用性。

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 邊緣評估 | 此模式的必要專案 | 區段規則運算式必須符合邊緣條件：簡單屬性比較、區段成員資格檢查、無時間序列查詢或彙總函式。 次秒評估延遲。 |
| 串流評估（遞補） | 當區段規則運算式不符合邊緣資格，但近乎即時是可接受的 | 數秒到數分鐘的延遲。 支援更複雜的區段規則運算式。 可能會在個人化傳遞中造成明顯的延遲。 |

**UI導覽：**&#x200B;客戶>對象>建立對象>建置規則

**金鑰組態詳細資料：**

- 使用區段產生器，利用行為屬性來定義對象規則
- 透過確認區段規則運算式僅使用支援的函式（簡單屬性比較、區段成員資格）來驗證邊緣資格
- 將合併原則設定為F4中設定的邊緣作用中合併原則
- 預覽對象母體以驗證區段會傳回預期結果
- 對於以作業階段內頁面檢視為基礎的對象，請使用目前作業階段的事件層級屬性，而非時間序列查詢

**選項差異的位置：**

選項A的&#x200B;**（規則型）：**
為每個內容變體建立不同的受眾區段。 每個區段代表特定的行為條件（例如「Referral = Google和Geo = US」對應至內容變體A）。 對象數等於個人化規則數。

選項B （實驗）的&#x200B;**：**
對象定義為選用。 如果實驗鎖定所有訪客，則不需要對象 — 流量分割處理變體指派。 如果實驗鎖定特定子集（例如，僅限行動訪客），請針對實驗資格定義單一鎖定對象。

選項C （決策）的&#x200B;**：**
定義對象，以用作內容專案的適用性規則。 這些對象會決定哪些訪客符合決定原則中哪些內容專案的資格。 決策引擎會處理合格專案中的內容選擇。

**Experience League檔案：**

- [區段產生器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [邊緣分段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Profile Query Language參考](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)
- [串流區段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)

### 階段3：編寫內容並建立變體

**應用程式功能：** AJO：訊息製作、AJO：內容實驗（選項B）、AJO：決策（選項C）

根據對象成員資格（選項A）、實驗指派（選項B）或決定邏輯（選項C），建立將傳送給訪客的個人化內容變體。 此階段涵蓋使用AJO網頁設計工具或程式碼型體驗編輯器建立內容，以及控制內容選取方式的實驗或決定設定。

此階段中的&#x200B;**決定點：**

>[!NOTE]
>**決定：內容製作方式** — 應如何製作網頁內容變體？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 網頁視覺化編輯器 | 行銷團隊無需程式碼即可以視覺化方式修改頁面元素 | 需要瀏覽器延伸模組。 最適合文字、影像和CTA修改。 僅限於修改現有頁面元素。 |
| 程式碼型體驗編輯器 | 內容需要應用程式程式碼轉譯的結構化資料(JSON) | 最大彈性。 需要開發人員實作才能使用裝載。 最適合動態元件和SPA。 |
| HTML/CSS程式碼編輯器 | 內容修改需要自訂HTML或CSS | 直接程式碼控制。 需要HTML/CSS專業知識。 最適合複雜版面變更。 |

>[!NOTE]
>**決定： Personalization Token** — 內容是否應該包含使用設定檔或內容相關屬性的動態個人化？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 靜態內容變體 | 每個變體都是固定內容片段，沒有動態權杖 | 最簡單的方法。 內容可預測，且易於品質保證。 沒有遺失屬性值的風險。 |
| 使用個人化運算式的動態內容 | 內容包含可解析為個人資料或事件屬性（例如城市名稱、反向連結來源）的Handlebars樣式權杖 | 更相關的內容。 匿名設定檔上可能為Null的屬性需要遞補值。 搭配協助程式使用`{{profile.homeAddress.city}}`語法。 |
| 條件式內容區塊 | 不同的內容區塊會根據單一變體中的屬性條件轉譯 | 減少所需的不同變體數量。 增加內容複雜性。 適合共用版面配置中的細微變化。 |

**使用者介面導覽：** [!DNL Journey Optimizer] >行銷活動>選取行銷活動>編輯內容

**金鑰組態詳細資料：**

- 使用網頁設計工具（視覺化修改）或程式碼型體驗編輯器（JSON裝載）製作內容
- 使用個人化運算式編輯器，從邊緣設定檔屬性插入動態權杖
- 針對匿名設定檔上可能為空白的個人化權杖設定遞補內容
- 使用測試設定檔預覽內容，以驗證跨情境的呈現

**選項差異的位置：**

選項A的&#x200B;**（規則型）：**
為階段2中定義的每個受眾區段製作不同的內容變體。 使用行銷活動設定中的條件式內容規則，將每個變體繫結至其目標對象。 確保不符合任何對象規則的訪客存在預設內容變體。

選項B （實驗）的&#x200B;**：**
作者處理方式的變體（A、B、C等） 用於實驗。 啟用行銷活動上的內容實驗、定義處理變體及其內容、設定流量分配百分比，並設定成功量度。

- 定義具有不同內容的2-10個處理變體
- 設定流量分配（例如，A/B為50/50，或低風險測試的加權分割）
- 可選擇加入保留群組（例如10%接收預設內容）以測量遞增提升度
- 選取成功量度：不重複開啟、不重複點按、轉換，或自訂量度
- 設定信賴臨界值：標準測試95%、重大決策99%、方向學習90%
- **使用者介面導覽：**&#x200B;行銷活動>內容實驗>新增處理>流量分配>成功量度

選項C （決策）的&#x200B;**：**
設定決策元件棧疊，並將其整合至行銷活動。

1. **建立版位** — 定義頁面上內容專案的顯示位置（網頁HTML、網頁JSON、網頁影像）
   - **UI導覽：** [!DNL Journey Optimizer] >元件>決定管理>位置
2. **定義適用性規則** — 根據邊緣設定檔屬性建立規則，以決定哪些訪客符合每個內容專案的資格
   - **UI導覽：** [!DNL Journey Optimizer] >元件>決定管理>規則
3. **建立內容專案（優惠方案）** — 製作個人化內容專案，其中包含每個版位、適用性規則、優先順序和選擇性上限的代表
   - **UI導覽：** [!DNL Journey Optimizer] >元件>決定管理>優惠>建立優惠
4. **建立遞補內容** — 定義當沒有個人化專案符合資格時傳回的遞補專案
   - **UI導覽：** [!DNL Journey Optimizer] >元件>決定管理>優惠>建立遞補優惠
5. **組織成集合** — 使用集合限定詞（標籤）將內容專案群組並建立集合
   - **UI導覽：** [!DNL Journey Optimizer] >元件>決定管理>集合限定詞/集合
6. **建立決定原則** — 將位置連結至集合併選取排名策略（優先順序、公式或AI排名）
   - **UI導覽：** [!DNL Journey Optimizer] >元件>決定管理>決定>建立決定

**Experience League檔案：**

- [建立網站體驗](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [程式碼型體驗管道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/get-started-code-based)
- [新增個人化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [動態內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [建立內容實驗](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [建立個人化優惠方案](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [建立決定](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [排名策略](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### 階段4：設定行銷活動和傳送

**應用程式函式：** AJO：行銷活動執行

建立並啟動AJO網路行銷活動，將網路介面（階段1）、對象目標定位或實驗設定（階段2-3）和內容變體（階段3）繫結到交付專案單位。 行銷活動會控制何時及如何向訪客提供個人化內容。

此階段中的&#x200B;**決定點：**

>[!NOTE]
>**決定：行銷活動型別** — 應如何觸發行銷活動？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 已排程的行銷活動（永遠開啟） | Personalization應持續為所有合格訪客執行 | 設定永恆個人化的開始日期，不含結束日期。 對象評估會在Edge即時進行。 最常用於網頁個人化。 |
| 已排程的行銷活動（時間範圍） | Personalization繫結至特定促銷期間或季節性事件 | 設定明確的開始和結束日期。 行銷活動會在結束日期自動停用。 適合促銷活動。 |
| API觸發的行銷活動 | Personalization傳遞必須由外部系統事件觸發 | 需要API整合。 不常用於匿名網路個人化。 當後端系統必須控制個人化何時生效時使用。 |

**使用者介面導覽：** [!DNL Journey Optimizer] >行銷活動>建立行銷活動

**金鑰組態詳細資料：**

- 選取階段1中設定的網頁管道和網頁表面
- 繫結目標對象（適用於選項A）、設定實驗設定（適用於選項B）或內嵌決定（適用於選項C）
- 設定行銷活動排程（開始日期、結束日期或一律開啟）
- 設定行銷活動層級的頻率限定（如果適用）
- 檢閱所有設定並啟動行銷活動

**選項差異的位置：**

選項A的&#x200B;**（規則型）：**
為每個個人化規則建立一個行銷活動，每個行銷活動都以不同的邊緣對象及其對應的內容變體為目標。 或者，使用具有條件式內容規則的單一行銷活動，將對象成員資格對應至單一行銷活動中的內容變體。

選項B （實驗）的&#x200B;**：**
建立已啟用內容實驗的單一行銷活動。 實驗設定（變體、流量分配、成功量度）已在階段3中定義。 啟動行銷活動以開始實驗。

選項C （決策）的&#x200B;**：**
建立行銷活動，其中嵌入階段3中設定的決定原則。 行銷活動的內容動作會參考決策範圍，在邊緣觸發決策引擎。 啟動行銷活動以開始決策型內容傳遞。

**Experience League檔案：**

- [建立行銷活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [開始使用行銷活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [在訊息中傳遞優惠方案](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

### 階段5：報告與分析效能

**應用程式函式：** AJO：報表與效能分析

使用AJO內建報表來監控個人化效能，並可選擇使用CJA擴充分析，以取得更深入的跨管道深入分析。 此階段包括存取即時和歷史行銷活動報告、檢閱實驗結果，以及建立自訂分析工作區。

此階段中的&#x200B;**決定點：**

>[!NOTE]
>**決定：報告深度** — 效能分析應該深入到何種程度？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 僅限AJO原生報表 | 基本交付和參與量度就足夠了 | 提供立即可用的曝光數、點選次數、CTR和轉換量度。 可立即在campaign UI中使用。 有限的自訂。 |
| AJO報表+ CJA分析 | 深層funnel分析、同類群組比較或跨管道影響測量都是必要作業 | 需要CJA連線和連結至AJO資料集的資料檢視。 啟用自由格式分析、自訂計算量度、歸因模型以及對象發佈。 |

**使用者介面導覽：** [!DNL Journey Optimizer] >行銷活動>選取行銷活動>檢視報告

**金鑰組態詳細資料：**

- 在作用中行銷活動期間存取即時報告，以監控即時傳送（每60秒重新整理一次，顯示過去24小時）
- 行銷活動完成後存取歷史（所有時間）報告，以進行全面分析（最多可能需要2小時才能完全填入）
- 選項B （實驗）：檢閱實驗報告，瞭解治療效能比較、信賴區間和獲勝者宣告
- 對於CJA analysis：確認CJA連線包含AJO體驗事件資料集，且資料檢視已設定網頁個人化量度

**選項差異的位置：**

選項A的&#x200B;**（規則型）：**
檢閱每個對象區段的促銷活動報告，以比較不同個人化內容變體的傳遞和參與量度。 使用CJA建立比較工作區，以測量個人化內容與預設內容的轉換影響。

選項B （實驗）的&#x200B;**：**
檢閱實驗報告，瞭解統計信賴度、處理提升度和成功者識別。 在宣告獲勝者之前，請等待達到信賴臨界值。 將成功內容套用為永久變體（轉換為選項A以進行持續傳遞）。

- **使用者介面導覽：**&#x200B;行銷活動>內容實驗>檢視報告
- **Experience League：** [內容實驗報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)

選項C （決策）的&#x200B;**：**
檢閱決策績效量度，包括優惠曝光率、選擇頻率和每個內容專案的轉換歸因。 分析排名策略的執行方式以及遞補內容的提供是否過於頻繁（表示適用性規則太嚴格）。

**Experience League檔案：**

- [行銷活動即時報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [行銷活動全域報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [使用Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Analysis Workspace概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [內容實驗中的統計計算](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-calculations)

## 實施考量

本節涵蓋此使用案例模式的護欄、常見陷阱、最佳實務和取捨決定。

### 護欄和限制

在實施之前和期間檢閱下列護欄。

- Edge區段僅限於簡單屬性檢查和區段會籍 — 無時間序列查詢或複雜彙總 — [Edge分段資格](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- 每個沙箱的Edge上只能有一個作用中的合併原則 — [設定檔護欄](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- 每個沙箱最多4,000個區段定義 — [分段護欄](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- 每個沙箱最多500個作用中即時行銷活動 — [Journey Optimizer護欄](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- 每個內容實驗最多10個處理變體 — [內容實驗限制](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- 每個沙箱最多10,000個核准的個人化優惠（選項C） — [決定管理護欄](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- 每個決定最多30個位置（選項C） — [Journey Optimizer護欄](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- AI排名模型需要至少1,000個轉換事件才能訓練（選項C）
- [!DNL Edge Network]回應時間SLA：邊緣評估區段小於200毫秒
- 假名設定檔有效期：僅限ECID的設定檔可設定14到365天
- 即時報表每60秒重新整理一次，並顯示過去24小時的資料
- 行銷活動完成後，可能需要最多2小時才能完全填入歷史報表

### 常見陷阱

請避免下列常見的實施錯誤。

- **[!DNL Web SDK]未傳送行為訊號至AEP：**&#x200B;請確認資料流已啟用[!DNL Adobe Experience Platform]服務，且事件資料集已正確對應。 若沒有此屬性，邊緣設定檔就不會填入，對象評估則會以無訊息方式失敗 — 訪客會收到預設內容而不會出現錯誤指示。
- **傳回零資格的Edge對象：** Edge細分具有嚴格的資格要求。 時間序列查詢、彙總函式和多實體查詢不符合邊緣資格。 使用簡單屬性比較或區段成員資格檢查來重寫區段規則運算式。
- **邊緣上沒有作用中的合併原則：**&#x200B;如果對象區段使用的合併原則沒有`isActiveOnEdge: true`，邊緣設定檔查詢將會失敗，且不會傳遞個人化。 每個沙箱在Edge上只能有一個作用中的合併原則 — 請確認衝突不存在。
- **頁面載入時Personalization忽隱忽現：**&#x200B;擷取個人化主張的[!DNL Web SDK] `sendEvent`呼叫必須在頁面轉譯目標內容區域之前執行。 實作預先隱藏程式碼片段或非同步轉譯，以防止預設內容在個人化內容載入之前閃爍。
- **未在SPA路由變更上呈現內容：**&#x200B;單頁應用程式在路由變更時，需要具有更新檢視資訊的明確`sendEvent`呼叫。 若沒有此專案，[!DNL Edge Network]就不會重新評估新檢視的個人化。
- **實驗未達到統計顯著性：**&#x200B;流量不足或處理變體太多，會稀釋每個變體的樣本大小。 減少變數的數量，或增加實驗持續時間。 不要過早停止實驗 — 結果可能會產生誤導。
- **僅傳回遞補內容的決策：**&#x200B;請檢查個人化內容專案是否在其有效日期範圍內獲得核准，以及資格規則是否與匿名訪客的邊緣設定檔屬性相符。 同時確認未達到上限限制。

### 最佳實務

請遵循下列建議以成功實作。

- **開始簡單，然後反複運算：**&#x200B;從選項A （規則型）開始進行初始個人化，然後使用選項B （實驗）來驗證假設，並將選項C （決策）用於進階使用案例。 每個選項都建立在基礎的基礎架構上。
- **使用預先隱藏來防止忽隱忽現情形：**&#x200B;在即將提供個人化的頁面上實作AEP預先隱藏程式碼片段。 這會隱藏目標內容區域，直到個人化內容準備好呈現為止，以防止視覺閃爍。
- **有意設計遞補內容：**&#x200B;預設（非個人化）內容本身應是高品質的體驗。 不符合個人化資格的訪客 — 或當[!DNL Edge Network]回應延遲時 — 不應接收降級體驗。
- **在建立對象之前驗證邊緣資格：**&#x200B;在投資對象規則開發之前，請檢閱Experience League中的資格條件，以確認區段規則運算式符合邊緣資格。 不符合資格的運算式將會無訊息地退回到批次或串流評估，且此模式會有無法接受的延遲。
- **監視邊緣傳遞效能：**&#x200B;設定[!DNL Edge Network]回應時間和個人化傳遞失敗的監視警示。 訪客看不到Edge傳送問題（他們會看到預設內容），且可能在沒有主動監視的情況下無法偵測到。
- **設定假名設定檔有效期：**&#x200B;設定匿名Edge設定檔的適當有效期，以平衡跨工作階段個人化（識別再度訪問的訪客）與隱私權法規遵循與儲存管理。
- **使用代表性設定檔進行測試：**&#x200B;預覽個人化內容時，請使用代表實際匿名訪客情況的測試設定檔（無CRM資料、有限的行為歷史記錄、各種地理位置和裝置）。

### 權衡決定

規劃實施時，請考慮下列取捨。

>[!NOTE]
>**取捨： Personalization廣度與實作複雜性**
>
>更細微的個人化（許多對象、許多內容變體）會產生更相關的體驗，但會增加設定複雜度和內容製作額外負荷。
>
>- **廣泛的個人化優點：**&#x200B;簡單、上市時間更短、內容生產成本更低。 一小部分的受眾和變體會涵蓋具有有意義的個人化的大部分訪客。
>- **細微的個人化優點：**&#x200B;最大關聯性、較高的參與提升度、較好的轉換率。 許多受眾和變體都會透過量身打造的內容來處理特定的行為訊號。
>- **建議：**&#x200B;從3到5個高影響力的個人化規則開始，目標是最常見的訪客區段（例如，轉介來源、裝置型別、地理區域）。 衡量影響，然後根據觀察到的效能和業務價值展開至更精細的規則。

>[!NOTE]
>**取捨：規則型決定式與AI驅動的最佳化**
>
>規則型方法（選項A）可讓企業完全控制每位訪客看到的內容。 AI排名方法（選項C）會隨著時間最佳化內容選擇，但減少特定內容被選擇的原因。
>
>- **規則型偏好：**&#x200B;可預測性、可稽核性、業務控制。 行銷團隊確切瞭解每個區段會收到哪些內容，並可向利害關係人說明邏輯。
>- **AI驅動的優點：**&#x200B;效能最佳化、擴充性、持續改善。 AI模型會探索人類規則撰寫可能遺漏的內容 — 訪客相關性。
>- **建議：**&#x200B;針對品牌一致性和利害關係人透明度至為重要的高風險內容決策，請使用規則型。 針對手動規則管理變得笨拙且持續最佳化帶來可衡量的提升度的大型內容目錄，使用AI排名。

>[!NOTE]
>**取捨：匿名設定檔持續性與隱私權法規遵循**
>
>較長的假名設定檔到期時間，可讓跨工作階段個人化效果更佳（辨識再度訪問的訪客、隨著時間建立行為內容）。 更短的到期時間可改善隱私權法規遵循，並降低儲存成本。
>
>- **更長的到期偏好：**&#x200B;更豐富的匿名設定檔、更佳的回訪訪客認知度、更多用於個人化決策的資料。 將到期日設為90-365天。
>- **較短的到期時間：**&#x200B;隱私權法規遵循(GDPR、CCPA)、降低儲存成本、將過時設定檔資料的風險降至最低。 將到期日設為14至30天。
>- **建議：**&#x200B;將到期日與貴組織的Cookie同意原則及隱私權要求保持一致。 對於大多數實作，30至90天可在個人化值與隱私權合規性之間取得合理平衡。

## 相關文件

以下Experience League資源提供此使用案例模式中所使用功能的其他詳細資料。

**網路通道和程式碼型體驗**

- [開始使用網路頻道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [建立網站體驗](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [程式碼型體驗管道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/get-started-code-based)
- [程式碼型體驗設定](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/code-based-configuration)

**對象和細分**

- [Segmentation Service概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [區段產生器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [邊緣分段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [串流區段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Profile Query Language參考](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

**Personalization與內容**

- [新增個人化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization語法](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [動態內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [使用內容範本](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [使用內容片段](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)

**內容實驗**

- [開始使用內容實驗](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [建立內容實驗](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [內容實驗報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [統計計算](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-calculations)

**決定管理**

- [決策管理概觀](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [建立產品建議放置環境](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [建立決定規則](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [建立個人化優惠方案](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [建立後備產品建議](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [建立集合](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [建立決定](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [排名策略](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)
- [在訊息中傳遞優惠方案](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

**行銷活動**

- [開始使用行銷活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [建立行銷活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)

**[!DNL Web SDK]和資料彙集**

- [網頁SDK概觀](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [安裝Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/install/overview)
- [設定資料串流](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [標籤總覽](https://experienceleague.adobe.com/en/docs/experience-platform/tags/home)

**身分和設定檔**

- [Identity Service總覽](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [身分名稱空間概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/identity/features/namespaces)
- [合併原則概觀](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [即時客戶個人檔案總覽](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)

**資料模式**

- [XDM系統概覽](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [結構描述組合基本面](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)

**報告和分析**

- [行銷活動即時報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [行銷活動全域報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [使用Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Analysis Workspace概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [CJA概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)

**資料控管和隱私權**

- [資料控管概覽](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [進階資料生命週期管理概觀](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)
- [同意和偏好設定欄位群組](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)

**護欄**

- [Journey Optimizer護欄](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [即時客戶個人檔案護欄](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Identity Service護欄](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)
