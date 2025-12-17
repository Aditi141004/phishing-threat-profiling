# 🗺️ Project Roadmap — Phishing Threat Profiling

This roadmap defines the technical evolution of the **Phishing Website Threat Profiling** project,
with the explicit goal of transitioning from exploratory analysis to a **maintainable,
interpretable, open-source phishing risk assessment system**.

The roadmap emphasizes **model transparency, statistical rigor, and practical deployment constraints**.

---

## ✅ Current State

The following components are complete and reproducible:

- Dataset selection and validation (PhiUSIIL — UCI ML Repository)
- Data preprocessing and normalization
- Exploratory analysis focused on feature distributions
- Correlation-driven feature filtering
- Hypothesis-based comparison of phishing vs legitimate behavior
- Interpretable Multiple Linear Regression (MLR) model
- Continuous numeric phishing threat score
- Project documentation and research poster

This establishes a statistically sound baseline.

---

## Phase 1: Model Benchmarking & Baselines

**Objective:** Quantify the trade-off between interpretability and performance.

Planned work:
- Benchmark MLR against:
  - Logistic Regression (interpretable baseline)
  - Random Forest (non-linear ensemble)
  - Gradient Boosting (performance-oriented model)
- Evaluate using:
  - R² and RMSE (regression framing)
  - Feature importance stability
- Compare explanation quality vs predictive gains

Deliverable:
- Model comparison report with explicit interpretability trade-offs

---

## Phase 2: Feature Engineering & Statistical Validation

**Objective:** Improve signal quality while controlling model complexity.

Planned work:
- Engineer additional URL-based features:
  - Entropy measures
  - Character and token n-grams
- Diagnose multicollinearity using:
  - Variance Inflation Factor (VIF)
- Evaluate dimensionality reduction:
  - PCA (exploratory, not default)
- Revalidate feature significance using hypothesis testing

Deliverable:
- Refined feature set with documented statistical justification

---

## Phase 3: Threat Score Calibration

**Objective:** Convert continuous scores into usable security signals.

Planned work:
- Define interpretable risk thresholds:
  - Low / Medium / High
- Calibrate score boundaries using validation data
- Analyze score stability on unseen URLs
- Document known failure modes and edge cases

Deliverable:
- Calibrated, documented phishing risk scoring scheme

---

## Phase 4: Tooling & Deployment Readiness

**Objective:** Enable real-world experimentation and integration.

Planned work:
- Implement a minimal scoring API
- Support batch and single-URL inference
- Add basic logging and monitoring
- Define input validation and failure handling

Deliverable:
- Usable prototype for downstream security tooling

---

## Phase 5: Open-Source Hardening & Research Extensions

**Objective:** Make the project extensible and contributor-friendly.

Planned work:
- Improve developer documentation
- Add contribution guidelines and issue templates
- Encourage community benchmarking
- Explore integration with threat intelligence feeds

Deliverable:
- Stable, community-ready open-source repository

---

## Contribution Scope

This roadmap is intentionally modular. Contributions may include:
- Model experimentation and evaluation
- Feature engineering and validation
- Tooling and deployment improvements
- Documentation and reproducibility enhancements

---

## Long-Term Vision

To build an **interpretable, statistically grounded phishing risk assessment system**
that supports both cybersecurity research and practical threat mitigation,
without relying on opaque black-box models.
