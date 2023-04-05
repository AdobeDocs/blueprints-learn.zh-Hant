---
title: Customer Journey Analytics藍圖
description: 統一並分析客戶歷程中的資料與客戶行為
solution: Customer Journey Analytics
kt: null
thumbnail: null
exl-id: 3bb2dada-f4cd-43f7-a0d0-f276510ad224
source-git-commit: dabb5ae0bf2fc186f67d4aa93a2e9e8c5bb04498
workflow-type: ht
source-wordcount: '406'
ht-degree: 100%

---

# Customer Journey Analytics藍圖

Customer Journey Analytics 顯示品牌如何統一各個互動通道及來源的客戶資料與行為，以為所有客戶互動建立基於歷程的視圖。可在 Customer Journey Analytics 應用程式服務中執行報告與分析，以評估和洞察客戶互動及行為模式。

如需 Customer Journey Analytics 使用案例的完整清單，請參閱此處的 Customer Journey Analytics 文件。

## Customer Journey Analytics 使用案例

[常見使用案例](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/cja-usecases.html?lang=zh-Hant)包括：

* 建立對象並發佈至 Real-time Customer Data Platform
* 頂端 / 底部轉換路徑
* 通道參與和轉換
* 最熱門的內容
* 頂級類別和產品
* 哪些行銷活動促成了轉換及參與度的提升
* 工具使用分析以最佳化自助服務體驗

## Customer Journey Analytics 架構

![架構圖](assets/CJA.svg){zoomable=&quot;yes&quot;}

主要使用案例範例包括下列。
| 藍圖 | 說明 | Experience Cloud 應用程式 |
|---|---|---|
| **[跨通道歷程分析](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/cross-channel/cross-channel.html?lang=zh-Hant)**  | <ul><li>統一來自不同網路、行動裝置及線上內容的資料，為各個通道建立單一整合的客戶行為視圖。</li></ul> | <ul><li>Adobe Experience Platform</li><li>Customer Journey Analytics</li><li>Adobe Analytics (可選)</li></ul>|
| **[將對象發佈至 Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html?lang=zh-Hant)** | <ul><li>在 Customer Journey Analytics(CJA) 中建立識別的對象，並將其發佈至 Adobe Experience Platform 中的 Real-time Customer Profile，以便鎖定客戶並個人化。非常適合使用歷史資料建立對象，或透過精細篩選和運算欄位建立更完善的對象(Customer Journey Analytics)。</li></ul> | <ul><li>Real-time Customer Data Platform</li><li>Customer Journey Analytics</li> |
| **[呼叫改向歷程分析](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/cross-channel/call-center.html?lang=zh-Hant)** | <ul><li>整合呼叫中心資料與網路、行動裝置及其他互動資料，確定哪些行為對產生代理協助的呼叫最有意義。</li><li>接著可將這些深入見解用於最佳化客戶體驗，透過最佳化的自助服務內容與工具縮短代理協助的互動路徑。  </li></ul> | <ul><li>Adobe Experience Platform</li><li>Customer Journey Analytics</li> |

## Customer Journey Analytics 藍圖的護欄圖

* 有關詳細的護欄和端到端延遲，請參閱[部署護欄文件](../experience-platform/deployment/guardrails.md)

![護欄圖](../experience-platform/assets/CJA_guardrails.svg){zoomable=&quot;yes&quot;}

## 相關部落格貼文

* [[!DNL Blueprint for Multi-Channel Orchestration in Adobe Experience Platform]](https://medium.com/adobetech/blueprint-for-multi-channel-orchestration-in-adobe-experience-platform-c68317e94184){target="_blank"}
* [[!DNL Leveraging External Data Platforms in Adobe Experience Platform Journey Orchestration]](https://medium.com/adobetech/leveraging-external-data-platforms-in-adobe-experience-platform-journey-orchestration-54fc6134fe17){target="_blank"}
* [[!DNL Event-Based Triggering on Adobe Experience Platform Orchestration Service using Apache Airflow]](https://medium.com/adobetech/event-based-triggering-on-adobe-experience-platform-orchestration-service-using-apache-airflow-8607b28251f1){target="_blank"}
* [[!DNL Adobe Campaign Classic Integration with Journey Orchestration]](https://medium.com/adobetech/adobe-campaign-classic-integration-with-journey-orchestration-ae577653281){target="_blank"}
* [[!DNL Demonstrating the Power of Adobe's New Journey Orchestration Service to Build Personalized Omnichannel Experiences in Real-Time]](https://medium.com/adobetech/demonstrating-the-power-of-adobes-new-journey-orchestration-service-to-build-personalized-aa60d88cd34){target="_blank"}
* [[!DNL Journey Orchestration in an Omnichannel World]](https://medium.com/adobetech/journey-orchestration-in-an-omnichannel-world-3a2d32d556d9){target="_blank"}
