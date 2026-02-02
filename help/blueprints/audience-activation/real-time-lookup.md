---
title: 適用於Web和Mobile Personalization的即時Edge設定檔存取
description: 在邊緣[!UICONTROL 即時客戶個人檔案]存取權，以提供即時網頁和行動個人化的內容。
solution: Real-Time Customer Data Platform, Data Collection
kt: 719
source-git-commit: 2fad3a8a9210d703130f251b0bd7cc4c0b7cbd32
workflow-type: tm+mt
source-wordcount: '1544'
ht-degree: 6%

---

# 適用於Web和Mobile Personalization的即時Edge設定檔存取

適用於Web和Mobile Personalization藍圖的即時Edge設定檔存取顯示，Web和行動應用程式如何在Edge存取Adobe Experience Platform的[!UICONTROL 即時客戶設定檔]，以進行高輸送量、低延遲的個人化。

應用程式能以毫秒的延遲存取即時設定檔屬性和邊緣的對象。 在設定檔中儲存屬性、對象會籍和模型導向功能（作為屬性），可跨網頁和行動裝置頻道即時存取以進行相同頁面和下一頁個人化。

透過此功能，您可以根據即時客戶個人檔案，在您的網站和行動應用程式上提供高度個人化的體驗，包括從即時行為、擷取到即時客戶個人檔案中的屬性以及計算的深入分析衍生的受眾。

>[!NOTE]
>
>Edge設定檔存取專門針對高輸送量、低延遲的使用案例，例如網頁/行動傳入個人化和即時優惠決定。 若為低輸送量的案例（例如代理商協助支援或銷售互動），則中心設定檔查詢API較為合適。 檢視[支援和銷售案例的即時設定檔存取](customer-activity.md)，以取得中心設定檔存取權。

## 應用程式

* Real-time Customer Data Platform
* Adobe Experience Platform資料收集(網頁SDK /行動SDK)
* Edge Network伺服器API

## 使用案例

* 針對已知客戶體驗在網頁和行動裝置頻道上即時個人化
* 根據即時設定檔屬性和對象的相同頁面和下一頁個人化
* 根據客戶個人檔案（包括即時行為資料、屬性和計算的深入分析）進行內容和選件個人化
* 與個人化引擎、內容管理系統及外部應用程式整合，用於即時決策
* 使用即時設定檔內容進行測試和內容最佳化

## 先決條件

如果您想要使用串流資料即時更新設定檔，此Blueprint需要使用下列其中一個資料收集方法。 您可以即時存取Edge設定檔，而不需要直接將資料收集到Edge設定檔；資料可以收集到集線器並投影到Edge設定檔。 請注意，收集到集線器然後預計到Edge的資料會增加延遲。

* 如果您想要從網站收集資料，請使用[Adobe Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/home.html?lang=zh-Hant)。
* 如果您想要從行動應用程式收集資料，請使用[Adobe Experience Platform Mobile SDK](https://developer.adobe.com/client-sdks/home/)。
* 如果您未使用Web SDK或Mobile SDK，或正在實作更直接的伺服器對伺服器連線，請使用[Edge Network伺服器API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=zh-Hant)。

>[!IMPORTANT]
>
>在實作Edge個人化之前，請閱讀如何[啟用邊緣個人化目的地的對象資料](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations)的指南。 本指南會針對跨多個Experience Platform元件的相同頁面和下一頁個人化使用案例，引導您進行所需設定步驟。

## 架構圖

<img src="assets/real-time-edge-lookup.svg" alt="適用於Web和Mobile Personalization的Edge設定檔存取參考架構" style="width:90%; border:1px solid #4a4a4a"  class="modal-image" />

## 護欄

* [[!UICONTROL 即時客戶個人資料]的護欄](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hant)
* [Edge Network護欄](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/guardrails.html)
* Edge設定檔具有14天的存留時間(TTL)。 如果使用者未在Edge上活動14天，Edge設定檔可能會過期，且需要從中心擷取，這可能會影響第一頁個人化。
* Edge個人化支援對符合邊緣細分條件的對象進行即時對象成員資格評估。 透過適當的設定，也可從邊緣取得批次和來自集線器的串流對象。

## 實作模式

Edge個人化可使用Real-time Customer Data Platform中的[自訂Personalization連線](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/catalog/personalization/custom-personalization)目的地實作。 根據您的使用案例，此目的地支援多種資料收集方法。

### 模式1：使用Web SDK / Mobile SDK以對象成員資格為基礎的個人化

* 使用Adobe Experience Platform Web SDK或Mobile SDK搭配Edge Network進行受眾成員資格型個人化。
* 此方法可根據對象成員資格為邊緣個人化提供低延遲和最佳效能。
* 即時邊緣劃分需要網頁/行動SDK實作。
* Web SDK和Mobile SDK **僅支援以對象成員資格為基礎的個人化**。
* [請參閱Experience Platform網頁和行動SDK藍圖](../experience-platform/deployment/websdk.md)，以瞭解SDK型實作。
* 對於行動SDK實作，[Adobe Journey Optimizer - Decisioning擴充功能](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/)必須安裝在行動SDK中。

### 模式2：使用Edge Network伺服器API的屬性型個人化（設定檔屬性的必要專案）

>[!IMPORTANT]
>
>**以屬性為基礎的個人化需求：**&#x200B;如果您想要根據設定檔屬性（而不只是對象成員資格）進行個人化，您&#x200B;**必須**&#x200B;使用[Edge Network Server API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=zh-Hant)搭配已驗證的伺服器端整合，無論您是否也在使用Web SDK或Mobile SDK進行資料收集。

* 啟用與協力廠商個人化引擎和CDN型個人化的整合。
* **需要Edge Network伺服器API**，才能安全地擷取個人化的設定檔屬性。
* 您可以新增伺服器端整合，運用您已在網頁或行動SDK實作中使用的相同資料流，透過Edge Network伺服器API擷取設定檔屬性。
* 所有設定檔屬性的Edge Network伺服器API呼叫，都必須在已驗證的內容中進行，才能保護敏感資料。
* 此模式會啟用以對象成員資格為基礎的個人化及以屬性為基礎的個人化。
* 適用於伺服器端個人化使用案例、API型整合以及需要設定檔屬性存取權的案例。

## 實施步驟

1. 為要擷取的資料[建立資料方案](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm&lang=zh-Hant)。
1. 為要擷取的資料[建立資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=zh-Hant)。
1. [在結構描述上設定正確的身分識別與身分識別名稱空間](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hant)，以確保擷取的資料可以拼接到統一的設定檔中。
1. [為個人資料啟用方案和資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=zh-Hant)。
1. [擷取資料](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&lang=zh-Hant)到 Experience Platform。
1. [設定合併原則](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=zh-Hant)以確保正確的身分拼接和設定檔合併。
1. [在Experience Platform資料收集中設定資料串流](https://experienceleague.adobe.com/docs/experience-platform/datastreams/configure.html?lang=zh-Hant)，並啟用目的地設定。 資料串流會決定要將對象包含在頁面的回應中的資料收集資料串流。
1. 在Web和行動屬性上實作[Adobe Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/home.html?lang=zh-Hant)或[Mobile SDK](https://developer.adobe.com/client-sdks/home/)以進行資料收集。
1. 為需要即時評估的對象設定邊緣細分。 [Edge細分檔案](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/edge-segmentation.html?lang=zh-Hant)。
1. 在目的地目錄中，設定[自訂Personalization連線](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/catalog/personalization/custom-personalization)目的地：
1. [啟用邊緣個人化目的地的對象](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations)。 選取您要對目的地啟用的對象。
1. （基於屬性的個人化選用專案）如果您除了受眾成員資格之外，還需要根據設定檔屬性進行個人化，請使用相同資料流實作[Edge Network Server API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=zh-Hant)與已驗證的伺服器端整合。 這是&#x200B;**存取設定檔屬性的必要**。
1. 在網頁/行動應用程式中實作個人化邏輯，以使用匯出的受眾資料和設定檔屬性：
   * 如果使用Adobe Experience Platform中的標籤，請使用[傳送事件完成功能](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=zh-Hant)來存取具有匯出資料的`event.destinations`變數。
   * 如果未使用標籤，請使用[命令回應](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/commands/command-responses.html?lang=zh-Hant)來剖析來自Adobe Experience Platform的JSON回應，並擷取對象ID和設定檔屬性。

## 實施考量

### 身分注意事項

* 透過Edge Network使用Web SDK或Mobile SDK時，任何主要身分均可用於邊緣個人化。
* 對於使用已知客戶資料首次登入個人化，個人化請求必須使用符合Real-time Customer Data Platform中已知客戶身分的主要身分。 如果主要ID設為ECID或尚未與已知客戶設定檔拼接的匿名身分，則需要時間才能實現身分拼接，這可能會影響個人化歷史設定檔資料的可用性。
* Edge設定檔必須先初始化，才能用於個人化。 邊緣設定檔已過期（14天TTL）的首次訪客或回訪訪客可能會根據有限的設定檔資料體驗初始個人化，直到邊緣設定檔完全填入為止。

### 屬性型個人化

>[!IMPORTANT]
>
>設定檔屬性可能包含敏感資料。 為了保護此資料，在設定以屬性為基礎的個人化的自訂Edge Network目的地時，您&#x200B;**必須**&#x200B;使用[Personalization伺服器API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=zh-Hant)。 所有Edge Network伺服器API呼叫都必須在已驗證的內容中進行。

* 針對使用設定檔屬性的屬性型個人化，您必須新增與Edge Network伺服器API的伺服器端整合，利用您用於網頁或行動SDK實施的相同資料流。
* 您必須透過自訂Personalization連線目的地設定，設定要包含在邊緣投影中的設定檔屬性。
* **僅網頁SDK和行動SDK僅支援根據對象成員資格進行個人化**。 **需要Edge Network伺服器API**，才能安全地擷取個人化的設定檔屬性。
* 如果您未實施Edge Network伺服器API來存取屬性，個人化將僅以對象成員資格為基礎。
* 具有屬性的自訂Personalization的API回應，除了受眾區段外還包含`attributes`區段。

### 對象考量事項

* 透過中心上的串流或批次細分評估的對象會投影到邊緣，並可用於個人化。
* 符合邊緣劃分條件的對象會在邊緣即時評估相同頁面個人化的對象。
* 根據受眾在即時個人化使用案例中的使用情況，設定適當的受眾以供邊緣評估。

## 相關文件

### 目的地設定

* [自訂Personalization連線](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/catalog/personalization/custom-personalization) — 主要實作指南
* [Personalization目的地概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/catalog/personalization/overview)
* [啟用對象以邊緣個人化目的地](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations)
* [即時查詢邊緣上的設定檔屬性](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/ui/activate/activate-edge-profile-lookup)

### SDK 檔案

* [Experience Platform Web SDK 文件](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/home.html?lang=zh-Hant)
* [Experience Platform Mobile SDK 文件](https://developer.adobe.com/client-sdks/home/)
* [Edge Network伺服器API檔案](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=zh-Hant)
* [Experience Platform Tags 文件](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=zh-Hant)
* 網頁SDK中的[命令回應](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/commands/command-responses.html?lang=zh-Hant)

### 設定檔和分段檔案

* [[!UICONTROL 即時客戶個人資料]文件](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html?lang=zh-Hant)
* [個人資料護欄](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hant)

### 教學課程

* [使用 Real-Time CDP 和 Adobe Target 進行下次點擊個人化](https://experienceleague.adobe.com/docs/platform-learn/tutorials/experience-cloud/next-hit-personalization.html?lang=zh-Hant)
* [資料流組態](https://experienceleague.adobe.com/docs/experience-platform/datastreams/configure.html?lang=zh-Hant)
