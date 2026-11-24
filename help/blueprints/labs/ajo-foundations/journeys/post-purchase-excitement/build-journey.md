---
title: 建立歷程
description: 建立回應Order Shipped事件的單一歷程、呼叫出貨ETA的自訂動作，並傳送個人化電子郵件。
doc-type: article
solution: Experience Platform
exl-id: 4dd15071-51e5-445a-932d-690d9a73a913
source-git-commit: 93fba2a4818790431306801b43a791508451f344
workflow-type: tm+mt
source-wordcount: '1078'
ht-degree: 0%
---

# 建立歷程

## 學習目標

建立以設定的Order Shipped事件開始的單一歷程，從外部服務取得ETA並傳送電子郵件。

## 建立歷程

前往&#x200B;**歷程**&#x200B;並按一下&#x200B;**建立歷程**

![建立歷程 — 在Adobe Journey Optimizer中從頭開始建立](assets/build-journey-create-journey-from-scratch.png)



## 歷程屬性

1. 使用以下專案更新右側邊欄中的歷程屬性：
   - **名稱**： `Order Shipped Journey`
   - **描述**： `Notify customer that order has shipped. Include shipping details.`
   - **標籤**： *留空*
   - **歷程量度**： *留空*

     >[!NOTE]
     >
     >**空下拉式清單？**
     >
     >別擔心，繼續前行。 在沙箱中建立的第一個歷程需要「裝填泵」。  發佈歷程後，此下拉式清單將可供選擇。

   - **允許重新進入**： `checked`

   - **重新進入等待期間：** `5 minutes`

   - **存取標籤**： *留空*

   - **時區**： `Your Local timezone`

   - **在等待和條件中使用設定檔時區**： `NOT checked`

   - **開始/結束日期**： *保留空白*

   - **逾時或錯誤**： `30`

   - **上限規則：** *留空*

   - **優先順序**： `0`



2. 如果一切正常，請按一下&#x200B;**儲存**&#x200B;按鈕

歷程屬性面板的![儲存按鈕](assets/build-journey-save-journey-properties.png)




## 歷程畫布

### 新增單一事件

按一下加號圖示，導覽至&#x200B;**自訂事件**&#x200B;並選取&#x200B;**orderShipped**&#x200B;事件，如下所示

![從[事件]功能表將orderShipped事件拖曳到歷程畫布](assets/build-journey-drag-order-shipped-event-onto-canvas.png)



![在歷程畫布上訂購送貨事件](assets/build-journey-drag-order-shipped-event-onto-canvas--2.png)





### 新增自訂動作

1. 按一下加號圖示，導覽至&#x200B;**自訂動作**，並選取您建置的名為&#x200B;**GetShippingDetails**&#x200B;的動作，使其出現在orderShipped事件之後

   ![將GetShippingDetails自訂動作拖曳到orderShipped事件之後的畫布上](assets/build-journey-drag-getshippingdetails-action-onto-canvas.png)

2. 在右側邊欄中，在「存取和隱私權設定 — >行銷動作」下拉式清單下，確定值設為&#x200B;**無**

   ![在存取和隱私權設定中，「行銷動作」下拉式清單設為「無」](assets/build-journey-set-marketing-action-to-none.png)

3. 在「端點組態 — >查詢引數」功能表下，按一下orderid旁的&#x200B;**鉛筆圖示**

   ![鉛筆圖示可編輯端點設定中的orderid查詢引數](assets/build-journey-edit-orderid-query-parameter.png)

4. 在出現的強制回應視窗中，展開&#x200B;**Context** -> **orderShipped** -> **Order**，然後選取&#x200B;**訂單ID (orderID)**，然後按一下&#x200B;**確定**

   來自orderShipped訂單內容欄位的![Select訂單識別碼(orderID)](assets/build-journey-select-order-id-context-field.png)

5. 回到右側邊欄，確定「逾時」或錯誤的選項為&#x200B;**未勾選**，然後按一下&#x200B;**儲存按鈕**

取消勾選![逾時或錯誤選項，並反白顯示「儲存」按鈕](assets/build-journey-uncheck-timeout-or-error.png)



### 新增電子郵件動作

1. 在GetShippingDetails自訂事件後按一下加號圖示，然後選取&#x200B;**動作**。

   ![在GetShippingDetails動作之後，將[動作]節點拖曳到畫布上](assets/build-journey-drag-email-action-onto-canvas.png)

2. Select **電子郵件**&#x200B;以取得行銷動作，然後&#x200B;**新增**。

   ![Select電子郵件作為行銷動作，然後按一下[新增]](assets/build-journey-select-email-marketing-action.png)

3. 在右側邊欄中，按一下&#x200B;**設定動作**

   ![設定右側邊欄中的動作按鈕](assets/build-journey-click-configure-action.png)

4. 將&#x200B;**電子郵件通道設定**&#x200B;設為`Profile-Email`，然後按一下&#x200B;**編輯內容**

![電子郵件通道設定已設定為具有編輯內容連結的設定檔電子郵件](assets/build-journey-set-profile-email-channel-configuration.png)



### 新增電子郵件內文內容

對於內容，您將保持簡單。 就像愚蠢的簡單。

1. 將主旨行更新為`Order Shipped`，然後按一下&#x200B;**編輯電子郵件內文按鈕**

   ![主旨列已更新為「訂單已隨附編輯電子郵件內文」按鈕](assets/build-journey-update-subject-line-order-shipped.png)

2. 在頂端列中，按一下&#x200B;**從草稿開始設計**&#x200B;內容區塊

   ![在頂端列中，從草稿設計內容區塊](assets/build-journey-click-design-from-scratch.png)

3. 在左方列中，移至「元件」標籤，並從「結構」容器下方將「n」拖放&#x200B;**1:1欄**&#x200B;至畫布

   ![將1:1資料行結構元素拖曳至電子郵件畫布](assets/build-journey-drag-1-1-column-onto-canvas.png)

4. 然後從「內容」容器下拖曳&#39;n，將&#x200B;**Text**&#x200B;元件拖放到您的&#x200B;**1:1欄**

   ![將文字元件拖曳至1:1欄](assets/build-journey-drag-text-component-into-column.png)

5. 按一下文字元件並&#x200B;**刪除目前的文字**，然後按一下&#x200B;**新增Personalization**&#x200B;圖示

   刪除預設文字後![新增Personalization圖示](assets/build-journey-click-add-personalization-icon.png)

6. 在左側邊欄中，按一下&#x200B;**內容屬性**&#x200B;資料夾，然後導覽至&#x200B;**Journey Orchestration** -> **動作**，並選取&#x200B;**GetShippingDetails**

   ![選取「內容屬性 — Journey Orchestration — 動作」下的GetShippingDetails](assets/build-journey-select-getshippingdetails-contextual-attribute.png)

7. 現在，在電子郵件的正文中&#x200B;**複製並貼上以下JSON**&#x200B;至Personalization **編輯器**

   ```json
   {{profile.person.name.firstName}}, your order has shipped
   ETA:
   Tracking Number:
   ```

8. 新增個人化欄位，如下所示（**按一下左側邊欄**&#x200B;欄位旁的加號「+」）：
   - **ETA：** `eta`
   - **追蹤號碼：** `tracking_number`

   ![ETA和追蹤號碼個人化欄位已新增至電子郵件](assets/build-journey-add-eta-tracking-number-fields.png)

   >[!NOTE]
   >
   >按一下&#x200B;**+符號**，將個人化屬性從邊欄新增至畫布。  它會將其放在游標所在的位置，以確保您正確「排好」

   >[!NOTE]
   >
   >您的電子郵件將使用內容屬性（ETA和追蹤編號）和設定檔屬性（名字）的組合。 如果您想要新增其他設定檔屬性，可以按一下「設定檔屬性」標籤，然後選取您看到的任何專案。
   >
   >![新增其他設定檔屬性的[設定檔屬性]索引標籤](assets/build-journey-profile-attributes-tab.png)

9. 在熒幕底部按一下&#x200B;**驗證**&#x200B;按鈕，並確定您沒有錯誤

   ![熒幕底部顯示沒有錯誤的「驗證」按鈕](assets/build-journey-click-validate-button.png)

10. 如果一切正常，請按一下右上方的&#x200B;**儲存按鈕**
11. 再按一下右上方的&#x200B;**儲存**&#x200B;按鈕，然後按一下左上方的&#x200B;**\&lt; — 左箭頭**

![儲存右上角及左上角的按鈕和後退箭號](assets/build-journey-save-and-back-arrow.png)

1. 最後，按一下左上方的&#x200B;**\&lt;上一頁圖示**&#x200B;以回到歷程畫布

左上方的![返回圖示以返回歷程畫布](assets/build-journey-back-icon-to-journey-canvas.png)

>[!TIP]
>
>然後再次按一下&#x200B;**上一步**&#x200B;按鈕……開玩笑！ 這是本節😜的最後一個按鈕



### 覆寫電子郵件引數

回到主要「歷程畫布」，在「電子郵件」節點上，確定您可以看到唯讀欄位（您可能需要按一下「**顯示唯讀欄位**」圖示）

![在歷程畫布的電子郵件節點上顯示的唯讀欄位](assets/build-journey-show-read-only-fields-email-node.png)

1. 向下捲動至&#x200B;**電子郵件引數**&#x200B;並按一下&#x200B;**啟用引數覆寫**&#x200B;圖示

   ![啟用電子郵件引數下的引數覆寫圖示](assets/build-journey-enable-parameter-override.png)

2. 按一下空白文字方塊，然後在左側邊欄中向下展開至&#x200B;**內容** -> **orderShipped** -> **\_dep**，然後按一下&#x200B;**personalEmail**&#x200B;欄位。  然後按一下「**確定」按鈕**
（請注意，以底線開頭的租使用者名稱稱可能因您的環境而不同，在此範例中為_dep。）

   ![Select orderShipped內容_dep](assets/build-journey-select-personalemail-context-field.png)下的personalEmail欄位

   >[!WARNING]
   >
   >這是很危險的做法，除非您需要在生產設定中使用，否則請避免使用。  這將覆寫Journeys在設定檔上尋找以執行訊息的預設位置。



3. 按一下右上方的&#x200B;**儲存按鈕**，然後按一下左上方的&#x200B;**上一箭號** \&lt; — 以&#x200B;**關閉**&#x200B;歷程

![儲存按鈕並往後箭號以關閉歷程](assets/build-journey-save-and-close-journey.png)

## 重述

能夠回應Order Shipped事件觸發器的已發佈歷程，從外部服務取得ETA並傳送電子郵件。
