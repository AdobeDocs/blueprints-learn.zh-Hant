---
title: B2B 對象和個人資料啟用藍圖
description: 透過 Real-Time Customer Data Platform​，提供以公司客戶對象和個人資料為中心的客戶體驗。
solution: Real-Time Customer Data Platform
kt: 9311
exl-id: 5215d077-b0a9-4417-ae9b-f4961d4a73fa
source-git-commit: 70816df06ec2dff5c3a4a94a8be701cb25e6f783
workflow-type: tm+mt
source-wordcount: '898'
ht-degree: 51%

---

# B2B 對象和個人資料啟用藍圖

使用與個別客戶系結的公司帳戶、機會和銷售機會資訊，建立可操作的 b2b 個人資料，以改進跨通道的個人化和鎖定目標。

## 使用案例

* 針對 B2B 資料（包括公司帳戶、機會和銷售機會），建立人員對象，以針對各通道鎖定目標和個人化。
* 對任何 Experience Platform 目標啟用對象，以用於鎖定目標和個人化。
* 建立帳戶的受眾（例如公司清單），並透過LinkedIn之類的目的地鎖定這些公司，該目的地接受公司清單作為輸入或匯出至雲端儲存目的地以進行目標定位和銷售推廣。

## 應用程式

* Real-time Customer Data Platform B2B版

## 整合模式

* B2B資料來源(Marketo、Salesforce等) -> Real-time Customer Data Platform B2B edition ->目的地
* 各種B2B資料來源可用於將帳戶、銷售機會、機會和人員資料對應到Real-time Customer Data Platform的B2B edition。

## 架構

![B2B啟動Blueprint的參考架構](assets/b2b-activation.png)

## 護欄

* 請注意，Marketo Engage 相關護欄和實作步驟僅在將 Marketo Engage 用作源和/或目標時才相關。

* 如需資料模型、大小和區段的詳細資訊和護欄，請參閱[部署護欄檔案](../experience-platform/deployment/guardrails.md)


### 多個執行個體和 IMS 組織支援：

以下概述了對應 Experience Platform 和 Marketo Engage 執行個體的支援模式。

#### Marketo 作為 Experience Platform 的資料來源：

* 支援將多個 Marketo Engage 執行個體對應到一個 Experience Platform 執行個體。
* 不支援將一個 Marketo Engage 執行個體對應到許多 Experience Platform 執行個體。
* 支援將一個 Marketo Engage 執行個體對應到一個 Experience Platform 執行個體和多個沙箱。

#### Marketo 作為 Experience Platform 的目的地：

* 支援 Experience Platform 對應到許多 Marketo Engage 執行個體
* 支援將許多 Experience Platform 執行個體對應到一個 Marketo Engage 執行個體

#### Experience Platform 個人資料和細分護欄：

* 請參閱 Experience Platform-[個人資料和細分護欄](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hant)的個人資料和細分護欄
* B2B 區段（包括帳戶、銷售機會、機遇）使用多實體關係，導致區段評估成為批。僅限人員和事件的區段支援串流細分。
* 納入批次b2b區段作為串流或邊緣區段的輸入，以支援串流b2b區段使用案例。 批次區段會籍以最新的每日批次區段評估結果為基礎。

#### Experience Platform-Marketo Engage 來源連接器：

* 歷史回填最多可能需要 7 天才能完成，具體取決於資料量。
* 來自Marketo的持續資料更新和變更會透過串流API傳送至Experience Platform，至設定檔的延遲時間最長約為10分鐘，而至資料湖的延遲時間最長可達60分鐘，具體取決於傳送量。

#### Experience Platform- Marketo 目標連接器：

* 在區段評估後，從Real-time Customer Data Platform到Marketo Engage的串流區段共用最多可能需要15分鐘。 在首次啟用前回填已存在於區段中的設定檔最多可能需要24小時。
* 根據 Experience Platform 分段排程，每日共用一次批次分段。使用多實體關係的B2B區段（例如，使用帳戶和機會物件中資料的區段）一律會以批次模式執行。

#### Marketo Engage 護欄：

* 聯絡人和銷售機會必須直接在 Marketo Engage 中擷取和定義，Real-time Customer Data Platform 對象才能與 Marketo Engage 連絡人和銷售機會相匹配。
* RTCDP Marketo目的地可選擇為區段中，但不存在於Marketo中的客戶在Marketo中建立新的銷售機會。

#### 目標護欄

* 請參閱目標文件，以取得有關目標的特定指南。[目標護欄](https://experienceleague.adobe.com/docs/experience-platform/destinations/guardrails.html?lang=zh-Hant)


## 實施步驟

如需如何實作和設定 Real-time Customer Data Platform B2B 版的指南，請參閱 Real-time Customer Data Platform B2B 版文件。[B2B 版 Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/b2b-overview.html?lang=zh-Hant)

有兩種可能的實施模式。從 Marketo Engage 擷取 B2B 資料和個人資料，或從其他 CRM 資料來源擷取 B2B 資料的能力。

## 實施考量

主要考量事項和設定指南藍圖

* CRM與Marketo的整合及不整合：
如果實作使用Marketo Engage作為來源，而Marketo Engage已連線至CRM，則CRM資料將自動透過相同的連線流動，除非有其他未透過Marketo傳遞的CRM資料物件，否則不需要直接將CRM連線至Platform。 如果需要擷取其他表格，請使用 Experience Platform 來源連接器。如果實作不會使用Marketo Engage做為來源，請使用CRM來源Experience Platform聯結器，直接將CRM來源連線至Platform。
* 適用於Platform的Marketo Engage目的地聯結器會將受眾推送至Marketo Engage以進行啟用，並根據相符的電子郵件地址和ECID共用受眾成員。 如果聯絡人不存在，則可選擇建立新的銷售機會。 建立新銷售機會時，Real-time Customer Data Platform中可以將最多50個設定檔屬性（非陣列或對應屬性）對應到Marketo中的「人員」欄位。

## 相關文件

* [B2B 版 Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/b2b-overview.html?lang=zh-Hant)
* [開始使用Real-time Customer Data Platform B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-tutorial)
* Real-time Customer Data Platform B2B edition的[護欄](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-guardrails)
* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hant)
* [Marketo Engage](https://experienceleague.adobe.com/docs/marketo/using/home.html)
* [Adobe Experience Platform - Marketo Source Connector](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo.html?lang=zh-Hant)
* [Adobe Experience Platform – Marketo Destination Connector](https://experienceleague.adobe.com/docs/marketo/using/product-docs/core-marketo-concepts/smart-lists-and-static-lists/static-lists/push-an-adobe-experience-cloud-segment-to-a-marketo-static-list.html)
