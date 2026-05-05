# Phase 2 Cumulative Report: Elaboration & Planning
**App Review Rating Prediction System**

---

## 1. Phase 2 Overview

Phase 2 focuses on translating the problem understanding and requirements established during Phase 1 into a concrete system design and execution strategy. The primary goals of this phase are to define the system architecture, establish traceability between requirements and success criteria, identify key risks, and plan iterative development. Rather than implementing solutions prematurely, this phase emphasizes thoughtful design decisions that support maintainability, interpretability, and stakeholder alignment.

The outputs of Phase 2 include a system context diagram (Figure 1), a component diagram (Figure 2), a success criteria matrix, a finalized risk register, and an iteration plan that guides future construction and experimentation.

---

## 2. System Context Diagram

The system context diagram (Figure 1) defines the App Review Rating Prediction System as a bounded system and illustrates its interactions with external users and services. At this level, the system is treated as a black box, with the focus placed on data flows and stakeholder interactions rather than internal implementation details.

The system ingests raw app reviews, ratings, and metadata from an external app review dataset. These data serve as the primary input for analytics and modeling. The system integrates with Azure Machine Learning, which is used to execute model training, scoring, and evaluation tasks. Predictions, metrics, and model outputs are returned to the system for downstream processing and presentation.

Two primary user groups interact with the system. Quality Analysts and Customer Success Analysts access dashboards and analytics tools to investigate reviews, identify emerging issues, and prioritize responses. Management and executive stakeholders consume higher‑level aggregated reports summarizing application performance, sentiment trends, and potential risks.

A conceptual feedback loop from the system back to Azure Machine Learning is included in the context diagram. This loop represents periodic model retraining and refinement using accumulated historical data and prior outcomes. Importantly, this feedback loop reflects an iterative learning process rather than a specific automated mechanism.

---

## 3. Component Diagram and Internal Responsibilities

While the context diagram establishes system boundaries, the component diagram (Figure 2) decomposes the system into major internal responsibilities and data flows. This diagram provides a shared architectural understanding while remaining at an appropriate level of abstraction for early design.

Key components identified include data ingestion and organization, preprocessing and cleaning, labeling and feature generation, the machine learning pipeline, data storage, dashboard and visualization, and authentication and access control. Data ingestion is responsible for collecting raw reviews and organizing them based on content relevance, including prioritizing reviews with substantive text. Preprocessing and cleaning address normalization, deduplication, and preparation of text data for modeling.

The machine learning pipeline, implemented using Azure ML, handles model training and scoring. Outputs from the pipeline feed into labeling and analytics logic that supports sentiment detection, issue categorization, and prioritization. Processed data and model outputs are stored for reporting, reproducibility, and potential future retraining. User‑facing dashboards present results in an interpretable manner to non‑technical users, while authentication mechanisms restrict system access to internal users.

---

## 4. Success Criteria and Requirements Traceability

To ensure that architectural decisions remain anchored to stakeholder needs, the team developed a Success Criteria Matrix that maps requirements to observable, testable outcomes. Each success criterion specifies how a requirement can be validated through system behavior and identifies the relevant stakeholder group.

The matrix covers functional requirements such as review ingestion, preprocessing, categorization, sentiment identification, dashboard visualization, and access control. It also addresses non‑functional requirements including interpretability, usability, performance, reliability, maintainability, scalability, and fairness. During Phase 2, this matrix serves as a design constraint rather than a testing checklist, ensuring architectural choices support meaningful evaluation in later phases.

---

## 5. Risk Analysis and Mitigation

A formal risk register was developed to identify and manage uncertainty across technical, data‑related, and organizational dimensions. Key machine learning risks include class imbalance in ratings, poor text quality, uncertainty in problem formulation, and interpretability challenges associated with complex models. Technical risks include missing data, duplicate records, and authentication complexity. Organizational risks include limited project time, requirement miscommunication, and underestimation of dashboard development effort.

Each risk is assessed in terms of likelihood and impact, with a mitigation strategy defined. These mitigations directly influence architectural and iteration‑planning decisions. By explicitly documenting risks during Phase 2, the team reduces the likelihood of unanticipated issues during construction.

---

## 6. Iteration Planning

Phase 2 concludes with a two‑iteration plan that defines how the system will evolve in subsequent phases.

Iteration 1 focuses on foundation and understanding. Its goals include reproducing the baseline Azure ML pipeline, validating data quality assumptions, finalizing context and component diagrams, defining evaluation metrics, and identifying key risks. This iteration prioritizes clarity, reproducibility, and shared understanding over performance improvement.

Iteration 2 focuses on purposeful experimentation and system evolution. Goals include evaluating alternative problem formulations, experimenting with text preprocessing strategies, exploring feature engineering opportunities, comparing model families, developing initial review categorization logic, and refining the architecture based on experimental findings.

---

## 7. Phase 2 Outcomes

By the end of Phase 2, the team has established a coherent system architecture, defined measurable success criteria, identified and mitigated key risks, and developed a clear iteration plan. These outcomes provide a strong foundation for Phase 3 construction and experimentation, ensuring future work remains aligned with stakeholder needs, architectural reasoning, and documented assumptions.
