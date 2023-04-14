---
title: 客戶活動中心藍圖
description: '[!UICONTROL Real-time Customer Profile] 查詢，提供代理協助的支援及銷售之情境。'
solution: Data Collection
kt: 7195
exl-id: 3616cbf1-2e59-4e68-a1ff-1d2e3b344a1c
source-git-commit: 5110ee2a7a079945475055cbcfdabf7cdcaa0ab5
workflow-type: ht
source-wordcount: '382'
ht-degree: 100%

---

# 客戶活動中心藍圖

客戶活動中心藍圖顯示外部應用程式如何存取 Adobe Experience Platform 的[!UICONTROL  Real-time Customer Profile]。

外部應用程式可以透過 API GET 請求存取個人資料。儲存在個人資料中的屬性、事件、區段會籍及模型驅動的功能然後可用於這些外部非 Adobe 應用程式。

有了此功能，您可以在客戶呼叫您的呼叫中心時顯示豐富的內容。例如，支援代理可以看見客戶的期限值、反感或接觸行銷活動的傾向性。銷售代理亦會受益，因為他們可以知道客戶的更多背景或洞察其客戶。

>[!NOTE]
>
>個人資料查詢 API 目前支援的延時約為 500 毫秒，所以此方法不適用於個人資料與即時決策引擎 (如同頁網路或行動裝置個人化) 的整合。

## 使用案例

* 為代理支援的互動提供更深入的消費者背景，例如支援和銷售經驗。使用對 Experience Platform 的個人資料查詢，代理可以獲得關於消費者的更多背景，例如最近的購買、行銷活動互動、傾向性、對象會籍，以及即時客戶個人資料中儲存的其他屬性和深入見解。

## 架構

<img src="assets/customer_activity_hub.svg" alt="客戶活動中心 Blueprint 的參考架構" style="width:90%; border:1px solid #4a4a4a"  class="modal-image" />

## 護欄

* [[!UICONTROL 即時客戶個人資料]的護欄](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hant)

## 實施步驟

1. 為要擷取的資料[建立資料方案](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm&amp;lang=zh-Hant)。
1. 為要擷取的資料[建立資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=zh-Hant)。
1. [在方案上設定正確的身份和身份命名空間](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hant)，以確保擷取的資料可以嵌入統一的個人資料。
1. [為個人資料啟用方案和資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=zh-Hant)。
1. [擷取資料](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=zh-Hant)到 Experience Platform。
1. [設定合併政策](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=zh-Hant)。
1. 使用[實體 API 從記錄實體或體驗事件實體查詢個人資料屬性](https://experienceleague.adobe.com/docs/experience-platform/profile/api/entities.html?lang=zh-Hant)。

## 相關文件

* [Adobe Experience Platform Activation 產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/adobe-experience-platform0.html)
* [[!UICONTROL 即時客戶個人資料]文件](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html?lang=zh-Hant)
* [個人資料護欄](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hant)
* [個人資料查詢 API](https://www.adobe.io/apis/experienceplatform/home/api-reference.html)
