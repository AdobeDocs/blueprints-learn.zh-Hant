---
title: 多沙箱事件轉送資料收集
description: 瞭解如何將使用Experience PlatformWeb和Mobile SDK收集的資料設定為收集單一事件並轉送至多個Experience Platform沙箱。
solution: Data Collection
kt: 7202
exl-id: ecc94fc8-9fad-4b88-a153-3d0fc00d8d58
source-git-commit: 72eb4e2ff276279a2fc88ead0b17d77cc8e99b97
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 0%

---

# 多沙箱事件轉送資料收集

此藍圖顯示如何將使用[!DNL Experience Platform]個Web和Mobile SDK收集的資料設定為收集單一事件並轉送至多個AEP沙箱。 此Blueprint專屬於使用[!UICONTROL 事件轉送]來達成此目標的多沙箱資料收集。

除了使用[!UICONTROL 事件轉送]功能來復寫事件之外，您也可以新增、篩選或操作原始收集資料，以符合其他沙箱的需求。

[!UICONTROL 事件轉送]使用單獨的屬性，其中包含資料需求所需的[!UICONTROL 資料元素]、[!UICONTROL 規則]和[!UICONTROL 延伸模組]。 有了傳入事件，您的[!UICONTROL 事件轉送]屬性便可以收集資料，並在轉送前視需要加以管理。

您的目的地沙箱需要已設定的HTTP串流端點，以供Adobe[!UICONTROL 雲端聯結器]擴充功能使用。

## 使用案例

* 全域資料報告 — 使用多個沙箱來隔離作業環境時，以及需要將資料收集整合到一個沙箱以進行跨沙箱報告時。 透過[!UICONTROL 事件轉送]將Experience Edge事件傳送至報告沙箱，讓每個沙箱作業環境可以將即時收集的資料傳送至報告沙箱。

* 根據每個沙箱作業環境的不同資料規則，管理沙箱之間的資料收集。

## 應用程式

* [!DNL Experience Platform]個資料集合
* [!UICONTROL 事件轉送]
* AEP [!UICONTROL 延伸模組]
* [!UICONTROL 雲端聯結器延伸模組]

## 考量事項

以[!UICONTROL 事件轉送]作為將資料傳送到多個沙箱的方法，您的解決方案架構中必須考量一些事項。

### 無HIPAA資料

[!UICONTROL 事件轉送]不視為HIPAA就緒，且不應用於收集HIPAA資料的任何HIPAA使用案例。

不過，用於[!UICONTROL 事件轉送]的基礎結構會視為HIPAA就緒，完全由客戶自行決定。 當您的[!UICONTROL 事件轉送]標籤屬性位於[!UICONTROL 事件轉送]系統時，收集的整個資料裝載都會傳送到[!UICONTROL 事件轉送]系統以進行處理。 此程式會針對HIPAA使用案例進行[!UICONTROL 事件轉送]的考慮。 整個裝載已送出[!UICONTROL 事件轉送]系統時，此程式將包含任何HIPAA值。 即使[!UICONTROL 事件轉送]規則在傳送資料到目的地之前篩選該資料，該HIPAA資料仍會傳送至不符合HIPAA要求的基礎結構。 不過，裝載資料絕不會儲存，且只是傳遞。

### 不同的資料串流和串流端點

當資料從[!DNL Platform Edge Network]流經資料串流時，使用[!UICONTROL 事件轉送]到另一個AEP沙箱時，要求永遠不要使用與製作原始集合的資料串流相同的資料串流或串流端點。 這可能會對AEP執行個體造成傷害，並可能觸發DoS情況。

### 預估流量

每個使用案例都需要檢閱流量。 這很重要，因為高容量可能會導致節流情況，如果發生這種情況，客戶會收到通知。

## 架構

![多沙箱[!UICONTROL 事件轉送]](assets/multi-sandbox-data-collection.png)

1. 必須收集事件資料並傳送至[!DNL Platform Edge Network]，才能使用[!UICONTROL 事件轉送]。 您可以為使用者端使用Adobe標籤，或為伺服器對伺服器資料收集使用[!DNL Platform Edge Network Server API]。

   [!DNL Platform Edge Network API]可提供伺服器對伺服器的集合功能。 但是，這需要不同的程式設計模型才能實作。 請參閱[Edge Network伺服器API總覽](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=en)。

1. 收集的裝載會從標籤實作傳送到[!DNL Platform Edge Network]到[!UICONTROL 事件轉送]服務，並由其自己的[!UICONTROL 資料元素]、[!UICONTROL 規則]和[!UICONTROL 動作]處理。 若要深入瞭解差異，請參閱[標籤和[!UICONTROL 事件轉送]](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=en#differences-from-tags)。

1. 還需要有[!UICONTROL 事件轉送]屬性，才能從[!DNL Platform Edge Network]接收收集到的事件資料，無論該事件資料是由已部署的Tags實作或伺服器對伺服器集合傳送到[!DNL Platform Edge Network]。

   作者會定義資料元素、規則和動作，以在轉送至第二個沙箱之前擴充事件資料。 請考慮使用自訂程式碼[!DNL JavaScript]資料元素來協助建構您的資料以利沙箱擷取。 結合Platform資料準備功能，您有幾個選項可管理您的資料結構。

1. 目前，[!UICONTROL Event Forwarding]屬性中需要使用Adobe[!UICONTROL 雲端聯結器擴充功能]。 在規則處理或擴充事件資料後，[!UICONTROL 雲端聯結器]用於為POST設定的擷取呼叫中，將裝載傳送至第二個沙箱。

1. 第二個沙箱需要資料擷取的串流端點。 您也可以考慮AEP中的[!UICONTROL 資料準備]功能，協助將[!UICONTROL 事件轉送]裝載擷取並對應至XDM。 請參閱AEP檔案使用UI建立[HTTP API串流連線](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/streaming/http.html?lang=zh-Hant)
