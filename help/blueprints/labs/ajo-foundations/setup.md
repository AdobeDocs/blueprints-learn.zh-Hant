---
title: 設定
description: 在啟動Postman基礎實驗室之前，完成所需的沙箱部署和AJO設定步驟。
doc-type: article

solution: Experience Platform
exl-id: 7c1a9e3d-5b8f-4a2e-9c6d-3f7b0e4a8c2d
source-git-commit: df6c1852a6e0357dc9f166c88e77dcf9d334f955
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 1%
---

# 設定

在開始AJO基礎實驗室之前，請完成下列設定步驟。 您需要採取哪些步驟，取決於您如何參加這個訓練營。

## 沙箱設定

>[!NOTE]
>
>如果您參加即時培訓課程或活動，您的沙箱已為您部署 — 請略過本節，直接前往下面的Postman設定。

如果您還沒有已部署實驗室資產的工作中沙箱，請完成以下步驟：

- [Developer Console設定](sandbox-setup/developer-console-setup.md)
- [部署指示](sandbox-setup/deployment-instructions.md)

## Postman設定

無論您的沙箱如何布建，此課程中的Labs都需要Postman。 請先完成下列作業再繼續：

- [Postman安裝](postman-setup/postman-installation.md)
- [匯入環境檔案](postman-setup/import-environment-file.md)
- [匯入API集合](postman-setup/import-api-collection.md)

## 管道必要條件

此訓練營稍後有兩個實驗室，取決於外部帳戶，只有自行進度的學習者才需要安排 — 如果您正在參加即時培訓課程或活動，這些已為您布建。

### 委派的子網域

[設定電子郵件通道](data-stores/configure-email-channels/overview.md)實驗室 — 以及依賴它的所有專案（[正在執行的訊息傳遞](orchestrated-campaigns/message-delivery-in-action/overview.md)、[購買後的興奮](journeys/post-purchase-excitement/overview.md)以及[AJO品牌](content-authoring-with-ai/overview.md)） — 需要委派給Adobe的子網域才能傳送電子郵件。 如果您還沒有網域，請向任何網域註冊機構（例如Namecheap）註冊一個網域。 然後，若要將其子網域（例如`email.yourdomain.com`）委派給Adobe，請依照Adobe的[子網域委派指示](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/delegate-subdomains/delegate-subdomain)操作。

>[!NOTE]
>
>子網域委派可能需要一些時間才能傳播。 在您計畫前往設定電子郵件通道實驗室之前，請先開始此委派。

### SMS 認證

[旗艦手機上市](orchestrated-campaigns/flagship-phone-launch/overview.md)實驗室會透過Twilio設定SMS頻道。 不會傳送任何訊息，但您需要工作認證才能完成設定。 最簡單的選項是免費的[Twilio試用帳戶](https://www.twilio.com/try-twilio) — 請參閱Twilio的[快速入門手冊](https://www.twilio.com/docs/usage/tutorials/how-to-use-your-free-trial-account)，瞭解如何註冊及尋找您的帳戶SID和驗證權杖。
