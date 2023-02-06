---
title: 匿名Audience Activation藍圖
description: 了解如何根據匿名和行為客戶資料，鎖定網路和廣告通路上的受眾。 此功能可在各裝置中實現個人化的統一即時客戶體驗。
landing-page-description: 了解如何根據匿名和行為客戶資料，鎖定網路和廣告通路上的受眾。
solution: Audience Manager
kt: 7211
thumbnail: null
exl-id: f17599f1-2e75-4cbe-841a-9fd1dae71ada
source-git-commit: 4b09d5e43dba53df2f066917f95eae0f74191de8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 匿名Audience Activation藍圖

「匿名受眾啟動」是指根據匿名裝置和行為資料，在網路、行動裝置和廣告通路上鎖定並個人化受眾的功能。

## 使用案例

* 在網站、行動應用程式或支援的廣告頻道上，執行匿名的數位受眾鎖定目標和個人化。
* 根據已知裝置和行為特性，最佳化登錄頁面和預先驗證體驗。
* 運用Audience Manager協力廠商資料網路，進一步精簡和擴展您的目標對象。


## 應用程式

* Audience Manager
* Real-time Customer Data Platform

可運用Audience Manager和Real-time Customer Data Platform來支援站上和廣告目的地的匿名Audience Activation。 請注意，Real-time Customer Data Platform僅支援包含匿名裝置識別碼的廣告目的地子集，如 [目的地檔案](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/advertising/overview.html?lang=en).

Microsoft Bing、Google DV360和TradeDesk是主要支援的Real-time Customer Data Platform廣告目的地，用於匿名裝置型鎖定目標。 除此之外，Real-time Customer Data Platform還支援許多已知客戶型目的地，如 [目的地檔案](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/advertising/overview.html?lang=en) 和如 [已知客戶啟用Blueprint](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/known-customer-audience-activation/known.html).

## 架構

<img src="assets/anonymous_activation.svg" alt="匿名對象啟用 Blueprint 的參考架構" style="width:90%; border:1px solid #4a4a4a" zoomable="yes" />

<br>

## Audience Manager實作步驟

* 如需實作Audience Manager的詳細資訊，請參閱下列 [檔案](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html?lang=zh-Hant).

## Real-time Customer Data Platform的實作步驟

* 如需Real-time Customer Data Platform的實作步驟，請參閱下列 [檔案](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/known-customer-audience-activation/known.html).

## 相關檔案

* [Audience Manager](https://experienceleague.adobe.com/docs/audience-manager.html?lang=zh-Hant)
* [Experience Cloud [!UICONTROL 受眾]](https://experienceleague.adobe.com/docs/core-services/interface/audiences/audience-library.html?lang=zh-Hant)
* [整合 Audience Manager 與 Target](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-other-solutions/aam-target-integration.html?lang=zh-Hant)
* [透過 Audience Manager 分享 Adobe Analytics 區段](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=zh-Hant)
* [已知客戶啟用Blueprint](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/known-customer-audience-activation/known.html).
* [Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/overview.html)
