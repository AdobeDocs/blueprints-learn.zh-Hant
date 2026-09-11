---
hold: true
title: 設定串流目的地
description: 使用webhook端點、治理原則、對象和欄位對應來設定HTTP API串流目的地，以測試區段啟用。
doc-type: article
solution: Experience Platform
exl-id: c52d301f-b308-40fc-a59c-ace1c96ccd13
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '736'
ht-degree: 0%

---


# 設定串流目的地

>[!NOTE]
>
>如果您已設定串流目的地，請跳至下一步！

## 取得webhook URL

>[!NOTE]
>
>我們將在這裡使用webhook，以便檢視資料是否已到達我們要傳送的目的地。 在真實世界的情境中，我們會改為登入該目的地，並使用他們的工具來檢視已到達的專案。

1. 在瀏覽器的新索引標籤中開啟下列連結 — > [https://webhook.site](https://webhook.site/)
1. 複製您看到的唯一URL，並將其儲存在安全的地方

![Webhook.site複製您的唯一URL](assets/setup-streaming-destination-webhooksite-copy-your-unique-url.png "Webhook.site複製您的唯一URL")


## 設定HTTP API目的地

>[!NOTE]
>
>我們使用串流目的地作為將此資料傳送給第三方（例如Facebook）的Proxy。 在真實世界中，您可以使用Facebook目的地來取代HTTP API目的地，以便將資料傳送至Facebook。

在Experience Platform UI中，執行下列操作以導覽至目的地目錄

1. 按一下左側邊欄中的&#x200B;**目的地**
1. 按一下頂端邊欄上的&#x200B;**目錄**
1. 在搜尋方塊中輸入&#x200B;**http**
1. 按一下&#x200B;**設定**&#x200B;按鈕以設定HTTP API目的地

![瀏覽至HTTP API目的地並起始安裝程式](assets/setup-streaming-destination-navigate-to-http-api-destination.png "瀏覽至HTTP API目的地並起始安裝程式")

>[!NOTE]
>
>您正在使用實驗室的HTTP API串流目的地，以示範現實世界的串流聯結器如何運作。

## 設定

1. 連線型別&#x200B;**無**
1. 按一下&#x200B;**連線至目的地**

![連線到目的地](assets/setup-streaming-destination-connect-to-destination.png "連線到目的地")

>[!NOTE]
>
>通常我們會在此階段新增任何驗證認證，但此webhook不需要任何認證。



3. 請依照以下步驟填寫您目的地的設定詳細資料：

- **名稱** -> `Streaming DEP Webhook - [Your Initials]`
- **描述** -> `[your webhook endpoint you copied above]`
- **端點** -> ` [your webhook endpoint you copied above]`
- **查詢引數** -> `leave blank`
- **標頭** -> `leave blank`
- 包含區段名稱 — >切換開啟
- 包含區段時間戳記 — >切換開啟

完成後，請確保您的設定符合以下內容。  如果看起來不錯，請按一下右上方的&#x200B;**下一步**&#x200B;按鈕，繼續下一步

![設定目的地欄位，包括名稱、說明、端點和切換](assets/setup-streaming-destination-configure-destination-fields.png)

>[!CAUTION]
>
>端點、標題和查詢引數儲存後就無法在UI中變更

## 定義治理

1. 從行銷動作中選取&#x200B;**跨網站目標定位**
1. 完成時，按一下&#x200B;**下一步**&#x200B;按鈕以繼續下一個步驟

![目的地的治理畫面](assets/setup-streaming-destination-governance-screen-for-destinations.png "目的地的治理畫面")

>[!NOTE]
>
>您可以進一步瞭解Experience League中的治理政策
>
>[https://experienceleague.adobe.com/docs/experience-platform/data-governance/policies/overview.html?lang=en#core-actions](https://experienceleague.adobe.com/docs/experience-platform/data-governance/policies/overview.html?lang=en#core-actions)

## 選取對象

1. 選取所有對象
1. 完成時，按一下&#x200B;**下一步**&#x200B;按鈕以繼續下一個步驟

![選取所有對象](assets/setup-streaming-destination-select-all-audiences.png)

## 新增對應

>[!NOTE]
>
>我們在這裡從設定檔新增欄位。 如果該欄位沒有資料，我們可能不會看到任何資料傳遞至目的地。 設定檔和事件在一段時間內進行多次更新，有時會導致目的地多次觸發並傳送多個負載。

1. 按一下&#x200B;**新增欄位**&#x200B;以將欄位新增至結構描述
1. 在結構描述欄位輸入方塊中輸入&#x200B;**model**，並從出現的欄位清單中選取&#x200B;**\_dep.activeProducts\[0].model**&#x200B;欄位
1. 變更欄位名稱中的&#x200B;**\[0]**&#x200B;為&#x200B;**\[\*]**。  您的最終欄位現在應該顯示為&#x200B;**\_dep.activeProducts\[\*].model**
1. 完成時，按一下&#x200B;**下一步**&#x200B;按鈕以繼續下一個步驟



![選取模型欄位](assets/setup-streaming-destination-select-model-field.png "選取模型欄位")



![最終模型欄位](assets/setup-streaming-destination-final-model-field.png "最終模型欄位")

>[!NOTE]
>
>這是對應設定檔上的欄位，而非體驗事件。 即使我們根據對象資格將設定檔傳送至目的地，但我們必須記住正在發生的事情。
>
>1. 事件已進入
>2. 受眾根據規則符合設定檔的資格
>3. 資格儲存在設定檔上
>4. 通知目的地設定檔已符合資格
>5. 目的地會傳送設定檔。 這表示當目的地要傳送設定檔時，它不再知道觸發對象評估的事件。

## 檢閱步驟

驗證您的最終目的地是否良好，然後按一下&#x200B;**完成**&#x200B;按鈕

![目的地檢閱畫面](assets/setup-streaming-destination-destination-review-screen.png "目的地檢閱畫面")

>[!NOTE]
>
>目的地現在已設定完畢，並等候根據評估速度新增的所有區段的區段資格：
>
>- Edge
>- 串流
>- 批次

>[!NOTE]
>
>一開始設定目的地時，請務必牢記以下事項：
>
>- 任何回填（現有的合格設定檔）開始啟用最多需要2小時
>- 新新增的對象需要最多20分鐘才能開始啟用
