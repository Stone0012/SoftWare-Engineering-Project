# Cumulative Project Report
### App Review Rating Prediction System
**DSC592 – Software Engineering for Data Science**

Phases 1 · 2 · 3 · 4

---

## Phase 1: Inception

### 1. Introduction & Problem Understanding

The company receives a large volume of free-text app reviews that contain valuable feedback about application quality, usability, and performance. While a baseline machine learning system exists that predicts a numeric rating from review text, the current system provides limited insight into *why* users leave certain reviews and does not support actionable decision-making.

Stakeholders expressed that existing outputs—such as average ratings—are insufficient. Reviews are treated uniformly regardless of content, system failures are not surfaced proactively, and the lack of a user-friendly dashboard limits accessibility for non-technical users. As a result, product teams and executives struggle to identify emerging issues, prioritize responses, and understand overall application health.

The goal of this project is to re-engineer the existing system to provide interpretable, actionable insights from app reviews while following strong software engineering practices.

### 2. Stakeholders & Personas

The primary users of the system are internal Quality Analysts and Customer Success Analysts who regularly review user feedback. These users require detailed explanations, categorization of issues, and prioritization of meaningful reviews.

Management and executive stakeholders, including investors, rely on aggregated insights and dashboards to assess app performance, customer satisfaction, and risk trends.

To reflect these needs, the team defined three personas:

- **Management Persona** – Focused on strategic oversight, dashboards, scalability, and fairness.
- **User Persona** – Focused on day-to-day review analysis, categorization, prioritization, and explainability.
- **Technical Persona** – Focused on system reliability, data quality, modeling, and maintainability.

These personas directly informed the system requirements described below.

### 3. Vision & Success Criteria

The vision for the enhanced app review system is to move beyond simple rating prediction toward an **interpretable analytics platform** that enables proactive decision-making.

The system should:

- Transform raw, unstructured reviews into categorized and prioritized insights
- Help customer-facing teams identify potential issues before negative reviews escalate
- Provide management with clear, trustworthy dashboards
- Ensure transparency and fairness in how reviews are flagged or categorized

Success will be measured by improved usability for non-technical users, the system's ability to accurately categorize and prioritize reviews, stakeholder confidence in system explanations and outputs, and reliable automated processing of new reviews.

### 4. Early System Requirements

Based on stakeholder interviews, dataset analysis, and persona needs, the team identified early functional and non-functional requirements. Each requirement was prioritized using a MoSCoW approach (Must / Should / Could) and explicitly traced to team personas to ensure alignment with stakeholder needs.

#### Functional Requirements

- Ingest and process app reviews containing free-text and ratings
- Automatically refresh and process new reviews on a nightly schedule
- Clean and preprocess review text to handle duplication and noise
- Categorize reviews into meaningful issue groups
- Identify sentiment and prioritize actionable reviews
- Provide predictive indicators linked to system issues
- Present insights through a filterable dashboard
- Explain why reviews are categorized or flagged
- Restrict access to internal users via authentication

#### Non-Functional Requirements

- Interpretability and explainability of outputs
- Acceptable performance for nightly processing
- Modular and maintainable system design
- Scalability to support additional apps and reviews
- Fairness toward developers in review flagging
- Usability for non-data users
- Reliability and data consistency across refresh cycles

### 5. Phase 1 Outcomes & Next Steps

Phase 1 established a clear understanding of the problem space, stakeholders, and system expectations. The resulting personas and early requirements created a foundation for architectural design and technical planning.

In Phase 2, the team translated requirements into system architecture, defined component and context diagrams, identified technical risks and mitigation strategies, and planned iterations for experimentation and implementation. This phased approach ensures that technical decisions remain grounded in stakeholder needs and software engineering best practices.

---

## Phase 2: Elaboration & Planning

### 1. Phase 2 Overview

Phase 2 focused on translating the problem understanding and requirements established during Phase 1 into a concrete system design and execution strategy. The primary goals were to define the system architecture, establish traceability between requirements and success criteria, identify key risks, and plan iterative development. Rather than implementing solutions prematurely, this phase emphasized thoughtful design decisions that support maintainability, interpretability, and stakeholder alignment.

The outputs of Phase 2 include a system context diagram, a component diagram, a success criteria matrix, a finalized risk register, and an iteration plan that guides future construction and experimentation.

### 2. System Context Diagram

The system context diagram defines the App Review Rating Prediction System as a bounded system and illustrates its interactions with external users and services. At this level, the system is treated as a black box, with focus placed on data flows and stakeholder interactions rather than internal implementation details.

The system ingests raw app reviews, ratings, and metadata from an external dataset. These data serve as the primary input for analytics and modeling. The system integrates with Azure Machine Learning, which executes model training, scoring, and evaluation tasks. Two primary user groups interact with the system: Quality and Customer Success Analysts accessing dashboards, and Management stakeholders consuming aggregated performance reports.

A conceptual feedback loop from the system back to Azure Machine Learning is included in the context diagram, representing periodic model retraining and refinement using accumulated historical data. This loop reflects an iterative learning process rather than a specific automated mechanism.

### 3. Component Diagram and Internal Responsibilities

The component diagram decomposes the system into major internal responsibilities and data flows, providing a shared architectural understanding while remaining at an appropriate level of abstraction for early design. Key components identified include:

- **Data Ingestion & Organization** – Collecting raw reviews and prioritizing those with substantive text
- **Preprocessing & Cleaning** – Normalization, deduplication, and preparation of text for modeling
- **Machine Learning Pipeline** – Model training and scoring via Azure ML
- **Labeling & Analytics Logic** – Sentiment detection, issue categorization, and prioritization
- **Data Storage** – Processed data and model outputs for reporting and reproducibility
- **Dashboard & Visualization** – Interpretable results presented to non-technical users
- **Authentication & Access Control** – Restricting system access to internal users

### 4. Success Criteria and Requirements Traceability

To ensure that architectural decisions remain anchored to stakeholder needs, the team developed a Success Criteria Matrix that maps requirements to observable, testable outcomes. Each success criterion specifies how a requirement can be validated through system behavior and identifies the relevant stakeholder group.

The matrix covers both functional requirements (review ingestion, preprocessing, categorization, sentiment identification, dashboard visualization, and access control) and non-functional requirements (interpretability, usability, performance, reliability, maintainability, scalability, and fairness). During Phase 2, this matrix served as a design constraint rather than a testing checklist, ensuring architectural choices support meaningful evaluation in later phases.

### 5. Risk Analysis and Mitigation

A formal risk register was developed to identify and manage uncertainty across technical, data-related, and organizational dimensions. Key risk categories include:

- **Machine Learning Risks** – Class imbalance in ratings, poor text quality, uncertainty in problem formulation, and interpretability challenges with complex models
- **Technical Risks** – Missing data, duplicate records, and authentication complexity
- **Organizational Risks** – Limited project time, requirement miscommunication, and underestimation of dashboard development effort

Each risk is assessed in terms of likelihood and impact, with a mitigation strategy defined. By explicitly documenting risks during Phase 2, the team reduces the likelihood of unanticipated issues during construction.

### 6. Iteration Planning

Phase 2 concluded with a two-iteration plan that defines how the system evolves in subsequent phases.

#### Iteration 1 – Foundation & Understanding

Goals include reproducing the baseline Azure ML pipeline, validating data quality assumptions, finalizing context and component diagrams, defining evaluation metrics, and identifying key risks. This iteration prioritizes clarity, reproducibility, and shared understanding over performance improvement.

#### Iteration 2 – Purposeful Experimentation & System Evolution

Goals include evaluating alternative problem formulations, experimenting with text preprocessing strategies, exploring feature engineering opportunities, comparing model families, developing initial review categorization logic, and refining the architecture based on experimental findings.

### 7. Phase 2 Outcomes

By the end of Phase 2, the team established a coherent system architecture, defined measurable success criteria, identified and mitigated key risks, and developed a clear iteration plan. These outcomes provide a strong foundation for Phase 3 construction and experimentation, ensuring future work remains aligned with stakeholder needs, architectural reasoning, and documented assumptions.

---

## Phase 3: Construction & Evaluation

### 1. Phase 3 Overview

Phase 3 evaluated a sequence of increasingly expressive models to assess how different modeling approaches perform on app review text when predicting numeric ratings. All models were trained and evaluated using consistent data splits and metrics, allowing for direct comparison. The progression from linear regression through tree-based ensembles to gradient-boosting methods was intentional, reflecting both increasing model capacity and alignment with the system's architectural goals.

### 2. Baseline Model

#### 2.1 Baseline Pipeline Structure

The Baseline Linear Regression model served as the foundational reference for all subsequent experiments. Despite basic text preprocessing and stopword removal, the model consistently produced negative R² values and high error metrics. These results indicate that the relationship between review text and numeric ratings is highly non-linear and poorly approximated by a linear model. Predictions tend to collapse toward the mean rating, a behavior reinforced by substantial class imbalance and the prevalence of very short reviews. While expected, this outcome was essential for establishing a meaningful performance floor and motivating more expressive approaches.

#### 2.2 Baseline Performance

Across both baseline variants, performance was consistently weak:

- R²: approximately −0.03
- RMSE: approximately 0.265
- MAE: approximately 0.205

Negative R² values indicate that the model performs worse than predicting the mean rating, reflecting strong class imbalance and the prevalence of very short, low-information reviews. These results established a meaningful lower bound and motivated richer text representations and non-linear models.

### 3. Pipeline-Based Models

#### 3.1 Decision Forest Regression

The Decision Forest Regression model introduced ensemble learning and nonlinear decision boundaries while maintaining the same manually constructed pipeline structure. Compared to the baseline, this model achieved modest improvements, suggesting that averaging across multiple trees captures limited nonlinear interactions. However, without boosting or richer feature representations, performance gains were constrained.

- R²: ~0.065
- RMSE: ~0.253
- MAE: ~0.186

#### 3.2 Boosted Decision Tree Regression

The Boosted Decision Tree Regression model extended the ensemble approach by applying boosting, allowing successive trees to correct prior errors. This resulted in incremental improvements over the decision forest, particularly in R². These results reinforce the importance of feature representation, showing that increasingly sophisticated algorithms cannot compensate indefinitely for limited input structure.

- R²: ~0.098
- RMSE: ~0.248
- MAE: ~0.194

### 4. Structured Text Representation

#### 4.1 Experiment 2: Explicit N-Gram Feature Extraction

A key turning point in Phase 3 occurred with the introduction of explicit unigram n-gram feature extraction. By converting unstructured text into a consistent, high-dimensional feature space, this experiment substantially improved performance even when paired with linear regression. Error metrics decreased markedly, and R² increased to approximately 0.385. This outcome demonstrates that feature representation has a greater impact on performance than model choice alone in text-heavy prediction tasks, validating the project's architectural emphasis on preprocessing and pipeline design as first-class system components.

- R²: ~0.385
- RMSE: ~0.205
- MAE: ~0.152

#### 4.2 Experiment 3: Review Substance Filtering

Experiment 3 evaluated the impact of filtering low-substance reviews based on textual length. While Azure ML Designer does not support dynamic string-length filtering within this pipeline, prior data analysis showed that very short reviews dominate the dataset and contribute limited semantic signal. In production, these reviews would be filtered prior to preprocessing to improve model stability and interpretability. Feature-level constraints served as a practical proxy, highlighting the importance of system-level design decisions when tooling imposes constraints.

### 5. AutoML-Based Models

#### 5.1 XGBoost Regressor

The XGBoost model, generated via Azure AutoML, incorporated significantly richer feature engineering than the pipeline-based models. Automated processing included word- and character-level TF-IDF features, numeric imputation, categorical encoding, and feature scaling. XGBoost produced a substantial improvement in predictive accuracy, with diagnostic plots showing improved alignment between predicted and true values and more balanced residual distributions.

- R²: ~0.393
- RMSE: ~0.207
- MAE: ~0.144

#### 5.2 LightGBM Regressor

The LightGBM model achieved the strongest overall performance among all evaluated models. With the same rich AutoML preprocessing applied in XGBoost, LightGBM's leaf-wise tree growth strategy enabled it to capture complex relationships in the sparse, high-dimensional feature space more efficiently. While the performance improvement over XGBoost was incremental rather than dramatic, it was consistent across all metrics. Given its efficiency, accuracy, and scalability, LightGBM represents the most suitable candidate for integration into the broader system.

- R²: ~0.454
- RMSE: ~0.196
- MAE: ~0.137

### 6. Comparative Results Summary

| Model | RMSE | R² | MAE | Type |
|---|---|---|---|---|
| Base Linear Regression | 0.2653 | −0.0319 | 0.2049 | Pipeline |
| Decision Forest | 0.2525 | 0.0653 | 0.1858 | Pipeline |
| Boosted Decision Tree | 0.2481 | 0.0976 | 0.1935 | Pipeline |
| XGBoost | 0.2066 | 0.3925 | 0.1442 | AutoML |
| **LightGBM** | **0.1958** | **0.4544** | **0.1366** | **AutoML** |

### 7. Overall Analysis and System Implications

Phase 3 reveals a clear performance hierarchy. Linear models were inadequate for noisy, imbalanced text-based regression. Tree-based pipeline models offered incremental improvements, but gradient-boosted AutoML models produced substantial gains by combining advanced feature engineering with expressive algorithms.

The dominant insight is that **feature representation outweighs algorithm selection** in text-heavy systems. Once text is properly structured, advanced learners such as LightGBM can fully leverage the data. Phase 3 also surfaced practical considerations—memory limitations, tooling constraints, and preprocessing tradeoffs—that shape real-world system design. These findings reinforce the project's emphasis on disciplined engineering decisions over purely metric-driven optimization. With a clear performance winner identified and the experimental work complete, the project was ready to transition into Phase 4: stabilization, documentation, and delivery.

---

## Phase 4: Transition & Delivery

### 1. Phase 4 Overview

Phase 4 focused on transitioning the system from an experimental machine learning effort into a stable, well-documented deliverable suitable for evaluation and handoff. Rather than pursuing further performance gains, this phase emphasized **stabilization, communication, and reflection** — translating the iterative work of prior phases into a coherent, professional-grade system.

### 2. Final Model Selection

Based on the comparative evaluation results from Phase 3, the **LightGBM AutoML model** was selected as the final model. Its superiority was consistent across all key metrics — achieving the lowest RMSE (0.1958) and MAE (0.1366) and the highest R² (0.4544) — and its leaf-wise tree growth strategy proved particularly well-suited to the high-dimensional, sparse feature space produced by automated text preprocessing.

Model selection was justified not only on predictive performance but also on broader system considerations: LightGBM's efficiency and scalability make it a practical choice for nightly batch processing, and its compatibility with Azure AutoML's feature pipeline supports long-term maintainability. The final model was registered in Azure ML with associated metadata, metrics, and run identifiers to ensure reproducibility.

### 3. Project Webpage

The project webpage was finalized to communicate the system's purpose, architecture, experimentation process, and results to an external audience. All metrics displayed were validated against Azure ML outputs to ensure consistency with the technical report. The webpage serves as an accessible, high-level summary of the project for stakeholders who may not engage with the full documentation — bridging the gap between technical depth and broader communicability.

### 4. Cumulative Final Report

This report was completed by integrating Phases 1 through 4 into a single, cohesive narrative. Earlier phase documents were refined to eliminate redundancy, clarify design decisions, and reflect lessons learned during experimentation. Architecture diagrams were retained without structural revision, with Phase 3 modeling changes documented as implementation-level variations rather than architectural ones — preserving the integrity of the original design while accurately representing how the system evolved in practice.

### 5. Team Presentation

A team presentation was prepared to summarize the project in a concise, structured format across 10–12 minutes. The presentation emphasized problem context, system design, iterative experimentation, key challenges, and final outcomes. Content was organized to align with professional communication expectations, prioritizing clarity and narrative flow over exhaustive technical detail.

### 6. Phase 4 Outcomes

By the conclusion of Phase 4, the project achieved its primary goal: delivering a well-engineered, end-to-end data science system supported by clear documentation, validated results, and reflective analysis. The work across all four phases demonstrates how a machine learning system evolves through structured planning, disciplined experimentation, and intentional transition — from an underspecified baseline to a deployable, interpretable, and stakeholder-aligned platform.
