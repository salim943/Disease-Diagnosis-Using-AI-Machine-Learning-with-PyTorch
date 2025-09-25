##  Dataset Structure

This script uses the `ImageFolder` dataset format. Your dataset should be organized like this:

dataset/
├── NORMAL/
│ ├── img1.jpg
│ ├── img2.jpg
│ └── ...
├── PNEUMONIA/
│ ├── img1.jpg
│ └── ...

# Classification Metrics Explanation

The metrics you're seeing are commonly used to evaluate classification models, and they're very helpful for understanding how well a model is performing, especially when dealing with imbalanced classes. Let's break them down:

---

## 1. Precision
**Definition:** Precision is the ratio of correctly predicted positive observations to the total predicted positives.  

**Formula:**  
Precision = TP / (TP + FP)

Where:  
- **TP** = True Positives (correctly predicted positives)  
- **FP** = False Positives (incorrectly predicted as positive)  

**Interpretation:**  
Precision tells you how many of the instances predicted as a certain class (e.g., "PNEUMONIA") were actually that class.  

Example: For **PNEUMONIA**, a precision of `1.00` means that every time the model predicted pneumonia, it was correct.

---

## 2. Recall (Sensitivity, True Positive Rate)
**Definition:** Recall is the ratio of correctly predicted positive observations to all observations in the actual class.  

**Formula:**  
Recall = TP / (TP + FN)

Where:  
- **TP** = True Positives  
- **FN** = False Negatives (instances of the positive class that were misclassified as negative)  

**Interpretation:**  
Recall tells you how many of the actual instances of a certain class were correctly identified by the model. High recall means the model is good at detecting positives.  

Example: For **PNEUMONIA**, a recall of `0.84` means that the model identified 84% of the actual pneumonia cases, but missed 16%.

---

## 3. F1-Score
**Definition:** The F1-score is the harmonic mean of precision and recall, balancing the two metrics. It's useful when you need to balance the importance of precision and recall.  

**Formula:**  
F1-Score = 2 × (Precision × Recall) / (Precision + Recall)

**Interpretation:**  
The F1-score provides a single metric that balances precision and recall. It's especially useful when there is an imbalance between precision and recall.  

Example: For **PNEUMONIA**, an F1-score of `0.91` means the model has a good balance between precision and recall for this class.

---

## 4. Support
**Definition:** Support refers to the number of actual occurrences of the class in the dataset.  

**Interpretation:** Support helps you understand the class distribution.  

For instance, your dataset has:  
- **1,349 instances of NORMAL**  
- **3,883 instances of PNEUMONIA**

Given the 80-20 train-test split:  
- **NORMAL Class (Validation set):** 270 images  
- **PNEUMONIA Class (Validation set):** 777 images  

---

## Summary of Your Results

### NORMAL Class:
- **Precision:** 0.69 → 69% of predictions for NORMAL were correct.  
- **Recall:** 0.99 → 99% of actual NORMAL cases were correctly identified.  
- **F1-Score:** 0.81 → The balance between precision and recall for NORMAL is good, but recall is dominant.  
- **Support:** 270 → There are 270 instances of the NORMAL class in the validation set.  

### PNEUMONIA Class:
- **Precision:** 1.00 → The model is perfectly precise in predicting pneumonia.  
- **Recall:** 0.84 → It correctly identifies 84% of the actual pneumonia cases.  
- **F1-Score:** 0.91 → A very strong F1 score.  
- **Support:** 777 → There are 777 instances of the PNEUMONIA class in the validation set.  

---

## Overall Metrics:
- **Accuracy:** 0.88 → The model is correct 88% of the time based on the validation set.  

### Macro Average:
- **Precision:** 0.84  
- **Recall:** 0.92  
- **F1-Score:** 0.86  

*(Treats each class equally, ignoring class imbalance.)*  

### Weighted Average:
- **Precision:** 0.92  
- **Recall:** 0.88  
- **F1-Score:** 0.89  

*(Accounts for class imbalance, giving more weight to the larger class.)*  

---

## Why These Metrics Matter
- **Precision** is important when minimizing false positives is critical.  
- **Recall** is important when minimizing false negatives is critical (common in medical diagnoses).  
- **F1-score** is useful when you need a balance between precision and recall, especially with class imbalances.  