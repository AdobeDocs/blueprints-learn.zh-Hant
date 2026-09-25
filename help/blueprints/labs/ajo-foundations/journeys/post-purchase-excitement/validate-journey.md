---
title: 驗證歷程
description: 透過登入和退出計數、電子郵件傳遞報告以及步驟事件的查詢服務資料來驗證歷程執行。
doc-type: article
solution: Experience Platform
exl-id: 2e6e73e5-6bd8-4dde-ba06-29b67f927131
source-git-commit: 96308d5726def849ef22540a5d13618017c40cc3
workflow-type: tm+mt
source-wordcount: '527'
ht-degree: 0%
---

# 驗證歷程

## 學習目標

確認歷程已觸發並按預期執行。  驗證報表顯示如預期更新的量度。

## 檢查您的歷程

1. 移至「訂單送貨歷程」，如果關閉則開啟
2. 您至少看到輸入了2個設定檔

   為歷程顯示的![設定檔輸入計數](assets/validate-journey-profile-entered-count.png)

3. 按一下右上角的&#x200B;**檢視報告** -> **過去24小時**。
4. 依預設，您位於&#x200B;**歷程**&#x200B;索引標籤（位於左側欄）
   - 您會看到部分進入和退出（計數將取決於您傳入的事件數、任何測試、任何錯誤等）

![顯示進入和結束的歷程索引標籤報告](assets/validate-journey-journey-tab-enters-exits.png)

如果一切準備就緒，您可以（向下捲動以檢查）：

**歷程的統計資料**

3已進入設定檔（Henry、You以及我們進行的測試）

您可以按一下頂端的切換按鈕，讓&#x200B;**排除測試事件** （如果您想要的話），而且您會看到這些數字變更

3個已退出的設定檔（Henry、You以及我們執行的測試）

**已執行的動作和錯誤**

6個動作（3封電子郵件、3個GetShippingDetails）

**動作錯誤原因**

0個錯誤（希望）

**個活動**

3個事件(orderShipped)

3個外部事件

1. 按一下&#x200B;**電子郵件**&#x200B;標籤（在左側邊欄上）
   - **電子郵件 — 傳送效能**
     - 您看到&#x200B;**已傳遞**&#x200B;及&#x200B;**已傳送**&#x200B;的某些值（計數將取決於您傳入的事件數、任何錯誤等）
     - 希望您沒有錯誤（除非您先前遇到一些問題）
   - **電子郵件 — 統計資料**
     - 電子郵件 — 3已鎖定目標、已傳送、已傳遞

   ![電子郵件索引標籤顯示傳送效能和統計資料](assets/validate-journey-email-tab-sending-performance.png)

1. 前往檢查您的&#x200B;**電子郵件收件匣**，檢視您是否收到電子郵件（如下所示）
   - *，*&#x200B;您的訂單已送出ETA： *10/17/2026*&#x200B;追蹤號碼： *051009364*

   >[!NOTE]
   >
   >檢查AJO行銷活動的垃圾郵件資料夾[ajo-campaigns@email.dep-labs.com](mailto:ajo-campaigns@email.dep-labs.com)

   >[!NOTE]
   >
   >**為什麼遺漏了名字？**
   >
   >我們已變更「電子郵件」節點，以檢視電子郵件地址的「事件內容」 。  但個人化中的名字是從\{\{profile.person.name.firstName\}\}提取。
   >
   >當您查詢電子郵件的設定檔時，您有firstName嗎？



1. *在30-60分鐘之後*，您甚至可以在資料湖中使用下列專案檢查您的資料集： **查詢** -> **建立查詢** -> **複製/貼上SQL** -> **執行**

>[!NOTE]
>
>已串流處理訂單出貨事件，因此雖然其會快速更新設定檔，但需要一些時間才會更新Data Lake。

```sql
SELECT * FROM dep_orders
WHERE timestamp >= CURRENT_DATE
LIMIT 10
```

![針對dep_orders資料集](assets/validate-journey-query-service-dataset-results.png)的查詢服務結果

## 額外優點（檢查步驟事件）

>[!NOTE]
>
>步驟事件會記錄設定檔何時開始歷程以及歷程中的每個步驟。 注意：將這些事件記錄到資料集可能需要幾分鐘的時間。



1. 在查詢服務中，您可以透過執行此SQL來檢視步驟事件資料集正在擷取的資訊。 複製以下SQL並貼到查詢中。

```sql
select timestamp,
  identityMap,
  _experience.journeyOrchestration.stepevents.journeyVersionName,
  _experience.journeyOrchestration.stepevents.NodeName,
  _experience.journeyOrchestration.stepevents.*
  from journey_step_events
limit 50
```

結果有超過100個欄，可讓您瞭解哪些步驟事件會記錄。

>[!NOTE]
>
>若想知道每個欄位的意思，請檢視AJO結構描述字典，並將下拉式清單變更為「歷程步驟事件」結構描述： [https://experienceleague.adobe.com/tools/ajo-schemas/schema-dictionary.html?lang=zh-Hant](https://experienceleague.adobe.com/tools/ajo-schemas/schema-dictionary.html?lang=zh-Hant)



## 重述

歷程執行個體會出現在歷程報告或記錄中，且會執行已設定的動作
