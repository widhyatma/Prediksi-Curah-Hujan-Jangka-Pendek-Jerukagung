# 📋 Changelog

All notable changes to this research project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [v1.0.0] - 2026-09-07 (First Scientific Release)

### 🚀 Initial Public Release for Academic Archiving (Zenodo)

This release establishes the baseline open-source software, datasets, model weights, and experimental notebooks for the study:
> **"Short-term Hourly Rainfall Prediction Framework via Two-Stage Hurdle Transfer Learning Integrating Satellite (GSMaP & IMERG), Reanalysis (ERA5), and Local IoT AWS Ground Truth"**

### ✨ Key Components & Features Included
- **Google Earth Engine (GEE) Extraction Pipelines (`Kode_GEE_Javascript/`):**
  - `GEE_ERA5_Hourly.js`: Script for extracting hourly surface atmospheric parameters (Temperature, Dewpoint, Surface Pressure, U/V Wind, CAPE, TCWV, Direct Radiation, etc.).
  - `GEE_GSMaP.js`: Script for extracting JAXA GSMaP NRT precipitation rate time series.
  - `GEE_IMERG.js`: Script for extracting NASA GPM IMERG Final Run precipitation rate time series.
- **Harmonized Time-Series Datasets (`Data_Satelit/`):**
  - ERA5 Hourly Surface Variables (2000–2026).
  - JAXA GSMaP NRT Satellite Hourly Precipitation.
  - NASA GPM IMERG Satellite Hourly Precipitation.
  - AWS IoT Jerukagung Ground Truth Hourly Telemetry (`id-05_clear_data_hourly`).
- **Two-Stage Hurdle Model Implementations:**
  - `model-xgboost-final.py` & `.ipynb`: Tree-based gradient boosting classifier (Occurrence $P \ge 0.2$ mm/h) and amount regressor with Optuna Dynamic HPO.
  - `model-ltsm-final.py` & `.ipynb`: Recurrent deep learning architecture using BiDirectional LSTM with 24-hour diurnal sliding window memory.
- **Domain Adaptation / Fine-Tuning Pipeline (`fine_tuning_pipeline.ipynb`):**
  - Transfer learning adapting pre-trained macro-satellite representations to local micro-climate ground observations.
  - Layer freezing, top-layer fine-tuning, and isotonic probability calibration.
- **Unified Inference & Benchmark Evaluation Pipeline (`inference_pipeline.ipynb`):**
  - Cross-domain validation evaluating 4 model configurations (XGBoost Pre-train, XGBoost Fine-tuned, LSTM Pre-train, LSTM Fine-tuned).
  - Multi-metric evaluation including PR-AUC, ROC-AUC, Precision, Recall, F1, MAE, RMSE, $R^2$, and Cumulative Water Balance.
- **Comprehensive Atmospheric & Climate Diagnostics (`analisis_data_atmosfer.ipynb`):**
  - 20-year climate trends, seasonal diurnal cycles, and sensor validation against AWS IoT telemetry.
- **Artifacts & Model Weights (`results_xgboost/`, `results_lstm/`, `.zip`):**
  - Pre-trained and fine-tuned `.pkl` and `.keras` models, scalers, and calibrators tracked via Git LFS.
- **Publication Visualizations (`outputs_inference/figures/`):**
  - 28+ high-resolution figures (300 DPI & 600 DPI) ready for academic publication.
- **Metadata & Citation Standardization:**
  - `CITATION.cff` for native GitHub citation indexing.
  - `.zenodo.json` for automated Zenodo DOI ingestion.
  - `LICENSE` under MIT Open Source terms.
