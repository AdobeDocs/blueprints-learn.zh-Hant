---
title: '[!DNL Journey Optimizer] — 觸發式傳訊和Adobe Experience Platform Blueprint'
description: 使用 Adobe Experience Platform 做為串流資料、客戶個人資料和分眾的中心，執行觸發式訊息和體驗。
solution: Journey Optimizer
exl-id: 97831309-f235-4418-bd52-28af815e1878
source-git-commit: f8b9cc115739b53bba71d06b228dcce57df9dd7b
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 53%

---

# [!DNL Journey Optimizer]個藍圖

Adobe [!DNL Journey Optimizer]是專門建置的系統，行銷團隊可即時回應客戶行為，並在他們所在的位置與他們見面。 資料管理功能已移至Adobe [!DNL Experience Platform]，讓行銷團隊專注於他們擅長的工作：建立世界級的客戶歷程和個人化對話。

此藍圖概述應用程式的技術功能，並深入探討構成[!DNL Journey Optimizer]的各種架構元件。

## 使用案例

* 觸發的訊息
* 歡迎和註冊確認資訊
* 購物車與申請表格放棄
* 位置觸發的訊息
* 體育場內體驗
* 旅行和酒店業抵達前和住宿期間的體驗

## 架構

<img src="assets/ajo-architecture.svg" alt="Journey Optimizer 參考架構藍圖" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## 藍圖方案

| 狀況 | 說明 | 功能 |
| :-- | :--- | :--- |
| [第三方傳訊](3rd-party-messaging.md) | 示範Adobe [!DNL Journey Optimizer]如何與協力廠商傳訊系統搭配使用，以協調並傳送個人化通訊 | 在客戶與您的品牌或公司互動時，立即提供 1:1 的個人化通訊<br><br>考量事項：<br><ul><li>第三方系統必須支援用於驗證的承載令牌</li><li>由於多租用戶架構，不支援靜態 IP</li><li>每秒的 API 呼叫次數，請注意協力廠商系統的架構限制。  客戶可能需要向協力廠商購買額外的磁碟區，以支援來自[!DNL Journey Optimizer]的磁碟區</li><li>在消息或承載中不支援決策管理</li></ul> |

<br>

## 整合模式

| 整合 | 說明 | 功能 |
| :-- | :--- | :--- |
| 使用Adobe Campaign](ajo-and-campaign.md)的[[!DNL Journey Optimizer]  | 顯示如何使用Adobe [!DNL Journey Optimizer]來利用即時客戶設定檔編排1:1體驗，並利用原生Adobe Campaign交易式訊息系統來傳送訊息 | 利用[!DNL Journey Optimizer]的即時客戶個人檔案和功能來協調即時體驗，同時利用Adobe Campaign的原生即時傳訊功能進行最後一哩通訊<br><br>考量事項：<br><ul><li>Campaign 應用程式必須位於 v7 版本編號 21.1 以上或 v8 上</li><li>傳送訊息輸送量</li><ul><li>Campaign v7 — 每小時最多 50k</li><li>Campaign v8 — 每小時最多 1M</li><li>Campaign Standard — 每小時最多 50k</li></ul><li>不執行限制，因此使用案例需要企業架構師的技術審查</li><li>不支援在 Campaign 傳送的訊息中使用決策管理</li></ul> |

<br>

## 先決條件

Adobe [!DNL Experience Platform]：

* 必須先在系統中設定結構描述和資料集，然後才能設定[!DNL Journey Optimizer]資料來源
* 如果您想要觸發非規則型的事件，則針對體驗事件類別型方案，新增「Orchestration eventID」欄位群組
* 對於以個別設定檔類別為基礎的結構描述，請新增「設定檔測試詳細資料」欄位群組，以便載入測試設定檔以與[!DNL Journey Optimizer]搭配使用

電子郵件：

* 必須準備好要用於訊息傳送的子網域
* 子網域可以完全委派給 Adobe（建議），或 CNAME 可用來指向 Adobe 專用的 DNS 伺服器（自訂）
* 每個子網域都需要 Google TXT 記錄，以確保良好的傳遞能力

行動推播：

* 客戶必須有可建立應用程式的行動裝置開發人員
* Adobe Experience Platform Mobile SDK

## 護欄

[[!DNL Journey Optimizer] 護欄產品連結](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)

[護欄與端對端延遲指引](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html)

## 相關文件

* [[!DNL Experience Platform] 檔案](https://experienceleague.adobe.com/docs/experience-platform.html?lang=zh-Hant)
* [[!DNL Experience Platform] 標籤檔案](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=zh-Hant)
* [[!DNL Experience Platform Mobile SDK] 檔案](https://experienceleague.adobe.com/docs/mobile.html?lang=zh-Hant)
* [[!DNL Journey Optimizer] 檔案](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=zh-Hant)
* [[!DNL Journey Optimizer] 產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/adobe-journey-optimizer.html)
