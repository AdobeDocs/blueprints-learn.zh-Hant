---
title: '[!DNL Journey Optimizer] — 觸發式傳訊和Adobe Experience Platform Blueprint'
description: 使用 Adobe Experience Platform 做為串流資料、客戶個人資料和分眾的中心，執行觸發式訊息和體驗。
solution: Journey Optimizer
source-git-commit: 0a3ebcbc6029df46bd988cb8f15ecf838f80c3c9
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 9%

---

# [!DNL Journey Optimizer] — 歷程Blueprint

Adobe Journey Optimizer歷程是即時、事件導向的工作流程，可根據個別客戶行為提供個人化的多步驟體驗。 它們支援廣泛的管道，包括電子郵件、簡訊、推播通知、應用程式內傳訊、程式碼型體驗和自訂API型整合，讓品牌可透過客戶偏好的接觸點，根據內容與客戶互動。

<br>

## 架構

<img src="images/ajo-journeys-architecture.svg" alt="參考架構Adobe Journey Optimizer — 歷程Blueprint" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## 歷程的架構考量事項

- **設定檔新鮮度**： AJO歷程需要客戶設定檔的即時更新。 確保將饋送至Adobe Experience Platform (AEP)的資料來源設定為低延遲擷取，以維持設定檔準確性。
- **可擴充的事件處理：**&#x200B;請確定基礎結構可以處理大量的歷程觸發程式和訊息傳送。
- **模組化整合：**&#x200B;設計API和自訂動作，用於連結AJO與外部系統以進行動態個人化。
- **身分解析**：跨裝置和管道精確拼接客戶身分至關重要。 未對齊的身分可能會導致歷程中斷或導向錯誤。
- **區段資格計時**：以對象為基礎的歷程取決於區段會籍。 瞭解評估區段的頻率，以及該時間如何影響歷程進入和個人化。
- **歷程進入條件**：設定檔必須符合特定條件才能進入歷程。 這些條件應謹慎設計，以避免非預期的排除或重疊。
- **對象評估與延遲**：讀取對象步驟取決於Adobe Experience Platform中的區段評估，此評估可能不會即時發生。 架構者瞭解評估頻率和延遲，以避免對象資格延遲並確保及時個人化。

<br>

## 護欄

[[!DNL Journey Optimizer] 護欄產品連結](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails.html)

[護欄與端對端延遲指引](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html?lang=zh-Hant)

<br>

## 相關文件

- [[!DNL Experience Platform] 檔案](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hant)
- [[!DNL Experience Platform] 標籤檔案](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=zh-Hant)
- [[!DNL Experience Platform Mobile SDK] 檔案](https://experienceleague.adobe.com/docs/mobile.html?lang=zh-Hant)
- [[!DNL Journey Optimizer] 檔案](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=zh-Hant)
- [[!DNL Journey Optimizer] 產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/adobe-journey-optimizer.html)