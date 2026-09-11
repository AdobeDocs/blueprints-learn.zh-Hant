---
title: 將訂單事件傳送至中樞
description: 瞭解如何透過API將訂單事件串流至中心、建立串流訂單區段、將其啟用至目的地，以及驗證設定檔結果。
doc-type: article
solution: Experience Platform
exl-id: d5de39d7-7340-487a-86fa-504344daeab7
source-git-commit: 0b33b2740ee7f5af73d64f217b4475650c1d28a0
workflow-type: tm+mt
source-wordcount: '669'
ht-degree: 0%

---


# 將訂單事件傳送至中樞

## 串流至集線器與Edge

在使用案例中，我們#1將事件傳送至Edge。  在某些使用案例中，我們可能有後端系統，想要在事件中串流，但不需要將其傳送至Edge。  本實驗說明如何透過將訂購事件串流至集線器來執行此操作。

## 建立訂單區段（如果尚未建立）

按一下左側邊欄上的「對象」 ，然後按一下右上方的「建立對象」按鈕。

![按一下左側邊欄中的對象，然後按一下「建立對象」](assets/send-order-event-to-hub-click-create-audience-button.png)

找到「已下訂單」事件型別卡片，並將其拖曳至畫布。

![將「已下訂單」事件型別卡片拖曳到畫布上](assets/send-order-event-to-hub-drag-order-placed-event-onto-canvas.png)

## 更新事件規則

對事件規則進行下列變更（您可能需要展開事件才能檢視）

1. 最近
1. 15
1. 分鐘
1. 串流評估的變更

儲存為&#x200B;**訂購事件串流（15分鐘內）**



![將對象儲存為「訂單事件串流」（在15分鐘內），並包含串流評估](assets/send-order-event-to-hub-save-streaming-evaluation-rule.png)

## 啟用到目的地

如果對象已關閉，請開啟您剛才建立的對象。

按一下「啟用至目的地」



![按一下訂單對象的「啟用至目的地」](assets/send-order-event-to-hub-click-activate-to-destination.png)

### 目標

選取您先前建立的串流目的地（串流DEP Webhook）



![選取串流DEP Webhook目的地](assets/send-order-event-to-hub-select-streaming-destination.png)

### 對應

保持對應不變，然後按下一步

![保持對應不變，然後按[下一步]](assets/send-order-event-to-hub-leave-mapping-click-next.png)

按一下完成

## 開啟Postman

在您的電腦上啟動Postman，並導覽至下列API呼叫：

1. **Postman左側邊欄** —> `Collections`
1. **集合** —> `AEP Foundations Bootcamps (labs)`
1. **資料夾** —>設定檔實驗室
1. **API要求** —> `Create Order Event`

![在Postman中開啟建立訂單事件API要求](assets/send-order-event-to-hub-create-order-event-api-request.png)


## 修改API請求

若要建立範例API請求，您需要在API請求內文中填寫以下片段。

首先，收集下列值：

## 尋找帳戶串流端點

1. 導覽至左側邊欄中的&#x200B;**來源**，然後按一下頂端導覽列中的&#x200B;**帳戶**
1. 搜尋&#x200B;**dep： HTTP API \[raw]**，反白標示該列，並複製&#x200B;**串流端點**&#x200B;的值並儲存於您稍後可參考的位置

帳戶並複製其串流端點](assets/send-order-event-to-hub-http-api-raw-streaming-endpoint.png &quot;dep： HTTP API \[raw]&quot;)

## 尋找資料流ID

1. 尋找&#x200B;**dep：訂單（串流）**&#x200B;的記錄，然後按一下資料流連結
1. 在右邊欄複製並將&#x200B;**資料流ID**&#x200B;值儲存到您稍後可參考的位置

>[!NOTE]
>
>在列的空白處按一下。  請勿按一下藍色連結！

![複製dep：訂單（串流）資料流的資料流ID](assets/send-order-event-to-hub-orders-stream-dataflow-id.png "網頁資料流和資料集ID")

## 建立最終API請求

將您先前步驟中儲存的值複製到下面反白顯示的位置。

- **紅色** —> `Streaming Endpoint URL`
- **綠色** —> `Dataflow ID`

完成時，您最終的API要求應該看起來像這樣

>[!CAUTION]
>
>尚未執行！

![已完成建立串流端點與資料流ID已填入的訂單事件API要求](assets/send-order-event-to-hub-final-order-api-request.png)


## 執行API

1. 按一下&#x200B;**儲存**&#x200B;按鈕以儲存您的API呼叫
1. 按一下&#x200B;**傳送**&#x200B;按鈕以執行您的要求

成功的呼叫應導致下列回應……

傳送訂單事件後![成功的API回應](assets/send-order-event-to-hub-successful-api-response.png)

## 驗證

1. 移至您的設定檔，並檢視您的設定檔，檢視事件是否已內嵌至設定檔中。  它應以秒為單位顯示。
   1. 使用訂單中的電子郵件查詢設定檔
1. 驗證設定檔是否符合區段的資格（可能需要幾分鐘的時間）。 它應以秒到分鐘顯示。
   1. 訂單事件串流（15分鐘內）
1. 檢查webhook，檢視目的地是否已通知webhook「已實現」區段。  它應該會在5到10分鐘內顯示。
1. 15到30分鐘後，您甚至可以使用以下專案檢查資料集：
   1. 將下方的表格名稱變更為沙箱中的表格名稱。  若要尋找，請前往您的資料集清單並在&quot;`dest`&quot;上篩選，開啟資料集並在右側邊欄上複製表格名稱。

```sql
SELECT * FROM profile_export_for_destination_merge_policy_xxx
WHERE extSourceSystemAudit.LASTREFERENCEDDATE >= CURRENT_DATE
AND identitymap['email'][0].ID in ('depche.mode@dep.com')
ORDER BY extSourceSystemAudit.LASTREFERENCEDDATE DESC
LIMIT 10
```
