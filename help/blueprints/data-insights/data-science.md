---
title: 自訂 Profile Enrichment 藍圖的資料科學
description: 此藍圖顯示了如何將基於資料科學的見解引入Experience Platform以豐富即時客戶概要資訊。
solution: Data Collection
kt: 7203
exl-id: e5ec6886-4fa4-4c9b-a2d8-e843d7758669,f0efaf3c-6c4f-47c3-ab8a-e8e146dd071c
source-git-commit: 6d44401fba8cc75402d4303825e32e7948753449
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 45%

---

# 自訂 Profile Enrichment 藍圖的資料科學

定制資料科學用於配置檔案濃縮藍圖說明了如何使用資料來訓練、部署和評分模型，從而從資料科學和機器學習工具提供機器學習對Experience Platform和Real-time Customer Data Platform的洞見。 模型化的洞察能夠被引入Experience Platform，以豐富即時客戶概況。 機器學習深入見解的範例包括期限值評分、產品和類別親和性、轉換傾向性或退訂傾向性。

## 使用案例

* 從客戶資料中提取洞察力和發現模式，從此資料中訓練和評分模型。
* 使用模型驅動的深入見解和屬性豐富的[!UICONTROL 即時客戶個人資料]，以進行更細緻的個人化和最佳的歷程最佳化。
* 對模型訓練和評分以確定客戶深入見解，例如客戶期限值、轉換或退訂傾向性、產品和內容相似性及參與分數。

## 架構

<img src="assets/data_science.svg" alt="為豐富個人資料自訂資料科學 Blueprint 的參考架構" style="width:90%; border:1px solid #4a4a4a" />

## 實施步驟

1. 為要擷取的資料[建立資料方案](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm)。
1. 為要擷取的資料[建立資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=zh-Hant)。
1. [擷取資料](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=zh-Hant)到 Experience Platform。

要將模型結果導入即時客戶概要檔案，請確保在接收資料之前執行以下操作：

1. [在方案上設定正確的身份和身份命名空間](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hant)，以確保擷取的資料可以嵌入統一的個人資料。
1. [為個人資料啟用方案和資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=zh-Hant)。

## 實施考量

* 在大多數情況下，模型結果應被作為配置檔案屬性而不是體驗事件來接收。 模型結果可以是簡單的屬性字串。 如果要接收多個模型結果，建議使用陣列或映射類型欄位。
* 可利用作為統一配置檔案屬性資料的每日導出的每日配置檔案快照資料集來訓練關於配置檔案屬性資料的模型。 可以訪問配置檔案快照資料集文檔 [這裡](https://experienceleague.adobe.com/docs/experience-platform/dashboards/query.html#profile-attribute-datasets)。
* 為從Experience Platform中提取資料，可使用以下方法
   * 資料存取SDK
      * 資料以原始檔案形式
      * 配置檔案體驗事件資料仍處於未統一的原始狀態。
   * RTCDP目標
      * 可以對配置檔案屬性和段成員身份進行表述。

## 相關文件

* [Adobe Experience Platform Intelligence 產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [Adobe Experience Platform查詢服務](https://experienceleague.adobe.com/docs/experience-platform/query/home.html)

## 相關部落格貼文

* [[!DNL Content and Commerce AI: Personalizing Your Interactions with Customers Through Content Intelligence]](https://medium.com/adobetech/content-and-commerce-ai-personalizing-your-interactions-with-customers-through-content-intelligence-dc182601deab)
* [[!DNL An Introductory Look at Exploratory Data Analysis on Adobe Experience Platform]](https://medium.com/adobetech/an-introductory-look-at-exploratory-data-analysis-on-adobe-experience-platform-1bfce7501d9a)
* [[!DNL Cutting Across Adobe Experience Products with Machine Learning to Elevated User Experience]](https://medium.com/adobetech/cutting-across-adobe-experience-products-with-machine-learning-to-elevated-user-experience-7c85000510d1)
* [[!DNL Segmentation.AI: Automated Audience-Clustering-as-a-Service in Adobe Experience Platform]](https://medium.com/adobetech/segmentation-ai-automated-audience-clustering-as-a-service-in-adobe-experience-platform-261f4099462c)