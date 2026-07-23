


# Project | Business Case: Automated Customer Reviews

<br>

## Project Goal

This project aims to develop a product review system powered by NLP models that aggregate customer feedback from different sources. The key tasks include classifying reviews, clustering product categories, and using generative AI to summarize reviews into recommendation articles.

<br>

## Problem Statement

With thousands of reviews available across multiple platforms, manually analyzing them is inefficient. This project seeks to automate the process using NLP models to extract insights and provide users with valuable product recommendations.

<br>

## Datasets

- **Primary Dataset**: [Amazon Product Reviews from Kaggel](https://www.kaggle.com/datasets/datafiniti/consumer-reviews-of-amazon-products/data)


<br>

## Main Tasks


### 1. Build a model for Sentiment Analysis



---


---


---

## MODEL TRACKING SPREADSHEET

| Model                                        | Feature extraction   | Training model          | Accuracy | test    | Notes                                                                                                                |
|----------------------------------------------|----------------------|-------------------------|----------|---------|----------------------------------------------------------------------------------------------------------------------|
| 1. Sentiment Analysis                                   | distilbert-base-uncased               | Log Regression          | 97.80%   |         | Baseline - start here                                                                                                |
| 2. Product Category Clustering                                   | KMeans + TF-IDF + ngrams    | Log Regression          | 98%      |         | Baseline - start here                                                                                                |
| 3. Product Review Summarization                                   | meta-llama/Llama-3.2-3B-Instruct | Linear SVM              | 97%      |         | When increasing vector size from 100 - 300 increased accuracy from 96% - 97%                                         |
| 4.                                  |                  |  |      |         |                                                                                                  |
| 5.                               |      |  |       |         |                                                                                 |
| 6.                                  | Embedding - Word2Vec | Log Regression          | 96,80%   |         |                                                                                                                      |

<br>

---



## Sample Prediction

### Streamlit Application

<center>
<table>
  <td><img src="/images/deploy_streamlit_02_pred_260710.jpg" height="420" alt="Horse prediction"></td>
  <td> &nbsp &nbsp </td>
  <td><img src="/images/deploy_streamlit_02_pred_260710.jpg" height="420" alt="Dookie prediction"></td>
</table>
</center>



---

## Live Demo

🌐 **Streamlit Cloud**

[https://project2-nlp-fakenews.streamlit.app](https://project2-nlp-fakenews.streamlit.app)

---

# Problem Statement

The rapid spread of misinformation through online news and social media makes it increasingly difficult to distinguish reliable information from fake news.

The objective of this project is to build a machine learning model capable of automatically classifying news articles into:

* **Real**
* **Fake**

using only the article text.

---

# Dataset

**Dataset:** Fake News Dataset

* File: `dataset/data.csv`
* Text-based binary classification dataset


---

# Model Architecture

## NLP Pipeline

```
Raw News Article
        │
        ▼
Text Cleaning
 • Lowercase
 • Remove punctuation
 • Remove numbers
 • Remove stopwords
 • Lemmatization
        │
        ▼
TF-IDF Vectorization
        │
        ▼
Linear Support Vector Machine
        │
        ▼
Prediction
Real / Fake
```

### Text Preprocessing

* Lowercase conversion
* Remove punctuation
* Remove numbers
* Remove stop words
* Lemmatization

### Feature Engineering

* TF-IDF Vectorizer
* TF-IDF with N-grams (best-performing model)

### Machine Learning Models Tested

* Multinomial Naive Bayes
* Linear SVM
* Linear SVM + TF-IDF
* **Linear SVM + TF-IDF N-grams (Final Model)**

The final deployed model was saved using **Joblib** together with the trained TF-IDF vectorizer.

---

# Results

The final model achieved strong performance on both validation and test datasets.

Evaluation metrics include:

* Accuracy
* Precision
* Recall
* F1-score
* Confusion Matrix

Example evaluation:

```
Accuracy: (generated in notebook)

Classification Report

Precision
Recall
F1-score

Confusion Matrix
```

The notebook also evaluates the model on unseen validation data and exports predictions to:

```
dataset/validation_predictions.csv
```

---

# Setup & Installation

Clone the repository

```bash
git clone https://github.com/Casildagsf/Ironhack-NLP-Challenge-Group-3-Fake_News

cd fake-news-nlp
```

Create a virtual environment (recommended)

```bash
python -m venv .venv
```

Activate the environment

Windows

```bash
.venv\Scripts\activate
```

Linux / macOS

```bash
source .venv/bin/activate
```

Install dependencies

```bash
pip install -r requirements.txt
```

Run the notebook

```bash
jupyter notebook
```

Run the Streamlit application

```bash
streamlit run app.py
```

---

# Project Structure

```
project/

│
├── requirements.txt
├── README.md
├── model_at_4_svm_tidf_joblib_predict.ipynb
│
├── dataset/
│   ├── data.csv
│   ├── validation_data.csv
│   └── validation_predictions.csv
│
├── models/
│   ├── mod4_joblib_svm_ngtfidf.pkl
│   └── mod4_joblib_svm_ngtfidf_vectorizer.pkl
│
├── streamlit/
│   ├── app.py
│
└── images/
    └── screenshots
    └── memes
```

---

# Tech Stack



---

# Future Improvements



---

# Authors

**Antonio Traquinas** - https://github.com/wtraquinas/

and 

**David Tayebwa** - https://github.com/kerondavid-debug/

AI Engineering | Machine Learning | NLP

---

## Acknowledgements

Special Thanks to Luis Junco and Tejal Bhatti, for the inestimable assistance.

This project was developed as part of the **IronHack AI Engineering Bootcamp**, demonstrating the complete machine learning workflow from data preprocessing to deployment of an interactive web application.

