---
title: '[!DNL Journey Optimizer] — 行銷活動協調流程'
description: 可讓行銷人員協調跨傳出訊息通道的已排程、以對象為基礎的多步驟行銷通訊。
solution: Journey Optimizer
exl-id: a8ff16f8-146d-4e1f-9bd0-9eda6af0c69b
TQID: https://experienceleague.adobe.com/aPDagEC1zZdi-Bz29fFf6g5Uy8v4qMPhDA47Cdwl-Sw
product_v2:
  - id: cb954087-f4fc-4456-afb9-e939cabcdc79
    internal-label: Journey Optimizer
feature_v2:
  - id: a653cc2e-bc85-4353-a306-399e5b247978
    internal-label: Journey Optimizer campaigns
  - id: d998adac-2f81-400b-a669-d07bb196e4eb
    internal-label: Journeys
  - id: df64005d-8f9a-422e-ba4d-c6f6dc3454b4
    internal-label: Use cases
  - id: fe338112-e2ce-4876-8989-fc4d497613f1
    internal-label: Email
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
source-git-commit: 79738031788419872e32b8f754febacbfd18cc06
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 6%
---
# [!DNL Journey Optimizer] — 行銷活動協調流程

>[!TIP]
>此架構也記錄為「行銷活動管理與協調」下的[使用案例模式](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md)。

AJO Campaign Orchestration可讓行銷人員跨對外頻道（例如電子郵件、簡訊、推播和直接郵件）設計和執行排程的、以對象為基礎的多步驟通訊。 AJO歷程會使用即時客戶個人檔案中的即時資料來回應個別客戶行為，而行銷活動則是協調行銷工作，按計畫間隔鎖定對象。 行銷活動和歷程結合起來提供互補的方法(€)行銷活動推動品牌參與策略，而歷程提供個人化、回應式體驗。

<br>

## 架構

![參考架構Adobe Journey Optimizer Campaign Orchestration](images/ajo-orchestrated-campaigns.png){width="1000" zoomable="yes"}

<br>

### 訊息執行架構

![參考架構Adobe Journey Optimizer Campaign Orchestration](images/ajo-orchestrated-campaigns-message-sending.png){width="1000" zoomable="yes"}

<br>

### 關聯式存放區 — 資料擷取延遲

![參考架構Adobe Journey Optimizer Campaign Orchestration](images/ajo-orchestrated-campaigns-data-ingestion.png){width="1000" zoomable="yes"}

<br>

## 行銷活動的架構考量事項

- **資料架構**： AJO Campaign Orchestration在下方使用關聯式資料庫來建立對象和協調流程
- **受眾入口網站整合**：與即時客戶設定檔中的受眾入口網站原生整合，可在建立行銷活動時從現有受眾讀取並儲存新受眾至
- **隨選對象建立**：針對緊急行銷使用案例，立即建立、評估及執行對象
- **即時客戶個人檔案整合：**&#x200B;同意和通訊記錄的真實來源；支援個人化的「精裝個人檔案」設計
- **多實體訊息傳送：**&#x200B;可在單一傳遞中為每個設定檔傳送多則訊息（例如，每個預訂向客戶電子郵件地址傳送一則訊息）
- **多實體分段**：開始從關聯式存放區內的任何實體建立對象（例如產品、詳細目錄、計畫等）

<br>

## 護欄

[協調的行銷活動產品連結](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/campaigns/orchestrated-campaigns/guardrails)

[護欄和端對端延遲指引](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails)

<br>

## 相關文件

- [[!DNL Journey Optimizer]個協調的行銷活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/orchestrated-campaigns/orchestrated-campaigns-landing-page.html)
- [[!DNL Experience Platform]檔案](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hant)
- [[!DNL Experience Platform]標籤檔案](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=zh-Hant)
- [[!DNL Experience Platform Mobile SDK]檔案](https://experienceleague.adobe.com/docs/mobile.html?lang=zh-Hant)
- [[!DNL Journey Optimizer]檔案](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=zh-Hant)
- [[!DNL Journey Optimizer]產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/adobe-journey-optimizer.html)
