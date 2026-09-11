---
hold: true
title: 測試歷程
description: 使用歷程測試模式模擬器來觸發「訂單已出貨」事件，並在發佈之前確認觸發器和動作邏輯正確執行。
doc-type: article
solution: Experience Platform
exl-id: fc3dbfb9-b44b-4866-acc9-398a8b52f2b9
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---


# 測試歷程

## 學習目標

使用歷程測試工具，驗證事件觸發器和歷程邏輯已正確設定。

## 測試歷程

1. 如果您沒有看到歷程清單，請按一下左側邊欄上的&#x200B;**歷程**&#x200B;和&#x200B;**瀏覽標籤**
2. 按一下您的&#x200B;**歷程**&#x200B;以開啟
3. 按一下&#x200B;**警示**&#x200B;並確保沒有錯誤（警告正常）

![開啟歷程後，警示面板未顯示任何錯誤](assets/test-journey-alerts-no-errors.png)

>[!NOTE]
>
>**什麼是CJMMAS - 2001-200**
>
>表示電子郵件變體缺少選擇退出連結

&#x200B;4. 按一下&#x200B;**模擬**，然後在左側選取&#x200B;**測試模式**

在左側[模擬]下選取了![測試模式](assets/test-journey-select-test-mode.png)



>[!NOTE]
>
>可能需要一分鐘的時間準備就緒。 在這段期間，將無法使用觸發事件按鈕。



&#x200B;5. 按一下&#x200B;**觸發事件**&#x200B;並填寫這些屬性：
   - **事件型別**： `orders.shipped`
   - **個人電子郵件**： `henry.creel@emailsim.io`
   - **訂單識別碼**： `123`
&#x200B;6. 按一下&#x200B;**傳送** （請注意，按一下傳送後需要幾秒鐘才會回應）

![觸發已填寫的事件表單並按一下](assets/test-journey-trigger-event-send.png)傳送

&#x200B;> [!WARNING]
>
>有些學生收到錯誤訊息，需要傳送此訊息幾次。 您可能需要執行此動作&#x200B;**多次**。
>
>**有時**&#x200B;第一次傳送會產生下列錯誤：
>
>**入口不存在（參考識別碼： 3216a850-c40d-11f0-8fa5-73d1522cc9a2）**
>
>如果發生錯誤，請按一下&#x200B;**觸發事件**，然後再按&#x200B;**傳送**。  您可能必須&#x200B;**多次**。



&#x200B;7. 在&#x200B;**結果** ->下，按一下左側的&#x200B;**顯示記錄檔**

觸發測試事件後![在結果底下顯示記錄選項](assets/test-journey-show-log-results.png)

&#x200B;> [!NOTE]
>
>有些收到錯誤的學生有時會收到不同的記錄，顯示空白的執行個體陣列`{"instances": []}`。 這不是阻斷因素，請繼續進行下一步驟。

您應該會在記錄檔中看到類似以下的內容：

>[!NOTE]
>
>我們正在尋找使用的關鍵欄位： **actionsHistory**、**transitionsHistory**、**eta**、**tracking_number**、**eventType**、**personalEmail**&#x200B;以及&#x200B;**orderID**。

```json
{
  "actionsHistory": {
    "8919055f-1b00-4a43-8bd6-c8af894474b2": {
      "eta": "11/27/2025",
      "tracking_number": "091204404",
      "jo_status_code": "http_200"
    }
  },
  "transitionsHistory": {
    "orderShipped (1158856989)": {
      "eventType": "orders.shipped",
      "_id": "joTestModeEvent_5abbfdcd-561d-45a7-ba42-d0640539831a",
      "_dep": {
        "personalEmail": "henry.creel@emailsim.io"
      },
      "order": {
        "orderID": "123"
      },
      "timestamp": "2025-11-17T23:30:49.576289372Z"
    }
  }
}
```



&#x200B;8. **關閉**&#x200B;瀏覽器&#x200B;**標籤**
&#x200B;9. 右上角的&#x200B;**關閉測試模式**

右上方的![關閉測試模式按鈕](assets/test-journey-close-test-mode.png)

&#x200B;10. 按一下右上角的&#x200B;**發佈**&#x200B;歷程

右上角歷程的![發佈按鈕](assets/test-journey-publish-journey.png)

&#x200B;11. 按一下左上方的\&lt; — 箭頭&#x200B;**關閉**&#x200B;**歷程**

左上方的![向後箭頭以關閉歷程](assets/test-journey-close-journey-back-arrow.png)

接下來，我們將傳送真實的「訂購已出貨事件」至AEP

## 重述

歷程已通過設定驗證，且可接收事件
