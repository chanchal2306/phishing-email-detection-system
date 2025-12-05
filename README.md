📧🔐 Email & URL Phishing Detection System
**Machine Learning–Powered Security Project

Author: Chanchal 

🚀 Overview

This project presents a Machine Learning–based Phishing Detection System capable of identifying malicious emails and URLs using:

47+ handcrafted URL features

Engineered email text features

TF-IDF text vectorization

Random Forest classification

Real-time inference using Flask

Interactive Web UI with probability scores

The system predicts whether an input email is LEGITIMATE or PHISHING, along with confidence percentages, extracted features, and suspicious keyword highlights.

🧠 Motivation

Phishing remains a major cybersecurity threat, leading to:

Financial loss

Identity theft

Password compromise

Organizational data breaches

Manual detection is unreliable — hence, an automated ML system is essential.

🎯 Project Objectives

Build a robust dataset combining URL and email features

Engineer multi-level features (URL, domain, text, HTML content)

Train a high-accuracy ML model to detect phishing

Deploy a real-time Flask-based inference pipeline

Build an intuitive UI for testing any suspicious email

📂 Project Structure
├── app/
│   ├── app.py                # Flask backend
│   ├── templates/
│   │   ├── index.html
│   │   ├── result.html
│   ├── static/
│       ├── styles.css
│       ├── favicon.ico
│
├── src/
│   ├── preprocessing/
│   │   ├── url_feature_extractor.py
│   │   ├── feature_extractor.py
│   │   ├── text_utils.py
│   ├── models/
│   │   ├── best_tuned_model.joblib
│
├── data/
│   ├── raw/
│   ├── clean_dataset.csv
│
├── notebook/
│   ├── 01_data_cleaning.ipynb
│   ├── 02_feature_engineering.ipynb
│   ├── 03_model_training.ipynb
│   ├── 04_hyperparameter_tuning.ipynb
│   ├── 05_evaluation.ipynb
│
├── rebuild_clean_dataset.py
├── retrain_pipeline.py
├── deep_debug.py
├── token_debug.py
├── README.md

🏗 System Architecture

User enters email text in UI

Flask backend receives email

Extract URL from email (if present)

Compute 47 URL + engineered features

Construct TEXT column (training-style)

Model predicts phishing / legitimate + probabilities

UI displays results + highlights suspicious words

📊 Dataset Description

~10,000 samples

Features include:

URL-based lexical patterns

Domain-based features

HTML features

Email text body

Engineered features (uppercase ratio, digits count, #links)

Label:

1 → Phishing

0 → Legitimate

🔧 Feature Engineering
✔ URL-based features (47 total)

Examples:

NumDots

SubdomainLevel

UrlLength

IpAddress

NumSensitiveWords

RandomString

EmbeddedBrandName

PathLength

QueryLength

✔ Email Text Features

Number of digits

Number of links

Uppercase ratio

HTML tag presence

Suspicious domain inside body

Subject exclamation

✔ Final TEXT Feature

Training used:

df["TEXT"] = df.astype(str).agg(" ".join, axis=1)


So inference replicates this exact structure.

⚙ ML Pipeline

Preprocessor

StandardScaler() → numeric features

TfidfVectorizer() → TEXT feature

Model

RandomForestClassifier

Tuned via GridSearchCV

📈 Model Performance
Metric	Score
Accuracy	97–99%
Precision	98%
Recall	97%
F1-score	97%

ROC-AUC Curve: Excellent separability

Confusion Matrix shows high TP and TN

🖥 Flask App Workflow

User enters email on index.html

/predict receives POST request

Features generated → Model → Probabilities

Results shown on result.html

🖼 UI Screenshots

🎉 Include your provided images here:

Homepage UI

Legitimate prediction screen

Phishing example result

Debug and pipeline screenshots

(Users cloning repo will see actual screenshots)

▶ Running the Project
1️⃣ Install Requirements
pip install -r requirements.txt

2️⃣ Run Flask App
cd app
python app.py

3️⃣ Open in Browser
http://127.0.0.1:5000/

🔄 Retraining

To rebuild dataset:

python rebuild_clean_dataset.py


To re-train full ML pipeline:

python retrain_pipeline.py

🧪 Debug Utilities
deep_debug.py

Prints:

Extracted features

TF-IDF behavior

SHAP values

Pipeline structure

token_debug.py

Shows:

Token presence

Preprocessing behavior

Why misclassification happens
