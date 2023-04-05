---
title: 檔案和企業串流目標的對象和設定檔啟用藍圖
description: 對象與個人資料啟用至企業目標
solution: Real-time Customer Data Platform
kt: 7475
exl-id: 32133174-eb28-44ce-ab2a-63fcb5b51cb5
source-git-commit: 0d1bb41eb6b70be7c3c8a3196c9974a0d7807404
workflow-type: ht
source-wordcount: '415'
ht-degree: 100%

---

# 檔案和企業串流目標的對象和設定檔啟用藍圖

以串流或批次方式從[!UICONTROL Real-time Customer Data Platform]分享個人資料及對象變更與事件至企業資料儲存空間和應用程式。這些個人資料和對象事件可用於啟動對客戶的銷售或支援行動，例如跟進放棄的應用程式程序或網路研討會註冊，或者用[!UICONTROL Real-time Customer Data Platform]中的最新客戶屬性和情報更新企業應用程式。

## 使用案例

* 針對雲端儲存目標或串流目標的個人資料和對象啟用，以進行客戶資料和分析的企業追蹤、儲存、分析和啟用。

## 應用程式

* Adobe Experience Platform啟用

## 架構

<img src="assets/known_activation.svg" alt="Enterprise Activation 狀況的參考架構" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />


## 護欄

[請參閱「對象與個人資料啟用」概觀頁面所述的護欄。](overview.md)

## 實施步驟

1. 為要擷取的資料[建立資料方案](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm)。
1. 為要擷取的資料[建立資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=zh-Hant)。
1. [在方案上設定正確的身份和身份命名空間](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hant)，以確保擷取的資料可以嵌入統一的個人資料。
1. [為個人資料啟用方案和資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=zh-Hant)。
1. [擷取資料](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=zh-Hant)到 Experience Platform。
1. [在 Experience Platform 與 Audience Manager 之間為 Experience Platform 中定義要分享至 Audience Manager 的對象佈建[!UICONTROL Real-time Customer Data Platform]區段分享。](https://www.adobe.com/go/audiences)
1. 在 Experience Platform 中[建立區段](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=zh-Hant)。系統會自動確定區段是作為批次還是串流評估。
1. 將用於個人資料屬性和對象會籍分享的目標[設定為所需的目標。](https://experienceleague.adobe.com/docs/platform-learn/tutorials/destinations/create-destinations-and-activate-data.html?lang=zh-Hant)

## 相關文件

* [目標文件](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=zh-Hant)
* [雲端儲存空間目標概觀](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/cloud-storage/overview.html?lang=zh-Hant#catalog)
* [HTTP 目標](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/http-destination.html?lang=zh-Hant#overview)
* [[!UICONTROL Real-time Customer Data Platform]產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/real-time-customer-data-platform.html)
* [個人資料與細分準則](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hant)
* [細分文件](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=zh-Hant)

## 相關視訊與教學課程

* [[!UICONTROL Real-time Customer Data Platform]概覽](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=zh-Hant)
* [[!UICONTROL Real-time Customer Data Platform]示範](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=zh-Hant)
* [建立區段](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=zh-Hant)
