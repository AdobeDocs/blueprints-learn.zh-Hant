---
title: 設定事件轉送
description: 瞭解事件轉送如何使用屬性、資料元素、規則和資料串流，將邊緣事件轉送至協力廠商端點。
doc-type: overview-page
solution: Experience Platform
exl-id: da3d1c7f-3642-4de7-a297-fc36d09e7336
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---


# 設定事件轉送

「事件轉送」位於Edge上，可讓我們建立一組規則和輕度轉換，以將事件傳送至任何端點。

在此步驟中，我們會將所有傳送至Edge的事件轉送至webhook。 webhook將做為協力廠商的Proxy，可讓我們檢視目前的情況。

若要設定此專案，我們將設定：

- 屬性，包含決定要轉送的專案和位置所需的所有擴充功能、資料元素和規則
  - 資料元素可參照傳入事件，或視需要將之剖析為多個個別元件
  - 此規則可新增任何條件，說明要轉送的內容、轉換裝載以及要傳送裝載的位置
- 資料串流，可設定要使用哪些服務（例如事件轉送和AEP）
  - 傳送至這些資料串流的資料隨後可以根據設定的服務採取動作（例如，轉送事件並將資料傳送至資料集）
