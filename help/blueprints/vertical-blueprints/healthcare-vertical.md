---
source-git-commit: f7104d114a2644a494003bc78eb20768904f652c
workflow-type: tm+mt
source-wordcount: '2323'
ht-degree: 1%

---
﻿---
title: 醫療保健
description: 了解Healthcare Shield，它是基於平台的應用程式(如Real-Time CDP、Customer Journey Analytics和Adobe Journey Optimizer)的Adobe Experience Platform附加元件。 該附加元件使這些應用程式符合HIPAA和PHI要求。
solution: Experience Platform
---
# 醫療保健盾

Healthcare Shield是基於Adobe Experience Platform的應用程式(如Real-Time CDP、Customer Journey Analytics和Adobe Journey Optimizer)的Adobe Experience Platform附加元件，旨在使這些應用程式HIPAA準備好滿足有關受保護健康資訊(PHI)的處理和使用的要求。

## 關於醫療保健盾的常見問題

以下常見問題集提供了有關Healthcare Shield的常見問題的解答。

### 什麼是HIPAA?

HIPAA是健康保險流通和責任法案(HIPAA)，這是一項美國法規，它規定了重要的保護，以限制由HIPAA覆蓋的實體或業務關聯方(如Adobe客戶)建立、接收、維護或傳輸的受保護健康資訊(PHI)的使用和披露，以及限制這些資訊(PHI)向業務關聯方(如Adobe)使用和披露。

Adobe作為與特定HIPAA就緒Adobe解決方案和HIPAA安全性、隱私和違規通知規則的合規性相關的業務，已準備好HIPAA。

### 什麼是業務協理協定(BAA)，為什麼它重要？

當覆蓋實體或業務關聯(Adobe客戶)使用業務關聯(如Adobe)的服務來建立、接收、維護或傳輸某些類型的消費者資料，即受保護的醫療保健資料(PHI)或ePHI（PHI的電子版本）時，覆蓋實體和業務關聯需要簽訂業務關聯協定(BAA)。

BAA合同要求Adobe，作為Business Associate，通過遵守HIPAA隱私、安全和違規通知規則的要求來適當保護PHI。

借助適用於Real-Time CDP的Healthcare Shield附加元件，Adobe現在能夠與授權此功能的客戶一起執行BAA，以及Adobe Real-Time CDP B2C和Adobe Real-Time CDP B2P版的消費者流。

### 為什麼Healthcare Shield for Real-Time CDP（以及未來基於平台的應用程式）只在美國提供？

由於HIPAA是美國法律，因此我們將Healthcare Shield的可用性限制在美國和受HIPAA管轄的公司。 Adobe打算將業務範圍擴大至其他司法轄區，因為我們考慮當地要求，並有信心能滿足這些要求。

### 什麼是Real-Time CDP的醫療保健盾？

Healthcare Shield for Real-Time CDP適用於作為「受保實體」或「業務關聯」的客戶，他們打算利用Real-Time CDP中的PHI來獲取資料、建立受眾和跨渠道激活，並要求Adobe執行BAA。 Covered Entities with HIPAA需要Healthcare Shield才能實現Real-Time CDP的使用案例。

### 為什麼Real-Time CDP的醫療保健前景要購買Healthcare Shield?

作為Real-Time CDP的附加元件， Healthcare Shield將應用程式升級到「HIPAA就緒」狀態。 這意味著應用程式具有根據HIPAA要求利用PHI的保護機制。 此外，使用Healthcare Shield ,Adobe願意並能夠授權客戶將某些類型的允許的敏感個人資料帶入HIPAA就緒型應用程式。 Adobe將與客戶簽署業務關聯協定(BAA)，這些客戶將授權Healthcare Shield實現相容的基於平台的應用程式。

### 使用Healthcare Shield為Real-Time CDP授權的資料類型是什麼（哪些不是）?

借助Healthcare Shield，品牌可能將以下PHI納入基於平台的應用程式，如Real-Time CDP（「允許的敏感個人資料」）:個人的財務資訊、醫療或健康資訊。 但我們明確排除了可用於識別未成年人濫用藥物、精神健康、遺傳健康記錄或健康記錄的資料、完整帳號、完整信用卡號、政府識別碼（如SSN），以及任何兒童保護法所保護兒童的個人資訊(如美國兒童線上隱私法(「COPPA」)所定義的個人資訊)。

### 使用Healthcare Shield,Real-Time CDP客戶是否可以使用任何類型的PHI來構建受眾並激活它們？

即使客戶可能將允許的敏感個人資料帶入平台原生應用程式，客戶也需要了解，他們應全權負責遵守所有適用法規，並從消費者處獲得適當的權限、同意、許可和授權，以便以預期方式使用資料。

### 使用非HIPAA就緒型Adobe應用程式來獲取和激活客戶資料有何細微差別？

授權Healthcare Shield的客戶不得使用、獲取、收集、共用或將允許的敏感個人資料與任何非HIPAA就緒型Adobe應用程式和服務整合。 例如，客戶不應啟用Audience Manager、Adobe Target和Adobe Analytics等應用程式中包含PHI的區段。 許可Healthcare Shield的客戶可以將允許的敏感個人資料或授權的PHI嵌入到HIPAA就緒型Adobe應用程式中，而不管該資料源是否認為HIPAA就緒。

### 利用非HIPAA就緒型非Adobe應用程式來獲取和激活客戶資料有何細微差別？

客戶授權Healthcare Shield時，應做出正確判斷，以確定他們在何處激活在Adobe應用程式之外包含PHI的段。 Adobe不控制第三方提供者且對第三方提供者不負責，且客戶傳送給第三方提供者的資料可能不支援根據客戶架構中的Adobe資料使用標籤處理資料。 此外，Adobe無法為客戶提供法律建議。

## 重要醫療使用案例

![](Aspose.Words.749b0c49-3370-4549-9a4d-bf21df8fbfb8.001.png)

|**RTCDP B2C版標準使用案例**|**說明**| | :- | :- | |流資料收集|<p> — 可跨Adobe和非Adobe連接使用的標準化、靈活的資料模型</p><p> — 為B2C行銷設計的人員和帳戶型資料結構</p><p> — 標籤管理和事件轉送即時收集和分發事件層級資料。</p><p> — 最佳化設定檔，可縮短體驗提供時間</p>| |受信任的配置檔案管理|<p> — 包含消費者屬性、行為和偏好資料的統一設定檔</p><p> — 資料治理框架靈活、透明，並通過策略建立和自動執行來應用於統一配置檔案，以防止資料濫用。 </p>| |即時激活|<p> — 專為B2C行銷人員設計的拖放區段</p><p> — 個人和帳戶層級身分解析，以及擴充設定檔，以利跨管道啟用</p><p> — 透過跨通路和環境(Adobe和非Adobe)的受眾協調和即時啟用，提供一致的客戶體驗</p>| |客戶贏取|<p> — 將未驗證轉換為已識別/已驗證使用者的深入分析</p><p> — 鼓勵未註冊用戶註冊會籍。</p><p> — 增加和/或贏回訂閱</p><p> — 分析客戶設定檔以了解傾向(例如. 比較高價值區段與表現欠佳的區段，並針對贏取進行最佳化) </p>| |客戶參與|<p> — 根據消費者行為時近和對選件的頻率動作來鎖定選件（線上和離線）</p><p> — 統一連線體驗的數位屬性（例如鼓勵行動應用程式下載，並跨管道使用區段啟用來連線體驗）</p>| |按比例個性化|<p> — 評估邊緣上的區段，以即時同一頁和下一頁個人化</p><p> — 為在歷程中放棄工作階段的訪客（例如放棄購物車、重複無法轉換的訪客）提供獨特且目標明確的體驗，以提高參與度。</p><p> — 統一並連線離線和線上行為，以最佳化和吸引使用者</p>| |交叉銷售/追加銷售|<p> — 在客戶成長的同時留住客戶，並保持與用戶的現有關係</p><p> — 透過跨業務單位/品牌/優惠方案創造新的收入流，創造客戶終生價值</p><p> — 了解不同產品和SKU的AOV（例如頻繁的套件組合、價格敏感性）</p>| |客戶保留率/忠誠度|<p> — 重新啟用消費者以提升忠誠度並避免客戶流失</p><p> — 根據偏好和傾向為高價值客戶組織個人化產品建議</p><p> — 為參與建立標準順序，並為忠實消費者提供特別優惠</p><p> — 連結線上和離線偏好設定，以最佳化各管道的優惠方案</p>| |資料協作|<p> — 在UI中建立握手，以建置資料協作工作流程。</p><p>-(利用跨行業的第一方資料重疊，以便做出明智的戰略性業務決策和開展宣傳活動。</p><p> — 打破資料孤立環境，全面了解客戶歷程</p><p> — 根據使用案例遵守偏好設定和同意</p>| |媒體/行銷效率與最佳化|<p> — 將客戶資料和激活渠道集中並維護在一個記錄系統中，從而提高組織效率</p><p> — 支援抑制宣傳活動，以提高媒體支出/效率</p><p> — 通過治理和政策執行與IT政策相協調</p><p> — 視需要即時提供資料存取權，以支援及時的行銷活動</p>|

## **3 — 相關技術能力**
![](Aspose.Words.749b0c49-3370-4549-9a4d-bf21df8fbfb8.001.png)

**差異**:

||**立即可用**|**醫療保健盾**| | :- | :- | :- | |加密|AEP中的資料加密 [官方檔案](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/encryption.html?lang=en)|<p>AEP中的資料加密 [官方檔案](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/encryption.html?lang=en)</p><p>+</p><p>客戶管理金鑰 </p>| |資料衛生|<p>**基礎**:可讓客戶管理資料生命週期的自助服務工具。 這包括客戶資料刪除、欄位</p><p>在資料集上更新層級並設定資料到期日，以在過期後移除資料。</p><p>限制 **10,000個刪除請求** 每月 </p><p>2個資料集TTL的上限</p>|<p>**Premium**:延長「資料衛生」功能的每日容量/臨界值，以更短的時間組織大型資料集。</p><p>限制 **2,000,000個刪除請求** 作為HealthCare Shield的一部分</p><p>20個資料集TTL的上限</p>| |同意|<p>**基礎**:手動將同意和偏好相關屬性新增至受眾細分，以精細顯示同意和偏好設定。</p><p></p>|<p>**Premium**:根據同意和偏好設定，建立並自動執行關於如何使用客戶資料的原則。</p><p></p>|

### **治理：**
- **資料衛生**
   - [**資料衛生概觀**](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-hygiene/overview.html?lang=en)
   - [**Adobe Experience Platform資料衛生**](https://experienceleague.adobe.com/docs/experience-platform/hygiene/home.html?lang=en)
- **政策執行**
   - [**資料控管概觀**](https://experienceleague.adobe.com/docs/experience-platform/data-governance/home.html?lang=en)
   - [**資料使用原則概觀**](https://experienceleague.adobe.com/docs/experience-platform/data-governance/policies/overview.html?lang=en)
   - [**Adobe Experience Platform的控管、隱私權及安全性**](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/overview.html?lang=en#consent)

### **隱私：**
- **同意**
   - [**自動策略實施**](https://experienceleague.adobe.com/docs/experience-platform/data-governance/enforcement/auto-enforcement.html?lang=en#consent-policy-evaluation)

### **安全性：**
- **存取控制**
   - [**基於屬性的訪問控制概述**](https://experienceleague.adobe.com/docs/experience-platform/access-control/abac/overview.html)
- **用戶活動審核**
   - [**稽核記錄**](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/audit-logs/overview.html)
- **增強加密**
   - [**Adobe Experience Platform安全性概述**](https://www.adobe.com/content/dam/cc/en/security/pdfs/AEP_SecurityOverview.pdf)
   - [**加密值**](https://experienceleague.adobe.com/docs/experience-platform/tags/api/guides/encrypting-values.html?lang=en)
   - [**Adobe Experience Platform中的資料加密**](https://experienceleague.adobe.com/docs/experience-platform/catalog/data-protection.html)
   - [**資料準備映射函式 — 散列**](https://experienceleague.adobe.com/docs/experience-platform/data-prep/functions.html?lang=en#hashing)
- [**Adobe Real-time Customer Data Platform與醫療盾 | Adobe Experience Cloud**](https://experienceleague.adobe.com/docs/customer-data-management-voices-events/events/healthcare-shield.html?lang=en)

實現體驗承諾，並能存取更少的資料。 無論您是廣告商、發行商或代理商，此網路研討會都可協助解鎖

- [**稽核記錄概述 | Adobe Experience Platform**](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/audit-logs/overview.html "https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/audit-logs/overview.html")

了解稽核紀錄如何讓您查看誰在 Adobe Experience Platform 中執行了哪些操作。

- [**資料衛生概觀 | Adobe Experience Platform**](https://experienceleague.adobe.com/docs/experience-platform/hygiene/home.html?lang=en)

Adobe Experience Platform資料衛生功能可讓您更新或清除過時或不準確的記錄，以管理資料的生命週期。

- [**自動策略實施 | Adobe Experience Platform**](https://experienceleague.adobe.com/docs/experience-platform/data-governance/enforcement/auto-enforcement.html?lang=en)

本檔案說明在Experience Platform中將區段啟用至目的地時，如何自動強制執行資料使用原則。

- [**基於屬性的訪問控制概述 | Adobe Experience Platform**](https://experienceleague.adobe.com/docs/experience-platform/access-control/abac/overview.html "https://experienceleague.adobe.com/docs/experience-platform/access-control/abac/overview.html")

本檔案提供Adobe Experience Platform中以屬性為基礎的存取控制資訊
## **4 - HIPAA和Adobe產品和服務**
Adobe繼續創新和適應醫療保健行業客戶的需求，以滿足其特定的隱私和安全需求。 

以下是 [詳細資訊](https://www.adobe.com/trust/compliance/hipaa-ready.html).
## **5 — 高階行銷架構圖**
符合HIPAA要求（而非）的產品：

![](Aspose.Words.749b0c49-3370-4549-9a4d-bf21df8fbfb8.001.png)

[https://lucid.app/lucidchart/8a795213-3bfa-43f3-a542-f0de56123afd/edit?invitationId=inv_d3183739-8c07-4ca2-bfd1-16d819b911a6&amp;page=0_0#](https://lucid.app/lucidchart/8a795213-3bfa-43f3-a542-f0de56123afd/edit?invitationId=inv_d3183739-8c07-4ca2-bfd1-16d819b911a6&amp;page=0_0)

![](Aspose.Words.749b0c49-3370-4549-9a4d-bf21df8fbfb8.001.png)
## **6 — 方法：**
### **實施階段：**
![](Aspose.Words.749b0c49-3370-4549-9a4d-bf21df8fbfb8.001.png)

每個步驟要考慮的方面：

![](Aspose.Words.749b0c49-3370-4549-9a4d-bf21df8fbfb8.001.png)

本節概述一些要遵循的最佳實務，並分為三個階段：
### **訪談階段：**
與利益相關方的面談過程是了解以下方面的關鍵：

- 目標：使用案例類型 — 轉換、探礦、參與等
- 效能：任何服務級別目標期望
- 資料來源：網站/分析、離線/線上、CRM、忠誠度等
- 資料量
- SLT/SLA要求
- 身分 — 身分數、驗證與匿名資料處理
- 資料格式：JSON、CSV等
- 資料質量，需要資料轉換
- 與合作夥伴進行區段比對（共用）的任何計畫 
- 要匯入的任何外部對象
- 加密：預設與客戶管理金鑰
- 資料的混合：被視為e-PHI
- 同意資料收集 — OneTrust、同意SDK
- 目的地需求：頻率和延遲及存取控制需求
- 存取控制
- 資料清理需求
- 資料更新需求
- 警報需求
- API存取

### **設計階段：**
根據面試流程，設計階段將處理以下問題。 不用說，設計檔案需要審查和簽核。 設計文檔可涵蓋以下方面：

- 資料的值：
   - 卷 — 資料攝取量
   - 時間範圍 — 擷取的資料應存留的時間長度
   - 保真度 — 設定檔豐富度
- 考慮AEP護欄以及SLT/SLA要求 
- 授權使用
- 資料隔離需求 — 單個或多個組織中有多個沙箱
- 資料篩選
- 資料衛生要求（資料量和頻率）
- 滿足資料刪除/更新要求的流程和方法 
- 資料轉換需求 — 上游、資料準備、查詢服務
- 了解並判斷主要身分和其他身分
- [XDM架構設計](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html?lang=en)
- 確定資料集數，已配置資料集與未配置資料集
- 合併策略設計
- 同意資料管理
- 治理：角色、標籤、原則、行銷動作和存取控制
- [設定檔擴充](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
- 邊緣/串流/批次的區段設計需求
- 預期的目的地和啟動計畫。 僅考慮HIPAA就緒的目的地需求
- 適用於Analytics的計畫
- 警報
- 新增API存取需求

### **實施階段：**
審核並簽核設計檔案後，實施階段就可以著手處理下列方面：

- 需要的沙箱數量：開發/測試/生產
- 對沙箱的存取控制
- 部署方法
- TTL需求和頻率（資料衛生）
- XDM結構與存取控制
- 同意強制執行
- 治理：角色、標籤、原則和行銷動作 
- 區段
- 資料集和存取控制
- 資料衛生設定
- 目的地設定和存取控制
- 設定警報
- 實作API存取需求
- 使用模擬資料端對端測試

