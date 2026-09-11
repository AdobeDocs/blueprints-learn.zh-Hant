---
hold: true
title: 選項#2 — 使用預先彙總
description: 使用上游計算的預先彙總使用量屬性，而非彙總對象規則內的事件，以建立完整串流對象。
doc-type: article
solution: Experience Platform
exl-id: fe6ee041-814f-41c1-91cf-c3473cbca0c2
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---


# 選項#2 — 使用預先彙總

對象中彙總的挑戰在於，我們的對象（串流時）是建構在批次對象對象內完成的彙總上。 由於行銷已經確定需要更即時的方法，因此我們做了三件事來將此納入設計：

- 在串流處理資料之前計算彙總

>[!NOTE]
>
>這相當罕見，因為大多數的串流資料都是圍繞單一事件而不是彙總而設計

- 使用非正規化計畫名稱
- 將資料串流到

## 建立對象

針對帳單資料使用量高但目前沒有最終電話方案的所有設定檔建立對象。

1. 建立新對象
1. 在「非事件屬性」索引標籤上搜尋「彙總」，並將兩個「彙總」拖曳至畫布上。 為每個設定適當的運運算元和值。

![為每個彙總設定適當的運運算元和值](assets/option-2-use-pre-aggregates-set-operators-and-values.png)



&#x200B;3. 在設定檔上搜尋計畫名稱並將其新增（XDM個別設定檔> Devbc >計畫詳細資訊>計畫名稱）。 選取不等於「Ultimate」

![選取計畫名稱不等於Ultimate](assets/option-2-use-pre-aggregates-select-does-not-equal-ultimate.png)



&#x200B;4. 提供說明。  驗證評估方法是串流。

&#x200B;5. 將對象儲存為&quot;*計費資料使用量高但無Ultimate計畫(Agg)*&quot;

>[!NOTE]
>
>請記住，我們已將彙總邏輯移至上游串流ETL層。
>
>這個選擇是在擁有批次對象和串流對象之間的權衡，其中行銷人員控制邏輯但將定義和控制權推送到ETL層，其中工程部門必須參與。

>[!TIP]
>
>**選用的挑戰實驗室**
>
>提早完成？
>
>我們希望VIP在購買時能即時收到特別訊息。  建立「VIP」受眾。  VIP是指上個月購買超過$1,000的客戶。
