# Risk Register

| ID | Risk Description | Type | Likelihood | Impact | Mitigation Strategy |
|----|----------------|------|------------|--------|---------------------|
| R1 | Imbalanced rating distribution may bias the model toward high ratings | ML | High | High | Use resampling techniques or alternative evaluation metrics (e.g., F1-score) |
| R2 | Poor text quality (typos, slang, noise) may reduce model performance | ML | High | Medium | Apply text preprocessing (cleaning, normalization, tokenization) |
| R3 | Missing values in dataset (e.g., reviewerName, textAnalytics) | Technical | Medium | Medium | Drop or impute missing values; ignore low-value columns like textAnalytics |
| R4 | Duplicate records affecting training quality | Technical | Medium | Medium | Remove duplicates during preprocessing |
| R5 | Baseline model (linear regression) may be too simple for text data | ML | High | High | Experiment with more advanced models (e.g., classification models, TF-IDF, embeddings) |
| R6 | Lack of external data (e.g., system logs) limits advanced features such as outage prediction | ML | High | Medium | Clearly define scope; simulate or document as future work |
| R7 | Miscommunication of requirements with stakeholders | Organizational | Medium | High | Regular team discussions and clear documentation of requirements |
| R8 | Limited time to implement all planned features | Organizational | High | High | Prioritize core features; focus on incremental improvements |
| R9 | Uncertainty in problem formulation (regression vs classification) may lead to suboptimal model choice | ML | Medium | High | Experiment with both approaches and compare performance using appropriate metrics |
| R10 | SSO/authentication implementation fails or is delayed, leaving the system without access control | Technical | Medium | High | Treat FR-10 as a Must from day one; prototype authentication early and decouple it from other features so delays don't block the rest of development |
| R11 | Dashboard and visualization work (FR-08) underestimated, causing delivery delays on a universally critical feature | Organizational | Medium | High | Allocate dedicated frontend effort early; use an existing charting library (e.g., Plotly, Streamlit) to reduce build time rather than building from scratch |
| R12 | Complex models (embeddings, neural approaches) produce black-box outputs that cannot be explained to non-technical users, violating NFR-01 | ML | High | High | Prefer interpretable models (TF-IDF + logistic regression) where possible; supplement with SHAP or LIME explanations; include explanation quality as an evaluation criterion alongside accuracy |