---
title: 電信產業 — Journey Optimizer觸發式訊息傳送
description: 提供客戶量身打造的即時交易，同時讓客戶有效率地加入，以提升長期忠誠度。
solution: Experience Platform, Journey Optimizer
kt: 9486
source-git-commit: 7a81ea5d71355323a784e12207542fb7dd6b286b
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 10%

---


# 電信行業的商業挑戰

在實作此Blueprint之前，電信公司的「新增線路」電子郵件促銷活動取決於使用者是否已轉換，且只會在等候7天後檢查。 一旦滿足這些標準，就會起始任何其他接觸點。

必須解決這一限制，以便對希望在當前狀態7天等待期之前添加線路的用戶啟動更及時的後續行動。

## Adobe方法

* Adobe Analytics資料可識別無法轉換以新增行的使用者，會作為資料來源納入，供Adobe Journey Optimizer使用。
* Adobe Journey Optimizer會不時使用規則，讓客戶收到自訂的「放棄」訊息，以鼓勵客戶在帳戶中新增一行以進行轉換。


## 交付的業務價值

| 目標 | 戰術 | 未鎖定的值 |
|---|---|---|
| **促進更高的促銷活動轉換率&#x200B;**<br></br>**增加年度客戶收入**</ul> | <ul><li>對於對新增行有興趣但尚未轉換的使用者，幾乎即時建立新區段。</li><li>對於未轉換的客戶，若有關的非轉換者，則使用第二個接觸點來追蹤。 </li><li>使用測試策略來測量歷程效能，並針對透過電子郵件的轉換進行最佳化。</li></ul> | <ul><li><strong>高品質的相關體驗：</strong> 隨著歷程協調就位，客戶將體驗更相關的訊息，以降低電子郵件清單流失率。</li><li><strong>Journey Orchestration規模：</strong>您可以建立個人化且更及時的歷程，以促進轉換數和總收入的增加。</li></ul> |

## 重要Blueprint:透過Experience Cloud應用程式啟動受眾

<strong>說明</strong>
<ul><li>使用 Adobe Experience Platform 作為串流資料、客戶個人資料與細分的中樞，以執行觸發的串流訊息傳送，使用 Journey Orchestration 串流歷程協調與訊息傳送</li></ul>

<strong>Experience Cloud 應用程式</strong>
<ul><li>Adobe Journey Optimizer</li></ul> 
<br>

### Blueprint架構

<a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer.html?lang=en"><img alt="電信業務的縮圖影像提供即時量身打造的交易，同時有效率的客戶加入，以保持長期忠誠度。" src="https://experienceleague.adobe.com/docs/blueprints-learn/assets/journey-optimizer.png?lang=en"/></a>





