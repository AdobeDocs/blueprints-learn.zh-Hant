---
title: B2B Customer Journey Analytics Blueprint
description: 在Customer Journey Analytics中包含B2B帳戶、商機和購買群組資料，以進行帳戶型報告和歷程分析。
solution: Customer Journey Analytics
source-git-commit: 10e54d97082143b61e43bae56250a524d1759d45
workflow-type: tm+mt
source-wordcount: '729'
ht-degree: 7%

---


# B2B Customer Journey Analytics Blueprint

Customer Journey Analytics B2B edition可為B2B組織啟用帳戶型報表和分析。 與以人為中心的B2C分析不同，此藍圖將&#x200B;**帳戶**&#x200B;置於資料模型的中心，因此您可以跨多個利害關係人、購買群組和銷售週期分析複雜的B2B購買歷程。 使用[!DNL Customer Journey Analytics]將行為資料與B2B維度（帳戶、商機、行銷活動和行銷清單）整合，以進行歷程型深入分析和對象建立。

## 應用程式

* Adobe [!DNL Customer Journey Analytics] (B2B edition)
* Adobe Experience Platform （適用於B2B和事件資料）

## 使用案例

* **最佳化帳戶行銷** — 分析行銷活動、管道和內容對帳戶內購買群組、管道進展和向上銷售/交叉銷售機會的行銷影響。
* **成長關鍵帳戶** — 識別關鍵帳戶內跨購買群組的高值接觸點，以告知行銷和銷售動作，並在帳戶層級計算客戶期限值。
* **建立產品價值** — 衡量產品發行與使用在帳戶和使用者層級對客戶滿意度的影響，以最佳化功能並通知開發人員。
* **個人式B2B分析** — 結合帳戶和機會內容與個別使用者行為，以進行潛在客戶評分、參與和歷程分析。

## 先決條件

* [!DNL Customer Journey Analytics] B2B edition權益。
* Adobe Experience Platform中的B2B和行為資料： B2B資料集（帳戶、機會、人員、行銷活動、行銷清單、B2B活動）和事件資料（網頁、行動或其他管道）可在[CJA連線](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-connections/create-connection.html)中使用。
* CJA的[B2B命名](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-dataviews/b2b.html)：為連線設定的B2B專屬資料檢視設定（帳戶ID、機會ID和相關維度）。

## 架構

![Customer Journey Analytics架構，其B2B帳戶與機會資料已整合以供歷程分析使用](assets/CJA.svg){zoomable="yes"}

資料會透過CJA連線，從Experience Platform （B2B和事件資料集）傳輸至[!DNL Customer Journey Analytics]。 B2B維度會顯示在資料檢視中，以便可在帳戶、機會和人員層級建立分析和對象。

## 護欄

* 如需B2B edition產品限制與權益的相關資訊，請參閱[Customer Journey Analytics B2B產品說明](https://helpx.adobe.com/legal/product-descriptions/customer-journey-analytics-b2b.html)。
* 如需Analytics Platform和CJA技術限制的相關資訊，請參閱[Analytics Platform護欄](https://experienceleague.adobe.com/en/docs/analytics-platform/using/technotes/guardrails)。
* 如需CJA資料擷取與連線限制的相關資訊，請參閱[Customer Journey Analytics資料擷取護欄](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html#what-is-the-expected-latency-for-analytics-data-on-platform%3F)。
* 如果將CJA對象發佈到Real-time Customer Data Platform，請參閱[Customer Journey Analytics對象共用護欄](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html#latency)。
* 如需端對端延遲和平台護欄，請參閱[部署護欄檔案](../experience-platform/guardrails.md)。

## 實施步驟

1. **將B2B和事件資料擷取至Experience Platform** — 使用[來源](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=zh-Hant) （例如[!DNL Marketo Engage]、CRM或其他B2B聯結器）匯入帳戶、商機、人員、行銷活動和活動資料，以及行為事件。
2. **建立CJA連線** — [將相關的Experience Platform資料集](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-connections/create-connection.html) （B2B和事件）新增至Customer Journey Analytics連線。
3. **在資料檢視中設定B2B** — 啟用[B2B命名和金鑰維度](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-dataviews/b2b.html) （帳戶ID、機會ID等） 在連線的資料檢視中。
4. **建置以帳戶為基礎的分析和對象** — 使用[CJA B2B使用案例和報告](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/b2b.html?lang=zh-Hant)在帳戶和機會層級建立報告、劃分和對象；可選擇地[將對象發佈到Real-time CDP](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html?lang=zh-Hant)以進行啟用。

## 相關文件

### Customer Journey Analytics B2B edition

* [Customer Journey Analytics B2B edition](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-overview/cja-b2b/cja-b2b-edition.html)
* [B2B使用案例](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/b2b.html?lang=zh-Hant)
* [B2B edition使用案例概觀](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/b2b/b2b-edition/use-cases-overview.html)
* [以人為本的B2B專案範例](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/b2b/example.html)

### 連線和資料檢視

* [建立連線](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-connections/create-connection.html)
* [B2B資料檢視設定](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-dataviews/b2b.html)

### 對象和護欄

* [將CJA對象發佈到Real-time CDP](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html?lang=zh-Hant)
* [Experience Platform和應用程式護欄](../experience-platform/guardrails.md)
