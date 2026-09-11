---
title: Postman安裝
description: 在稍後的Labs中進行API呼叫之前，請先安裝Postman並熟悉其集合、環境和工作區介面。
doc-type: article
solution: Experience Platform
exl-id: c277edb5-f758-4955-bcd7-b15a9b9ab949
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 0%

---


# Postman安裝

## 目標

本實驗結束時，您將能夠安裝Postman、設定基本的工作區和環境，以便進行未來labs所需的後續api呼叫。

> [!IMPORTANT]
>
>本課程的各個labs需要Postman。  即使您已安裝Postman，也需要完成本實驗，以確保已安裝並正確設定環境檔案和API集合。



## 安裝Postman

導覽至Postman網站，然後下載Postman應用程式或利用Web版本 — > [https://www.postman.com/download/](https://www.postman.com/download/)

Postman網站上的![Postman下載頁面](assets/postman-installation-postman-download.png)

## 建立Postman工作區（選用）

如果您&#x200B;*是Postman的新手*，而且這是您的第一次安裝，則不需要建立新的工作區。 第一次啟動時，選擇繼續而不登入，您會使用不需要工作區的輕量型使用者端。

如果您&#x200B;*已經熟悉Postman*&#x200B;並已安裝它，則您可能已經登入並具有數個工作區。 如果是這種情況，我們建議您為&#x200B;*這個bootcamp*&#x200B;建立新的工作區。 您可以在[Postman網站上找到指示。](https://learning.postman.com/docs/collaborating-in-postman/using-workspaces/create-workspaces/)

## Postman介面

開啟Postman，快速熟悉應用程式的幾個方面。 為了與Experience Platform合作，我們實際上只需要專注於應用程式的幾個關鍵領域。

![Postman介面概觀，側欄、標題和標示為](assets/postman-installation-interface-overview.png "Postman介面")的主要工作區

## 側欄

側邊欄可讓您快速瀏覽不同的Postman元素。 在Labs中，您只會使用下列兩個專案：

**集合** — 可從外部位置匯入或自行建立的已儲存要求群組。

**環境** — 可在Postman要求中參考的一組變數。 在Experience Platform中，您可以將Postman環境視為IMS組織中Adobe沙箱的同義詞。我們將使用Postman中的環境功能



## 頁首

工作區 — 可讓您將工作組織成各種群組（即專案、團隊等）



## 主要工作區

主要工作區是您在Postman中工作時將執行大部分工作的區域。 所有API請求都會顯示在主要工作區域的特定標籤中。

**右側邊欄** — 根據目前選取的索引標籤，提供工具的額外存取權。 範例是請求、註釋和程式碼片段的檔案，以及一些功能。

**環境選擇器** — 可讓您在使用API時，快速切換不同的環境以存取預先設定的變數。 使用Experience Platform時，您將在指派的IMS組織內使用特定AEP沙箱時善用此工具。



## 頁尾

在Postman應用程式的最底部，您會找到一組函式，可讓您快速檢視呼叫的記錄、快速存取以尋找和取代，以及各種其他函式。



## 重述

您現在應該已安裝Postman並瞭解UI的一些基本知識
