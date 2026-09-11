---
hold: true
title: 修正傳遞對應
description: 在驗證之前，識別並修正不正確的AI/ML傳遞對應，例如重複或不相符的目標欄位指派。
doc-type: article
solution: Experience Platform
exl-id: b06cc091-661e-4ff4-b6e5-f16bc5128b6b
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---


# 修正傳遞對應

## 卸除特定對應

有些您必須使用計算欄位處理的來源資料。  若要解決這些問題，請從對應中卸除這些專案，然後重新驗證對應。

1. 從對應中拖放下列來源資料：
   - birth\_date
   - 來源
   - sms\_optIn
1. 按一下驗證按鈕以重新驗證對應

![在卸除欄位後用來重新驗證對應的「驗證」按鈕](assets/fix-passthrough-mappings-re-validate-mappings-using-validate-button.png "使用驗證按鈕重新驗證對應")

>[!NOTE]
>
>按一下「驗證」後，您仍可能會出現錯誤



## 錯誤的對應範例

雖然AI/ML建議有幫助，但有時是錯誤的。  如果您檢查建議，可能會發現您需要修正的這類錯誤

>[!NOTE]
>
>以下是您可能在自己的沙箱中看到的一些無效對應範例。 您也可能看到其他錯誤。

## 複製對應

在此案例中，您看到AI/ML推薦程式將兩個不同的來源欄位對應到相同的目標欄位&#x200B;**person.name.lastName**



![兩個對應到相同目標欄位person.name.lastName](assets/fix-passthrough-mappings-person-lastname-mapped-twice.png "person.name.lastName的兩個不同來源欄位在此對應中對應到兩次")

![涉及plan_name欄位](assets/fix-passthrough-mappings-plan-name-duplicate-mapping.png)的重複傳遞對應範例



## 錯誤的對應

這個對應看起來是正確的，但在仔細檢查時，**電子郵件**&#x200B;與&#x200B;**emailFormat**&#x200B;不同

![對應電子郵件不正確對應，而非emailFormat的對應](assets/fix-passthrough-mappings-email-mapped-incorrectly.png "電子郵件似乎正確對應，但依照要求是不正確的")

這個&#x200B;**email\_optIn**&#x200B;對應到錯誤的同意物件不正確

![email_optIn未正確對應到錯誤的同意物件](assets/fix-passthrough-mappings-email-optin-wrong-consent-object.png "email_optIn似乎已正確對應，但依照要求是不正確的")



## 修正傳遞對應

若要修正指向錯誤目標欄位的傳遞對應，請執行以下步驟。

### 範例

1. 從無效對應開始，然後按一下目標欄位方塊。 例如，在下列對應中，**person.name.lastName**&#x200B;欄位未正確對應，且已對應至&#x200B;**planName**
1. 在右側開啟的目標結構描述面板中，選擇適當的目標欄位並選取&#x200B;**\_devbc.plan.name**
1. 目標欄位現在應在目標欄位方塊中更新
1. 修正每個這類錯誤後，您應該按下&#x200B;**驗證**&#x200B;按鈕，以確保減少這類錯誤，並且不會引入新錯誤。



![處理對應清單以修正每個對應錯誤](assets/fix-passthrough-mappings-work-through-mapping-errors.png "處理對應並修正對應錯誤")



![目標結構描述面板，用於選取正確的欄位以修正傳遞對應](assets/fix-passthrough-mappings-choose-correct-target-field.png "選擇正確的目標欄位，並驗證它是否符合傳遞需求")

>[!WARNING]
>
>在解決所有對應錯誤之前，請勿繼續下一個步驟
