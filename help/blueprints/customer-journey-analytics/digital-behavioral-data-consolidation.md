---
title: 數位行為資料整合藍圖
description: 分析客戶在整個客戶歷程中的互動並從中獲取見解。
solution: Experience Platform, Customer Journey Analytics, Data Collection
kt: 7208
exl-id: b042909c-d323-40d5-8b35-f3e5e3e26694
translation-type: tm+mt
source-git-commit: 844fff1cefe367575beb5c03aa0f0d026eb9f39b
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 0%

---

# 數位行為資料整合藍圖

透過統一各種網路、行動裝置和離線屬性的資料，以單一的整合檢視跨不同通道的客戶行為。

## 使用案例

* 分析案頭和行動裝置上的客戶互動，以瞭解客戶行為並獲取見解，以最佳化數位客戶體驗。
* 分析跨通道的客戶互動，包括數位和離線通道（例如支援互動和店內購買），以便更好地瞭解和最佳化客戶歷程。 

## 應用程式

* Adobe Experience Platform
* Customer Journey Analytics
* Adobe Analytics（可選）

## 整合模式

* Adobe Experience Platform→Customer Journey Analytics
* Adobe Analytics→Adobe Experience Platform→Customer Journey Analytics

## 建築

<img src="assets/CJA.svg" alt="Customer Journey Analytics藍圖的參考架構" style="border:1px solid #4a4a4a" />

## 瓜德賴爾

將資料擷取至Customer Journey Analytics:

* 資料擷取至湖泊：API ~ 7 GB/小時，源介面~ 200 GB/小時，流到湖的時間~ 15分鐘，Adobe Analytics源介面到湖的時間~ 45分鐘。
* 在資料發佈至資料湖後，最多需要90分鐘才能處理至Customer Journey Analytics。

## 實施步驟

1. 配置資料集和方案。
1. 將資料內嵌至平台。
資料必須先匯入平台，才能處理為Customer Journey Analytics。
1. 分析要聯合分析的跨通道事件資料集，以確定它們有共同的命名空間ID，或是透過基於欄位的Customer Journey Analytics拼接功能重新鍵入。 

   >[!NOTE]
   >
   >Customer Journey Analytics目前不使用Experience Platform設定檔或身分服務進行拼接。

1. 在資料上執行任何自訂資料準備或使用現場識別連結，以確保在時間系列資料集上有共同的索引鍵可吸收至Customer Journey Analytics。
1. 為查閱資料提供可連結至事件資料欄位的主要ID。 在授權中計算為列。
1. 設定描述檔資料的相同主要ID，作為事件資料的主要ID。
1. 設定資料連線，將資料從Experience Platform內嵌至Customer Journey Analytics。 資料進入資料湖後，90分鐘內就會處理至Customer Journey Analytics。
1. 在連線上設定資料檢視，以選取要包含在檢視中的特定維度和量度。 資料檢視中也會設定歸因和配置設定。 這些設定是在報告時計算。
1. 建立專案，在Analysis Workspace內設定控制面板和報表。

## 實作考量

### 身分聯繫考量事項

* 要統一的時間系列資料在每個記錄上都必須有相同的ID名稱空間。
* 統一不同資料集的聯合過程要求在資料集上使用共同的主要人員／實體密鑰。
* 目前不支援次要基於金鑰的聯盟。
* 基於欄位的身份拼接處理允許基於後續的瞬時ID記錄（如驗證ID）重新鍵入行中的身份。 這可讓您將分散的記錄解析為單一ID，以便在人員層級進行分析，而非在裝置或Cookie層級進行分析。
* 縫合每週進行一次，縫合後重播。

## 常見問答集

* 資料模型在Customer Journey Analytics中的下游影響是什麼？

   同一XDM欄位的對象和屬性在Customer Journey Analytics中合併為一個維。 至  將不同資料集的多個屬性合併到同一Customer Journey Analytics維中，資料集應引用相同的XDM欄位或模式。

## 相關檔案

* [Customer Journey Analytics產品說明](https://helpx.adobe.com/legal/product-descriptions/customer-journey-analytics.html)
* [Customer Journey Analytics檔案](https://experienceleague.adobe.com/docs/customer-journey-analytics.html)
* [Customer Journey Analytics教學課程](https://experienceleague.adobe.com/docs/customer-journey-analytics-learn/tutorials/overview.html)
