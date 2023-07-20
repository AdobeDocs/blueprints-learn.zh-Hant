---
title: 零售業 — 使用 Experience Cloud 應用程式啟用
description: 跨數位媒體、電子郵件、推播和網頁通道提供即時的客戶體驗。
solution: Real-Time Customer Data Platform, Customer Journey Analytics, Journey Orchestration, Campaign, Analytics, Target
kt: 9474
exl-id: a675bc81-e76c-491a-8718-359867d63351
source-git-commit: ae7347be5095ca4a7f99f9371dd94d87097112b0
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 39%

---

# 零售業業務挑戰

此整合式體驗業務致力於個人化整個客戶歷程，以提升忠誠度、向現有客戶追加銷售，並改善其行銷活動中的行銷支出。實現目標的策略是擴展其數位功能，將離線客戶資料和交易資料納入其中，以推動增長。

## Adobe 方法

* 產生統一的客戶個人資料，其中包含所有可即時啟動的相關線上/線下資料
* 跨網路、媒體和推播通道策劃客戶互動，以促進首次或第二次的購買行為。

## 提供的業務價值

| 目標 | 策略 | 值已解除鎖定 |
|---|---|---|
| **策劃即時客戶歷程&#x200B;**<br></br>**推動新客戶重複購買&#x200B;**<br></br>**改進行銷效率並降低媒體成本**</ul> | <ul><li>強大的資料和身分策略可提升整個即時個人資料。</li><li>即時串流客戶和異動資料，包括90天的歷史負載</li><li>將區段串流至Advertising Networks和Adobe Target，以強化媒體支出和個人化工作。</li><li>透過Adobe Campaign的即時客戶歷程，其中包括測量績效的策略</li></ul> | <ul><li><strong>Real-time Customer Data Platform</strong>： 跨媒體、電子郵件、推播和網路提供即時的客戶體驗</li><li><strong>資料來源：</strong> 串流資料涵蓋此零售商的個人資料存儲、訂單系統、產品目錄和零售門市。</li><li><strong>即時媒體啟用：</strong>將區段串流至Advertising Networks以進行歸因和廣告抑制</li><li><strong>即時網頁個人化：</strong>串流區段已啟用至Adobe Target，以便在零售商的網頁體驗上啟用。</li><li><strong>規模Journey Orchestration：</strong>透過可用客戶資料即時豐富的觸發式傳訊，並即時啟用至電子郵件和推播頻道</li></ul> |


## 使用案例

| 類別 | 目標 | 使用案例 | 說明 |
|:----|:----|:----|:----|
| 客戶歷程 | 贏取 | 歡迎系列 | 歡迎新訂閱者，瞭解業務、產品和服務簡介 |
| | | 第1個購買計畫 | |
| | 提升銷售 | 捨棄的購物車/瀏覽 | 回覆潛在購買者，提高銷售額 |
| | | 產品審查/交叉銷售 | 透過產品評論交叉銷售更多專案。 |
| | | 產品促銷活動 |  |
| | | 重新排序時間 | 循環產品/服務的週期性提醒 |
| | 品牌忠誠度 | 贏回 | 復原已停用的客戶。 |
| | | 生日提醒 | 參與客戶生日慶典，與客戶建立更個人化的關係！ |
| 銷售 | 管理詳細目錄 | 重新補充庫存 | 顯示客戶想買的產品有庫存，藉此改善庫存狀況 |
| | | 下一個最佳類別 | 識別使用者的最佳類別/銷售 |
| | | 最暢銷商品 | |
| | | 降價提醒 | 向使用者顯示他們喜歡的專案的價格已降低 |
| | | 類似產品 |  |
| 個人化 | 增加轉換 | 優惠券/優惠 | 向客戶顯示最佳優惠方案/優惠券 |
| | | 個人化產品搜尋 | 改善搜尋體驗 |
| | | 產品Recommendations | 改善產品瀏覽體驗 |
| | | 全頻道體驗 | 跨所有管道觸及客戶 |
| 測量 | 瞭解客戶歷程 | 跨頻道行銷活動 | 衡量跨頻道行銷活動 |
| | | 區段績效 | 瞭解區段效能和貢獻 |
| | | 流失報表 | 視覺化每個階段的轉換 |
| | | 同類群組分析 | 測量區段群組之間的參與 |
| | | 點按到磚塊報表 | 瞭解客戶轉換如何帶來店內體驗 |
| | | 出處 | 檢視哪個接觸點/體驗對購買轉換的影響最大 |
| | | 預測性分析 | 進一步瞭解客戶傾向 |

## 架構

<img src="../vertical-blueprints/assets/retail-architecture.png" alt="零售參考架構" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />


## 相關 Blueprints


| 使用案例/整合  | 連結 |
|:----|:----|
| CJA + AEP | [Customer Journey Analytics藍圖概觀](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journey-analytics/overview.html?lang=zh-Hant) |
| | [Customer Journey Analytics — 使用案例](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/cja-usecases.html?lang=zh-Hant) |
| AJO + AEP | [Adobe Journey Optimizer — 使用案例](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/journey-optimizer.html?lang=en) |
| | [決策管理](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-overview.html?lang=zh-Hant) |
| RTCDP + AEP | [線上/離線對象啟用](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/known-customer-audience-activation/known.html?lang=zh-Hant) |
| | [Experience Platform+應用程式啟動](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/platform-and-applications.html?lang=zh-Hant) |
| MARKETO + AEP | [B2B 啟用與行銷 ](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/b2b-activation/overview.html?lang=en) | |
| Target + AEP | [Adobe Target使用案例 — 行為網頁/行動個人化](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/web-personalization/behavioral.html?lang=en) | [使用已知客戶資料進行 Web/行動個人化](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/web-personalization/known-personalization.html?lang=en) | |
