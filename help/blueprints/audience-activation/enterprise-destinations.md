---
title: 企業目標受眾與個人檔案啟動藍圖
description: 受眾和個人檔案啟動至企業目標
solution: Experience Platform,Real-time Customer Data Platform
kt: 7475
exl-id: 32133174-eb28-44ce-ab2a-63fcb5b51cb5,None
translation-type: tm+mt
source-git-commit: 76fe52d8e83e075f9e7ce6e8596880181b01a7fd
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 39%

---

# 企業目標受眾與個人檔案啟動藍圖

以串流或批次方式從[!UICONTROL 即時客戶資料平台]分享個人檔案和觀眾變更和事件至企業資料存放區和應用程式。 這些描述檔和受眾事件可用於啟動客戶的銷售或支援活動，例如跟蹤放棄的應用程式流程或網路研討會註冊，或用[!UICONTROL 即時客戶資料平台]的最新客戶屬性和智慧更新企業應用程式。

## 使用案例

* 針對雲端儲存目的地或串流目的地的個人檔案和受眾啟動，以進行企業追蹤、儲存、分析和啟動客戶資料和見解。

## 應用程式

* Adobe Experience Platform 啟動

## 架構

<img src="assets/enterprise_destination_activation.svg" alt="企業啟動方案的參考架構" style="border:1px solid #4a4a4a" />

## 護欄

請參閱觀眾與設定檔啟動概述頁面- [LINK](overview.md)中概述的護欄

## 實施步驟

1. 建立要收錄的資料結構。
1. 建立資料集以供收錄。
1. 在方案上設定正確的身份和身份命名空間，以確保擷取的資料可以嵌入統一的設定檔。
1. 啟用結構描述檔和資料集以進行描述檔處理。
1. 設定任何資料擷取來源。
1. 在Experience Platform中編寫區段，以批次或串流方式評估。 系統會自動確定區段是作為批次還是串流評估。
1. 將用於設定檔屬性和對象會籍分享的目標設定為所需的目標。

## 相關文件

* [目標文件](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html?lang=zh-Hant)
* [雲端儲存空間目標概觀](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/cloud-storage/overview.html?lang=en#catalog)
* [HTTP目標](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/http-destination.html?lang=en#overview)
* [即時客戶資料平台產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/real-time-customer-data-platform.html)
* [描述檔與區段指南](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hant)
* [細分文件](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html?lang=zh-Hant)

## 相關視訊與教學課程

* [即時客戶資料平台概覽](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html?lang=zh-Hant)
* [[!UICONTROL 即時客戶資料平台示範]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html?lang=zh-Hant)
* [建立區段](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html?lang=zh-Hant)
