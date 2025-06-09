# 📝 比賽技術細節報告 | Soaring Stock Prediction

## 1. 賽題簡介
本比賽旨在預測潛在飆股（隔日可能大幅上漲），屬於非平衡分類問題。

## 2. 資料特性與前處理
- 多為數值型技術指標與籌碼面特徵
- 使用中位數、KNN 補值處理缺失值
- 樣本極度不平衡（標記為 1 者 < 5%）

## 3. 特徵選擇策略
- 先以領域知識排除明顯無關變數
- XGBoost importance 排序 + permutation importance
- 移除共線性高的變數（|ρ| > 0.9）

## 4. 模型設計與融合
- 主模型：XGBoost / LightGBM / CatBoost
- 使用 GridSearchCV 對正則化與深度等參數調整
- Stacking 融合（元模型為 Logistic 回歸）

## 5. 評估與 leaderboard 結果
| 模型 | 特徵數 | Macro F1 | Leaderboard |
|------|--------|----------|-------------|
| 精簡模型 | 23     | 0.73     | Top 6%      |
| 融合模型 | all + stacking | 0.76 | Top 3%      |

## 6. 分析與反思
- 精簡特徵反而提升穩定性與泛化能力
- 再平衡處理改善 recall，但可能降低 precision
- 可延伸為回歸問題或結合時間窗做持股建議

> 📌 本檔案僅記錄技術流程，資料內容因比賽規範不予公開。

