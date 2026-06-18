# d2c-churn-part3-eda
# Part 3: Churn Prediction Model & Model Card

This repository contains the complete, production-ready machine learning workflow for predicting direct-to-consumer (D2C) customer churn within a 60-day window. It operates independently and serves as the data scoring engine for the retention API endpoints developed in Part 4.

---

##  Getting Started (Google Colab & Drive Workflow)

This model script is optimized to run inside Google Colab and relies on mounting Google Drive to pull the tracking dataset package.

### 1. Environment Setup
* Upload your `churn_model.ipynb` file into your Google Colab workspace.
* Ensure your dataset snapshot is placed at the following target path within your Google Drive:
  `My Drive/D2c Churn prediction/ rfm_modeling_snapshot.csv`

### 2. Running the Pipeline
* Open the notebook in Colab and execute the initial cell to mount your personal Google Drive:
```python
  from google.colab import drive
  drive.mount('/content/drive')
