---
title: API集合
description: 下載並匯入bootcamp的Postman API集合，其中包含整個AEP基礎實驗室所使用的請求。
doc-type: article
solution: Experience Platform
exl-id: 18d820c5-56ad-46b8-a9cf-f725555d2db3
source-git-commit: df6c1852a6e0357dc9f166c88e77dcf9d334f955
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%
---

# API集合

## Postman API集合檔案

下載檔案 — [AEP Foundation Bootcamp (Labs)。postman_collection.json](assets/aep-foundations-bootcamp-labs.postman_collection.json)



## 匯入API集合

1. 按一下檔案，從瀏覽器上開啟`Postman API Collection File`
1. 將檔案URL複製到剪貼簿
1. 在本機電腦上啟動Postman，然後按一下工作區中的`Import`按鈕
1. 將`Postman API Collection File`的URL貼入匯入模組文字方塊。 這會觸發自動匯入

![在Postman工作區中按一下[匯入]按鈕以匯入API集合](assets/api-collection-click-import-button.png "匯入按鈕")



![將API集合檔案URL貼入Postman匯入模組文字方塊](assets/api-collection-import-modal-paste-url.png "匯入按鈕模組文字方塊")

您現在會在左側邊欄的`Collections`標籤下看到名稱為`AEP Foundations Bootcamp`的集合已填入



![AEP Foundation Bootcamp集合已填入Postman Collections側邊欄標籤下](assets/api-collection-imported-collection-in-sidebar.png)

## AEP基礎Bootcamp集合概觀

您匯入的API集合包含您在整個bootcamp中進行Labs所需的所有必要API呼叫。  每個實驗室都會分組到具有自己一組API的特定資料夾中。  本週完成Labs時，請注意此資料夾結構。

您可以在下方找到每個資料夾的詳細資訊：

- **IMS驗證** — 包含產生access\_token的單一請求，此為使用任何Adobe Experience Platform API時的必要專案
- **XDM結構描述實驗室** — 包含一組請求，用於建立建立和設定即時客戶設定檔的結構描述所需的XDM元件
- **資料擷取實驗室** — 包含一組將資料串流至Experience Platform的要求
- **設定檔實驗室** — 包含一組檢視即時客戶設定檔特徵和行為的要求

>[!SUCCESS]
>
>恭喜！  您已成功匯入啟動營的Postman集合
