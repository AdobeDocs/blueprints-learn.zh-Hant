---
title: 已知客戶激活
description: 線上/離線對象啟用。
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7086
exl-id: 011f4909-b208-46db-ac1c-55b3671ee48c
source-git-commit: aba3bfcecac07cb51393fef9e6278d9d6af3e377
workflow-type: tm+mt
source-wordcount: '753'
ht-degree: 60%

---

# 已知客戶激活藍圖

使用離線屬性和事件，例如離線訂單、事務、CRM 或忠誠度資料，與線上行為一起進行線上目標定位和個人化。

擴展的具有內置治理控制的標識符提供了更多與已知客戶溝通的機會。 啟用對象至基於已知個人資料的目標，例如電子郵件供應商、社交網路及廣告目標。

其他詳細資料在[對象與個人資料啟用中提供，其中 Experience Cloud 應用程式 Blueprint](platform-and-applications.md) 特定於 Experience Platform 與 Experience Cloud 應用程式之間的互動。

## 使用案例

* 對社交及廣告目標上已知對象的對象目標定位。
* 使用線上和離線屬性的線上個人化。
* 啟用對象至已知通道，例如電子郵件和簡訊。

## 應用程式

* Adobe Experience Platform
* [!UICONTROL 即時客戶資料平台]

## 架構

### 使用目標進行聯機和離線資料激活

<img src="assets/online_offline_activation.svg" alt="線上/離線對象啟用 Blueprint 的參考架構" style="width:80%; border:1px solid #4a4a4a" />
<br>

## 護欄

[請參閱「對象與個人資料啟用」概觀頁面所述的護欄。](overview.md)

## 實施步驟

1. 為要擷取的資料[建立資料方案](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm)。
1. 為要擷取的資料[建立資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=zh-Hant)。
1. [在方案上設定正確的身份和身份命名空間](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=zh-Hant)，以確保擷取的資料可以嵌入統一的個人資料。
1. [為個人資料啟用方案和資料集](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=zh-Hant)。
1. [擷取資料](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion&amp;lang=zh-Hant)到 Experience Platform。
1. [在 Experience Platform 與 Audience Manager 之間為 Experience Platform 中定義要分享至 Audience Manager 的對象佈建[!UICONTROL 即時客戶資料平台]區段分享。](https://www.adobe.com/go/audiences)
1. 在 Experience Platform 中[建立區段](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=zh-Hant)。系統會自動確定區段是作為批次還是串流評估。
1. 將用於個人資料屬性和對象會籍分享的目標[設定為所需的目標。](https://experienceleague.adobe.com/docs/platform-learn/tutorials/destinations/create-destinations-and-activate-data.html?lang=zh-Hant)

## 實施考量

* 分享個人資料資料到目標需要您在目標負載中包含目標使用的特定身份值。對目標必要的任何身份必須擷取到 Platform，並且設定為[!UICONTROL 即時客戶個人資料]的身份。

### 從Real-time Customer Data Platform到Audience Manager的觀眾分享

* 一旦完成段評估並將其寫入即時客戶配置檔案（無論段評估是批處理還是流處理）,RT-CDP的受眾成員身份將以流方式共用到Audience Manager。 如果限定的簡檔包含相關簡檔設備的區域路由資訊，則RTCDP的觀眾成員在相關的Audience Manager邊緣上以流方式限定。 如果將區域路由資訊應用於過去14天內時間戳記的配置檔案，則將在Audience Manager邊緣上以流形式進行計算。 如果RTCDP中的配置檔案不包含區域路由資訊或區域路由資訊大於14天，則配置檔案成員資格將發送到Audience Manager中心位置以進行基於批的評估和激活。 符合邊緣激活資格的配置檔案將在RTCDP的細分市場鑑定後幾分鐘內激活，不符合邊緣激活資格的配置檔案將在Audience Manager集線器中獲得資格，並且可能有12-24小時的處理時間。

* 可以從Audience Manager、訪問者ID服務、分析、啟動或直接從Web SDK中收集儲存了Audience Manager配置檔案的邊緣區域路由資訊，以便使用「資料捕獲區域資訊」 XDM欄位組作為單獨的配置檔案記錄類資料集進行Experience Platform。

* 對於從Experience Platform到Audience Manager的受眾共用的激活情形，將自動共用以下標識：IDFA、GAID、AdCloud、Google、ECID、EMAIL_LC_SHA256。 當前，未共用自定義命名空間。

當所需的目標身份包含在[!UICONTROL 即時客戶個人資料]中時，或者[!UICONTROL 即時客戶個人資料]中的身份可以關聯至 Audience Manager 中連結的所需目標身份時，Experience Platform 中的對象可透過 Audience Manager 目標分享。

## 相關文件

* [[!UICONTROL 即時客戶資料平台]產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/real-time-customer-data-platform.html)
* [個人資料與細分準則](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hant)
* [細分文件](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=zh-Hant)
* [目標文件](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=zh-Hant)

## 相關視訊與教學課程

* [[!UICONTROL 即時客戶資料平台]概覽](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=zh-Hant)
* [[!UICONTROL 即時客戶資料平台]示範](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=zh-Hant)
* [建立區段](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html)
