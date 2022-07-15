---
title: Journey Optimizer — 觸發的訊息傳送與 Adobe Experience Platform Blueprint
description: 使用 Adobe Experience Platform 做為串流資料、客戶個人資料和分眾的中心，執行觸發式訊息和體驗。
solution: Journey Optimizer
exl-id: 97831309-f235-4418-bd52-28af815e1878
source-git-commit: 37fa3bc00175a4636766564f0b8fb847fa8a951e
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Journey Optimizer

Adobe Journey Optimizer 是行銷團隊專門建立的一款系統，可即時回應客戶行為，並滿足客戶需求。資料管理功能已移至 Adobe Experience Platform，有助於行銷團隊專注於其最佳作法：建立一流的客戶歷程和個人化對話。此 Blueprint 概述了應用程式的技術功能，並深入探討了組成 Adobe Journey Optimizer 的各種架構元件。

<br>

## 使用案例

* 觸發的訊息
* 歡迎和註冊確認
* 購物車與申請表格放棄
* 位置觸發的訊息
* 體育場內體驗
* 抵達前的旅行和招待以及入住體驗

<br>

## 架構

<img src="assets/ajo-architecture.svg" alt="參考建築Journey Optimizer藍圖" style="width:100%; border:1px solid #4a4a4a" />

<br>

## 藍圖方案

| 狀況 | 說明 | 功能 |
| :-- | :--- | :--- |
| [第三方消息傳遞](3rd-party-messaging.md) | 演示如何將Adobe Journey Optimizer與第三方消息傳遞系統一起使用，以協調和發送個性化通信 | 在客戶與您的品牌或公司進行互動時，立即提供1:1的個性化通信<br><br>注意事項：<br><ul><li>第三方系統必須支援用於驗證的承載令牌</li><li>由於多租戶體系結構，不支援靜態IP</li><li>在每秒API調用時，請注意第三方系統的體系結構限制。  可能需要客戶從第三方供應商購買更多卷以支援來自Journey Optimizer的卷</li><li>不支援消息或負載中的決策管理</li></ul> |

<br>

## 整合模式

| 整合 | 說明 | 功能 |
| :-- | :--- | :--- |
| [Journey Optimizer與Adobe Campaign](ajo-and-campaign.md) | 顯示如何使用Adobe Journey Optimizer來協調利用即時客戶概要資訊的1:1體驗，並利用本機Adobe Campaign事務性消息傳遞系統來發送消息 | 利用Journey Optimizer的即時客戶概況和能力，在利用Adobe Campaign的本機即時消息傳遞功能進行最後一英里通信的同時，協調即時體驗<br><br>注意事項：<br><ul><li>市場活動應用程式必須位於v7版本>21.1或v8上</li><li>消息傳送吞吐量</li><ul><li>活動v7 — 每小時最多5萬</li><li>促銷v8 — 每小時最多100萬</li><li>Campaign Standard — 每小時最多5萬</li></ul><li>不執行限制，因此使用案例需要企業架構師進行技術審查</li><li>不支援在市場活動發送的消息中使用決策管理</li></ul> |

<br>

## 先決條件

Adobe Experience Platform

* 必須先在系統中配置架構和資料集，然後才能配置Journey Optimizer資料源
* 對於基於經驗事件類的架構，當希望觸發的事件不是基於規則的事件時，添加「業務流程事件ID」欄位組
* 對於基於單個配置檔案類的架構，添加「配置檔案test詳細資訊」欄位組，以便能夠載入test配置檔案以與Journey Optimizer一起使用

電子郵件

* 必須準備好子域以用於消息發送
* 子域可以完全委託給Adobe（推薦），也可以使用CNAME指向特定於Adobe的DNS伺服器（自定義）
* 每個子域都需要GoogleTXT記錄，以確保良好的可交付性

行動裝置推送

* 客戶必須有可建立應用程式的行動裝置開發人員
* Adobe Experience Platform Mobile SDK

<br>

## 護欄

[Journey Optimizer護欄產品連結](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=en)

請注意上述連結中未列出的這些內容：

* 批次區段 — 需要確保您瞭解符合資格使用者的每日流量，並確保目標系統可以處理每個歷程以及所有歷程的高載輸送量
* 串流區段 — 需要確保個人資料資格的初始高載可隨每個歷程及所有歷程中符合資格的每日串流流量一起處理
* 僅在消息中本機支援決策管理（無自定義操作）
* 支援的消息類型：
   * 電子郵件
   * 推送 (FCM / APNS)
   * 自定義操作（通過Rest API）
* 與第三方系統的出站整合
   * 不支援單個靜態IP，因為我們的基礎架構是多租戶（必須允許列出所有資料中心IP）
   * 自定義操作僅支援POST和PUT方法
   * 通過用戶/通過或授權令牌進行身份驗證
* 無法將Adobe Experience Platform或Journey Optimizer的各個部件包裝和在各種沙箱之間移動。 必須在新環境中重新實施

### 資料擷取護欄

<img src="assets/aep-data-ingestion-details-latency.svg" alt="參考建築Journey Optimizer藍圖" style="width:80%; border:1px solid #4a4a4a" />

<br>

### 激活護欄

<img src="assets/ajo-activation-details-latency.svg" alt="參考建築Journey Optimizer藍圖" style="width:80%; border:1px solid #4a4a4a" />

<br>

## 實施步驟

### Adobe Experience Platform

#### 方案 / 資料集

1. 在 Experience Platform 中基於客戶提供的資料[設定個別個人資料、體驗事件及多實體方案。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm)
1. 在 Experience Platform 中為要擷取的資料[建立資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=zh-Hant)。
1. [在 Experience Platform 中新增使用標籤](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=zh-Hant)至資料集以便於治理。
1. [建立政策](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=zh-Hant)以在目標上執行治理。

#### 個人資料 / 身份

1. [建立任何客戶特定的命名空間。](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hant)
1. [新增身份至方案](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html)。
1. [為個人資料啟用方案和資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=zh-Hant)。
1. 為[!UICONTROL 即時客戶個人資料]的不同檢視[設定合併政策](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=zh-Hant) (可選)。
1. 為行程使用建立段。

#### 來源 / 目標

1. 使用串流 API 和來源連接器[將資料擷取到 Experience Platform。](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=zh-Hant)

### Journey Optimizer

1. 配置Experience Platform資料源並確定快取哪些欄位作為配置檔案的一部分流資料用於啟動客戶行程必須先在Journey Optimizer內配置流資料，才能獲取業務流程ID。 此業務流程ID隨後將提供給開發人員以用於接收
1. 設定外部資料來源。
1. 設定自訂動作。

### 移動推送配置

1. 實施Experience PlatformMobile SDK以收集推送令牌和登錄資訊，以將其與已知客戶配置檔案綁定
1. 利用Adobe標籤並建立具有以下副檔名的移動屬性：
1. Adobe Journey Optimizer
1. Adobe Experience Platform Edge Network
1. 身分 邊緣網路
1. 行動裝置核心
1. 確保您有專用資料流用於移動應用部署與Web部署
1. 有關詳細資訊，請遵循 [Adobe Journey Optimizer移動指南](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-journey-optimizer)


## 相關文件

* [Experience Platform文檔](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hant)
* [Experience Platform標籤文檔](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=en)
* [Experience Platform Mobile SDK 文件](https://experienceleague.adobe.com/docs/mobile.html?lang=zh-Hant)
* [Journey Optimizer 文件](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=en)
* [Journey Optimizer產品說明](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer.html)
