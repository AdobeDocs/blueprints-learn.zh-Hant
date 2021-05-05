---
title: 觸發訊息與Adobe Experience Platform藍圖
description: 使用 Adobe Experience Platform 做為串流資料、客戶個人資料和分眾的中心，執行觸發式訊息和體驗。
solution: Experience Platform, Campaign, Journey Orchestration
kt: 7197
exl-id: 97831309-f235-4418-bd52-28af815e1878
translation-type: tm+mt
source-git-commit: 81df87f850b7ac4be9dce7a3b96d39a3a47685c5
workflow-type: tm+mt
source-wordcount: '694'
ht-degree: 68%

---

# 觸發訊息與Adobe Experience Platform藍圖

使用 Adobe Experience Platform 做為串流資料、客戶個人資料和分眾的中心，執行觸發式訊息和體驗。

## 使用案例

* 觸發的訊息
* 註冊確認
* 購物車與申請表格放棄
* 位置觸發的訊息

## 架構

<img src="assets/triggered.svg" alt="觸發訊息與Adobe Experience Platform藍圖的參考架構" style="border:1px solid #4a4a4a" />

## 整合模式

* Adobe Experience Platform -> Journey Orchestration

## 先決條件

* Adobe Experience Platform
* Journey Orchestration

## 護欄

### Journey Orchestration

* 請參閱連結以獲取[關於限制的更多詳情](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=zh-Hant#starting-with-journeys)
* 封頂可透過 API 設定使用，以確保目標系統不會飽和至失敗點。封頂意味著超出上限的訊息將徹底予以丟棄，不再傳送。仍不支援節流。
   * 最大連接數：目標可以處理的最大 http/s 連接數
   * 最大呼叫數：要在 periodInMs 參數中設定的最大呼叫數
   * periodInMs：時間 (毫秒)
* 由區段會籍發起的歷程可以兩種模式操作：
   * 批次區段 (每 24 小時重新整理一次)
   * 串流區段 (&lt;5 分鐘資格)
* 批次區段：確保您瞭解符合資格使用者的每日流量，並確保目標系統可以處理每個歷程以及所有歷程的高載輸送量
* 串流區段：確保設定檔資格的初始高載可隨每個歷程及所有歷程中符合資格的每日串流流量一起處理
* 最終目標必須支援 REST API 和 JSON 負載
* 目前不支援 Offer Decisioning
* 請參閱 [Experience Platform 的設定檔和資料擷取護欄](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hant)

### Adobe Campaign Standard

* 僅可支援 14 tps (每小時 50k) 的輸送量
* 不支援區段會籍發起的歷程
* Journey Orchestration 中支援對異動訊息開啟 / 點擊的反應事件。
* 異動訊息記錄目前不會自動同步至 Experience Platform，需要手動設定。建議最多每隔四小時匯出一次記錄。


## 實施步驟

### Adobe Experience Platform

#### 方案 / 資料集

1. [在 Experience Platform 中基於客戶提供的資料設定個別設定檔、體驗事件及多實體方案。](https://experienceleague.adobe.com/docs/platform-learn/tutorials/schemas/create-a-schema.html)
1. 為broadLog、trackingLog、非交付項位址和描述檔偏好設定建立Adobe Campaign結構（選用）。
1. [建立](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html) 要收錄資料的資料Experience Platform。
1. [將資料使用](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html) Experience Platform新增至資料集以利管理。
1. [建立政策以在目標上執行治理。](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html)

#### 設定檔 / 身份

1. [建立任何客戶專屬的命名空間](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html)。
1. [將身分新增至結構](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html)。
1. [為配置檔案啟用模式和資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html)。
1. [為「即時客](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html) 戶個人資料」的 [!UICONTROL 不同檢視設定合併政策] （可選）。
1. 建立區段以利Adobe Campaign使用。

#### 來源 / 目標

1. [使用串流API和來](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion) 源連接器，將資料內嵌至Experience Platform。1配置 [!DNL Azure] blob儲存目標以用於Adobe Campaign。

#### 行動應用程式部署

1. 實作Adobe Campaign Classic的Adobe CampaignSDK或Adobe Campaign Standard的Experience PlatformSDK。 如果有Experience Platform Launch，建議將Adobe Campaign Classic或Adobe Campaign Standard擴充功能與Experience PlatformSDK搭配使用。


### Journey Orchestration

1. 必須先在 Journey Orchestration 中設定用於啟動客戶歷程的串流資料才可獲得協調 ID。此協調 ID 然後提供給開發者與擷取一起使用。
1. 設定外部資料來源。
1. 設定自訂動作。

### Adobe Campaign Standard

1. 使用適當的個人化設定來設定訊息傳送範本。
1. 設定匯出工作流程匯出異動訊息記錄。建議最多每隔四小時執行一次。


## 相關文件

* [Adobe Experience Platform 文件](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hant)
* [Journey Orchestration 文件](https://experienceleague.adobe.com/docs/journey-orchestration.html?lang=zh-Hant)
* [Adobe Campaign Classic檔案](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=zh-Hant)
* [Adobe Campaign Standard檔案](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=zh-Hant)
* [Experience Platform Launch 文件](https://experienceleague.adobe.com/docs/launch.html?lang=zh-Hant)
* [Experience Platform Mobile SDK 文件](https://experienceleague.adobe.com/docs/mobile.html?lang=zh-Hant)
