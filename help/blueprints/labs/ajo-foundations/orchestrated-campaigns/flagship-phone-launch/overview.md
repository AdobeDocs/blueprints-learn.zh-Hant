---
title: 旗艦手機上市
description: 在旗艦電話推出後，取得建立協調行銷活動的概覽，以帳戶持有人和個別行作為目標，提供SMS升級優惠。
doc-type: overview-page
solution: Experience Platform
exl-id: 04c509f1-aa10-4d29-aa59-5e627b79e498
source-git-commit: df6c1852a6e0357dc9f166c88e77dcf9d334f955
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%
---

# 旗艦手機上市

## 先決條件

>[!WARNING]
>
>下列Labs必須在開始本實驗前完成

- **Postman安裝程式** **—>** [Postman安裝](../../postman-setup/postman-installation.md)
- **資料存放區 — 動作中的關聯存放區** **—>** [設定檔目標Dimension](../../data-stores/relational-store-in-action/profile-target-dimension.md)
- **資料存放區 — 設定電子郵件通道 — >** [設定關聯式](../../data-stores/configure-email-channels/configure-for-relational.md)
  *（此設定步驟最多需要3小時才能完成）*

如果您尚未完成這些Labs，請立即完成後再繼續。

>[!CAUTION]
>
>本實驗需要在您的沙箱中安裝SMS認證才能完成設定SMS通道步驟 — 不會傳送實際訊息，但必須有Twilio認證。 如果您是自行設定進度且尚未布建這些專案，請參閱[設定](../../setup.md)。

## Lab概述

在此影片中，您會瞭解旗艦級手機上市使用案例如何對應至精心安排的促銷活動，在建置促銷活動目標定位帳戶持有人和個別產品線之前，重述重要的思考問題和架構。

>[!VIDEO](https://video.tv.adobe.com/v/3486217/)

## 學習目標

- 使用各種工作流程活動建立協調的行銷活動
- 使用「建立對象」活動來建構對象
- 瞭解如何設定簡訊頻道
- 將對象儲存至對象入口網站
- 使用電子郵件和簡訊訊息鎖定客戶帳戶和個別行



## 使用案例說明

製造商推出最新旗艦裝置後，立即傳送目標訊息給帳戶持有人，並列出使用舊型號的使用者，邀請他們升級至最新的行動運算技術。

**索引鍵圖說文字：**

- 將所有客戶明細行的對象儲存至對象入口網站
- 透過訊息定位個別行和帳戶持有者（您將使用簡訊）

>[!NOTE]
>
>此情境會模擬&#x200B;**電信合約升級行銷活動**，其中次要（相依）線路會接收目標升級訊息。
