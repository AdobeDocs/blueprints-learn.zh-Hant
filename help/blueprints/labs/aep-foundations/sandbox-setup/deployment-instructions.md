---
title: 部署指示
description: 使用DEP CLI將AEP Foundation實驗室套件的結構描述、資料集、資料流和範例設定檔資料部署到您的沙箱。
doc-type: article
solution: Experience Platform
exl-id: 9f2b6d4a-8e1c-4b7a-a3d5-6c9f0e2a4b8d
source-git-commit: 0b33b2740ee7f5af73d64f217b4475650c1d28a0
workflow-type: tm+mt
source-wordcount: '749'
ht-degree: 1%

---


# 部署指示

>[!NOTE]
>
>只有在您按照自己的進度進行Labs時，才需要這樣做。 如果您正在參加即時培訓課程或活動，您的沙箱已為您部署。

AEP Foundation lab pack會使用DEP CLI部署至您的沙箱，這個命令列工具會建立您將在各個Labs使用的結構描述、資料集、資料流和範例資料。

## 部署內容

- 4個身分名稱空間
- 1個方案類別、13個欄位群組、10個方案
- 12個身分描述項、6個關係/參考描述項、3個易記名稱描述項
- 10個目錄資料集
- 1個HTTP API來源連線和10個資料流
- 設定檔資料：單一深度模式設定檔（3個特徵資料集、7個事件資料集）加上3個查詢資料集
- 2個設定檔合併原則和1個對象（任何事件串流，一小時內）

>[!NOTE]
>
>端對端部署大約需要2小時24分鐘，其中大部分是步驟之間的自動等候時間。 CLI會自動強制執行這些等待，因此您不需要自行安排任何時間。

## 先決條件

- **授權權益。** 使用Real-Time CDP的IMS組織的管理許可權（包含串流分段）
- **存取許可權。** 具有目標沙箱上所有許可權的Adobe Experience Platform角色，包括您從[Developer Console安裝程式](developer-console-setup.md)建立的API認證。
- **Developer Console認證。** 包含Adobe Experience Platform API的專案。 如果您還沒有這些專案，請先依照[Developer Console安裝程式](developer-console-setup.md)操作
- **沙箱。** 空白，型別為`dev`，且在「就緒」狀態中至少持續60分鐘，然後再開始部署
- **Node.js.** 任何最新的LTS版本，在Windows或Mac上

## &#x200B;1. 安裝CLI

1. 複製或下載[dep-cli存放庫](https://github.com/adobe/dep-cli)
1. 從`dep-cli`目錄，執行`npm install`
1. 使用`npm start`啟動CLI

>[!NOTE]
>
>執行上述命令前需要Node.js。 如果您尚未安裝Node.js，請先參閱Wiki的[Node.js安裝程式](https://github.com/adobe/dep-cli/wiki/Nodejs-Setup)頁面。 如需完整的安裝詳細資料，包括熒幕擷取畫面以及如何更新現有安裝，請參閱[安裝](https://github.com/adobe/dep-cli/wiki/Installation)Wiki頁面

## &#x200B;2. 設定您的環境檔案

CLI會部署到您的環境檔案指向的任何沙箱，因此這必須在您執行任何操作之前正確設定。

1. 複製`envFiles/sample-env.json`並賦予其新名稱，例如`my-env.json`
1. 開啟檔案，並使用[Developer Console安裝程式](developer-console-setup.md)中的值填入下列欄位：

   | **欄位** | **值** |
   | --------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
   | `API_KEY` | 使用者端ID |
   | `CLIENT_SECRET` | 使用者端密碼 |
   | `IMS_ORG` | 組織ID |
   | `SCOPES` | 必須包括Experience Platform API範圍(openid、session、AdobeID、read_organizations、additional_info.projectedProductContext) |
   | `SANDBOX_NAME` | 您定位的沙箱 — 必須為空白且型別為`dev` |

1. 儲存並關閉檔案

>[!NOTE]
>
>每次執行CLI命令時，都會提示您輸入此檔案的名稱，這樣您便可以在下列的每一個步驟中重複使用它。

## &#x200B;3. 執行AEP基礎功能表

從主功能表中選取&#x200B;**AEP基礎**。 有三個步驟，必須依序執行。

>[!WARNING]
>
>在執行步驟1之前，沙箱必須處於至少60分鐘的「就緒」狀態。

| **步驟** | **它的作用** | **執行之前** |
| ----------------------- | ------------------------------------------------------------------------------------------ | ------------------------------- |
| &#x200B;1. 建立設定檔基底 | 部署身分識別名稱空間、結構描述、資料集、合併原則和對象 | 沙箱「就緒」60分鐘以上 |
| &#x200B;2. 載入設定檔資料 | 建立資料流和串流設定檔及查詢資料 | 步驟1後等待60分鐘以上 |
| &#x200B;3. 檢查設定檔健康狀況 | 驗證所有資料皆已正確載入 | 在步驟2後等待15分鐘以上 |

執行步驟1需要大約2分鐘，執行步驟2需要大約6分鐘，而步驟3是快速驗證，不需要自行等待。 步驟之間的60到15分鐘間隔可讓AEP在幕後完成資料傳播，這是2小時時間軸的大部分。

>[!NOTE]
>
>CLI會自動檢查這些等待時間。 如果您太早執行步驟，它會封鎖並告訴您還有多少分鐘剩餘 — 您不需要自己追蹤時鐘。

>[!NOTE]
>
>如果發生錯誤，可以安全地重新執行步驟2。 它會覆寫現有特徵記錄並略過重複事件。

## 疑難排解

>[!WARNING]
>
>**健康狀態檢查因遺失事件**&#x200B;而失敗。 部分設定檔資料尚未完成傳播。 請再等待15分鐘，然後重新執行檢查設定檔健康狀態。 如果仍然失敗，請重新執行載入設定檔資料，等待15分鐘，然後再次檢查。

**發生其他錯誤。** 您最後可以從CLI的沙箱管理選單重設沙箱，並從步驟1重新部署。

>[!CAUTION]
>
>重設沙箱具有破壞性。 CLI會要求您輸入沙箱名稱以進行確認，然後再繼續。
