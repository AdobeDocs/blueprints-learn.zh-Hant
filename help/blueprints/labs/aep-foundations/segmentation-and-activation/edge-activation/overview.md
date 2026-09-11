---
title: Edge啟用
description: 瞭解Edge、串流和批次啟用速度的差異，並預覽建立邊緣區段和設定事件轉送的實驗步驟。
doc-type: overview-page
solution: Experience Platform
exl-id: 9ecadff9-3838-4cd4-93b1-7c23a232f84c
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 0%

---


# Edge啟用

## 啟用速度回顧

Adobe有三種啟動速度，可滿足不同需求：

1. Edge
1. 串流
1. 批次

我們將透過事件轉送、Edge Audiences和Edge Personalization，瞭解如何使用Adobe Edge來啟用。 接著，我們將說明如何使用從中樞到外部Edge的串流目的地。

>[!NOTE]
>
>我們不會在本實驗室說明批次啟用。 批次啟用可以排程在不同的時間間隔，並且這個時間很難在沒有至少3-24小時的實驗室環境中展示。



## 實驗室將涵蓋的內容

- 建立Edge區段
- 設定事件轉送
- 在Edge事件中傳送
- 此觸發程式
  - 符合資格的Edge區段
  - 在Edge上事件轉寄以傳送至webhook
