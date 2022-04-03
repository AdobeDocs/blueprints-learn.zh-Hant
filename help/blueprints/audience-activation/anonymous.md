---
title: 匿名對象啟用 Blueprint
description: 了解如何根據匿名和行為客戶資料，鎖定網路和廣告通路上的受眾。此功能可在各裝置中實現個人化的統一即時客戶體驗。
landing-page-description: 了解如何根據匿名和行為客戶資料，鎖定網路和廣告通路上的受眾。
solution: Audience Manager, Experience Platform
kt: 7211
thumbnail: null
exl-id: f17599f1-2e75-4cbe-841a-9fd1dae71ada
source-git-commit: 3425495df36ff8da0f2fd737b35d294ccafe31bd
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 33%

---

# 匿名對象啟用 Blueprint

匿名用戶激活是指基於匿名設備和行為資料，通過Web、移動和廣告渠道針對受眾進行目標和個性化設定的能力。

## 使用案例

* 在網站、移動應用或支援的廣告渠道上執行匿名數字受眾目標和個性化設定。
* 根據已知設備和行為特徵優化登錄頁和預驗證體驗。
* 利用Audience Manager第三方資料網路進一步優化和擴展您的受眾，以實現目標。


## 應用程式

* Audience Manager
* 即時客戶資料平台

Audience Manager和Real-time Customer Data Platform都可以利用匿名Audience Activation為現場和廣告目的地提供支援。 請注意，Real-time Customer Data Platform僅支援包含匿名設備標識符的廣告目標的子集，這些標識符在 [目標文檔](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/advertising/overview.html?lang=en)。

Microsoft必應、GoogleDV360和TradeDesk是Real-time Customer Data Platform基於匿名設備目標的主要支援廣告目的地。 除此之外，Real-time Customer Data Platform還支援在 [目標文檔](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/advertising/overview.html?lang=en) 如 [已知客戶激活藍圖](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/known-customer-audience-activation/known.html)。

## 架構

<img src="assets/anonymous_activation.svg" alt="匿名對象啟用 Blueprint 的參考架構" style="width:90%; border:1px solid #4a4a4a" />

<br>

## 實施步驟以Audience Manager

* 有關實施Audience Manager的詳細資訊，請參閱以下 [文檔](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html?lang=zh-Hant)。

## Real-time Customer Data Platform實施步驟

* Real-time Customer Data Platform的執行步驟見 [文檔](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/known-customer-audience-activation/known.html)。

## 相關文件

* [Audience Manager](https://experienceleague.adobe.com/docs/audience-manager.html?lang=zh-Hant)
* [Experience Cloud [!UICONTROL 受眾]](https://experienceleague.adobe.com/docs/core-services/interface/audiences/audience-library.html?lang=zh-Hant)
* [整合 Audience Manager 與 Target](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-other-solutions/aam-target-integration.html?lang=zh-Hant)
* [透過 Audience Manager 分享 Adobe Analytics 區段](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html?lang=zh-Hant)
* [已知客戶激活藍圖](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/known-customer-audience-activation/known.html)。
* [即時客戶資料平台](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/overview.html)
