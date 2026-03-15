---
source-git-commit: a632042b3a7434dd88f52804e15e30fa06057e3b
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---
# Experience League Agent記憶體

## 此存放庫中的金鑰參考檔案- `/Users/nick/Library/CloudStorage/OneDrive-Adobe/Documents/GitHub/blueprints-learn.en/metadata.md` — 存放庫層級中繼資料預設值- `/Users/nick/Library/CloudStorage/OneDrive-Adobe/Documents/GitHub/blueprints-learn.en/help/blueprints/TOC.md` — 指南層級中繼資料- `/Users/nick/Library/CloudStorage/OneDrive-Adobe/Documents/GitHub/blueprints-learn.en/.cursor/skills/blueprint-document-reference/reference.md` — Blueprint製作模式

## 中繼資料規則（如需完整參考資訊，請參閱metadata-fields.md）- 需要文章內容： `title`、`description`、`exl-id`- 強烈建議使用文章標題： `solution`- `exl-id`必須為有效的UUID；複製檔案時請刪除/保留空白（由系統自動指派）- `description`應該以「瞭解如何……」開始 或「瞭解……」 依據Adobe准則- SEO最多`title`個~60個字元；標題中的產品名稱請使用`[!DNL ProductName]`- `solution`值區分大小寫，且必須符合核准的列舉（請參閱metadata-fields.md）- `thumbnail: null`或`thumbnail:` （空白）皆已使用；可接受空白- `kt:`是舊版欄位（知識文章JIRA號碼）；在此存放庫中仍可看到；可接受空白- 使用的目錄檔案： `user-guide-title`、`breadcrumb-title`、`user-guide-description`、`product`、`mini-toc-levels`、`role`- 存放庫層級`metadata.md`使用： `cloud`、`solution`、`product`、`type`、`doc-type`、`mini-toc-levels`、`git-repo`、`index`

## 此存放庫中的常見模式(blueprint-learn.en)- 大多數藍圖檔案有： `title`、`description`、`solution`、`exl-id`- 某些較舊的檔案也包含： `kt`、`thumbnail`- 某些檔案使用`version` （Campaign v8藍圖）- 總覽頁面使用`doc-type: overview-page`- `solution`通常包含多個逗號分隔值：例如`Real-Time Customer Data Platform, Campaign`- 如果存在`exl-id`，沒有`solution`的檔案仍會通過驗證

## 此存放庫中使用的Adobe Markdown擴充功能- `>[!NOTE]`, `>[!TIP]`, `>[!IMPORTANT]`, `>[!WARNING]`, `>[!CAUTION]`- 索引標籤內容的`>[!BEGINTABS]` / `>[!TAB Name]` / `>[!ENDTABS]`- `[!DNL ProductName]` — 不要將產品名稱的標籤本地化- `[!UICONTROL Label]` — UI控制項參考- `&lbrace;zoomable="yes"&rbrace;` — 影像縮放屬性- `&lbrace;width="1000"&rbrace;` — 影像寬度屬性- `&lbrace;target="_blank"&rbrace;` — 外部連結目標

## 詳細參考資料- 完整的中繼資料欄位參考： `metadata-fields.md`- 抓取撰寫指南：https://experienceleague.adobe.com/en/docs/authoring-guide-exl/using/home （2026年2月）
