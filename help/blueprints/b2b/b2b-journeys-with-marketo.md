---
title: 使用Marketo資料藍圖的B2B歷程
description: 使用Marketo Engage資料快速部署Journey Optimizer B2B edition的藍圖。
solution: Journey Optimizer B2B Edition
exl-id: d7bd0bd3-0f61-4e59-855f-27afc147c9aa
source-git-commit: a0cbce2b4ed06517234b18020cef7acbda7de736
workflow-type: tm+mt
source-wordcount: '1574'
ht-degree: 2%

---

# 使用Marketo資料藍圖的B2B歷程

本全方位指南概述Marketo Engage與Adobe Journey Optimizer B2B edition整合的程式。 它涵蓋自訂結構的設定、設定檔和帳戶的擷取，以及針對購買群組協調個人化歷程。 透過使用Marketo Engage資料，此藍圖可確保跨多個管道的精準目標定位和參與，從而推動更符合條件的需求並增強客戶體驗。

## 使用案例

* **建立及管理購買群組**：使用創作AI在目標帳戶中組合及管理購買群組，確保全面涵蓋關鍵利害關係人
* **自動化成員指派**：根據定義的條件（例如內容消耗和CRM資料），自動指派成員給購買群組角色
* **個人化歷程**：根據每個購買群組和成員的角色、帳戶、產品興趣和生命週期階段，設計並視覺化針對他們量身打造的多步驟歷程
* **即時自動化**：使用即時參與觸發程式和資格評分，透過歷程自動化帳戶和購買群組的進度
* **Cross-Channel Engagement**：與多個頻道的購買群組互動（包括電子郵件、簡訊、廣告、聊天、活動和網路研討會），以簡化需求產生和資格
* **AI導向的深入分析**：使用AI導向的深入分析，將個別購買者和整個購買群組的內容傳遞和參與策略最佳化
* **整合資料啟用**：啟用Adobe Real-Time Customer Data Platform的整合帳戶清單，以提供建立及管理購買群組的最新及完整資料
* **增強型Collaboration**：協調行銷和銷售工作，以創造更精確的銷售機會，並加速建立管道

## 應用程式

* Journey Optimizer B2B 版
* Real-time Customer Data Platform B2B版
* Marketo Engage

## 整合模式

| 整合 | 說明 |
| :-- | :--- |
| [Marketo Engage聯結器](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo) | Adobe Experience Platform可協助從Marketo擷取資料，並提供使用服務來建構、加標籤及增強資料的功能。 |
| [Journey Optimizer B2B edition - Marketo Engage動作](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer-b2b/user/account-journeys/journey-nodes/action-nodes#marketo-engage-actions) | 同步Journey Optimizer B2B edition中的Account-Based Marketing與Marketo Engage中的銷售機會型工作，使用以人物為基礎的動作來管理清單成員資格、人物分割和請求行銷活動。 |
| [Journey Optimizer B2B edition - Marketo Engage資產](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer-b2b/user/content-management/assets/marketo-engage-dam/marketo-engage-design-studio) | Marketo Engage Design Studio是Journey Optimizer B2B edition的預設資產來源，可讓帳戶歷程輕鬆進行資產管理。 |

## 架構

![僅含Marketo資料的AJO B2B解決方案架構](./assets/ajo-b2b-marketo-only.png){zoomable="yes"}

## 實施步驟

* 使用以下任一選項安裝B2B結構描述和名稱空間
   * 使用[Postman集合](https://github.com/adobe/experience-platform-postman-samples/tree/master/Postman%20Collections/CDP%20Namespaces%20and%20Schemas%20Utility)
   * 在Platform UI中使用[範本](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sources/ui-tutorials/templates)
* 建立資料字典，定義Marketo欄位和Experience Platform XDM結構描述之間的對應
   * 使用[Marketo物件中繼資料](https://experienceleague.adobe.com/zh-hant/docs/marketo/using/product-docs/administration/field-management/export-all-object-metadata)作為起點
   * [自訂XDM結構描述](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/xdm/ui/fields/overview)以包含您的自訂欄位
   * 檢閱Journey Optimizer B2B edition支援的標準[XDM欄位](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer-b2b/user/accounts/field-mapping)。 如果您需要其他欄位，請開啟支援票證進行設定
      * 人員資料集需要&#x200B;**workEmail.address**
      * 帳戶資料集需要&#x200B;**accountName**
   * 將新的XDM欄位欄新增到匯出的Marketo中繼資料試算表，以記錄預期的對應
* 設定[Marketo Engage來源聯結器](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
   * 使用上面定義的資料字典來定義來源聯結器的[匯入對應](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-prep/ui/mapping#import-mapping)
   * 在考慮[實作考量事項](#implementation-considerations)之前，建議不要啟用設定檔
   * 建議至少擷取人員、公司、商機和活動，因為這些物件在建立您的帳戶對象時最有用
* 實作人員的[身分圖表連結規則](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/identity/features/identity-graph-linking-rules/overview)：
   * 定義如何使用身分名稱空間來連結Person記錄。
   * 在AEP中設定身分名稱空間和身分拼接規則。
   * 使用範例人員資料和預覽工具驗證連結。
* 為[設定檔](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/catalog/datasets/user-guide#enable-profile)啟用人員、公司、商機和活動資料集
* 定義您的前[個帳戶對象](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer-b2b/user/accounts/account-audience-overview)
* [可使用帳戶對象來定義購買群組](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer-b2b/user/accounts/buying-groups/buying-groups-overview)或[帳戶歷程](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer-b2b/user/account-journeys/journey-overview)
   * 當帳戶符合「帳戶對象」的資格時，購買群組工作每天都會執行，以建立購買群組，並在對象更新後立即將角色指派給相關人員。
   * 此外，購買團體維護作業會在每星期五的CT午夜執行。 此每週程式會處理更新，例如移除不再符合資格的成員，或新增在初始對象更新期間未擷取的新符合資格的成員。

## 建議的設定

若要簡化實作並確保與Adobe Journey Optimizer B2B edition的相容性，建議進行下列設定：

* **使用預設的身分識別欄位：**
   * _電子郵件_&#x200B;和&#x200B;_b2b_person_&#x200B;應該保留為Person結構描述中的身分欄位，以支援身分拼接和受眾啟用。
* **對Marketo Source Connector使用預設的對應：**
   * 運用Adobe提供的現成欄位對應，簡化資料擷取並減少設定額外負荷。
* **對AJO B2B使用預設對應：**
   * 針對Journey Optimizer B2B edition採用[標準欄位對應](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer-b2b/user/accounts/field-mapping)，以確保與購買群組邏輯和歷程協調相容。
* **封鎖電子郵件以外所有欄位的欄位更新：**
   * 在Marketo Engage中，針對[電子郵件](https://experienceleague.adobe.com/zh-hant/docs/marketo/using/product-docs/administration/field-management/block-updates-to-a-field)以外的所有欄位，設定欄位管理以&#x200B;_封鎖來自Adobe Experience Platform的更新_。 這有助於維持資料完整性，同時仍可啟用身分解析。
* **使用電子郵件做為唯一的身分名稱空間，實作身分連結規則**
   * 在Adobe Experience Platform中設定[身分圖表連結規則](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/identity/features/identity-graph-linking-rules/overview)，明確將&#x200B;_電子郵件_&#x200B;用作唯一的身分名稱空間。 這些規則可確保設定檔在存在&#x200B;_電子郵件_的資料來源間準確拼接，以啟用強大的身分解析。 依照Adobe的最佳做法，定義連結規則，將電子郵件優先視為穩定且全域唯一的識別碼，以維護一致且符合隱私權要求的識別圖。
此設定在輕鬆部署與資料控管之間取得平衡，確保為協調B2B歷程奠定可靠的基礎。

## 實施考量

在實作Adobe Journey Optimizer B2B edition時，瞭解Real-time Customer Data Platform提供的身分拼接功能至關重要。 此平台會同時在人員和帳戶層級執行身分拼接，確保客戶資料的統一檢視。

### 要點

* **身分拼接**：平台會使用預設識別碼(例如Marketo ID、CRM ID和電子郵件)來拼接身分。 這有助於合併來自不同來源的資料，以建立完整的設定檔。
* **潛在風險**：使用電子郵件作為拼接的識別碼，可能會導致無意中的身分坍塌。 這表示共用相同電子郵件地址的不同個人可能會錯誤地合併到單一設定檔中。 此身分摺疊可能會對CRM資料的準確性產生負面影響，並損害其完整性。
* **合併策略**： B2B CDP採用以時間為基礎的合併策略，其中使用特定設定檔屬性的最新lastUpdatedDate。 此策略可確保最新資料反映在設定檔中。
* **電子郵件考量事項**：必須徹底評估使用電子郵件作為合併設定檔片段的識別碼的情況。 雖然這可能有益，但必須針對優點仔細考量身分塌陷的風險。 有一個缺點是，如果沒有電子郵件做為識別碼，AJO B2B建立的外部對象成員資格不會整合到現有的設定檔中。
* **Marketo人員整合**：在多個AJO記錄合併為單一設定檔時，Marketo B2B會使用潛在客戶ID最低的Marketo人員。

您可以牢記這些要點，針對如何在Adobe Journey Optimizer B2B edition中設定身分拼接做出明智的決策，以確保準確可靠的客戶設定檔。

### 評估身分拼接結果

Query Service可用來檢視身分拼接對非設定檔啟用資料集的影響。 以下查詢可用於進行評估

#### 擷取的記錄數

此查詢會傳回擷取至個人資料集的記錄總數

```sql
select
    count(distinct b2b.personKey.sourceKey)
from
    marketo_person_ajo_b2b
```

#### 複製電子郵件

此查詢會傳回作為平台身分拼接一部分而合併的人員記錄數

>[!NOTE]
>
>資料集表格marketo_person_ajo_b2b是用來提供如何使用Marketo人員資料集的完整範例。
>&#x200B;>您可以在[資料集](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/catalog/datasets/user-guide)工作區中找到您的沙箱資料集。

```sql
select
    SUM(personCount)
from
    (
        select
            emailAddress,
            count(*) as personCount
        from
            (
                select
                    MAX(workemail.address) as emailAddress
                from
                    marketo_person_ajo_b2b
                where
                    workemail.address IS NOT NULL
                group by
                    b2b.personKey.sourceKey
            )
        group by
            emailAddress
        having
            count(*) > 1
    )
```

#### 包含重複記錄的電子郵件地址

此查詢會傳回資料集中重複記錄最多的電子郵件。  此清單可用來檢查其中一些記錄，以更加瞭解連結身分可能會對Marketo和CRM造成哪些影響。  如需有關身分連結運作方式的詳細資訊，請參閱[身分識別服務總覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/identity/home)。

```sql
select
    *
from
    (
        select
            emailAddress,
            MAX(personId) as personId,
            count(*) as personCount
        from
            (
                select
                    b2b.personKey.sourceKey,
                    MAX(workemail.address) as emailAddress,
                    MAX(b2b.personKey.sourceId) as personId
                from
                    marketo_person_ajo_b2b
                where
                    workemail.address IS NOT NULL
                group by
                    b2b.personKey.sourceKey
            )
        group by
            emailAddress
        having
            count(*) > 1
    )
order by
    personCount desc
```

### 選項

#### 移除電子郵件作為身分

分析之後，如果您判斷電子郵件不是有效的欄位，無法當作身分欄位使用，則可修改人員結構描述，以[移除電子郵件做為身分欄位](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/xdm/ui/fields/identity)

#### 封鎖來自Adobe Experience Platform的更新

如果以身分欄位形式保留電子郵件最適合您的使用案例，則可選擇封鎖來自AJO B2B的欄位更新[，並允許AJO B2B主要在Marketo資料上執行。](https://experienceleague.adobe.com/zh-hant/docs/marketo/using/product-docs/administration/field-management/block-updates-to-a-field)

## 護欄

如需使用Marketo Engage時適用於B2B歷程的護欄的全面瞭解，請參閱下列正式檔案：

* [Adobe Journey Optimizer B2B edition — 產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/adobe-journey-optimizer-b2b.html)
包含Journey Optimizer B2B edition的特定護欄和使用引數。
* [Adobe Experience Platform部署護欄](https://experienceleague.adobe.com/zh-hant/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails?lang=en)
涵蓋Adobe Experience Platform解決方案的一般架構和部署護欄。
* [Adobe Marketo Engage — 產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/adobe-marketo-engage---product-description.html#performance-guardrails)
詳細說明Marketo Engage的效能和使用狀況護欄，包括啟用和CRM同步考量事項。
* [Real-Time CDP護欄](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/rtcdp/guardrails/overview?lang=en)
在Real-Time Customer Data Platform內提供資料擷取、細分和啟用限制的指引。

## 相關文件

* [B2B 版 Real-time Customer Data Platform](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-overview)
* [開始使用Real-time Customer Data Platform B2B edition](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-tutorial)
* Real-time Customer Data Platform B2B edition的[護欄](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-guardrails)
* [Adobe Experience Platform](https://experienceleague.adobe.com/zh-hant/docs/experience-platform)
* [Adobe Experience Platform Identity服務](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/identity/home)
* [Marketo Engage](https://experienceleague.adobe.com/zh-hant/docs/marketo/using/home)
* [Adobe Experience Platform - Marketo Source Connector](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
* [Adobe Journey Optimizer B2B edition檔案](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer-b2b/user/guide-overview)
