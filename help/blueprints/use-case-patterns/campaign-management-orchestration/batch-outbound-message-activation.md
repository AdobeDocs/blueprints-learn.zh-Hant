---
title: 批次傳出訊息啟用
description: 瞭解如何在單一批次執行中評估對象及傳遞已排程的傳出訊息。
solution: Journey Optimizer, Real-Time Customer Data Platform
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '8246'
ht-degree: 1%

---


# 批次傳出訊息啟用

本指南提供完整的實作參考，說明如何使用[!DNL Adobe Journey Optimizer] (AJO)和[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)，將排程的傳出訊息傳遞至已定義的對象區段。 它是為需要瞭解所有可行的實作方法、推動每個選擇的決定考量以及何處尋找[!DNL Adobe Experience League]的詳細檔案的解決方案架構師、行銷技術人員和實作工程師所設計。

批次傳出訊息啟用是一對多傳出訊息的基本行銷活動模式。 它涵蓋從受眾定義到訊息傳遞和效能分析的完整生命週期。 本指南提供三種實施選項 — 排程行銷活動、受眾觸發的歷程和API觸發的行銷活動 — 並為選擇每個使用案例的正確方法提供結構化決策指引。

它提供實作選項、權衡分析、UI導覽路徑和[!DNL Experience League]檔案參考。

## 使用案例概述

組織經常需要在特定時間或回應系統事件，將單一訊息傳送給已知受眾區段。 此模式解決該需求，方法是將[!DNL RT-CDP]中的對象評估與[!DNL Journey Optimizer]中的訊息編寫和行銷活動執行結合。

業務案例簡單明瞭：定義應該接收訊息的人員、使用個人化建立訊息內容、將對象和訊息繫結至行銷活動或歷程，並透過對象資格或系統觸發器，依排程執行傳送。 結果會傳送訊息，並包含傳送、參與和轉換量度的完整報表。

每當可透過一次執行將單一訊息傳遞給已知對象來推進業務目標時，此模式即適用。 它與回應即時行為事件的事件觸發訊息不同，也不同於隨著時間透過多個接觸點引導設定檔的多步驟協調歷程。 批次啟動是最簡單的行銷活動模式，也是傳出訊息使用案例最常見的起點。

## 主要業務目標

本節說明批次傳出訊息啟用支援的主要業務目標。

### 增加電子郵件和行銷活動參與度

**說明：**&#x200B;透過最佳化的內容和目標定位，改善開啟率、點進率及整體行銷活動回應。

**KPI：**&#x200B;開放率、參與度、轉換率

### 增加收入與銷售

**說明：**&#x200B;透過最佳化的數位頻道、行銷活動和客戶歷程，推動營收增長。

**KPI：**&#x200B;轉換率、遞增收入、平均訂單值

**相關業務目標：** [增加收入與銷售](/help/blueprints/business-objectives/revenue-monetization/increase-revenue-sales.md)

### 簡化行銷活動的執行

**說明：**&#x200B;透過範本、自動化和標準化程式，縮短行銷活動建置時間，並簡化多管道行銷活動傳遞。

**KPI：**&#x200B;上市速度、效率、準時完成%

## 戰術使用案例範例

下列案例說明批次傳出訊息啟用的常見應用程式。

- **銷售公告或促銷電子郵件爆增** — 在排程日期向符合資格的客戶區段廣播促銷優惠
- **產品上市推播通知** — 透過推播通知感興趣的客戶有新的產品可供使用
- **電子報或摘要電子郵件** — 定期傳送內容四捨五入給訂閱者對象
- **活動註冊邀請** — 邀請合格的潛在客戶參加網路研討會、會議或面對面活動
- **訂閱續約提醒電子郵件** — 提醒即將續約日期的客戶採取行動
- **熟客方案里程碑通知** — 恭喜達到熟客層級或點臨界值的會員
- **特定call-to-action電子郵件** — 推動目標動作，例如完成購買、更新偏好設定或註冊程式
- **快閃銷售或限時優惠方案的SMS行銷活動** — 透過簡訊傳送緊急且限時的促銷活動給選擇加入的對象

## 關鍵績效指標

下表定義用來測量促銷活動效益的KPI。

| KPI | 說明 | 測量方法 |
| --- | --- | --- |
| 傳遞率 | 成功傳遞給收件者的郵件百分比 | 已傳遞/已傳送x 100 |
| 開啟率 | 收件者開啟的傳遞訊息百分比 | 不重複開啟/傳送x 100 |
| 點進率(CTR) | 已點按連結的傳遞訊息百分比 | 不重複點按/傳送x 100 |
| 點按開啟率(CTOR) | 已點按連結的已開啟訊息百分比 | 不重複點按/不重複開啟x 100 |
| 轉換率 | 完成所需動作的收件者百分比 | 轉換/傳遞x 100 |
| 取消訂閱率 | 接收訊息後取消訂閱的收件者百分比 | 取消訂閱/送達x 100 |
| 跳出率 | 無法傳遞的訊息百分比 | 退回/傳送x 100 |
| 每封傳送電子郵件的收入 | 行銷活動的收入除以傳送的訊息 | 總收入/已傳送 |

## 使用案例模式

**批次傳出訊息啟用**

評估對象，然後在單一批次執行中將排程的傳出訊息（電子郵件、簡訊、推播）傳送給所有符合資格的設定檔。

**功能鏈：**&#x200B;對象評估>訊息製作>行銷活動執行>報告

## 應用程式

下列應用程式可用來實作此模式。

- **[!DNL Adobe Journey Optimizer] (AJO)** — 訊息製作、頻道設定、行銷活動執行、歷程協調、內容實驗、頻率規則和報告
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** — 對象評估、同意和治理實施
- **[!DNL Adobe Experience Platform] (AEP)** — 設定檔存放區、身分服務、結構描述、資料集、資料集合

## 基礎函式

下列基本功能必須為此使用案例模式準備就緒。 對於每個函式，狀態會指出它通常是必要的、假設為預先設定或不適用。

| 基礎函式 | 狀態 | 必須準備就緒的專案 | Experience League參考 |
| --- | --- | --- | --- |
| 管理與治理 | 已假設就位 | 布建使用中管道設定的AJO沙箱。 傳送委派的子網域、指派的IP集區及IP熱身完成。 已指派具有行銷活動/歷程建立許可權的使用者角色。 | [沙箱總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sandbox/home)，[存取控制總覽](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| 資料模型與準備 | 必填 | XDM個人設定檔結構描述具有用於細分和個人化的屬性（例如名稱、電子郵件、偏好設定、層級）。 擷取促銷活動後轉換追蹤之目標轉換動作（例如`commerce.purchases`、`web.webInteraction`）的XDM ExperienceEvent結構描述。 兩個結構描述已啟用設定檔的資料集。 | [XDM系統總覽](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)，[結構描述組合基本概念](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| 資料來源與收集 | 已假設就位 | CTA目的地上的Web SDK或Analytics標籤必須作用中才能擷取轉換事件。 設定檔屬性的串流或批次擷取管道必須可運作。 | [網頁SDK概觀](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)，[來源概觀](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home) |
| 身分和設定檔設定 | 已假設就位 | 已設定的電子郵件（以及任何跨裝置識別碼）身分名稱空間。 個人化所需的設定檔屬性，在傳送時會對應、擷取且可解析。 已設定合併原則。 | [身分識別服務總覽](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)，[合併原則總覽](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview) |
| 對象定義與細分 | 必填 | 使用區段產生器或受眾構成來鎖定在RT-CDP中定義的受眾。 對象已發佈，並使用非零母體進行評估。 透過RT-CDP對象評估在實施階段1中涵蓋。 | [區段服務總覽](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)，[區段產生器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder) |

## 支援功能

以下功能可擴大此使用案例模式，但不是核心執行的必要功能。

| 支援功能 | 狀態 | 為什麼重要 | Experience League參考 |
| --- | --- | --- | --- |
| 計算/衍生屬性建立 | 推薦 | 計算屬性（例如上次購買間隔天數、期限訂單計數或參與分數）可改善對象精確度並啟用更豐富的訊息個人化。 | [計算屬性總覽](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| 資料生命週期管理 | 推薦 | 應針對推動轉換追蹤的事件資料集制定資料保留原則（有效期）。 必須為頻道層級的選擇加入/選擇退出強制執行設定同意結構描述欄位。 | [進階資料生命週期管理概觀](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)，[同意和偏好設定欄位群組](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents) |
| 資料使用標籤和實作 | 推薦 | 用於個人化的PII欄位上的治理標籤可確保啟用期間的合規性。 防止在訊息內容或受眾匯出未經授權即使用敏感設定檔資料。 | [資料控管概觀](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)，[資料使用標籤概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/labels/overview) |
| 監控與可觀察性 | 已包含 | 即時傳送監視屬於報告階段的一部分。 平台層級的擷取失敗警示或授權使用狀況，可提供行銷活動層級量度以外的運作可見度。 | [可觀察性深入分析概觀](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)，[警示概觀](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview) |
| 報告與分析 | 已包含 | 行銷活動和歷程報告包含在報告階段。 為了進行更深入的跨管道分析，CJA整合提供了funnel分析、歸因模型和同類群組分析，超出AJO內建的報表。 | [CJA概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)，[AJO + CJA整合指南](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo) |

## 應用程式函式

此計畫會從應用程式功能目錄中執行下列功能。 函式會對應至實作階段，而非編號步驟。

### [!DNL Journey Optimizer] (AJO)

| 函式 | 實作階段 | 說明 |
| --- | --- | --- |
| 通道設定 | 階段2：通道設定 | 設定或驗證管道表面（電子郵件、簡訊或推播），包括子網域、IP集區、寄件者設定和隱藏清單 |
| 訊息製作 | 階段3：訊息製作 | 使用範本、電子郵件Designer、個人化運算式、條件內容區塊和內容片段建立訊息內容 |
| 行銷活動執行 | 階段4：行銷活動或歷程建立 | 建立、設定和啟用排程或API觸發的行銷活動，此行銷活動會繫結對象、訊息和執行排程 |
| 內容實驗 | 階段4：行銷活動或歷程建立 | 可選擇設定A/B或多變數內容實驗，以最佳化訊息效能 |
| 頻率與業務規則 | 階段4：行銷活動或歷程建立 | 可選擇套用頻率限定規則，以防止在並行行銷活動間傳送過度訊息 |
| 衝突與優先順序管理 | 階段4：行銷活動或歷程建立 | 當多個行銷活動鎖定重疊的對象時，指派優先順序分數並設定衝突解決方案 |
| 報告與效能分析 | 第5階段：報告與效能分析 | 在執行期間透過即時報告監視傳遞指標，並在完成後透過歷史報告分析行銷活動績效 |

### [!DNL Real-Time CDP] (RT-CDP)

| 函式 | 實作階段 | 說明 |
| --- | --- | --- |
| 對象評估 | 階段1：對象評估 | 使用區段產生器或對象構成定義對象規則，選取評估方法（批次、串流或邊緣），並驗證對象母體 |
| 同意與治理實施 | 階段1：對象評估 | 強制執行同意偏好設定和資料使用原則，以確保僅同意的設定檔會收到行銷活動訊息 |

## 先決條件

開始實作前請先完成下列作業。

- AJO沙箱已布建並啟用
- 傳送子網域已委派和驗證（已設定SPF、DKIM、DMARC）
- IP集區已針對生產傳送磁碟區進行指派和預熱
- 至少存在一個使用中的頻道介面（電子郵件、簡訊或推播）
- 使用者帳戶具有行銷活動/歷程建立和內容製作許可權
- XDM設定檔結構描述包含對象細分和訊息個人化所需的屬性
- XDM事件結構描述會擷取促銷活動後追蹤的轉換事件
- 透過Identity Service擷取及整合設定檔資料
- CTA目的地頁面上已啟用網頁SDK或Analytics標籤，以擷取轉換事件
- 同意欄位會填入目標訊息頻道的設定檔中
- 訊息設計可使用內容資產（影像、標誌、品牌指引）

## 實作選項

本節說明批次傳出訊息啟用的三個實作選項，以及比較和決定指引。

### 選項A：排程的行銷活動（一次性批次傳送）

**最適合：**&#x200B;以日期為準的傳送 — 銷售公告、產品推出、活動註冊截止日期、續約提醒、電子報爆炸，以及任何預先知道執行日期的傳送。

**運作方式：**

已排程的行銷活動是批次傳出訊息最簡單的變體。 行銷人員定義目標對象、編寫訊息內容、設定傳送日期和時間，以及啟用行銷活動。 在排程的執行時間，AJO會評估對象以判斷目前的合格母體，然後將訊息傳遞至單一批次中的所有合格設定檔。

整個設定會在AJO Campaigns介面中進行 — 沒有歷程畫布、沒有分支邏輯，也沒有等待步驟。 這可讓排程行銷活動最快速地進行設定，也最容易管理。 您可以將行銷活動設為立即執行、特定的未來日期/時間或循環排程（每日、每週、每月）。

**主要考量事項：**

- 會在執行時評估對象，因此會納入在排程和執行之間符合資格的設定檔
- 無分支、等待或條件邏輯可用 — 訊息會傳遞至所有符合資格的設定檔
- 直接在行銷活動設定中支援內容實驗（A/B測試）
- 行銷活動屬性包含與其他行銷活動解決衝突的優先順序分數

**優點：**

- 最簡易的設定和最少的額外負荷
- 直接批次傳送的上市時間最短
- 對週期性排程的內建支援
- 原生支援的內容實驗
- 對象在執行時重新評估新鮮度

**限制：**

- 傳遞前沒有等待步驟、條件或分支
- 無法對排程和執行之間的設定檔行為做出反應
- 僅限單一訊息動作 — 無多重觸控順序
- 啟動後即無法編輯（必須複製並修改）

**Experience League：**

- [開始使用行銷活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [建立行銷活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)

### 選項B：受眾觸發的歷程

**最適合：**&#x200B;行為導向傳送 — 捨棄的購物車通知、試用到期提醒、里程碑慶祝活動、資格型外展活動，以及觸發器為對象資格或業務事件（而非日曆日期）的任何傳送。

**運作方式：**

對象觸發的歷程使用歷程畫布，在設定檔符合定義的對象資格或引發合格事件時傳遞訊息。 歷程專案是由受眾成員資格變更（設定檔進入受眾）觸發，而不是固定排程。 歷程畫布可在訊息動作前允許選用的等待步驟、條件分支和隱藏邏輯，提供比排程行銷活動更大的彈性。

歷程是在AJO Journeys介面中使用「讀取對象」專案事件設定的。 當設定檔符合對象資格時，他們會進入歷程並透過畫布節點進行。 簡單實施可能僅包含單一電子郵件動作節點，因此其功能類似於已排程的行銷活動，但具有以對象資格為基礎的登入時間。 更複雜的實施可新增等待節點（例如，在資格後等待24小時）、條件節點（例如，檢查設定檔是否開啟了先前的電子郵件），或訊息傳送前的隱藏邏輯。

**主要考量事項：**

- 歷程專案是由對象資格觸發，而非行事曆日期
- 歷程畫布支援預先傳送邏輯的等待、條件和分割節點
- 歷程重新進入規則控制設定檔是否可以多次進入歷程
- 歷程仲裁設定決定設定檔已在競爭歷程中的行為

**優點：**

- 根據對象資格而不是固定排程的靈活進入時間
- 等待和條件節點允許預先傳遞邏輯（例如，延遲、檢查、抑制）
- 重新進入控制項可防止將重複傳送至相同的設定檔
- 如果使用案例發展，可延伸至多步驟歷程
- 透過登入、退出和節點層級量度支援歷程層級報告

**限制：**

- 比排程行銷活動更多的設定額外負荷
- 歷程畫布即使對於單一訊息使用案例，也增加了複雜性
- 歷程必須發佈，且上線時無法編輯（必須建立新版本）
- 進入上限可能會限制在時間範圍內輸入的設定檔數

**Experience League：**

- [開始使用歷程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [讀取對象歷程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)

### 選項C：API觸發的行銷活動

**最佳用途：**&#x200B;系統啟動的傳送 — 含追加銷售內容的訂單確認、支援票證解析後續追蹤、含行銷內容的交易式通知，以及在特定時刻觸發事件源自外部系統的任何傳送。

**運作方式：**

API觸發的行銷活動會在觸發系統事件發生時透過REST API呼叫來啟動。 此行銷活動已在AJO中預先設定訊息內容和頻道設定，但API呼叫不會繫結預先定義的對象，而是會指定收件者設定檔，且可傳遞填入動態訊息引數的內容資料。

此變體最適合在傳送時間是由外部系統（例如訂單管理系統、CRM工作流程或支援平台）而非對象評估或行事曆排程所決定的情況。 在API觸發裝載中傳遞的內容相關資料（例如訂單詳細資料、票證編號或產品名稱）可以使用未儲存在設定檔上的內容相關屬性來個人化訊息內容。

**主要考量事項：**

- 不需要預先繫結對象 — 收件者是在API觸發要求中指定
- 觸發裝載中的內容資料可啟用設定檔屬性以外的動態個人化
- 行銷活動必須屬於「API觸發」型別，且必須先啟用，才能接收觸發要求
- 每個API觸發程式要求最多可支援20個設定檔收件者
- 由於收件者來自API呼叫，因此可能會略過對象評估（階段1）

**優點：**

- 事件當下從外部系統即時觸發
- 未在設定檔中儲存資料的情境式個人化（訂單詳細資料、票證資訊）
- 無對象評估額外負荷 — 直接指定收件者
- 支援異動+行銷混合式傳訊

**限制：**

- 需要外部系統整合才能傳送API觸發程式
- 每個API觸發程式請求最多20個收件者
- 無內建對象評估 — 呼叫系統必須決定收件者
- 由於API整合需求，技術複雜性更高
- API觸發的行銷活動不支援內容實驗

**Experience League：**

- [API觸發的行銷活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/api-triggered-campaigns/api-triggered-campaigns)
- [使用API觸發行銷活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/api-triggered-campaigns/api-triggered-campaigns)

### 選項比較

下表比較各個關鍵條件的三個實作選項。

| 條件 | 選項A：排程的行銷活動 | 選項B：受眾觸發的歷程 | 選項C：API觸發的行銷活動 |
| --- | --- | --- | --- |
| 最適合 | 錨定日期的傳送（促銷活動、啟動、電子報） | 行為導向傳送（資格事件、里程碑） | 系統啟動的傳送（訂單確認、異動） |
| 複雜性 | 低 | 中 | Medium — 高 |
| 觸發器型別 | 行事曆日期/時間或週期性排程 | 對象資格或業務事件 | 外部系統API呼叫 |
| 預先傳遞邏輯 | 無 | 等待，條件，分割節點可用 | 無（呼叫系統中的邏輯） |
| 對象繫結 | 預先定義的RT-CDP對象 | 預先定義的RT-CDP對象 | API裝載中指定的收件者 |
| 內容資料 | 僅限設定檔屬性 | 僅限設定檔屬性 | 設定檔屬性+ API裝載資料 |
| 內容實驗 | 支援 | 支援（訊息動作時） | 不支援 |
| 頻率上限 | 支援 | 支援 | 支援 |
| 重新進入控制項 | 不適用（單次執行） | 可設定的重新進入規則 | 不適用（依請求） |
| 設定介面 | AJO行銷活動 | AJO歷程 | AJO Campaigns +外部系統 |
| 需要 | 對象、頻道介面、訊息 | 對象、頻道介面、訊息、歷程畫布 | 頻道介面、訊息、API整合 |

### 選擇正確的選項

使用以下決定流程來選取適當的實施選項：

1. **外部系統事件是否觸發傳送（例如，已下訂單，票證已解決）？** 如果是，請選擇&#x200B;**選項C： API觸發的行銷活動**。 這是唯一支援系統起始的觸發程式搭配內容裝載資料的選項。

2. **傳送是否已錨定至特定行事曆日期或週期性排程？** 如果是，請選擇&#x200B;**選項A：排程的行銷活動**。 這是設定日期驅動傳送的最簡單也最快。

3. **傳送是否需要回應對象資格，或需要傳遞前邏輯（等待、條件、隱藏）？** 如果是，請選擇&#x200B;**選項B：對象觸發的歷程**。 歷程畫布提供行為導向進入和傳遞前決定邏輯的彈性。

4. **傳送簡單廣播給已知對象是否沒有特殊的時間或邏輯需求？** 選擇&#x200B;**選項A：排程的行銷活動**&#x200B;以獲得最低的組態額外負荷。

## 實作階段

本節將詳細介紹實作的每個階段，包括決策點和選項特定指引。

### 階段1：評估對象

**應用程式函式：** RT-CDP：對象評估

此階段會定義並評估將接收行銷活動訊息的目標對象區段。 它會根據設定檔屬性、行為訊號和隱藏規則，判斷哪些設定檔符合傳送的資格。

>[!NOTE]
>對於選項C （API觸發的行銷活動），如果收件者完全在API觸發程式裝載中指定，則可以略過此階段。 不過，即使是API觸發的行銷活動也能透過隱藏受眾受益，以篩選掉不應接收訊息的設定檔。

#### 決定：對象條件

哪些條件可定義目標對象？ 哪些隱藏規則應排除設定檔？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 以設定檔屬性為基礎的對象 | 目標對象是由人口統計、偏好設定或狀態屬性所定義 | 最容易建置；支援所有評估方法 |
| 行為事件型對象 | 目標對象是由一段時間內已採取（或未採取）的動作所定義 | 需要事件資料擷取；時間範圍規則可能會限制串流適用性 |
| 對象構成（衍生對象） | 目標對象需要跨多個來源對象排名、分割、排除或擴充作業 | 更強大但僅限批次的評估；每個沙箱僅限10個組合 |

#### 決定：評估方法

對象必須多久更新一次，才能反映新的符合資格或取消資格設定檔？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 批次評估 | 排程的行銷活動，接受一天內的對象新鮮度；大型複雜對象 | 大部分節段型態的預設值；每日排程或隨選處理；支援所有節段規則功能 |
| 串流評估 | 受眾觸發的歷程，其中設定檔在符合資格時必須近乎即時輸入 | 適用於合格區段規則運算式的自動；並非所有區段型別都適用於串流；幾近即時的延遲（秒到分鐘） |
| 邊緣評估 | 此模式不典型（用於相同頁面個人化） | 有限的區段規則支援；毫秒延遲；僅在結合網頁個人化模式時相關 |

#### 決定：合併原則

對象應使用哪個合併原則來解析設定檔片段？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 預設合併原則（已排序時間戳記） | 批次促銷活動最常見的使用案例 | 最近的屬性值wins；傳出訊息的標準方式 |
| 自訂合併原則（資料集優先順序） | 特定資料來源何時應該取得關鍵屬性的優先權 | 當CRM資料應該覆寫特定欄位的Web收集資料時非常有用 |

#### UI導覽

客戶>受眾>建立受眾>建立規則

#### 關鍵設定詳細資料

- 使用區段產生器，搭配設定檔屬性、行為事件和區段會籍的區段規則來定義對象
- 套用隱藏規則以排除已轉換、最近收到類似訊息或選擇退出的設定檔
- 繼續之前，請驗證對象是否具有非零母體
- 對於批次行銷活動，請確保區段評估排程作用中或觸發隨選評估
- 確認同意欄位（`consents.marketing.email.val`、`consents.marketing.sms.val`等） 填入並強制執行

#### 選項差異之處

選項A （排程的行銷活動）的&#x200B;**：**

批次評估為典型。 促銷活動執行時會重新評估對象，因此會鎖定最新符合資格的母體。 定義對象並驗證其母體，然後繼續建立行銷活動。

選項B的&#x200B;**（對象觸發的歷程）：**

偏好使用串流評估，因此設定檔在符合資格時即會進入歷程。 確保區段規則運算式符合串流條件（簡單事件觸發器、屬性比較、有限時間視窗）。 設定對象並確認串流資格為作用中。

選項C （API觸發的行銷活動）的&#x200B;**：**

可完全略過對象評估。 如果已使用，請建立隱藏受眾，以篩選不應收到訊息的設定檔（例如，最近取消訂閱、已轉換）。 撥號系統決定主要收件者。

#### Experience League檔案

- [Segmentation Service概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [區段產生器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [串流區段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [對象構成](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Profile Query Language參考](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### 階段2：設定通道

**應用程式函式：** AJO：頻道設定

此階段會驗證或建立定義訊息傳送基礎結構的管道表面（預設集） — 子網域、IP集區、寄件者身分、回覆位址和取消訂閱設定。 在可以編寫訊息內容或啟動行銷活動之前，必須存在有效的管道表面。

#### 決定： Target頻道

哪個傳訊通道會傳遞行銷活動訊息？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 電子郵件 | 大部分的行銷活動型別 — 電子報、促銷活動、通知、續約 | 需要委派的子網域、暖化的IP集區、傳送者身分和取消訂閱設定 |
| 簡訊 | 時間敏感型或簡短的訊息 — 快閃銷售、約會提醒、OTP代碼 | 需要SMS提供者憑證（Sinch、Twilio或Infobip）；更高的每訊息成本；更嚴格的同意要求 |
| 推播通知 | 行動參與對象 — 應用程式更新、位置型優惠、應用程式內功能公告 | 需要APN (iOS)和/或FCM (Android)認證；使用者已安裝已授予推送許可權的應用程式 |

#### 決定：選取管道表面

沙箱中是否已存在適當的管道表面，或必須建立新的管道表面？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 重複使用現有表面 | 經過驗證的活動表面符合所需的子網域、傳送者身分和管道型別 | 最快路徑；不需要DNS或熱身設定 |
| 建立新表面 | 沒有符合需求的現有表面，或需要新的子網域/傳送者身分 | 需要子網域委派、DNS驗證、IP集區指派，以及可能的IP熱身（新IP需要2-4週） |

#### 決定：取消訂閱處理

如何在頻道介面上管理選擇退出？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 一鍵式list-unsubscribe標頭 | 所有行銷電子郵件的標準；主要ISP (Gmail、Yahoo)傳遞能力所需 | 新增mailto：或URL型取消訂閱標題，ISP會將其顯示為「取消訂閱」按鈕 |
| 電子郵件內文中的取消訂閱連結 | 對於不支援list-unsubscribe標題的電子郵件使用者端，此為遞補專案時的必要專案 | 在電子郵件頁尾中加入取消訂閱連結與list-unsubscribe標頭 |
| 兩者（建議） | 所有行銷電子郵件的最佳實務 | 最大合規涵蓋範圍和最佳傳遞能力設定檔 |

#### UI導覽

「管理」(Administration) >「色版」(Channels) >「色版曲面」(Channel surfaces) >「建立曲面」(Create surfaces) （或選取現有）

#### 關鍵設定詳細資料

- 電子郵件：繫結傳送子網域、IP集區、寄件者名稱、寄件者電子郵件、回覆地址及密件副本地址（如果需要稽核副本）
- SMS：設定SMS提供者憑證和短程式碼或長程式碼設定
- 對於推播：使用應用程式的憑證或伺服器金鑰設定APN和/或FCM憑證
- 繼續之前，請先驗證管道表面是否顯示「作用中」狀態
- 確認傳送子網域的DNS記錄(SPF、DKIM、DMARC)已正確設定
- 檢閱過時專案的隱藏清單；啟動前先清除

#### Experience League檔案

- [開始使用電子郵件設定](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [委派子網域](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [建立 IP 池](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [IP熱身計畫](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [電子郵件表面設定](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [設定簡訊頻道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [設定推播通知頻道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [管理隱藏清單](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### 階段3：編寫訊息

**應用程式函式：** AJO：訊息製作

此階段會建立將傳送給對象的訊息內容。 這包括選取或建立內容範本、設計訊息版面、使用設定檔屬性新增個人化、針對對象特定變數設定條件式內容區塊、建立可重複使用的內容片段，以及使用範例設定檔預覽/測試訊息。

#### 決定：內容方法

應如何建立訊息內容？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 從現有範本開始 | 存在品牌核准的範本，且符合訊息型別（促銷、異動、電子報） | 最快的製作路徑；確保品牌一致性；範本是沙箱專屬的 |
| 從頭開始設計 | 沒有合適的範本存在，或訊息需要唯一的配置 | 更具彈性但需付出更多心力；請考慮儲存為範本以供重複使用 |
| 匯入HTML | 訊息設計已在外部建立（例如，在設計工具中），且HTML已準備好匯入 | 保留外部設計；可能需要調整AJO相容性和個人化權杖 |

#### 決定： Personalization深度

哪些設定檔屬性應該個人化訊息，以及是否需要條件式內容區塊？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 基本個人化（姓名、問候語） | 簡單的行銷活動，具有個人化稱呼的一般內容已足夠 | 工作量低；轉譯問題風險極低；使用標準設定檔屬性 |
| 屬性型個人化 | 訊息內容會因設定檔屬性（階層、偏好設定、位置）而異 | 需要已驗證的XDM路徑；使用多個設定檔進行測試，以確保所有變數都正確呈現 |
| 條件式內容區塊 | 不同的內容區段必須顯示給相同訊息中的不同受眾區段 | 製作過程更複雜；每個條件都需要預裝置援；測試所有排列 |
| 內容個人化（僅限選項C） | API觸發的行銷活動需要呈現傳入觸發裝載（訂單詳細資料、票證資訊）的資料 | 內容屬性不會儲存在設定檔上；在訊息中定義預留位置，並對應至裝載欄位 |

#### 決定：片段策略

共用內容區塊是否應建立為可重複使用的片段？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 可重複使用的片段 | 頁首、頁尾、法律免責宣告或取消訂閱區塊會在多個行銷活動之間共用 | 片段的變更會傳播到所有參照它的訊息（即時和草稿）；每則訊息最多30個片段 |
| 內嵌內容 | 沒有跨其他行銷活動的共用元素的一次性訊息 | 單次使用內容更簡單；無傳播風險 |

#### UI導覽

行銷活動>選取行銷活動>編輯內容>傳送電子郵件至Designer （或SMS/推播編輯器）

#### 關鍵設定詳細資料

- 使用拖放內容元件（文字、影像、按鈕、分隔線、欄）來設計訊息版面
- 設定電子郵件標頭屬性：主旨行、標頭文字和寄件者表面
- 使用Handlebars語法插入個人化運算式（例如，`{{profile.person.name.firstName}}`）
- 設定協助程式函式以格式化（日期、數字、字串操控）
- 新增條件式內容規則，以根據設定檔屬性或區段成員資格顯示不同內容
- 設定不符合任何條件時的預設遞補內容
- 對於SMS，在字元限制考量事項內撰寫訊息內文
- 對於推播，設定標題、內文、影像和動作（深層連結或URL）
- 使用範例設定檔預覽訊息，以驗證個人化呈現
- 傳送證明電子郵件給內部利害關係人以供稽核
- 使用電子郵件轉譯功能測試跨電子郵件使用者端的轉譯

#### Experience League檔案

- [建立電子郵件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [設計電子郵件內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [使用電子郵件Designer內容元件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/content-components)
- [新增個人化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization語法](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [輔助函式](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [動態內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [使用內容範本](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [使用內容片段](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [預覽和測試您的內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)
- [傳送電子郵件校樣](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/proofs)
- [電子郵件呈現](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/email-rendering)
- [建立簡訊訊息](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/create-sms)
- [設計推播通知](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/design-push)

### 階段4：建立行銷活動或歷程

**應用程式函式：** AJO：行銷活動執行（選項A和C）或AJO：Journey Orchestration （選項B）

此階段會建立行銷活動或歷程，將對象、訊息和執行機制繫結至交付專案單位。 這是三個實作選項分歧最大的地方。

#### 決定：內容實驗

行銷活動是否應該包含A/B測試或多變數實驗，以最佳化訊息效能？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 無實驗 | 對內容有效性有高度信賴的單一訊息變體 | 最簡單的設定；最快速的啟動 |
| A/B測試（2種變體） | 透過明確的假設來測試主旨列、CTA或內容版面 | 以50/50或加權配置分割流量；需要足夠的對象規模才能達到統計顯著性 |
| 多變數測試（3個以上的變數） | 同時測試多個內容元素 | 需要較大的對象；達到信賴臨界值的持續時間較長；每個實驗最多10個處理 |

#### 決定：頻率限定

此行銷活動是否應遵守全域頻率上限規則，以防止過度傳訊？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 套用頻率規則 | Campaign是更廣泛的傳訊方案的一部分，可同時傳送多封郵件 | 避免客戶疲勞；超過上限的設定檔會從傳送中隱藏 |
| 免除上限 | Campaign需要大量時間或異動，且必須觸及所有合格的設定檔，無論近期的訊息歷史記錄為何 | 謹慎使用；將行銷活動從頻率規則中排除可能會造成過度傳送訊息的風險 |

#### 決定：優先順序分數

此行銷活動相對於其他作用中行銷活動應該有哪個優先等級？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 高優先順序(75-100) | 關鍵行銷活動 — 主要產品推出、限時優惠、法規通知 | 發生衝突時，優先於優先順序較低的行銷活動 |
| Medium優先順序(25-74) | 標準行銷活動 — 電子報、參與行銷活動、一般促銷活動 | 與其他行銷活動平衡；如果較高優先順序的行銷活動衝突，可能會隱藏 |
| 低優先順序(0-24) | 善待傳送 — 資訊更新、次要促銷 | 將抑制以支援較高優先順序的行銷活動 |

#### 選項差異之處

選項A （排程的行銷活動）的&#x200B;**：**

**UI導覽：**&#x200B;行銷活動>建立行銷活動>排程>行銷

1. 建立新的排程行銷活動
2. 從受眾選擇器選取目標受眾
3. 選取頻道介面並連結編寫的訊息內容
4. 設定執行排程：立即、特定日期/時間或週期性
5. 可選擇啟用內容實驗並定義處理變體
6. 可選擇設定頻率上限和優先順序分數
7. 檢閱完整的行銷活動設定
8. 啟動行銷活動

選項B的&#x200B;**（對象觸發的歷程）：**

**UI導覽：**&#x200B;歷程>建立歷程

1. 使用「讀取對象」進入事件建立新歷程
2. 選取目標對象作為專案來源
3. 設定重新進入規則（允許重新進入、一次性進入或等待期間後重新進入）
4. 可選擇新增等待節點（例如，在資格認證後等待24小時）
5. 選擇性地新增條件節點（例如，檢查設定檔是否符合其他條件）
6. 新增訊息動作節點並選取頻道介面和編寫的內容
7. 設定退出條件（例如，個人資料轉換、個人資料取消訂閱）
8. 可選擇在訊息動作上啟用內容實驗
9. 檢閱並發佈歷程

選項C （API觸發的行銷活動）的&#x200B;**：**

**UI導覽：**&#x200B;行銷活動>建立行銷活動> API觸發

1. 建立新的API觸發的行銷活動
2. 選取頻道介面並連結編寫的訊息內容
3. 為將在API觸發裝載中傳遞的資料設定內容個人化權杖
4. 檢閱及啟動行銷活動
5. 記下促銷活動ID以用於外部系統的API觸發器整合
6. 呼叫系統會將觸發要求傳送至具有收件者設定檔和內容資料的行銷活動端點

#### Experience League檔案

- [建立行銷活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [開始使用行銷活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [API觸發的行銷活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/api-triggered-campaigns/api-triggered-campaigns)
- [開始使用歷程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [讀取對象歷程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [開始使用內容實驗](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [建立內容實驗](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [頻率規則](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [優先順序分數](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [識別潛在衝突](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)

### 階段5：分析報表和效能

**應用程式函式：** AJO：報表與效能分析

此階段透過即時報告監視執行期間的傳遞量度，並透過歷史報告分析完成後的行銷活動績效。 可選擇設定CJA整合，以進行更深入的跨管道分析。

#### 決定：報告方法

此行銷活動需要什麼層級的報表？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 僅限AJO原生報表 | 標準傳送和參與量度就足夠了（傳送、傳送、開啟、點按、跳出） | 無其他設定；報告內建於行銷活動/歷程UI中 |
| AJO原生報表+ CJA analysis | 除了傳遞量度以外，還需要跨管道影響分析、歸因模型或funnel分析 | 需要CJA連線和連結至AJO資料集的資料檢視；提供更深入的分析功能 |
| CJA程式化報告 | 利害關係人需要自動化儀表板或排程報告傳遞 | 需要CJA Reporting API整合；適合用於執行控制面板和週期性效能摘要 |

#### 決定：轉換追蹤

行銷活動的成功衡量標準將如何超越傳遞和參與量度？

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 無轉換追蹤 | 行銷活動目標是認知或參與（開啟、點按），無特定下游動作 | 最簡單；不需要額外的事件追蹤 |
| 網頁轉換追蹤 | 促銷活動CTA連結至追蹤轉換事件（購買、註冊、表單提交）的網頁 | 需要在目的地頁面上使用Web SDK或Analytics標籤；事件必須在AEP資料集中擷取 |
| 自訂轉換事件 | 促銷活動成功與否，取決於網站上未擷取的特定業務事件（例如店內購買、客服中心互動） | 需要將自訂事件擷取至AEP中，並納入報表資料集 |

#### UI導覽

- 即時報告：行銷活動>選取行銷活動>即時報告（或歷程>選取歷程>即時報告）
- 歷史報表：促銷活動>選取促銷活動>所有時間報表（或歷程>選取歷程>所有時間報表）

#### 關鍵設定詳細資料

- 在行銷活動執行期間存取即時報告，以監控即時傳遞和參與
- 檢閱關鍵量度：已傳送、已傳送、退信、開啟、點按、取消訂閱（電子郵件）；已傳送、已傳送、點按、錯誤（簡訊）；已傳送、已傳送、已傳送、開啟、動作（推播）
- 行銷活動完成後，存取歷史（所有時間）報告以進行全面分析
- 分析傳送funnel：已鎖定目標>已傳送>已傳送>已傳送>開啟>點按
- 檢閱錯誤和排除原因，以識別傳遞問題
- 如果已啟用內容實驗，請先檢閱實驗結果並等待統計信賴度，再宣告獲勝者
- 針對CJA整合，請確認AJO資料檢視包含相關的AJO資料集（訊息回饋事件資料集、電子郵件追蹤體驗事件資料集）

#### Experience League檔案

- [行銷活動即時報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [行銷活動全域報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [歷程即時報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [歷程全域報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [內容實驗報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [使用Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [AJO + CJA整合指南](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

## 實施考量

本節涵蓋護欄、常見陷阱、最佳實務和取捨決定。

### 護欄和限制

- 每個沙箱最多500個作用中即時行銷活動 — [Journey Optimizer護欄](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- 每個沙箱最多4,000個區段定義 — [即時客戶設定檔護欄](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- 每個沙箱每個管道型別最多10個管道表面
- API觸發的行銷活動支援每個觸發請求最多20個設定檔收件者
- 行銷活動一旦啟動即無法編輯 — 改為複製和修改
- 即時報表每60秒重新整理一次，並顯示過去24小時的資料
- 行銷活動完成後，可能需要最多2小時才能完全填入歷史報表
- 每個內容實驗最多10個處理（變體）
- 每個沙箱最多10個上限設定
- 每則訊息最多30個內容片段
- 建議電子郵件大小上限為100 KB，以實現最佳傳遞能力
- IP熱身計畫應在2-4週內逐漸增加新IP的容量
- 隱藏清單專案會保留至可設定的期間（軟退信的預設值為14天）

### 常見陷阱

- **在IP熱身完成之前傳送：**&#x200B;立即傳送大量的IP新位址將由ISP標示，導致傳遞能力不佳並可能列入黑名單。 在生產作業傳送新IP之前，請務必完成IP熱身計畫。

- **不在多個設定檔之間測試個人化：**&#x200B;如果參照的XDM路徑不存在或某些設定檔為空，則適用於一個測試設定檔的Personalization Token可能會失敗。 永遠使用代表不同資料完整度層級的多個測試設定檔預覽。

- **略過隱藏清單檢閱：**&#x200B;過時的隱藏清單專案可能會封鎖傳送至有效位址，而遺漏專案可能會導致傳送至產生跳出的無效位址。 在主要行銷活動之前檢閱及清除隱藏清單。

- **忽略促銷活動的頻率限定：**&#x200B;在其他促銷活動同時生效時傳送促銷活動而沒有頻率限定，可能會導致設定檔在短時間內收到多封郵件，進而導致取消訂閱和垃圾郵件投訴。

- **排程行銷活動而不驗證對象母體：**&#x200B;在確認目標對象之前啟動行銷活動，評估母體結果不為零，因此傳送了零則訊息。 一律在啟用前驗證對象規模。

- **針對受眾觸發的歷程使用批次評估：**&#x200B;如果歷程使用具有批次評估的讀取受眾專案，則設定檔不會近乎即時進入。 當需要近乎即時歷程輸入時，對對象使用串流評估。

- **未設定同意強制執行：**&#x200B;在沒有有效行銷同意的情況下傳送訊息給設定檔，違反法規並損害傳遞能力信譽。 確保在頻道介面層級填入和強制執行同意欄位。

### 最佳實務

- 對於簡單的廣播使用案例，從選項A （排程行銷活動）開始，只有在需要預先傳遞邏輯或行為導向計時時，才會升級至選項B （對象觸發的歷程）
- 一律在電子郵件內文中包含一鍵式list-unsubscribe標題和取消訂閱連結，以符合最大規範
- 為頁首、頁尾和法律免責宣告建立可重複使用的內容片段，以確保跨行銷活動的一致性
- 在啟用行銷活動之前設定頻率上限規則，以防止在同時傳送時過度傳送訊息
- 使用內容實驗來最佳化主旨行和CTA，從A/B測試開始，然後再進行多變數實驗
- 指派優先順序分數給所有作用中的行銷活動，以確保一致的衝突解決方案
- 排程批次對象評估在行銷活動執行時間之前完成，以確保新的對象資料
- 傳送校樣電子郵件並使用電子郵件呈現功能來驗證訊息在啟用之前可在電子郵件使用者端間正確顯示
- 在行銷活動啟動後立即監視即時報告，以及早發現傳送問題
- 封存行銷活動設定和實驗結果，以供未來參考和持續最佳化

### 權衡決定

選擇實作時，應評估下列利弊。

#### 簡單性與彈性

排程行銷活動（選項A）提供最簡單的設定，但沒有傳遞前邏輯。 受眾觸發的歷程（選項B）提供預先傳送邏輯，但增加設定複雜性。

- **選項A優點：**&#x200B;上市速度、營運簡化、行銷人員自助服務
- **選項B偏好：**&#x200B;行為目標定位、條件隱藏、多步驟歷程的可擴充性
- **建議：**&#x200B;從選項A開始，直接傳送。 只有當使用案例在傳送之前確實需要等待、條件或分支邏輯時，才移至選項B。 避免將歷程畫布用於無法從協調功能受益的簡單批次傳送。

#### 對象新鮮度與評估成本

串流評估提供近乎即時的對象更新，但具有區段規則限制。 批次評估支援所有區段規則功能，但會依每日排程進行評估。

- **串流優惠：**&#x200B;及時性、行為導向的正確性、受眾觸發的歷程專案
- **批次偏好：**&#x200B;複雜的對象邏輯、大量母體、較低的評估額外負荷
- **建議：**&#x200B;請對每日新鮮度足夠的已排程行銷活動使用批次評估（選項A）。 對受眾觸發的歷程（選項B）使用串流評估，其中設定檔在符合資格時必須輸入。 如果對象區段規則運算式不符合串流條件，請重組規則或接受批次層級的延遲。

#### Personalization深度與製作複雜性的比較

更深入的個人化（條件式內容區塊、動態區段）可改善參與度，但會增加製作和測試的工作量。

- **深入的個人化優點：**&#x200B;較高的參與率、更相關的客戶體驗、更好的轉換
- **簡單的個人化優點：**&#x200B;啟動時間更快，測試負擔更輕，減少發生錯誤的風險
- **建議：**&#x200B;從基本個人化（名字、相關產品類別）開始，並根據測量的效能增益，在條件式內容區塊中建立圖層。 在啟用之前，請一律測試多個測試設定檔中的所有內容變異。

#### 頻率控制與訊息觸及的比較

嚴格的頻率上限可防止過度傳訊，但可能會抑制向最近收到其他訊息的設定檔傳送行銷活動。

- **嚴格的限制偏好：**&#x200B;客戶體驗品質、較低的取消訂閱率、品牌信譽
- **寬鬆的上限偏好：**&#x200B;最大訊息觸及率、較高的總曝光數、行銷活動涵蓋範圍
- **建議：**&#x200B;一律啟用行銷活動的頻率限定。 設定頻道專屬上限（例如，每週3-5封電子郵件、每週1-2封簡訊）。 只有真正的時間關鍵或交易式訊息才可免除上限規則。

## 相關文件

本節提供依主題組織的[!DNL Experience League]檔案的完整連結。

### 行銷活動

- [開始使用行銷活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [建立行銷活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [API觸發的行銷活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/api-triggered-campaigns/api-triggered-campaigns)

### 歷程

- [開始使用歷程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [讀取對象歷程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)

### 管道設定

- [開始使用電子郵件設定](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [委派子網域](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [建立 IP 池](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [IP熱身計畫](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [電子郵件表面設定](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [設定簡訊頻道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [設定推播通知頻道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [管理隱藏清單](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### 訊息製作與個人化

- [建立電子郵件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [設計電子郵件內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [使用電子郵件Designer內容元件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/content-components)
- [匯入或編碼電子郵件內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/code-content)
- [新增個人化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization語法](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [輔助函式](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [動態內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)

### 內容管理

- [使用內容範本](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [使用內容片段](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [預覽和測試您的內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)
- [傳送電子郵件校樣](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/proofs)
- [電子郵件呈現](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/email-rendering)

### 內容實驗

- [開始使用內容實驗](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [建立內容實驗](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [內容實驗報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [統計計算](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-calculations)

### 頻率和衝突管理

- [頻率規則](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [商業規則概觀](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [開始使用衝突與優先順序管理](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [優先順序分數](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [識別潛在衝突](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)
- [歷程上限和仲裁](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)

### 對象和細分

- [Segmentation Service概述](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [區段產生器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [串流區段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [邊緣分段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [對象構成](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Profile Query Language參考](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### 報告

- [行銷活動即時報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [行銷活動全域報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [歷程即時報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [歷程全域報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [使用Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [AJO + CJA整合指南](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

### 資料控管和同意

- [資料控管概覽](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [資料使用標籤概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/labels/overview)
- [同意和偏好設定欄位群組](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)
- [Journey Optimizer中的同意](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)

### 資料模型與身分

- [XDM系統概覽](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [結構描述組合基本面](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)
- [Identity Service總覽](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [合併原則概觀](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

### 護欄

- [Journey Optimizer護欄](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [即時客戶個人檔案護欄](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [擷取護欄](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)

### 教學課程和快速入門

- [開始使用Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/get-started)
- [建立您的第一個行銷活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [建立您的第一個歷程](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
