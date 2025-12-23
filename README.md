# 🕵️ Fake or Real: The Impostor Hunt in Texts

## 📌 Project Overview

This project is a solution for the Kaggle competition **"Fake or Real: The Impostor Hunt in Texts."** The goal is to identify the **"Real"** article from pairs of text files where one has been modified.

**Competition Link:** [https://www.kaggle.com/competitions/fake-or-real-the-impostor-hunt](https://www.kaggle.com/competitions/fake-or-real-the-impostor-hunt)

---

## 🛠️ Methodology

### 1. 📂 Data Loading

The pipeline reads raw text from a structured directory. It uses `train.csv` to map article IDs to the correct "real" file number (1 or 2) to build the training set.

### 2. 🔡 Text Vectorization (TF-IDF)

The raw text is converted into numerical features using `TfidfVectorizer` with the following parameters:

* `max_features=5000`
* `stop_words='english'`
* `ngram_range=(1, 2)`

### 3. 🤖 Classification Model

A **Random Forest Classifier** is used for the classification task.

* **Hyperparameters:** `n_estimators=300`, `max_depth=20`, `random_state=42`.
* **Logic:** The model predicts the probability of a text being "Real" using `predict_proba`. For each test pair, the file with the higher probability is selected as the winner.

---

## 📂 Project Structure

The project files are organized as follows:

```text
└── data/
    ├── train/                     # Folders containing paired training text files
    ├── test/                      # Folders containing paired test text files
    ├── train.csv                  # Labels for each training pair
    ├── fake_news_detection.ipynb  # Main Jupyter Notebook
    └── submission.csv             # Generated predictions for the test set

```

---

## 🚀 How to Run

1. **Prepare Data:** Ensure the dataset is placed in the `data/` folder as shown above.
2. **Install Libraries:**
```bash
pip install numpy pandas scikit-learn

```


3. **Execute:** Run the cells in `fake_news_detection.ipynb` to process the data, train the model, and generate the `submission.csv` file.
