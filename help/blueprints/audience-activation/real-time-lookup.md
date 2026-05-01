---
title: 適用於Web和Mobile Personalization的即時Edge設定檔存取
description: 在邊緣[!UICONTROL 即時客戶個人檔案]存取權，以提供即時網頁和行動個人化的內容。
solution: Real-Time Customer Data Platform, Data Collection
kt: 719
exl-id: 61b81d00-c4bd-41b2-8161-683814947b56
TQID: https://experienceleague.adobe.com/H59c3UBbNCQFs3H0VL5iVDKKZ5D3CFt4ri2RVwNlq7s
product_v2:
  - id: fdddec33-c9cb-4459-b8b6-2664395a6f10
feature_v2:
  - id: ba929a52-9339-4154-9487-317dc875a3c7
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
  - id: c4147b6e-073b-4d3c-9ab1-d60f2f4434ef
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: d3cdead0-685a-4489-9250-4bb709942f66
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
  - id: fd2e3797-f2ea-4b36-a9af-52acf5e90513
source-git-commit: 95ba7aa681e67efb136adac15dc7894cb413a4f0
workflow-type: tm+mt
source-wordcount: 631
ht-degree: 8%

---

# 適用於Web和Mobile Personalization的即時Edge設定檔存取

>[!TIP]
>此Blueprint也可作為Personalization下的[使用案例模式](/help/blueprints/use-case-patterns/personalization/edge-profile-access.md)。

適用於Web和Mobile Personalization藍圖的即時Edge設定檔存取顯示，Web和行動應用程式如何在Edge存取Adobe Experience Platform的[!UICONTROL 即時客戶設定檔]，以進行高輸送量、低延遲的個人化。

應用程式能以毫秒的延遲存取即時設定檔屬性和邊緣的對象。 在設定檔中儲存屬性、對象會籍和模型導向功能（作為屬性），可跨網頁和行動裝置頻道即時存取以進行相同頁面和下一頁個人化。

透過此功能，您可以根據即時客戶個人檔案，在您的網站和行動應用程式上提供高度個人化的體驗，包括從即時行為、擷取到即時客戶個人檔案中的屬性以及計算的深入分析衍生的受眾。

>[!NOTE]
>
>Edge設定檔存取專門針對高輸送量、低延遲的使用案例，例如網頁/行動傳入個人化和即時優惠決定。 若為低輸送量的案例（例如代理商協助支援或銷售互動），則中心設定檔查詢API較為合適。 檢視[支援和銷售案例的即時設定檔存取](customer-activity.md)，以取得中心設定檔存取權。

## 應用程式

* Real-time Customer Data Platform
* Adobe Experience Platform資料收集（網頁SDK /行動SDK）
* Edge Network伺服器API

## 使用案例

* 針對已知客戶體驗在網頁和行動裝置頻道上即時個人化
* 根據即時設定檔屬性和對象的相同頁面和下一頁個人化
* 根據客戶個人檔案（包括即時行為資料、屬性和計算的深入分析）進行內容和選件個人化
* 與個人化引擎、內容管理系統及外部應用程式整合，用於即時決策
* 使用即時設定檔內容進行測試和內容最佳化

## 架構圖

<img src="assets/real-time-edge-lookup.svg" alt="適用於Web和Mobile Personalization的Edge設定檔存取參考架構" style="width:90%; border:1px solid #4a4a4a"  class="modal-image" />

## 護欄

* [[!UICONTROL 即時客戶設定檔]資料的護欄](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hant)
* [Edge Network護欄](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/guardrails.html)
* Edge設定檔具有14天的存留時間(TTL)。 如果使用者未在Edge上活動14天，Edge設定檔可能會過期，且需要從中心擷取，這可能會影響第一頁個人化。
* Edge個人化支援對符合邊緣細分條件的對象進行即時對象成員資格評估。 透過適當的設定，也可從邊緣取得批次和來自集線器的串流對象。

## 相關文件

### 目的地設定

* [自訂Personalization連線](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/custom-personalization) — 主要實作指南
* [Personalization目的地概觀](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/overview)
* [啟用對象以邊緣個人化目的地](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations)
* [即時查詢邊緣上的設定檔屬性](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-edge-profile-lookup)

### SDK 檔案

* [Experience Platform Web SDK檔案](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/home.html)
* [Experience Platform Mobile SDK檔案](https://developer.adobe.com/client-sdks/home/)
* [Edge Network伺服器API檔案](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=zh-Hant)
* [Experience Platform標籤檔案](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=zh-Hant)
* [Web SDK中的命令回應](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/commands/command-responses.html)

### 設定檔和分段檔案

* [[!UICONTROL 即時客戶個人檔案]檔案](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html)
* [設定檔護欄](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hant)

### 教學課程

* [使用Real-Time CDP和Adobe Target進行下一次點選個人化](https://experienceleague.adobe.com/docs/platform-learn/tutorials/experience-cloud/next-hit-personalization.html)
* [資料流設定](https://experienceleague.adobe.com/docs/experience-platform/datastreams/configure.html)
