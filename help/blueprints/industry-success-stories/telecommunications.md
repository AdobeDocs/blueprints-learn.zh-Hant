---
title: 電信行業 — Journey Optimizer用於觸發資訊
description: 提供客戶即時定制交易，同時高效地讓客戶加入長期忠誠度。
solution: Journey Optimizer
kt: 9486
exl-id: fa4a6569-3972-4b97-91f1-7ca8ffd3c5b3
source-git-commit: d19555201107b6aa827e63eb8ecff8642d9f967c
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 10%

---

# 電信行業業務挑戰

在實施此藍圖之前，電信公司的「添加新線路」電子郵件活動取決於用戶是否已轉換並僅在經過7天的等待期後才檢查此內容。 一旦滿足這些標準，就會啟動任何附加的接觸點。

必須解決這一限制，以便對希望在當前狀態7天等待期之前添加一行的用戶啟動更及時的後續行動。

## Adobe方法

* Adobe Analytics資料將作為資料源包括，供Adobe Journey Optimizer使用。
* Adobe Journey Optimizer會不時使用一條規則，讓客戶收到定製的「放棄」消息，以鼓勵客戶通過在其帳戶中添加新行來進行轉換。


## 交付的業務價值

| 目標 | 戰術 | 值已解鎖 |
|---|---|---|
| **提高促銷活動轉換率&#x200B;**<br></br>**增加年度客戶收入**</ul> | <ul><li>為已顯示有興趣添加行但尚未轉換的用戶幾乎即時建立新段。</li><li>未轉換客戶的驅動器跟蹤，第二個觸點用於感興趣的非轉換器。 </li><li>使用測試策略來衡量行程效能並優化通過電子郵件進行轉換。</li></ul> | <ul><li><strong>高質量、相關經驗：</strong> 隨著行程協調到位，客戶將體驗到更相關的消息傳遞，從而減少電子郵件清單的混亂。</li><li><strong>Journey Orchestration:</strong>可以建立個性化且更及時的行程，以推動轉換和總收入的增加。</li></ul> |

## 主藍圖：使用Experience Cloud應用程式進行受眾和激活

### 說明

<ul><li>使用 Adobe Experience Platform 作為串流資料、客戶個人資料與細分的中樞，以執行觸發的串流訊息傳送，使用 Journey Orchestration 串流歷程協調與訊息傳送</li></ul>

### Experience Cloud 應用程式

<ul><li>Adobe Journey Optimizer</li></ul>

### 藍圖體系結構

<a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer.html?lang=en"><img alt="電信業務的縮略圖影像提供定製的即時交易，同時高效地讓客戶加入長期忠誠度。" src="https://experienceleague.adobe.com/docs/blueprints-learn/assets/journey-optimizer.png?lang=en"/></a>
