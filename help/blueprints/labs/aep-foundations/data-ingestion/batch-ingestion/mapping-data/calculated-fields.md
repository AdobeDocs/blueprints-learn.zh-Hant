---
title: 計算欄位
description: 建立計算欄位運算式，以回填遺失的SMS同意值，並將出生日期分割為日、月和年欄位。
doc-type: article
solution: Experience Platform
exl-id: ea5d006b-11c5-439c-af01-bc00b919851f
source-git-commit: 3076f01e06023cebd30ead73d61f4540da9ce791
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 0%

---


# 計算欄位

## 概觀

sms\_optIn欄位是客戶帳戶結構描述中的必填欄位。 問題是串流來源中的sms\_optIn欄位可以傳送&#x200B;*null*&#x200B;值，因此需要計算欄位才能解決此問題；否則擷取時會略過這些記錄，這會造成損失。

![目標結構描述中顯示的consents.marketing.sms.val欄位](assets/calculated-fields-consents-marketing-sms-val-schema-field.png "consents.marketing.sms.val欄位，結構描述中顯示的")



## 建立計算欄位

1. 按一下&#x200B;**新增欄位型別**&#x200B;圖示，然後選取&#x200B;**新增計算欄位**，以建立計算欄位。 對於所有遺失的值，假設未提供同意，並標示為&#x200B;**&quot;n&quot;**。 請注意，計算欄位會顯示在左欄，因為透過計算欄位的轉換是此新對應的輸入。

   ![新欄位型別圖示功能表已選取[新增計算欄位]選項](assets/calculated-fields-add-a-calculated-field.png "新增計算欄位")



1. 在[建立計算欄位]對話方塊中新增下列運算式，然後按一下[預覽] ****

   ```none
   iif(sms_optIn == null or sms_optIn == "", 'n', sms_optIn)
   ```

   ![使用sms_optIn運算式和預覽結果建立計算欄位對話方塊](assets/calculated-fields-sms-optin-calculated-field.png "sms_optIn計算欄位")



1. 您應該會在黑色方塊的右上角看到綠色核取記號，表示運算式的有效性，而且資料預覽應該只會顯示&#x200B;**&quot;n&quot;**&#x200B;或&#x200B;**&quot;y&quot;**&#x200B;為值。 如果一切正常，請按一下&#x200B;**儲存**。



## 對應至目標

新欄位會新增至對應畫面，但具有未對應的目標欄位路徑。

![新的sms_optin計算欄位已新增至對應畫面，且未對應目標欄位](assets/calculated-fields-sms-optin-unmapped.png "sms_optin未對應")

1. 按一下您建立的新計算欄位的&#x200B;**對應目標欄位**
1. 在右窗格中，您現在會看到目標結構面板已開啟。 在搜尋方塊中輸入&#x200B;**簡訊**
1. 選取&#x200B;**val**&#x200B;欄位

   ![針對計算欄位對應選取了sms.val欄位的目標結構描述面板](assets/calculated-fields-map-calculated-field-to-target-xdm-field.png)



   您的最終對應應如下所示：

   ![使用sms_optin計算欄位對應到目標結構描述的最終對應畫面](assets/calculated-fields-final-mapping-screen.png)



1. 驗證您的對應以確保它看起來不錯

![確認sms_optin對應有效的驗證按鈕](assets/calculated-fields-validate-mappings.png)

>[!NOTE]
>
>擷取期間，會拒絕任何沒有有效SMS值的列。 如果未啟用部分擷取，在此案例中，此列的擷取失敗會導致整個批次或檔案的擷取失敗。 啟用部分擷取後，必填欄位缺少值的列會被拒絕，但其他列會被擷取。



## 處理生日

需要將出生日、月份和年份分隔成個別的欄位，以便下游活動中不得使用其中某些欄位。 您必須建立兩個計算欄位才能解決此問題。

### 建立出生日期和月份的對應

1. 新增計算欄位以擷取設定檔的出生日期和月份
1. 針對計算欄位使用下列程式碼：

   >[!NOTE]
   >
   >嘗試透過分別執行程式碼片段來瞭解正在發生的情況，而不是僅複製上述程式碼，以瞭解其構成方式，以便在單一行中建立更複雜的計算欄位，因為不允許使用多行。 請嘗試下列步驟：
   >
   >1. `date(birth_Date,"M/d/yyyy")`
   >2. `date_part("day", date(birth_Date,"M/d/yyyy")).toString()`
   >3. `date_part("month", date(birth_Date,"M/d/yyyy")).toString()`
   >4. `concat(date_part("month", date(birth_Date,"M/d/yyyy")).toString(),`
   >   `"-", date_part("day", date(birth_Date,"M/d/yyyy")).toString())`



1. 按一下「預覽」，您應該會看到下列結果。 如果一切正常，請按一下&#x200B;**儲存**

   ![預覽出生日期和月份計算欄位運算式的結果](assets/calculated-fields-birth-day-month-preview.png)



1. 將計算欄位對應至&#x200B;**person.birthDayAndMonth**

1. 驗證您的對應



### 建立出生年份的對應

1. 使用下列程式碼建立新的計算欄位，以擷取設定檔的出生年份

   ```none
   date_part("yyyy",date(birth_Date,"M/d/yyyy"))
   ```

1. 將計算欄位對應到&#x200B;**person.birthYear**&#x200B;的目標位置

1. 驗證您的對應

>[!NOTE]
>
>請注意，日期格式為&#x200B;**MM/DD/YYYY**，但範例中的&#x200B;**birth\_Date**&#x200B;資料為日期與月份的單位數或雙位數。 若要讓&#x200B;**date**&#x200B;函式運作，您必須指定資料的輸入格式，例如&#x200B;**M/d/yyyy**，如此您就可以將月份和日數列為1到2位數。 如果沒有此日期輸入格式規格，這些對應的驗證就會失敗。
