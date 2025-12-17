# 📄 Fairness Auditing and Mitigation in Dermoscopic AI: From Data Equity to Spurious Localization Bias

## 🌟 Abstract

This project presents a rigorous fairness audit of a deep learning classifier (EfficientNet-B0) for skin lesion diagnosis on the HAM10000 dataset. While initial mitigation involved a **Multi-Factor Fairness Weighting Scheme** (based on Lesion Class, Age, and Sex), severe performance disparities persisted. Our primary contribution is the execution and quantification of a **Spurious Confounding Bias** audit, where performance was analyzed against a non-demographic factor: **13 Anatomical Localization Sites**. The findings revealed critical safety concerns, including a **$55\%$ absolute disparity in the False Negative Rate (FNR)** for Vascular lesions based solely on the image's source location. This evidence justifies a critical shift in research toward **Disentangled Representation Learning** to ensure equitable and trustworthy clinical AI systems, moving fairness beyond simple demographic parity.

---

## 🔑 Key Features and Contributions

* **Pioneered Hidden Bias Auditing:** Developed and executed an audit framework focusing on **Spurious Confounding Bias** by analyzing model performance across 13 Anatomical Localization sites.
* **Quantified FNR Disparity:** Identified a critical clinical safety risk by quantifying up to a $\mathbf{55\%}$ absolute variance in the **False Negative Rate (FNR)** for Vascular lesions based purely on the lesion's location.
* **Established Research Trajectory:** Confirmed persistent Demographic Bias (Nevus accuracy drops $\approx 55\%$ from age $<30$ to $>50$) and used the quantified localization bias to justify a novel research direction: **Disentangled Representation Learning**.
* **Methodology:** Implemented Multi-Factor Sample Weighting ($\text{Class} \times \text{Age} \times \text{Sex}$) to establish a fairness-aware baseline and conducted rigorous clinical trustworthiness assessments (Calibration Curves).

---

## 🔬 Methodology Overview

### 1. Data and Preparation
* **Dataset:** HAM10000 (10,000 dermoscopic images, 7 lesion classes).
* **Preprocessing:** Age imputation (median), missing localization fill ('unknown'), and Age Binning ($<30$, $30-50$, $>50$).

### 2. Model Training
* **Architecture:** EfficientNet-B0 (Transfer Learning) with Fine-tuning.
* **Mitigation:** Training utilized a custom **Multi-Factor Sample Weighting Scheme** applied to the categorical cross-entropy loss to mitigate class, age, and sex imbalances simultaneously.

### 3. Auditing Metrics
* **Classification Metrics:** Accuracy, AUC, and clinical metrics (False Negative Rate - FNR, False Positive Rate - FPR).
* **Trustworthiness Metrics:** Calibration Curves and Brier Score.

---

## 📊 Core Results and Visual Evidence

### 1. Demographic and Trustworthiness Audit

| Figure | Description | Key Finding |
| :--- | :--- | :--- |
| **Figure 1: Accuracy by Age Bin** | Performance across lesion classes stratified by age bin. | Accuracy for Nevus (`nv`) drops $\approx 55\%$ for patients $>50$, showing severe demographic bias despite weighting. |
| **Figure 2: FNR by Sex** | False Negative Rate across lesion classes by Sex. | FNR $\approx 1.0$ for critical rare classes (e.g., BCC, MEL) regardless of sex, highlighting persistent underperformance. |
| **Figure 3: Calibration Curves** | Predicted probability vs. Fraction of Positives. | Severe miscalibration, particularly for Nevus (`nv`), demonstrating unreliable probability outputs for clinical use. |

**Figure 1: Accuracy by Age Bin for Each Class**
![Figure 1: Accuracy by Age Bin for Each Class](Experiment%20%231%20-%20Accuracy%20by%20age%20Bine%20for%20each%20class.png)

**Figure 2: False Negative Rate by Sex for Each Class**
![Figure 2: False Negative Rate by Sex for Each Class](Experiment%20%232%20-%20False%20Negtive%20Rate%20by%20Sex.png)

**Figure 3: Calibration Curves**
![Figure 3: Calibration Curves](Experiment%20%232%20-%20Calibration%20Curves.png)

---

### 2. Localization Bias Audit (Hidden Bias Breakthrough)

This section demonstrates the model's reliance on non-clinical features, such as the image background or texture associated with the body part.

| Figure | Description | Key Finding |
| :--- | :--- | :--- |
| **Figure 4: FNR by Localization** | FNR across classes stratified by 13 Anatomical Sites. | Shows high volatility, proving Spurious Bias. Vascular FNR ranges from $\approx 0.20$ to $\approx 0.75$ (**a $55\%$ disparity**). |
| **Figure 5: Accuracy by Localization** | Overall accuracy across classes by 13 Anatomical Sites. | Accuracy is highly unstable for common lesions (e.g., Nevus accuracy varies $\approx 25\%$ across locations), showing poor generalization. |

**Figure 4: False Negative Rate (FNR) by Anatomical Localization (Hidden Bias)**
![Figure 4: False Negative Rate (FNR) by Anatomical Localization (Hidden Bias)](Experiment%20%233%20-%20False%20Negtive%20Rate%20(FNR)%20By%20Anatomical%20Localization%20(Hidden%20Bias).png)

**Figure 5: Accuracy by Anatomical Localization (Hidden Bias)**
![Figure 5: Accuracy by Anatomical Localization (Hidden Bias)](Experiment%20%233%20-%20Accuracy%20by%20Anatomical%20Localization%20(Hidden%20Bias).png)

---

## 🛠️ Repository Structure
.
├── `Fairness Auditing and Mitigation in Dermoscopi.ipynb`  # Complete execution script (model, training, audit)
├── `README.md`       # (This file)
├── `HAM10000_metadata.csv`

## 🚀 Future Research Direction (PhD Pitch)

The quantified localization bias proves that current fairness methods are insufficient. This work justifies a novel research trajectory focused on mitigating spurious correlation through:

* **Disentangled Representation Learning:** Developing models to explicitly separate pathological features (the lesion) from confounding features (the background/localization context).
* **Loss Function Design:** Implementing fairness-aware loss terms that directly penalize performance variance across non-demographic subgroups (localization sites).

---

## 🔗 Links and Resources

* **Full Technical Report:** [Hosted Report Link](Fairness%20Auditing%20and%20Mitigation%20in%20Dermoscopic%20AI%20-%20From%20Data%20Equity%20to%20Spurious%20Localization%20Bias.pdf)
* **Code Repository:** [GitHub Code Link](https://github.com/adilrasheed139/Fairness-Auditing-and-Mitigation-in-Dermoscopic-AI-From-Data-Equity-to-Spurious-Localization-Bias.git)
* **Dataset:** HAM10000 Skin Cancer MNIST Dataset [Kaggle](https://www.kaggle.com/datasets/kmader/skin-cancer-mnist-ham10000)
