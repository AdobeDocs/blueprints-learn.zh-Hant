---
hold: true
title: 設定來源
description: 建立HTTP API串流帳戶，並設定資料流以將客戶帳戶JSON資料串流到已啟用設定檔的資料集中。
doc-type: article
solution: Experience Platform
exl-id: a5c02337-8af3-45dc-82a0-fa9731892fe4
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%

---


# 設定來源

## 導覽至串流來源

1. 前往Adobe Experience Platform UI並導覽至&#x200B;**來源**
1. 按一下頂端導覽列中的&#x200B;**目錄**
1. 從來源清單中選取&#x200B;**串流** （確定已選取[所有來源]選項按鈕）
1. 按一下HTTP API的&#x200B;**設定** / **新增資料**

![建立新HTTP API來源帳戶的步驟順序](assets/setup-source-sequence-of-steps-to-create-a-http-api-account.png)



## 建立HTTP API帳戶

您首先需要做的就是建立新帳戶。 此帳戶儲存有關如何處理驗證的詳細資訊，以及流傳入的資料是否與XDM相容（即已經符合基礎XDM結構描述的結構）

執行下列工作：

1. 選取&#x200B;**新帳戶**&#x200B;並新增下列詳細資料：
   - 帳戶名稱 — > `Streaming Ingestion - <Your Initials>`
1. 讓&#x200B;**啟用驗證**&#x200B;的切換保持停用
1. 保留&#x200B;**XDM相容**&#x200B;的核取方塊未勾選
1. 按一下&#x200B;**連線至來源**&#x200B;按鈕以繼續

>[!CAUTION]
>
>請勿開啟&#x200B;**啟用驗證**&#x200B;或勾選&#x200B;**XDM相容**&#x200B;的方塊。 這會破壞實驗室

您的畫面應如下所示：

按一下新HTTP API帳戶的[連線到來源]後![畫面](assets/setup-source-connect-to-source-screen.png)



您現在應該會看到綠色核取方塊，其中顯示「已連線」訊息。 按一下右上角的&#x200B;**下一步**&#x200B;按鈕以繼續設定資料流：

設定HTTP API帳戶後，![綠色核取方塊顯示連線訊息](assets/setup-source-green-checkbox-with-connected-message.png "您應該會看到綠色核取方塊顯示連線")



## 上傳範例資料

>[!NOTE]
>
>如果尚未下載，請務必下載[範例檔案](../sample-files.md)



1. 在畫面的Source資料結構描述區段中，從您從先前實驗室下載的本機檔案系統上傳JSON檔案&#x200B;**Lab\_Single\_Customer\_sample.json**。
1. 上傳檔案後，預覽會顯示如下。 按一下右上角的&#x200B;**下一步**&#x200B;按鈕以繼續。 觀察birth_Date欄位的格式YYYY-MM-DD與您之前在批次擷取實驗室中看到的MM/DD/YYYY格式有何不同。

![管道設計和驗證的上傳Lab_Single_Customer_sample.json記錄預覽](assets/setup-source-sample-customer-record-for-pipeline-design-and-validation.png)

>[!NOTE]
>
>JSON範例檔案包含用於設計和驗證管道的單一記錄。 如果您要捲動，必須按一下XDM節點才能讓節點捲動。



## 設定資料流詳細資料

在此畫面中，您會建立特定資料流，該資料流會利用您設定的HTTP API帳戶。  每個帳戶可以有許多資料流。  此情境中，您需要建立資料流以串流處理客戶帳戶資料。 資料流需要來源帳戶、具有關聯結構的資料集以及設定詳細資料之間的關聯。

執行下列步驟：

1. 建立新資料集並將其命名為 — > `Customer Account Stream - <Your Initials>`
1. 選擇&#x200B;**結構描述**&#x200B;為 — >`dep: Customer Account`
1. 請確定&#x200B;**設定檔資料集**&#x200B;切換為&#x200B;**已啟用**。  若未&#x200B;**啟用**。
1. 更新&#x200B;**資料流名稱**，如下所示：
   - `Customer Account Stream - <Your Initials>`
1. 按一下&#x200B;**下一步**&#x200B;按鈕以繼續

![正在設定客戶帳戶串流資料集的資料流詳細資料](assets/setup-source-configuring-a-dataflow.png)

>[!NOTE]
>
>如果您未為設定檔啟用資料集，則資料只會串流到資料湖。 您不會在「設定檔」或「身分圖表」中看到串流事件。
