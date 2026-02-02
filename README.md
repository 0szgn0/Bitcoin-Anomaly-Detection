# 🛡️ Bitcoin Illicit Transaction Detection (Anti-Money Laundering)


## 👋 About The Project

This project is my attempt to solve a real-world financial problem: **Detecting illicit (illegal) transactions in the Bitcoin network.** I used the famous **Elliptic Data Set** to build a Machine Learning model that can flag suspicious activities like money laundering or ransomware payments.

## ❓ The Problem
In this dataset, **only ~10%** of transactions are illicit, while 90% are licit.
* This is a classic **"Imbalanced Data"** problem.
* If a model just guesses "Legal" for everything, it gets 90% accuracy but catches **zero** criminals.
* **My Goal:** is to build a model that actually catches the "bad guys" (High Recall) without accusing innocent users (High Precision) so i used F1 score.

## 🛠️ My Approach
I treated this as a **Binary Classification** problem. Here is what I did:

1.  **Data Cleaning:** Filtered out unlabelled data.
2.  **Handling Imbalance:** I used `class_weight='balanced'` and Stratified Splitting to make sure the model pays attention to the minority class (illegal transactions).
3.  **Model Selection:** I chose **Random Forest Classifier** because it works well with complex tabular data.
4.  **Optimization:** I didn't stick with default settings. I used **`RandomizedSearchCV`** to find the best hyperparameters (like `n_estimators`, `max_depth`) to improve the F1-Score.

## 📊 Results
After optimizing the model, I tested it on unseen data. Here are the metrics for the **Illicit (Fraud)** class:

* **Precision (0.99):** When my model says "This is illegal," it is **99%** likely to be true. (Very few false alarms).
* **Recall (0.90):** The model successfully caught **90%** of all illegal transactions in the test set.
* **F1-Score (0.94):** The balance between precision and recall is excellent.

### Confusion Matrix
<img width="651" height="547" alt="indir" src="https://github.com/user-attachments/assets/a80f6c80-8cac-49ec-a356-1ddcaf0d315c" />

### Top Features
I also analyzed which features were most important. It turns out that specific transaction patterns (Feature V23, V55, etc.) are strong indicators of illegal activity.

<img width="1189" height="590" alt="indir (1)" src="https://github.com/user-attachments/assets/b354b244-30bb-4943-84ff-a99ff5af0261" />


## 💻 How to Run This Code
1.  Clone this repository.
2.  Install the libraries:
    ```bash
    pip install -r requirements.txt
    ```
3.  Open the `The_Clean_Data_And_The_Model` notebook to see the code and in the notebook called `Hyperparameter_Optimization` you will see the optimization code it takes too long to run and you dont have to run it.

---
*Author: Selman Sezgin | Statistics Student & FinTech Enthusiast*
