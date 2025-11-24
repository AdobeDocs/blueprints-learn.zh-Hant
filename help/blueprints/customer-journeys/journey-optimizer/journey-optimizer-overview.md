---
title: '[!DNL Journey Optimizer] — 歷程Blueprint'
description: 使用 Adobe Experience Platform 做為串流資料、客戶個人資料和分眾的中心，執行觸發式訊息和體驗。
solution: Journey Optimizer
exl-id: 97831309-f235-4418-bd52-28af815e1878
source-git-commit: 3a3988e93dd9e92f4f564bfedfa314e8e2b5d9ba
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 15%

---

# [!DNL Journey Optimizer]藍圖

Adobe [!DNL Journey Optimizer]是以Adobe Experience Platform建置的雲端原生應用程式，可跨多個管道即時和排程協調客戶歷程。 它支援事件導向觸發器、受眾細分和決策服務，透過電子郵件、簡訊、推播、網頁和應用程式內傳訊提供個人化體驗。 它可整合傳入和傳出系統，允許跨客戶生命週期進行統一的受眾狀態管理和情境式參與。

此藍圖概述應用程式的技術功能，並深入探討構成[!DNL Journey Optimizer]的各種架構元件。

<br>

## 使用案例

>[!BEGINTABS]
>[!TAB 歷程（事件導向，即時）]

- **放棄復原：**&#x200B;當使用者透過電子郵件、推播或應用程式內放棄購物車、表單或工作階段時，觸發個人化訊息。
- **新使用者註冊：**&#x200B;新使用者註冊新帳戶偏好設定、相關促銷活動或權益後，請立即與他們互動
- **異動訊息：**&#x200B;使用事件觸發器傳送即時確認、警示或更新（例如已送出訂單、重設密碼）。
- **內容鎖定目標：**&#x200B;根據使用者的訊號與位置即時與使用者通訊，以協助引導和引導其體驗
- **關聯式向上銷售/交叉銷售：**&#x200B;根據即時設定檔屬性和最近的互動，提供個人化優惠。

>[!TAB 行銷活動協調流程（已排程，品牌已啟動）]

- **促銷活動**：針對產品啟動、季節性優惠或銷售活動，啟動多步驟、多管道行銷活動。
- **生命週期行銷**：自動循環行銷活動，例如生日訊息、續約提醒或忠誠度里程碑。
- **以對象為基礎的Funnel推送**：根據商業邏輯或CRM屬性，將對象細分並推送到結構化的行銷活動中。
- **電子報與內容發佈**：透過電子郵件和行動裝置，排程並傳遞個人化內容給目標對象。
- **重新參與行銷活動**：識別休眠的使用者，並根據非使用狀態臨界值將其重新匯入參與流程。

>[!ENDTABS]

<br>

## 架構

<img src="images/ajo-architecture.svg" alt="參考架構Adobe Journey Optimizer Blueprint" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## Blueprint案例

| 狀況 | 說明 |
| :-- | :-- |
| [個歷程](journey-optimizer-journeys.md) | Adobe Journey Optimizer中的AJO歷程是由即時事件或受眾區段觸發的自動個人化客戶體驗，可讓行銷人員跨電子郵件、簡訊和推播通知等通道傳送相關訊息。 |
| [行銷活動協調流程](journey-optimizer-campaigns.md) | AJO Campaign Orchestration可讓行銷人員使用即時資料和對象深入分析，設計和執行個人化的跨頻道行銷活動。 它支援動態目標定位、訊息傳送和歷程邏輯，以最佳化跨電子郵件、簡訊、推播和自訂通道的客戶參與。 |

<br>

## 整合模式

| 整合 | 說明 | 技術考量 |
| :-- | :-- | :-- |
| [第三方傳訊](3rd-party-messaging.md) | 示範Adobe [!DNL Journey Optimizer]如何與協力廠商傳訊平台整合，以協調及提供個人化的客戶通訊。 | <ul><li>協力廠商系統必須支援&#x200B;**持有人權杖驗證**</li><li>**由於多租使用者架構，不支援**&#x200B;靜態IP。</li><li>請注意，第三方系統上的&#x200B;**API速率限制**；客戶可能需要購買額外的容量來處理源自&#x200B;**Adobe Journey Optimizer**&#x200B;的流量。</li><li>訊息裝載或傳遞邏輯中不支援&#x200B;**決定管理**。</li></ul> |
| 使用Adobe Campaign v8[[!DNL Journey Optimizer] 的](../campaign-v8/ajo-and-campaign-v8.md) | 示範Adobe [!DNL Journey Optimizer]如何整合Adobe Campaign v8的交易式傳訊功能，以執行最終訊息傳送。 | <ul><li>沒有訊息限制。 每5分鐘最多4,000則訊息。</li><li>僅支援事件起始歷程的</li><li>Campaign傳送的訊息不支援決定管理</li></ul> |

<br>

## 先決條件

Adobe [!DNL Experience Platform]：

- 必須先在系統中設定結構描述和資料集，然後才能設定[!DNL Journey Optimizer]資料來源
- 針對XDM體驗事件類別型結構，當您想要觸發非規則型事件的事件時，請新增「協調流程eventID」欄位群組
- 針對XDM個別設定檔類別型結構描述，請新增「設定檔測試詳細資料」欄位群組，以便載入測試設定檔以與[!DNL Journey Optimizer]搭配使用

<br>

電子郵件：

- 必須準備好要用於訊息傳送的子網域
- 子網域可以完全委派給 Adobe（建議），或 CNAME 可用來指向 Adobe 專用的 DNS 伺服器（自訂）
- 每個子網域都需要 Google TXT 記錄，以確保良好的傳遞能力

<br>

行動推播：

- 客戶必須有可建立應用程式的行動裝置開發人員
- Adobe Experience Platform Mobile SDK

<br>

## 護欄

[[!DNL Journey Optimizer] 護欄產品連結](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails.html)

[護欄與端對端延遲指引](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html?lang=zh-Hant)

## 相關文件

- [[!DNL Experience Platform] 檔案](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hant)
- [[!DNL Experience Platform] 標籤檔案](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=zh-Hant)
- [[!DNL Experience Platform Mobile SDK] 檔案](https://experienceleague.adobe.com/docs/mobile.html?lang=zh-Hant)
- [[!DNL Journey Optimizer] 檔案](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=zh-Hant)
- [[!DNL Journey Optimizer] 產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/adobe-journey-optimizer.html)