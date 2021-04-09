---
title: 批次訊息與Adobe Experience Platform藍圖
description: 使用Adobe Experience Platform作為客戶個人檔案和細分的中心，執行排程和批次傳訊促銷活動。
solution: Experience Platform, Campaign
kt: 7196
exl-id: 4e55218c-c158-4f78-9f0b-c03528d992fa
translation-type: tm+mt
source-git-commit: ee1d97af9bf58076fbce24fbc8a3f0d50a4b52a0
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---

# 批次訊息與Adobe Experience Platform藍圖

使用Adobe Experience Platform作為客戶個人檔案和細分的中心，執行排程和批次傳訊促銷活動。

## 使用案例

* 排程的電子郵件促銷活動
* 上線和再行銷宣傳

## 應用程式

* Adobe Experience Platform
* Adobe Campaign Classic或標準

## 整合模式

* Adobe Experience Platform→Adobe Campaign Classic
* Adobe Experience Platform→Adobe Campaign Standard

## 建築

<img src="assets/aepbatch.svg" alt="批傳訊和Adobe Experience Platform情境的參考架構" style="border:1px solid #4a4a4a" />

## 瓜德賴爾

* 僅支援Campaign單一組織單位部署
* 促銷活動是所有作用中描述檔的真實來源，這表示描述檔必須存在於促銷活動中，且不應根據Experience Platform區段建立新的描述檔。
* 從Experience Platform實現的區段成員資格對於批次（每天1次）和流（約5分鐘）都是延遲的

**[!UICONTROL 即時客戶資料平台區] 段共用至促銷活動：**

* 建議20個區段上限
* 啟動限制為每24小時
* 只有聯合模式屬性可用於激活（不支援陣列／映射／體驗事件）。
* 建議每個區段不超過20個屬性
* 所有具有「已實現」區段成員資格的描述檔的每個區段有一個檔案，或如果區段成員資格新增為檔案中「已實現」和「已退出」的描述檔屬性
* 支援增量或完整的區段匯出
* 不支援檔案加密
* 促銷活動匯出工作流程最多每4小時執行一次
* 請參閱[Experience Platform的概要檔案和資料接收護欄](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html)

## 實施步驟

### Adobe Experience Platform

#### 架構／資料集

1. 根據客戶提供的資料，在Experience Platform中設定個別描述檔、體驗事件和多實體結構。
1. 為broadLog、trackingLog、非交付項位址和描述檔偏好設定建立促銷活動結構（選用）。
1. 將資料使用標籤新增至資料集以利管理。
1. 建立可在目標上強制執行治理的原則。

#### 個人檔案／身分識別

1. 建立任何客戶專屬的命名空間。
1. 將身分新增至結構。
1. 啟用描述檔和資料集。
1. 為即時客戶個人檔案的不同檢視設定合併規則（可選）。
1. 建立促銷活動使用的區段。

#### 來源／目標

1. 使用串流API和來源連接器將資料內嵌至Experience Platform。
1. 設定[!DNL Azure] blob儲存目標以搭配促銷活動使用。

#### 行動應用程式部署

1. 實作Campaign Classic的促銷活動SDK或Campaign Standard的Experience PlatformSDK。 如果有Experience Platform Launch，建議使用Campaign Classic/標準擴充功能與Experience PlatformSDK。

#### Campaign

1. 設定描述檔、查閱資料和相關的傳遞個人化資料的結構。

>[!IMPORTANT]
>
>目前，您必須瞭解描述檔和事件資料的Experience Platform資料模型，以便瞭解Campaign需要哪些資料。

#### 匯入工作流程

1. 將簡化的描述檔資料載入並收錄至Campaign sFTP。
1. 將協調及傳訊個人化資料載入Campaign sFTP並內嵌在其中。
1. 透過工作流程從[!DNL Azure] Blob內嵌Experience Platform區段。

#### 匯出工作流程

1. 每四小時透過工作流程將促銷活動記錄檔傳回Experience Platform（broadLog、trackingLog、非交付地址）。
1. 透過諮詢建立的工作流程，每四小時（可選）將描述檔偏好設定傳回Experience Platform。


## 相關檔案

* [Adobe Experience Platform檔案](https://experienceleague.adobe.com/docs/experience-platform.html?lang=en)
* [Campaign Classic檔案](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=en)
* [Campaign Standard檔案](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=en)
* [Experience Platform Launch檔案](https://experienceleague.adobe.com/docs/launch.html?lang=en)
* [Experience Platform行動SDK檔案](https://experienceleague.adobe.com/docs/mobile.html?lang=en)
