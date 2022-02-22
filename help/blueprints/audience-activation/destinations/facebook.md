---
title: 激活到Facebook自定義受眾
description: 激活到Facebook自定義受眾。
solution: Experience Platform, Real-time Customer Data Platform, Data Collection
kt: 7086
exl-id: b75a7a01-04ba-4617-960d-f73f7a9cc6c7
source-git-commit: 051b094412419363e5e2406f2e436cc528bd409e
workflow-type: tm+mt
source-wordcount: '957'
ht-degree: 3%

---

# 激活到Facebook自定義受眾

從多個來源接收客戶資料以構建客戶的單個配置檔案視圖，將這些配置檔案細分為構建的受眾以進行營銷和個性化，將這些受眾共用到社交廣告網路(如Facebook)，以針對這些受眾進行定向和個性化活動。

## 使用案例

* 對社交及廣告目標上已知對象的對象目標定位。
* 使用線上和離線屬性的線上個人化。

## 應用程式

* 即時客戶資料平台

## 架構

<img src="../assets/facebook.png" alt="facebook定制Audience Activation的參考體系結構" style="width:80%; border:1px solid #4a4a4a" />

## 實施步驟

1. 配置要在配置檔案資料源中使用的標識命名空間。
   * 使用現成的命名空間（如電子郵件、電子郵件SHA256哈希）（可用）。
   * Facebook有一個支援的身份清單。 為了激活到Facebook自定義受眾，必須在要激活的配置檔案中存在支援的身份之一。
   * 以下標識目前受Facebook支援：GAID、IDFA、phone_sha256、email_lc_sha256、extern_id。
   * 有關其他詳細資訊，請參閱 [Facebook目的地指南](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/social/facebook.html)。
   * 建立自定義命名空間，其中非現成命名空間對於適用的標識不可用。
1. 配置配置檔案資料源架構和資料集。
   * 為所有配置檔案記錄源資料建立配置檔案記錄方案。
      * 指定每個架構的主標識和次標識。
      * 啟用架構以接收配置檔案。
   * 為所有配置檔案記錄源資料建立配置檔案記錄資料集，分配關聯的架構。
      * 啟用資料集以接收配置檔案。
   * 為所有基於配置檔案時間序列的源資料建立配置檔案體驗事件方案。
      * 指定架構的主標識和次標識。
   * 啟用架構以接收配置檔案。
   * 為所有配置檔案體驗事件源資料建立配置檔案體驗事件資料集，並分配關聯的架構。
      * 啟用資料集以接收配置檔案。
1. 使用源連接器將源資料接收到上面配置的關聯資料集。
   * 使用憑據配置源連接器帳戶。
   * 配置資料流，將指定時間表的源檔案或資料夾位置的資料接收到指定的資料集。
   * 將源資料中的任何欄位映射到目標架構。
   * 將任何欄位轉換為正確的格式以接收為Experience Platform。
      * 日期轉換
      * 在適當時轉換為小寫 — 例如電子郵件地址
      * 模式轉換（例如電話號碼）
      * 如果源資料中不存在，則為體驗事件記錄添加唯一記錄ID。
      * 轉換陣列和映射類型欄位以確保正確映射和建模陣列和映射以在Experience Platform中分段。
1. 配置配置檔案合併策略以確保正確配置標識圖以及在合併配置檔案時應包括哪些資料集。
1. 執行資料流後，確保配置檔案資料接收成功且無錯誤。
   * Inspect幾個配置檔案的身份圖以確保正確處理身份關係。
   * Inspect多個配置檔案的屬性和事件，以確保正確接收配置檔案的屬性和事件。
1. 創作段以建立配置檔案受眾
   * 使用屬性和事件規則在段生成器中生成段。
   * 保存段以進行評估。 段將按指定的計畫每天計算一次。
      * 如果段規則適合流分段，則當為配置檔案接收新的流資料時，將評估段。 在計畫的批處理分段期間，流段也將每天評估一次。
1. 確保分部業績符合預期。
   * 複查給定段的段結果計數。
   * 調查應包括在段中的配置檔案，以驗證段成員資格是否包括在配置檔案的段成員資格部分中。
1. 在「目標」配置中配置訪問群體到目標的傳遞。
   * 查看 [Facebook目的地指南](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/social/facebook.html) 有關配置Facebook目標的詳細資訊。
   * 配置目標時，選擇要激活到目標的受眾。
   * 確定希望目標資料流開始將訪問群體傳送到目標的預定開始日期。
   * 每個目標都具有要發送的必需屬性和可選屬性。
      * 對於Facebook，必須包括其中一個必需的身份，並用於將Experience Platform內受眾中的個人資料與Facebook可瞄準的個人資料相匹配。
   * 每個目標還具有指定的傳遞類型，無論是流傳輸還是批處理、基於檔案或JSON負載。
      * 對於Facebook，觀眾成員身份以流式方式以JSON格式發送給Facebook終結點。
      * 在流式處理或Experience Platform中的批分段評估之後，將以流式方式交付受眾成員。
1. 確保目標流已按預期將受眾傳遞到目標。
   * 檢查監視介面，確認已將受眾與預期的配置檔案數量一起交付。 受眾大小應反映激活的配置檔案的預期數量，指出特定目標(如Facebook)將需要某些欄位，如電子郵件哈希標識，如果不存在於作為受眾成員的配置檔案中，則不會激活到目標。
   * 檢查是否有任何跳過的配置檔案標識缺失或屬性缺失（必需）。
   * 檢查是否有其他需要解決的錯誤。
1. 驗證受眾是否已使用預期的受眾成員數激活到最終目標。
   * 登錄Facebook定制受眾門戶以驗證是否已傳送來自Real-time Customer Data Platform的受眾，以及Facebook受眾中個人資料的匹配率是否與來自Real-time Customer Data Platform的受眾中個人資料的數量合理匹配。

## 護欄

[輪廓和分段護欄](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=zh-Hant)

## 相關文件

激活到Facebook自定義受眾 —  [目標配置](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/social/facebook.html)