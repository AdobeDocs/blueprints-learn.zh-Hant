---
title: 描述檔擴充藍圖的自訂資料科學
description: 此藍圖說明Adobe Experience Platform的資料科學工作區如何使用Experience Platform內的資料來訓練、部署及評分模型，以從資料中提供機器學習見解。
solution: Experience Platform, Data Collection
kt: 7203
translation-type: tm+mt
source-git-commit: e1a9881996a181310bdc32cb083e4c5654139bf0
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 0%

---


# 描述檔擴充藍圖的自訂資料科學

此藍圖顯示資料科學工作區如何使用Adobe Experience Platform的資料來訓練、部署和評分模型，以提供機器學習見解。 這些模型可直接輸出至啟用即時客戶個人檔案的資料集。 機器學習深入資訊的範例包括終身價值、產品與類別相似性、轉換傾向或流失傾向。

## 使用案例

* 從Experience Platform中的客戶資料擷取見解並探索模式。 從這些資料中訓練和評分模型。
* 利用模型導向的見解和屬性豐富即時客戶個人檔案，以便更精細的個人化和最佳化歷程。
* 訓練和分數模型，以判斷客戶見解，例如客戶終身價值、轉換或流失傾向、產品與內容相關性，以及參與分數。

## 藍本

| 藍本 | 方案說明 | Experience Cloud應用程式 |
|---|---|---|
| 探索性資料科學 | <ul><li>發現信號、完整性、資料正確性</li><li>使用資料科學工具發掘新見解</li></ul> | <ul><li>Experience Platform智慧</li></ul> |
| 使用AI/ML<br>擴充描述檔——批次 | <ul><li>發現、製作、訓練、部署、評分和操作模型。</li><li>將模型預測推播至描述檔或資料湖，以進行批次啟動。</li></ul> | <ul><li>Experience Platform智慧</li></ul> |

## 建築

<img src="assets/datascience.svg" alt="基於定制資料科學的輪廓富集藍圖參考體系結構" style="border:1px solid #4a4a4a" />

## 實施步驟

1. 建立結構描述和資料集。
1. 將資料內嵌至Experience Platform。
1. 建立DSW筆記本。
1. 選擇語言。 支援Python和PySpark。
1. 在筆記型電腦中製作模型。
1. 訓練模型。
1. 對模型進行分數，以便使用目標資料產生預測。
1. 如果將模型結果推送至即時客戶描述檔，請啟用描述檔的模型結果資料集。

## 相關檔案

* [Adobe Experience Platform智慧產品說明](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [Data Science Workspace檔案](https://experienceleague.adobe.com/docs/experience-platform/data-science-workspace/home.html?lang=en)
* [資料科學工作區教學課程](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-science-workspace/understanding-data-science-workspace.html)

## 相關部落格文章

* [使用Adobe平台體驗簡化資料科學生命週期](https://medium.com/adobetech/simplifying-the-data-science-lifecycle-with-adobe-platform-experience-8ea4f056d82f)
* [內容與商務AI:透過內容智慧個人化您與客戶的互動](https://medium.com/adobetech/content-and-commerce-ai-personalizing-your-interactions-with-customers-through-content-intelligence-dc182601deab)
* [使用資料科學工作區深入瞭解客戶流失](https://medium.com/adobetech/gaining-a-deeper-understanding-of-churn-using-data-science-workspace-18a2190e0cf3)
* [理解Adobe Experience Platform的資料科學](https://medium.com/adobetech/understanding-data-science-in-adobe-experience-platform-5bce5a17b42)
* [Adobe Experience Platform探索性資料分析初探](https://medium.com/adobetech/an-introductory-look-at-exploratory-data-analysis-on-adobe-experience-platform-1bfce7501d9a)
* [運用機器學習跨Adobe體驗產品提升使用體驗](https://medium.com/adobetech/cutting-across-adobe-experience-products-with-machine-learning-to-elevated-user-experience-7c85000510d1)
* [在Adobe Experience Platform大規模資料科學中建模XDM資料](https://medium.com/adobetech/modeling-xdm-data-for-data-science-at-scale-on-adobe-experience-platform-222bb2a6dbf7)
* [Segmentation.AI:Adobe Experience Platform的自動化受眾群集服務](https://medium.com/adobetech/segmentation-ai-automated-audience-clustering-as-a-service-in-adobe-experience-platform-261f4099462c)
* [重新想像Jupyter筆記本企業規模](https://medium.com/adobetech/reimagining-jupyter-notebooks-for-enterprise-scale-8bc6340d504a)
* [利用Adobe Experience Platform資料科學工作區加速智慧洞察](https://medium.com/adobetech/accelerate-intelligent-insights-with-adobe-experience-platform-data-science-workspace-89538bacbbea)
* [時間序列預測的Adobe Experience Platform預測](https://medium.com/adobetech/preview-of-time-series-forecasting-with-adobe-experience-platform-38a2fc778e89)
* [運用機器學習跨Adobe體驗產品提升使用體驗](https://medium.com/adobetech/cutting-across-adobe-experience-products-with-machine-learning-to-elevated-user-experience-7c85000510d1)

