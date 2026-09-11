---
hold: true
title: 匯入環境檔案
description: 匯入Postman環境檔案，並設定像是整個bootcamp內API呼叫所需的EDGE_REGION等全域變數。
doc-type: article
solution: Experience Platform
exl-id: a5d45656-e3f5-4207-823c-ad33d4ef26a4
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---


# 匯入環境檔案

## 目標

在本頁中，您將匯入Postman環境檔案。  此檔案包含一些全域變數，這些變數將用於您在整個bootcamp中的其他Labs進行的各種API呼叫。

## 匯入環境檔案

1. 下載&#x200B;**AJO Bootcamp.postman\_environment.json**&#x200B;檔案：

下載檔案 — [AJO Bootcamp.postman_environment.json](assets/ajo-bootcamp.postman_environment.json)

&#x200B;2. 在本機電腦上啟動Postman。
&#x200B;3. 如有必要，請切換到您用於這些Labs的Workspace （如果您完全使用Workspace），然後按一下&#x200B;**匯入**&#x200B;按鈕。

![Postman開始匯入](assets/import-environment-file-click-import-button.png)

&#x200B;4. 將&#x200B;**AJO Bootcamp.postman\_environment.json**&#x200B;檔案的本機URL貼入匯入模組文字方塊，或將它拖放到匯入對話方塊中。  這應該會觸發自動匯入

![Postman匯入對話方塊，顯示透過URL貼上檔案URL的選項](assets/import-environment-file-import-button-overlay.png "Postman匯入")

![Postman匯入對話方塊接受透過拖放方式捨棄的檔案](assets/import-environment-file-drag-and-drop-import.png "Postman透過拖放方式匯入")

&#x200B;5. 匯入後，按一下左側邊欄中的&#x200B;**環境**&#x200B;索引標籤，以驗證環境是否存在。 您會看到AJO Bootcamp環境現在可供您使用。

![驗證環境匯入](assets/import-environment-file-validate-environment-imported.png)

## 設定環境變數

Postman是專為測試及與API互動而設計。 不過，我們使用它來模擬來自瀏覽器的AEP Web SDK點選，或用於伺服器端的即時資料收集呼叫。 雖然從最嚴格的術語來看，這些仍然是API呼叫，但不是典型的API呼叫，需要在標頭中放入授權權杖之類的專案。 這些Labs中的環境變數主要用於URL路徑中的變數（有一個用於標頭）。

1. 如有必要，請按一下Postman左側邊欄中的&#x200B;**環境**&#x200B;索引標籤
2. 按一下&#x200B;**AJO Bootcamp**&#x200B;環境檔案。 您會看到一些需要填寫的值

![需要填入空值的Postman環境變數](assets/import-environment-file-values-need-filling-in.png "驗證環境中的郵遞員變數")

&#x200B;3. 現在跳過DATASTREAM\_CONFIG值。 您將在稍後的實驗室中建立資料串流設定。
&#x200B;4. 使用下表作為查閱，以最接近您實際放置此Bootcamp的區域代碼更新&#x200B;**EDGE\_REGION**&#x200B;欄位。

| **地區** | **地區碼** |
| ---------- | --------------- |
| 美國西部 | 或2 |
| 美國東部 | va6 |
| 歐洲 | irl1 |
| 澳洲 | aus3 |
| 日本 | jpn3 |
| 亞洲 | spg3 |

完成後，您的環境檔案應該看起來類似這樣：



![驗證Postman區域變數](assets/import-environment-file-region-variable-set.png)

&#x200B;5. 您現在需要儲存環境變數；不過Postman UI中沒有儲存按鈕。 使用Windows或Mac快速鍵進行儲存（例如Windows上的Ctrl+s）。 當您在Postman UI的右下方看到&#x200B;**已儲存的變更**&#x200B;訊息時，就表示您的變更已儲存：

![驗證已儲存的變更](assets/import-environment-file-changes-saved-confirmation.png)

>[!TIP]
>
>恭喜！ 您已完成Postman環境檔案
