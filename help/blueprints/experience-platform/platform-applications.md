---
title: Adobe Experience Platform 與應用程式架構圖
description: 此架構圖顯示 Adobe Experience Platform 如何與其他 Adobe Experience Cloud 應用程式及應用程式服務連結。
solution: Experience Platform, Campaign, Analytics, Target, Customer Journey Analytics, Journey Orchestration, Offer Decisioning, Real-time Customer Data Platform
kt: 7199
thumbnail: null
exl-id: 9b12cd7a-5e5f-443a-91a1-44273cdabc2d
source-git-commit: 6c4b72159d4ba2a171215678e4e4842956d82745
workflow-type: ht
source-wordcount: '939'
ht-degree: 100%

---

# Adobe Experience Platform 與應用程式

## Adobe Experience Platform 與應用程式架構圖

此架構圖顯示 Adobe Experience Platform 如何與 Adobe Experience Cloud 應用程式及應用程式服務連結。

<img src="assets/aep+apps_vertical.svg" alt="Experience Platform 與應用程式" style="border:1px solid #4a4a4a; width:80%;" />

>[!VIDEO](https://video.tv.adobe.com/v/32456/?quality=12&learn=on)

## Adobe Experience Platform 與應用程式詳細架構圖

<img src="assets/aep+apps_horizontal.svg" alt="Experience Platform 與應用程式" style="border:1px solid #4a4a4a; width:80%;" />

## Adobe Experience Platform 與 Experience Cloud 應用程式整合

<table class="relative-table wrapped" style="width: 100%;" >
   <colgroup>
    <col style="width: 16.0202%;"/>
    <col style="width: 29.3423%;"/>
    <col style="width: 33.5582%;"/>
    <col style="width: 21.0793%;"/>
  </colgroup>
  <tbody>
    <tr>
      <th>應用程式</th>
      <th>Experience Platform 到應用程式</th>
      <th>應用程式到 Experience Platform</th>
      <th>相關 Blueprints</th>
    </tr>
    <tr>
      <td colspan="1">Ad Cloud</td>
      <td colspan="1">
        <ul>
          <li>在即時客戶資料平台中定義的對象可透過 Audience Manager 共用至 Ad Cloud，以進行目標定位。</li>
        </ul>
      </td>
      <td colspan="1">目前無整合</td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/anonymous.html?lang=zh-Hant">匿名對象啟用</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/online-offline.html?lang=zh-Hant">線上/離線對象啟用</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/platform-and-applications.html?lang=zh-Hant">使用 Experience Platform 和應用程式啟用</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>Analytics</td>
      <td>目前無整合</td>
      <td>
        <ul>
          <li>Analytics 收集的資料可傳送至 Experience Platform 資料湖和設定檔儲存區。 <a href="https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html?lang=zh-Hant">Analytics Data Connector</a>
          </li>
        </ul>
      </td>
      <td>
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/platform-data-flow.html?lang=zh-Hant">Experience Platform 資料流程</a>
          </li>
        </ul>
        <p>
          <br/>
        </p>
      </td>
    </tr>
    <tr>
      <td>Audience Manager</td>
      <td>
        <ul>
          <li>可以與 Audience Manager 共用在即時客戶資料平台中定義的對象，以啟用至第三方 Cookie 目的地。</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>收集的資料和評估的對象會籍可以共用至 Experience Platform 資料湖和設定檔儲存區。 <a href="https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/audience-manager.html?lang=zh-Hant">Audience Manager 來源連接器</a>
          </li>
        </ul>
      </td>
      <td>
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/anonymous.html?lang=zh-Hant">匿名對象啟用</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/online-offline.html?lang=zh-Hant">線上/離線對象啟用</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/platform-and-applications.html?lang=zh-Hant">使用 Experience Platform 和應用程式啟用</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Campaign Classic</td>
      <td colspan="1">
        <ul>
          <li>在即時客戶資料平台中定義的對象可以共用至 Campaign Classic，作為啟動行銷活動的對象。</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>Campaign 所收集的互動和行銷活動資料可作為資料來源擷取至 Experience Platform，以便透過即時客戶資料平台進一步用於對象建立，以及透過 Customer Journey Analytics 和 Experience Platform 查詢服務及資料科學工作區進一步用於分析。</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/multi-channel-message-orchestration/batch-messaging.html?lang=zh-Hant">批次訊息傳送</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Campaign Standard</td>
      <td colspan="1">
        <ul>
          <li>在即時客戶資料平台中定義的對象可以共用至 Campaign Standard，作為啟動行銷活動的對象。</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>Campaign 所收集的互動和行銷活動資料可作為資料來源擷取至 Experience Platform，以便透過即時客戶資料平台進一步用於對象建立，以及透過 Customer Journey Analytics 和 Experience Platform 查詢服務及資料科學工作區進一步用於分析。</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/multi-channel-message-orchestration/batch-messaging.html?lang=zh-Hant">批次訊息傳送</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Customer Journey Analytics</td>
      <td colspan="1">
        <ul>
          <li>收集並擷取至 Experience Platform 資料湖的資料可供處理 Customer Journey Analytics。 </li>
        </ul>
      </td>
      <td colspan="1">目前沒有可用的整合。從 Customer Journey Analytics 共用對象結果到 Experience Platform 的能力正在設計中。</td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journey-analytics/overview.html?lang=zh-Hant">Customer Journey Analytics</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Experience Manager</td>
      <td colspan="1">
        <ul>
          <li>Experience Platform 設定檔可直接在伺服器端存取，以支援透過 Experience Manager 提供的個人化體驗。請注意，個人化活動最常透過 Experience Manager 經由 Target 整合傳送。 </li>
        </ul>
      </td>
      <td colspan="1">不會直接透過 Experience Platform Web 和 Mobile SDK 收集目前在 Experience Manager 網站上執行的整合、行為和互動。</td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/online-offline.html?lang=zh-Hant">線上/離線對象啟用</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Journey Optimizer</td>
      <td colspan="1">
        <ul>
          <li>擷取至 Experience Platform 的資料事件和設定檔可供 Journey Optimizer 使用，以發起並支援 Journey Optimizer 中的歷程。</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>Journey Optimizer 所生成的互動和行銷活動資料被收集至 Experience Platform，以便透過即時客戶資料平台進一步用於對象建立，以及透過 Customer Journey Analytics、Experience Platform 查詢服務及資料科學工作區進一步用於分析。</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/multi-channel-message-orchestration/triggered-messaging.html?lang=zh-Hant">觸發的訊息傳送</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Magento</td>
      <td colspan="1">目前無整合</td>
      <td colspan="1">目前無整合</td>
      <td colspan="1">目前無整合</td>
    </tr>
    <tr>
      <td colspan="1">Marketo</td>
      <td colspan="1">
        <ul>
          <li>在即時客戶資料平台中定義的對象可以共用至 Marketo，作為啟動 Marketo 行銷活動和更新 Marketo 物件的對象。</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>Marketo 帳戶、連絡人和商機資料以及 Marketo 所產生的互動和行銷活動資料，會擷取至 Experience Platform 中，以便透過 B2B-CDP 進一步用於對象構建，以及透過 Customer Journey Analytics、Experience Platform 查詢服務和資料科學工作區進一步用於分析。 <a href="https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo.html?lang=zh-Hant">Marketo Engage Connector</a>
          </li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>B2B Activation - 開發中</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">即時 CDP</td>
      <td colspan="1">
        <ul>
          <li>擷取和收集至 Experience Platform 的資料是匯整即時客戶設定檔的資料來源，這些設定檔為即時客戶資料平台提供支援。</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>「對象」和「設定檔」量度指標會傳送至 Experience Platform 資料湖，以支援設定檔深入分析報告控制面板。</li>
          <li>資料湖中的「對象」和「設定檔」資料可用於透過查詢服務、資料科學工作區和 Customer Journey Analytics 進一步進行深入分析。</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/online-offline.html?lang=zh-Hant">線上/離線對象啟用</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/platform-and-applications.html?lang=zh-Hant">使用 Experience Platform 和應用程式啟用</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Target</td>
      <td colspan="1">
        <ul>
          <li>在即時客戶資料平台中定義的對象可共用至 Target，並用於 Target 提供的個人化和目標定位體驗。 </li>
          <li>Experience Edge 與 Target 進行直接整合，以用於即時區段會籍和設定檔屬性存取的能力正在設計中。</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>為 Target 體驗和互動收集的資料可透過 Experience Platform Web SDK 收集至 Experience Platform。這些資料可用於透過即時客戶資料平台進行對象構建，以及用於透過 Customer Journey Analytics、Experience Platform 查詢服務和資料科學工作區進行分析。</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/online-offline.html?lang=zh-Hant">線上/離線對象啟用</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/platform-and-applications.html?lang=zh-Hant">使用 Experience Platform 和應用程式啟用</a>
          </li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>
