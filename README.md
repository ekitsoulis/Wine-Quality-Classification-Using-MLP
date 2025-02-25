# 🍷 Wine Quality Classification Using Multi-Layer Perceptron (MLP)

## 📌 Overview
This project explores **binary classification of wine quality (Good vs. Bad)** using a **Multi-Layer Perceptron (MLP)** neural network. The dataset consists of **6497 samples** of red and white wine, with **11 physicochemical properties** as features. Extensive **preprocessing**, **hyperparameter tuning**, and **model evaluation** were conducted to optimize performance.

---

## 📂 Dataset
- **Source:** [Wine Quality Dataset on Kaggle](https://www.kaggle.com/datasets/rajyellow46/wine-quality)
- **Features:**
  - Fixed acidity, volatile acidity, citric acid, residual sugar, chlorides, free sulfur dioxide, total sulfur dioxide, density, pH, sulphates, alcohol.
  - **Target variable:** Binary **(Good = 1, Bad = 0)** based on quality score (Threshold = 7).

---

## 🚀 Methodology
### **1️⃣ Data Preprocessing**
✔ **Missing Values Handling:** Removed 34 rows with missing data (insignificant impact).  
✔ **Duplicate Removal:** Dropped 1168 duplicate rows.  
✔ **Feature Encoding:** Converted quality into **binary classification** (Good ≥ 7, Bad < 7).  
✔ **Data Balancing:** Compared **SMOTE (oversampling)** and **downsampling** methods.  
✔ **Feature Scaling:** Experimented with different scalers:
   - **StandardScaler** (Best Performance)
   - **Normalizer**
   - **MinMaxScaler**
   - **MaxAbsScaler**

### **2️⃣ Machine Learning Model: Multi-Layer Perceptron (MLP)**
- Used an **MLPClassifier** (Feedforward Neural Network).
- **Hyperparameters Tuned:**
  - **Number of neurons**
  - **Number of hidden layers**
  - **Learning rate**
  - **Activation functions**
- **Optimization method:** **Backpropagation**

### **3️⃣ Evaluation Metrics**
- **Accuracy Score**
- **Precision, Recall, and F1-score**
- **Confusion Matrix**
- **Comparative Analysis of Hyperparameters**

---

## 📊 Comparative Results & Findings

### **1️⃣ Impact of Different Preprocessing Approaches**
| Scaling Method  | Accuracy | F1 Score (Bad) | F1 Score (Good) |
|----------------|---------|---------------|---------------|
| **Standard Scaler (Best Choice)** | **79%** | **0.79** | **0.80** |
| Normalizer    | 50% | 0.67 | 0.03 |
| MaxAbs Scaler | 76% | 0.76 | 0.76 |
| MinMax Scaler | 76% | 0.74 | 0.78 |

✔ **Conclusion:** **Standard Scaler + SMOTE produced the best results**.

---

### **2️⃣ Impact of Neuron Count on Model Performance**
| Neurons | Accuracy | F1 Score (Bad) | F1 Score (Good) |
|---------|---------|---------------|---------------|
| **5**   | 79% | 0.78 | 0.80 |
| **10**  | 80% | 0.80 | 0.81 |
| **18**  | 80.5% | 0.79 | 0.82 |
| **20**  | 81.6% | 0.81 | 0.83 |
| **50**  | 80.6% | 0.80 | 0.81 |
| **100** | 80.9% | 0.81 | 0.81 |
| **500** | 76.1% | 0.74 | 0.78 |

✔ **Conclusion:** The optimal number of **neurons per layer was (70,60)**. More neurons led to **overfitting**, while fewer neurons **reduced accuracy**.

---

### **3️⃣ Impact of Hidden Layer Depth**
| Hidden Layers | Accuracy | F1 Score (Bad) | F1 Score (Good) |
|--------------|---------|---------------|---------------|
| **(15,15)**  | 80.9% | 0.79 | 0.82 |
| **(20,20)**  | 82.5% | 0.82 | 0.84 |
| **(30,30)**  | 82.4% | 0.81 | 0.84 |
| **(50,50)**  | 82.2% | 0.81 | 0.84 |
| **(70,60) (Best Choice)** | **82.8%** | **0.81** | **0.84** |
| **(100,100)**| 82.3% | 0.82 | 0.83 |
| **(80,60,50)** | 81.6% | 0.81 | 0.82 |

✔ **Conclusion:** More than **2 hidden layers caused overfitting**.

---

### **4️⃣ Learning Rate Tuning**
| Learning Rate | Accuracy | F1 Score (Bad) | F1 Score (Good) |
|--------------|---------|---------------|---------------|
| **0.001**    | 74.8%  | 0.74 | 0.76 |
| **0.01**     | 76.9%  | 0.75 | 0.78 |
| **0.05**     | 79.8%  | 0.79 | 0.81 |
| **0.2**      | 82.8%  | 0.81 | 0.84 |
| **0.5 (Best Choice)** | **86.4%** | **0.86** | **0.87** |
| **0.6**      | 85.3%  | 0.85 | 0.86 |
| **0.7**      | 85.4%  | 0.85 | 0.86 |

✔ **Conclusion:** **A learning rate of 0.5 performed best**.

---

### **5️⃣ Activation Functions**
| Activation Function | Accuracy | F1 Score (Bad) | F1 Score (Good) |
|-------------------|---------|---------------|---------------|
| **Sigmoid (Best Choice)** | **86.4%** | **0.86** | **0.87** |
| ReLU             | 84.4%  | 0.84 | 0.85 |

✔ **Conclusion:** **Sigmoid outperformed ReLU**, improving both **recall and precision**.

---

## 📜 How to Run
### **🔧 Installation**
1. **Clone this repository**:
   ```bash
   git clone https://github.com/ekitsoulis/Wine-Quality-MLP.git
   cd Wine-Quality-MLP
