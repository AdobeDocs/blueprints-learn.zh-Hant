---
title: 客戶活動中心藍圖
description: 即時客戶個人檔案查閱，以提供代理商協助支援和銷售的內容。
solution: Experience Platform,Data Collection
kt: 7195
exl-id: 3616cbf1-2e59-4e68-a1ff-1d2e3b344a1c,4f15aa5d-9ee3-4d92-8012-3e2f0c0d615f
translation-type: tm+mt
source-git-commit: 98d44067a1640dc8b695cb0d25f69ec26be647e1
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 0%

---

# 客戶活動中心藍圖

客戶活動中心藍圖顯示外部應用程式如何存取Adobe Experience Platform的即時客戶個人檔案。

外部應用程式可透過APIGET要求存取即時客戶個人檔案。 然後，儲存在描述檔中的屬性、事件、區段成員資格和模型導向功能可用於這些外部非Adobe應用程式。

有了這項功能，當客戶呼叫您的客服中心時，您就可以呈現豐富的內容。 例如，支援代理可以洞察客戶的終身價值、客戶流失傾向或行銷宣傳的曝光度。 銷售代理也可以從更深入的情境或洞察客戶中獲益。

>[!NOTE]
>
>目前由描述檔查閱API支援的延遲約為500毫秒，因此此方法不適用於將描述檔與即時決策引擎（例如同頁網頁或行動個人化）整合。

## 使用案例

* 為代理支援的互動（例如支援和銷售體驗）提供更深入的消費者情境。 使用Experience Platform的描述檔查閱，工程師可以接收更多消費者的相關內容，例如最近購買、促銷活動互動、傾向、受眾會籍，以及儲存在即時客戶描述檔中的其他屬性和見解。

## 建築

<img src="assets/cah.svg" alt="客戶活動中心藍圖的參考體系結構" style="border:1px solid #4a4a4a" />

## 瓜德賴爾

* [即時客戶個人檔案資料的護欄](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html)

## 實施步驟

1. 配置資料集和方案。
1. 配置[!UICONTROL 即時客戶配置檔案]:為[!UICONTROL 即時客戶設定檔配置架構和資料集，並設定合併原則和身分。]
1. 將資料內嵌至平台並處理至[!UICONTROL 即時客戶個人檔案]。
1. 使用實體API從記錄實體或體驗事件實體中尋找描述檔屬性。

## 相關檔案

* [Adobe Experience Platform啟動產品說明](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-platform0.html)
* [即時客戶個人檔案檔案](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html?lang=en)
* [描述檔護欄](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html)
* [描述檔查閱API](https://www.adobe.io/apis/experienceplatform/home/api-reference.html)
