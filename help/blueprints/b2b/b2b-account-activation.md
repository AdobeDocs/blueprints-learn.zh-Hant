---
title: Advertising目的地和檔案目的地的B2B帳戶啟用
description: 使用以帳戶為基礎的參與，建立受眾，並透過目的地鎖定他們。
solution: Real-Time Customer Data Platform
exl-id: 578c0019-6133-4508-ae9d-8a8a463376f0
source-git-commit: a632042b3a7434dd88f52804e15e30fa06057e3b
workflow-type: tm+mt
source-wordcount: '718'
ht-degree: 4%

---

# B2B帳戶對廣告目的地和檔案目的地的啟用

以帳戶為基礎的參與可讓B2B行銷人員建立帳戶的對象（即公司清單），並透過LinkedIn之類的目的地鎖定這些公司，該目的地可接受公司清單作為輸入或匯出至雲端儲存目的地以用於目標定位和銷售推廣。

## 使用案例

使用以帳戶為基礎的參與，行銷人員可以解鎖三個關鍵使用案例：

* **填補購買群組的空白：**&#x200B;行銷人員可以在尚未擁有CMO或CIO角色聯絡人的帳戶上做廣告。 他們可以先建立帳戶的對象，而不需連絡人且標題為「CMO」或「CIO」，然後在LinkedIn上啟用對象。 在目標LinkedIn中，他們隨後可發起行銷活動，目標鎖定於擁有「CMO」或「CIO」職稱的受眾和特定人員，以聯絡這些新聯絡人並突顯其產品的優點。
* **向現有客戶所在公司的其他部門追加銷售或交叉銷售：**&#x200B;行銷人員可以建立在3到9個月前購買產品X但尚未擁有產品Y的帳戶對象。接著，他們就可以啟用，強調產品Y的優勢給該目標對象。
* **使用競爭產品的目標公司：**&#x200B;行銷人員可以行銷至帳戶，以取代競爭者的產品，即使這些帳戶沒有任何連絡人。 他們可以依據顯示競爭者產品所有權或使用情況的合作夥伴資料，建立帳戶的對象，然後透過LinkedIn對目標帳戶的來源聯絡人進行啟用，以進行擴展。

## 應用程式

* Real-time Customer Data Platform B2B版

## 整合模式

* B2B資料來源（Marketo、Salesforce等） -> Real-time Customer Data Platform B2B edition ->目的地。
* 各種B2B資料來源可用於將帳戶、銷售機會、機會和人員資料對應到Real-time Customer Data Platform的B2B edition。

## 架構

![B2B帳戶Audience Activation Blueprint的參考架構](assets/b2b-blueprint-account-audience-activation.png)

## 帳戶對象目的地

* （公司） LinkedIn相符的對象
* 雲端儲存空間目的地
   * Azure Data Lake
   * 資料登陸區域
   * SFTP
   * Azure Blob
   * AWS S3

## 護欄

* 每個沙箱的上限為50個帳戶區段。
* 批次細分評估。
   * 批次對象執行和設定檔匯出作業完成後，每24小時自動評估一次。
   * 不支援邊緣、串流或臨時評估。
* 帳戶屬性可供匯出。
* 人員活動。
   * 事件回顧最多30天，事件述詞不排序。
   * AND / OR受到支援（因此您可以說「A和B必須發生」）  但您無法說「A必須在B之前3天發生」)。
* 針對雲端儲存目標，匯出排程支援「區段評估後」選項。
* [B2B設定檔與分段護欄](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-guardrails)。

## 即時客戶資料平台B2B edition、帳戶對象建立和啟用的實作步驟

* 如需Real-time Customer Data Platform B2B edition的實作步驟，請參閱[Real-Time Customer Data Platform B2B版本快速入門](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-tutorial)檔案。
* 如需帳戶對象建立步驟，請參閱[帳戶對象](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/account-audiences)檔案。
* 如需帳戶Audience Activation步驟，請參閱[啟用帳戶對象](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-account-audiences)檔案。
   * [（公司） LinkedIn相符對象目的地](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-account-audiences#required-mappings)的必要對應。

## 實施考量

LinkedIn相符對象有一些要求，包括相符成員的最小對象人數為300人。 如果為公司連結的相符對象目的地啟用的帳戶對象不符合要求，則需要修改對象定義，以增加對象規模，從而啟動LinkedIn行銷活動。

## 相關文件

* [即時客戶資料平台的B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-overview)
* [建立及啟用帳戶對象教學課程影片](https://experienceleague.adobe.com/zh-hant/docs/platform-learn/tutorials/audiences/create-audiences-with-b2b-data)
* [建立帳戶對象](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/account-audiences)
* [啟用帳戶對象](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-account-audiences)
* [Adobe Experience Platform - LinkedIn目的地聯結器](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/social/linkedin)
