---
hold: true
title: 沙箱存取
description: 在啟動Labs之前，請確認您的Postman環境可以成功擷取指派的Experience Platform沙箱。
doc-type: article
solution: Experience Platform
exl-id: c841e497-a695-4d3f-85e6-d653478cad1e
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 0%

---


# 沙箱存取

在繼續之前，請再次確認您的存取權是否合法。 執行下列步驟：

1. 開啟標題為`Check Sandbox Access`的資料夾，然後按一下標題為`Retrieve Your Sandbox`的呼叫
1. 接下來，在Postman的右上角，您會看到「環境」下拉式方塊。  請務必選取`AEP Bootcamp`環境
1. 按一下`Send`按鈕以執行呼叫

![Postman要求窗格，用於在傳送前擷取您的沙箱呼叫](assets/sandbox-access-check-sandbox-request.png "擷取您的沙箱API呼叫")



成功的回應看起來像這樣：

![200 OK回應確認已成功擷取指派的沙箱](assets/sandbox-access-successful-response.png "200 OK成功的沙箱要求")

>[!NOTE]
>
>**name**&#x200B;值應該與您的Postman環境中的sandbox\_name變數相符

>[!TIP]
>
>恭喜！  您已準備好開始使用Experience Platform API
