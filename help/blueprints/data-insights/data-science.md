---
title: 為豐富個人資料的自訂資料科學藍圖
description: 此藍圖顯示如何將資料科學型的見解內嵌至 Experience Platform 中，以豐富即時客戶個人資料。
solution: Data Collection
kt: 7203
exl-id: e5ec6886-4fa4-4c9b-a2d8-e843d7758669,f0efaf3c-6c4f-47c3-ab8a-e8e146dd071c
source-git-commit: 802507291f54dc3f253d469e7a64d78e34b75c6a
workflow-type: ht
source-wordcount: '500'
ht-degree: 100%

---

# 為豐富個人資料的自訂資料科學藍圖

為豐富個人資料的自訂資料科學藍圖闡述如何使用資料來訓練、部署和計分模型，以透過資料科學和機器學習工具向 Experience Platform 和 Real-time Customer Data Platform 提供機器學習見解。模型化的見解可擷取至 Experience Platform 中，以豐富即時客戶個人資料。機器學習深入見解的範例包括期限值評分、產品和類別親和性、轉換傾向性或退訂傾向性。

## 使用案例

* 從客戶資料中擷取見解並探索模式，從這些資料中訓練模型並對模型評分。
* 使用模型驅動的深入見解和屬性豐富[!UICONTROL 即時客戶個人資料]，以進行更細緻的個人化和最佳的歷程。
* 對模型訓練和評分以確定客戶深入見解，例如客戶期限值、轉換或流失傾向性、產品和內容相似性及參與分數。

## 架構

<img src="assets/data_science.svg" alt="為豐富個人資料自訂資料科學藍圖的參考架構" style="width:90%; border:1px solid #4a4a4a" />

## 護欄

* 有關將資料科學結果擷取到 Experience Platform 和 Real-time Customer Profile 中的詳細護欄和端對端延遲，請參閱[部署護欄文檔](../experience-platform/deployment/guardrails.md)中所引用的資料擷取護欄和延遲方案。

## 實施步驟

1. 為要擷取的資料[建立資料方案](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm)。
1. 為要擷取的資料[建立資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=zh-Hant)。
1. [擷取資料](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=zh-Hant)到 Experience Platform。

若要將模型結果擷取至即時客戶個人資料中，請務必先執行下列操作，再擷取資料：

1. [在方案上設定正確的身分和身分命名空間](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hant)，以確保擷取的資料可以嵌入統一的個人資料。
1. [為個人資料啟用方案和資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=zh-Hant)。

## 實施考量

* 在大多數情況下，模型結果應擷取為個人資料屬性，而非體驗事件。模型結果可以是簡單的屬性字串。如果要擷取多個模型結果，建議使用陣列或對應類型欄位。
* 每日個人資料快照資料集是統一個人資料屬性資料的每日匯出，可用來訓練個人資料屬性資料的模型。可存取[此處](https://experienceleague.adobe.com/docs/experience-platform/dashboards/query.html?lang=zh-Hant)的個人資料快照資料集文檔。
* 若要從 Experience Platform 中擷取資料，可使用下列方法
   * 資料存取 SDK
      * 資料為原始檔案形式
      * 個人資料體驗事件資料會維持在非統一的原始狀態。
   * RTCDP 目標
      * 可輸出個人資料屬性和區段成員資格。

## 相關文件

* [Adobe Experience Platform Intelligence 產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [Adobe Experience Platform Query Service](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=zh-Hant)

## 相關部落格貼文

* [[!DNL Content and Commerce AI: Personalizing Your Interactions with Customers Through Content Intelligence]](https://medium.com/adobetech/content-and-commerce-ai-personalizing-your-interactions-with-customers-through-content-intelligence-dc182601deab)
* [[!DNL An Introductory Look at Exploratory Data Analysis on Adobe Experience Platform]](https://medium.com/adobetech/an-introductory-look-at-exploratory-data-analysis-on-adobe-experience-platform-1bfce7501d9a)
* [[!DNL Cutting Across Adobe Experience Products with Machine Learning to Elevated User Experience]](https://medium.com/adobetech/cutting-across-adobe-experience-products-with-machine-learning-to-elevated-user-experience-7c85000510d1)
* [[!DNL Segmentation.AI: Automated Audience-Clustering-as-a-Service in Adobe Experience Platform]](https://medium.com/adobetech/segmentation-ai-automated-audience-clustering-as-a-service-in-adobe-experience-platform-261f4099462c)