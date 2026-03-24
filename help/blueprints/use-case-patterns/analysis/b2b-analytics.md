---
title: B2B分析
description: 瞭解如何在跨管道客戶歷程分析中加入B2B帳戶層級資訊。
solution: Customer Journey Analytics, Real-Time Customer Data Platform
exl-id: 9d576e5c-cbd2-4c60-a6b0-88f8b8b963b4
source-git-commit: e8185f348f926acab2ca2e0c3cd55c08c663cf41
workflow-type: tm+mt
source-wordcount: '7528'
ht-degree: 1%

---

# B2B分析

本指南提供使用[!DNL Customer Journey Analytics] ([!DNL CJA]) B2B edition和[!DNL Real-Time Customer Data Platform] ([!DNL RT-CDP]) B2B edition之B2B帳戶層級分析的完整實作參考。 它專為需要將B2B帳戶層級資訊整合至跨管道客戶歷程分析的解決方案架構師、行銷技術人員和實作工程師所設計。

它涵蓋以帳戶為中心的分析的所有可行方法，從扁平帳戶結構到複雜的全域帳戶階層，並提供何時選擇每個選項的指引。 此計畫解決B2B資料連線、帳戶資料檢視設定、工作區分析和儀表板發佈的問題。

B2B Analytics透過帳戶型連線、B2B特定容器（帳戶、全域帳戶、商機、購買群組）和帳戶層級報表，擴充標準[!DNL CJA]功能。 此功能可讓組織在帳戶層次分析行銷與銷售參與度、追蹤商機進展、測量購買群組完整性，以及將收入歸因於延長B2B銷售週期內的行銷接觸點。

## 使用案例概述

B2B組織面臨根本性的分析挑戰：他們的客戶不是個別人員，而是由多個利害關係人、購買群組和機會組成的帳戶。 標準人員型分析無法回答「哪些帳戶最參與？」、「我們的購買群組有多完整？」或「哪些行銷接觸點推動機會進展？」等問題。

B2B Analytics利用[!DNL CJA] B2B edition建立以帳戶為中心的分析檢視，將個人層級的行為資料與帳戶、商機及購買群組維度相結合，藉此解決此問題。[!DNL RT-CDP] B2B edition提供基礎的帳戶設定檔統一和B2B身分解析度，可提供analytics層。 這些解決方案可共同讓組織在帳戶層級建立跨管道歷程分析、將行銷參與與管道進展建立關聯，並向行銷和銷售團隊提供可操作的深入分析。

目標受眾包括B2B行銷營運團隊、需求產生負責人、收入營運分析師，以及需要深入瞭解帳戶層級參與度和管道運作狀態的銷售負責人。

## 主要業務目標

此使用案例模式支援下列業務目標。

### 改善分析和報告

增強報告功能，透過統一的儀表板和自助服務工具提供更快、更實際可行的行銷深入分析。 B2B Analytics可讓組織將來自多個來源的帳戶層級參與資料合併成單一分析環境，提供行銷方案如何影響管道和收入的跨管道可見度。

**KPI：**&#x200B;效率、生產力

[進一步瞭解改善分析和報告](/help/blueprints/business-objectives/analytics-insights/improve-analytics-reporting.md)

### 啟用資料導向式決策

為團隊提供自助分析、即時客戶見解和AI支援的預測以指導策略。 帳戶層級的分析可為行銷和銷售團隊提供排定帳戶優先順序、最佳化參與策略，以及把握潛在商機所需的資料。

**KPI：**&#x200B;效率、生產力

[進一步瞭解如何啟用資料導向式決策](/help/blueprints/business-objectives/analytics-insights/enable-data-driven-decision-making.md)

### 改善銷售機會資格和轉換

透過評分、培育及個人化的後續追蹤，提高銷售機會品質並加速管道進度。 CJA B2B edition提供專為B2B銷售週期設計的延長13個月帳戶回顧期間，以便在整個帳戶歷程中實現準確的多點接觸歸因。

**KPI：**&#x200B;效率、遞增收入

[進一步瞭解如何改善銷售機會資格和轉換](/help/blueprints/business-objectives/qualification-sales-b2b/improve-lead-qualification-conversion.md)

## 戰術使用案例範例

以下案例說明此模式在實際中如何套用。

- **帳戶參與評分分析** — 透過帳戶在網路、電子郵件、事件和內容互動中的彙總參與，來衡量和排名帳戶，以識別高意圖帳戶以進行銷售追蹤
- **購買群組完整度追蹤** — 分析跨帳戶的購買群組構成，以找出角色涵蓋範圍的差距，並優先為不完整的購買群組取得潛在客戶
- **機會管道關聯** — 將行銷參與資料與機會階段進展建立關聯，以瞭解哪些行銷活動和接觸點可促進管道進展
- **多重接觸B2B歸因** — 將具有13個月回顧期間的歸因模型套用至整個B2B購買歷程（從首次接觸到結束交易）中的評分行銷接觸點
- **帳戶歷程對應** — 透過機會建立和關閉，識別共同路徑和摩擦點，將跨管道帳戶歷程從最初的認知視覺化
- **行銷活動對管道的影響** — 測量特定行銷活動對帳戶管道建立、機會提升和收入產生的影響
- **購買群組參與進度** — 追蹤購買群組參與分數如何隨時間演變，並將參與臨界值與機會結果建立關聯
- **以帳戶為基礎的內容效能** — 分析哪些內容資產和主題與特定帳戶區段、產業或購買群組角色產生共鳴
- **銷售和行銷一致性儀表板** — 建置共用儀表板，為行銷和銷售團隊提供帳戶參與度、管道狀況和收入歸因的統一檢視
- **啟用的帳戶區段** — 根據帳戶層級的分析建立B2B區段（例如，「沒有開啟機會的高度參與帳戶」），並發佈這些區段以供下游啟用

## 關鍵績效指標

以下KPI可協助評估此使用案例模式的成功。

| KPI | 說明 | 測量方法 |
| --- | --- | --- |
| 帳戶參與分數 | 彙總帳戶內所有聯絡人的參與量度 | 結合帳戶層級的網站造訪、電子郵件互動、事件出席和內容下載的計算量度 |
| 購買群組完整性 | 購買群組內所需角色的百分比 | 一段時間內追蹤的已填角色與每個購買群組所需角色總數的比率 |
| 受行銷影響的管道 | 行銷活動觸及的管道中的收入 | 相關帳戶聯絡人在歸因時段內具有行銷接觸點的機會值 |
| 帳戶對商機的轉換率 | 產生合格商機的參與客戶百分比 | 具有商機的帳戶除以定義期間內的參與帳戶總數 |
| 平均交易週期長度 | 從首次行銷接觸到成功關閉的時間 | 從第一個已歸因的接觸點到機會關閉日期的平均持續時間 |
| 行銷歸因收入 | 歸因於行銷接觸點的收入 | 透過歸因模型分銷，從具有行銷接觸的成功機會中獲得的收入 |
| 帳戶觸及率和滲透率 | 每個目標帳戶的參與聯絡人數目 | 每個帳戶具有行銷互動的不重複聯絡人，與已知聯絡人總數相比 |
| 購買角色的內容參與度 | 依購買群組角色區段的參與量度 | 依購買群組中的角色/角色劃分的頁面檢視、下載和逗留時間 |

## 使用案例模式

**B2B分析**

在跨管道客戶歷程分析中加入B2B帳戶層級資訊。

**功能鏈：** B2B資料連線>帳戶資料檢視設定> Workspace Analysis >控制面板發佈

## 應用程式

以下應用程式可用來實作此使用案例模式。

- **[!DNL Customer Journey Analytics]B2B edition** — 提供帳戶型連線、B2B特定資料檢視容器、帳戶層級工作區分析、購買群組分析、商機分析、B2B區段，以及具有延伸回顧期間的B2B歸因
- **[!DNL Real-Time CDP]B2B edition** — 提供B2B資料基礎，包括帳戶設定檔統一、B2B身分解析、B2B結構描述類別（Account、Opportunity、購買群組），以及用於擷取B2B參與資料的[!DNL Marketo Engage]整合

## 基礎函式

下列基本功能必須為此使用案例模式準備就緒。 對於每個函式，狀態會指出它通常是必要的、假設為預先設定或不適用。

| 基礎函式 | 狀態 | 必須準備就緒的專案 | Experience League參考 |
| --- | --- | --- | --- |
| 管理與治理 | 必填 | 沙箱已設定為[!DNL CJA]個B2B edition和[!DNL RT-CDP]個B2B edition使用許可權。 為可存取[!DNL CJA]和B2B資料模型的資料工程師、分析師和行銷作業使用者布建的角色。 | [沙箱總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sandbox/home) |
| 資料模型與準備 | 必填 | 使用B2B類別設定的B2B XDM結構描述：XDM商業帳戶、XDM商業機會、XDM商業帳戶個人關係、XDM商業機會個人關係和XDM商業行銷清單成員。 必須定義帳戶屬性、商機階段和購買群組角色的欄位群組。 為設定檔建立和啟用的資料集。 | [XDM系統總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/xdm/home)，[B2B edition結構描述](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/rtcdp/schemas/b2b) |
| 資料來源與收集 | 必填 | B2B資料來源已連線，通常透過[!DNL Marketo Engage]來源聯結器或[!DNL Salesforce] CRM來源聯結器。 帳戶記錄、機會記錄、人員 — 帳戶關係和行為參與事件必須流入AEP資料集。[!DNL Web SDK] 或[!DNL Marketo]整合必須透過帳戶關聯擷取行為事件。 | [來源總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sources/home)，[Marketo Engage聯結器](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo) |
| 身分和設定檔設定 | 必填 | 已設定用來解析個人與帳戶關係的B2B身分解析。 必須連結帳戶ID、人員ID （[!DNL Marketo]銷售機會ID或CRM聯絡人ID）和跨裝置身分識別（ECID、電子郵件）。 身分圖表必須支援B2B資料模型固有的多對多人個人對帳戶對應。 | [身分識別服務總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/identity/home)，[B2B身分識別解析](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/rtcdp/schemas/b2b) |
| 對象定義與細分 | 已假設就位 | 如果要從[!DNL CJA]將B2B區段發佈回AEP以進行啟用，則應該可以使用帳戶層級的對象定義。 若是僅限分析的使用案例，並非最嚴格的先決條件，但建議您針對區段型分析採取此做法。 | [分段服務總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/home) |

## 支援功能

以下功能可擴大此使用案例模式，但不是核心執行的必要功能。

| 支援功能 | 狀態 | 為什麼這很重要 | Experience League參考 |
| --- | --- | --- | --- |
| 計算/衍生屬性建立 | 推薦 | 帳戶設定檔上的計算屬性（例如，總參與分數、上次活動後間隔天數、機會計數）豐富了[!DNL CJA]中可用於帳戶層級分析的分析維度。 | [計算屬性總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/computed-attributes/overview) |
| 資料生命週期管理 | 推薦 | B2B資料集，尤其是來自[!DNL Marketo Engage]的行為事件資料，可能會快速增長。 資料集到期原則有助於管理儲存空間，並確保符合資料保留要求。 | [進階資料生命週期管理](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-lifecycle/home) |
| 資料使用標籤和實作 | 推薦 | B2B資料通常包含敏感的業務資訊（合約價值、競爭情報）。 資料使用標籤和治理原則可確保這些資料在分析和啟用工作流程中得到適當使用。 | [資料控管概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/home) |
| 監控與可觀察性 | 推薦 | B2B來源聯結器([!DNL Marketo]， [!DNL Salesforce])需要監視擷取健康狀態。 [!DNL CJA]中的連線狀況監視可確保分析資料的時效性。 擷取失敗的警報規則可防止陳舊儀表板。 | [可觀察性深入分析概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/observability/home) |
| 報告與分析 | 已包含 | 此模式本身即為分析模式。 此函式原本就包含在核心函式鏈中，可提供報表與分析功能。 | [CJA概觀](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-overview/cja-overview) |

## 應用程式函式

此計畫會從「應用程式功能目錄」中執行下列功能。 函式會對應至實作階段，而非編號步驟。

### [!DNL Customer Journey Analytics] B2B edition

| 函式 | 實作階段 | 說明 |
| --- | --- | --- |
| 以帳戶為基礎的連線 | 階段1：B2B資料連線 | 使用帳戶或全域帳戶作為組織層級分析的主要識別碼來設定連線 |
| B2B資料檢視設定 | 階段2：帳戶資料檢視設定 | 使用B2B特定容器（帳戶、全域帳戶、商機、購買群組）以及標準人員、工作階段和事件容器來定義資料檢視 |
| 帳戶層級Workspace分析 | 階段3：Workspace Analysis | 使用帳戶層級的維度、量度和B2B容器來建立自由格式分析，以進行組織層級的歷程深入分析 |
| 購買群組分析 | 階段3：Workspace Analysis | 透過購買決策程式，分析購買群組構成、參與及進度 |
| 機會分析 | 階段3：Workspace Analysis | 透過銷售funnel階段追蹤商機進展，並與行銷參與資料建立關聯 |
| B2B分段 | 階段3：Workspace Analysis | 使用B2B容器建立區段以進行篩選的帳戶層級分析 |
| B2B歸因 | 階段3：Workspace Analysis | 套用歸因模型與延長的13個月帳戶回顧期間，以進行B2B銷售週期分析 |
| 建立計算量度 | 階段3：Workspace Analysis | 定義B2B KPI的計算量度，例如帳戶參與率、購買群組完整度和管道影響 |
| 儀表板和計分卡發佈 | 第4階段：控制面板發佈 | 為行銷和銷售領導力建立和共用控制面板和行動計分卡 |
| 對象發佈 | 第4階段：控制面板發佈 | 將[!DNL CJA]定義的帳戶型對象發佈回AEP以供下游啟用 |

### [!DNL Customer Journey Analytics] — 標準函式

| 函式 | 實作階段 | 說明 |
| --- | --- | --- |
| 資料連線 | 階段1：B2B資料連線 | 繫結AEP B2B資料集至[!DNL CJA]個連線以進行跨管道分析 |
| 資料檢視設定 | 階段2：帳戶資料檢視設定 | 在B2B資料檢視中設定標準維度、量度、歸因和持續性設定 |
| Workspace Analysis | 階段3：Workspace Analysis | 使用表格、流失、流量、同類群組和歸因視覺效果建立自由格式分析 |
| 指導分析 | 階段3：Workspace Analysis | 在帳戶層級使用引導式工作流程進行funnel、趨勢和保留率分析 |

### [!DNL Real-Time CDP] B2B edition

| 函式 | 實作階段 | 說明 |
| --- | --- | --- |
| 帳戶設定檔統一 | 先決條件(F2/F4) | 使用專門的XDM B2B結構描述類別，將跨來源B2B資料整合至統一的帳戶設定檔中 |
| B2B身分解析 | 先決條件(F4) | 解析支援多重層次帳戶階層與多對多對應的人員與帳戶關係 |
| [!DNL Marketo Engage]整合 | 先決條件(F3) | 透過原生B2B來源聯結器從[!DNL Marketo Engage]擷取行為參與資料和帳戶/潛在客戶記錄 |

## 先決條件

開始實作前，必須具備下列專案。

- [ ] [!DNL CJA] B2B edition授權作用中且已針對組織布建
- [ ] [!DNL RT-CDP] B2B edition授權使用中，且已設定B2B結構描述和帳戶設定檔
- [ 已定義]個B2B XDM結構描述（帳戶、機會、帳戶個人關係、機會個人關係、行銷清單成員）
- [ 已設定] [!DNL Marketo Engage]和/或CRM來源聯結器，且正在主動擷取資料
- [ ]帳戶層級的行為事件資料（網站造訪、電子郵件互動、表單提交）透過帳戶關聯流入AEP
- [ ]個人與帳戶關係已建立在身分圖表中
- [ ]至少有30天的歷史B2B參與資料可用於有意義的分析
- [ ]個利害關係人已同意購買群組角色定義和解決方案興趣對應
- [ ] [!DNL CJA]使用者帳戶已針對B2B edition功能布建適當的產品設定檔
- [ ]目標KPI和報告要求已由行銷和銷售領導定義

## 實作選項

以下小節說明實施此使用案例模式的不同方法。

### 選項A：以帳戶為中心的分析

**最適合：**&#x200B;想要透過帳戶鏡頭分析所有參與和管道資料的組織。 此方法使用「帳戶」容器作為主要分析單位，自上而下檢視帳戶在購買歷程中的進度。

**運作方式：**

設定以帳戶作為主要識別碼的[!DNL CJA] B2B連線。 所有行為事件、商機和購買群組資料都會彙總至帳戶層級。 資料檢視使用「帳戶」作為最上層容器，並將「人員」、「工作階段」和「事件」巢狀內嵌。 如此即可啟用分析，例如「有多少帳戶造訪定價頁面，接著在30天內建立商機？」

以帳戶為中心的分析可為B2B組織提供最自然的檢視畫面，其中帳戶是購買單位。 產業、公司規模、帳戶層級和帳戶擁有者等維度可用來劃分參與模式和管道量度。 歸因會套用至帳戶層級，並具有13個月的回溯期，以因應較長的B2B銷售週期。

**主要考量事項：**

- 需要在身分圖表中進行乾淨的帳戶對個人對應
- 所有個人層級事件都必須歸因於帳戶
- 無法與帳戶關聯的匿名網站流量將不會出現在帳戶層級的分析中

**優點：**

- 提供整個購買歷程的真實帳戶層級檢視
- 啟用符合B2B收入產生方式的帳戶型歸因
- 支援購買群組和商機分析，作為帳戶內的巢狀容器
- 使分析符合以帳戶為基礎的行銷(ABM)策略

**限制：**

- 需要健全的個人對帳戶身分解析
- 匿名或不相符的參與資料會從分析中排除
- 設定比以人為中心的分析更複雜

**Experience League：**

- [CJA B2B edition概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)
- [B2B edition結構描述](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/rtcdp/schemas/b2b)

### 選項B：以全球帳戶為中心的分析

**最適合：**&#x200B;具有複雜帳戶階層的企業組織，其中母公司具有多個子公司帳戶。 此方式使用「全域科目」作為主要識別碼，將所有子公司科目作業累計至母公司組織層次。

**運作方式：**

將[!DNL CJA] B2B連線設定為全域帳戶作為主要識別碼，而非帳戶。 這會彙總母公司組織下所有子公司科目的業務開發資料。 例如，如果「Acme Corp」擁有地區子公司「Acme EMEA」和「Acme APAC」，則「全球帳戶」連線會將來自所有三個實體的所有參與整合為單一分析檢視。

資料檢視包含「全域帳戶」作為頂層容器，「帳戶」、「人員」、「工作階段」和「事件」作為巢狀容器。 這可在相同工作區專案中的全域與子公司科目層次進行分析。 歸因回顧期間適用於全球帳戶層級，擷取整個公司階層中的所有接觸點。

**主要考量事項：**

- 需要在B2B資料模型中定義父子關係的帳戶階層資料
- 必須填入全域帳戶ID，且在所有帳戶記錄中皆為正確
- 子公司帳戶必須正確對應至其母公司

**優點：**

- 提供複雜企業帳戶結構的整合可見度
- 當單一企業客戶有多個帳戶記錄時，避免進行分散分析
- 啟用單一全球帳戶中地區子公司之間的比較
- 支援企業級管道和收入報表

**限制：**

- 需要精確的帳戶階層資料，許多組織都難以維護這些資料
- 僅於全球層次檢視時，可能會模糊子公司的層次模式
- 建立及維護階層關係的其他資料模型化工作

**Experience League：**

- [CJA B2B edition概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)

### 選項C：混合式人員+帳戶分析

**最適合：**&#x200B;從個人型分析轉換為帳戶型分析的組織，或同時需要個人層級和帳戶層級檢視的組織。 此方法會從相同的連線建立兩個資料檢視：一個以人為中心，另一個以帳戶為中心。

**運作方式：**

設定單一[!DNL CJA] B2B連線，其中包含所有B2B資料集（事件、帳戶、商機、購買群組、人員 — 帳戶關係）。 然後建立兩個資料檢視：一個使用「人員」作為主要容器（類似於標準[!DNL CJA]），另一個使用「帳戶」作為主要容器。 分析人員可以根據所詢問的問題在資料檢視之間切換。

以人為中心的資料檢視提供傳統的個人層級歷程分析（例如「成為商機的潛在客戶有哪些轉換路徑？」），而以帳戶為中心的資料檢視則提供組織層級分析（例如「哪些帳戶具有最高的參與對管道轉換率？」）。 兩個檢視都使用相同的基礎資料，以確保一致性。

**主要考量事項：**

- 需要兩個可能具有不同維度和量度設定的資料檢視
- 分析師需要有關何時使用每個檢視的訓練
- 可能需要分別為每個資料檢視建立計算量度

**優點：**

- 提供在個人和帳戶層級分析資料的靈活性
- 對於習慣於個人層級分析的團隊來說，採用路徑更簡單
- 啟用個人層級和帳戶層級量度之間的比較
- 支援銷售線索型與帳戶型行銷策略

**限制：**

- 兩個要維護和保持同步的資料檢視
- 分析師在要使用哪個檢視上可能會感到困惑
- 計算量度和篩選器可能需跨檢視重複

**Experience League：**

- [建立或編輯資料檢視](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [資料檢視總覽](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dataviews/data-views)

### 選項比較

| 條件 | 選項A：以帳戶為中心 | 選項B：以全球帳戶為中心 | 選項C：混合式人員+帳戶 |
| --- | --- | --- | --- |
| 最適合 | 具平面帳戶結構的標準B2B | 具有父子階層的企業 | 轉換組織或雙重需求 |
| 複雜性 | 中 | 高 | Medium — 高 |
| 資料需求 | 帳戶 — 個人對應 | 帳戶階層+對應 | 帳戶 — 個人對應 |
| 歸因範圍 | 帳戶層級（13個月的回溯） | 全域帳戶層級（13個月的回溯期） | 個人和帳戶層級 |
| 匿名資料 | 已從帳戶檢視中排除 | 已從全域檢視中排除 | 包含在人員檢視中，從帳戶檢視中排除 |
| 需要 | [!DNL RT-CDP] B2B edition，[!DNL CJA] B2B edition | [!DNL RT-CDP] B2B edition，[!DNL CJA] B2B edition，階層資料 | [!DNL RT-CDP] B2B edition，[!DNL CJA] B2B edition |
| 維護工作 | 單一資料檢視 | 單一資料檢視 | 兩個資料檢視 |

### 選擇正確的選項

- **如果貴組織具有扁平的帳戶結構（無父子階層）、您的ABM策略在個別帳戶層級運作，而且您想要最簡單的帳戶層級分析路徑，請選擇選項A**。
- **如果目標帳戶是跨區域或部門擁有子公司帳戶的大型企業，且您需要在公司母公司層次合併報表，請選擇「選項B**」。 此選項需要高品質的帳戶階層資料。
- **如果您的組織正在從銷售機會型行銷轉換為帳戶型行銷，您的分析師需要人員層級的funnel分析和帳戶層級的參與分析，或者您同時擁有B2B和B2C業務線，請選擇選項C**。

## 實作階段

下列階段概述建議的實作順序。

### 階段1：B2B資料連線

**應用程式函式：** [!DNL CJA] B2B：以帳戶為基礎的連線，[!DNL CJA]：資料連線

設定將AEP B2B資料集繫結至[!DNL CJA]以進行分析的[!DNL CJA]連線。 此連線定義哪些資料集流入[!DNL CJA]、主要識別碼型別（帳戶或全域帳戶），以及如何擷取歷史資料和串流資料。 此連線是所有後續分析的基礎。

#### 決定：主要識別碼型別

決定連線應使用帳戶ID或全域帳戶ID作為主要識別碼。

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 帳戶 ID | 統一帳戶結構，無父子階層 | 設定更簡單；每個帳戶都可獨立分析。 適合中小企業需求的B2B最常見選擇。 |
| 全域帳戶ID | 具有子公司階層的企業帳戶 | 需要階層資料；彙總父項下的所有子公司。 最適合企業ABM程式。 |

#### 決定：資料集選取和型別指定

決定應包含哪些B2B資料集以及如何輸入每個資料集。

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 事件資料集（行為） | 一律包括 | 網路互動、電子郵件事件、表單提交、內容下載。 必須有時間戳記欄位。 這些是參與訊號。 |
| 帳戶記錄資料集（設定檔） | 一律包括 | 帳戶屬性，例如，產業、大小、階層、所有者。 提供帳戶分析的維度內容。 |
| 機會資料集（查詢/設定檔） | 包括用於管道分析 | 機會階段、值、結束日期。 對於管道和收入歸因分析是必要的。 |
| 購買群組資料集（查詢/個人資料） | 包括用於購買群組分析 | 購買群組角色、參與分數、完整性。 購買群組構成分析時需要。 |
| 人員 — 帳戶關係資料集（查詢） | 一律包括 | 將人員對應至帳戶。 將個人層級事件與帳戶層級分析建立關聯的重要步驟。 |
| 行銷活動/方案資料集（查詢） | 納入歸因 | 行銷活動中繼資料、方案型別、頻道。 啟用行銷活動影響分析。 |

#### 決定：回填範圍

決定應該將多少歷史資料匯入連線。

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 所有現有資料 | B2B銷售週期很長（6至18個月），您需要完整的記錄 | 建議用於B2B。 對於大型資料集，回填可能需要數天的時間，但可提供完整的歸因資料。 |
| 自訂日期範圍（過去2-3年） | 資料品質降低到一定程度後 | 平衡完整性與資料品質。 CRM資料在歷史不一致時很常見。 |
| 無回填 | 僅測試或開發 | 只有新資料會流入。 不適用於生產B2B分析。 |

#### 設定B2B資料連線

**使用者介面導覽：** [!DNL Customer Journey Analytics] >連線>建立新連線

主要設定詳細資料：

- 選取包含B2B資料集的AEP沙箱
- 設定產能計畫的平均每日事件數
- 新增每個資料集並指定其型別（事件、查詢或設定檔）
- 設定人員ID欄位，將帳戶ID或全域帳戶ID用於B2B連線
- 為需要近乎即時更新的資料集啟用串流
- 啟用歷史回填的「匯入所有現有資料」

**選項差異的位置：**

選項A （以帳戶為中心）的&#x200B;**：**
將主要識別碼設定為帳戶ID。 新增帳戶記錄、商機、購買群組和人員 — 帳戶關係資料集。 使用「帳戶ID」欄位設定人員層級事件資料集，以進行跨資料集連結。

選項B （以全球帳戶為中心）的&#x200B;**：**
將主要識別碼設定為全域帳戶ID。 確認帳戶階層資料包含全域帳戶ID欄位。 所有資料集都必須包含或可結合至全域帳戶ID，才能正確彙總。

選項C （混合式）的&#x200B;**：**
建立與所有B2B資料集的單一連線。 使用帳戶ID作為主要識別碼。 在階段2中，將透過在相同連線上使用不同的資料檢視設定來建立以人為中心的檢視。

**Experience League檔案：**

- [連線總覽](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-connections/overview)
- [建立或編輯連線](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-connections/create-connection)
- [管理連線](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-connections/manage-connections)
- [CJA B2B edition概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)

### 階段2：帳戶資料檢視設定

**應用程式函式：** [!DNL CJA] B2B： B2B資料檢視組態，[!DNL CJA]：資料檢視組態

設定資料檢視，定義連線資料在分析中的顯示方式。 對於B2B分析，這包括設定B2B特定容器（帳戶、商機、購買群組）、將B2B結構描述欄位對應到維度和量度、設定具有B2B適當回顧視窗的歸因模型，以及建立B2B商業邏輯的衍生欄位。

#### 決定：容器設定

決定應該啟用哪些B2B容器以及如何命名它們。

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 帳戶+人員+工作階段+事件 | 標準B2B （不購買群組或商機分析） | 最簡單的B2B容器階層。 帳戶是頂層容器。 |
| 帳戶+機會+人員+工作階段+事件 | 需要管道和收入分析 | 將機會新增為容器層級，以啟用機會範圍分析。 |
| 帳戶+購買群組+商機+人員+工作階段+事件 | 完整的B2B分析（包括購買團體組合） | 最全面。 啟用B2B資料模型每個層級的分析。 |
| 全域帳戶+帳戶+人員+工作階段+事件 | 全域帳戶階層分析 | 新增全域帳戶作為帳戶之上的最高層級容器。 |

#### 決定： B2B量度的歸因模型

決定轉換量度的預設歸因模型。

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 線性歸因（13個月的回溯） | 等同於B2B歷程中的所有接觸點 | 最適合瞭解行銷活動的完整組合。 B2B的建議起點。 |
| U形歸因（13個月的回溯期） | 強調首次接觸和上次接觸，點數歸於中間接觸 | 強調銷售機會建立和機會轉換時刻。 在需求產生分析中很常見。 |
| 時間耗損（13個月的回溯） | 較新的接觸點應獲得更多評分 | 當參與造訪間隔是銷售整備的重要訊號時的最佳時機。 |
| 上次接觸 | 轉換前最終接觸點的簡單報告 | 容易理解，但低估了早期行銷的價值。 僅用於快速作業報告。 |

#### 決定：B2B的工作階段定義

決定應如何為B2B參與定義工作階段。

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 30分鐘逾時（預設） | 標準網站分析工作階段行為 | Web參與分析的標準。 可能會分割長時間的內容使用工作階段。 |
| 延伸逾時（60-120分鐘） | B2B使用者參與更長的研究課程 | B2B購買者經常會花很長的時間來檢閱技術內容、定價和檔案。 |
| 事件型新工作階段 | 特定事件應一律開始新的工作階段 | 使用促銷活動點進次數或示範要求時，應一律開始新的分析作業。 |

#### 設定帳戶資料檢視

**使用者介面導覽：** [!DNL Customer Journey Analytics] >資料檢視>建立新資料檢視

主要設定詳細資料：

- 選取階段1中建立的連線
- 設定適用於組織的時區與行事曆型別
- 將容器重新命名為B2B相關術語（例如「帳戶/參與/接觸點」）
- 將B2B結構描述欄位對應到維度：帳戶名稱、帳戶ID、產業、公司規模、帳戶層、帳戶所有者、機會階段、機會值、購買群組角色、解決方案興趣
- 對應參與量度：事件（發生次數）、人員、工作階段、頁面檢視、表單提交、電子郵件開啟、電子郵件點按
- 設定關鍵維度的持續性（例如，帳戶產業會在帳戶層級持續存在）
- 將歸因設為線性，並將13個月的回溯設為轉換量度的預設值
- 為行銷管道分類、參與評分層級和機會階段群組建立衍生欄位

**選項差異的位置：**

選項A （以帳戶為中心）的&#x200B;**：**
使用「帳戶」作為頂層容器設定單一資料檢視。 如果需要管道和購買群組分析，請包括「商機」和「購買群組」容器。

選項B （以全球帳戶為中心）的&#x200B;**：**
將「全域帳戶」設定為最上層容器。 將「帳戶」納入為子容器，以啟用全域與子公司分析。

選項C （混合式）的&#x200B;**：**
從相同的連線建立兩個資料檢視。 資料檢視1使用「人員」作為主要容器（標準[!DNL CJA]行為）。 資料檢視2使用帳戶作為具有B2B容器的主要容器。 將相同的量度對應至兩個檢視（如適用）。

**Experience League檔案：**

- [資料檢視總覽](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dataviews/data-views)
- [建立或編輯資料檢視](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [元件設定概觀](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dataviews/component-settings/overview)
- [持續性設定](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dataviews/component-settings/persistence)
- [歸因設定](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dataviews/component-settings/attribution)
- [衍生欄位](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dataviews/derived-fields)
- [工作階段設定](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dataviews/session-settings)

### 階段3：Workspace分析

**應用程式功能：** [!DNL CJA] B2B：帳戶層級Workspace Analysis，購買群組分析，機會分析， B2B細分， B2B歸因，[!DNL CJA]： Workspace Analysis，計算量度建立，引導式分析

建立可提供KPI中定義之分析深入分析的工作區專案。 此階段包括使用B2B維度和量度建立自由表格、建立B2B KPI的計算量度、設定B2B特定的視覺效果（帳戶層級流量、商機funnel、購買群組參與）、使用B2B容器建立篩選器/區段，以及套用B2B歸因模型。

#### 決定： Analysis Workspace結構

決定應如何組織工作區專案。

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 具有多個面板的單一完整專案 | 小型團隊，所有利害關係人檢視相同的報告 | 更容易維護。 使用面板來分隔主題（參與、管道、歸因）。 每個專案最多40個面板。 |
| 依對象區分的多個重點專案 | 不同的利害關係人需要不同的觀點 | 行銷活動獲得參與度/歸因。 銷售取得管道/帳戶健康狀態。 作業可取得資料品質。 提供更多的維護作業，但提供更佳的目標定位。 |
| 具有引導式分析的範本型專案 | 非專家使用者的自助分析 | 針對funnel和趨勢檢視使用引導式分析。 另存為範本以供重複分析。 最適合廣泛採用。 |

#### 決定： B2B計算量度

決定B2B KPI所需的計算量度。

| 量度 | 公式 | 建立時間 |
| --- | --- | --- |
| 帳戶參與率 | （帳戶事件總數/帳戶總數） | 一律 — 核心B2B量度 |
| 購買群組完整性% | （填入的角色/必要角色） * 100 | 當購買群組分析在範圍內時 |
| 帳戶對商機的轉換 | 具有商機/參與客戶的客戶 | 需要管道分析時 |
| 管道影響% | 受影響的管道值/總管道值 | 需要行銷歸因時 |
| 每個連絡人的平均參與數 | 每個帳戶的事件/不重複人員 | 需要帳戶滲透分析時 |
| 依角色的內容參與度 | 依購買群組角色篩選的事件 | 需要B2B的內容最佳化時 |

#### 決定： B2B篩選器/區段範圍

決定應在哪個容器層級建立篩選器。

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 帳戶層級篩選器 | 限定範圍以符合條件的帳戶的分析（例如，企業帳戶、特定產業） | 包含合格帳戶的所有活動。 最常用於B2B。 |
| 機會層級篩選器 | 限定特定機會型別或階段範圍的分析 | 包括與合格商機相關的所有事件。 |
| 購買群組層級篩選器 | 限定於特定購買群組狀態的分析 | 包含符合購買群組資格的人員所舉辦的活動。 |
| 個人層級篩選器 | 限定分析範圍以符合條件的個人（例如，特定角色、標題） | 標準篩選器行為。 分析B2B內容中的個別參與時使用。 |

#### 建立工作區分析

**使用者介面導覽：** [!DNL Customer Journey Analytics] > Workspace >專案>建立專案

主要設定詳細資料：

- 選取階段2中建立的B2B資料檢視
- 使用依參與量度劃分的帳戶層級維度（帳戶名稱、產業、階層）建立自由表格
- 建立機會funnel視覺效果，顯示各個階段中的機會進度
- 建立顯示角色填充率和每個角色參與度的購買群組組合表
- 設定B2B歸因面板，比較歸因模型（線性、U形、時間衰減）與13個月的回顧
- 建立帳戶流程視覺效果，顯示購買歷程的通用路徑
- 建立同類群組表格，分析一段時間內的帳戶保留率和重新參與率
- 套用B2B篩選器至依帳戶階層、產業或參與層級的區段分析
- 建立重大事件（行銷活動啟動、產品發行、價格變更）的註解

**Experience League檔案：**

- [Workspace概觀](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/home)
- [建立專案](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/build-workspace-project/create-projects)
- [自由格式表格](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/visualizations/freeform-table/freeform-table)
- [歸因面板](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/panels/attribution)
- [流量視覺效果](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/visualizations/flow/flow)
- [流失視覺效果](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/visualizations/fallout/fallout-flow)
- [同類群組表格](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/visualizations/cohort-table/cohort-analysis)
- [篩選器概觀](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-components/cja-filters/filters-overview)
- [計算量度概觀](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)
- [建立計算量度](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-workflow/cm-build-metrics)
- [註解概述](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-components/annotations/overview)
- [引導式分析概述](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/guided-analysis/overview)
- [劃分維度](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/components/dimensions/t-breakdown-fa)

### 第4階段：控制面板發佈

**應用程式功能：** [!DNL CJA]：儀表板和計分卡發佈，[!DNL CJA]：對象發佈

建立可共用的儀表板和行動計分卡，為利害關係人提供B2B分析見解。 此階段也包括將[!DNL CJA]定義的B2B對象發佈回AEP，以便在下游使用案例（例如B2B對象啟用）中啟用。

#### 決定：控制面板傳送方法

決定應如何將B2B分析見解提供給利害關係人。

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| Workspace專案（案頭） | 需要互動式探索的分析師和行銷作業 | 完全互動、向下鑽研、篩選器切換。 需要[!DNL CJA]存取權。 |
| 行動計分卡 | 需要一覽KPI的管理人員與銷售主管 | 具有趨勢線的摘要數字。 可透過[!DNL Adobe Analytics]儀表板應用程式存取。 互動能力有限。 |
| 已排程PDF/CSV匯出 | 沒有[!DNL CJA]存取權的利害關係人需要定期更新 | 依排程自動傳送。 無互動。 最適合用於每週/每月執行摘要。 |
| 以上全部 | 有不同利害關係人需求的大型組織 | 最大觸及。 維護工作量較高。 建議用於成熟的B2B分析程式。 |

#### 決定：從[!DNL CJA]發佈對象

決定是否應將B2B區段發佈回AEP以進行啟用。

| 選項 | 何時選擇 | 考量事項 |
| --- | --- | --- |
| 發佈以帳戶為基礎的對象 | Analytics深入分析應可提供鎖定目標和抑制的相關資訊 | 透過[!DNL RT-CDP]啟用[!DNL CJA]定義的區段（例如「高度參與且沒有未完成銷售機會的帳戶」）。 重新整理步調：每週4小時。 |
| 不要發佈 | Analytics僅供報表使用，不適用於啟用作業 | 更簡單的設定。 在[!DNL RT-CDP]中單獨處理啟動。 |

#### 發佈控制面板和受眾

**UI導覽：** [!DNL Customer Journey Analytics] >專案>共用（適用於Workspace）、專案>建立>行動計分卡（適用於計分卡）、元件>對象>發佈（適用於對象發佈）

主要設定詳細資料：

- 使用關鍵B2B KPI的摘要數字建立執行儀表板（參與帳戶總數、管道值、購買群組完整性）
- 設定趨勢指標的比較期間（月對月、季對季）
- 使用圖磚來建立行動計分卡，用於帳戶參與度、管道健全度和歸因量度
- 新增篩選器給高階主管以依地區、產業或帳戶層級切換檢視
- 設定每週執行報告的排程專案傳送
- 對象發佈：選取B2B篩選器，設定身分名稱空間（帳戶ID），並設定重新整理步調

**Experience League檔案：**

- [建立行動計分卡](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dashboards/create-scorecard)
- [共用專案](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/curate-share/share-projects)
- [排程專案](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/curate-share/send-schedule-files)
- [設定及組織計分卡](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/curate)
- [Adobe Analytics控制面板 — 執行指南](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dashboards/set-up-execs)
- [受眾概述](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-components/audiences/audiences-overview)
- [建立及發佈對象](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-components/audiences/publish)

## 實施考量

以下章節涵蓋實施期間需牢記的護欄、常見陷阱、最佳實務和取捨決定。

### 護欄和限制

- [!DNL CJA]連線只能包含來自一個AEP沙箱的資料集 — [CJA護欄](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-admin/guardrails)
- 每個資料檢視最多5,000個維度和5,000個量度
- 每個資料檢視最多100個衍生欄位
- B2B歸因支援帳戶層級分析最多13個月的回顧期間
- 所有沙箱中每個[!DNL CJA]客戶最多可發佈75個對象
- 對象發佈最低重新整理步調為每4小時
- 從AEP到[!DNL CJA]的串流延遲通常少於90分鐘
- 自由表格支援最多10個深入劃分維度
- 行動計分卡支援每個計分卡最多16個圖磚
- Workspace專案支援每個專案最多40個面板
- 大型B2B資料集（數十億筆記錄）的回填可能需要數天時間才能完成

### 常見陷阱

- **不完整的個人對帳戶對應：**&#x200B;如果個人層級事件無法與帳戶建立關聯，將不會出現在帳戶層級分析中。 請確定所有事件資料集都包含可直接連結至帳戶ID的欄位，或透過人員 — 帳戶關係查詢資料集。 在建立分析之前，稽核缺少帳戶關聯的事件百分比。
- **不正確的資料集型別指定：** B2B查詢資料集（商機、購買群組、人員 — 帳戶關係）必須在[!DNL CJA]連線中正確指定為查詢或設定檔型別。 將查詢資料集錯誤輸入為事件資料集將產生錯誤的結果，因為[!DNL CJA]會嘗試將每個記錄視為時間戳記事件。
- **歸因時段對於B2B來說太短：**&#x200B;使用預設的30天歸因時段將會錯過通常跨越6至18個月的B2B歷程中的早期接觸點。 一律設定B2B歸因量度的13個月回顧期間。
- **錯誤地混合帳戶層級和人員層級的量度：**&#x200B;在帳戶層級的分析中計算「人員」可能會產生誤導。 請確認已在適當的容器層級定義計算量度。 「帳戶參與率」應使用帳戶層級事件除以帳戶，而非人員。
- **過時的購買群組資料：**&#x200B;購買群組構成和角色指派會隨著時間而改變。 如果購買群組資料集未定期更新，完整性量度將會不準確。 請確認來源系統（[!DNL Marketo Engage]或[!DNL AJO] B2B edition）正在主動同步處理購買群組資料。
- **多載單一工作區專案：** B2B分析涵蓋參與、管道、歸因和購買群組。 嘗試將所有內容放在一個專案中會導致載入速度緩慢和導覽混亂。 使用多個重點專案或標籤清楚的面板。

### 最佳實務

- 即使您稍後打算使用選項B （全球帳戶），還是從選項A （以帳戶為中心）開始。 以帳戶為中心的分析更簡單，並在增加階層複雜性之前先驗證您的資料模型。
- 建立專用的「B2B資料品質」工作區專案，追蹤與帳戶關聯之事件的百分比、孤立帳戶的數目，以及購買群組完整性量度。 每週執行此動作，以及早發現資料問題。
- 使用衍生欄位，根據帳戶層級的事件計數，建立參與計分層（高/Medium/低）。 這可簡化分析，並讓控制面板對非技術利害關係人更具可操作性。
- 設定B2B歸因時，請從線性歸因當作基線開始，然後與U型和時間衰減模型比較。 模型之間的差異通常會顯示您的行銷組合是以知名度還是轉換活動為主。
- 發佈「B2B執行摘要」行動計分卡，內含最多8個圖磚，涵蓋對領導力而言最重要的KPI。 保持專注 — 執行計分卡應該會回答「我們的表現如何？」 而不是「為什麼？」
- 為關鍵事件（產品推出、重大促銷活動推出、價格變更、銷售程式變更）加上註解，以提供資料趨勢的內容。 B2B資料通常會顯示沒有事件內容就無法解釋的尖峰和下降。
- 從[!DNL CJA]發佈B2B對象時，請對標準啟用區段使用每日重新整理，對有時效性的區段則使用4小時重新整理。 頻繁的重新整理會消耗處理資源。

### 權衡決定

>[!NOTE]
>下列權衡決定應根據您組織的特定需求和限制進行評估。

**資料完整性與分析正確性的比較**

在帳戶分析中包含所有個人層級事件（即使帳戶關聯性較弱的事件）可改善資料完整性，但如果帳戶對應不可靠，則可能會降低分析準確性。

- **包含所有事件偏好：**&#x200B;完整的參與測量、較高的帳戶參與分數、更廣的能見度
- **排除不相符事件優先：**&#x200B;精確的帳戶層級量度、值得信賴的歸因、可靠的管道關聯
- **建議：**&#x200B;從帳戶層級的分析排除不相符的事件，但將其納入個別人員層級的資料檢視（選項C），以瞭解全貌。 優先改善帳戶關聯資料品質，使其成為平行工作流程。

**B2B歸因回顧期間長度**

較長的回顧期間（13個月）會擷取更多接觸點，但可能包括不再與目前購買決定相關的行銷活動。

- **更長的回溯期（13個月）好處：**&#x200B;擷取完整的B2B歷程，將感知階段活動加入信用，配合較長的銷售週期
- **較短的回顧（6個月）優點：**&#x200B;著重於最近的參與，減少舊接觸點的雜訊，更清楚反映目前的購買意圖
- **建議：**&#x200B;對於銷售週期長（12個月以上）的企業帳戶使用13個月的回溯。 對於週期較短的中端市場帳戶使用6個月的回溯期。 為每個視窗建立個別的計算量度以進行比較。

**單一完整資料檢視與多個重點資料檢視的比較**

含有所有B2B容器和維度的單一資料檢視更容易維護，但可能讓分析師不知所措變得複雜。 多個重點資料檢視（參與、管道、歸因）較容易使用但較難維護。

- **單一檢視的優點：**&#x200B;一致性、更簡單的維護、單一專案中的跨網域分析
- **多重檢視的優點：**&#x200B;分析師的簡單性、更快的載入時間、根據使用案例量身打造的元件清單
- **建議：**&#x200B;從單一完整資料檢視開始。 如果分析師報告難以找到正確的維度和量度，請在分割成多個檢視之前，於相同檢視內建立已組織的元件群組。 使用工作區範本引導分析師使用正確的元件。

## 相關文件

以下資源提供實施此使用案例模式的其他資訊。

**[!DNL CJA]B2B edition**

- [CJA B2B edition概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)
- [CJA概觀](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-overview/cja-overview)
- [CJA護欄](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-admin/guardrails)

**連線**

- [連線總覽](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-connections/overview)
- [建立或編輯連線](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-connections/create-connection)
- [管理連線](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-connections/manage-connections)

**資料檢視**

- [資料檢視總覽](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dataviews/data-views)
- [建立或編輯資料檢視](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [元件設定概觀](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dataviews/component-settings/overview)
- [持續性設定](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dataviews/component-settings/persistence)
- [歸因設定](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dataviews/component-settings/attribution)
- [格式設定](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dataviews/component-settings/format)
- [衍生欄位](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dataviews/derived-fields)
- [工作階段設定](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dataviews/session-settings)

**Workspace和分析**

- [Workspace概觀](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/home)
- [建立專案](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/build-workspace-project/create-projects)
- [自由格式表格](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/visualizations/freeform-table/freeform-table)
- [流量視覺效果](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/visualizations/flow/flow)
- [流失視覺效果](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/visualizations/fallout/fallout-flow)
- [同類群組表格](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/visualizations/cohort-table/cohort-analysis)
- [歸因面板](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/panels/attribution)
- [共用專案](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/curate-share/share-projects)
- [排程專案](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-workspace/curate-share/send-schedule-files)
- [劃分維度](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/components/dimensions/t-breakdown-fa)

**元件**

- [篩選器概觀](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-components/cja-filters/filters-overview)
- [建立篩選器](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-components/cja-filters/create-filters)
- [計算量度概觀](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)
- [建立計算量度](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-workflow/cm-build-metrics)
- [註解概述](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-components/annotations/overview)
- [日期範圍](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/date-ranges/overview)

**對象**

- [受眾概述](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-components/audiences/audiences-overview)
- [建立及發佈對象](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-components/audiences/publish)
- [管理對象](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-components/audiences/manage)

**儀表板和計分卡**

- [建立行動計分卡](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dashboards/create-scorecard)
- [設定及組織計分卡](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/curate)
- [Adobe Analytics控制面板 — 執行指南](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/cja-dashboards/set-up-execs)

**引導式分析**

- [引導式分析概述](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/guided-analysis/overview)
- [funnel檢視](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/funnel/funnel)
- [趨勢檢視](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/guided-analysis/trends/usage)
- [保留檢視](https://experienceleague.adobe.com/zh-hant/docs/analytics-platform/using/guided-analysis/retention/retention-rates)

**[!DNL RT-CDP]B2B edition**

- [RT-CDP B2B edition概述](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/overview#702702)
- [B2B edition結構描述](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/rtcdp/schemas/b2b)
- [B2B來源概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/rtcdp/sources/b2b)

**AEP資料基礎**

- [XDM系統概覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/xdm/home)
- [來源概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sources/home)
- [Marketo Engage聯結器](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
- [Identity Service總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/identity/home)
- [沙箱概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sandbox/home)

**資料控管和生命週期**

- [資料控管概覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/home)
- [進階資料生命週期管理](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-lifecycle/home)

**教學課程與指南**

- [結構描述組合基本面](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/xdm/schema/composition)
- [計算屬性概述](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/computed-attributes/overview)
- [可觀察性深入分析概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/observability/home)
