---
source-git-commit: ef1c207922c1079117d8bd255dbfa32a1527b014
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 100%

---
# 使用案例目錄列範本

## 列格式

使用案例目錄表格中的每一列都遵循此確切格式：

```
| <img src="assets/use-case-icons/{industry}/icon-{kebab-name}.png" alt="{Alt Text}" width="40"> | [{Use Case Title}]({industry}/{industry}-overview.md#{heading-anchor}) | {One-sentence description} | [!BADGE {Maturity}]{type={Type}} | [{Pattern Name}](/help/blueprints/use-case-patterns/{category}/{pattern-file}.md) |
```

### 沒有圖示的列（尚未提供圖示時使用）

```
| | [{Use Case Title}]({industry}/{industry}-overview.md#{heading-anchor}) | {One-sentence description} | [!BADGE {Maturity}]{type={Type}} | [{Pattern Name}](/help/blueprints/use-case-patterns/{category}/{pattern-file}.md) |
```

## 欄位參考

| 欄位 | 格式 | 範例 |
| --- | --- | --- |
| industry | kebab-case目錄名稱 | 零售、金融服務、旅遊、旅館業 |
| kebab-name | 圖示的kebab-case使用案例名稱 | 捨棄的購物車、潛在客戶培養 |
| 替代文字 | 字首大寫，短 | 捨棄的購物車，銷售機會培養 |
| heading-anchor | 總覽中##標題的串音大小寫 | abandred-cart-email-recovery |
| 成熟度+型別 | 徽章語法 | `[!BADGE Foundational]{type=Neutral}`, `[!BADGE Emerging]{type=Informative}`, `[!BADGE Advanced]{type=Caution}` |

## 目錄中的產業標籤標籤

目錄檔案使用此索引標籤結構：

- `>[!TAB Retail]`
- `>[!TAB Automotive]`
- `>[!TAB Financial Services]`
- `>[!TAB Healthcare]`
- `>[!TAB Insurance]`
- `>[!TAB Media & Entertainment]`
- `>[!TAB Telecommunications]`
- `>[!TAB Travel & Hospitality]`
- `>[!TAB B2B]`

## 在索引標籤中排序

列會依成熟度層級排序：

1. **Foundation**&#x200B;資料列優先（型別=中性）
2. **新增**&#x200B;資料列（型別=資訊）
3. **進階**&#x200B;列最後（型別=警告）

在同一成熟度層級內，在該群組的結尾新增列。
