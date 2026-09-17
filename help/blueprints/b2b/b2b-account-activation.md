---
title: Advertising和檔案目的地的B2B帳戶啟用
description: 使用以帳戶為基礎的參與來建立帳戶對象，並將這些對象啟用至廣告目標和雲端儲存空間。
solution: Real-Time Customer Data Platform
exl-id: 578c0019-6133-4508-ae9d-8a8a463376f0
source-git-commit: 7f0b624616480cf563142c08eb0598d1dd55d551
workflow-type: tm+mt
source-wordcount: '965'
ht-degree: 1%
---

# B2B帳戶對廣告目的地和檔案目的地的啟用

以帳戶為基礎的參與可讓B2B行銷人員在&#x200B;**Real-Time Customer Data Platform B2B edition**&#x200B;中建立帳戶對象（公司清單），並將這些帳戶對象啟用至LinkedIn Matched Audiences、Bombora和Demandbase等廣告目的地，以及雲端儲存空間目的地。 這些客戶受眾可用於目標定位、銷售拓展和下游分析。

## 使用案例

使用以帳戶為基礎的參與，行銷人員可以解鎖三個關鍵使用案例：

- **填補購買群組的空白：**&#x200B;行銷人員可以在尚未擁有CMO或CIO角色聯絡人的帳戶上做廣告。 他們可以先建立帳戶的對象，而不需聯絡標題「CMO」或「CIO」，然後在LinkedIn相符對象或其他支援的廣告目的地啟用對象。 在目標中，他們隨後可以啟動行銷活動，鎖定具有「CMO」或「CIO」職稱的受眾和特定人員，以聯絡這些新聯絡人並突顯其產品的好處。
- **向現有客戶所在公司的其他部門追加銷售或交叉銷售：**&#x200B;行銷人員可以建立在3到9個月前購買產品X但尚未擁有產品Y的帳戶對象。接著，他們便可以啟用此帳戶對象，並透過LinkedIn比對對象、其他廣告平台或用於銷售和行銷推廣的雲端儲存空間匯出，強調產品Y適用於該目標對象的好處。
- **使用競爭產品的目標公司：**&#x200B;行銷人員可以行銷至帳戶，以取代競爭者的產品，即使這些帳戶沒有任何連絡人。 他們可以依據顯示競爭者產品擁有權或使用情況的合作夥伴或意圖資料，建立帳戶的對象，然後透過LinkedIn比對對象或其他支援的廣告目的地來啟用，以從目標帳戶取得聯絡人進行擴充。

## 應用程式

- Real-Time Customer Data Platform B2B edition
- （選用） Customer Journey Analytics B2B edition

## 整合模式

此Blueprint的一般整合模式包括：

- **RTCDP B2B edition→的B2B參與和CRM來源→帳戶對象→目的地**

  B2B參與和CRM系統（例如Marketo Engage、Salesforce和Microsoft Dynamics）會使用標準B2B結構描述和關係，將銷售機會/聯絡人、帳戶和機會傳送到&#x200B;**Real-Time CDP B2B edition**。 帳戶對象是建置在此統一的B2B資料模型上，並啟用至廣告和檔案目的地。

- **RTCDP B2B edition→的B2B意圖和事件來源→帳戶對象→目的地**

  B2B意圖和事件來源（例如Bombora Intent和Demandbase Intent）會將意圖和參與事件傳送至Experience Platform。 這些資料集對應至標準B2B結構描述，可讓行銷人員建立帳戶受眾（例如，湧上競爭對手主題的帳戶），並將其啟用至廣告和雲端儲存目的地。 在支援的情況下，帳戶對象可以交由Bombora和Demandbase等廣告合作夥伴啟用。

## 架構

<img src="assets/b2b-account-activation.png" alt="B2B帳戶啟動藍圖的參考架構" style="border:1px solid #4a4a4a"  width="100%" />

## 帳戶對象目的地

- **LinkedIn符合的對象**
- **龐博拉**
- **Demandbase**
- **雲端儲存空間目的地**
  - Azure Data Lake儲存第2代
  - 資料登陸區域
  - SFTP
  - Azure Blob
  - AWS S3

如需支援帳戶對象的最新目的地清單，請參閱目的地檔案。

## 護欄

設計和啟用帳戶對象時，請參閱下列護欄：

- [Real-Time Customer Data Platform B2B edition的護欄](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-guardrails?lang=en)
- [帳戶對象](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/ui/account-audiences?lang=en)
- [啟用帳戶對象](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/ui/activate/activate-account-audiences?lang=en)
- [設定檔和分段護欄](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/profile/guardrails)
- [串流細分資格標準更新](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/eligibility-criteria-update)

## Real-Time Customer Data Platform B2B edition的實作步驟、帳戶對象建立和啟用

- 如需Real-Time Customer Data Platform B2B edition的實施步驟，請參閱檔案： [Real-Time Customer Data Platform B2B edition快速入門](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-tutorial?lang=en)。
- 如需帳戶對象建立步驟，請參閱[帳戶對象](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/ui/account-audiences?lang=en)檔案。
- 如需帳戶對象啟用步驟，請參閱[啟用帳戶對象](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/ui/activate/activate-account-audiences?lang=en)檔案：

  - [LinkedIn相符對象目的地](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/ui/activate/activate-account-audiences?lang=en#required-mappings)的必要對應。

## 實施考量

LinkedIn相符對象具有最低對象人數要求（例如300個相符成員）。 如果啟用LinkedIn Matched Audiences的帳戶對象不符合這項要求，您可能需要擴大對象定義，以增加可比對的對象人數，然後再啟動行銷活動。

## 相關文件

- [B2B Audience和Profile Activation藍圖](b2bactivation.md) — 涵蓋人員層級和帳戶層級B2B啟用的父級Blueprint。
- [Real-Time Customer Data Platform的B2B edition](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-overview?lang=en)
- [建立及啟用帳戶對象 — 教學課程影片](https://experienceleague.adobe.com/zh-hant/docs/platform-learn/tutorials/audiences/create-audiences-with-b2b-data?lang=en)
- [建立帳戶對象](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/segmentation/ui/account-audiences?lang=en)
- [啟用帳戶對象](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/ui/activate/activate-account-audiences?lang=en)
- [Adobe Experience Platform - LinkedIn目的地聯結器](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/catalog/social/linkedin?lang=en)
- [Real-Time CDP B2B edition中的結構描述](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/rtcdp/schemas/b2b)
- [Real-Time CDP B2B edition的架構升級](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-architecture-upgrade)
- [目標護欄](https://experienceleague.adobe.com/zh-hant/docs/experience-platform/destinations/guardrails)
