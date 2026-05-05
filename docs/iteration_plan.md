# Iteration Planning – Phase 2

This document outlines the planned iterations for Phase 2 of the App Review Rating Prediction System project. Each iteration is defined by a clear objective and a set of high-level goals that guide development without prescribing specific task-level assignments.

---

## Iteration 1: Foundation and Baseline Understanding

### Iteration 1 Objective
The primary objective of Iteration 1 is to establish a stable and well-understood foundation for the system. This iteration focuses on understanding the existing baseline, validating assumptions about the data and pipeline, and finalizing architectural artifacts before beginning major experimentation.

Rather than attempting to improve model performance, this iteration emphasizes clarity, reproducibility, and shared understanding across the team.

### Iteration 1 Goals

- Reproduce and validate the baseline Azure ML pipeline to ensure expected outputs, metrics, and limitations are clearly understood.
- Confirm data quality characteristics and preprocessing needs, including missing values, duplicate records, and class imbalance.
- Finalize the system context diagram, including system boundaries, external actors, and the conceptual feedback loop.
- Finalize the system component diagram at an appropriate level of abstraction.
- Define evaluation criteria and success metrics aligned with stakeholder needs and system goals.
- Identify and document key technical, data, and process risks along with mitigation strategies.

### Iteration 1 Expected Outcome
By the conclusion of Iteration 1, the team will have a shared and documented understanding of the baseline system, the dataset, and the proposed architecture. This foundation ensures that subsequent experimentation is intentional and traceable.

---

## Iteration 2: Purposeful Experimentation and System Evolution

### Iteration 2 Objective
The objective of Iteration 2 is to evolve the system beyond the baseline through controlled and well-documented experimentation. This iteration focuses on learning which modeling approaches, preprocessing strategies, and problem formulations best support the system’s goals.

Iteration 2 emphasizes learning through evidence rather than optimization for its own sake.

### Iteration 2 Goals

- Evaluate alternative problem formulations, such as regression versus classification, based on dataset characteristics and stakeholder requirements.
- Experiment with different text preprocessing strategies to assess their impact on model performance and stability.
- Explore feature engineering opportunities, including review length, redundancy indicators, and keyword signals.
- Compare alternative model families while maintaining a manageable experimental scope.
- Develop an initial approach to review categorization aligned with Quality Analyst and Customer Success needs.
- Refine architectural documentation based on insights gained from experimentation.

### Iteration 2 Expected Outcome
At the end of Iteration 2, the team will have empirical evidence supporting key design decisions, a clearer understanding of trade-offs between approaches, and an updated system design informed by experimental results. This positions the project for convergence in later phases.

---

## Iteration Strategy Rationale
This two-iteration structure reflects a deliberate progression from understanding to learning. Iteration 1 focuses on establishing architectural and analytical clarity, while Iteration 2 leverages that foundation to drive informed system evolution. This approach aligns with OpenUP principles and supports disciplined software engineering for data science.
