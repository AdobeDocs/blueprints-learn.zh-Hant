---
title: Customer Journey Analytics與即時客戶資料平台
description: 在 Customer Journey Analytics 中統一和分析客戶歷程中的資料和客戶行為，從 CJA 向 RTCDP 發佈對象
solution: Customer Journey Analytics
kt: null
thumbnail: null
exl-id: 9e1ba723-63f2-4622-ba67-f2a315c3ba0c
TQID: https://experienceleague.adobe.com/gbNXsco0cQIcn5O83ofB-rb0PF65v7kaTZ7mTngqHks
product_v2:
  - id: e98b7246-966c-4318-9e95-cad2f7a17dc7
    internal-label: Customer Journey Analytics
feature_v2:
  - id: ce577701-5b9e-4fe4-8fa3-4eedea976da4
    internal-label: Components
source-git-commit: ce7331f279a6e59db95ca3b763148440598cde84
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 8%
---

# Adobe Customer Journey Analytics

Adobe Customer Journey Analytics將來自Adobe Experience Platform和其他來源的客戶互動資料整合到歷程型分析服務中。 此架構提供跨管道分析、B2B CJA衍生專案的核心參考，並可將這些CJA對象發佈至Real-Time CDP。

## Customer Journey Analytics架構

此圖表顯示客戶互動資料流入Customer Journey Analytics的核心流程，用於連線、資料檢視、分析和建立對象。

![Adobe Customer Journey Analytics核心架構](assets/cja.png){width="1000" zoomable="yes"}

## 架構衍生

- B2B Customer Journey Analytics利用帳戶、商機、購買群組和人員維度擴充核心架構，以進行帳戶型分析。
- CJA受眾共用會將從Customer Journey Analytics建立的受眾發佈到Real-Time CDP，以供啟動和下游歷程執行。

## 主要資料流程和整合點

- 客戶互動資料是從Web、行動裝置、商務、CRM和其他來源收集到Adobe Experience Platform中。
- 在Experience Platform連線中選取Customer Journey Analytics資料集。
- 資料檢視會公開量度、維度和計算欄位，以供跨管道分析使用。
- Customer Journey Analytics對象可發佈至Real-Time CDP以進行啟用。
- Customer Journey Analytics見解可透過專用的整合架構與Journey Optimizer搭配使用。

## 支援的使用案例模式

- [B2B分析](/help/blueprints/use-case-patterns/b2b/account-analytics.md) — 分析具有B2B維度的帳戶、機會和人員層級歷程。
- [Customer Analytics與insight產生](/help/blueprints/use-case-patterns/analysis/customer-analytics-insight-generation.md) — 分析跨頻道行為並產生歷程深入分析。

## 進一步閱讀

- [Customer Journey Analytics概觀](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Customer Journey Analytics連線](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/create-connection)
- [發佈Customer Journey Analytics對象](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/publish)
