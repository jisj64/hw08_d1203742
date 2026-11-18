# 聚餐費用分攤與預算判斷

本專案使用 Python 計算聚餐的服務費、折價後應付總額，以及每人平均分攤金額，並判斷是否超過設定的個人預算。程式收錄於 Jupyter Notebook，共有三組不同人數與折扣的測試情境。

## 功能說明

- 使用 `strip()` 和 `lower()` 清理聚餐名稱。
- 移除餐費字串中的 `NT$`、千分位逗號與空白，再轉換成數值。
- 將人數字串轉換為整數。
- 依原始餐費計算服務費，扣除折價券後取得應付總額。
- 計算每人平均費用，並以布林值判斷是否超出預算。
- 將金額以小數點後兩位格式輸出。

## 使用環境

- Python 3
- Jupyter Notebook（執行 `.ipynb` 檔案）
- 不需安裝額外的第三方 Python 套件

## 計算公式

```python
service_fee = meal_value * service_rate
total_amount = meal_value + service_fee - discount
amount_per_person = total_amount / people_count
is_over_budget = amount_per_person > budget_per_person
```

> 當每人費用**等於**預算時，`is_over_budget` 為 `False`；只有嚴格大於預算時才為 `True`。

## 測試情境與結果

三組程式皆使用原始餐費 NT$1,200、服務費率 10%、每人預算 NT$300，差異如下：

| 項目 | 情境一 | 情境二 | 情境三 |
| --- | ---: | ---: | ---: |
| 聚餐名稱（清理後） | weekend dinner | weekend dinner | weekend dinner |
| 原始餐費 | NT$1,200 | NT$1,200 | NT$1,200 |
| 服務費 | NT$120 | NT$120 | NT$120 |
| 折價券 | NT$220 | NT$100 | NT$100 |
| 應付總額 | NT$1,100 | NT$1,220 | NT$1,220 |
| 分攤人數 | 4 人 | 5 人 | 4 人 |
| 每人費用 | NT$275 | NT$244 | NT$305 |
| 每人預算 | NT$300 | NT$300 | NT$300 |
| 是否超過預算 | `False` | `False` | `True` |

## 執行方式

1. 使用 Jupyter Notebook 或支援 `.ipynb` 的編輯器開啟專案 Notebook。
2. 依序執行三個程式碼儲存格，觀察各情境的計算結果。
3. 如需測試其他聚餐條件，可修改各儲存格開頭的參數：

```python
event_name = "  WEEKEND DINNER  "
meal_amount = " NT$1,200 "
people = "4"
service_rate = 0.10
discount = 220
budget_per_person = 300
```

## 輸出範例

以下為情境一的輸出：

```text
聚餐名稱：weekend dinner
原始餐費：1200.00 元
服務費：120.00 元
折價券：220.00 元
應付總額：1100.00 元
分攤人數：4 人
每人費用：275.00 元
每人預算：300.00 元
是否超過預算：False
```

## 注意事項

- 目前的餐費清理方式預期輸入包含 `NT$`、逗號及空白；其他幣別格式未另外處理。
- 程式假設人數為正整數，未加入零人數或無效輸入的例外處理。
- 三個儲存格是獨立的測試情境，並非需要依序傳遞資料的流程。
