---
title: 串流設定檔
description: 使用Postman和串流端點及資料流ID，透過HTTP API將客戶設定檔記錄傳送至Adobe Experience Platform。
doc-type: article
solution: Experience Platform
exl-id: 937d153c-9230-4f5a-a397-6c177a3ea890
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 0%

---


# 串流設定檔

## API總覽

以原始格式將資料串流至Adobe Experience Platform時，請務必瞭解API的結構，如此一來，無論您建立什麼資料流，都可以輕鬆重新建立。  以下是使用cURL呼叫的基本結構範例

**範例要求（原始資料）**

```curl
curl --location '' \
--header 'Content-Type: application/json' \
--header 'x-adobe-flow-id:  <dataflow-id>;' \
--header 'Authorization: Bearer XXX;' \
--data '{
    "customer_id": "202208240125",
    "firstName": "",
    "lastName": "",
    "email": "",
    "createDate": "1660096899",
    "modifyDate": "2022-08-09T22:01:40Z",
    "birth_Date": "1991-06-12",
    "mobile_phone": "888-888-8888",
    "email_optIn": "y",
    "sms_optIn": "n",
    "shipping_street_address": "1901 W Madison St",
    "shipping_city": "Chicago",
    "shipping_state": "IL",
    "shipping_zip_code": "60612",
    "billing_street_address": "1901 W Madison St",
    "billing_city": "Chicago",
    "billing_state": "IL",
    "billing_zip_code": "60612",
    "plan_id": "m1",
    "plan_name": "basic",
    "account_create_date": "Created on 2022-04-20T22:19:03Z",
    "account_end_date": "2022-01-20T13:15:32Z",
    "source": "inStore"
}'
```



上述請求中需要注意的幾個重要元素：

| 關鍵元素 | 必填 | 說明 |
| --------------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 請求URL （即位置） | - | 這是您建立之串流資料將指向的HTTP API來源帳戶的URL。 **它永遠屬於POST型別** |
| 頁首&#39;Content-Type&#39; | * | 一律設為`application/json`，因為您傳入的資料為JSON格式 |
| 頁首「x-adobe-flow-id」 | - | 設為從來源聯結器建立的資料流ID |
| 標頭&#39;Authorization&#39; | * | 可選值，但出於安全性考量，強烈建議使用。 這與您在[Postman設定](../../postman-setup/environment-file.md) Labs期間產生的`access_token`相同 |
| 內文內容 | - | 包含您想要傳送至Adobe Experience Platform的實際資料 |

>[!NOTE]
>
>內文內容應一律為JSON格式，並與資料流設計期間提供的範例裝載相符



## 收集必要的值

在您可以串流處理資料之前，您需要收集上面列出的幾個必要值（特別是串流端點URL和本文內容「標題」值）。

執行下列步驟：

1. 複製&#x200B;**串流端點**&#x200B;值並將其儲存到您的本機電腦（假設您尚未離開上一節的步驟）。 如果您確實離開了，可以在「來源」 — >「帳戶」下找到它。

   >[!NOTE]
   >
   >如果您確實離開了，您可以執行下列動作來進入此頁面：
   >
   >- 按一下左側邊欄中的&#x200B;**來源**
   >- 確定您位於&#x200B;**帳戶**&#x200B;索引標籤上，然後按一下您建立的名為&#x200B;**串流擷取 — \&lt;您的首字母>**&#x200B;的帳戶

   >[!NOTE]
   >
   >如果沒有看到此值，請確定您沒有按一下資料流列來選取該列。  請勿按一下藍色連結

   ![串流端點URL顯示在帳戶詳細資訊的右側](assets/stream-a-profile-streaming-endpoint-url-on-the-right.png)



1. 按一下資料流列的任意位置以避免藍色連結來選取資料流列。 複製&#x200B;**資料流ID**&#x200B;並將其儲存在安全的地方

![資料流詳細資料右側邊欄顯示API使用詳細資料和資料流ID](assets/stream-a-profile-dataflow-details-right-rail-api-usage.png)



## 更新您的API請求

切換至您的Postman應用程式，並以您剛收集的資訊更新「建立客戶帳戶」請求。

1. 開啟Postman並導覽至&#x200B;**資料擷取實驗室 — >建立客戶帳戶** API要求並開啟

   ![在Postman中開啟建立客戶帳戶API請求](assets/stream-a-profile-create-customer-account-api-request.png)



1. 複製並貼上您先前儲存至請求URL的&#x200B;**串流端點**&#x200B;值

   ![串流端點值已貼入建立客戶帳戶請求URL](assets/stream-a-profile-create-customer-account-streaming-endpoint-url.png)



1. 複製並貼上您先前儲存的資料流ID值至&#x200B;**x-adobe-flow-id**&#x200B;標頭值

   ![資料流ID已貼到x-adobe-flow-id標頭值中](assets/stream-a-profile-copy-paste-x-adobe-flow-id.png)



1. 在請求內文中，更新以下屬性，如下所示：

   - **名字** ->您的名字
   - **姓氏** ->您的姓氏
   - **電子郵件** ->您的電子郵件地址
   - **出生日期** -> YYYY-MM-DD

   **5. 儲存**&#x200B;您的請求

1. 按一下&#x200B;**傳送**&#x200B;按鈕，執行在您的客戶帳戶設定檔中串流的請求

   ![最終建立客戶帳戶要求已準備好在Postman中傳送](assets/stream-a-profile-final-create-customer-account-request.png)



1. 您應該會收到`200 OK`回應，指出Adobe Experience Platform已成功接收該回應

範例200 OK回應

```none
{
    "inletId": "57e8b639020de08147888c2ce2046f2f4d36f622ee22b7313a565ab3a4ecee54",
    "xactionId": "1688068236344:7186:152",
    "flowId": "7d1d1a20-3df2-43fb-8bd8-2856bb3ea6a4",
    "receivedTimeMs": 1688068236344
}
```

>[!NOTE]
>
>記下回應中的&#x200B;**xactionId**。  如果發生錯誤，而您未看到擷取的記錄，則應一律將此作為客戶支援票證的一部分提供，因為它是我們的支援團隊用於偵錯任何環境問題的追蹤專案符號

>[!TIP]
>
>恭喜！  您已成功將設定檔記錄中的資料流傳輸至Adobe Experience Platform
