# Drug-Toxicity-Prediction
Prediction of Drug Toxicity using ToX21 Dataset

# 🧪 Tox21 Toxicity Prediction using Deep Learning and Ensemble Models

This project implements a robust pipeline for predicting compound toxicity based on the **Tox21 dataset**. It leverages dense molecular descriptors and sparse fingerprints as features, applies preprocessing and feature selection, and uses a combination of **Neural Networks**, **XGBoost**, and **LightGBM**, along with **SMOTE balancing** and **stacked ensembling** to improve classification performance.

---

## 📁 Dataset

The dataset used is from the **Tox21 Challenge**, which contains:
- SMILES representations of compounds
- Binary labels for 12 different toxicity assays
- Precomputed:
  - `dense` features (physicochemical descriptors)
  - `sparse` features (fingerprints)
  
Files:
- `tox21_labels_train.csv.gz`, `tox21_labels_test.csv.gz`
- `tox21_dense_train.csv.gz`, `tox21_dense_test.csv.gz`
- `tox21_sparse_train.mtx.gz`, `tox21_sparse_test.mtx.gz`

---

## 🧠 Model Overview

### ➤ Feature Engineering
- Dense and sparse features are combined.
- Sparse features with >5% presence across compounds are retained.
- Features are normalized using `StandardScaler` followed by `tanh()`.

### ➤ Models Used
- **Neural Network (Keras)**: 2-layer MLP with BatchNorm, Dropout, LeakyReLU.
- **XGBoost**
- **LightGBM**
- **Weighted Ensemble**: Combines model outputs based on validation AUC.
- **Stacking Ensemble**: Uses Logistic Regression as meta-model.

### ➤ Balancing
- **SMOTE** is applied to handle class imbalance for each assay.

---

## 📊 Evaluation Metric

All models are evaluated using **ROC-AUC score**, which measures the ability to distinguish between toxic and non-toxic classes. AUC is computed for each of the 12 assays individually and averaged.

---

## 🚀 How to Run

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/tox21-toxicity-prediction.git
   cd tox21-toxicity-prediction
````

2. Install required packages:

   ```bash
   pip install -r requirements.txt
   ```

3. Place all dataset files in the root folder or update paths in the script.

4. Run the training script:

   ```bash
   python main.py
   ```

---

## 📈 Sample Output

```
🔬 Training on assay: NR-AhR
  ➤ NN AUC         = 0.898
  ➤ XGBoost AUC    = 0.905
  ➤ LightGBM AUC   = 0.904
  ➤ Weighted AUC   = 0.911
  ➤ Stacking AUC   = 0.909
```

Final Average AUCs:

  ➤ Neural Network : 0.802
  ➤ XGBoost        : 0.816
  ➤ LightGBM       : 0.820
  ➤ Weighted Ens.  : 0.830
  ➤ Stacking Ens.  : 0.830

---

## 📦 Dependencies

```text
numpy
pandas
scikit-learn
tensorflow
xgboost
lightgbm
imbalanced-learn
scipy
```

> Install with: `pip install -r requirements.txt`

---

## 🧠 Future Improvements

* Incorporate Graph Neural Networks (GCNs) using molecular graphs from SMILES.
* Add SHAP/feature importance analysis for model interpretability.
* Create a web interface for users to submit SMILES and get predictions.

---

## 🔖 License

This project is licensed under the [MIT License](LICENSE).

---

## 🤝 Acknowledgments

* [Tox21 Data Challenge](https://tripod.nih.gov/tox21/challenge/)
* RDKit (for computing descriptors/fingerprints, if used externally)

---

## 🧑‍💻 Author

**Soumyadeep Chakraborty**
Feel free to connect or raise issues if you have questions!

---

Would you also like a sample `requirements.txt` or `main.py` starter file? Let me know!


```

---



