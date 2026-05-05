# Phase 1 Observations

## 1. Dataset Structure

The dataset contains **111,143 observations** and **6 variables**:

- **appID** (int64): Identifier for the application.
- **reviewerName** (object): Name of the reviewer.
- **reviewText** (object): Free-text user review.
- **reviewerRating** (float64): Rating given by the user (0.0 to 1.0 scale).
- **reviewDate** (object): Timestamp of the review.
- **textAnalytics** (float64): Sparse feature column with many missing values.

### Data Types
- Numerical: appID, reviewerRating, textAnalytics  
- Categorical/Text: reviewerName, reviewText, reviewDate  

---

## 2. Missing Values

- reviewerName: 5,303 missing values  
- textAnalytics: 110,656 missing values  
- Other columns: no missing values  

The `textAnalytics` column is largely incomplete and may not be useful without further processing.

---

## 3. Duplicate Records

- 160 duplicate records were identified in the dataset.

These duplicates should be handled during preprocessing to avoid bias.

---

## 4. Unique Value Analysis

- appID: 492 unique applications  
- reviewerName: 79,372 unique users  
- reviewText: 100,936 unique reviews  
- reviewerRating: 6 unique values  
- reviewDate: 6,104 unique timestamps  

This indicates a diverse dataset with many unique users and reviews.

---

## 5. Review Length Analysis

A new feature, `review_length`, was computed to measure the number of characters in each review.

- Mean length: ~114 characters  
- Median length: 80 characters  
- Minimum: 13 characters  
- Maximum: 2501 characters  

The distribution is right-skewed, indicating that most reviews are short, with some very long reviews.

---

## 6. Rating Distribution

- Mean rating: 0.83  
- Median rating: 1.0  
- 75th percentile: 1.0  

The ratings are heavily skewed toward higher values, indicating a strong class imbalance where most reviews are positive.

---

## 7. Baseline Pipeline Summary

The baseline Azure ML pipeline includes the following components:

- **Data Input**: App review dataset
- **Preprocessing**: Text preprocessing (lowercasing, stopword removal, normalization, etc.)
- **Train-Test Split**: 80% training, 20% testing
- **Model**: Linear Regression
- **Training**: Model trained using review text features
- **Scoring**: Predictions generated for test data
- **Evaluation (optional)**: Metrics such as RMSE, MAE, and R² can be used to assess performance

---

## 8. Limitations of the Baseline Pipeline

- The model is relatively simple (Linear Regression) and may not capture complex patterns in text data.
- The problem is treated as a regression task, which may not be the most appropriate formulation for rating prediction.
- The dataset exhibits class imbalance toward higher ratings, which may bias predictions.
- The `textAnalytics` feature contains excessive missing values and is not fully utilized.
- The baseline pipeline does not include advanced text feature extraction methods (e.g., TF-IDF, n-grams, embeddings).
- Limited handling of noisy or variable-length text inputs.

---

## 9. Key Takeaways

- The dataset is rich in text data but requires significant preprocessing.
- There is strong skewness in the rating distribution.
- Data quality issues such as missing values and duplicates must be addressed.
- The baseline model serves as a starting point but has clear limitations that motivate further experimentation and improvement.
## 10. Implications for Modeling

- Class imbalance may affect predictive performance, as the majority of ratings are skewed toward higher values (closer to 1.0). This may bias the model toward predicting positive outcomes.

- Text-based features such as `reviewText` will require preprocessing steps including tokenization, stopword removal, and vectorization (e.g., TF-IDF or embeddings).

- Review length may be a useful engineered feature, as longer or shorter reviews could correlate with sentiment or rating patterns.

- The problem formulation should be carefully considered:
  - Regression: predicting the numerical rating value.
  - Classification: converting ratings into categories (e.g., positive vs. negative sentiment).

Choosing the appropriate formulation will influence model selection, evaluation metrics, and preprocessing strategies.