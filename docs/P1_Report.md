# Phase 1 Cumulative Report – Inception
**App Review Rating Prediction System**  
DSC592 – Software Engineering for Data Science

---

## 1. Introduction & Problem Understanding

The company receives a large volume of free‑text app reviews that contain valuable feedback about application quality, usability, and performance. While a baseline machine learning system exists that predicts a numeric rating from review text, the current system provides limited insight into *why* users leave certain reviews and does not support actionable decision‑making.

Stakeholders expressed that existing outputs—such as average ratings—are insufficient. Reviews are treated uniformly regardless of content, system failures are not surfaced proactively, and the lack of a user‑friendly dashboard limits accessibility for non‑technical users. As a result, product teams and executives struggle to identify emerging issues, prioritize responses, and understand overall application health.

The goal of this project is to re‑engineer the existing system to provide interpretable, actionable insights from app reviews while following strong software engineering practices.

---

## 2. Stakeholders & Personas

The primary **users** of the system are internal Quality Analysts and Customer Success Analysts who regularly review user feedback. These users require detailed explanations, categorization of issues, and prioritization of meaningful reviews.

**Management and executive stakeholders**, including investors, rely on aggregated insights and dashboards to assess app performance, customer satisfaction, and risk trends.

To reflect these needs, the team defined three personas:

- **Management Persona** – Focused on strategic oversight, dashboards, scalability, and fairness.
- **User Persona** – Focused on day‑to‑day review analysis, categorization, prioritization, and explainability.
- **Technical Persona** – Focused on system reliability, data quality, modeling, and maintainability.

These personas directly informed the system requirements described below.

---

## 3. Vision & Success Criteria

The vision for the enhanced app review system is to move beyond simple rating prediction toward an **interpretable analytics platform** that enables proactive decision‑making.

The system should:
- Transform raw, unstructured reviews into categorized and prioritized insights
- Help customer‑facing teams identify potential issues before negative reviews escalate
- Provide management with clear, trustworthy dashboards
- Ensure transparency and fairness in how reviews are flagged or categorized

Success will be measured by:
- Improved usability for non‑technical users
- The system’s ability to accurately categorize and prioritize reviews
- Stakeholder confidence in system explanations and outputs
- Reliable, automated processing of new reviews

---

## 4. Early System Requirements (Summary)

Based on stakeholder interviews, dataset analysis, and persona needs, the team identified early functional and non‑functional requirements.

### Functional Requirements
- Ingest and process app reviews containing free‑text and ratings
- Automatically refresh and process new reviews on a nightly schedule
- Clean and preprocess review text to handle duplication and noise
- Categorize reviews into meaningful issue groups
- Identify sentiment and prioritize actionable reviews
- Provide predictive indicators linked to system issues
- Present insights through a filterable dashboard
- Explain why reviews are categorized or flagged
- Restrict access to internal users via authentication

### Non‑Functional Requirements
- Interpretability and explainability of outputs
- Acceptable performance for nightly processing
- Modular and maintainable system design
- Scalability to support additional apps and reviews
- Fairness toward developers in review flagging
- Usability for non‑data users
- Reliability and data consistency across refresh cycles

Each requirement was prioritized using a MoSCoW approach (Must / Should / Could) and explicitly traced to the team personas to ensure alignment with stakeholder needs.

---

## 5. Phase 1 Outcomes & Next Steps

Phase 1 established a clear understanding of the problem space, stakeholders, and system expectations. The resulting personas and early requirements create a foundation for architectural design and technical planning.

In Phase 2, the team will:
- Translate requirements into system architecture
- Define component and context diagrams
- Identify technical risks and mitigation strategies
- Plan iterations for experimentation and implementation

This phased approach ensures that technical decisions remain grounded in stakeholder needs and software engineering best practices.
