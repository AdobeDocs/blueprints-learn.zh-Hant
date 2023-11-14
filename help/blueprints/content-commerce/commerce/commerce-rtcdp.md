---
title: Adobe Commerce - RTCDP Blueprint
description: Adobe Experience Platform與Adobe Commerce整合，以建立客戶的單一檢視，並在數位店面和各管道間聰明地打造個人化體驗。
solution: Real-Time Customer Data Platform, Commerce
source-git-commit: abb946358ceeee1af427c5b362ed2f48f733a6c9
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# Adobe Commerce與RTCDP

此整合式體驗可協助Adobe Commerce客戶順暢地與Adobe Experience Platform整合，以豐富客戶設定檔並在數位店面和其他頻道中個人化體驗。

## 已啟用技術功能

* 收集和傳送到任何Adobe Experience Cloud產品的店面資料（使用者端）。 （加入購物車、放棄購物車等）
* 任何Adobe Experience Cloud產品的後台訂單狀態
* 可將後台歷史訂單傳送至Adobe Experience Platform
* 在Adobe Commerce共用及個人化RTCDP對象

## 先決條件

若要使用Experience Platform聯結器，您必須具備下列專案：

* Adobe Commerce 2.4.4或更新版本
* Adobe ID和組織ID
* Adobe Experience Platform/RTCDP
* [Adobe使用者端資料層(ACDL)](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/client-data-layer/overview.html?lang=en). 需要ACDL才能收集店面事件資料。

## 入門步驟

### 從Adobe Commerce到Adobe Experience Platform的資料收集

* [安裝](https://experienceleague.adobe.com/docs/commerce-merchant-services/experience-platform-connector/fundamentals/install.html?lang=en) Experience Platform聯結器擴充功能。
* [登入](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) 至您的Adobe帳戶並檢視，以確認您的組織ID。 組織ID是與已布建Experience Cloud公司相關聯的ID。 此ID是24個字元的英數字串，後面接著（而且必須包含） @AdobeOrg。
* [建立或更新](https://experienceleague.adobe.com/docs/commerce-merchant-services/experience-platform-connector/fundamentals/update-xdm.html?lang=en) 您的XDM結構描述和商務特定欄位群組。
* [建立資料集](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html?lang=en#create-a-dataset) 根據您建立或更新的結構描述。 此資料集將包含您傳送的Commerce資料。
* [建立資料串流](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en) 並選取包含商務特定欄位群組的XDM結構描述。
* [連線至Commerce Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html?lang=en).
* [連線至Adobe Experience Platform](https://experienceleague.adobe.com/docs/commerce-merchant-services/experience-platform-connector/fundamentals/connect-data.html?lang=en).

### 從Adobe Experience Platform連線至Commerce目的地以共用對象

若要連線至Adobe Commerce目的地：

* 在 [Adobe Experience Platform介面](https://experience.adobe.com/platform/)，前往目的地>目錄。
* 選取「個人化」。
* 選取Adobe Commerce目標以反白顯示，然後選取「設定」。
* 請依照中所述的步驟操作。 [目的地設定教學課程](https://experienceleague.adobe.com/docs/experience-platform/destinations/ui/connect-destination.html?lang=en).

## 現成可用的資料

* 店面（瀏覽器/應用程式）活動
* 後台活動
* 歷史訂單資料

如需支援事件的完整清單，請參閱 [商務事件](https://experienceleague.adobe.com/docs/commerce-merchant-services/experience-platform-connector/event-forwarding/events.html?lang=en)

## 架構

<img src="../commerce/assets/commerce_rtcdp.png" alt="Adobe Commerce RTCDP架構" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## 相關實作指南

| 指南  | 連結 |
|:----|:----|
| 平台聯結器 | [Adobe CommerceExperience Platform聯結器總覽](https://experienceleague.adobe.com/docs/commerce-merchant-services/experience-platform-connector/overview.html?lang=en) |
| 商務目的地 | [RTCDP中的Adobe Commerce連線](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-commerce.html?lang=en) |
| 邊緣個人化 | [啟用對象以邊緣個人化目的地](https://experienceleague.adobe.com/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations.html?lang=en) | |
