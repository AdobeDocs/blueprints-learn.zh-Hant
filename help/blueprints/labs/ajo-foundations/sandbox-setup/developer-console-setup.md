---
hold: true
title: Developer Console設定
description: 針對DEP CLI使用的Experience Platform和Journey Optimizer API，建立具有OAuth伺服器對伺服器憑證的Adobe Developer Console專案。
doc-type: article
solution: Experience Platform
exl-id: 8b8f2a3e-2f4a-4b0e-9c5a-6e0c2b7a1d4f
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---


# Developer Console設定

>[!WARNING]
>
>只有在您按照自己的進度進行Labs時，才需要這樣做。 如果您正在參加即時培訓課程或活動，您的沙箱已為您部署。

DEP CLI會使用Adobe Developer Console專案中的OAuth伺服器對伺服器認證，對您的沙箱進行驗證。 此頁面會逐步說明如何建立該專案。 您只需要執行此操作一次 — 只要您新增下述兩個API，相同的憑證就能在AEP基礎和AJO架構基礎追蹤之間運作。

>[!NOTE]
>
>如果您已經有具有Adobe Experience Platform認證的Developer Console專案（如有需要，還有Adobe Journey Optimizer），請略過本節，並直接移至[部署指示](deployment-instructions.md)。

## 先決條件

- 擁有您組織開發人員存取許可權的Adobe ID
- 空白且型別為`dev`的Adobe Experience Platform沙箱
- 擁有授與沙箱之所有許可權的Adobe Experience Platform角色（如果您不確定，請詢問您的系統管理員）

## 建立專案

1. 前往[Adobe Developer Console](https://developer.adobe.com/console)並登入
1. 如果您可以存取多個組織，請使用右上角的組織切換器來選取正確的組織
1. 選取&#x200B;**建立新專案**
1. 將專案重新命名為您稍後可辨識的專案（例如，`DEP Sandbox`）

## 新增Experience Platform API

1. 從專案概述中，選取&#x200B;**新增API**
1. 選擇&#x200B;**Adobe Experience Platform**&#x200B;產品圖示，然後選取&#x200B;**Adobe Experience Platform API**
1. 選取&#x200B;**下一步**
1. 選擇&#x200B;**OAuth伺服器對伺服器**&#x200B;做為驗證型別，並選取&#x200B;**下一步**
1. 提供認證名稱，並選取&#x200B;**下一步**
1. 選取與您使用的沙箱相符的產品設定檔，然後選取「**儲存已設定的API**」

## 新增Adobe Journey Optimizer API

1. 從專案概述中，選取&#x200B;**新增API**
1. 選擇&#x200B;**Adobe Journey Optimizer**&#x200B;產品圖示並選取相關的API
1. 選取&#x200B;**OAuth伺服器對伺服器**
1. 選取相同的產品設定檔，然後選取&#x200B;**儲存設定的API**

>[!NOTE]
>
>重複使用您在上面建立的認證，而不是建立新的認證 — CLI只需要一組認證，而且有合併的範圍。



## 收集您的值

開啟認證的&#x200B;**OAuth伺服器對伺服器**&#x200B;總覽頁面。 CLI的環境檔案需要4個值：

| **開發主控台值** | **環境檔案欄位** |
| --------------------- | ------------------------------- |
| 使用者端ID | `API_KEY` |
| 使用者端密碼 | `CLIENT_SECRET` |
| 組織ID | `IMS_ORG` （結束於`@AdobeOrg`） |
| 範圍 | `SCOPES` |

>[!NOTE]
>
>複製認證頁面上顯示的預設範圍 — 您不需要手動新增任何內容。 如果您新增了上述兩個API，範圍清單會自動包含這兩個。

請保持此頁面開啟，或將這四個值複製到安全的位置。 您會在追蹤設定指南的下一個步驟中，將這些檔案貼到CLI的環境檔案中。
