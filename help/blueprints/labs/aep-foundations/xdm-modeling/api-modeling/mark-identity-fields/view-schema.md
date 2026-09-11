---
title: 檢視結構描述
description: 透過UI和API檢視結構描述的身分描述項，並比較已解析與未解析結構描述回應的「接受」標頭選項。
doc-type: article
solution: Experience Platform
exl-id: 44eedb82-259f-4f7f-84fe-acc2b42376eb
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---


# 檢視結構描述

## 透過UI檢視

1. 開啟瀏覽器並導覽回`Schema -> Browse`區段。
1. 搜尋&#x200B;**客戶帳戶**&#x200B;結構描述
1. 請注意，身分已新增到結構描述

![結構描述瀏覽檢視，顯示已新增至結構描述](assets/view-schema-schema-ui-with-identities.png "結構描述UI檢視中的身分")


## 透過API檢視

1. 按一下以選取`Step 3 - Get Customer Account Schema and its descriptors` API。

   ![步驟3 — 使用描述項API要求取得客戶帳戶結構描述](assets/view-schema-step-3-get-customer-account-schema-w-descriptors.png "步驟3 — 使用描述項取得客戶帳戶結構描述")



1. 在要求的URL中，將`<replace me>`取代為您從上一節（建立您的結構描述）儲存到呼叫結尾的`$meta:altId`，如下所示

   ![附加altId的最後步驟5要求至URL](assets/view-schema-final-step-5-request.png "最後步驟5要求")



1. 儲存您所做請求的編輯

1. 按一下`Send`按鈕以執行要求

您現在應該會看到`200 OK`回應，而且應該能夠透過XDM JSON結構的鏡頭瀏覽您建立的結構描述

![顯示結構描述之XDM JSON結構的API回應內文](assets/view-schema-body-of-the-api-response.png "API回應的內文")



在API回應中向下瀏覽，檢視您建立的身分描述項

![顯示在API回應中的身分描述項](assets/view-schema-descriptors-displayed-in-api-response.png "顯示在API回應中的描述項")


## 接受標頭

請注意請求中使用的&#x200B;**Accept**&#x200B;標頭。 此標頭會通知XDM結構描述登入傳回結構描述的`$refs`未解析（即顯示最小資訊量），以及它在API回應中的關聯描述項。  Adobe提供其他&#x200B;**Accept**&#x200B;標頭，供您用來取得結構描述的詳細資訊。

步驟3取得客戶帳戶結構描述請求&rbrack;(assets/view-schema-accept-header.png "步驟3 — 取得客戶帳戶結構描述接受標題中的!&lbrack;接受標題欄位")

>[!NOTE]
>
>您可以在這裡閱讀有關各種Accept標頭的詳細資訊 — > [Experience League結構描述API端點](https://experienceleague.adobe.com/docs/experience-platform/xdm/api/schemas.html?lang=zh-Hant#lookup)



若要實際檢視此專案，請變更&#x200B;**Accept**&#x200B;標頭，以告知結構描述登入以所有`$ref`和`allOf`完全解析（亦即爆炸）的回應以及任何關聯的描述項

1. 將`Accept`標頭值更新為：
   `application/vnd.adobe.xed-full-desc+json; version=1`
1. 使用`Save`按鈕儲存您的請求
1. 使用`Send`按鈕執行您的要求

您現在應該會看到類似以下的回應：

![顯示所有已解析屬性的完整展開結構描述回應](assets/view-schema-fully-exploded-schema-showing-all-properties.png "顯示所有屬性的完整展開結構描述")

>[!NOTE]
>
>請注意，現在回應中如何完整顯示結構描述的所有屬性，而在先前的呼叫中，您只會顯示結構描述的`$ref`值（即它參考的欄位群組），而且不會將任何內容完全解析為個別欄位/屬性。

>[!NOTE]
>
>瞭解這一點很重要，因為使用API時，如果您要做的只是取得結構描述的`$id`或只是檢查其構成，則並不一定需要完全解析的回應
