---
title: 電信產業 — 用於觸發式訊息傳送的 Journey Optimizer
description: 提供客戶量身打造的即時交易，同時讓客戶高效登入，帶來長期忠誠度。
solution: Journey Optimizer
kt: 9486
exl-id: fa4a6569-3972-4b97-91f1-7ca8ffd3c5b3
source-git-commit: 1a0ce987fc615080bb78fb8ecf60c96e362a95c0
workflow-type: ht
source-wordcount: '333'
ht-degree: 100%

---

# 電信行業面臨的業務挑戰

在實作此藍圖之前，電信公司的「新增線路」電子郵件促銷活動取決於使用者是否已轉換，且只會在等候 7 天後檢查。一旦滿足這些標準，就會啟動任何其他接觸點。

必須解決這一限制，以便對希望在當前 7 天等待期之前新增線路的使用者啟動更及時的後續行動。

## Adobe 方法

* Adobe Analytics 資料可識別無法轉換以新增線路的使用者，會作為資料來源納入，供 Adobe Journey Optimizer 使用。
* Adobe Journey Optimizer 會不時使用規則，讓客戶收到自訂的「放棄」訊息，以鼓勵客戶在帳戶中新增線路以進行轉換。


## 提供的業務價值

| 目標 | 策略 | 值已解除鎖定 |
|---|---|---|
| **推動更高的促銷活動轉換率&#x200B;**<br></br>**增加年度客戶收入**</ul> | <ul><li>對於對新增線路有興趣但尚未轉換的使用者，幾乎即時建立新區段。</li><li>利用面向感情趣的非轉換客戶的第二個接觸點，對為未轉換客戶進行追蹤。 </li><li>使用測試策略來測量歷程效能，並透過電子郵件最佳化轉化。</li></ul> | <ul><li><strong>高品質的相關體驗：</strong>隨著歷程協調就位，客戶將體驗更相關的訊息，以降低電子郵件清單流失率。</li><li><strong>大規模的歷程策劃：</strong>您可以建立個人化且更及時的歷程，以促進轉換率和總收入的增加。</li></ul> |

## 主要藍圖：透過 Experience Cloud 應用程式的對象與啟用

### 說明

<ul><li>使用 Adobe Experience Platform 作為串流資料、客戶個人資料與細分的中樞，以執行觸發的串流訊息傳送，使用 Journey Orchestration 串流歷程協調與訊息傳送</li></ul>

### Experience Cloud 應用程式

<ul><li>Adobe Journey Optimizer</li></ul>

### 藍圖架構

<a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer.html?lang=zh-Hant"><img alt="圖片：電信企業提供即時定製交易，同時高效地客戶登入，實現了長期忠誠度。" src="https://experienceleague.adobe.com/docs/blueprints-learn/assets/ajo-architecture.svg"/></a>
