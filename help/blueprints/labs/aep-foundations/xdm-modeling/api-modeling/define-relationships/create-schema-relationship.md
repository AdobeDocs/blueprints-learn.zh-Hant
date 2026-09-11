---
hold: true
title: 建立結構描述關係
description: 使用結構描述登入API建立一對一的關係描述項，將客戶帳戶結構描述連結至查詢計畫結構描述。
doc-type: article
solution: Experience Platform
exl-id: c9079585-fff1-4ee1-8992-93825fcde759
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---


# 建立結構描述關係

1. 按一下`XDM Schema Lab -> Create Relationship Descriptors`資料夾中的`Step 2 - Relationship Descriptor Customer Account To Plan` API要求

>[!CAUTION]
>
>尚未執行要求

![步驟2 — 規劃API要求的關係描述項客戶帳戶](assets/create-schema-relationship-step-2-descriptor-request.png "步驟2 — 規劃的關係描述項客戶帳戶")



&#x200B;2. 更新API呼叫內文中的下列屬性。

- 將`xdm:sourceSchema`屬性的值設定為您從[建立結構描述](../build-schema/create-schema.md)實驗室步驟中儲存的客戶帳戶結構描述的`$id`
- 將`xdm:sourceProperty`的值設為客戶帳戶結構描述中`planID`欄位的路徑。
- 將`xdm:destinationSchema`屬性的值設定為您在第1個步驟中儲存的`dep: Lookup Plan`個結構描述的`$id`

>[!NOTE]
>
>使用客戶帳戶結構描述中planId欄位的點標籤法值，並將`.`取代為`/`
>
>
>別忘了前置`/` 😄

僅限範例

```json
{
  "@type": "xdm:descriptorOneToOne",
  "xdm:sourceSchema": "https://ns.adobe.com/devbc/schemas/8415ac18dd8943e35d12caf0c24b57b4a5a9ab7fd637245e",
  "xdm:sourceVersion": 1,
  "xdm:sourceProperty": "/_devbc/plan/planID",
  "xdm:destinationSchema": "https://ns.adobe.com/devbc/schemas/6470f71181cf87aa39c2c2c43824eaa15f523652f7f88ff7"
,
  "xdm:destinationVersion": 1
}
```

>[!NOTE]
>
>請記得使用您自己的名稱更新上述租使用者名稱稱(\_devbc)



&#x200B;3. 繼續使用`Save`按鈕前請先儲存您的請求

&#x200B;4. 按一下`Send`按鈕執行API

您現在應該會看到如下的`201 Created`回應

![201建立客戶帳戶至計畫關係描述項後已建立回應](assets/create-schema-relationship-customer-account-plan-descriptor.png "客戶帳戶 — 計畫關係描述項")

>[!NOTE]
>
>請記住，即時客戶設定檔（以及所有Experience Platform）僅支援我們所稱的&#x200B;**一(1)個躍點加入** （來自XDM個人設定檔或XDM體驗事件結構） (也就是您只能建立一(1)個層級的查閱關係)

>[!NOTE]
>
>您注意到關聯性描述項`@type`設定為值`OneToOne`嗎？ 紙張XDM ERD中客戶帳戶與計畫表格之間的關係不是1\：N嗎？  怎麼回事？
>
>
>即時客戶個人檔案的建立可描述個人特徵與行為。  因此，從個人鏡頭中，查詢表格僅&#x200B;**僅** **永遠是**，在細分期間定義為1:1關係。
>
>如果你的腦子痛……
