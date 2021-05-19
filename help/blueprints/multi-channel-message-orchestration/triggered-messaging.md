---
title: 觸發的訊息傳送與 Adobe Experience Platform Blueprint
description: 使用 Adobe Experience Platform 做為串流資料、客戶個人資料和分眾的中心，執行觸發式訊息和體驗。
solution: Experience Platform, Campaign, Journey Orchestration
kt: 7197
exl-id: 97831309-f235-4418-bd52-28af815e1878
translation-type: ht
source-git-commit: 01f70fe432d7be38b71889ae19c0d5fe4cf0f78a
workflow-type: ht
source-wordcount: '694'
ht-degree: 100%

---

# 觸發的訊息傳送與 Adobe Experience Platform Blueprint

使用 Adobe Experience Platform 做為串流資料、客戶個人資料和分眾的中心，執行觸發式訊息和體驗。

## 使用案例

* 觸發的訊息
* 註冊確認
* 購物車與申請表格放棄
* 位置觸發的訊息

## 架構

<img src="assets/triggered.svg" alt="觸發的訊息傳送與 Adobe Experience Platform Blueprint 之參考架構" style="border:1px solid #4a4a4a" />

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
* 串流區段：確保個人資料資格的初始高載可隨每個歷程及所有歷程中符合資格的每日串流流量一起處理
* 最終目標必須支援 REST API 和 JSON 負載
* 目前不支援 Offer Decisioning
* 請參閱 [Experience Platform 的個人資料和資料擷取護欄](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hant)

### Adobe Campaign Standard

* 僅可支援 14 tps (每小時 50k) 的輸送量
* 不支援區段會籍發起的歷程
* Journey Orchestration 中支援對異動訊息開啟 / 點擊的反應事件。
* 異動訊息記錄目前不會自動同步至 Experience Platform，需要手動設定。建議最多每隔四小時匯出一次記錄。


## 實施步驟

### Adobe Experience Platform

#### 方案 / 資料集

1. 在 Experience Platform 中基於客戶提供的資料[設定個別個人資料、體驗事件及多實體方案。](https://experienceleague.adobe.com/docs/platform-learn/tutorials/schemas/create-a-schema.html?lang=zh-Hant)
1. 建立 broadLog、trackingLog、無法送達的地址及個人資料偏好設定 (可選)　的 Adobe Campaign 方案。
1. 在 Experience Platform 中為要擷取的資料[建立資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=zh-Hant)。
1. [在 Experience Platform 中新增使用標籤](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=zh-Hant)至資料集以便於治理。
1. [建立政策](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=zh-Hant)以在目標上執行治理。

#### 個人資料 / 身份

1. [建立任何客戶特定的命名空間。](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hant)
1. [新增身份至方案](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hant)。
1. [為個人資料啟用方案和資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=zh-Hant)。
1. 為[!UICONTROL 即時客戶個人資料]的不同檢視[設定合併政策](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=zh-Hant) (可選)。
1. 建立 Adobe Campaign 使用的區段。

#### 來源 / 目標

1. 使用 API 與來源連接器[擷取資料到 Experience Platform](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=zh-Hant)。1. 設定[!DNL Azure]要與 Adobe Campaign 一起使用的 Blob 儲存目標。

#### 行動應用程式部署

1. 對 Adobe Campaign Classic 實施 Adobe Campaign SDK，或對 Adobe Campaign Standard 實施 Experience Platform SDK。如果 Experience Platform Launch 存在，建議 Adobe Campaign Classic 或 Adobe Campaign Standard 延伸與 Experience Platform SDK 一起使用。


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
* [Adobe Campaign Classic 文件](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=zh-Hant)
* [Adobe Campaign Standard 文件](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=zh-Hant)
* [Experience Platform Launch 文件](https://experienceleague.adobe.com/docs/launch.html?lang=zh-Hant)
* [Experience Platform Mobile SDK 文件](https://experienceleague.adobe.com/docs/mobile.html?lang=zh-Hant)
