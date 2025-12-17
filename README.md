# 🛡️ Phishing Website Threat Profiling  
### Interpretable Statistical Modeling for URL-Based Phishing Risk

---

## Overview

This repository explores **phishing website behavior through statistical analysis and interpretable modeling**, with the goal of **quantifying phishing risk rather than merely classifying URLs**.

Instead of optimizing black-box accuracy, this work focuses on:
- Feature-level reasoning
- Statistical significance
- Model interpretability
- Risk scoring suitable for security pipelines

The project deliberately avoids deep learning to emphasize **transparent decision-making**, a requirement in many real-world cybersecurity systems.

This repository serves as:
- A research-oriented analysis
- A baseline for interpretable phishing risk modeling
- A foundation for open-source security tooling

---
## Quick Start

```bash
git clone https://github.com/Aditi141004/phishing-threat-profiling.git
cd phishing-threat-profiling
pip install -r requirements.txt
jupyter notebook
notebook/phishing_threat_profiling.ipynb

```

---

## Problem Framing

Most phishing detection systems reduce the problem to binary classification:

> *Phishing vs. Legitimate*

This framing is insufficient for real security systems, which require:
- Graduated risk levels
- Explainable signals
- Human-interpretable diagnostics

This project reframes phishing detection as a **risk estimation problem**, producing a numeric threat score derived from statistically meaningful URL and content features.

---

## Objectives

- Analyze phishing behavior at the feature-distribution level
- Identify statistically dominant phishing indicators
- Reduce feature noise using correlation-based selection
- Construct an interpretable regression-based threat score
- Evaluate model reliability using classical statistical diagnostics
- Produce insights actionable for security tooling

---

## Dataset

**Dataset:** PhiUSIIL Phishing URL Dataset  
**Source:** UCI Machine Learning Repository (2024)

### Scale & Composition
- **235,795 URLs**
  - 134,850 legitimate
  - 100,945 phishing
- **56 engineered features**
  - URL structure
  - Domain metadata
  - Content-based attributes
- **No missing values**
- Binary label (`1 = legitimate`, `0 = phishing`)

### Rationale
- Recent and realistically engineered
- Designed for explainable analysis
- Suitable for statistical modeling and hypothesis testing

---

## Data Preparation

- Removed non-informative identifiers (raw URL, filenames, titles)
- Encoded categorical variables (e.g., TLDs)
- Eliminated **120 duplicate samples**
- Verified mild class imbalance
- Applied **StandardScaler** for feature normalization

No synthetic sampling or artificial balancing was applied.

---

## Exploratory Analysis

EDA focused on **distributional behavior**, not presentation-level visualization.

### Observations

**Phishing URLs tend to:**
- Be longer and entropy-heavy
- Contain higher special character ratios
- Lack metadata consistency

**Legitimate websites exhibit:**
- Strong URL–title/domain alignment
- Presence of social links and copyright
- Structured and predictable patterns

These observations guided feature selection.

---

## Correlation & Statistical Filtering

- Computed **Pearson correlation** with the target label
- Retained **40 statistically informative features**
- Removed weak predictors to reduce noise and instability

### Dominant Signals

| Feature | Interpretation |
|------|---------------|
| URLSimilarityIndex | Structural legitimacy proxy |
| HasSocialNet | Transparency and trust |
| HasCopyrightInfo | Content maturity |
| DomainTitleMatchScore | Structural consistency |
| HasDescription | Legitimate content behavior |

---

## Modeling: Interpretable Regression

### Motivation
Multiple Linear Regression was chosen to:
- Preserve interpretability
- Enable coefficient-level reasoning
- Allow statistical significance testing
- Serve as a transparent baseline model

### Target Variable

**`URLSimilarityIndex`**  
Used as a continuous proxy for similarity to legitimate URL patterns.

This is a design choice, not a claim of ground truth.

### Configuration

- 14 statistically dominant predictors
- 80/20 stratified train-test split
- All predictors significant at **p < 0.001**

### Performance

- **R² = 0.725**

This reflects explanatory strength, not predictive perfection.

---

## Threat Score Interpretation

| Feature | Effect |
|------|--------|
| DomainTitleMatchScore | Strong legitimacy signal |
| HasSocialNet | Increases trust score |
| URLCharProb | Common patterns reduce risk |
| URLTitleMatchScore | Mismatch signals phishing |
| SpecialCharRatio | Structural obfuscation |
| HTTPS | Minimal standalone value |

**Key Insight:** HTTPS is no longer a reliable phishing discriminator.

---

## Limitations

- Linear models cannot capture complex non-linear phishing tactics
- URLSimilarityIndex is a proxy, not absolute ground truth
- Engineered features may not fully represent real-world noise
- Model is not deployment-ready without calibration and validation

---

## Model Assumptions & Validity Constraints
This project intentionally prioritizes interpretability over raw predictive
performance. The modeling choices and results should be interpreted under the
following assumptions and constraints.

### Assumptions

- **Linearity:**  
  The Multiple Linear Regression (MLR) model assumes linear relationships
  between features and the threat score.

- **Feature Independence:**  
  While correlation-based filtering was applied, residual multicollinearity
  may still exist.

- **Stationary Feature Behavior:**  
  The model assumes phishing URL characteristics remain stable over time.

- **Proxy Target Variable:**  
  `URLSimilarityIndex` is used as a continuous proxy for legitimacy patterns,
  not as absolute ground truth risk.

### Limitations

- Linear models cannot capture complex non-linear phishing strategies.
- Engineered features may not fully reflect real-world adversarial behavior.
- HTTPS is no longer a reliable standalone indicator of legitimacy.
- The model is **not production-ready** without calibration and continuous
  validation.

These limitations are explicitly acknowledged and motivate future work
outlined in the project roadmap.

## Future Work

- Benchmark against interpretable tree-based models
- Calibrate continuous scores into discrete risk bands
- Temporal phishing evolution analysis
- API-based scoring service
- Integration with browser and email security tools

---

## Tech Stack

- Python
- Pandas, NumPy
- Matplotlib, Seaborn
- Scikit-learn
- Statsmodels

---

## Repository Structure

phishing-threat-profiling/

│

├── data/

│   └── phiusill_phishing_urls.csv

│

├── notebook/

│   └── phishing_threat_profiling.ipynb

│

├── poster/

│   └── phishing_threat_analysis_poster.pdf

│

├── README.md

├── requirements.txt

└── LICENSE

---

## Open Source Readiness

This repository is structured for:
- Reproducibility
- Extension
- Comparative experimentation

Contributions are welcome in:
- Feature engineering
- Model benchmarking
- Evaluation methodology
- Deployment-oriented refactoring

---

## Authors

- Aditi Gupta  
- Anusha Sarkar
