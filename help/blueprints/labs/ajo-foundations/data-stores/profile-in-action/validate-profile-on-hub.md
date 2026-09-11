---
hold: true
title: 驗證集線器上的設定檔
description: 瞭解如何在Real-time Customer Profile Hub上查詢設定檔，以及在串流事件後驗證其事件和區段會籍。
doc-type: article
solution: Experience Platform
exl-id: f1c8b1ac-e57c-48c6-aa91-5c83f79ce7e3
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---


# 驗證集線器上的設定檔

## 學習目標

驗證事件是否導致集線器上即時設定檔中的設定檔更新及區段資格。

## 在集線器上查詢設定檔

在Adobe Experience Platform中，查詢您剛才從您剛傳送至Edge Network的事件傳送的設定檔。

1. 瀏覽至&#x200B;**客戶** -> **設定檔** -> **瀏覽**&#x200B;以使用下列資訊執行查詢：
   - **合併原則** -> `Default Timebased`
   - **身分識別名稱空間** -> `Email`
   - **身分值** -> `henry.creel@emailsim.io`
1. 按一下&#x200B;**檢視**&#x200B;以查閱設定檔

![使用合併原則與身分查詢欄位來瀏覽設定檔畫面](assets/validate-profile-on-hub-browse-profile-lookup.png)



## 檢查中心設定檔

1. 按一下&#x200B;**設定檔識別碼**&#x200B;以開啟設定檔
1. 先按一下&#x200B;**屬性**&#x200B;標籤，再按一下&#x200B;**集線器**&#x200B;選項按鈕以檢視&#x200B;**集線器設定檔**

在[屬性]索引標籤上顯示![中心設定檔](assets/validate-profile-on-hub-attributes-tab.png)


## 驗證事件

1. 按一下頂端導覽列中的&#x200B;**事件**，您就可以看到剛才傳入的事件

![事件索引標籤顯示設定檔上的串流事件](assets/validate-profile-on-hub-events-tab.png)

## 驗證區段

### 透過JSON

1. 按一下&#x200B;**屬性**&#x200B;標題並檢視&#x200B;**JSON**

![顯示segmentMembership的設定檔屬性JSON檢視](assets/validate-profile-on-hub-json-view.png)

&#x200B;2. 尋找&#x200B;**segmentMembership**。  應該看起來像這樣（您的ID將會不同）

```json
  "segmentMembership": {
    "ups": {
      "ce0b8386-ef2a-4244-8ad0-1a72d6494181": {
        "status": "realized",
        "lastQualificationTime": "2025-12-15T23:11:49Z"
      },
      "8ce516fe-920a-4f9d-b92b-0403890a8491": {
        "status": "realized",
        "lastQualificationTime": "2025-12-12T15:01:01Z"
      }
    }
```

>[!NOTE]
>
>**如何讀取segmentMembership？**
>
>[https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/segmentation](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/segmentation)
>
>**ups：**&#x200B;這是AEP支援之不同對象型別的對應索引鍵。  ups鍵包含規則產生器建立的對象。  其他對象將包含在其他索引鍵（例如AAM）中。
>
>**lastQualificationTime**&#x200B;此設定檔上次符合區段資格的時間戳記
>
>**狀態**
>
>*已實現*：設定檔符合區段的資格。
>*已退出*：設定檔正在退出此區段，做為目前請求的一部分。
>
>

### 透過UI

1. 若要驗證設定檔符合對象資格，比較簡單的方式是檢視&#x200B;**對象成員資格**&#x200B;標籤（您應該至少會看到這些內容）：
   - dep：任何事件串流（一小時內）
   - dep：任何事件Edge （一小時內）

![對象會籍標籤顯示合格區段](assets/validate-profile-on-hub-audience-membership-tab.png)

>[!NOTE]
>
>**為什麼沒有批次對象？**
>
>您應該不會看到&#x200B;**dep：任何事件批次（一天內）**&#x200B;符合資格，因為我們在資料中串流化，且批次評估每天發生一次。

## 重述

設定檔存在於集線器中，並符合預期對象的資格。
