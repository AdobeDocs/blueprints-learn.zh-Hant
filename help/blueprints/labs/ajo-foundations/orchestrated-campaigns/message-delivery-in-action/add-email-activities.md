---
hold: true
title: 新增電子郵件活動
description: 瞭解如何在協調的行銷活動中，使用不同的電子郵件通道設定，在個別的分支上新增及設定兩個電子郵件活動。
doc-type: article
solution: Experience Platform
exl-id: e911a251-9f9f-484c-a2de-101b0fc2c417
source-git-commit: 2b2b9b9c359c4cc6757ac62ad502ece9a4923095
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---


# 新增電子郵件活動

## 目標

在接下來的幾組步驟中，您將建置促銷活動，以將兩個電子郵件活動新增至兩個復本活動分支。 您將設定兩個電子郵件活動以使用先前建立的電子郵件頻道。 最後，您也會將基本電子郵件設定（主旨與內文）新增至這些電子郵件活動的每一項中。

>[!CAUTION]
>
>在繼續之前，您必須確定您的兩個電子郵件通道設定在其狀態中都顯示為作用中。
>
>![兩個電子郵件通道設定都顯示使用中狀態](assets/add-email-activities-email-channel-configs-active.png "電子郵件通道設定")



## 新增主要分支電子郵件活動

1. 按一下頂端流程的&#x200B;**+**，並從&#x200B;**頻道活動**&#x200B;中選取&#x200B;**電子郵件**

![新增電子郵件活動](assets/add-email-activities-select-email-activity.png)

**電子郵件**&#x200B;詳細資料窗格開啟

![電子郵件詳細資料窗格](assets/add-email-activities-email-details-pane.png)

2. 使用&#x200B;**電子郵件**&#x200B;活動的設定檔屬性&#x200B;**，將標籤重新命名為**&#x200B;電子郵件，然後按一下&#x200B;**編輯電子郵件**。 請注意，建立電子郵件內文僅供測試之用

![重新命名電子郵件活動標籤，然後按一下[編輯電子郵件]](assets/add-email-activities-rename-and-edit-email.png)

3. 選取「**動作**」標籤，然後從下拉式清單中選取「**設定檔 — 電子郵件**」頻道設定

![在[動作]索引標籤中選取設定檔 — 電子郵件通道設定](assets/add-email-activities-select-profile-email-channel.png)

4. 接著，按一下&#x200B;**編輯內容**&#x200B;以新增一些測試內容

![按一下[編輯內容]以新增測試內容](assets/add-email-activities-edit-content.png)

5. 提供&#x200B;**主旨列** （「基本計畫成員的升級優惠」），然後按一下&#x200B;**編輯電子郵件內文**&#x200B;按鈕

![新增主旨行並編輯電子郵件內文](assets/add-email-activities-subject-line-edit-body.png)

6. 有許多選項，對於此測試，請選擇&#x200B;**自行編碼** HTML選項

![選擇編碼您自己的HTML選項](assets/add-email-activities-code-your-own-html.png)

7. 在&#x200B;**電子郵件Designer**&#x200B;中，插入測試行「有可用的升級優惠！」 在所示的`</body></html>`標籤之前，按一下&#x200B;**儲存**

![在電子郵件Designer中插入測試行並按一下[儲存]](assets/add-email-activities-email-designer-save.png)

8. 等候確認訊息出現在右下角

![顯示確認訊息](assets/add-email-activities-confirmation-message.png)

9. 按一下&#x200B;**電子郵件Designer**&#x200B;旁的&#x200B;**向左箭號**&#x200B;結束

![按一下向左鍵結束電子郵件Designer](assets/add-email-activities-exit-email-designer.png)

10. 確認對話方塊隨即出現，請按一下&#x200B;**儲存並關閉**&#x200B;按鈕

![含有[儲存並關閉]按鈕的確認對話方塊](assets/add-email-activities-save-and-close-dialog.png)

11. 檢閱電子郵件屬性和動作，包括新增至電子郵件內文的文字。 按一下&#x200B;**向左箭頭**&#x200B;以導覽回促銷活動畫布

![導覽回促銷活動畫布](assets/add-email-activities-back-to-campaign-canvas.png)

## 新增底部分支電子郵件活動

回到行銷活動畫布，按一下底部流程的&#x200B;**+**，並從&#x200B;**頻道活動**&#x200B;中選取&#x200B;**電子郵件**。 請遵循上述相同步驟（步驟2至11），但以下步驟除外：

- 針對&#x200B;**電子郵件**&#x200B;活動，使用Target Dimension **將標籤重新命名為**&#x200B;電子郵件
- 在電子郵件設定中，選擇&#x200B;**關聯式電子郵件**&#x200B;電子郵件通道設定

![設定為關聯式電子郵件通道的第二個電子郵件活動](assets/add-email-activities-bottom-branch-relational-email.png "新增第二個電子郵件活動")

## 重述

您現在已瞭解如何使用電子郵件通道設定電子郵件活動。 每個活動接著都會設定非常基本的電子郵件主旨與內文。 接下來將測試整個行銷活動。
