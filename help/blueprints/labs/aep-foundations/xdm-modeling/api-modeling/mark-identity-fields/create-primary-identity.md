---
title: 建立主要身分
description: 使用結構描述登入API為客戶帳戶結構描述建立主要的customerID身分描述項。
doc-type: article
solution: Experience Platform
exl-id: db690081-e857-4875-8bb9-7ac197d73cab
source-git-commit: 0b33b2740ee7f5af73d64f217b4475650c1d28a0
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 0%

---


# 建立主要身分

1. 按一下`XDM Schema Lab -> Create Identity Descriptors`資料夾中的`Step 1 - Create Primary Identity for Customer Account Schema` API要求

   ![步驟1 — 建立客戶帳戶結構描述Postman請求的主要身分](assets/create-primary-identity-step-1-postman-request.jpeg "步驟1 — 建立客戶帳戶結構描述的主要身分")

   >[!CAUTION]
   >
   >尚未執行要求



1. 使用您從[建立結構描述](../build-schema/create-schema.md)實驗室步驟中儲存的`$id`，更新要求內文中的`xdm:sourceSchema`值

1. 將要求內文中的`xdm:isPrimary`值更新為`true`

   僅限範例

   ```json
   {
     "@type": "xdm:descriptorIdentity",
     "xdm:sourceSchema": "https://ns.adobe.com/devbc/schemas/8415ac18dd8943e35d12caf0c24b57b4a5a9ab7fd637245e",
     "xdm:sourceVersion": 1,
     "xdm:sourceProperty": "/_devbc/customerID",
     "xdm:namespace": "customerID",
     "xdm:property": "xdm:code",
     "xdm:isPrimary": true
   }
   ```

   >[!NOTE]
   >
   >請記得使用您自己的名稱更新上述租使用者名稱稱(\_devbc)



1. 繼續使用`Save`按鈕前請先儲存您的請求

1. 按一下`Send`按鈕執行API。 您現在應該會看到如下的`201 Created`回應

![201成功建立主要身分描述項後已建立回應](assets/create-primary-identity-201-created-response.png "已成功建立主要身分描述項")

>[!TIP]
>
>恭喜！  您剛才在結構描述中建立了主要身分描述項
