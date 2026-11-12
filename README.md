# Sentiment Analysis 

An end-to-end deep learning NLP project that reads the mood inside a sentence. A Bidirectional GRU (BiGRU) model classifies the emotion of any text into six categories, and a FastAPI web app serves real-time predictions through an interactive interface.

**Live Demo:** https://sentiment-analysis-6-rlws.onrender.com

> The app is hosted on Render's free tier, so the first request may take 30-60 seconds while the server wakes up.

---

## Table of Contents

- [Features](#features)
- [Tech Stack](#tech-stack)
- [How It Works](#how-it-works)
- [Emotion Categories](#emotion-categories)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Running the App](#running-the-app)
- [API Usage](#api-usage)
- [Deployment](#deployment)
- [Future Improvements](#future-improvements)
- [Author](#author)

---

## Features

- Deep learning NLP model built on a Bidirectional GRU (BiGRU).
- Text preprocessing pipeline: cleaning, tokenization, and sequence padding.
- Real-time emotion predictions with confidence scores.
- Probability distribution for all six emotion categories.
- REST API built with FastAPI.
- Clean, interactive web interface (Moodline).
- Automatic model and tokenizer loading at startup.
- Deployed live on Render.

## Tech Stack

| Area | Tools |
|------|-------|
| Language | Python |
| Deep Learning | TensorFlow / Keras, BiGRU |
| NLP | Tokenizer, Sequence Padding, Text Cleaning |
| Data Processing | NumPy |
| Backend | FastAPI, Uvicorn |
| Frontend | HTML, CSS, JavaScript |
| Model Storage | Keras, Pickle |
| Deployment | Render |
| Version Control | Git, GitHub |

## How It Works

```text
Raw Text
   |
   v
Text Cleaning
   |
   v
Tokenization
   |
   v
Sequence Padding
   |
   v
Embedding
   |
   v
Bidirectional GRU (BiGRU)
   |
   v
Dense Layer
   |
   v
Softmax
   |
   v
Emotion Prediction
```

1. **Preprocessing:** Text is converted into lowercase, cleaned of URLs, symbols and extra spaces, then converted into integer sequences and padded to a fixed length of 50.

2. **Model:** An Embedding layer feeds a Bidirectional GRU, which reads the sentence in both directions to capture contextual information. The model uses a Softmax output layer to generate probabilities for six emotion categories.

3. **Serving:** The trained model and tokenizer are loaded once at startup. The `/predict` endpoint returns the predicted emotion, confidence score, and probabilities for all emotion categories.

## Emotion Categories

The model classifies text into six emotion categories:

| Emotion | Description |
|---------|-------------|
| Sadness | Expresses sadness or unhappiness |
| Joy | Expresses happiness or excitement |
| Love | Expresses affection or love |
| Anger | Expresses anger or frustration |
| Fear | Expresses fear or anxiety |
| Surprise | Expresses surprise or unexpected feelings |

## Project Structure

```text
Sentiment_Analysis/
│
├── Artifacts/
│   ├── BiGRU_Model.keras
│   └── tokenizer.pkl
│
├── static/
│   ├── index.html
│   ├── style.css
│   └── script.js
│
├── main.py
├── requirements.txt
├── runtime.txt
└── README.md
```

### File Descriptions

- **main.py:** FastAPI application containing model loading, text preprocessing, and prediction logic.
- **Artifacts/:** Stores the trained BiGRU model and tokenizer.
- **BiGRU_Model.keras:** Saved trained deep learning model.
- **tokenizer.pkl:** Saved tokenizer used for text tokenization.
- **static/:** Contains frontend files.
- **index.html:** Moodline web interface.
- **requirements.txt:** Contains project dependencies.
- **.python-version:** Specifies the Python version.
- **runtime.txt:** Python runtime configuration, if used.

## Installation

### Prerequisites

- Python 3.11
- Git
- VS Code
- pip

### Step 1: Clone the Repository

```bash
git clone https://github.com/Anchal674/Sentiment_Analysis.git
```

### Step 2: Navigate to the Project Directory

```bash
cd Sentiment_Analysis
```

### Step 3: Create a Virtual Environment

```bash
python -m venv venv
```

### Step 4: Activate the Virtual Environment

**Windows:**

```bash
venv\Scripts\activate
```

**Linux / macOS:**

```bash
source venv/bin/activate
```

### Step 5: Upgrade pip

```bash
python -m pip install --upgrade pip
```

### Step 6: Install Dependencies

```bash
pip install -r requirements.txt
```

### Requirements

The project dependencies are listed in `requirements.txt`.

```text
fastapi==0.115.0
uvicorn[standard]==0.30.6
pydantic==2.9.2
tensorflow-cpu==2.17.0
numpy==1.26.4
h5py==3.11.0
```

## Running the App

Start the FastAPI server using Uvicorn:

```bash
uvicorn main:app --reload
```

The application will be available at:

http://127.0.0.1:8000

Open this URL in your browser to access the Moodline interface.

## API Usage

The project provides the following API endpoints:

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/` | Opens the web interface |
| GET | `/health` | Checks server and model status |
| POST | `/predict` | Predicts the emotion of input text |

### Prediction Endpoint

**Endpoint:** `POST /predict`

**Request Body:**

```json
{
    "text": "I am feeling very happy today"
}
```

**Example Response:**

```json
{
    "text": "I am feeling very happy today",
    "predicted_emotion": "joy",
    "confidence": 0.95,
    "all_probabilites": {
        "sadness": 0.01,
        "joy": 0.95,
        "love": 0.01,
        "anger": 0.01,
        "fear": 0.01,
        "surprise": 0.01
    }
}
```

> Note: The response values are illustrative examples. Actual predictions depend on the trained model.

### API Documentation

FastAPI automatically generates interactive API documentation.

- Swagger UI: http://127.0.0.1:8000/docs
- ReDoc: http://127.0.0.1:8000/redoc

## Deployment

The application is deployed on Render.

### Build Command

```bash
pip install -r requirements.txt
```

### Start Command

```bash
uvicorn main:app --host 0.0.0.0 --port $PORT
```

### Deployment Steps

1. Push the project code to GitHub.
2. Log in to Render.
3. Create a new Web Service.
4. Connect the GitHub repository.
5. Select the Python runtime.
6. Configure the build and start commands.
7. Set the Python version to 3.11.11.
8. Deploy the application.

## Future Improvements

- Improve model performance through hyperparameter tuning.
- Experiment with LSTM and Transformer architectures.
- Add support for more emotion categories.
- Improve text preprocessing.
- Add prediction history and analytics.
- Enhance the frontend user experience.
- Explore multilingual emotion classification.

## Author

**Anchal Devi**

GitHub: https://github.com/Anchal674

Project: Moodline – Sentiment Analysis with BiGRU

---
