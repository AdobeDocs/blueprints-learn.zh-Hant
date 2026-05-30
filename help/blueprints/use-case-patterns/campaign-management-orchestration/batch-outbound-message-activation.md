---
title: 批次傳出訊息啟用
description: 瞭解如何在單一批次執行中評估對象及傳遞已排程的傳出訊息。
solution: Journey Optimizer, Real-Time Customer Data Platform
exl-id: 192853ce-02ab-46e6-9092-3db5354bc19c
source-git-commit: 349d26f612d4002d1de3d27c7f893bd63ac467a3
workflow-type: tm+mt
source-wordcount: '1758'
ht-degree: 4%

---

# 批次傳出訊息啟用

本指南說明批次傳出訊息啟用使用案例模式，此模式使用[!DNL Adobe Journey Optimizer] (AJO)和[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)將排程傳出訊息傳送至定義的受眾區段。 它專為需要瞭解此模式的功能、其支援的業務目標、其啟用的戰術使用案例以及所涉及的Adobe應用程式的解決方案架構師、行銷技術人員和實作工程師所設計。

批次傳出訊息啟用是一對多傳出訊息的基本行銷活動模式。 它涵蓋從受眾定義到訊息傳遞和效能分析的完整生命週期。

## 使用案例模式

**批次傳出訊息啟用**

評估對象，然後在單一批次執行中將排程的傳出訊息（電子郵件、簡訊、推播）傳送給所有符合資格的設定檔。

**執行計畫：**&#x200B;對象評估>訊息編寫>行銷活動執行>報告

## 使用案例概述

組織經常需要在特定時間或回應系統事件，將單一訊息傳送給已知受眾區段。 此模式解決該需求，方法是將[!DNL RT-CDP]中的對象評估與[!DNL Journey Optimizer]中的訊息編寫和行銷活動執行結合。

業務案例簡單明瞭：定義應該接收訊息的人員、使用個人化建立訊息內容、將對象和訊息繫結至行銷活動或歷程，並透過對象資格或系統觸發器，依排程執行傳送。 結果會傳送訊息，並包含傳送、參與和轉換量度的完整報表。

每當可透過一次執行將單一訊息傳遞給已知對象來推進業務目標時，此模式即適用。 它與回應即時行為事件的事件觸發訊息不同，也不同於隨著時間透過多個接觸點引導設定檔的多步驟協調歷程。 批次啟動是最簡單的行銷活動模式，也是傳出訊息使用案例最常見的起點。

## 主要業務目標

本節說明批次傳出訊息啟用支援的主要業務目標。

### 增加電子郵件和行銷活動參與度

**說明：**&#x200B;透過最佳化的內容和目標定位，改善開啟率、點進率及整體行銷活動回應。

**KPI：**&#x200B;開放率、參與度、轉換率

### 增加收入與銷售

**說明：**&#x200B;透過最佳化的數位頻道、行銷活動和客戶歷程，推動營收增長。

**KPI：**&#x200B;轉換率、遞增收入、平均訂單值

**相關業務目標：** [增加收入與銷售](/help/blueprints/business-objectives/revenue-monetization/increase-revenue-sales.md)

### 簡化行銷活動的執行

**說明：**&#x200B;透過範本、自動化和標準化程式，縮短行銷活動建置時間，並簡化多管道行銷活動傳遞。

**KPI：**&#x200B;上市速度、效率、準時完成%

## 戰術使用案例範例

下列案例說明批次傳出訊息啟用的常見應用程式。

- **銷售公告或促銷電子郵件爆增** — 在排程日期向符合資格的客戶區段廣播促銷優惠
- **產品上市推播通知** — 透過推播通知感興趣的客戶有新的產品可供使用
- **電子報或摘要電子郵件** — 定期傳送內容四捨五入給訂閱者對象
- **活動註冊邀請** — 邀請合格的潛在客戶參加網路研討會、會議或面對面活動
- **訂閱續約提醒電子郵件** — 提醒即將續約日期的客戶採取行動
- **熟客方案里程碑通知** — 恭喜達到熟客層級或點臨界值的會員
- **特定call-to-action電子郵件** — 推動目標動作，例如完成購買、更新偏好設定或註冊程式
- **快閃銷售或限時優惠方案的SMS行銷活動** — 透過簡訊傳送緊急且限時的促銷活動給選擇加入的對象

## 關鍵績效指標

下表定義用來測量促銷活動效益的KPI。

| KPI | 說明 | 測量方法 |
| --- | --- | --- |
| 傳遞率 | 成功傳遞給收件者的郵件百分比 | 已傳遞/已傳送x 100 |
| 開啟率 | 收件者開啟的傳遞訊息百分比 | 不重複開啟/傳送x 100 |
| 點進率(CTR) | 已點按連結的傳遞訊息百分比 | 不重複點按/傳送x 100 |
| 點按開啟率(CTOR) | 已點按連結的已開啟訊息百分比 | 不重複點按/不重複開啟x 100 |
| 轉換率 | 完成所需動作的收件者百分比 | 轉換/傳遞x 100 |
| 取消訂閱率 | 接收訊息後取消訂閱的收件者百分比 | 取消訂閱/送達x 100 |
| 跳出率 | 無法傳遞的訊息百分比 | 退回/傳送x 100 |
| 每封傳送電子郵件的收入 | 行銷活動的收入除以傳送的訊息 | 總收入/已傳送 |

## 應用程式

下列應用程式可用來實作此模式。

- **[!DNL Adobe Journey Optimizer] (AJO)** — 訊息製作、頻道設定、行銷活動執行、歷程協調、內容實驗、頻率規則和報告
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** — 對象評估、同意和治理實施
- **[!DNL Adobe Experience Platform] (AEP)** — 設定檔存放區、身分服務、結構描述、資料集、資料集合

## 相關文件

本節提供依主題組織的[!DNL Experience League]檔案的完整連結。

### 行銷活動

- [開始使用行銷活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [建立行銷活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [API觸發的行銷活動](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/campaigns/api-triggered-campaigns/api-triggered-campaigns)

### 歷程

- [開始使用歷程](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [讀取對象歷程](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)

### 管道設定

- [開始使用電子郵件設定](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [委派子網域](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [建立 IP 池](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [IP熱身計畫](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [電子郵件表面設定](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [設定簡訊頻道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [設定推播通知頻道](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [管理隱藏清單](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### 訊息製作與個人化

- [建立電子郵件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [設計電子郵件內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [使用電子郵件Designer內容元件](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/content-components)
- [匯入或編碼電子郵件內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/code-content)
- [新增個人化](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization語法](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [輔助函式](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [動態內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)

### 內容管理

- [使用內容範本](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [使用內容片段](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [預覽和測試您的內容](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)
- [傳送電子郵件校樣](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/proofs)
- [電子郵件呈現](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/email-rendering)

### 內容實驗

- [開始使用內容實驗](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [建立內容實驗](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [內容實驗報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [統計計算](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-calculations)

### 頻率和衝突管理

- [頻率規則](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [商業規則概觀](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [開始使用衝突與優先順序管理](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [優先順序分數](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [識別潛在衝突](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/conflict-prioritization/conflicts)
- [歷程上限和仲裁](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)

### 對象和細分

- [Segmentation Service概述](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/home)
- [區段產生器UI指南](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [串流區段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [邊緣分段](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [對象構成](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Profile Query Language參考](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### 報告

- [行銷活動即時報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [行銷活動全域報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [歷程即時報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [歷程全域報告](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [使用Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [AJO + CJA整合指南](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

### 資料控管和同意

- [資料控管概覽](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/home)
- [資料使用標籤概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/data-governance/labels/overview)
- [同意和偏好設定欄位群組](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/xdm/field-groups/profile/consents)
- [Journey Optimizer中的同意](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)

### 資料模型與身分

- [XDM系統概覽](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [結構描述組合基本面](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/xdm/schema/composition)
- [Identity Service總覽](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [合併原則概觀](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/merge-policies/overview)

### 護欄

- [Journey Optimizer護欄](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [即時客戶個人檔案護欄](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [擷取護欄](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/ingestion/guardrails)

### 教學課程和快速入門

- [開始使用Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/get-started)
- [建立您的第一個行銷活動](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [建立您的第一個歷程](https://experienceleague.adobe.com/zh-hant/docs/journey-optimizer/using/orchestrate-journeys/journey)
