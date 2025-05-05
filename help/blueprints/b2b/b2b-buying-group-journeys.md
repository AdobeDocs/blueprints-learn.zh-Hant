---
title: 購買群組式行銷和歷程管理Blueprint
description: 瞭解如何在Adobe Journey Optimizer B2B edition中構思、設計和建置符合潛在客戶購買群組的歷程。
solution: Journey Optimizer B2B Edition
exl-id: 0a9da49c-f13a-4f2a-8407-277def2db591
source-git-commit: b777ea5c301fb1fac39bc243b09a02a2f411f40e
workflow-type: tm+mt
source-wordcount: '2118'
ht-degree: 0%

---

# 購買群組式行銷和歷程管理藍圖

行銷團隊目前在向銷售人員提供合格銷售機會方面面臨許多挑戰。 這些挑戰之一是與組織中的適當人員合作，且通常在努力和準確性方面較為明顯。 由於有&#x200B;_個銷售機會得分_，群組太窄，團隊可能會錯過合適的人員。 若使用&#x200B;_帳戶評分_，則需花費更多精力以如此廣泛的帳戶檢視來識別正確的人員。

此挑戰是&#x200B;**_購買群組_**&#x200B;概念的匯入位置。 購買群組可讓行銷人員在帳戶中尋找正確的人員群組，並透過確認潛在客戶及識別他們在群組中的角色來與這些個人合作。

## 如何使用購買群組來確認銷售線索和帳戶

建立並努力完成購買群組，可提高行銷活動在確認銷售機會中的有效性。 購買群組取決於連結至解決方案意圖的相符銷售線索與角色範本。

購買群組的範例可能是&#x200B;_Acme Corp Seeds Buying Group_，其解決方案利益為&#x200B;_AI驅動種子_。

購買群組代表公司中對解決方案感興趣的一組人員。 而且可以識別一個購買群組是否有多個解決方案的興趣，而且個人會出現在多個購買群組中。

Journey Optimizer B2B edition提供的B2B功能增強後，您現在可以解決這些挑戰：

* 缺少&#x200B;_客戶優先_&#x200B;行銷活動。
* Marketing Qualified Lead (MQL)轉換為Sales Qualified Lead (SQL)不一致，需要讓方案與銷售保持一致，以培養MQL
* 缺少可銷售機制來識別並鎖定&#x200B;_競爭_&#x200B;帳戶。
* 收入與管道中的集中風險。

以下KPI與測量使用案例成功相符：

* **意識**：目標客戶是否看到您的廣告，而且這些廣告驅使他們進入您網站的頻率是否比之前更高？
* **參與**： Target客戶來您的網站並參與內容嗎？
* **時間**：銷售團隊需要多少時間才能從各種工具尋找並新增連絡人到商機？
* **成本**：每個潛在客戶在每個平台上的成本為何？

## 帳戶型行銷

常見的使用案例以及此Blueprint的焦點在於帳戶型行銷計畫。 此使用案例會探索當建立的購買群組與角色和解決方案興趣相關聯時，銷售機會會填入其中的一個點。

當您引導個人完成歷程時，會透過表單、CRM同步和LinkedIn啟用，收集有關潛在客戶（購買群組工作流程）的更多資訊。

當潛在客戶清楚地展示解決方案的興趣時，它表示由業務鏡頭定義的業務事件。 此時，企業確信此潛在客戶確實對產品感興趣。 在Journey Optimizer B2B edition中，銷售機會與角色範本中該解決方案的購買群組相關聯（例如影響者、決策者、擁護者和贊助者）。

下圖說明，您可以收集表單中或LinkedIn啟用的詳細資料，並在與聊天機器人互動時限定解決方案意圖。

![購買團體歷程](./assets/buying-group-journey-diagram.svg){zoomable="yes"}

當購買群組完成百分比足夠高時，您可以透過SQL或SOL將群組共用給銷售團隊，以將帳戶中的潛在客戶轉換為完成銷售。

## 以帳戶為中心的解決方案

B2B銷售機會管理的重點在於客戶及其銷售機會。 技術層的設定可支援代表這些特性的資料，這是成功帳戶細分和歷程管理的必要條件。

### 需求

以帳戶為中心的解決方案需要下列應用程式和服務：

* Adobe Journey Optimizer B2B edition
* Adobe Real-time Customer Data Platform (RTCDP) B2B edition
* Adobe Marketo Engage

>[!NOTE]
>
>Journey Optimizer B2B edition的授權應包括下列專案：
><ul><li>連線至Experience PlatformB2B的Journey Optimizer B2B edition執行個體</li><li>Marketo Engage執行個體已同步至RTCDP</li></ul>
>&gt;<br/>
>&gt;若為現有Marketo Engage客戶，建議連線至現有執行個體。
>&gt;<br/><br/>
>&gt;解決方案有其他擴充功能可用，可增強設定檔豐富度：
>&gt;<ul><li>RTCDP的其他來源可豐富設定檔</li><li>到Marketo Engage的RTCDP目的地</li></ul>

此解決方案的實作也需要您清楚瞭解&#x200B;_帳戶_&#x200B;和&#x200B;_購買群組_&#x200B;的概念，以及它們如何擴大並加速銷售機會資格。 有了這項瞭解，您也必須識別所需的購買群組完整度分數。

### 架構

![購買群組式行銷和歷程管理的解決方案架構](./assets/ajo-b2b-architecture.png){zoomable="yes"}

### 資料結構描述

對於任何資料導向行銷自動化的實作，結構描述的設計對於實作的成功都至關重要。 在設計結構描述之前，請檢閱[B2B名稱空間和結構描述](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo-namespaces)，並確定您瞭解可在新的實作案例中產生新結構描述的自動產生公用程式。

結構描述已特別使用B2B資料元素來擴充，以支援設定檔中的豐富關係，並透過`sourceKey`包含帳戶透視，以將事件和設定檔連結到帳戶結構描述。 結構描述能代表您的組織需求，以及所收集和分析的資料。 為了滿足這些需求，B2B結構具有靈活性，是所需B2B元素的擴展。

在為您的組織設計資料結構時，最佳實務是使用高階實體來表示和標示ERD中的主要實體。 （請參閱[RTCDP B2B結構描述檔案](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/xdm/tutorials/relationship-b2b)中的第一個圖表）。 此程式非常有助於瞭解您需要在每個結構描述中定義的所需資料元素。

在此階段，體驗事件尚無法影響歷程。 除了體驗事件結構描述外，建議您將屬性新增到帳戶，這些屬性代表根據使用者活動進行的主要決策。 這些屬性用於歷程設計器中的分割路徑元素。

>[!NOTE]
>
>目前，Journey Optimizer B2B edition支援的唯一關聯性是透過`Person`實體上的`personComponents[0].sourceAccountKey.sourceKey`屬性建立的直接關聯性。 未來擴展計畫適應B2b結構描述中的帳戶 — 人員關係物件。

### Marketo Engage來源聯結器

若要擴充帳戶資料元素，您可以使用Marketo Engage及其B2B資料來擴充RTCDP和Journey Optimizer B2B edition帳戶檢視。 設定Marketo EngageSource聯結器並將Marketo Engage資料對應到RTCDP結構描述屬性，可讓資料從Marketo Engage流向RTCDP，並在指定時流向設定檔。

如需有關聯結器設定和對應到結構描述之必要欄位的詳細資訊，請參閱[Marketo Engage聯結器檔案](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)。

### 護欄

在[產品說明頁面](https://helpx.adobe.com/tw/legal/product-descriptions/adobe-journey-optimizer-b2b.html)中詳細說明Journey Optimizer B2B edition護欄。

實施相關的護欄

* 在[B2B Audience和Profile Activation藍圖](https://experienceleague.adobe.com/zh-hant/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails)中說明了所有B2B Audience護欄，可直接轉置為Journey Optimizer B2B edition成功。
* 如果帳戶歷程中需要透過Marketo Engage管道進行啟用，或使用CRM Sync來擴充帳戶，則[與Marketo Engage相關的護欄](https://helpx.adobe.com/tw/legal/product-descriptions/adobe-marketo-engage---product-description.html#performance-guardrails)為相關。

請檢閱[Real-Time CDP護欄檔案](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/rtcdp/guardrails/overview)，以瞭解RTCDP護欄的其他詳細資訊。

### 佈建

* 所有執行個體都必須位在相同的IMS組織上。
* 只有一個Journey Optimizer B2B edition執行個體可以連結到一個Experience Platform沙箱。
* 強烈建議您將此[Marketo Source Connector實作至Real-time Customer Data Platform](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)。

## 實作

下列步驟提供在Journey Optimizer B2B edition例項中啟用購買群組的指引，包括受眾啟用，以支援擴充您的帳戶基礎，並著重於遺失購買群組角色範本。

### 必要步驟

1. 定義將代表您帳戶和潛在客戶業務檢視的XDM結構描述。

   首先，您可以定義並建立體驗結構，以符合B2B使用案例需求並涵蓋批次和即時資料來源。 此設計應呈現企業思考客戶與個人實體以及您想要支援的使用案例的方式。 若要讓結構描述成為B2B結構描述，結構描述應該遵循[RTCDP B2B結構描述檔案](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/xdm/tutorials/relationship-b2b)中可用的結構。

   一個實用的做法是從圖表中取得實體名稱，並以相同的方式標籤這些實體，以識別架構中的這些實體。 請注意，某些結構需要特定金鑰（例如`sourceKey`）才能在RTCDP B2B中運作。 短期而言，Journey Optimizer B2B不支援帳戶和人員之間透過帳戶個人關係的&#x200B;_多對多_&#x200B;關係。 使用加速器指令碼以獲得最佳起點：

   * 使用[RTCDP B2B結構描述建立指令碼](https://github.com/adobe/experience-platform-postman-samples/tree/master/Postman%20Collections/CDP%20Namespaces%20and%20Schemas%20Utility)來產生初始結構描述
   * 將使用案例特定欄位新增到產生的結構描述中，以完成結構描述以符合組織的需求。

   在此階段，您擁有Marketo Engage和RTCDP之間的連線，以及結構描述結構，以接受帳戶和個人資料以填入已定義的帳戶區段的資料集。 下一步是將RTCDP與Marketo Engage和Journey Optimizer B2B edition連線。

1. 設定Marketo Engage聯結器，包括將Marketo Engage對應至XDM結構。

   準備好XDM結構和欄位後，繼續使用聯結器將Marketo Engage連線至RTCDP，聯結器會使用來自Marketo Engage和Journey Optimizer B2B的資料饋送資料集。 首先，組織從Marketo Engage到RTCDP類別的欄位對應。 使用[聯結器檔案](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo#field-mapping-from-marketo-engage-to-xdm)中的資訊來識別您要包含在Marketo Engage實作中的欄位。

### 購買群組組態

1. 在Journey Optimizer B2B edition或RTCDP中建立帳戶對象。

   啟用「客戶→對象→瀏覽」頁面中的「排程所有對象」選項，以啟用「帳戶對象」。 （如果此方法無法解決問題，您必須建立客戶設定檔區段，才能建立帳戶對象。）

   若要建立區段，請依照[帳戶對象檔案](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer-b2b/user/account-audiences/account-audience-overview)中的步驟操作。 使用區段產生器搭配您已識別為帳戶對象索引鍵的資料欄位，將是定義對象的主要活動。

   在此階段，您知道透過RTCDP聚焦於帳戶並用於購買群組的組成要素。

1. 定義角色範本。

   在每個購買群組中，識別代表個人在您想要處理的群組中擔任的角色的角色。 例如，您可以使用&#x200B;_決策者_、_影響者_&#x200B;和&#x200B;_冠軍_。 同時定義此角色在購買群組中的權重和條件。

   [角色範本檔案](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-role-templates)說明此程式以及如何定義特殊條件。

1. 定義解決方案興趣。

   解決方案興趣是指示購買群組專注於行銷活動和策略的方式。

   若要定義解決方案興趣，請依照[解決方案興趣檔案](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer-b2b/user/buying-groups/solution-interests)中的步驟操作。 請記住，您會使用它來比對組織中的購買群組與銷售方案。

1. 設定購買群組。

   在購買群組的建置區塊準備就緒後，針對解決方案興趣設定購買群組，並以目標設定帳戶對象，以使用帳戶的正確成員完成角色範本。 使用此設定，將解決方案興趣指派給您識別的角色範本，然後您為該特定產品的銷售成功賦予每個角色權重。

   若要建立購買群組，請依照[購買群組檔案](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-create)中的步驟進行。

   在此階段，您已準備好[建立歷程](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer-b2b/user/account-journeys/journey-overview#get-started-with-a-journey)並開始與帳戶對象合作，以建立購買群組，並符合解決方案興趣的條件。

### Audience activation

透過受眾啟用提高購買群組的完整性。

1. 定義LinkedIn廣告比對的帳戶對象。

   除了電子郵件和表單填寫活動外，Journey Optimizer B2B edition還提供LinkedIn廣告功能，以增加您帳戶的廣度，並透過擴展帳戶潛在客戶範圍和增加行銷活動的觸及率，支援完成購買群組的工作。

   若要使用LinkedIn付費媒體與未完成購買群組或未充分參與的帳戶通訊，請展開或與「帳戶對象」互動，請使用[「LinkedIn帳戶比對對象」功能](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer-b2b/user/account-audiences/linkedin-account-matched-audiences)，透過「帳戶比對對象」產生「LinkedIn廣告」對象。

1. 啟用購買群組的對象。

>[!TIP]
>
>成功行銷活動的幾個提示：
>
>* 行銷活動應具有角色篩選器，以適合缺少角色的購買群組，進而提高ROI。
>* 若要擷取銷售機會，請直接將銷售機會填入表單(LinkedIn或Marketo Engage表單)，並重新鎖定表單遺漏的目標。
