---
title: 傳送Edge事件
description: 透過Postman將未驗證的Web事件傳送至Edge，並驗證其是否透過事件轉送、設定檔擷取和邊緣對象資格進行。
doc-type: article
solution: Experience Platform
exl-id: 8d6e9552-1fa0-4f12-928c-03f836c1652e
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 0%

---


# 傳送Edge事件

現在所有專案皆已設定，請將事件傳送至Edge以檢視其運作情況。

若要這麼做，請使用Postman將網頁事件傳送至您建立的資料流。

這會傳送沒有OAuth權杖&#x200B;**的事件**&#x200B;來模擬從網路進入Edge的頁面檢視。  請確認您的電腦已開啟Postman以執行本實驗作業。

>[!NOTE]
>
>因為您未傳入已驗證的Token，所以無法取回任何屬性。

## 實驗室期望

1. 點選Edge的體驗事件
1. 使用事件轉送服務的資料流設定
1. 事件轉寄以將事件傳送至webhook
1. 使用AEP服務的資料流設定
   1. 要執行的Edge對象
   1. 將事件傳送至中樞
1. Postman回應以包含Edge對象（不含屬性）
1. 用於接收事件並新增事件設定檔片段的設定檔存放區
1. 要新增關係的身分存放區
1. 要接收資料並儲存在Data Lake中的資料集



## 導覽至通話

1. **Postman左側邊欄** ->集合
1. **系列** -> AEP Foundation Bootcamp （實驗室）
1. **資料夾** ->設定檔實驗室
1. **API要求** ->建立Web事件Edge （無驗證）

![Postman側邊欄導覽至「設定檔實驗室」資料夾中的「建立網頁事件Edge （無驗證） API」請求](assets/send-an-edge-event-navigate-to-the-postman-call.png)

## 修改API請求

在執行API請求之前，您需要將一些其他資訊新增到請求中。 首先，收集下列值：

## 收集資料串流ID

1. 在左側邊欄中，按一下&#x200B;**資料串流** （在「資料收集」標題下）
1. 選取您的資料流並複製&#x200B;**資料流ID**&#x200B;值

![資料串流清單，其資料串流ID值已反白顯示以供複製](assets/send-an-edge-event-gather-datastream-id.png)

## 更新Postman查詢引數

1. 在要求本身中按一下&#x200B;**引數**
1. 使用上一步驟的資料流ID更新&#x200B;**值**
1. 按一下&#x200B;**儲存**&#x200B;按鈕以儲存您的更新

將資料串流ID值貼入值欄位的![Postman Params索引標籤](assets/send-an-edge-event-update-datastream-id-param.png "更新dataStreamId")



將電子郵件變更為您的電子郵件

![Postman要求內文，其中顯示更新至測試者自己電子郵件地址的電子郵件值](assets/send-an-edge-event-change-email-param.png "將電子郵件變更為您的電子郵件")

## 執行API

按一下&#x200B;**傳送**&#x200B;按鈕以執行您的要求。

![按一下Postman傳送按鈕以執行建立網頁事件Edge要求](assets/send-an-edge-event-execute-request.png)

您應會看到回應中傳回的內容是核心內容：

- 200 OK回應表示Edge Network已成功傳送及接受資料

>[!NOTE]
>
>所有串流和批次區段直到在中心先評估後才會顯示

## 驗證事件轉送

在webhook.site上，您應該會立即看到您透過Postman請求傳送的相同裝載內文。

![Webhook.site顯示從事件轉送接收的轉送事件裝載](assets/send-an-edge-event-webhook-payload.png)

>[!NOTE]
>
>請注意，裝載已新增您在設定邊緣設定中使用的資料流時要求的地理查閱資訊

## 查詢設定檔

在Adobe Experience Platform中，查詢您剛才從您剛傳送至Edge Network的事件傳送的設定檔。 瀏覽至「設定檔 — >瀏覽」，使用下列資訊執行查詢：

- 合併原則 — >預設時間
- 身分名稱空間 — >電子郵件
- 身分值 — > edge-email\@dep.com
  - 注意：請變更此專案，以符合您在上述&#x200B;*更新Postman查詢引數*&#x200B;步驟中使用的電子郵件

1. 按一下&#x200B;**檢視**&#x200B;以查閱設定檔
1. 按一下&#x200B;**設定檔識別碼**&#x200B;以開啟設定檔

   ![具有[檢視]連結的設定檔瀏覽搜尋結果，以開啟符合的設定檔](assets/send-an-edge-event-lookup-profile.png "查詢設定檔")

1. 按一下頂端導覽列中的&#x200B;**事件**，您就可以看到剛才傳入的事件

   ![顯示剛傳送至Edge之體驗事件的[設定檔事件]索引標籤](assets/send-an-edge-event-view-profile-event.png "檢視設定檔事件")

1. 檢閱頂端導覽中的「對象成員資格」索引標籤，以驗證設定檔是否符合對象的資格。 您應該會看到下列內容：

- 任何活動Edge （15分鐘內）
- dep：任何事件串流（一小時內）

![「對象成員資格」索引標籤顯示任何事件Edge的資格，以及dep：任何事件串流對象](assets/send-an-edge-event-any-event-streaming-within-the-last-hour.png)

## 如何解讀檢查

1. 檢查Postman中的200回應（正確格式化的裝載）
1. 檢查webhook是否有事件（正確設定的事件轉送）
1. 檢查設定檔是否有事件（正確設定的AEP服務、集線器上已接收及處理的事件）
1. 幾分鐘後，檢查設定檔是否有兩個身分（身分圖表已連結到集線器）
1. 檢查設定檔是否符合對象的資格（正確定義的對象）
1. 檢查Data Lake是否有事件。
