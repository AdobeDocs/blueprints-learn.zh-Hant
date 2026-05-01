---
title: 支援與銷售案例的即時設定檔存取
description: '[!UICONTROL 即時客戶個人資料]查詢，提供代理協助的支援及銷售之內容。'
solution: Data Collection
kt: 7195
exl-id: 3616cbf1-2e59-4e68-a1ff-1d2e3b344a1c
TQID: https://experienceleague.adobe.com/Ci9pUbGCLQ9uhlQ9l1na7A2NiI9CpCRMLrUSN6lSOnU
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
  - id: fdddec33-c9cb-4459-b8b6-2664395a6f10
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
  - id: b12f6872-9271-4369-85e5-86969a0b99a2
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
  - id: ba929a52-9339-4154-9487-317dc875a3c7
  - id: c132d929-fa62-4271-803e-b823be07b914
  - id: daec7ead-f475-492a-a3b3-02ae08565d6f
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
  - id: e5ae22e3-a3b0-46ed-804f-9abf1bbe3e74
  - id: ee602049-8a18-43df-9299-a689a025a371
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 95ba7aa681e67efb136adac15dc7894cb413a4f0
workflow-type: tm+mt
source-wordcount: 368
ht-degree: 54%

---

# 支援與銷售案例的即時設定檔存取

>[!TIP]
>此Blueprint也可作為Audience Building &amp; Activation下的[使用案例模式](/help/blueprints/use-case-patterns/audience-building-activation/real-time-profile-lookup.md)。

支援和銷售案例藍圖的即時設定檔存取顯示外部應用程式如何存取Adobe Experience Platform的[!UICONTROL 即時客戶設定檔]。

外部應用程式可以透過 API GET 請求存取個人資料。 儲存在個人資料中的屬性、事件、區段會籍及模型驅動的功能然後可用於這些外部非 Adobe 應用程式。

有了此功能，您可以在客戶呼叫您的呼叫中心時顯示豐富的內容。 例如，支援代理可以看見客戶的期限值、反感或接觸行銷活動的傾向性。 銷售代理亦會受益，因為他們可以知道客戶的更多背景或洞察其客戶。

>[!NOTE]
>
>中樞上的設定檔查詢不適用於高輸送量、低延遲的使用案例，例如網頁/行動傳入個人化。 中樞上的設定檔查詢是針對低延遲情境，例如代理程式輔助支援或銷售互動。 若是低延遲、高輸送量的案例，例如網頁/行動個人化或即時優惠方案決策，則應運用Edge設定檔。 Edge設定檔可讓您透過Real-time Customer Data Platform的[自訂Personalization連線](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/catalog/personalization/custom-personalization)進行即時存取。

## 使用案例

* 為代理支援的互動提供更深入的消費者背景，例如支援和銷售經驗。 使用對 Experience Platform 的個人資料查詢，代理可以獲得關於消費者的更多背景，例如最近的購買、行銷活動互動、傾向性、對象會籍，以及即時客戶輪廓中儲存的其他屬性和洞察。

## 架構

<img src="assets/customer_activity_hub.svg" alt="客戶活動中心 Blueprint 的參考架構" style="width:90%; border:1px solid #4a4a4a"  class="modal-image" />

## 護欄

* [[!UICONTROL 即時客戶設定檔]資料的護欄](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hant)

## 相關文件

* [Adobe Experience Platform Activation產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/adobe-experience-platform0.html)
* [[!UICONTROL 即時客戶個人檔案]檔案](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html?lang=zh-Hant)
* [設定檔護欄](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hant)
* [設定檔查詢API](https://www.adobe.io/apis/experienceplatform/home/api-reference.html)
