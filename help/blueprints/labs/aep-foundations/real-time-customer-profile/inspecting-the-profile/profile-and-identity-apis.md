---
title: 設定檔與身分API
description: 在Postman中使用設定檔實體API和身分識別服務叢集API來查詢設定檔屬性、事件和連結的身分。
doc-type: article
solution: Experience Platform
exl-id: 1db55c5b-fdf8-4c63-b435-477626bb0450
source-git-commit: df6c1852a6e0357dc9f166c88e77dcf9d334f955
workflow-type: tm+mt
source-wordcount: '1143'
ht-degree: 1%
---

# 設定檔與身分API

## 設定檔實體API

在使用Real-Time Customer Profile時，瞭解如何利用設定檔API至關重要。 它開啟了快速分類與除錯功能，同時為您提供從呼叫中心到資訊站等許多可能的系統整合功能。

其中最重要的API是設定檔實體API。 此API可讓您查詢個別設定檔，就像您在UI中看到的一樣。 它會使用引數來指定您是否要檢視設定檔的屬性或事件。

以下是設定檔實體API的GET方法的完整規格


## API總覽

以下是呼叫設定檔實體API所需的最低資訊。

`GET https://platform.adobe.io/data/core/ups/access/entities`

### 必要的查詢引數

隨每個請求傳送此引數。 其值取決於您要查詢設定檔的屬性或其事件：

| 引數 | 類型 | 說明 | 範例 |
| ------------- | ------ | ---------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------ |
| `schema.name` | 字串 | 您要查詢之實體的XDM結構描述類別名稱。 | `_xdm.context.profile` |
| `schema.name` | 字串 | 請改用此值來查閱設定檔的事件。 配對`relatedSchema.name=_xdm.context.profile`以限定事件的範圍為設定檔。 | `_xdm.context.experienceevent` |

### 識別要查閱的實體

大多數請求會使用`entityId`和`entityIdNS`，透過任何已知的身分值（例如電子郵件地址、CRM ID或忠誠度ID）來識別實體，而不是要求您已經知道其XID。 XID是Identity Service內部產生和指派的base64編碼識別碼，用來代表身分，並將其名稱空間和ID值合併成單一壓縮權杖（如需詳細資訊，請參閱[原生XID](https://experienceleague.adobe.com/docs/experience-platform/identity/api/list-native-id.html?lang=zh-Hant)）：

| 引數 | 類型 | 說明 | 範例 |
| ------------ | ------ | ---------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------- |
| `entityId` | 字串 | 要查閱的識別碼值。 如果您已經知道實體的XID，請在這裡自行使用並省略`entityIdNS`。 | `depeche.mode@dep.com` |
| `entityIdNS` | 字串 | `entityId`所屬的身分名稱空間程式碼（例如，`email`、`crmid`、`ECID`）。 當`entityId`不是XID時為必要。 | `email` |

>[!NOTE]
>
>此實驗室的Postman要求會依其電子郵件地址(`entityIdNS=email`， `entityId=depeche.mode@dep.com`)而非XID來查詢深層模式設定檔。

### 必要的標頭

每個請求也需要以下標頭：

| 頁首 | 類型 | 說明 | 範例 |
| ----------------- | ------ | ---------------------------------------------- | --------------------- |
| `x-gw-ims-org-id` | 字串 | IMS組織ID。 | `<your IMS org>` |
| `x-api-key` | 字串 | 您註冊的專案/認證的API金鑰。 | `<your API key>` |
| `Authorization` | 字串 | 要求的持有人權杖。 | `Bearer <your token>` |

>[!NOTE]
>
>如需完整的查詢引數清單，請參閱[設定檔實體API參考](https://developer.adobe.com/experience-platform-apis/references/profile#tag/Entities)，包括其他身分查詢選項、事件篩選(`startTime`、`endTime`、`property`、`orderby`、`limit`)、欄位選取和合併原則覆寫。

>[!WARNING]
>
>請記住，所有API要求都是沙箱專屬的，因此使用這些API時，請務必確保每個要求（稱為`x-sandbox-name`）中的標頭引數都正確設定為適當的沙箱。
>
>您已在環境檔案中設定此實驗室的`x-sandbox-name`

## 實體查閱（屬性）

若要感受實體查詢API，請使用上一個實驗室的深度模式設定檔。

1. 開啟&#x200B;**Postman**&#x200B;並導覽至&#x200B;**設定檔實驗室**&#x200B;資料夾
1. 按一下&#x200B;**實體查詢（屬性）**&#x200B;要求以開啟它
1. 按一下&#x200B;**傳送**&#x200B;按鈕以執行呼叫

   傳送![&#128279;](assets/profile-and-identity-apis-entity-lookup-attributes-request.png "設定檔實體查詢（屬性） API")之前，實體查詢（屬性）呼叫的Postman要求窗格

   成功的要求應該會以`200 OK`回應，而且您應該會看到包含Depeche Mode設定檔所有屬性的結果。

   ![200 OK回應包含Depeche模式設定檔的所有屬性](assets/profile-and-identity-apis-successful-attributes-api-response.png "成功的設定檔實體（屬性） API回應")

   >[!NOTE]
   >
   >根據預設，如果在設定檔實體請求中未指定合併原則，則會使用沙箱中的預設合併原則

   透過Entity API，使用查詢引數來變更傳回的回應。

1. 在實體查詢（屬性）要求中，按一下要求的&#x200B;**引數**&#x200B;選項
1. 勾選名為&#x200B;**欄位**&#x200B;的&#x200B;**索引鍵**&#x200B;旁的方塊
1. 按一下&#x200B;**傳送**&#x200B;按鈕以執行要求

![啟用欄位引數以篩選回應的Entity Lookup （屬性）要求](assets/profile-and-identity-apis-entity-lookup-attributes-with-filter-enabled.png)

>[!NOTE]
>
>請注意，也有指定`mergePolicyId`的引數。 若要尋找此專案的值，請使用其他API或使用UI查詢ID。

成功的要求應該會以`200 OK`回應，而且您應該只會看到剛才啟用的引數篩選中指定的欄位：名字、姓氏以及作用中產品的陣列。

![篩選的200 OK回應只顯示「名字」、「姓氏」和「使用中產品」欄位](assets/profile-and-identity-apis-successful-filtered-attributes-response.png "成功的設定檔實體查詢（屬性） API回應，並啟用篩選器")

>[!SUCCESS]
>
>恭喜！  您已使用設定檔實體API成功查詢設定檔的屬性

## 實體查閱（事件）

若要查詢設定檔的事件，請使用相同的設定檔實體API。  唯一的區別是，您必須告訴設定檔服務您想要變更要在回應中使用的類別型別。

1. 按一下&#x200B;**實體查詢（事件）**&#x200B;要求以開啟
1. 按一下&#x200B;**傳送**&#x200B;按鈕以執行呼叫

傳送前實體查詢（事件）呼叫的![Postman要求窗格](assets/profile-and-identity-apis-entity-lookup-events-request.png)

成功的要求應該會以`200 OK`回應，而且您應該會看到包含深度模式設定檔之所有事件的結果。



![200 OK回應包含Depeche模式設定檔的所有事件](assets/profile-and-identity-apis-successful-events-api-response.png "成功的設定檔實體查詢（事件） API回應")

查詢設定檔屬性時，Entity API會有更多查詢引數，這些引數會變更傳回的回應內容。

請在Params區段中啟用這些引數，然後執行請求，以試用其中的一些引數。 瞭解其運作方式！

![實體查詢（事件）要求，已在Params區段](assets/profile-and-identity-apis-entity-lookup-events-query-params.png "體驗事件的設定檔實體查詢")中啟用其他查詢引數

**範例查詢引數定義**

| 索引鍵 | 值 | 說明 |
| ------------- | ------------------------------- | ------------------------------------------------------------------------------------------------------- |
| mergePolicyId | \&lt;blank> | 切換用於查閱的合併原則。 將其保留為空白將使用沙箱的預設合併原則 |
| 欄位 | eventType，timestamp，identityMap | 僅顯示每個事件的這些欄位，無論它們是否有值 |
| 屬性 | eventType=&quot;order.placed&quot; | 僅將事件篩選為指定型別的事件 |
| orderby | +timestamp | 以遞增順序排序事件 |
| limit | 5 | 在回應中僅顯示5個事件 |

>[!NOTE]
>
>在這裡深入瞭解所有查詢引數選項 — > [https://developer.adobe.com/experience-platform-apis/references/profile/#tag/Entities/operation/retrieveEntity](https://developer.adobe.com/experience-platform-apis/references/profile/#tag/Entities/operation/retrieveEntity)



## Identity服務叢集API

在某個時候，您可能會對身分圖表中，哪些身分屬於特定設定檔的身分叢集存有疑問。  此API可讓您傳遞單一身分名稱空間/值，而且當回應時，您會收到該設定檔的完整身分叢集。

自己試試看：

1. 按一下&#x200B;**列出連結的身分**&#x200B;要求以開啟
1. 按一下&#x200B;**傳送**&#x200B;按鈕以執行呼叫

>[!NOTE]
>
>請注意，請求中的引數為身分名稱空間和ID （即值）



在傳送前先為List Linked Identities呼叫![Postman要求窗格](assets/profile-and-identity-apis-list-linked-identities-request.png "List Linked Identities API")

成功的回應看起來應該像下面的熒幕擷圖



![成功列出連結的身分回應，顯示深度模式設定檔的所有身分](assets/profile-and-identity-apis-successful-list-linked-identities-response.png)

>[!NOTE]
>
>您注意到回應包含設定檔深層模式的所有身分
