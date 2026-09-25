---
title: Adobe Real-Time CDP啟用
description: 用於啟用對象和設定檔資料的架構參考，從Adobe Real-Time CDP到廣告、社交、雲端儲存空間，以及企業目的地。
solution: Real-Time Customer Data Platform, Experience Platform
source-git-commit: ce7331f279a6e59db95ca3b763148440598cde84
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%
---
# Adobe Real-Time CDP啟用

此架構顯示Adobe [!DNL Real-Time Customer Data Platform] ([!DNL Real-Time CDP])如何透過串流和批次資料流程，將對象和設定檔資料啟用至廣告、社交、雲端儲存空間和企業目的地。

## 對象和設定檔啟用

架構說明了從[!DNL Real-Time CDP]個對象和設定檔到目的地應用程式的共用啟用路徑。 其中包括廣告和社交平台的目的地啟用，以及用於儲存、分析和下游應用程式工作流程的企業目的地。

![Adobe Real-Time CDP對象和設定檔啟用架構](assets/real_time_cdp_activation.png){width="1000" zoomable="yes"}

## 支援的使用案例模式

上述架構支援下列使用案例模式：

- [對目的地的對象啟用](/help/blueprints/use-case-patterns/audience-building-activation/audience-activation-to-destinations.md) — 對廣告、社交、雲端儲存空間、CRM和其他企業目的地啟用評估過的對象。
- [匿名訪客網頁個人化](/help/blueprints/use-case-patterns/personalization/anonymous-visitor-web-personalization.md) — 支援跨數位管道的對象啟用和設定檔個人化。

## 主要資料流程和整合點

- 將來自多個來源的客戶資料擷取至[!DNL Real-Time CDP]。
- 在[!DNL Real-Time Customer Profile]中統一身分和設定檔屬性。
- 評估設定檔並放入對象以進行啟用。
- 串流或批次對象，以及廣告、社交、雲端儲存和企業目標的設定檔變更。
- 在下遊行銷、銷售、支援、分析和個人化工作流程中使用已啟用的設定檔和受眾資料。

## 進一步閱讀

- [Adobe Real-Time CDP目的地](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [對目的地啟用對象](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [Adobe Real-Time CDP護欄](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/guardrails/overview)
