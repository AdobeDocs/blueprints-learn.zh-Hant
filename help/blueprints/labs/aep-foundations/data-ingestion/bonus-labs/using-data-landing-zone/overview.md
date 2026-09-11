---
hold: true
title: 使用資料登陸區域
description: 使用SAS URL安裝並設定Azure Storage Explorer以連線至Adobe Experience Platform資料登陸區域。
doc-type: overview-page
solution: Experience Platform
exl-id: d61bef25-7039-450d-a8e7-01bb12e8df7c
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---


# 使用資料登陸區域

## 先決條件

如果您尚未下載Azure Storage Explorer，請立即下載，因為這是本實驗室的必要條件。  您可以透過以下連結找到下載專案：

[下載Azure儲存體總管](https://azure.microsoft.com/en-us/blog/microsoft-azure-data-lake-storage-adls-in-storage-explorer-public-preview/)

1. 安裝應用程式
1. 首次啟動時接受使用者授權合約

在Azure Storage Explorer](assets/overview-end-user-license-agreement-screen.png "使用者授權合約畫面中![使用者授權合約畫面")


## 使用Experience Platform設定Azure儲存體總管

1. 開啟Azure Storage Explorer，然後按一下&#x200B;**選取資源圖示**，然後選取&#x200B;**ADLS Gen 2容器或目錄**

![選取ADLS Gen2容器或目錄作為Azure儲存總管中的資源](assets/overview-choose-the-resource-as-shown-above.png)



1. 選取&#x200B;**共用存取簽章URL (SAS)**&#x200B;並按一下&#x200B;**下一步**

![選擇SAS URL選項作為連線模式](assets/overview-choose-the-sas-url-option-as-the-mode-of-connection.png "選擇SAS URL選項作為連線模式")



1. 輸入顯示名稱作為&#x200B;**資料登陸區域**

>[!NOTE]
>
>您必須提供SAS URL，才能繼續此步驟。  您可以從Experience Platform取得此專案，在下個步驟中就會看到。

![命名連線資料登陸區域](assets/overview-name-the-connection.png "命名連線")



1. 前往Adobe Experience Platform ，並執行下列操作以導覽至資料登陸區域：

- 導覽至&#x200B;**來源 — >目錄**
- 在來源底下選取&#x200B;**雲端儲存空間**
- 接著找出&#x200B;**資料登陸區域**&#x200B;卡片
- 按一下資料登陸區域卡片，然後在右側邊欄上按一下&#x200B;**檢視認證**

![在Adobe Experience Platform中具有檢視認證選項的資料登陸區域來源卡片](assets/overview-data-landing-zone-view-credentials.png "在Adobe Experience Platform中存取資料登陸區域Source卡片")



1. 從顯示的模組複製&#x200B;**SASUri**。

導覽回Azure Storage Explorer，並將&#x200B;**SASUri值**&#x200B;貼到&#x200B;**Blob容器或目錄SAS URL**&#x200B;中。您在上一步中留空

![將SASUri值從Experience Platform複製到Azure Storage Explorer](assets/overview-copy-sas-uri-into-azure-storage-explorer.png "從Adobe Experience Platform複製SAS URL認證，並將其複製到Azure Storage Explorer")



1. 按一下[下一步]****&#x200B;繼續

![將SAS URL認證複製到連線資訊的SAS URL區段](assets/overview-copy-sas-url-into-connection-info.png "將SAS URL認證複製到連線資訊的SAS URL區段")



1. 在[摘要]畫面上，按一下[**連線**]

![具有[連線]按鈕的摘要畫面](assets/overview-connect-screen.png "連線畫面")



您現在應該會看到如下所示的畫面

![Azure Storage Explorer顯示成功連線的資料登陸區域帳戶](assets/overview-successfully-connected-account.png)

> [!TIP]
>
>恭喜！  您已成功設定Azure儲存體總管
