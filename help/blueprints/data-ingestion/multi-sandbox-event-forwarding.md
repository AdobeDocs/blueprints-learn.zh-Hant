---
title: 多沙箱事件轉送資料收集
description: 瞭解如何將使用Experience PlatformWeb和Mobile SDK收集的資料設定為收集單一事件並轉送至多個Experience Platform沙箱。
solution: Data Collection
kt: 7202
exl-id: ecc94fc8-9fad-4b88-a153-3d0fc00d8d58
source-git-commit: 3d6a2416cdb9956e59be4b2918ba19f88cd2150b
workflow-type: tm+mt
source-wordcount: '793'
ht-degree: 0%

---

# 多沙箱事件轉送資料收集

此藍圖顯示如何將使用Experience Platform Web和Mobile SDK收集的資料設定為收集單一事件並轉送至多個AEP沙箱。 此Blueprint專用於以下用途的多沙箱資料收集： [!UICONTROL 事件轉送] 以達成此目標。

除了透過複製事件之外 [!UICONTROL 事件轉送] 功能，您可以新增、篩選或操控原始收集資料，以符合其他沙箱的需求。

[!UICONTROL 事件轉送] 使用單獨屬性，包含 [!UICONTROL 資料元素]， [!UICONTROL 規則]、和 [!UICONTROL 擴充功能] 您的資料需求所需。 傳入事件時，您的 [!UICONTROL 事件轉送] 屬性可收集資料，並在轉送前視需要管理。

您的目的地沙箱需要設定的HTTP串流端點供Adobe使用 [!UICONTROL 雲端聯結器] 副檔名。

## 使用案例

* 全域資料報告 — 使用多個沙箱來隔離作業環境時，以及需要將資料收集整合到一個沙箱以進行跨沙箱報告時。 路由體驗邊緣事件，透過 [!UICONTROL 事件轉送] 至報告沙箱，可讓每個沙箱作業環境將即時收集的資料傳送至報告沙箱。

* 根據每個沙箱作業環境的不同資料規則，管理沙箱之間的資料收集。

## 應用程式

* [!DNL Experience Platform] 資料彙集
* [!UICONTROL 事件轉送]
* AEP [!UICONTROL 副檔名]
* [!UICONTROL Cloud Connector擴充功能]

## 考量事項

替換為 [!UICONTROL 事件轉送] 作為將資料傳送至多個沙箱的方法，在您的解決方案架構中必須考慮一些注意事項。

### 無HIPAA資料

[!UICONTROL 事件轉送] 系統不會將HIPAA視為「就緒」，且不應在收集HIPAA資料的任何HIPAA使用案例中使用。 然而，用於下列專案的基礎架構： [!UICONTROL 事件轉送] 被視為HIPAA就緒，完全由客戶自行決定。 當您的 [!UICONTROL 事件轉送] Tag屬性位於 [!UICONTROL 事件轉送] 系統時，收集到的整個資料裝載都會傳送至 [!UICONTROL 事件轉送] 處理系統。 正是這個程式使得 [!UICONTROL 事件轉送] 關於HIPAA使用案例。 整個裝載已傳送至 [!UICONTROL 事件轉送] 系統，這會包含任何HIPAA值。 即使 [!UICONTROL 事件轉送] 規則會在傳送資料至目的地之前篩選該資料，如此一來HIPAA資料仍會傳送至不符合HIPAA要求的基礎結構。 不過，裝載資料絕不會儲存，僅是直接通過。

### 不同的資料串流和串流端點

當資料流經資料流時，從 [!UICONTROL Platform Edge Network]，使用時 [!UICONTROL 事件轉送] 對於另一個AEP沙箱，永遠必須使用與製作原始集合的資料流相同的資料流或串流端點。 這可能會對AEP執行個體造成傷害，並可能觸發DoS情況。

### 預估流量

每個使用案例都需要檢閱流量。 這很重要，因為高容量可能會導致節流情況，如果發生這種情況，客戶會收到通知。

## 架構

![多沙箱 [!UICONTROL 事件轉送]](assets/multi-sandbox-data-collection.png)

1. 收集事件資料並傳送至 [!UICONTROL Platform Edge Network] 需要，才能使用 [!UICONTROL 事件轉送]. 客戶可以使用使用者端的Adobe標籤或 [!UICONTROL Platform Edge Network伺服器API] 用於伺服器對伺服器資料收集。 此 [!UICONTROL Platform Edge Network API] 可提供伺服器對伺服器的收集功能。 但是，這確實需要不同的程式設計模型才能實作。 請參閱 [Edge Network伺服器API總覽](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=en).

1. 收集到的裝載會從標籤實作傳送至 [!UICONTROL Platform Edge Network] 至 [!UICONTROL 事件轉送] 服務並由其本身處理 [!UICONTROL 資料元素]， [!UICONTROL 規則] 和 [!UICONTROL 動作]. 您可深入瞭解以下專案的差異： [標籤和 [!UICONTROL 事件轉送]](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=en#differences-from-tags).

1. 一個 [!UICONTROL 事件轉送] 屬性也需要用來接收從收集到的事件資料 [!UICONTROL Platform Edge Network]. 該事件資料是由部署的標籤實作還是伺服器對伺服器集合傳送至Platform Edge Network。 作者會定義資料元素、規則和動作，以在轉送至第二個沙箱之前擴充事件資料。 考慮使用自訂程式碼 [!DNL JavaScript] 資料元素來協助您建構資料以供沙箱擷取。 結合Platform資料準備功能，您有幾個選項可管理您的資料結構。

1. 目前，Adobe的使用 [!UICONTROL Cloud Connector擴充功能] 內需要 [!UICONTROL 事件轉送] 屬性。 一旦規則處理或擴充了事件資料，便會在為將裝載傳送至第二個沙箱的POST設定的擷取呼叫中使用Cloud Connector

1. 第二個沙箱需要資料擷取的串流端點。 您也可以考慮AEP中的資料準備功能，以協助擷取和對應 [!UICONTROL 事件轉送] 裝載至XDM。 請參閱AEP檔案建立 [使用UI的HTTP API串流連線](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/streaming/http.html?lang=zh-Hant)
