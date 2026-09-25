---
title: Real-Time CDP 與 Adobe Campaign v8 整合模式
description: 展示 Adobe Experience Platform 及其 Real-Time Customer Profile 和集中式細分工具如何與 Adobe Campaign v8 一起使用，以提供個人化的對話體驗。
solution: Real-Time Customer Data Platform, Campaign
exl-id: d0291088-02ed-4e7e-b538-018ea40e38c6
TQID: https://experienceleague.adobe.com/LANKBKui1B5RfyNI8ufsgjrC98TXpAf74IB-alwDTnk
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fdddec33-c9cb-4459-b8b6-2664395a6f10
    internal-label: Real-Time Customer Data Platform
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
source-git-commit: 79738031788419872e32b8f754febacbfd18cc06
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 72%
---
# 具有Adobe [!DNL Campaign] v8整合模式的[!DNL Real-Time CDP]

展示Adobe [!DNL Experience Platform]及其即時客戶設定檔和集中式細分工具如何與Adobe Campaign搭配使用，以提供個人化的對話。

## 應用程式

* Adobe [!DNL Experience Platform Real-Time CDP]
* Adobe [!DNL Campaign] v8

## 架構

![批次傳訊與Adobe Experience Platform整合模式的參考架構](images/campaign-v8-with-rtcdp.png){width="1000" zoomable="yes"}

<br>

## 先決條件

* 必須使用有效的 IMS Org，才能為 Experience Cloud 佈建客戶
* 建議將Adobe Experience Platform和[!DNL Campaign]布建在同一個用於單一登入URL的IMS組織中
* 客戶必須布建[!DNL Campaign]的V8執行個體
* 客戶必須符合資格且擁有 RTCDP、Sources、Destinations 的存取權。
* Adobe [!DNL Campaign]產品內容必須存在

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

* 請參閱 AEP 的設定檔和資料擷取護欄 — [連結](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hant)
