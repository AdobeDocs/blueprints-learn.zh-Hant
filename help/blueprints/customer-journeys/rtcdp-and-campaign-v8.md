---
title: Real-Time CDP 與 Adobe Campaign v8 整合模式
description: 展示 Adobe Experience Platform 及其 Real-Time Customer Profile 和集中式細分工具如何與 Adobe Campaign v8 一起使用，以提供個人化的對話體驗。
solution: Real-time Customer Data Platform, Campaign
exl-id: d0291088-02ed-4e7e-b538-018ea40e38c6
source-git-commit: 711d781e4b0cf967786808233badbc5eac8a5815
workflow-type: ht
source-wordcount: '356'
ht-degree: 100%

---

# Real-Time CDP 與 Adobe Campaign v8 整合模式

展示 Adobe Experience Platform 及其即時客戶設定檔和集中式細分工具如何與 Adobe Campaign 一起使用，以提供個人化的對話體驗。

<br>

## 應用程式

* Adobe Experience Platform Real-Time CDP
* Adobe Campaign v8

<br>

## 架構

<img src="assets/rtcdp-campaignv8-architecture.svg" alt="批次訊息傳送與 Adobe Experience Platform 整合模式之參考架構" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## 先決條件

* 必須使用有效的 IMS Org，才能為 Experience Cloud 佈建客戶
* Adobe Experience Platform 和 Campaign 建議在相同的 IMS 組織中布建，以取得單一登入 URL
* 客戶必須布建 Campaign V8 執行個體
* 客戶必須符合資格且擁有 RTCDP、Sources、Destinations 的存取權。
* Adobe Campaign 產品情境必須存在

<br>

## 實施步驟

請參閱下列文件，了解如何將 Campaign v8 來源連接器設定為 Adobe Experience Platform，以及將 Real-time Customer Data Platform 目標連接器設定為 Campaign v8。
[Campaign 與 AEP 連接器](https://experienceleague.adobe.com/docs/campaign/campaign-v8/connect/ac-aep.html?lang=zh-Hant)

## 護欄

### Adobe Campaign

* 請參閱 Campaign 來源連接器文件 — [Campaign 來源連接器](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/adobe-applications/campaign.html?lang=zh-Hant)
* 僅支援 Adobe Campaign 單一組織單位部署


### Experience Platform Real-time Customer Data Platform 區段共用

* 請參閱 RTCDP Campaign Destination 連接器 — [RTCDP Campaign 連線](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign-managed-services.html?lang=zh-Hant)
* 建議限制為 50 個區段
* 請注意，AEP 的區段成員資格實現對於批次（每天 1 次）和串流（約 5 分鐘）都會延遲，並且基於區段評估排程。
* 啟用延遲最少 3 小時
* 僅聯合方案屬性可啟用 (不支援陣列/地圖/體驗事件)
* 建議每個區段不超過 20 項屬性
* 所有「已實現」區段會籍的個人資料為每個區段一個檔案；或者擁有「已實現」和「已退出」個人資料的檔案，則將區段匯集新增為一個屬性
* 支援漸進式和完整區段匯出
* 不支援檔案加密
* 請參閱 AEP 的設定檔和資料擷取護欄 — [連結](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hant)
