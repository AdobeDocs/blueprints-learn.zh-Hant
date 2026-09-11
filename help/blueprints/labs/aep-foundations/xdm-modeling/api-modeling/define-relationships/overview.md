---
title: 定義關係
description: 瞭解關係描述元如何透過API將客戶方案連結到XDM方案登入中的查閱方案。
doc-type: overview-page
solution: Experience Platform
exl-id: be672c84-09ac-4941-b40e-da7bd3fd6704
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---


# 定義關係

## 關係描述項

為了建立一個結構描述與另一個結構描述的關係，您需要在結構描述登入中建立一個關係描述項。 結構描述描述項內文的範例看起來如下所示：

一對一描述項

```json
{
  "@type": "xdm:descriptorOneToOne",
  "xdm:sourceSchema": "https://ns.adobe.com/devbc/schemas/8415ac18dd8943e35d12caf0c24b57b4a5a9ab7fd637245e",
  "xdm:sourceVersion": 1,
  "xdm:sourceProperty": "/_devbc/plan/planID",
  "xdm:destinationSchema": "https://ns.adobe.com/devbc/schemas/6470f71181cf87aa39c2c2c43824eaa15f523652f7f88ff7",
  "xdm:destinationVersion": 1
}
```

參考身分描述項

```json
{
  "@type": "xdm:descriptorReferenceIdentity",
  "xdm:sourceSchema": "https://ns.adobe.com/devbc/schemas/6470f71181cf87aa39c2c2c43824eaa15f523652f7f88ff7",
  "xdm:sourceVersion": 1,
  "xdm:sourceProperty": "/_devbc/plan/planID",
  "xdm:identityNamespace": "planID"
}
```

## 您的目標

為客戶帳戶結構描述建立關係身分。 執行下一節中的步驟後，您的結構描述應如下所示。

![客戶帳戶結構描述顯示關聯性和參考身分描述項](assets/overview-schema-with-relationship-identities.png)
