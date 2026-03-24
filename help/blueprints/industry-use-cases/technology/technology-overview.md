---
title: 技術使用案例
description: 探索技術組織如何使用Adobe Experience Platform來統一資料收集、即時轉送事件，並強化數位產品的分析和啟用。
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
exl-id: a1b2c3d4-e5f6-7890-abcd-ef1234567890
source-git-commit: 77908fd8a9f4309cbe66063cd33f065424697e55
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# 技術使用案例

技術組織使用Adobe Experience Platform來集中管理網頁、行動裝置和產品表面的資料收集，並將即時事件發佈到分析、Data Warehouse和啟動目的地，以便為其產品和行銷方案提供支援。 透過整合邊緣的事件收集，技術團隊可降低使用者端的複雜性、改善資料品質，並確保所有下游系統都能從單一權威來源接收一致的行為資料。

## 即時事件轉送

將透過Edge Network收集的即時行為事件轉送至第三方分析、資料倉儲和合作夥伴平台，以擴充和啟用。 在邊緣集中事件收集並轉送至多個目的地可減少使用者端標籤負荷、改善資料品質，並確保所有下游系統都能從單一權威來源接收一致的事件資料。

### 企業影響

技術組織實作即時事件轉送，可減少使用者端標籤負載和相關效能額外負荷，同時改善分析、Data Warehouse和啟用目的地之間事件資料的一致性。 伺服器端轉送也可減少頁面重量並改善載入效能，直接有利於使用者體驗量度。

### 實施方式

使用[事件轉送](/help/blueprints/use-case-patterns/audience-building-activation/event-forwarding.md)模式，將Adobe Experience Platform Web SDK所收集的事件透過Edge Network路由傳送到已設定的伺服器端目的地。 當目標是從單一收集點進行伺服器對伺服器的事件分配時，這是正確的模式，而不是為使用者端的每個目的地管理個別的標籤，這會增加頁面權重並建立跨系統的資料不一致。

### 技術考量

- Edge Network事件轉送需要將事件集合移轉到Adobe Experience Platform Web SDK或Mobile SDK；在設定轉送目的地之前，必須評估現有的標籤型實施是否相容性。
- 轉送規則必須設定為僅傳送每個目的地所需的欄位 — 避免將完整XDM裝載轉送至只需要一小部分欄位子集的目的地，因為這會增加資料傳輸成本並建立法規遵循風險。
- 目的地聯結器必須妥善處理失敗；事件轉送管道應該針對變得無法使用的目的地實施重試邏輯和警報，以防止在中斷期間遺失資料。
- 必須檢閱每個轉送目的地的資料治理原則，以確保在轉送設定中遵循邊緣擷取的使用者同意偏好設定。
