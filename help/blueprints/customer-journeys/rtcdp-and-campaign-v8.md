---
title: Real-Time CDP與Adobe Campaign v8整合模式
description: 展示Adobe Experience Platform及其即時客戶個人檔案和集中化細分工具如何與Adobe Campaign v8搭配使用，以提供個人化的對話。
solution: Real-Time Customer Data Platform, Campaign
exl-id: d0291088-02ed-4e7e-b538-018ea40e38c6
source-git-commit: 8355a36a235d847a6faf2398f3fadbed28ccac37
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 21%

---

# Real-Time CDP與Adobe Campaign v8整合模式

展示 Adobe Experience Platform 及其即時客戶設定檔和集中式細分工具如何與 Adobe Campaign 一起使用，以提供個人化的對話體驗。

<br>

## 應用程式

* Adobe Experience PlatformReal-Time CDP
* Adobe Campaign v8

<br>

## 架構

<img src="assets/rtcdp-campaignv8-architecture.svg" alt="批次傳訊和Adobe Experience Platform整合模式的參考架構" style="width:100%; border:1px solid #4a4a4a" />

<br>

## 先決條件

* 必須使用有效的 IMS Org，才能為 Experience Cloud 佈建客戶
* Adobe Experience Platform和Campaign建議在相同的IMS組織中布建，以取得單一登入URL
* 客戶必須布建Campaign的V8執行個體
* 客戶必須符合資格且擁有RTCDP、Sources、Destinations的存取權。
* Adobe Campaign產品內容必須存在

<br>

## 實作步驟

請參閱下列檔案，了解如何將Campaign v8來源連接器設定為Adobe Experience Platform，以及將Real-time Customer Data Platform目的地連接器設定為Campaign v8。
[Campaign與AEP連接器](https://experienceleague.adobe.com/docs/campaign/campaign-v8/connect/ac-aep.html?lang=en)

## 護欄

### Adobe Campaign

* 請參閱Campaign來源連接器檔案 —  [促銷活動來源連接器](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/adobe-applications/campaign.html?lang=en)
* 僅支援Adobe Campaign單一組織單位部署
* Adobe Campaign 是所有啟用的個人資料之真相來源，代表著個人資料必須存在於 Adobe Campaign 中，且不應基於 Experience Platform 區段建立新的個人資料。


### Experience PlatformReal-time Customer Data Platform區段共用

* 請參閱RTCDP Campaign Destination連接器 —  [RTCDP Campaign連線](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign-managed-services.html)
* 建議50個區段限額
* 請注意，批次（每天1次）和串流（約5分鐘）及根據區段評估排程，AEP的區段成員資格實現都會延遲。
* 啟動延遲最少3小時
* 僅聯合結構屬性可用於激活（不支援陣列/地圖/體驗事件）
* 建議每個區段最多20個屬性
* 具有「已實現」區段成員資格的所有設定檔的每個區段有一個檔案，或如果區段成員資格已新增為檔案中「已實現」和「已退出」設定檔的屬性
* 支援增量和完整區段匯出
* 不支援檔案加密
* 請參閱AEP的設定檔和資料擷取護欄 —  [連結](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hant)
