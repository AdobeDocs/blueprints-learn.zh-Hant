---
title: Customer Journey Analytics 搭配 Real-time Customer Data Platform 藍圖
description: 在 Customer Journey Analytics 中統一和分析客戶歷程中的資料和客戶行為，從 CJA 向 RTCDP 發佈對象
solution: Customer Journey Analytics
kt: null
thumbnail: null
exl-id: 9e1ba723-63f2-4622-ba67-f2a315c3ba0c
source-git-commit: 9fe44d93dcc05711c77ce1325b6549bb6c27a860
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 98%

---

# Customer Journey Analytics 搭配 Real-time Customer Data Platform 藍圖

在 Customer Journey Analytics(CJA) 中建立識別的對象，並將其發佈至 Adobe Experience Platform 中的 Real-time Customer Profile，以便鎖定客戶並個人化。非常適合使用歷史資料建立對象，或透過精細篩選和運算欄位建立更完善的對象(Customer Journey Analytics)。

## Customer Journey Analytics 對象發佈指南

請參閱下列檔案，以取得從 Customer Journey Analytics 向 Real-time Customer Data Platform 發佈對象的實作與設定指南。[文件](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html?lang=zh-Hant)

## Customer Journey Analytics 藍圖架構

![架構圖](assets/CJA.svg){zoomable="yes"}

## Customer Journey Analytics 藍圖的護欄圖

* 有關詳細的護欄和端到端延遲，請參閱[部署護欄文件](../experience-platform/deployment/guardrails.md)

![護欄圖表](../experience-platform/deployment/assets/CJA_guardrails.svg){zoomable="yes"}

## 常見問題集

* 如果 CJA 傳送的 RTCDP 中不存在對應的個人資料，會建立新的個人資料，還是只會從 CJA 記錄已存在個人資料的對象？將會建立新的個人資料。因此，如果您的 RTCDP 實作僅針對已知客戶，則應編寫 CJA 對象規則，以僅篩選具有已知身分的個人資料。如果不需要，這將確保 RTCDP 個人資料計數不會將匿名個人資料算入其中。

* CJA 會傳送哪些身分識別？CJA 會在 CJA 設定期間傳送任何已設為「人員 ID」的身分識別。

* 什麼將設定為主要身分？無論使用者選取何種身分，他們都會將 CJA 設為主要「人員」ID。

* 身分服務是否也會處理 CJA 訊息？也就是說 CJA 可以透過對象共用，將身分新增至個人資料身分圖表嗎？否，身分服務不會處理 CJA 訊息。