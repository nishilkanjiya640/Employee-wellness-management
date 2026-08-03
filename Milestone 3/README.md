# 😊 MoodMentor – Multilingual Employee Emotion Detection & Sentiment Analysis

> An AI-powered platform that analyzes multilingual employee feedback using NLP and Deep Learning to detect emotions, perform sentiment analysis, and provide actionable workplace insights.

---

## 📌 Project Objective

MoodMentor is designed to help organizations understand employee well-being through automated emotion and sentiment analysis.

The system accepts employee feedback in multiple languages, detects the language, translates it into English (if required), predicts the overall sentiment, identifies the dominant emotion, calculates the prediction confidence, and stores the results securely for dashboard visualization.

---

## 🚀 Features

- 🌍 Multilingual Feedback Support
- 🔍 Automatic Language Detection
- 🌐 English Translation
- 🧹 Text Preprocessing
- 😊 Emotion Detection
- 📊 Sentiment Analysis
- 📈 Confidence Score
- 👤 JWT Authentication
- 📧 Email OTP Verification
- 📂 CSV Upload
- 📉 Employee Mood Dashboard
- 📜 Mood History

---

# 🛠 Tech Stack

| Category | Technology |
|-----------|------------|
| Frontend | Streamlit |
| Backend | FastAPI |
| Database | PostgreSQL |
| NLP | spaCy, LangDetect, VADER |
| Translation | Google Translator |
| Deep Learning | HuggingFace Transformers |
| Emotion Model | BERT GoEmotions |
| Chat Assistant | Qwen 2.5 |
| Authentication | JWT |

---

# 🧠 Model Used

| Task | Model |
|------|-------|
| Language Detection | LangDetect |
| Translation | Google Translator API |
| Text Cleaning | Regex + Emoji Removal |
| Tokenization | spaCy |
| Lemmatization | spaCy |
| Sentiment Analysis | VADER |
| Emotion Detection | BERT GoEmotions (`bhadresh-savani/bert-base-go-emotion`) |
| Wellness Chat | Qwen 2.5-0.5B-Instruct |

---

# ⚙️ Emotion Detection Pipeline

```text
Employee Feedback
        │
        ▼
Language Detection
        │
        ▼
Translation (if required)
        │
        ▼
Text Cleaning
        │
        ▼
Tokenization
        │
        ▼
Stopword Removal
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
Confidence Score
        │
        ▼
Store Results in PostgreSQL
        │
        ▼
Dashboard Visualization
```

---

# 📊 Confidence Score Calculation

The confidence score represents how certain the model is about the predicted emotion.

```text
Confidence Score = Highest Softmax Probability × 100
```

### Example

| Emotion | Probability |
|----------|------------:|
| Joy | 0.93 |
| Happy | 0.04 |
| Neutral | 0.02 |
| Sad | 0.01 |

**Predicted Emotion:** Joy

**Confidence Score:** **93%**

---

# 😊 Sentiment Analysis

Sentiment is computed using the **VADER Sentiment Analyzer**.

| Compound Score | Sentiment |
|----------------|-----------|
| ≥ 0.05 | Positive |
| -0.05 to 0.05 | Neutral |
| ≤ -0.05 | Negative |

### Example

**Input**

```text
I really enjoyed working with my team today.
```

**Output**

```text
Sentiment : Positive
Compound Score : 0.84
```

---

# 🗄 Database Schema

## Users

| Column | Type |
|---------|------|
| id | SERIAL PRIMARY KEY |
| username | VARCHAR |
| email | VARCHAR |
| password_hash | VARCHAR |
| is_verified | BOOLEAN |
| role | VARCHAR |

---

## Mood Logs

| Column | Type |
|---------|------|
| id | SERIAL PRIMARY KEY |
| user_id | INTEGER |
| feedback | TEXT |
| detected_language | VARCHAR |
| translated_text | TEXT |
| sentiment | VARCHAR |
| emotion | VARCHAR |
| confidence | FLOAT |
| created_at | TIMESTAMP |

---

## OTP Verification

| Column | Type |
|---------|------|
| email | VARCHAR |
| otp | VARCHAR |
| expiry_time | TIMESTAMP |

---

# 🔗 API Endpoints

| Method | Endpoint | Description |
|----------|----------|-------------|
| GET | `/health` | Health Check |
| POST | `/register` | Register User |
| POST | `/login` | User Login |
| POST | `/verify-otp` | Verify Email OTP |
| POST | `/predict` | Predict Emotion & Sentiment |
| POST | `/upload` | Upload CSV |

---

# 📥 Sample Input

```text
I feel motivated after today's meeting.
```

---

# 📤 Sample Output

    "language": "English",
    "translated_text": "I feel motivated after today's meeting.",
    "sentiment": "Positive",
    "compound_score": 0.87,
    "emotion": "Joy",
    "confidence": 94.6

```
# 📈 Observations

- Supports multilingual employee feedback.
- Sentiment (VADER) and emotion (BERT) can disagree on short/ambiguous text since they measure different things — this is expected.
- Shorter entries tend to give lower confidence scores.


