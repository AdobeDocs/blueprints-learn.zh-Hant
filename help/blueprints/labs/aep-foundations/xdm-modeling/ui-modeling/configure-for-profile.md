---
title: 為設定檔進行設定
description: 標示主要和人員身分欄位、建立方案關係、啟用即時客戶設定檔的方案，以及檢閱設定檔聯合方案。
doc-type: article
solution: Experience Platform
exl-id: 52cfc0d2-ba8c-4f81-9e03-c5c2c5e276b7
source-git-commit: 3039df0c022176e9dada9c5a300f2df14429033d
workflow-type: tm+mt
source-wordcount: '920'
ht-degree: 0%

---


# 為設定檔進行設定

## 概觀

若要將方案用於Real-time Customer Profile，您必須先確保其設定正確。 這表示將您在LID實驗室中識別的內容當成主要/個人身分、關係身分等，並確保針對每個結構描述進行這些設定。 完成所有工作後，您可以「翻轉開關」並啟用結構描述以與設定檔一起使用。

檢視Connection 5G ERD紙張上的XDM，您會看到關於客戶帳戶結構的下列資訊。  這是要在Real-Time Customer Profile中利用結構描述的工作。



![紙張客戶帳戶結構描述上的連線5G XDM及其相關查閱表格](assets/configure-for-profile-connection-5g-erd-customer-account-schema.jpeg "紙張客戶帳戶結構描述上的連線5G XDM及其相關查閱表格")


## 標籤主要身分欄位

每個結構描述都需要主要身分欄位，才能與即時客戶個人檔案搭配使用。 請依照下列步驟，將欄位標示為主要身分。

1. 開啟您建立的&#x200B;**客戶帳戶**&#x200B;結構描述
1. 按一下結構描述中的欄位來選取&#x200B;**\_\&lt;tenant-name>.customerID**&#x200B;欄位
1. 在右側邊欄中，勾選&#x200B;**身分**&#x200B;和&#x200B;**主要身分**&#x200B;核取方塊
1. 從下拉式清單中選取&#x200B;**customerID**&#x200B;名稱空間
1. 完成時，請按一下右側邊欄中的&#x200B;**套用**&#x200B;按鈕，然後&#x200B;**儲存**&#x200B;您的變更。

![將customerID欄位標示為主要身分](assets/configure-for-profile-mark-customerid-as-primary-identity.png "將_dxp.customerID標示為主要身分")

>[!NOTE]
>
>按一下套用後，驗證您的欄位上是否顯示指紋，如下所示
>
>標示為身分後，在欄位上顯示![指紋圖示](assets/configure-for-profile-identity-thumbprint-icon.png)
>
>

>[!NOTE]
>
>另請注意，您現在應該會在左側邊欄中看到下列專案。 身分（主要或非主要）會顯示在這裡，而&#x200B;**主要**&#x200B;身分也標示為必填欄位。
>
>
>
>左側邊欄中的![身分割槽段顯示主要和非主要身分欄位](assets/configure-for-profile-identities-list-in-left-rail.png)



## 標示人員身分欄位

請記住，每個要與Real-Time Customer設定檔&#x200B;**搭配使用的結構描述，可選擇性地包含**&#x200B;個其他人員身分識別欄位。 若要將欄位標示為人員身分，請在您先前建立的「客戶帳戶」綱要上執行下列動作。

1. 選取&#x200B;**個人電子郵件地址**&#x200B;欄位
1. 檢查右側邊欄中的&#x200B;**身分**&#x200B;核取方塊
1. 從下拉式清單中選取&#x200B;**電子郵件**&#x200B;身分名稱空間
1. **套用並儲存**&#x200B;您的變更

![將personalEmail.address欄位標示為身分](assets/configure-for-profile-mark-personal-email-as-identity.png "將personalEmail.address標示為身分")

>[!NOTE]
>
>按一下「套用」後，驗證您的欄位上是否顯示指紋



## 建立結構描述關係

若要依照ERD中的概述，將「計畫」結構描述與客戶帳戶結構描述建立關聯，您必須定義關係。 請依照下列步驟，在客戶帳戶與計畫（查詢）方案之間建立方案關係。

### 新增關係

1. 選取Plan物件中的&#x200B;**planID**&#x200B;欄位，如下所示
1. 在右側邊欄中，按一下&#x200B;**新增關係**&#x200B;圖示

![新增在planID欄位上選取的關係圖示](assets/configure-for-profile-add-relationship-to-planid-field.png "新增關係至planID欄位")



### 定義關係

1. 在「型別」選取方塊中，選取&#x200B;**一對一**&#x200B;選項
1. 在「參考結構描述」選取方塊中，選擇名為&#x200B;**dep： Plan \[Lookup]**&#x200B;的結構描述（這是為您預先建立的）
1. 按一下&#x200B;**套用**&#x200B;和&#x200B;**儲存**

![定義與深層的一對一關係：計畫[查詢]結構描述](assets/configure-for-profile-define-one-to-one-relationship.png)



### 確認關係

完成後，您應該會看到您建立的關係顯示，如底下熒幕擷圖所示。

![確認已建立客戶帳戶與計畫結構描述之間的關係](assets/configure-for-profile-relationship-created-confirmation.png "已建立關係")



## 設定設定檔的結構描述

即時客戶設定檔會合併來自不同來源的資料，以建構每個個別客戶的完整檢視。 如果您希望結構描述擷取的資料參與此程式，您必須設定結構描述以用於設定檔。 若要這麼做，您必須執行下列步驟：



1. 開啟您新建立的&#x200B;**客戶帳戶 — \[您的縮寫]**&#x200B;結構描述
1. 從左側欄按一下您的結構描述標題
1. 透過在右側邊欄中切換&#x200B;**ON**&#x200B;設定檔的結構描述以進行設定
1. 在出現的強制回應視窗中，按一下&#x200B;**啟用**&#x200B;按鈕
1. 完成時，別忘了&#x200B;**儲存**&#x200B;您的結構描述！

![在右邊欄中為客戶帳戶結構描述啟用設定檔切換](assets/configure-for-profile-schema-profile-toggle.png "結構描述設定檔切換")

在切換設定檔切換後出現的強制回應視窗中的![啟用按鈕](assets/configure-for-profile-enable-profile-modal.png)

>[!TIP]
>
>恭喜！  您剛才已建立要與即時客戶個人檔案搭配使用的結構描述。



## 檢閱設定檔聯合結構描述

如前所述，XDM和即時客戶個人檔案的力量是能夠將個人的各種片段及其行為組合在一起。  這稱為客戶的「聯合檢視」。  在下列步驟中，您會預覽針對即時客戶設定檔設定的每個XDM類別中此聯合的外觀

1. 導覽至左側邊欄中的&#x200B;**設定檔**
1. 選取頂端功能表上的&#x200B;**聯合結構描述**&#x200B;索引標籤
1. 從下拉式清單中選取&#x200B;**XDM個別設定檔**&#x200B;類別

瀏覽XDM Individual Profile類別，然後花一些時間檢閱其他類別，例如XDM ExperienceEvent或Plan類別。

XDM個別設定檔類別的![設定檔聯合結構描述檢視](assets/configure-for-profile-profile-union-schema-view.png "設定檔聯合結構描述檢視")

>[!NOTE]
>
>請注意，顯示的結構是沙箱中所有啟用設定檔的結構描述的彙總合併檢視。 階層XDM結構中的類似欄位會合併在一起，而具有不同名稱和/或階層的欄位會新增到整體檢視。
> [!NOTE]
>
>只有XDM個別設定檔型別會執行類似名稱欄位之間的合併。
