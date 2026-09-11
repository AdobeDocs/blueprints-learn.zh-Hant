---
hold: true
title: 設定來源
description: 將歷史訂單JSON檔案上傳至資料登陸區域，並設定以訂單結構描述為目標的新資料流。
doc-type: article
solution: Experience Platform
exl-id: 046d50ad-687e-4cdb-a8b1-3c55ab39b68e
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---


# 設定來源

## 上傳範例檔案

您需要透過Azure Storage Explorer將範例資料檔案上傳至您的資料登陸區域，以便在實驗室期間使用。  若要這麼做，請執行下列動作：

1. 下載[範例檔案](../../../sample-files.md)
1. 拖放和/或上傳&#x200B;**Lab\_Historical\_Orders.json**&#x200B;檔案至您從上方儲存的資料登陸區域。



上傳後，您的畫面看起來應該類似下面的熒幕擷圖。

![Lab_Historical_Orders.json檔案已上傳至資料登陸區域](assets/setup-source-lab-historical-orders-json-uploaded-to-dlz.png "Lab_Historical_Orders.json檔案已上傳至DLZ")

## 導覽至來源

1. 前往Adobe Experience Platform並導覽至： **來源** -> **目錄** -> **雲端儲存空間**
1. 按一下資料登陸區域的&#x200B;**設定** / **新增資料**

![瀏覽至[來源] > [目錄] > [雲端儲存空間]以設定資料登陸區域](assets/setup-source-navigate-to-data-landing-zone-source.png "來源 — 資料登陸區域")

>[!NOTE]
>
>如果您已經從先前的批次擷取實驗室設定了連線，您會看到&#x200B;**新增資料**&#x200B;作為預設動作



## 預覽檔案

1. 選取&#x200B;**Lab\_Historical\_Orders.json**&#x200B;檔案並預覽其內容
1. 按一下畫面右上角的&#x200B;**[下一步]**&#x200B;以繼續下一步

![選取並預覽Lab_Historical_Orders.json檔案內容](assets/setup-source-select-and-preview-lab-historical-orders.png "選取並預覽Lab_Historical_Orders.json檔案")

## 設定資料流

1. 在資料流詳細資訊畫面中，選擇&#x200B;**新資料集**
1. 將輸出資料集命名為&#x200B;**Orders - YourNameHere**
1. 選取結構描述名稱&#x200B;**dep：訂單**
1. 開啟&#x200B;**設定檔資料集**&#x200B;切換方塊
（如果您未開啟此功能，設定檔存放區將無法監視是否有新資料進入此資料集，因此不會將此資料擷取到設定檔中）
1. 開啟&#x200B;**啟用部分擷取**
（如果您未開啟此功能，如果其中一個記錄發生錯誤，擷取可能會失敗）
1. 將資料流名稱設為&#x200B;**Orders - Backfill - YourNameHere**
1. 開啟所有警示&#x200B;**來源資料流開始/成功/失敗**

![針對訂單資料集設定的資料流詳細資訊畫面](assets/setup-source-dataflow-details-for-orders.png "訂單的資料流詳細資訊")

>[!CAUTION]
>
>請確定您已針對設定檔和部分擷取&#x200B;**啟用**&#x200B;您的資料集。

按一下畫面右上角的&#x200B;**[下一步]**&#x200B;以繼續下一步
