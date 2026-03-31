<p align="center">
  <img src="https://img.shields.io/badge/SLDTS-Sign%20Language%20Detection-blue?style=for-the-badge&logo=accessibility&logoColor=white" alt="SLDTS" />
</p>

<h1 align="center">Sign Language Detection and Translation System</h1>
<p align="center">
  <strong>Real-time ASL recognition using MediaPipe, LSTM + Random Forest, and Gemini AI</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.8+-3776AB?style=flat-square&logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/TensorFlow-2.7-FF6F00?style=flat-square&logo=tensorflow&logoColor=white" />
  <img src="https://img.shields.io/badge/MediaPipe-Hands-red?style=flat-square" />
  <img src="https://img.shields.io/badge/Flask-Web%20App-000?style=flat-square&logo=flask&logoColor=white" />
  <img src="https://img.shields.io/badge/Gemini-AI%20Correction-4285F4?style=flat-square&logo=google&logoColor=white" />
</p>

---

## Overview

Real-time American Sign Language (ASL) detection and translation system. Captures hand gestures from a webcam, classifies them into ASL letters (A-Z) using a hybrid LSTM + Random Forest model, and converts detected signs into corrected text and speech.

## Features

- Real-time gesture recognition via webcam using **MediaPipe Hands** (21 keypoints)
- Hybrid classification: **LSTM neural network** + **Random Forest** ensemble
- Gemini AI-powered **text correction** for natural sentence formation
- **Text-to-Speech** output using gTTS
- **Multi-language translation** support
- **Spell correction** using SymSpell for noisy predictions
- Web-based interface with Flask

## Technical Approach

1. **Hand Landmark Detection** — MediaPipe extracts 21 3D hand keypoints at 30+ FPS
2. **Feature Engineering** — Landmark coordinates normalized and scaled
3. **Classification** — Keras LSTM model (`all-letter-model.h5`) with sklearn scaler/encoder
4. **Post-Processing** — SymSpell spell correction + Gemini AI sentence correction
5. **Output** — Text display + gTTS speech synthesis + translation

## Project Structure

```
SLDTS/
├── app.py                              # Flask application (main entry point)
├── all-letter-model.h5                 # Trained LSTM model weights
├── all-letter-model_scaler_and_encoder.pkl  # Feature scaler + label encoder
├── static/
│   ├── css/                            # Stylesheets
│   └── js/                             # Client-side webcam + prediction logic
├── templates/
│   └── index.html                      # Web interface
└── .gitignore
```

## Tech Stack

| Component | Technology |
|:----------|:-----------|
| **Detection** | MediaPipe Hands (21 keypoints) |
| **Model** | TensorFlow/Keras LSTM + scikit-learn Random Forest |
| **AI Correction** | Google Gemini 1.5 Pro |
| **Spell Check** | SymSpell |
| **Translation** | Python Translate |
| **TTS** | gTTS (Google Text-to-Speech) |
| **Backend** | Flask + Flask-CORS |
| **Frontend** | HTML/CSS/JavaScript |

## Getting Started

```bash
git clone https://github.com/rupeshbharambe24/SLDTS__Sign-Language-Detection-and-Translation.git
cd SLDTS__Sign-Language-Detection-and-Translation
pip install flask flask-cors opencv-python mediapipe tensorflow scikit-learn symspellpy gtts translate google-generativeai python-dotenv
```

Create a `.env` file:
```
GEMINI_API_KEY=your_gemini_api_key
```

Run:
```bash
python app.py
```

Open `http://localhost:5000` in your browser.
