---
title: 標示身分欄位
description: 瞭解身分描述項如何使用XDM結構描述登入API將結構描述欄位標示為主要或非主要身分。
doc-type: overview-page
solution: Experience Platform
exl-id: f6498584-0f4d-4baf-86b5-b00cc78e2ba7
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 0%

---


# 標示身分欄位

## 身分描述項

若要將欄位標示為身分，您必須在結構描述登入中建立身分描述項。 結構描述描述項內文的範例看起來如下所示：

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

- **@type** ->一律設為`xdm:descriptorIdentity`
- **xdm\：sourceSchema** ->欄位所在之結構描述的`$id`
- **xdm\：sourceVersion** ->一律為1
- **xdm\：sourceProperty** ->結構描述中欄位的路徑
- **xdm\：namespace** ->應儲存欄位的身分名稱空間程式碼
- **xdm\：property** ->一律為`xdm:code`
- **xdm\：isPrimary** ->如果主要身分，則`true`，否則為`false`


## 您的目標

建立客戶帳戶結構描述的主要和非主要身分。 執行下一節中的步驟後，您的結構描述應如下所示。

建立主要和非主要身分描述項後![客戶帳戶結構描述](assets/overview-schema-with-primary-and-non-primary-identities.png)
