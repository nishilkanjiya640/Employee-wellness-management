# 🧠 MoodMentor – AI-Powered Emotional Wellness Assistant

MoodMentor is an **AI-powered emotional wellness application** designed to help users understand, track, and reflect on their emotional well-being.

The application allows users to record their mood manually, write journal entries, analyze emotions from text, view mood trends, receive personalized wellness recommendations, and communicate with an AI wellness assistant.

The project combines **Natural Language Processing (NLP), Sentiment Analysis, Emotion Detection, Generative AI, Authentication, Database Management, and Data Visualization** into one web application.

---

## 📌 Project Objective

The main objective of MoodMentor is to provide an easy-to-use platform that can:

* Track a user's daily mood.
* Analyze emotions from journal text.
* Detect the language of user input.
* Clean and preprocess text.
* Translate multilingual text into English.
* Perform sentiment analysis.
* Detect emotions using a BERT-based model.
* Provide personalized wellness recommendations.
* Provide an AI-powered wellness chat assistant.
* Store mood and journal information securely.
* Display emotional trends through charts and dashboards.
* Generate PDF and CSV wellness reports.
* Provide managers with an employee wellness overview.

---

## ✨ Main Features

### 1. User Authentication

The application provides a complete authentication system.

Users can:

* Create an account.
* Select Employee or Manager role.
* Login securely.
* Verify their email using OTP.
* Reset their password using OTP.
* Logout from the application.

Passwords are protected using **bcrypt**, while authentication sessions use **JWT tokens**.

The application stores user accounts and authentication information in PostgreSQL.

---

### 2. Daily Mood Tracking

Employees can manually select their current mood.

The application supports:

* 😊 Happy
* 😐 Neutral
* 😢 Sad
* 😫 Stress
* 😠 Angry
* 😨 Fear

The selected mood is stored in the PostgreSQL database with the user's ID and date.

---

### 3. Mood Calendar

The Home page provides a calendar that displays the user's mood history.

Each day can show:

* Date
* Mood
* Emoji
* Mood color
* Recorded time

Users can navigate between previous and next months.

---

### 4. Journal Analysis

Users can write about how they are feeling in the Journal section.

Example:

> "I am feeling stressed because I have a lot of work today."

The application sends the text to the FastAPI backend for NLP processing.

The system then performs:

```text
User Text
   ↓
Text Normalization
   ↓
Language Detection
   ↓
Text Cleaning
   ↓
Tokenization
   ↓
Stopword Removal
   ↓
Translation to English
   ↓
Lemmatization
   ↓
Sentiment Analysis
   ↓
Emotion Detection
   ↓
Recommendation
   ↓
Dashboard / Database
```

---

## 🌐 Multilingual NLP Pipeline

MoodMentor supports multilingual text processing.

The notebook includes language handling for languages such as:

* English
* Hindi
* Marathi
* Gujarati
* Telugu
* Kannada
* Tamil
* Malayalam
* Bengali
* French
* German
* Spanish
* Portuguese
* Arabic
* Chinese
* Japanese
* Korean
* Russian

The pipeline uses language detection and translation so that the analysis can be performed consistently.

The NLP pipeline is defined in `nlp_pipeline.py`.

---

## 🧹 Text Preprocessing

The application performs several preprocessing operations.

### Text Normalization

The `ftfy` library is used to fix problematic text encoding.

### URL Removal

URLs such as:

```text
https://example.com
```

are removed.

### Email Removal

Email addresses are removed from the text.

### Mention and Hashtag Removal

Mentions and hashtags are cleaned.

### Emoji Processing

Emojis are identified and stored separately, while emojis are removed from the text used for NLP processing.

### Tokenization

The text is divided into individual tokens.

### Stopword Removal

Language-specific stopwords are removed using `stopwordsiso`.

### Translation

The preprocessed text is translated to English using `GoogleTranslator`.

### Lemmatization

The translated English text is lemmatized using spaCy.

The notebook explicitly implements this pipeline as:

```text
normalize
→ detect language
→ clean
→ tokenize
→ stopword-filter
→ translate to English
→ lemmatize
→ sentiment
→ emotion
```

---

## 😊 Sentiment Analysis

MoodMentor uses **VADER Sentiment Analysis** to determine the overall sentiment of the text.

The sentiment categories are:

* Positive
* Negative
* Neutral

The VADER compound score ranges from approximately:

```text
-1 → Negative
 0 → Neutral
+1 → Positive
```

The application uses these thresholds:

```text
Compound >= 0.05  → Positive

Compound <= -0.05 → Negative

Otherwise          → Neutral
```

The sentiment scores are displayed in the Journal and Dashboard sections.

---

## 😃 Emotion Detection

The project uses a BERT-based emotion classification model:

```text
bhadresh-savani/bert-base-go-emotion
```

The model produces multiple emotion scores.

These are mapped into six application-level emotions:

```text
Happy
Sad
Stress
Angry
Fear
Neutral
```

For example:

```text
Joy
Love
Excitement
Gratitude
Optimism
        ↓
     Happy
```

Similarly, sadness-related emotions are mapped to `Sad`, nervousness and confusion to `Stress`, and anger-related emotions to `Angry`.

## The final emotion is selected based on the highest aggregated emotion score.

## 🤖 AI Wellness Chat

MoodMentor includes an AI wellness chatbot.

The chatbot uses:

```text
Qwen/Qwen2.5-0.5B-Instruct
```

The chatbot is designed to provide:

* Supportive responses
* General coping suggestions
* Encouragement
* Non-judgmental conversation

The system prompt specifically prevents the assistant from presenting itself as a doctor or therapist.

The chatbot also checks for crisis-related keywords before generating an AI response.

---

## 💡 Wellness Recommendation System

After emotion and sentiment analysis, MoodMentor provides wellness recommendations.

Recommendations depend on the detected emotion and confidence.

For example:

```text
Happy
   ↓
Positive / encouraging recommendation

Sad
   ↓
Journaling / breathing / support recommendation

Stress
   ↓
Break / breathing / workload recommendation

Angry
   ↓
Pause / step away / reflection recommendation

Fear
   ↓
Grounding / breathing / support recommendation
```

For negative emotions, the system uses three confidence levels:

```text
Low confidence
    ↓
Light/general suggestion

Medium confidence
    ↓
Matched coping suggestion

High confidence
    ↓
More structured/professional support suggestion
```

---

## 📊 Employee Dashboard

Employees have access to a personal dashboard.

The dashboard provides:

* Mood distribution
* Mood trend over time
* Detected emotions
* VADER sentiment split
* Recent activity
* Date filtering
* Mood filtering
* Source filtering
* Journal text search

The dashboard also provides report export functionality.

---

## 📈 Mood Visualization

The application uses charts to visualize emotional data.

Implemented visualizations include:

### Mood Distribution

A donut chart showing the distribution of moods.

### Mood Trend

A line chart showing how mood changes over time.

### Emotion Distribution

A bar chart displaying detected emotions from journal entries.

### Sentiment Distribution

A chart displaying:

* Positive
* Negative
* Neutral

sentiment results.

---

## 📄 Report Generation

Users can export their emotional wellness data.

Supported formats:

### PDF

The PDF report contains:

* Username
* Selected date range
* Mood summary
* Wellness recommendation
* Mood entries
* Emotion
* Confidence
* Data source

### CSV

The CSV export contains fields such as:

```text
Date
Time
Mood
Emotion
Confidence
Source
Journal Text
```

The notebook implements both PDF and CSV export functionality.

---

## 👨‍💼 Manager Dashboard

Managers have a separate role in the application.

Managers can view:

* Latest mood for each employee
* Employee name
* Employee email
* Date
* Time
* Mood
* Emotion

Managers can search employees and filter results by mood.

They can also export employee wellness information as CSV.

The manager dashboard additionally provides a **team mood trend for the last 30 days**.

---

## 🗄️ Database

The project uses **PostgreSQL** as its database.

The notebook creates the following major tables:

### Users

Stores:

* User ID
* Username
* Email
* Password hash
* Verification status
* Role

### OTP Codes

Stores:

* Email
* OTP code
* Purpose
* Expiration time
* Used status

### Mood Logs

Stores:

* User ID
* Mood date
* Sentiment
* Emotion
* Compound score
* Confidence
* Journal text
* Source
* Creation time








