---
title: 自訂 Profile Enrichment 藍圖的資料科學
description: 此藍圖顯示 Adobe Experience Platform 的 Data Science Workspace 如何使用 Experience Platform 中的資料訓練、部署及評分模型，以從資料中獲取機器學習深入見解。
solution: Data Collection
kt: 7203
exl-id: e5ec6886-4fa4-4c9b-a2d8-e843d7758669,f0efaf3c-6c4f-47c3-ab8a-e8e146dd071c
source-git-commit: 011f5b247ccd606348b4cbb4210218f28eddbd4c
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 68%

---

# 自訂 Profile Enrichment 藍圖的資料科學

定制資料科學用於配置檔案濃縮藍圖說明了如何使用Adobe Experience Platform的資料來訓練、部署和評分模型，從而從資料科學和機器學習工具中提供機器學習對Experience Platform和Real-time Customer Data Platform的洞見。 模型化的洞察能夠被引入Experience Platform，以豐富即時客戶概況。 機器學習深入見解的範例包括期限值評分、產品和類別親和性、轉換傾向性或退訂傾向性。

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

## 相關文件

* [Adobe Experience Platform Intelligence 產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [Adobe Experience Platform查詢服務](https://experienceleague.adobe.com/docs/experience-platform/query/home.html)

## 相關部落格貼文

* [[!DNL Content and Commerce AI: Personalizing Your Interactions with Customers Through Content Intelligence]](https://medium.com/adobetech/content-and-commerce-ai-personalizing-your-interactions-with-customers-through-content-intelligence-dc182601deab)
* [[!DNL An Introductory Look at Exploratory Data Analysis on Adobe Experience Platform]](https://medium.com/adobetech/an-introductory-look-at-exploratory-data-analysis-on-adobe-experience-platform-1bfce7501d9a)
* [[!DNL Cutting Across Adobe Experience Products with Machine Learning to Elevated User Experience]](https://medium.com/adobetech/cutting-across-adobe-experience-products-with-machine-learning-to-elevated-user-experience-7c85000510d1)
* [[!DNL Segmentation.AI: Automated Audience-Clustering-as-a-Service in Adobe Experience Platform]](https://medium.com/adobetech/segmentation-ai-automated-audience-clustering-as-a-service-in-adobe-experience-platform-261f4099462c)