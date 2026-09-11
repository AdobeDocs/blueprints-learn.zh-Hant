---
title: 識別
description: 瞭解LID方法的兩部分識別步驟：標籤剩餘的表格型別並識別關鍵識別欄位。
doc-type: article
solution: Experience Platform
exl-id: 83657cf0-db35-4d4d-8cfb-1934ff40baca
source-git-commit: 8fba6e953de0e588af5398b21554ebad085899fd
workflow-type: tm+mt
source-wordcount: '157'
ht-degree: 0%

---


# 識別

## 學習目標

LID方法中的&#x200B;**識別**&#x200B;步驟分成兩個不同的部分：

1. 第1部分 — 剩餘的表格型別 — >識別剩餘的未標籤表格並標示反正規化型別
1. 第2部分 — 關鍵欄位 — >識別主要和支援實體的關鍵欄位



它會教導您在關聯模型中識別設計Real-Time Customer Profile所需的下列專案：

- Bridge表格（處理多對多關係的表格）
- 需要反正規化的表格
- 即時客戶個人檔案中的主要身分
- 主要實體類別中以人員為基礎的身分，可用於唯一識別人員
- 個別設定檔/體驗事件表格和相關聯的查閱表格之間的關係識別碼
- 體驗事件結構描述所需的必填欄位
- 個別設定檔和查詢結構描述的建議欄位
