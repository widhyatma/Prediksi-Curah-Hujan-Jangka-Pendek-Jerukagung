# 📦 Release Notes: v1.0.0 - Initial Scientific Release

**Title:** Prediksi Curah Hujan Jangka Pendek Jerukagung: Two-Stage Hurdle Transfer Learning Framework for Hourly Precipitation Prediction  
**Release Tag:** `v1.0.0`  
**Date:** September 7, 2026  
**Repository:** [https://github.com/widhyatma/Prediksi-Curah-Hujan-Jangka-Pendek-Jerukagung](https://github.com/widhyatma/Prediksi-Curah-Hujan-Jangka-Pendek-Jerukagung)  
**Author:** Evan Alif Widhyatma  
**License:** MIT License  

---

## 🎯 Overview

We are pleased to announce the **first official scientific release (`v1.0.0`)** of the Jerukagung Short-Term Rainfall Prediction research repository, prepared for permanent academic archiving on **Zenodo** with a citable Digital Object Identifier (DOI).

This release contains the complete end-to-end scientific software pipeline, harmonized meteorological datasets, pre-trained and fine-tuned models, and evaluation notebooks reproducing all empirical findings.

---

## 🔬 Scientific Highlights

### 1. Two-Stage Hurdle Architecture
Tropical precipitation exhibits severe zero-inflation (>85% non-rain hours). Standard single-regression models tend to predict artificial drizzle (*drizzle artifacts*). This framework addresses the zero-inflation challenge by separating:
- **Stage 1 (Binary Occurrence Classifier):** Determines whether rain will occur ($P \ge 0.2$ mm/h) using calibrated probabilities.
- **Stage 2 (Conditional Amount Regressor):** Estimates rainfall magnitude exclusively on rain events, followed by zero-mask gating.

### 2. Dual-Paradigm Benchmark
- **Tree-Based:** Gradient Boosted Trees (XGBoost) optimized dynamically using Bayesian optimization via Optuna.
- **Deep Learning:** BiDirectional LSTM capturing diurnal atmospheric cycles through a 24-hour temporal sliding window ($LOOKBACK = 24$).

### 3. Satellite-to-Ground Domain Adaptation
Pre-training on continuous multi-year satellite estimates (JAXA GSMaP NRT & Copernicus ERA5) provides robust macro-atmospheric feature representations. Fine-tuning on local AWS IoT telemetry (Stasiun Klimatologi Jerukagung, Kebumen) successfully adapts the models to micro-climatic terrain conditions, significantly boosting Precision and $R^2$ scores.

---

## 📊 Benchmark Summary Table

| Model Architecture | Phase | Precision | Recall | F1-Score | ROC-AUC | PR-AUC | MAE (mm/h) | RMSE (mm/h) | $R^2$ Score |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| **XGBoost** | Pre-Trained (AWS) | 0.252 | **0.867** | 0.390 | 0.814 | 0.347 | 0.449 | 1.829 | -0.124 |
| **XGBoost** | **Fine-Tuned (AWS)** | **0.672** | 0.584 | **0.625** | **0.871** | **0.669** | **0.261** | **1.218** | **0.502** |
| **BiLSTM** | Pre-Trained (AWS) | 0.219 | 0.832 | 0.346 | 0.776 | 0.301 | 0.521 | 2.014 | -0.362 |
| **BiLSTM** | **Fine-Tuned (AWS)** | 0.541 | 0.690 | 0.607 | 0.852 | 0.597 | 0.298 | 1.345 | 0.393 |

---

## 💻 Quick Start & Replication

1. **Clone with Git LFS:**
   ```bash
   git clone https://github.com/widhyatma/Prediksi-Curah-Hujan-Jangka-Pendek-Jerukagung.git
   cd Prediksi-Curah-Hujan-Jangka-Pendek-Jerukagung
   git lfs pull
   pip install -r requirements.txt
   ```

2. **Run Inference & Reproduce Figures:**
   ```bash
   jupyter notebook inference_pipeline.ipynb
   ```

3. **Fine-Tune Models:**
   ```bash
   jupyter notebook fine_tuning_pipeline.ipynb
   ```

---

## 📖 How to Cite

If you utilize this framework or datasets in your research, please cite:

```bibtex
@software{widhyatma_2026_rainfall,
  author       = {Evan Alif Widhyatma},
  title        = {{Prediksi Curah Hujan Jangka Pendek Jerukagung: Two-Stage Hurdle Transfer Learning Framework for Hourly Precipitation Prediction}},
  month        = sep,
  year         = 2026,
  publisher    = {Zenodo},
  version      = {v1.0.0},
  url          = {https://github.com/widhyatma/Prediksi-Curah-Hujan-Jangka-Pendek-Jerukagung}
}
```
