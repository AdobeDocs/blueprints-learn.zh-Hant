---
title: 修正CreateDate的MAPPER錯誤
description: 疑難排解並解決因格式錯誤的createDate值轉換成空白欄位所導致的MAPPER錯誤。
doc-type: article
solution: Experience Platform
exl-id: e3f7ef23-6fd1-4f7a-8dc7-db82445322b0
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 0%

---


# 修正CreateDate的MAPPER錯誤

在本練習中，您將需要找出如何移除我們在批次擷取實驗室中看到的MAPPER錯誤。 此錯誤需要修正，因為即使createDate不是必要欄位，記錄仍會被擷取，因為格式錯誤的日期會轉換為空白欄位。

![createDate值格式無效，造成MAPPER錯誤](assets/fix-mapper-errors-for-createdate-invalid-format-mapper-error.png)
