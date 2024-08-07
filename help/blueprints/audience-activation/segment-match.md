---
title: 區段比對藍圖
description: 了解 Adobe Experience Platform(AEP) 的[!UICONTROL 區段比對]。[!UICONTROL 區段比對]是資料協作服務，可讓您以安全、受管且有利於隱私權的方式，根據通用的產業識別碼來交換區段資料。
solution: Experience Platform
exl-id: d7e6d555-56aa-4818-8218-b87f6286a75e
source-git-commit: 9648235f5b626a8cbf2d8c9a619cf0f3ef1641ca
workflow-type: tm+mt
source-wordcount: '2118'
ht-degree: 80%

---

# 區段比對藍圖

區段比對可讓合作夥伴品牌在其各自的 Experience Platform 環境中共用受眾。品牌的關鍵是根據客戶與消費者直接關係中收集的資料與客戶建立聯繫。透過更佳的控管、權限和偏好管理系統，行銷人員可進一步增強其與主要合作夥伴的第一方驗證對象。

[!UICONTROL 區段比對]是資料共同作業服務，可讓 Experience Platform (AEP) 客戶（稱為&#x200B;_合作夥伴_），以安全、受控且有利於隱私權的方式，根據通用產業識別碼來交換區段資料。

此服務可讓客戶以安全、中立的方式安全地識別相符的 ID，而不需披露其整個資料庫。合作夥伴只會收到重疊 ID 的指定屬性（區段名稱），以可控、同意控管的方式更快、更輕鬆地實現共用。

[!UICONTROL 區段比對]以 AEP 資料控管與同意架構為骨幹。可供所有 B2C 和 B2P Real-time Customer Data Platform 客戶使用。[!UICONTROL [!UICONTROL 區段比對]]的主要功能包括：

* 重疊同意客戶的區段共用
* 共用前重疊報表，以取得預估匹配量的深入分析
* 完全整合的 DULE 政策和許可執行
* 資料共用同意框架骨幹
* 組織區段和合作夥伴的資料摘要

## 應用程式

品牌對發佈商：

第三方 Cookie 和行動廣告 ID 資料淘汰後，「發佈商使用案例」的影響最大。此使用案例對注重以銷售廣告作為商業模式的媒體和娛樂業有重大影響。[!UICONTROL 區段比對]對於具有大型第一方對象、且想要與其廣告商直接合作的發佈商而言，是一條途徑。廣告商可直接與發佈商合作，針對發佈商屬性上相符的對象進行廣告宣傳，以便精細鎖定目標或分析行銷活動。

### 品牌對品牌

消費者歷程從來不是線性的。例如，客戶可能忠於航空公司及其信用卡公司。使用[!UICONTROL 區段比對]，航空公司和信用卡公司可以建立資料合作關係來了解重疊的對象，然後量身打造優惠活動以為每家公司的忠實消費者帶來個人化的體驗。

### BU 對 BU

全球跨國公司在獨立運營業務部門之間進行資料協作方面面臨挑戰。鑒於跨 BU 的隱私權政策、贏取或管理權限的不同，將資料合併至單一沙箱可能是不可能的。

[!UICONTROL 區段比對]有助於跨大型組織的分散行銷團隊，進行更有效率地協作，同時繼續獨立運作

## 架構

![區段比對架構](assets/architecture-segment-match.png){zoomable="yes"}

[!UICONTROL 區段比對]不是可購買資料的資料市集。而是 AEP 功能，可搭配特定合作夥伴使用第一方資料，透過隱私權和同意控制協助進行協作。[!UICONTROL 區段比對]有助於專注於改善客戶關係和提升品牌。如果存在預先存在的品牌或合作夥伴關係，則這是有益的。[!UICONTROL 區段比對]體驗易於管理、可擴充，且可讓管理員以選擇加入、可控的方式共用區段。

[!UICONTROL 區段比對]可以：

* 使用標準人員層級識別碼（例如雜湊電子郵件或電話號碼），在組織之間安全地移植區段成員資料
* 對象共用 UI 和含有通知的工作流程
* 預先共用的重疊估計數
* 自助式合作夥伴設定
* 精選的標準化命名空間（雜湊電子郵件、雜湊電話、ECID、IDFA、GAID）重疊
* 強制執行資料共用同意
* 共用受眾生命週期管理
* 共用工作流程中的 DULE 實施
* 每日批次更新

[!UICONTROL 區段比對]可建立互連的客戶體驗。支援的持久識別碼為雜湊電子郵件、雜湊電話號碼，以及 ECID、IDFA 和 GAID 等識別碼。客戶可以建立動態消息，在品牌沙箱之間比對和移動對象資料，具備強大的控管、透明度和撤銷功能，以用於廣告和行銷活動

## 先決條件

[!UICONTROL 區段比對]的先決條件：

* RT-CDP 活動許可
* 支援的標準雜湊識別碼為 SHA256 雜湊電子郵件、雜湊電話、ECID、Apple IDFA 和 GAID
* 隱私權架構與同意策略
* 客戶之間已簽訂資料共用協定

## 安全性

### RBAC

管理合作夥伴的[!UICONTROL 區段比對]流量由 RBAC 保護。只有具有適當權限的個人才能啟動、接受或管理合作夥伴。這可在產品設定檔的資料擷取區段中完成。需要下列權限：

![對象共用連線](assets/data-ingestion.png){zoomable="yes"}

| 權限 | 說明 |
|---|---|
| **管理對象共用連線** | 此權限可讓您完成合作夥伴交握程式，此程式會連接兩個 IMS 組織以啟用[!UICONTROL 區段比對]流量。 |
| **管理對象共用** | 此權限可讓您與活躍合作夥伴（管理員使用者使用&#x200B;**對象共用連線**&#x200B;存取連線的合作夥伴）建立、編輯和發佈摘要（用於[!UICONTROL 區段比對]的資料包） |

請參閱[官方文件](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/segment-match/overview.html?lang=zh-Hant#understanding-segment-match-permissions)以進一步了解權限。

### 連接 ID

合作夥伴連接過程由&#x200B;**[!UICONTROL 連接 ID] 管理，**&#x200B;這是隨機產生的識別碼，會對應至特定 AEP 沙箱。起始和管理合作夥伴沙箱時需要此連接 ID。此外，還可以重新產生連接 ID 以視需要重新設定合作夥伴連線。

### 治理

任何資料集或資料屬性，*C11* 合同標籤為[!UICONTROL 區段比對]服務。使用這些屬性的區段無法用於[!UICONTROL 區段比對]。這可提供區段可用於或無法用於[!UICONTROL 區段比對]的控件。此外，建立的自訂原則和行銷動作也會強制執行。依預設，會停用原則，且必須啟用以執行。共用區段時選擇的電子郵件行銷和現場廣告等限制也會傳播並與合作夥伴共用。

### 同意

[!UICONTROL 區段比對]的同意設定可透過下列方式管理：

* 在組織層級、在上線期間，使用同意檢查的退出或加入設定。

  此設定決定是否可共用使用者資料。預設值設為選擇退出，指出使用者資料可在 AEP 客戶已具備資料共用使用所需同意協定的假設下共用。您可以聯絡 Adobe 客戶經理，並額外勾選強制 AEP 客戶明確追蹤同意，將此設定變更為選擇加入。

* 使用[同意和首選項欄位組](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/consents.html?lang=zh-Hant)設定身分專屬的共用屬性 (idSpecific)。

  此欄位組提供單個對象類型欄位（同意），以捕獲同意和首選項資訊。[!UICONTROL 區段比對]，依預設會包含所有未明確選擇退出的身分，例如：

  ```
  "share": {
  `                `"val": "n"
  `     `}
  ```

  您可以聯絡 Adobe 帳戶管理員以變更此設定，僅包含具有明確選擇加入的身分識別，例如：

  ```
  "share": {
  `                `"val": "y"
  `     `}
  ```

### 警報

當合作夥伴連線啟動或與合作夥伴共用區段摘要時，會產生警報。

## 設定工作流程

如上所述，設定合作夥伴連線的工作流程是透過 RBAC 管理。擁有正確權限後，若要連線至合作夥伴沙箱，必須共用該合作夥伴組織內該沙箱/實例的連線 ID。

向發送夥伴請求連接後，必須在接收方批准該連接，以確保安全的合作夥伴設定。合作夥伴連接握手可確保兩個組織之間達成協定，並允許 Adobe 代表組織協助[!UICONTROL 區段比對]流程。如果連接已批准且處於作用中狀態，則可從任一方啟動區段共用流程。

### 區段共用

只有在所選識別碼上存在相符項目時，才會與合作夥伴共用區段。可以是一對多合作夥伴關係，這表示區段可以與多個合作夥伴共用。

若要在合作夥伴連線設定後啟動區段共用，傳送合作夥伴應建立摘要。接著，選取應排除區段資料的行銷使用案例或動作，以及耐久識別碼。接著，相關區段便可新增至摘要以供共用。

在此區段共用工作流程中，傳送合作夥伴可在移動任何資料前，透過預估的重疊發現潛在的高價值區段。

整體流程為：

![區段共用](assets/segment-sharing.png){zoomable="yes"}

這些重疊估計提供關鍵的深入分析、合作夥伴發現和資料，以推動資料協作協定。不會跨沙箱移動任何客戶或區段資料，以取得這些重疊的估計量度。任何指定沙箱中，由 Adobe 選取且經過預先雜湊處理的適用身分會新增至可能性資料結構，讓客戶能執行兩者之間的聯合和交集作業。這些操作有助於[!UICONTROL 區段比對]從兩個不同的沙箱中獲取由身份組成的兩個資料結構的估計交集，而無需比較實際值

身分重疊流程取決於來自傳送者和接收者沙箱的&#x200B;**每日完整個人資料匯出**&#x200B;資料集，以識別屬於共用區段的常見個人資料。重疊流程的詳細流程如下所示：

![身分重疊處理序](assets/overlap-process.png){zoomable="yes"}

從傳送合作夥伴完成區段共用後，接收者會收到共用區段摘要的相關通知。必須啟用此區段摘要，接收者的個人資料才能起始區段成員資格資料流。只有區段成員資格會擷取至接收者 IMS 組織的重疊個人資料片段，且不會從傳送者傳送其他身分給接收者。

共用區段位於&#x200B;**[!UICONTROL 區段產生器]**&#x200B;的&#x200B;**[!UICONTROL 對象]**&#x200B;標籤的`AEPSegmentMatch`區段，可在接收者沙箱中建立區段時，用來包含或隱藏對象。

每日重疊流程可讓傳送者與接收者之間區段成員資格保持同步。接收者可停用收到之區段摘要的個人資料，以暫停區段共用流程。

#### 區段退出/登入

在完整個人資料匯出中，個人資料區段成員資格下的共用區段 ID 狀態會有其中一個對應值 — _實現_, _退出_，或&#x200B;_現有_&#x200B;來反映當前狀態。

在每日身分重疊流程中，如果接收者沙箱中存在對應身分，共用區段的這些區段成員資格狀態會傳送至接收者以進行擷取。

#### 區段撤銷

從發件者取消/刪除區段是隨選流程，從接收者取得具有撤銷區段 ID 之所有個人資料的清單。區段 ID 會從這些身分的區段成員資格中移除，並在接收者端擷取。此動作會覆寫現有的區段成員資格片段，而刪除該區段的成員資格。

## 在程式化交易中使用區段比對

隨著第三方Cookie和裝置識別碼的相關限制日益嚴格，程式化廣告正在尋找建立及鎖定受眾的新方法。 已建議了越來越多的「通用ID」解決方案，但業界仍持續變動，尚未達成一致意見，並以可擴充的方式達成相同程度的目標定位，同時平衡適用的隱私權疑慮。

您可以在以隱私權為中心的受眾共同作業中使用Adobe Experience Platform Segment Match，並增強廣告商與發佈商之間的程式化私人交易。 透過區段比對，您可以：

* 分割&#x200B;**廣告非法交易**&#x200B;和&#x200B;**對象**&#x200B;工作流程。
* 允許合作夥伴品牌在同意強制的流程中，使用雜湊電子郵件和雜湊電話號碼等永續性識別碼，針對相互共用和同意的身分識別共用對象中繼資料。

### 使用案例

* 透過程式化的私人交易鎖定第一方對象。
* 透過程式化的私人交易隱藏第一方對象。
* 鎖定透過程式化私人交易植入的第一方對象中的相似對象。

>[!BEGINSHADEBOX]

**請考量下列在品牌(Luma)和媒體網路(ACME)之間的範例工作流程：**

1. 品牌(Luma)透過區段比對與媒體網路(ACME)進行受眾比對。
2. ACME透過Adobe Real-Time CDP目的地將受眾推送至廣告伺服器或程式設計SSP。
3. ACME會使用適用的鎖定目標條件（包括上一步驟中建立的對象）來設定私人詳細目錄交易(ID)。 接著，私有詳細目錄交易ID會推送至Luma的DSP。
4. Luma設定私人詳細目錄交易和流量行銷活動/廣告創意。
5. 接著，行銷活動會透過程式化私人詳細目錄交易進行傳遞。
6. 接著，廣告伺服器或SSP會提供符合已建立目標定位條件的廣告曝光數。 (視合約中是否建立「保證」交易或「偏好」交易而定，其他鎖定目標條件（例如頻率限定）可透過廣告伺服器及/或DSP使用。)
7. 流量會流向Luma的品牌屬性。
8. 然後ACME會透過「區段比對」分享行銷活動後的深入分析或對象，以利重新鎖定目標。

>[!ENDSHADEBOX]

![品牌和發佈者之間的工作流程圖表。](./assets/segment-match-blueprints.png)

>[!IMPORTANT]
>
> 雖然上述解決方案可讓您透過程式化的私人交易輕鬆鎖定第一方資料，但在執行前可能會有一些考量事項，包括但不限於下列範例：
>
>* 同意：品牌、發佈商或零售媒體網路適用的同意收集，以此方式運用資料。
>
>* 原則與授權協定：品牌、發佈商或零售媒體網路遵守任何適用的原則（包括隱私權政策、協力廠商協定），以這種方式運用和啟用資料。



## 更多資訊

* [區段比對](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/segment-match/overview.html?lang=zh-Hant#)
* [權限](https://experienceleague.adobe.com/docs/experience-platform/access-control/home.html?lang=zh-Hant)
* [疑難排解](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/segment-match/troubleshooting.html?lang=zh-Hant)
* [XID](https://experienceleague.adobe.com/docs/experience-platform/identity/api/list-native-id.html?lang=zh-Hant)
