---
hold: true
title: 建立使用案例#3
description: 建立批次對象，使用容器變數在一週內比對相同訂單的訂單下單和訂單取消事件。
doc-type: article
solution: Experience Platform
exl-id: 4b72b76f-de64-4712-85a6-ec7890b23b97
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---


# 建立使用案例#3

## 建立對象

1. 建立新對象
1. 將「訂購事件」新增至畫布
1. 新增「訂單取消事件」至「下單事件」的右側
1. 將時間變更為一週內

>[!NOTE]
>
>**事件型別欄位**
>
>我們原本可以使用：
>
>- 依Event Type=order.placed篩選的任何事件
>- 依「事件型別=order.canceled」篩選的任何事件

![將事件時間範圍變更為一週內](assets/build-use-case-3-change-time-to-within-a-week.png)



![已下單和已取消訂單事件設定為一週內發生](assets/build-use-case-3-change-time-to-within-a-week--2.png)

>[!NOTE]
>
>**時間**
>
>Audience Engine僅會使用時間戳記來解譯事件的順序。 因此，如果「事件」有多個日期時間欄位，請記住「時間戳記」欄位就是使用的欄位。



## 設定取消的事件

搜尋「訂單識別碼」，並將欄位拖曳至「已取消訂單事件」。

![搜尋訂單ID並將欄位拖曳到「訂單已取消」事件](assets/build-use-case-3-search-order-id-drag-onto-order-cancelled-event.png)

>[!NOTE]
>
>我們將新增「訂單ID」的篩選器，以確保「已下訂單」與「已取消訂單」相同



清除任何搜尋並按一下&#x200B;**瀏覽變數**&#x200B;下方的&#x200B;**置入**

![按一下以放置在[瀏覽變數]下](assets/build-use-case-3-click-into-placed-under-browse-variables.png)



向下展開至訂單ID，然後拖移以新增比較運算元

![向下展開至訂單ID並拖曳以新增比較運算元](assets/build-use-case-3-drill-down-to-order-id-add-compare-operand.png)

>[!WARNING]
>
>**請勿在變數**&#x200B;內使用搜尋
>
>不會保留變數的內容



您的最終結果應該如以下所示

![已新增訂單ID比較運算元的最終對象組態](assets/build-use-case-3-final-audience-configuration-result.png)

>[!NOTE]
>
>**容器**
>
>這是使用變數容器，以確保「已取消訂單」與已下單的訂單相同
>
>之前，我們使用容器來隔離陣列中的元素。 在此處，我們使用容器來參照另一個事件內篩選條件中的特定事件。
>
>「訂單已取消」事件可確保自己的訂單識別碼與下單的訂單識別碼相同
>
>我們還能如何使用此功能？
>
>- 比較頁面檢視的產品SKU是購買的產品SKU
>- 比較「送貨地點」與「帳單地點」不同
>- 比較相同資料型別的任意兩個欄位應該是可行的，即使事件可能來自不同的結構描述
>
>https\：//experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-blogs/how-exactly-do-containers-work-in-aep-segmentation-a-deader-look/ba-p/458780

>[!NOTE]
>
>**容器名稱**
>
>容器將從其內容繼承其變數名稱。
>
>例如：如果您使用「任何事件」卡，容器名稱將是「任何1」



## 儲存您的對象

1. 提供說明。 將評估方法設定為「批次」。
1. 將您的對象儲存為「在一週內已下訂單和已取消訂單&#x200B;*」*

>[!TIP]
>
>**選用的挑戰實驗室**
>
>提早完成？ 試試這個……
>
>我們想要為「放棄購物車」開始新的行銷活動。  建立放棄購物車的對象，但請確定我們不會在一小時內開始鎖定目標人員。
>
>
>
>還有時間嗎？ 試試這個……
>
>該企業合併並取得兩個新的業務單位：
>
>- ISP
>- 纜線
>
>您需要如何修改結構以包含這些專案？
