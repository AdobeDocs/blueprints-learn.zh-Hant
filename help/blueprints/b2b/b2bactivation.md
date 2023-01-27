---
title: B2B受眾和設定檔啟用藍圖
description: 透過Real-time Customer Data Platform提供以帳戶為基礎的受眾和以設定檔為中心的客戶體​驗。
solution: Real-time Customer Data Platform
kt: 9311
exl-id: 5215d077-b0a9-4417-ae9b-f4961d4a73fa
source-git-commit: b18d491fdefc57762932d1570401b5437bf97c76
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 4%

---

# B2B受眾和設定檔啟用藍圖

使用與個別客戶系結的帳戶、機會和銷售機會資訊，建立可操作的b2b設定檔，以改進跨管道的個人化和鎖定目標。

## 使用案例

* 針對B2B資料（包括帳戶、機會和銷售機會），建立人員對象，以針對各管道鎖定目標和個人化。
* 對任何Experience Platform目的地啟用對象，以用於鎖定目標和個人化。

## 應用程式

* 即時客戶資料平台 B2B版

## 整合模式

* B2B資料來源(Marketo、Salesforce等) -> Real-time Customer Data Platform B2B版 — >目的地各種B2B資料來源可用來將帳戶、銷售機會、機會和人員資料對應至Real-time Customer Data Platform的B2B版。

## 架構

<img src="assets/b2b-activation.svg" alt="B2B啟動Blueprint的參考架構" style="width:90%; border:1px solid #4a4a4a" />
<br>

## 護欄

* 請注意，Marketo Engage相關護欄和實作步驟僅在將Marketo Engage用作源和/或目標時才相關。

* 有關端到端延遲的其他詳細資訊和護欄，請參閱 [部署護欄文檔](../experience-platform/deployment/guardrails.md)


### 多個執行個體和IMS組織支援：

以下概述支援的映射Experience Platform和Marketo Engage實例模式。

#### Marketo作為Experience Platform的資料來源：

* 支援將多個Marketo Engage例項轉換為一個Experience Platform例項。
* 不支援多個Marketo Engage例項至多個Experience Platform例項。
* 不支援一個Marketo Engage例項至多個Experience Platform例項。
* 支援一個Marketo Engage例項至一個Experience Platform例項和多個沙箱。

#### Marketo作為Experience Platform的目的地：

* 支援Experience Platform至許多Marketo Engage例項
* 支援多個Experience Platform例項至一個Marketo Engage例項

#### Experience Platform設定檔和分段護欄：

* 請參閱設定檔和分段護欄，以取得Experience Platform- [設定檔和分段護欄](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hant)
* B2B區段（包括帳戶、銷售機會、銷售機會）使用多實體關係，導致區段評估成為批。 僅限於人員和事件的區段支援串流細分。

#### Experience Platform-Marketo Engage源連接器：

* 根據資料量，歷史回填最多可能需要7天才能完成。
* 持續的Marketo資料更新和變更會透過串流API傳送至Experience Platform，最多可將資料延遲5分鐘至設定檔，並將延遲約15分鐘至資料湖（視數量而定）。

#### Experience Platform- Marketo目的地連接器：

* 從Real-time Customer Data Platform到Marketo Engage的串流區段共用最多需要5分鐘。
* 根據Experience Platform分段排程，每日共用一次批次分段。 B2B區段（包括帳戶、銷售機會、銷售機會）使用多實體關係，導致區段成為批。

#### Marketo Engage護欄：

* 聯絡人和銷售機會必須直接在Marketo Engage中擷取和定義，Real-time Customer Data Platform對象才能與Marketo Engage連絡人和銷售機會相符。

#### 目標護欄

* 請參閱目的地檔案，以取得有關目的地的特定指引。 [目標護欄](https://experienceleague.adobe.com/docs/experience-platform/destinations/guardrails.html?lang=en)


## 實作步驟

如需如何實作和設定Real-time Customer Data Platform B2B版的指引，請參閱Real-time Customer Data Platform檔案的B2B版。 [B2B版Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/b2b-overview.html?lang=en)

有兩種可能的實施模式。 從Marketo Engage內嵌B2B資料和設定檔，或從其他CRM資料來源內嵌B2B資料。

## 實作考量事項

藍圖主要考量事項和設定的指引。

* CRM與Marketo的整合與不整合：如果實作將使用Marketo Engage作為來源，且Marketo Engage已連線至CRM，請使用Experience Platform中的Marketo來源連接器，將CRM資料內嵌至Experience Platform。 如果需要擷取其他表格，請使用Experience Platform來源連接器。 如果實作不會使用Marketo Engage作為來源，請使用CRM來源Experience Platform連接器，將CRM來源直接連結至AEP。
* 僅Real-time Customer Data PlatformB2B版不建議鉛啟動和培養。 對於此使用案例，建議使用銷售機會培養工具(例如Marketo Engage)。
* AEP的Marketo Engage目的地連接器可將對象推送至Marketo Engage以進行啟用，只會推送電子郵件地址和ECID。 如果該聯繫人尚未存在，則不會建立新的銷售機會，因此需要將配置檔案和銷售機會資料內嵌到Marketo Engage中。

## 相關檔案

* [B2B版Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/b2b-overview.html?lang=en)
* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hant)
* [Marketo Engage](https://experienceleague.adobe.com/docs/marketo/using/home.html?lang=en)
* [Adobe Experience Platform - Marketo Source Connector](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo.html?lang=zh-Hant)
* [Adobe Experience Platform - Marketo目的地連接器](https://experienceleague.adobe.com/docs/marketo/using/product-docs/core-marketo-concepts/smart-lists-and-static-lists/static-lists/push-an-adobe-experience-cloud-segment-to-a-marketo-static-list.html?lang=en)
