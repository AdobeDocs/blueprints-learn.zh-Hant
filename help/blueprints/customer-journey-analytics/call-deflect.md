---
title: 呼叫偏轉分析藍圖
description: 在客戶聯絡呼叫中心之前分析客戶行為。
solution: Experience Platform, Customer Journey Analytics
kt: 7209
exl-id: 13593c1c-4c58-4b8a-aa6c-7530fd679a14
translation-type: tm+mt
source-git-commit: 6365fa00a77ba22774b2d6de3e882a3e09dcae0f
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 92%

---

# 呼叫偏轉歷程分析藍圖

在客戶聯絡呼叫中心之前分析客戶在桌面和行動裝置上的行為。瞭解您的客戶嘗試完成哪些操作、他們查看什麼內容以及在聯絡客戶支援之前搜尋哪些詞語，以發現改善客戶歷程的機會。確定可以改善的內容和自助服務工具，以協助您的客戶不需要致電而自行解決問題。

## 使用案例

* 在客戶聯絡支援之前分析客戶行為
* 探索改善自助服務能力的機會

## 應用程式

* Adobe Experience Platform
* Customer Journey Analytics

## 整合模式

* Adobe Experience Platform → Customer Journey Analytics

## 架構

<img src="assets/CJA.svg" alt="Customer Journey Analytics Blueprint 的參考架構" style="border:1px solid #4a4a4a" />

## 實施步驟

1. [建立](https://experienceleague.adobe.com/docs/platform-learn/tutorials/schemas/create-a-schema.html) 要收錄的資料架構。
1. [建立](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html) 要收錄的資料資料集。
1. [將資料內嵌至平台](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion)。資料在擷取到 Customer Journey Analytics 之前，必須先擷取到 Platform。
1. 分析跨通道事件資料集。
聯合分析的資料集必須具有公共的命名空間 ID，或者透過 Customer Journey Analytics 基於欄位的功能重建索引鍵。 

   >[!NOTE]
   >
   >Customer Journey Analytics 目前不使用 Experience Platform Profile 或 Identity 服務進行接合。

1. 執行任何自訂資料準備或對資料使用基於欄位的身份接合，以確保時間序列資料集中的公用鍵擷取到 Customer Journey Analytics。
1. 提供查詢資料的主要 ID，可以加入事件資料中的欄位。在授權中計算為列。
1. 將個人資料的同一主要 ID 設定為事件資料的主要 ID。
1. 設定資料連接以將資料從 Experience Platform 擷取到 Customer Journey Analytics。在資料進入資料湖後，將在 90 分鐘內處理到 Customer Journey Analytics。
1. 設定連接的資料視圖以選擇要納入視圖中的特定維度與指標。屬性與分配設定亦會在資料視圖中設定。這些設定在報告時計算。
1. 建立專案以在 Analysis Workspace 中設定儀表板和報告。

## 實施考量

### 身份接合考量

* 要聯合的時間序列資料必須在每條記錄上具有相同的 ID 命名空間。要將所有呼叫中心資料連接到匿名裝置資料，數位 ID 必須連接到呼叫 ID。此輸入可透過多種可能的機制進行：
   * 撥入號碼是該訪客在該時間的唯一撥入號碼，結合查詢表一起追蹤關係。
   * 要求使用者在請求支援之前進行驗證，並且將此驗證關聯至呼叫代理確定的識別號 (例如電話號碼或電子郵件地址)。
   * 使用引導合作夥伴協助鍵入線上裝置識別號，將已知的識別號關聯至支援請求。
* 聯合不同資料集的過程需要所有資料集具有一個公共的主要人員/實體鍵。
* 基於次要鍵的聯合目前不受支援。
* 基於欄位的身份接合過程允許根據後續暫時 ID 記錄 (如驗證 ID) 對列中的身份重建索引鍵。此過程允許不同的記錄使用一個 ID，以便在個人級別分析，而不是在裝置或 cookie 級別分析。
* 接合每週進行一次，並在接合後重播。

## 常見問題

* Customer Journey Analytics 中的資料模型對下游有何影響？

   同一 XDM 欄位的物件與屬性在 Customer Journey Analytics 中合併成一個維度。若要將不同資料集中的多個屬性合併成同一個 CJA 維度，資料集應參考同一個 XDM 欄位或方案。

## 相關文件

* [Customer Journey Analytics 產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/customer-journey-analytics.html)
* [Customer Journey Analytics 文件](https://experienceleague.adobe.com/docs/customer-journey-analytics.html?lang=zh-Hant)
* [Customer Journey Analytics 教學課程](https://experienceleague.adobe.com/docs/customer-journey-analytics-learn/tutorials/overview.html?lang=zh-Hant)
