---
title: 呼叫偏轉分析藍圖
description: 在客戶聯絡客服中心之前，先分析客戶行為。
solution: Experience Platform, Customer Journey Analytics
kt: 7209
exl-id: 13593c1c-4c58-4b8a-aa6c-7530fd679a14
translation-type: tm+mt
source-git-commit: 844fff1cefe367575beb5c03aa0f0d026eb9f39b
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 0%

---

# 呼叫偏轉歷程分析藍圖

在客戶聯絡客服中心之前，先分析客戶在桌上型電腦和行動裝置上的行為。 瞭解客戶在聯絡客戶支援之前要完成哪些動作、檢視哪些內容，以及搜尋哪些詞語，借此找出改善客戶歷程的機會。 確定可加以改進的內容和自助服務工具，以協助客戶解決問題，而不需來電。

## 使用案例

* 在客戶聯絡支援前分析客戶行為
* 發現改善自助服務功能的機會

## 應用程式

* Adobe Experience Platform
* Customer Journey Analytics

## 整合模式

* Adobe Experience Platform→Customer Journey Analytics

## 建築

<img src="assets/CJA.svg" alt="Customer Journey Analytics藍圖的參考架構" style="border:1px solid #4a4a4a" />

## 瓜德賴爾

將資料擷取至Customer Journey Analytics:

* 資料擷取至湖泊：API ~ 7 GB/小時，源介面~ 200 GB/小時，流到湖的時間~ 15分鐘，Analytics源介面到湖的時間~ 45分鐘。
* 在資料發佈至資料湖後，最多需要90分鐘才能處理至Customer Journey Analytics。

## 實施步驟

1. 配置資料集和方案。
1. 將資料內嵌至平台。
資料必須先擷取到平台中，才能擷取到Customer Journey Analytics。
1. 分析跨通道事件資料集。
聯合分析的資料集必須具有通用的命名空間ID，或通過基於欄位的Customer Journey Analytics拼接功能重新鍵入。 

   >[!NOTE]
   >
   >Customer Journey Analytics目前不使用Experience Platform設定檔或身分服務進行拼接。

1. 在資料上執行任何自訂資料準備或使用現場識別連結，以確保將時間序列資料集上的共用索引鍵內嵌在Customer Journey Analytics中。
1. 提供查閱資料的主要ID，可連結至事件資料中的欄位。 在授權中計算為列。
1. 設定描述檔資料的主要ID與事件資料的主要ID相同。
1. 設定資料連線，將資料從Experience Platform內嵌至Customer Journey Analytics。 資料進入資料湖後，90分鐘內就會處理至Customer Journey Analytics。
1. 在連線上設定資料檢視，以選取要包含在檢視中的特定維度和量度。 資料檢視中也會設定歸因和配置設定。 這些設定是在報告時計算。
1. 建立專案，在Analysis Workspace內設定控制面板和報表。

## 實作考量

### 身分聯繫考量事項

* 要統一的時間系列資料在每個記錄上都必須有相同的ID名稱空間。 若要將呼叫中心資料連接至匿名裝置資料，數位ID必須系結至呼叫ID。 這種束縛可以通過幾種可能的機制實現：
   * 撥號號碼是該訪客在該時間的唯一撥號號碼，以及追蹤關係的查閱表格。
   * 要求用戶在請求支援之前進行驗證，並將此驗證與由呼叫代理確定的標識符（例如，電話號碼或電子郵件）關聯。
   * 使用入門合作夥伴協助輸入線上裝置識別碼，其中已知識別碼會系結至支援要求。
* 統一不同資料集的聯合過程要求在資料集上使用共同的主要人員／實體密鑰。
* 目前不支援次要基於金鑰的聯盟。
* 基於欄位的身份拼接處理允許基於後續的瞬時ID記錄（如驗證ID）重新鍵入行中的身份。 此程式可將分散的記錄解析為單一ID，以便在人員層級進行分析，而非在裝置或Cookie層級分析。
* 縫合每週進行一次，縫合後重播。

## 常見問答集

* 資料模型在Customer Journey Analytics中的下游影響是什麼？

   同一XDM欄位的對象和屬性在Customer Journey Analytics中合併為一個維。 要將不同資料集的多個屬性合併到同一CJA維中，資料集應引用相同的XDM欄位或模式。

## 相關檔案

* [Customer Journey Analytics產品說明](https://helpx.adobe.com/legal/product-descriptions/customer-journey-analytics.html)
* [Customer Journey Analytics檔案](https://experienceleague.adobe.com/docs/customer-journey-analytics.html)
* [Customer Journey Analytics教學課程](https://experienceleague.adobe.com/docs/customer-journey-analytics-learn/tutorials/overview.html)
