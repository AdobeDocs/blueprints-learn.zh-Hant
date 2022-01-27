---
title: B2B激活
description: 與Real-time Customer Data Platform提供基於客戶的受眾和以個人資料為中心的客戶體​驗。
solution: Experience Platform, Real-time Customer Data Platform
kt: 9311
source-git-commit: c64aa472624abd7279e9c26e2affa0878796ab33
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# B2B受眾和配置檔案激活

使用與單個客戶關聯的客戶、機會和潛在客戶資訊建立可操作的b2b配置檔案，以跨渠道改進個性化和目標化。

## 使用案例

* 建立用戶群，以針對客戶、機會和銷售線索等B2B資料跨渠道進行定位和個性化。
* 將受眾激活到任何Experience Platform目標，以便進行目標和個性化。

## 應用程式

* 即時客戶資料平台 B2B版

## 整合模式

* B2B資料源(Marketo、Salesforce等) ->Real-time Customer Data PlatformB2B版 — >目的地各種B2B資料源可用於將帳戶、潛在顧客、機會和人員資料映射到Real-time Customer Data PlatformB2B版。

## 架構

<img src="assets/b2b-activation.svg" alt="B2B激活藍圖的參考體系結構" style="width:80%; border:1px solid #4a4a4a" />
<br>

## 護欄

請注意，只有將Marketo Engage用作源和/或目標時，Marketo Engage相關的護欄和實施步驟才相關。

### 多實例和IMS組織支援：

以下概述了支援的映射Experience Platform和Marketo Engage實例模式。

#### Marketo作為資料源Experience Platform:

* 支援多個Marketo Engage實例到一個Experience Platform實例。
* 不支援多個Marketo Engage實例到多個Experience Platform實例。
* 不支援一個Marketo Engage實例到多個Experience Platform實例。
* 支援一個Marketo Engage實例到一個Experience Platform實例和多個沙箱。

#### Marketo是Experience Platform的目的地：

* Experience Platform到多個Marketo Engage實例
* 支援多個Experience Platform實例到一個Marketo Engage實例

#### Experience Platform輪廓和分段護欄：

* 請參閱配置檔案和分段護欄以獲取Experience Platform- [配置檔案和分段指南](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hant)
* B2B網段（包括帳戶、銷售線索、業務機會）使用多實體關係，導致網段評估成為批。 支援流分段，該分段限於人和事件。

#### Experience Platform-Marketo Engage源連接器：

* 歷史回填最多可能需要7天才能完成，具體取決於資料量。
* 通過流API將Marketo的持續資料更新和更改發送到Experience Platform，流API最多可以潛在到概要檔案約5分鐘，而根據卷的不同，潛在到資料湖約15分鐘。

#### Experience Platform-Marketo目的地連接器：

* 從Real-time Customer Data Platform到Marketo Engage的流媒體段共用最多需要5分鐘。
* 基於Experience Platform分段調度每天共用一次批分段。 B2B網段（包括帳戶、銷售線索、業務機會）使用多實體關係，導致網段成為批。

#### Marketo Engage瓜德賴爾：

* 聯繫人和線索必須直接以Marketo Engage方式接收和定義，以便Real-time Customer Data Platform受眾與Marketo Engage聯繫人和線索匹配。

#### 目標護欄

* 請參閱目標文檔以瞭解有關目標的特定指導。 [目標指導原則](https://experienceleague.adobe.com/docs/experience-platform/destinations/home.html?lang=en)


## 實施步驟

有關如何實施和配置Real-time Customer Data PlatformB2B版的指導，請參閱Real-time Customer Data Platform文檔的B2B版。 [B2B版Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/b2b-overview.html?lang=en)

存在兩種可能的實施模式。 從Marketo Engage中接收B2B資料和配置檔案，或從其他CRM資料源中接收B2B資料。

## 實施考量

關於藍圖的主要考慮事項和配置的指導。

* CRM與Marketo的整合和不整合：如果實現將使用Marketo Engage作為源，並且Marketo Engage連接到CRM，則使用Experience Platform中的Marketo源連接器將CRM資料錄入Experience Platform。 如果需要接收其他表，請使用Experience Platform源連接器。 如果實現將不使用Marketo Engage作為源，則使用CRM源Experience Platform連接器將CRM源直接連接到AEP。
* 不建議僅從Real-time Customer Data Platform的B2B版中引導和培養鉛。 在此使用案例中，建議使用鉛培養工具(如Marketo Engage)。
* AEP的Marketo Engage目標連接器將受眾推送到Marketo Engage以進行激活，僅推送電子郵件地址和ECID。 如果聯繫人不存在，則不會建立新的潛在顧客，因此需要將配置檔案和潛在顧客資料錄入Marketo Engage。

## 相關文件

* [B2B版Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/b2b-overview.html?lang=en)
* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hant)
* [Marketo Engage](https://experienceleague.adobe.com/docs/marketo/using/home.html?lang=en)
* [Adobe Experience Platform-Marketo源連接器](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo.html?lang=zh-Hant)
* [Adobe Experience Platform-Marketo目的地連接器](https://experienceleague.adobe.com/docs/marketo/using/product-docs/core-marketo-concepts/smart-lists-and-static-lists/static-lists/push-an-adobe-experience-cloud-segment-to-a-marketo-static-list.html?lang=en)
