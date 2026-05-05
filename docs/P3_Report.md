
# Phase 3 Cumulative Report: Construction & Evaluation  
**App Review Rating Prediction System**

---

## 1. Phase 3 Overview  

Phase 3 evaluated a sequence of increasingly expressive models to assess how different modeling approaches perform on app
review text when predicting numeric ratings. All models were trained and evaluated using consistent data splits and metrics, 
allowing for direct comparison. The progression from linear regression through tree‑based ensembles to gradient‑boosting methods was 
intentional, reflecting both increasing model capacity and alignment with the system’s architectural goals

---

## 2. Baseline Model  

### 2.1 Baseline Pipeline Structure  

The **Baseline Linear Regression model**, documented as Baseline and its variants (Baseline Stopwords = False and Baseline Stopwords = True), served as the foundational reference for all subsequent experiments. Despite basic text preprocessing and stopword removal, the model consistently produced negative R² values and high error metrics.
These results indicate that the relationship between review text and numeric ratings is highly non‑linear and poorly approximated by a linear model. Predictions tend to collapse toward the mean rating, a behavior reinforced by substantial class imbalance and the prevalence of very short reviews. While expected, this outcome was essential for establishing a meaningful performance floor and motivating more expressive approaches.

This configuration served as the reference point for all subsequent experiments.

### 2.2 Baseline Performance  

Across both baseline variants, performance was consistently weak:

- **R²:** approximately −0.03  
- **RMSE:** approximately 0.265  
- **MAE:** approximately 0.205

Negative R² values indicate that the model performs worse than predicting the mean rating. This behavior reflects strong class imbalance in the dataset and the prevalence of very short, low‑information reviews. Although expected, these results established a meaningful lower bound and motivated richer text representations and non‑linear models.

---

## 3. Pipeline‑Based Models  

### 3.1 Decision Forest Regression  

The **Decision Forest Regression model** introduced ensemble learning and nonlinear decision boundaries while maintaining the same manually constructed pipeline structure. Compared to the baseline, this model achieved modest improvements in R² and reduced RMSE and MAE values.
The results suggest that averaging across multiple trees allows the model to capture limited nonlinear interactions present in the data. However, performance gains were constrained. Without boosting or richer feature representations, the decision forest struggles to focus on difficult or high‑variance cases. This outcome demonstrates that algorithmic complexity alone is insufficient when the feature space remains limited.

- **R²:** ~0.065  
- **RMSE:** ~0.253  
- **MAE:** ~0.186

These results indicate that ensemble averaging captures limited non‑linear structure, but gains remained constrained due to limited feature representation.

### 3.2 Boosted Decision Tree Regression  

The **Boosted Decision Tree Regression model** extended the ensemble approach by applying boosting, allowing successive trees to correct prior errors. This resulted in incremental improvements over the decision forest, particularly in R².
Boosting proved beneficial, but improvements remained moderate. Like the decision forest, this model was constrained by the same preprocessing and feature pipeline. These results reinforce the importance of feature representation, showing that increasingly sophisticated algorithms cannot compensate indefinitely for limited input structure.

The Boosted Decision Tree Regression model further extended the ensemble approach by applying boosting, resulting in incremental improvements over the decision forest:

- **R²:** ~0.098  
- **RMSE:** ~0.248  
- **MAE:** ~0.194

Boosting improved performance slightly, but gains remained limited without richer text features.

---

## 4. Structured Text Representation  

### 4.1 Experiment 2: Explicit N‑Gram Feature Extraction  

A key turning point in Phase 3 occurred with the introduction of explicit unigram n‑gram feature extraction, documented under N‑Gram Structure, N‑Gram Params, and N‑Gram Metrics. By converting unstructured text into a consistent, high‑dimensional feature space, this experiment substantially improved performance even when paired with linear regression.
Error metrics decreased markedly, and R² increased to approximately 0.385. This outcome demonstrates that feature representation has a greater impact on performance than model choice alone in text‑heavy prediction tasks. The results validate the project’s architectural emphasis on preprocessing and pipeline design as first‑class system components.

- **R²:** ~0.385  
- **RMSE:** ~0.205  
- **MAE:** ~0.152

This experiment demonstrated that feature representation has a greater impact on performance than model choice alone for text‑driven tasks.

### 4.2 Experiment 3: Review Substance Filtering  

> **Experiment 3 evaluated the impact of filtering low‑substance reviews based on textual length. While Azure ML Designer does not support dynamic string‑length filtering within this pipeline, prior data analysis showed that very short reviews dominate the dataset and contribute limited semantic signal. In production, these reviews would be filtered prior to preprocessing to improve model stability and interpretability.**

Feature‑level constraints served as a practical proxy, highlighting the importance of system‑level design decisions when tooling imposes constraints.

---

## 5. AutoML‑Based Models  

### 5.1 XGBoost Regressor  

The **XGBoost model**, generated via Azure AutoML, incorporated significantly richer feature engineering than the pipeline‑based models. Automated processing included word‑ and character‑level TF‑IDF features, numeric imputation, categorical encoding, and feature scaling.
XGBoost produced a substantial improvement in predictive accuracy, achieving an R² near 0.39 with lower RMSE and MAE values. Diagnostic plots showed improved alignment between predicted and true values, along with more balanced residual distributions. These results demonstrate the effectiveness of gradient‑boosting methods when paired with automated, heterogeneous feature pipelines.

- **R²:** ~0.393  
- **RMSE:** ~0.207  
- **MAE:** ~0.144

These results confirm the value of gradient boosting combined with automated text and feature pipelines.

### 5.2 LightGBM Regressor  

The **LightGBM model** achieved the strongest overall performance among all evaluated models. With the same rich AutoML preprocessing applied in XGBoost, LightGBM’s leaf‑wise tree growth strategy enabled it to capture complex relationships in the sparse, high‑dimensional feature space more efficiently.
LightGBM achieved the lowest RMSE and MAE and the highest R², indicating superior generalization. While the performance improvement over XGBoost was incremental rather than dramatic, it was consistent across metrics. Given its efficiency, accuracy, and scalability, LightGBM represents the most suitable candidate for integration into the broader App Review Rating Prediction System.

- **R²:** ~0.454  
- **RMSE:** ~0.196  
- **MAE:** ~0.137

LightGBM’s efficiency in handling sparse, high‑dimensional features makes it the strongest candidate for system integration.

---

## 6. Comparative Results Summary  

Across all models, a clear performance hierarchy emerged:

1. Linear Regression established a weak but necessary baseline.
2. Tree‑based pipeline models captured limited nonlinearity but were constrained by feature representation.
3. Gradient‑boosted AutoML models delivered substantial improvements through combined feature engineering and advanced learning algorithms.

The most significant insight from Phase 3 is that feature representation dominates model selection for this task. Once text is properly structured, advanced models such as LightGBM can fully leverage the data. Conversely, even sophisticated algorithms underperform when paired with limited preprocessing.
Just as important, Phase 3 surfaced practical considerations—memory limitations, tooling constraints, and preprocessing tradeoffs—that shape real‑world system design. These findings reinforce the project’s emphasis on disciplined engineering decisions rather than purely metric‑driven optimization.

| Model | RMSE | R² | MAE | Notes |
|------|------|----|-----|------|
| Base Linear Regression | 0.2653 | −0.0319 | 0.2049 | Pipeline |
| Decision Forest | 0.2525 | 0.0653 | 0.1858 | Pipeline |
| Boosted Decision Tree | 0.2481 | 0.0976 | 0.1935 | Pipeline |
| XGBoost | 0.2066 | 0.3925 | 0.1442 | AutoML |
| **LightGBM** | **0.1958** | **0.4544** | **0.1366** | **AutoML** |

---

## 7. Overall Analysis and System Implications  

Phase 3 reveals a clear performance hierarchy. Linear models were inadequate for noisy, imbalanced text‑based regression. Tree‑based pipeline models offered incremental improvements, but gradient‑boosted AutoML models produced substantial gains by combining advanced feature engineering with expressive algorithms.

The dominant insight is that **feature representation outweighs algorithm selection** in text‑heavy systems. Once text is properly structured, advanced learners such as LightGBM can fully leverage the data. These findings reinforce the project’s emphasis on disciplined software engineering decisions over purely metric‑driven optimization.
