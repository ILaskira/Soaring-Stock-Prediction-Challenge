# 🚀 Soaring Stock Prediction

本專案致力於建構一套能預測「潛在飆股（soaring stocks）」的機器學習系統，重點在於資料處理策略與模型設計。
📘 詳細資料處理與建模流程請見 🔗 [完整建模與分析流程（competition_details.md）](https://github.com/ILaskira/Soaring-Stock-Prediction-Challenge/blob/main/competition_details.md)

> ⚠️ **注意**：因應主辦單位規範，原始資料無法公開，以下僅說明技術流程與建模方法。
---

## 🔧 專案流程

### 1. 特徵工程與變數篩選
- 結合領域知識初步篩選出重要變數
- **運用多種變數選擇方法，從上萬個特徵中精選出 23 個關鍵變數**  
  相較於多數參賽者使用上百變數，我們以約**十分之一**的特徵達成相似甚至更佳的預測表現

### 2. 資料前處理
- 處理遺失值：採用 KNN 補值、中位數填補等策略
- 類別不平衡處理：使用 SMOTE、ADASYN 等重抽樣技術改善樣本比例失衡問題

### 3. 建模與調參
- 主模型：`XGBoost` / `LightGBM`
- 調參策略：Grid Search CV，同時設定正則化參數以降低過擬合風險

### 4. 模型融合與預測
- 採用 Stacking 方法進行多模型融合
- 根據預測機率與風險排序篩選潛在飆股

---

## ✅ 成果概述

我設計了一套具備高度策略性的資料處理與建模流程，具體特色如下：

- ⚙️ 多階段特徵選擇策略：結合 XGBoost 與 Permutation Importance，精準篩選具穩定預測力的變數
- 🔀 精簡模型 × 差集模型設計：建構變數兩兩互斥的多個模型，提升 Stacking 多樣性與效果
- 🧠 Stacking 融合策略：以簡潔的 meta-model（Logistic Regression）整合異質模型，強化整體表現
- 🔍 特徵完整性驗證：訓練反向模型驗證未選變數之預測貢獻，佐證特徵選擇具高度覆蓋率與解釋力

## 📊 最終成果
| Public Macro F1 | Private Macro F1 | Leaderboard 排名 |
|------------------|-------------------|-------------------|
| **0.8366**        | **0.8262**         | Top **3%**        |

> 🎯 模型整體兼顧效能、效率與解釋性，展現出良好的實務應用潛力。

🔗 [參賽證明（飆股比賽參賽證明）](https://github.com/ILaskira/Soaring-Stock-Prediction-Challenge/blob/main/%E9%A3%86%E8%82%A1%E6%AF%94%E8%B3%BD%E5%8F%83%E8%B3%BD%E8%AD%89%E6%98%8E.jpg)

---

## 📖 延伸閱讀與完整報告

更多技術細節、資料處理流程、模型設計邏輯與分析策略，請參考我們的完整技術說明文件：

🔗 [完整建模與分析流程（competition_details.md）](https://github.com/ILaskira/Soaring-Stock-Prediction-Challenge/blob/main/competition_details.md)

> 包含各階段實作邏輯、參數選擇依據、驗證策略與最終成效分析。

