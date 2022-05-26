---
title: 多沙盒事件轉發資料收集藍圖
description: 使用事件轉發將SDKExperience Platform到多個沙箱來將收集的資料流
solution: Data Collection
kt: 7202
source-git-commit: 8ea7041103f86f034740f00a607ae36ca0b358cf
workflow-type: tm+mt
source-wordcount: '608'
ht-degree: 12%

---

# 多沙盒事件轉發資料收集藍圖

多沙盒事件轉發資料收集藍圖顯示了如何配置使用Adobe Experience PlatformWeb和移動SDK收集的資料以收集單個事件並轉發到多個AEP沙盒。 此藍圖是使用「Adobe」標籤的「事件轉發」功能的特定用例。

除了使用「事件轉發」功能複製事件外，您還可以添加、過濾或處理符合其他沙箱要求的原始收集資料。 例如，沙盒A需要接收所有事件資料元素，沙盒B應僅接收非PII資料。

事件轉發使用單獨的標籤屬性，該屬性包含滿足資料要求所必需的資料元素、規則和擴展。 在傳入事件時，您的事件轉發屬性可以收集資料並根據需要進行管理，然後再轉發。

目標sadnbox需要配置HTTP流終結點，該終結點將由事件轉發HTTPS擴展使用。



## 使用案例

* 全局資料報告 — 使用多個沙箱隔離操作環境時，需要將資料收集整合到一個沙箱以進行跨沙箱報告。 事件轉發到報告沙盒允許每個沙盒操作環境在將資料即時收集到報告沙盒時發送資料
* 根據每個沙箱操作環境的不同資料規則跨沙箱管理資料收集。 需要篩選敏感資料（如醫療保健和金融服務）的此類操作環境

## 應用程式

* Adobe Experience Platform 集合

## 架構

<img src="assets/multi-Sandbox-Data-Collection.svg" alt="多沙盒事件轉發的參考體系結構" style="width:90%; border:1px solid #4a4a4a" />

1. 標籤作者既定義了標籤屬性，也定義了事件轉發屬性。 在此，作者將定義管理資料收集的資料元素、規則和操作。 請記住，標籤屬性代碼在客戶端上運行，並由CDN主機分發。 事件轉發屬性代碼在Adobe Edge伺服器上運行。

1. 在客戶端上收集的資料會發送到邊緣伺服器。 客戶還可以選擇先將資料發送到自己的伺服器作為伺服器端收集的方法。
WebSDK可以提供伺服器到伺服器的收集功能。 但是，這確實需要一種不同的寫程式模型來實現。 請參閱文檔 **邊緣網路伺服器API概述** 下

1. Platform Edge Server接收資料收集負載並協調資料到所需系統（如Target和Analytics）的流。

1. 事件轉發屬性資料元素用於訪問負載中到達的事件資料。 在轉發之前，還可以使用規則根據需要操縱事件資料。 例如，將資料格式化為流資料接收所需的XDM

1. 事件轉發提供HTTPS擴展，該擴展提供將事件資料轉發到HTTPS端點的功能。

1. 沙盒2配置了接收轉發事件的流端點。

## 相關文件

* [事件轉發文檔](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html)
* [事件轉發視頻](https://experienceleague.adobe.com/docs/launch-learn/tutorials/server-side/overview.html?lang=zh-Hant)
* [事件轉發課](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/event-forwarding/setup-event-forwarding.html) Web SDK教程
* [Experience PlatformWebSDK概述](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html?lang=zh-Hant)
* [邊緣網路伺服器API概述](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html)

## 相關部落格貼文

* [[!DNL Boosting Website Performance with Adobe Experience Platform Web SDK and Edge Network]](https://medium.com/adobetech/boosting-website-performance-with-adobe-experience-platform-web-sdk-and-edge-network-329fcf70fdf9)
* [[!DNL Solving Implementation Pain Points with Adobe Experience Platform Web SDK and Edge Network]](https://medium.com/adobetech/solving-implementation-pain-points-with-adobe-experience-platform-web-sdk-and-edge-network-880b635e6819)
* [[!DNL Adobe Experience Platform Web SDK for Audience Management]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
* [[!DNL Adobe Experience Platform Web SDK — Adobe Target]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-adobe-target-9b9f621d271)
* [[!DNL Adobe Experience Platform Web SDK Migration Scenarios for Adobe Analytics]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-migration-scenarios-for-adobe-analytics-91c255ec82b0)
* [[!DNL Unify Your Adobe Experience Platform Services with Adobe Experience Platform Web SDK]](https://medium.com/adobetech/unify-your-adobe-experience-platform-services-with-adobe-experience-platform-web-sdk-75cf6851a9fc)
* [[!DNL Accelerate Your Mobile Application Development with Adobe Experience Platform Mobile SDK and Launch]](https://medium.com/adobetech/accelerate-your-mobile-application-development-with-adobe-experience-platform-mobile-sdk-and-launch-ed023536d611)
* [[!DNL Simplifying Customer Workflows with Adobe Experience Platform Web SDK]](https://medium.com/adobetech/simplifying-customer-workflows-with-adobe-experience-platform-web-sdk-4e54fe134f4a)
