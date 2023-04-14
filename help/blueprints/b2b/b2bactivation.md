---
title: B2B 對象和個人資料啟用藍圖
description: 透過 Real-Time Customer Data Platform​，提供以公司客戶對象和個人資料為中心的客戶體驗。
solution: Real-time Customer Data Platform
kt: 9311
exl-id: 5215d077-b0a9-4417-ae9b-f4961d4a73fa
source-git-commit: dabb5ae0bf2fc186f67d4aa93a2e9e8c5bb04498
workflow-type: ht
source-wordcount: '842'
ht-degree: 100%

---

# B2B 對象和個人資料啟用藍圖

使用與個別客戶系結的公司帳戶、機會和銷售機會資訊，建立可操作的 b2b 個人資料，以改進跨通道的個人化和鎖定目標。

## 使用案例

* 針對 B2B 資料（包括公司帳戶、機會和銷售機會），建立人員對象，以針對各通道鎖定目標和個人化。
* 對任何 Experience Platform 目標啟用對象，以用於鎖定目標和個人化。

## 應用程式

* Real-time Customer Data Platform B2B版

## 整合模式

* B2B 資料來源（Marketo、Salesforce 等）-> Real-time Customer Data Platform B2B 版 -> 目標
各種 B2B 資料來源可用於將公司客戶、銷售機會、機遇以及人員資料對應至 B2B 版本的 Real-time Customer Data Platform。

## 架構

<img src="assets/b2b-activation.svg" alt="B2B 啟用藍圖參考架構" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />
<br>

## 護欄

* 請注意，Marketo Engage 相關護欄和實作步驟僅在將 Marketo Engage 用作源和/或目標時才相關。

* 有關端對端延遲的其他詳細資訊和護欄，請參閱[部署護欄文件](../experience-platform/deployment/guardrails.md)


### 多個執行個體和 IMS 組織支援：

以下概述了對應 Experience Platform 和 Marketo Engage 執行個體的支援模式。

#### Marketo 作為 Experience Platform 的資料來源：

* 支援將多個 Marketo Engage 執行個體對應到一個 Experience Platform 執行個體。
* 支援將多個 Marketo Engage 執行個體對應到許多 Experience Platform 執行個體。
* 不支援將一個 Marketo Engage 執行個體對應到許多 Experience Platform 執行個體。
* 支援將一個 Marketo Engage 執行個體對應到一個 Experience Platform 執行個體和多個沙箱。

#### Marketo 作為 Experience Platform 的目的地：

* 支援 Experience Platform 對應到許多 Marketo Engage 執行個體
* 支援將許多 Experience Platform 執行個體對應到一個 Marketo Engage 執行個體

#### Experience Platform 個人資料和細分護欄：

* 請參閱 Experience Platform-[個人資料和細分護欄](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hant)的個人資料和細分護欄
* B2B 區段（包括帳戶、銷售機會、機遇）使用多實體關係，導致區段評估成為批。僅限人員和事件的區段支援串流細分。

#### Experience Platform-Marketo Engage 來源連接器：

* 歷史回填最多可能需要 7 天才能完成，具體取決於資料量。
* 持續的 Marketo 資料更新和變更會透過串流 API 傳送至 Experience Platform，最多可將資料延遲 5 分鐘至個人資料，並將延遲約 15 分鐘至資料湖（視數量而定）。

#### Experience Platform- Marketo 目標連接器：

* 從 Real-time Customer Data Platform 到 Marketo Engage 的串流區段共用最多需要 5 分鐘。
* 根據 Experience Platform 分段排程，每日共用一次批次分段。B2B 區段（包括帳戶、銷售機會、機遇）使用多實體關係，導致區段成為批。

#### Marketo Engage 護欄：

* 聯絡人和銷售機會必須直接在 Marketo Engage 中擷取和定義，Real-time Customer Data Platform 對象才能與 Marketo Engage 連絡人和銷售機會相匹配。

#### 目標護欄

* 請參閱目標文件，以取得有關目標的特定指南。[目標護欄](https://experienceleague.adobe.com/docs/experience-platform/destinations/guardrails.html?lang=zh-Hant)


## 實施步驟

如需如何實作和設定 Real-time Customer Data Platform B2B 版的指南，請參閱 Real-time Customer Data Platform B2B 版文件。[B2B 版 Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/b2b-overview.html?lang=zh-Hant)

有兩種可能的實施模式。從 Marketo Engage 擷取 B2B 資料和個人資料，或從其他 CRM 資料來源擷取 B2B 資料的能力。

## 實施考量

主要考量事項和設定指南藍圖

* CRM 整合與不整合 Marketo：
如果實作將使用 Marketo Engage 作為來源，且 Marketo Engage 已連線至 CRM，請使用 Experience Platform 中的 Marketo 來源連接器，將 CRM 資料擷取至 Experience Platform。如果需要擷取其他表格，請使用 Experience Platform 來源連接器。如果實作不會使用 Marketo Engage 作為來源，請使用 CRM 來源 Experience Platform 連接器，將 CRM 來源直接連接至 AEP。
* 不建議單獨使用 Real-time Customer Data Platform B2B 版進行銷售機會啟動和培養。對於此使用案例，建議使用銷售機會培養工具（例如 Marketo Engage）。
* AEP 的 Marketo Engage 目標連接器可將對象推送至 Marketo Engage 以進行啟用，只會推送電子郵件地址和 ECID。如果該聯繫人尚未存在，則不會建立新的銷售機會，因此需要將個人資料和銷售機會資料擷取到 Marketo Engage 中。

## 相關文件

* [B2B 版 Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/b2b-overview.html?lang=zh-Hant)
* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hant)
* [Marketo Engage](https://experienceleague.adobe.com/docs/marketo/using/home.html?lang=zh-Hant)
* [Adobe Experience Platform - Marketo Source Connector](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo.html?lang=zh-Hant)
* [Adobe Experience Platform – Marketo Destination Connector](https://experienceleague.adobe.com/docs/marketo/using/product-docs/core-marketo-concepts/smart-lists-and-static-lists/static-lists/push-an-adobe-experience-platform-segment-to-a-marketo-static-list.html?lang=zh-Hant)
