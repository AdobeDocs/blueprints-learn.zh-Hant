---
title: 電信產業 — Journey Optimizer觸發式訊息傳送
description: 提供客戶量身打造的即時交易，同時讓客戶有效率地加入，以提升長期忠誠度。
solution: Journey Optimizer
kt: 9486
exl-id: fa4a6569-3972-4b97-91f1-7ca8ffd3c5b3
source-git-commit: bf99ef23bb07c845a396767a65114874f3a18180
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 9%

---

# 電信行業業務挑戰

在實作此Blueprint之前，電信公司的「新增線路」電子郵件促銷活動取決於使用者是否已轉換，且只會在等候7天後檢查。 一旦滿足這些標準，就會啟動任何其他接觸點。

必須解決這一限制，以便對希望在當前狀態7天等待期之前添加線路的用戶啟動更及時的後續行動。

## Adobe方法

* Adobe Analytics資料可識別無法轉換以新增行的使用者，會作為資料來源納入，供Adobe Journey Optimizer使用。
* Adobe Journey Optimizer會不時使用規則，讓客戶收到自訂的「放棄」訊息，以鼓勵客戶在帳戶中新增一行以進行轉換。


## 業務價值

| 目標 | 戰術 | 值已解除鎖定 |
|---|---|---|
| **促進更高的促銷活動轉換率&#x200B;**<br></br>**增加年度客戶收入**</ul> | <ul><li>對於對新增行有興趣但尚未轉換的使用者，幾乎即時建立新區段。</li><li>對於具有第二個接觸點的未轉換客戶，對感興趣的非轉換客戶，請加以追蹤。 </li><li>使用測試策略來測量歷程效能，並針對透過電子郵件的轉換進行最佳化。</li></ul> | <ul><li><strong>高品質的相關體驗：</strong> 隨著歷程協調就位，客戶將體驗更相關的訊息，以降低電子郵件清單流失率。</li><li><strong>Journey Orchestration規模：</strong>您可以建立個人化且更及時的歷程，以促進轉換數和總收入的增加。</li></ul> |

## 主要藍圖：透過Experience Cloud應用程式啟動受眾

### 說明

<ul><li>使用 Adobe Experience Platform 作為串流資料、客戶個人資料與細分的中樞，以執行觸發的串流訊息傳送，使用 Journey Orchestration 串流歷程協調與訊息傳送</li></ul>

### Experience Cloud應用程式

<ul><li>Adobe Journey Optimizer</li></ul>

### Blueprint架構

<a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer.html?lang=en"><img alt="電信業務的映像提供即時定製的交易，同時高效地為長期忠誠客戶提供入門服務。" src="https://experienceleague.adobe.com/docs/blueprints-learn/assets/journey-optimizer.png?lang=en"/></a>
