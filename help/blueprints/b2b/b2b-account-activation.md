---
title: Advertising目的地和檔案目的地的B2B帳戶啟用
description: 使用以帳戶為基礎的參與，建立受眾，並透過目的地鎖定他們。
solution: Real-Time Customer Data Platform
source-git-commit: 074edca2f061459935d5f8b5e59e8cbd69b0fe4f
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 5%

---

# B2B帳戶對廣告目的地和檔案目的地的啟用

以帳戶為基礎的參與可讓B2B行銷人員建立帳戶受眾（即公司清單），並透過LinkedIn之類的目的地鎖定這些公司，該目的地接受公司清單作為輸入或匯出至雲端儲存目的地以進行目標定位和銷售推廣。

## 使用案例

使用以帳戶為基礎的參與，行銷人員可以解鎖三個關鍵使用案例：

* **填補購買群組的空白：**&#x200B;行銷人員可以在尚未擁有CMO或CIO角色聯絡人的帳戶上做廣告。 他們可以先建立帳戶的對象，而不需聯絡標題「CMO」或「CIO」，然後在LinkedIn上啟用對象。 在目標位置LinkedIn，他們隨後可以啟動行銷活動，鎖定具有「CMO」或「CIO」職稱的受眾和特定人員，以聯絡這些新聯絡人並突顯其產品的好處。
* **向現有客戶所在公司的其他部門追加銷售或交叉銷售：**&#x200B;行銷人員可以建立在3到9個月前購買產品X但尚未擁有產品Y的帳戶對象。接著，他們就可以啟用，強調產品Y的優勢給該目標對象。
* **使用競爭產品的目標公司：**&#x200B;行銷人員可以行銷至帳戶，以取代競爭者的產品，即使這些帳戶沒有任何連絡人。 他們可以依據顯示競爭者產品所有權或使用情況的合作夥伴資料，建立帳戶的對象，然後透過LinkedIn啟用至目標帳戶的來源聯絡人以進行擴充。

## 應用程式

* Real-time Customer Data Platform B2B版

## 整合模式

* B2B 資料來源（Marketo、Salesforce 等）-> Real-time Customer Data Platform B2B Edition ->目的地。
* 各種B2B資料來源可用於將帳戶、銷售機會、機會和人員資料對應至Real-time Customer Data Platform的B2B版本。

## 架構

![B2B帳戶Audience ActivationBlueprint的參考架構](assets/b2b-blueprint-account-audience-activation.png)

## 帳戶對象目的地

* （公司） LinkedIn相符的受眾
* 雲端儲存空間目的地
   * Azure資料湖
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
* [B2B設定檔與分段護欄](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-guardrails)。

## Real-time Customer Data Platform B2B Edition、帳戶對象建立和啟用的實作步驟

* 如需Real-time Customer Data Platform B2B版本的實作步驟，請參閱[Real-time Customer Data Platform B2B版本快速入門](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-tutorial)檔案。
* 如需帳戶對象建立步驟，請參閱[帳戶對象](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/ui/account-audiences)檔案。
* 如需帳戶Audience Activation步驟，請參閱[啟用帳戶對象](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/ui/activate/activate-account-audiences)檔案。
   * [&#x200B; （公司） LinkedIn的必要對應符合對象目的地](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/ui/activate/activate-account-audiences#required-mappings)。

## 實施考量

linkedIn相符對象有一些要求，包括相符成員300人的最小對象規模。 如果為公司連結的相符對象目的地啟用的帳戶對象不符合要求，則需要修改對象定義，以增加對象規模，以啟動LinkedIn行銷活動。

## 相關文件

* [B2B 版 Real-time Customer Data Platform](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-overview)
* [建立並啟用帳戶對象教學課程影片](https://experienceleague.adobe.com/zh-hant/docs/platform-learn/tutorials/audiences/create-audiences-with-b2b-data)
* [建立帳戶對象](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/ui/account-audiences)
* [啟用帳戶對象](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/ui/activate/activate-account-audiences)
* [Adobe Experience Platform - LinkedIn目的地聯結器](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/catalog/social/linkedin)
