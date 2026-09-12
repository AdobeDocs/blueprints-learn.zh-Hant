---
title: 存取權杖
description: 在Postman中產生OAuth伺服器對伺服器存取權杖，並瞭解驗證AEP API呼叫所需的標頭。
doc-type: article
solution: Experience Platform
exl-id: e38a1bd4-5a09-40c6-8303-c3770801c864
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 0%

---


# 存取權杖

## API安全性總覽



若要建立與Adobe產品的安全API連線，Adobe會提供OAuth伺服器對伺服器認證的建立。 若要這麼做，您必須先在Adobe Developer Console中建立開發人員專案。 您必須在Adobe Admin Console中指派開發人員許可權，才能存取Developer Console。 一旦您擁有這些許可權，您就可以使用各種Adobe產品相關API來建立開發人員專案。 這是OAuth伺服器對伺服器認證發揮作用的地方。 若要產生存取權杖，您必須將一組宣告傳遞至Adobe的Identity Management服務(IMS)。 針對OAuth伺服器對伺服器認證，呼叫範例看起來會像這樣：

```curl
curl -X POST 'https://ims-na1.adobelogin.com/ims/token/v3?client_id={CLIENT_ID}' \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -d 'client_secret={CLIENT_SECRET}&grant_type=client_credentials&scope={SCOPE}'
```

>[!NOTE]
>
>您可以在[此處](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/#generate-access-tokens)進一步瞭解使用OAuth伺服器對伺服器認證建立開發人員專案的e2e程式。 對於啟動營，我們將「手動」處理序😄的這個步驟



## Adobe Experience Platform + Adobe IMS

對任何Adobe服務的每個請求都必須在Authorization標頭中包含存取權杖以及在開發人員專案建立期間產生的使用者端密碼。 此外，Experience Platform及其相關應用程式需要在每個請求中出現兩個其他標頭引數。

- `x-gw-ims-org-id` — 此引數會指定請求所屬的`IMS Org`，並確保請求的處理會解析至適當的SaaS環境
- `x-sandbox-name` — 此引數會指定在Experience Platform中處理請求的沙箱

現在您已瞭解關於Adobe如何保護其API以及操作它們所需的內容，請立即使用。

>[!CAUTION]
>
>未指定`x-sandbox-name`引數不會如您預期般使要求失敗。 而是預設要求為處理至`default`沙箱，而沙箱會自動布建至任何Experience Platform環境

>[!NOTE]
>
>在這個Bootcamp中，我們建立了一個開發人員專案，為您提供Postman環境檔案，其中包含請求`access_token`所需的所有必要值。 這是您在本實驗先前步驟中上傳的資料

## 使用Postman進行驗證

1. 啟動Postman並導覽至標題為`IMS Authenticate`的目錄，然後按一下以開啟要求
1. 接下來，在Postman的右上角，您會看到一個環境下拉式清單。 從下拉式清單中選取`AEP Bootcamp`環境
1. 現在按一下「傳送」按鈕來執行呼叫

傳送IMS驗證呼叫以產生存取權杖後![Postman請求](assets/access-token-execute-ims-authenticate-request.png)

成功的回應應如下所示：

```none
200 OK Successful Authentication
```

成功的回應

```json
{
    "token_type": "bearer",
    "access_token": "<value>",
    "expires_in": 86399979
}
```

`token_type` — 一律為持有人

`access_token` — 在所有API呼叫的授權標頭中證明授權和必要

`expires_in` — 存取權杖到期前的毫秒（今天的24小時到期期間）

>[!TIP]
>
>恭喜！ 您已成功驗證，且您的access\_token現在已儲存至您的環境檔案



## 常見錯誤

### 無效的權杖

當環境檔案中的`private_key`格式錯誤或不再有效時，就會發生這種情況。 如果您看到這個訊息，請確定您已複製整個索引鍵，包括分行符號

範例：

```none
-----BEGIN PRIVATE KEY----- 
some uber long varchar set is here
-----END PRIVATE KEY----- 
```

```none
400 invalid_token
```

>[!NOTE]
>
>僅適用於使用JWT型驗證時

### 無效的IMS\_ORG

當您忘記從下拉式清單設定您的郵遞員環境時，就會發生此錯誤

未選取Postman環境時，在作用中環境中找不到![IMS_ORG錯誤](assets/access-token-forgot-to-select-postman-environment.png)

>[!NOTE]
>
>執行API呼叫時，別忘了設定您的Postman環境
>
>![從AEP環境下拉式清單中選取Postman Bootcamp環境](assets/access-token-set-postman-environment.png)
