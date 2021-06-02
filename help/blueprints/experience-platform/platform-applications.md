---
title: Adobe Experience Platform 與應用程式架構圖
description: 此架構圖顯示 Adobe Experience Platform 如何與其他 Adobe Experience Cloud 應用程式及應用程式服務連結。
solution: Experience Platform, Campaign, Analytics, Target, Customer Journey Analytics, Journey Orchestration, Offer Decisioning, Real-time Customer Data Platform
kt: 7199
thumbnail: null
exl-id: 9b12cd7a-5e5f-443a-91a1-44273cdabc2d
source-git-commit: 6c4b72159d4ba2a171215678e4e4842956d82745
workflow-type: tm+mt
source-wordcount: '939'
ht-degree: 11%

---

# Adobe Experience Platform 與應用程式

## Adobe Experience Platform 與應用程式架構圖

此架構圖顯示 Adobe Experience Platform 如何與 Adobe Experience Cloud 應用程式及應用程式服務連結。

<img src="assets/aep+apps_vertical.svg" alt="Experience Platform 與應用程式" style="border:1px solid #4a4a4a; width:80%;" />

>[!VIDEO](https://video.tv.adobe.com/v/32456/?quality=12&learn=on)

## Adobe Experience Platform 與應用程式詳細架構圖

<img src="assets/aep+apps_horizontal.svg" alt="Experience Platform 與應用程式" style="border:1px solid #4a4a4a; width:80%;" />

## Adobe Experience Platform與Experience Cloud應用程式整合

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
      <th>Experience Platform到應用程式</th>
      <th>應用程式到Experience Platform</th>
      <th>相關藍圖</th>
    </tr>
    <tr>
      <td colspan="1">Ad Cloud</td>
      <td colspan="1">
        <ul>
          <li>即時客戶資料平台中定義的對象可共用至Ad Cloud，以透過Audience Manager鎖定目標。</li>
        </ul>
      </td>
      <td colspan="1">無當前整合</td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/anonymous.html?lang=en">匿名對象啟用</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/online-offline.html?lang=en">線上/離線對象啟用</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/platform-and-applications.html?lang=en">使用Experience Platform和應用程式啟動</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>Analytics</td>
      <td>無當前整合</td>
      <td>
        <ul>
          <li>Analytics收集的資料可傳送至Experience Platform資料湖和設定檔存放區。 <a href="https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html?lang=en">Analytics Data Connector</a>
          </li>
        </ul>
      </td>
      <td>
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/platform-data-flow.html?lang=en">Experience Platform資料流程</a>
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
          <li>可以與Audience Manager共用在即時客戶資料平台中定義的對象，以啟用至第三方Cookie目的地。</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>收集和評估的受眾成員資格資料可以共用至Experience Platform資料湖和設定檔存放區。 <a href="https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/audience-manager.html?lang=en">Audience Manager 來源連接器</a>
          </li>
        </ul>
      </td>
      <td>
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/anonymous.html?lang=en">匿名對象啟用</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/online-offline.html?lang=en">線上/離線對象啟用</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/platform-and-applications.html?lang=en">使用Experience Platform和應用程式啟動</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Campaign Classic</td>
      <td colspan="1">
        <ul>
          <li>可在即時Campaign Classic資料平台中定義的受眾可以共用給客戶，作為啟動行銷活動的受眾。</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>Campaign所收集的互動和促銷活動資料可擷取至Experience Platform，作為資料來源，以便透過即時客戶資料平台建立受眾，並透過Customer Journey Analytics和Experience Platform查詢服務及資料科學工作區進行分析，以供進一步使用。</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/multi-channel-message-orchestration/batch-messaging.html?lang=en">批次傳訊</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Campaign Standard</td>
      <td colspan="1">
        <ul>
          <li>可在即時Campaign Standard資料平台中定義的受眾可以共用給客戶，作為啟動行銷活動的受眾。</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>Campaign所收集的互動和促銷活動資料可擷取至Experience Platform，作為資料來源，以便透過即時客戶資料平台建立受眾，並透過Customer Journey Analytics和Experience Platform查詢服務及資料科學工作區進行分析，以供進一步使用。</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/multi-channel-message-orchestration/batch-messaging.html?lang=en">批次傳訊</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Customer Journey Analytics</td>
      <td colspan="1">
        <ul>
          <li>收集並擷取至Experience Platform資料湖的資料可供處理至Customer Journey Analytics。 </li>
        </ul>
      </td>
      <td colspan="1">目前沒有可用的整合。 從Customer Journey Analytics分享受眾結果的Experience Platform能力，在藍圖上。</td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journey-analytics/overview.html?lang=en">Customer Journey Analytics</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Experience Manager</td>
      <td colspan="1">
        <ul>
          <li>Experience Platform設定檔可直接在伺服器端存取，以透過Experience Manager提供個人化體驗。 請注意，個人化活動最常透過Target整合透過Experience Manager傳送。 </li>
        </ul>
      </td>
      <td colspan="1">不會透過Experience ManagerWeb和行動SDK直接收集目前在Experience Platform網站上執行的整合、行為和互動。</td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/online-offline.html?lang=en">線上/離線對象啟用</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Journey Optimizer</td>
      <td colspan="1">
        <ul>
          <li>擷取至Experience Platform的資料事件和設定檔可供Journey Optimizer使用，以起始並支援Journey Optimizer中的歷程。</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>Journey Optimizer產生的互動和促銷活動資料會收集到Experience Platform中，以供透過即時客戶資料平台建立受眾，以及透過Customer Journey Analytics、Experience Platform查詢服務和資料科學工作區進行分析時進一步使用。</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/multi-channel-message-orchestration/triggered-messaging.html?lang=en">觸發訊息</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Magento</td>
      <td colspan="1">無當前整合</td>
      <td colspan="1">無當前整合</td>
      <td colspan="1">無當前整合</td>
    </tr>
    <tr>
      <td colspan="1">Marketo</td>
      <td colspan="1">
        <ul>
          <li>可在即時客戶資料平台中定義的對象可以與Marketo共用，作為對象，以啟動Marketo促銷活動和更新Marketo物件。</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>Marketo帳戶、連絡人和商機資料，以及Marketo所產生的互動和行銷活動資料，會匯入Experience Platform中，以便透過B2B-CDP建立受眾，以及透過Customer Journey Analytics、Experience Platform查詢服務和資料科學工作區進行分析時進一步使用。 <a href="https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo.html?lang=en">Marketo Engage連接器</a>
          </li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>B2B啟動 — 開發中</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Real-time CDP</td>
      <td colspan="1">
        <ul>
          <li>匯入和收集至Experience Platform的資料是匯整即時客戶設定檔的資料來源，為即時客戶資料平台提供支援。</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>「對象」和「設定檔」量度會傳送至「Experience Platform」資料湖，以支援「設定檔分析」報表控制面板。</li>
          <li>資料湖中的「對象」和「設定檔」資料可透過Query Service、Data Science Workspace和Customer Journey Analytics，用於進一步深入分析。</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/online-offline.html?lang=en">線上/離線對象啟用</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/platform-and-applications.html?lang=en">使用Experience Platform和應用程式啟動</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">目標</td>
      <td colspan="1">
        <ul>
          <li>可在即時客戶資料平台中定義的對象可共用至Target，並用於Target提供的個人化和鎖定體驗。 </li>
          <li>藍圖中會提供與Target的直接Experience Edge整合，以提供即時區段成員資格和設定檔屬性存取。</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>針對Target體驗和互動收集的資料可透過Experience PlatformWeb SDK收集以Experience Platform。 這些資料可用於透過即時客戶資料平台建立受眾，以及透過Customer Journey Analytics進行分析，  Experience Platform查詢服務與資料科學工作區。</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/online-offline.html?lang=en">線上/離線對象啟用</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/platform-and-applications.html?lang=en">使用Experience Platform和應用程式啟動</a>
          </li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>
