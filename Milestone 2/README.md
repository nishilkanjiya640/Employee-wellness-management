<div align="center">

# 🌸 Mood Mentor
### *Employee Wellness Management Analytics*

<img src="https://img.shields.io/badge/Python-3.10+-blue?style=for-the-badge&logo=python" />
<img src="https://img.shields.io/badge/Streamlit-Web%20App-red?style=for-the-badge&logo=streamlit" />
<img src="https://img.shields.io/badge/NLP-Sentiment%20Analysis-green?style=for-the-badge" />
<img src="https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge" />

---

💙 Helping users understand their emotions through Artificial Intelligence.

</div>

# 🌍 Multilingual NLP Text Preprocessing Pipeline

## 📌 Project Objective

The objective of this project is to build a **Multilingual Natural Language Processing (NLP) Text Preprocessing Pipeline** capable of processing employee feedback written in different languages. The pipeline automatically detects the language, cleans and normalizes the text, removes stopwords, translates the content into English, performs lemmatization, analyzes sentiment, and identifies emotions. The processed data can then be used for employee wellness analysis and organizational insights.

---

## 🛠 NLP Pipeline Overview

The project follows the complete NLP preprocessing workflow shown below:

```text
Input Text
     │
     ▼
Language Detection
     │
     ▼
Text Cleaning
(Remove URLs, Emojis, Numbers, Punctuation)
     │
     ▼
Tokenization
     │
     ▼
Stopword Removal
(Language Specific)
     │
     ▼
Translation to English
     │
     ▼
Lemmatization
     │
     ▼
Sentiment Analysis (VADER)
     │
     ▼
Emotion Detection (BERT)
     │
     ▼
Final Structured Output
```

---

## 🚀 Technologies and Libraries Used

### Programming Language
- Python 3

### Development Environment
- Google Colab

### Frontend
- Streamlit

### Backend
- FastAPI
- Uvicorn

### Database
- PostgreSQL

### Authentication & Security
- JWT (JSON Web Token)
- bcrypt

### NLP Libraries
- langdetect
- ftfy
- emoji
- deep-translator
- spaCy
- stopwordsiso
- transformers
- vaderSentiment

### Other Libraries
- pandas
- matplotlib
- requests
- python-dotenv
- pyngrok
- torch
- accelerate

---

## ⚙ Google Colab Setup Instructions

### Step 1

Open the notebook in **Google Colab**.

### Step 2

Install the required libraries.

```python
!pip install streamlit psycopg2-binary PyJWT bcrypt \
python-dotenv email-validator pyngrok fastapi uvicorn \
python-multipart requests langdetect ftfy emoji \
deep-translator vaderSentiment spacy pandas matplotlib \
transformers accelerate torch stopwordsiso
```

### Step 3

Download the multilingual SpaCy model.

```python
!python -m spacy download xx_sent_ud_sm
```

### Step 4

Create the following Google Colab Secrets.

| Secret | Description |
|---------|-------------|
| DB_HOST | PostgreSQL Host |
| DB_PORT | Database Port |
| DB_NAME | Database Name |
| DB_USER | Database Username |
| DB_PASSWORD | Database Password |
| JWT_SECRET | JWT Secret Key |
| SMTP_EMAIL | Gmail Address |
| SMTP_APP_PASSWORD | Gmail App Password |
| NGROK_AUTHTOKEN | ngrok Authentication Token |

### Step 5

Run all notebook cells sequentially.

### Step 6

Launch:
- FastAPI Backend
- Streamlit Frontend

### Step 7

Upload a CSV or TXT file containing employee feedback and click **Run NLP Analysis**.

---

## 🔄 Preprocessing Workflow

The preprocessing pipeline performs the following operations:

### 1. Language Detection
Detects the language using **langdetect**.

### 2. Text Normalization
- Fix encoding issues
- Normalize Unicode text
- Convert text into a standard format

### 3. Text Cleaning
Removes:
- URLs
- Email IDs
- HTML Tags
- Numbers
- Punctuation
- Extra Spaces
- Emojis

### 4. Tokenization
Splits sentences into meaningful words.

### 5. Stopword Removal
Removes language-specific stopwords using **stopwordsiso**.

### 6. Translation
Translates multilingual text into English using **Deep Translator**.

### 7. Lemmatization
Converts words into their root form using **spaCy**.

### 8. Sentiment Analysis
Performs sentiment analysis using **VADER**.

Possible outputs:
- Positive
- Neutral
- Negative

### 9. Emotion Detection
Detects emotions using a Transformer (BERT) model.

Possible emotions:
- Joy
- Anger
- Sadness
- Fear
- Love
- Surprise

---

## 📥 Sample Input

---

## 📤 Sample Output



## 📊 Observations

- Successfully processes multilingual employee feedback.
- Automatically detects the input language.
- Removes unwanted characters and noisy text.
- Supports language-specific stopword removal.
- Translates multilingual content into English.
- Performs lemmatization for better NLP analysis.
- Accurately predicts sentiment (Positive, Neutral, Negative).
- Detects emotions using a Transformer-based model.
- Generates structured output suitable for dashboards and analytics.
- Can be integrated into HR systems, employee wellness platforms, and chatbot applications.

---

## 📂 Project Structure
Milestone2/
├── NLP_Preprocessing_Pipeline.ipynb
├── README.md
└── Screenshots/
`
```
---

## 🎯 Future Enhancements

Sentiment Analysis
Emotion Classification
Employee Feedback Analysis
Mental Wellness Prediction
AI-powered Employee Wellness Dashboard

---
## Conclusion

This milestone successfully implements a complete multilingual NLP preprocessing pipeline capable of transforming raw employee feedback into structured text suitable for sentiment and emotion analysis.


