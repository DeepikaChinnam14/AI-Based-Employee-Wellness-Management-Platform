# MoodMentor – AI-Powered Employee Wellness Management Platform

An AI-driven employee wellness platform that helps users monitor their emotional well-being, analyze their mood and journal entries, and receive personalized wellness recommendations.

MoodMentor brings together **Natural Language Processing (NLP), sentiment analysis, emotion detection, wellness assessment, personalized recommendations, and conversational support** in one application.

---

## 📌 Project Overview

Employee emotional well-being can influence productivity, engagement, and overall workplace satisfaction. MoodMentor provides a simple platform for understanding wellness patterns through AI-based analysis.

The system allows employees to:

* Register and securely log in
* Verify their account through email OTP
* Record and track their moods
* Write journal entries for emotional analysis
* Analyze text and uploaded feedback files
* Detect sentiment and emotions from text
* Complete a wellness questionnaire
* Receive personalized wellness recommendations
* View mood and wellness history
* Interact with an AI wellness assistant

Managers can also access **aggregated wellness insights** to understand overall employee wellness trends.

---

## 🎯 Objectives

* Analyze employee text and journal entries using AI and NLP.
* Identify sentiment and emotional states from user input.
* Track changes in employee mood over time.
* Provide personalized wellness recommendations.
* Assess employee wellness using questionnaire responses.
* Present useful wellness trends through visual analytics.
* Provide conversational wellness support.
* Protect employee information using secure authentication and database management.

---

## ✨ Key Features

### 👤 Employee Wellness

* Employee registration and login
* Email OTP verification
* Forgot password and OTP-based reset
* Employee profile management
* Mood logging
* Mood history and calendar
* Wellness questionnaire
* Wellness score and category
* Personalized recommendations

### 🧠 AI & NLP Analysis

MoodMentor uses a multilingual NLP pipeline to process and analyze employee text.

The pipeline includes:

* Language detection
* Text cleaning and normalization
* Emoji handling
* Text correction
* Translation support
* Sentiment analysis
* Emotion classification
* Confidence score generation
* Wellness recommendation generation

The project uses tools such as **Hugging Face Transformers, PyTorch, VADER Sentiment, LangDetect, Deep Translator, spaCy, FTFY, Emoji, and StopwordsISO**.

### 📂 Text / CSV Analysis

Users can provide text or upload supported **CSV/TXT files** containing employee feedback.

The backend processes the input through the NLP pipeline and returns:

* Detected language
* Sentiment
* Emotion
* Confidence score
* Wellness recommendation

### 💬 AI Wellness Assistant

The system provides an AI-based wellness assistant that can respond according to the employee's wellness context and provide supportive suggestions.

### 📊 Wellness Analytics

The application provides insights such as:

* Mood trends
* Emotion distribution
* Sentiment trends
* Questionnaire scores
* Wellness categories
* Individual wellness history
* Team-level wellness patterns
* Personalized recommendations
* Visual analytics

### 📄 Reports & Export

The system supports:

* PDF wellness reports
* CSV data export
* Questionnaire history export
* Wellness analysis reports

---

# 🏗️ System Architecture

```text
                    ┌───────────────────────┐
                    │   Employee / Manager  │
                    │          UI           │
                    └───────────┬───────────┘
                                │
                                ▼
                    ┌───────────────────────┐
                    │      Streamlit        │
                    │       Frontend        │
                    └───────────┬───────────┘
                                │
                           REST / HTTP
                                │
                                ▼
                    ┌───────────────────────┐
                    │       FastAPI         │
                    │        Backend        │
                    └───────────┬───────────┘
                                │
                 ┌──────────────┴──────────────┐
                 ▼                             ▼
       ┌──────────────────┐          ┌──────────────────┐
       │   NLP Pipeline   │          │ Authentication   │
       │                  │          │                  │
       │ Language         │          │ JWT              │
       │ Translation      │          │ Bcrypt            │
       │ Sentiment        │          │ OTP              │
       │ Emotion          │          │ Account Security │
       └────────┬─────────┘          └──────────────────┘
                │
                ▼
       ┌────────────────────┐
       │    PostgreSQL      │
       │      Database      │
       │                    │
       │ Users              │
       │ Mood Records       │
       │ OTP Data           │
       │ Journal Entries    │
       │ Questionnaires     │
       └────────────────────┘
```

---

# 🛠️ Technology Stack

## Programming Language

* **Python 3.11**

## Frontend

* **Streamlit**
* HTML/CSS
* Matplotlib
* Seaborn

Streamlit is used to build the interactive user interface and dashboards.

## Backend

* **FastAPI**
* **Uvicorn**
* REST APIs
* Pydantic
* Python Requests

FastAPI handles communication between the frontend, NLP modules, authentication services, and database.

## Database

* **PostgreSQL**
* **psycopg2-binary**

PostgreSQL stores user information, authentication data, mood records, journal information, questionnaire responses, and related wellness data.

## AI / NLP

* **Hugging Face Transformers**
* **PyTorch**
* **spaCy**
* **VADER Sentiment**
* **LangDetect**
* **Deep Translator**
* **FTFY**
* **Emoji**
* **StopwordsISO**

## Data Processing & Visualization

* **Pandas**
* **Scikit-learn**
* **Matplotlib**
* **Seaborn**

## Authentication & Security

* **JWT / PyJWT**
* **Bcrypt**
* Email OTP verification
* Password reset through OTP
* Failed-login tracking
* Account lockout
* Input sanitization
* Environment-variable based secret management

## Email Service

* Gmail SMTP
* Python `smtplib`
* Gmail App Password

Email services are used for account verification and password-reset OTPs.

## Reporting

* **ReportLab**
* CSV export

## Deployment

* **Docker**
* Docker Compose
* Streamlit container
* FastAPI container

## CI/CD

* **GitHub Actions**
* Python syntax checks
* Dependency installation
* Docker image builds

---

# 🔐 Authentication & Security

MoodMentor uses multiple mechanisms to protect user accounts and application data:

* Bcrypt password hashing
* JWT-based authentication
* Token expiration
* Email OTP verification
* OTP-based password reset
* Failed login attempt monitoring
* Temporary account lockout
* Input sanitization
* Environment variables for confidential values
* Protected PostgreSQL credentials

Database passwords, JWT secrets, SMTP credentials, and other sensitive configuration values are stored outside the source code using environment variables.

---

# 🗄️ Database

MoodMentor uses **PostgreSQL** for persistent data storage.

### Users

Stores information such as:

* User ID
* Username
* Email
* Password hash
* Verification status
* User role
* Failed login attempts
* Account lockout information
* Profile information

### OTP Records

Stores:

* Email
* OTP
* OTP purpose
* Expiration time
* Verification/used status

### Mood & Journal Records

Stores:

* Employee/User ID
* Mood date
* Journal text
* Detected emotion
* Sentiment
* Compound sentiment score
* Confidence score
* Input source
* Timestamp

### Questionnaire Responses

Stores:

* Employee/User ID
* Questionnaire answers
* Total score
* Maximum score
* Wellness category
* Support preferences
* Submission timestamp

---

# 📋 Wellness Questionnaire

The wellness questionnaire evaluates different aspects of an employee's current well-being, including:

* Current mood
* Overall mood
* Stress level
* Factors affecting mood
* Energy level
* Sleep quality
* Preferred support
* Willingness to talk
* Frequency of negative emotions
* Confidence in managing emotions
* Immediate support requirements
* Recommendation preferences

Based on the score, users can be grouped into categories such as:

```text
Thriving
Doing Well
Needs Attention
At Risk
```

The application uses the resulting category and support preferences to provide suitable wellness recommendations.

---

# 📈 Analytics

MoodMentor can generate insights from employee wellness information, including:

* Individual mood patterns
* Emotion distribution
* Sentiment changes
* Questionnaire performance
* Wellness categories
* Common mood-related factors
* Preferred support types
* Overall team wellness trends

These insights can help visualize wellness patterns while maintaining appropriate access to employee information.

---

# ⚙️ Main Dependencies

```text
streamlit
fastapi
uvicorn
python-multipart
requests
psycopg2-binary
PyJWT
bcrypt
python-dotenv
email-validator
langdetect
ftfy
emoji
deep-translator
vaderSentiment
spacy
pandas
matplotlib
seaborn
transformers
accelerate
torch
stopwordsiso
reportlab
bleach
```

The complete dependency list is maintained in `requirements.txt`.

---

# ▶️ Running the Project

## 1. Clone the Repository

```bash
git clone <your-repository-url>
cd MoodMentor
```

## 2. Install Dependencies

```bash
pip install -r requirements.txt
```

## 3. Configure Environment Variables

Create a `.env` file and add the required PostgreSQL, JWT, SMTP, and backend configuration.

Example:

```env
DB_HOST=your-postgres-host
DB_PORT=5432
DB_NAME=your-database-name
DB_USER=your-database-user
DB_PASSWORD=your-database-password

JWT_SECRET=your-secret-key

SMTP_EMAIL=your-email@gmail.com
SMTP_APP_PASSWORD=your-gmail-app-password

BACKEND_URL=http://localhost:8000
```

**Do not upload your actual `.env` file or credentials to GitHub.**

---

# ▶️ Start the Backend

Run the FastAPI server:

```bash
uvicorn backend:app --host 0.0.0.0 --port 8000
```

Backend:

```text
http://localhost:8000
```

Health check:

```text
http://localhost:8000/health
```

---

# ▶️ Start the Frontend

Run Streamlit:

```bash
streamlit run app.py
```

The frontend will normally be available at:

```text
http://localhost:8501
```

---

# 🐳 Docker Deployment

The project can also be executed using Docker and Docker Compose.

```bash
docker compose up --build
```

Services:

```text
Frontend → Streamlit → Port 8501
Backend  → FastAPI   → Port 8000
```

The frontend communicates with the FastAPI backend through the configured Docker network.

---

# 🔄 CI/CD Pipeline

GitHub Actions can be used to automatically:

1. Set up Python 3.11
2. Install project dependencies
3. Check Python modules for compilation/syntax issues
4. Build the backend Docker image
5. Build the frontend Docker image

This helps detect code and build problems before deployment.

---

# 📸 Screenshots

Application screenshots can be placed inside the `Screenshots` folder.

Recommended screenshots include:

* Login / Registration
* OTP Verification
* Employee Dashboard
* Mood Analysis
* Journal Analysis
* Wellness Questionnaire
* AI Wellness Assistant
* CSV/TXT Analysis
* Analytics Dashboard
* Wellness Recommendations
* Database Structure

---

# 🔒 Privacy & Responsible Use

MoodMentor is designed as an **employee wellness support and analytics application**, not as a medical or clinical diagnostic system.

AI-generated emotion, sentiment, and wellness results should be considered supportive indicators rather than professional medical diagnoses.

Employee wellness information should be handled responsibly with appropriate access controls, privacy practices, and organizational consent.

---

# 🔮 Future Enhancements

Possible improvements include:

* More advanced wellness dashboards
* Improved emotion classification models
* Real-time wellness monitoring
* Enhanced multilingual NLP support
* Smarter recommendation models
* Anonymous organization-level analytics
* Cloud deployment
* Expanded role-based administration
* Additional wellness metrics
* Integration with HR systems

---

# 👨‍💻 Project

## MoodMentor

**AI-Powered Emotional Tone Analyzer and Well-Being Recommendation System**

### Core Technologies

**Python • Streamlit • FastAPI • PostgreSQL • NLP • Hugging Face Transformers • PyTorch • VADER • JWT • Bcrypt • Docker • GitHub Actions**

---

## ⭐ Project Highlights

> **MoodMentor combines AI-based emotion and sentiment analysis, wellness assessment, personalized recommendations, secure authentication, analytics, and PostgreSQL data management to support employee well-being through a single platform.**
