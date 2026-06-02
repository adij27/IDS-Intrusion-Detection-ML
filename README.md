# 🛡️ IDS Project - Intrusion Detection System Analysis [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

> **Academic Group Project** — CS519 Machine Learning, New Mexico State University  
> **Team:** Aditya Jadhav · Nikshith Kilaru · Dinesh Kumar Gowd Jadapalli · Siva Sai Kumar Boina · Md Omar Faruque

## 📌 Project Overview
Comprehensive machine learning framework for intrusion detection system analysis featuring:
- Random Forest classifiers (base and tuned)
- Artificial Neural Networks with SMOTE
- Fuzzy C-Means clustering
- Advanced feature selection techniques

## 🔍 Features
- Supports both Kaggle and UNSW-NB15 datasets
- Comprehensive Exploratory Data Analysis (EDA)
- Outlier detection and removal (IQR method)
- Feature scaling comparison
- Correlation-based feature selection
- Dynamic SHAP-based top 10 feature selection
- Multiple model types:
  - Base Random Forest
  - Tuned Random Forest (GridSearchCV)
  - PCA + Random Forest
  - ANN with SMOTE (requires TensorFlow)
  - Fuzzy C-Means clustering (requires scikit-fuzzy)
- SHAP analysis for model interpretation
- Detailed results logging

## 📂 Dataset Information
### UNSW-NB15 Dataset
Created by the Australian Centre for Cyber Security (ACCS)  
🔗 [Dataset Link](https://research.unsw.edu.au/projects/unsw-nb15-dataset)  
Files:
- `UNSW_NB15_training-set.csv`
- `UNSW_NB15_testing-set.csv`

### Kaggle Cybersecurity Dataset
Provided by user dnkumars on Kaggle  
🔗 [Dataset Link](https://www.kaggle.com/datasets/dnkumars/cybersecurity-intrusion-detection-dataset/)  
File: `cybersecurity_intrusion_data.csv`

## 🏗️ Project Structure
```
IDS_project/
├── CS_519_Project_report/       # LaTeX source + final PDF report
├── merged_ids_analysis.py       # Main analysis script
├── tf_gpu_env.yml               # Conda environment config
└── README.md                    # Project documentation
```

> **Note:** Datasets (~46MB) and model output files (~61MB) are excluded from the repo to keep it lightweight. Download datasets from the links below and run the script to regenerate results.

## 🚀 Getting Started
### Environment Setup
```bash
conda env create -f tf_gpu_env.yml
conda activate tf_gpu_env
```

### Basic Usage
```bash
python merged_ids_analysis.py --dataset_name [kaggle|unsw] --input_dir /path/to/data --output_dir ./results
```

### Examples
**Kaggle Dataset:**
```bash
python merged_ids_analysis.py --dataset_name kaggle --input_dir . --output_dir ./kaggle_results
```

**UNSW-NB15 Dataset:**
```bash
python merged_ids_analysis.py --dataset_name unsw --input_dir . --output_dir ./unsw_results
```

### Advanced Options
| Flag | Description | Default |
|------|-------------|---------|
| `--sample_size` | Number of samples (0=full dataset) | 20000 |
| `--run_ann` | Include ANN+SMOTE analysis | False |
| `--run_fuzzy` | Include Fuzzy C-Means | False |
| `--run_shap` | Include SHAP analysis | False |
| `--feature_selection_corr_threshold` | Correlation threshold for feature selection | 0.0 (disabled) |
| `--run_shap_selection` | Use top 10 SHAP features | False |

## 📊 Output
- `summary.txt`: Detailed analysis results
- Trained models (`.pkl`, `.keras`)
- Fuzzy C-Means cluster centers (`.pkl`)

## 🔄 Analysis Stages
1. **Original Data**: Full analysis on raw dataset
2. **Outlier Removal**: Analysis after IQR-based outlier removal
3. **SHAP Feature Selection**: Analysis using top 10 SHAP features

## 🛠️ Feature Selection
- **Correlation-Based**: Removes highly correlated features
- **SHAP-Based**: Selects most influential features

For full documentation, run:
```bash
python merged_ids_analysis.py --help