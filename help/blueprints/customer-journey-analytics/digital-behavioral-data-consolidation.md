---
title: 跨通道歷程分析
description: 分析整個客戶歷程中的客戶互動並從中擷取深入見解。
solution: Experience Platform, Customer Journey Analytics, Data Collection
kt: 7208
exl-id: b042909c-d323-40d5-8b35-f3e5e3e26694
translation-type: tm+mt
source-git-commit: 58368eb06b9bbd6c332424bdcfa2789dde7d4c2f
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 98%

---

# 跨通道歷程分析藍圖

統一來自不同網路、行動裝置及線上內容的資料，為各個通道建立單一整合的客戶行為視圖。

## 使用案例

* 分析桌上型裝置與行動裝置上的客戶互動，以瞭解客戶行為並擷取深入見解，以最佳化數位客戶體驗。
* 分析各通道中的客戶互動，包括數位與離線通道，例如支援互動與店內購買，以更好地瞭解並最佳化客戶歷程。 

## 應用程式

* Adobe Experience Platform
* Customer Journey Analytics
* Adobe Analytics (可選)

## 整合模式

* Adobe Experience Platform → Customer Journey Analytics
* Adobe Analytics → Adobe Experience Platform → Customer Journey Analytics

## 架構

<img src="assets/CJA.svg" alt="Customer Journey Analytics Blueprint 的參考架構" style="border:1px solid #4a4a4a" />

## 實施步驟

1. 設定資料集與方案。
1. 擷取資料至 Platform。資料在處理到 Customer Journey Analytics 之前，必須先擷取到 Platform。
1. 分析要統一分析的跨通道事件資料集，以確保它們具有共同的命名空間 ID，或者透過 Customer Journey Analytics 基於欄位的結合功能重建索引鍵。 

   >[!NOTE]
   >
   >Customer Journey Analytics 目前不使用 Experience Platform Profile 或 Identity 服務進行接合。

1. 執行任何自訂資料準備或對資料使用基於欄位的身份接合，以確保時間序列資料集的公用鍵擷取到 Customer Journey Analytics。
1. 為查詢資料提供一個可以加入事件資料中某個欄位的主要 ID。在授權中計算為列。
1. 將個人資料的同一主要 ID 設定為事件資料的主要 ID。
1. 設定資料連接以將資料從 Experience Platform 擷取到 Customer Journey Analytics。在資料進入資料湖後，將在 90 分鐘內處理到 Customer Journey Analytics。
1. 設定連接的資料視圖以選擇要納入視圖中的特定維度與指標。屬性與分配設定亦會在資料視圖中設定。這些設定在報告時計算。
1. 建立專案以在 Analysis Workspace 中設定儀表板和報告。

## 實施考量

### 身份接合考量

* 要聯合的時間序列資料必須在每條記錄上具有相同的 ID 命名空間。
* 聯合不同資料集的過程需要所有資料集具有一個公共的主要人員/實體鍵。
* 基於次要鍵的聯合目前不受支援。
* 基於欄位的身份接合過程允許根據後續暫時 ID 記錄 (如驗證 ID) 對列中的身份重建索引鍵。這允許不同的記錄使用單一 ID，以便在個人層級分析，而非在裝置或 cookie 層級分析。
* 接合每週進行一次，並在接合後重播。

## 常見問題

* Customer Journey Analytics 中的資料模型對下游有何影響？

   同一 XDM 欄位的物件與屬性在 Customer Journey Analytics 中合併成一個維度。若要將不同資料集中的多個屬性合併成同一個 Customer Journey Analytics 維度，資料集應參考同一個 XDM 欄位或方案。

## 相關文件

* [Customer Journey Analytics 產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/customer-journey-analytics.html)
* [Customer Journey Analytics 文件](https://experienceleague.adobe.com/docs/customer-journey-analytics.html?lang=zh-Hant)
* [Customer Journey Analytics 教學課程](https://experienceleague.adobe.com/docs/customer-journey-analytics-learn/tutorials/overview.html?lang=zh-Hant)
