---
title: 傳送Web事件至中樞
description: 瞭解如何使用Postman將網頁事件直接傳送至中心，並驗證其是否符合串流區段的資格及設定檔。
doc-type: article
solution: Experience Platform
exl-id: a8343499-b4d5-4540-8fe1-7497bc20e437
source-git-commit: 8b3391d41cd4a3ea6cb52d5167e627b7f6bd2c6e
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 0%
---

# 傳送Web事件至中樞

>[!IMPORTANT]
>
>請先完成[Postman安裝程式](../../postman-setup/postman-installation.md)，再開始這個實驗室。 您還需要存取相關[外部目的地啟用工作流程](../use-case-1-acquisition/configure-destinations/setup-streaming-destination.md)的[webhook.site](https://webhook.site/)。

## 開啟Postman

在您的電腦上啟動Postman，並導覽至下列API呼叫：

1. **Postman左側邊欄** —> `Collections`
1. **集合** —> `AEP Foundations Bootcamps (labs)`
1. **資料夾** —>設定檔實驗室
1. **API要求** —> `Create Web Event`

![在Postman中開啟建立網頁事件API要求](assets/send-web-event-to-hub-create-web-event-api-request.png)


## 修改API請求

若要建立範例API請求，您需要在API請求內文中填寫以下片段。

首先，收集下列值：



## 尋找帳戶串流端點

1. 導覽至左側邊欄中的&#x200B;**來源**，然後按一下頂端導覽列中的&#x200B;**帳戶**
1. 搜尋&#x200B;**dep： HTTP API \[raw]**，反白標示該列，並複製&#x200B;**串流端點**&#x200B;的值並儲存於您稍後可參考的位置

帳戶並複製其串流端點&rbrack;(assets/send-order-event-to-hub-http-api-raw-streaming-endpoint.png &quot;dep： HTTP API \[raw]&quot;)

## 尋找網頁資料流ID

1. 按一下&#x200B;**HTTP API \[raw]**&#x200B;帳戶
1. 尋找並選取名為&#x200B;**dep： Web （串流）**&#x200B;的資料流列
1. 在右邊欄複製並將&#x200B;**資料流ID**&#x200B;值儲存到您稍後可參考的位置

>[!NOTE]
>
>在列的空白處按一下。  請勿按一下藍色連結！

![複製dep： Web （串流）資料流的資料流ID](assets/send-web-event-to-hub-web-stream-dataflow-id.png "Web資料流ID")

## 建立最終API請求

將您先前步驟中儲存的值複製到下面反白顯示的位置。

- **紅色** —> `Streaming Endpoint URL`
- **綠色** —> `Dataflow ID`

完成時，您最終的API要求應該看起來像這樣

>[!CAUTION]
>
>尚未執行！

![已完成建立串流端點和資料流ID已填入的Web事件API要求](assets/send-web-event-to-hub-final-web-api-request.png)

## 執行API

1. 按一下&#x200B;**儲存**&#x200B;按鈕以儲存您的API呼叫
1. 按一下&#x200B;**傳送**&#x200B;按鈕以執行您的要求

成功的呼叫應導致下列回應……

傳送網頁事件後![成功的API回應](assets/send-web-event-to-hub-successful-api-response.png)

## 驗證

1. 移至您的設定檔，並檢視您的設定檔，檢視事件是否已內嵌至設定檔中。  它應以秒為單位顯示。
   1. 在電話中使用電子郵件來查詢設定檔
1. 根據您上次在事件中傳送後的時間，您可能無法符合新區段的資格。 否則，您可能會看到以下內容或其他內容：
   1. 任何活動Edge （15分鐘內）
      1. 請記住：當串流資料傳入時，所有以Edge評估儲存的對象也會在中心進行評估
   2. dep：任何事件串流（一小時內）
1. 此中心事件未傳送至您的webhook。
   1. 事件轉送會處理傳送至Edge的事件，而非直接傳送至集線器的事件。 使用[external-destination啟用工作流程](../use-case-1-acquisition/configure-destinations/setup-streaming-destination.md)擷取webhook.site上的事件。
1. 在至少30分鐘後，您甚至可以使用以下內容檢視您的資料集：
   1. 將下方的表格名稱變更為沙箱中的表格名稱。  若要尋找，請前往您的資料集清單並在&quot;`dest`&quot;上篩選，開啟資料集並在右側邊欄上複製表格名稱。

```sql
SELECT * FROM profile_export_for_destination_merge_policy_xxx
WHERE extSourceSystemAudit.LASTREFERENCEDDATE >= CURRENT_DATE
AND identitymap['email'][0].ID in ('depche.mode@dep.com')
ORDER BY extSourceSystemAudit.LASTREFERENCEDDATE DESC
LIMIT 10
```
