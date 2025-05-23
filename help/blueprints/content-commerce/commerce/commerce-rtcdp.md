---
title: Adobe Commerce - RTCDP Blueprint
description: Adobe Experience Platform與Adobe Commerce整合，以建立客戶的單一檢視，並在數位店面和各管道間聰明地打造個人化體驗。
solution: Real-Time Customer Data Platform, Commerce
exl-id: e2fc5e1c-c865-4c24-9b82-861a34aba487
source-git-commit: 80a4716a7ed64ec30b9c60b3444affc5bd8984e4
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 1%

---

# Adobe Commerce與RTCDP

[!DNL Data Connection]擴充功能可協助Adobe Commerce客戶順暢地與Adobe Experience Platform整合，以豐富客戶設定檔並個人化數位店面和其他管道中的體驗。

## 已啟用技術功能

* 收集並傳送到任何Adobe Experience Cloud產品的店面資料（使用者端，例如加入購物車、放棄購物車等）。
* 任何Adobe Experience Cloud產品的後台訂單狀態
* 可將後台歷史訂單傳送至Adobe Experience Platform
* 在Adobe Commerce共用及個人化RTCDP對象

## 先決條件

若要使用[!DNL Data Connection]擴充功能，您必須具備下列條件：

* Adobe Commerce 2.4.4或更新版本
* Adobe ID和組織ID
* Adobe Experience Platform/RTCDP
* [Adobe使用者端資料層(ACDL)](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/client-data-layer/overview.html?lang=zh-Hant)。 需要ACDL才能收集店面事件資料。

## 入門步驟

### 從Adobe Commerce到Adobe Experience Platform的資料收集

* [安裝](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/fundamentals/install.html?lang=zh-Hant) [!DNL Data Connection]延伸模組。
* [登入](https://helpx.adobe.com/tw/manage-account/using/access-adobe-id-account.html)您的Adobe帳戶並檢視以確認您的組織ID。 組織ID是與已布建Experience Cloud公司相關聯的ID。 此ID是24個字元的英數字串，後面接著（而且必須包含） @AdobeOrg。
* [建立或更新](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/fundamentals/update-xdm.html?lang=zh-Hant)具有Commerce特定欄位群組的XDM結構描述。
* [根據您建立或更新的結構描述建立資料集](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html?lang=zh-Hant#create-a-dataset)。 此資料集將包含您傳送的Commerce資料。
* [建立資料流](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=zh-Hant)並選取包含Commerce特定欄位群組的XDM結構描述。
* [連線到Commerce服務](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html?lang=zh-Hant)。
* [連線到Adobe Experience Platform](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/fundamentals/connect-data.html?lang=zh-Hant)。

### 從Adobe Experience Platform連線至Commerce目的地以共用對象

若要連線至Adobe Commerce目的地：

* 在[Adobe Experience Platform介面](https://experience.adobe.com/platform/)中，前往「目的地>目錄」。
* 選取「Personalization」。
* 選取Adobe Commerce目標以反白顯示，然後選取「設定」。
* 請依照[目的地組態教學課程](https://experienceleague.adobe.com/docs/experience-platform/destinations/ui/connect-destination.html?lang=zh-Hant)中所述的步驟進行。

## 現成可用的資料

* 店面（瀏覽器/應用程式）活動
* 後台活動
* 歷史訂單資料

如需支援事件的完整清單，請參閱[Commerce事件](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/event-forwarding/events.html?lang=zh-Hant)

## 架構

<img src="../commerce/assets/commerce_rtcdp.png" alt="Adobe Commerce RTCDP架構" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## 相關實作指南

| 指南 | 連結 |
|:----|:----|
| 平台聯結器 | [Adobe CommerceExperience Platform聯結器總覽](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/overview.html?lang=zh-Hant) |
| Commerce目的地 | RTCDP中的[Adobe Commerce連線](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-commerce.html?lang=zh-Hant) |
| Edge Personalization | [啟用對象以邊緣個人化目的地](https://experienceleague.adobe.com/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations.html?lang=zh-Hant) |
