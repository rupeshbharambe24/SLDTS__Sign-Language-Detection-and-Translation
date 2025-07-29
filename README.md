
# 🧠 Sign Language Detection and Translation System

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue)](https://www.python.org/)
[![OpenCV](https://img.shields.io/badge/OpenCV-4.5.5-orange)](https://opencv.org/)
[![MediaPipe](https://img.shields.io/badge/MediaPipe-0.8.11-red)](https://google.github.io/mediapipe/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.7.0-yellow)](https://www.tensorflow.org/)

This project implements a real-time **American Sign Language (ASL)** detection and translation system using **computer vision** and **hybrid deep learning techniques**. It captures hand gestures from a webcam and translates them into text and speech with high accuracy and low latency.

---

## 🚀 Features

- 🔍 Real-time gesture recognition using webcam
- 🤟 Recognition of ASL static alphabets (A–Z)
- 🔊 Text-to-speech support for detected signs
- 🔁 Bi-directional: Sign → Text/Speech and Speech → Sign
- 🧠 Hybrid architecture combining LSTM + Random Forest
- 📦 Modular codebase for easy extension and customization

---

## 📁 Project Structure

```

Sign-Language-Detection-and-Translation/
├── dataset/                   # Class-wise training images (e.g., A/, B/)
├── models/                    # Pretrained models (.h5 and .pkl)
├── utils/                     # Feature extraction and evaluation scripts
│   ├── data\_processing.py
│   └── model\_evaluation.py
├── training/                  # Training scripts
│   ├── train\_lstm.py
│   └── train\_rf.py
├── realtime\_detection.py      # Main app for real-time inference
├── requirements.txt           # Python dependencies
└── README.md

````

---

## 🧠 Technical Approach

### 1. **Hand Landmark Detection**
- Utilized **MediaPipe Hands** to extract 21 hand keypoints in real-time.
- Achieves >30 FPS on standard CPUs without requiring GPU acceleration.

### 2. **Feature Engineering**
- **Geometric features** calculated:
  - Angles between key joints
  - Distances between fingertips and wrist
- Features normalized for scale and position independence.

### 3. **Model Architectures**
- **Random Forest** (model.pkl):
  - Used for efficient classification on static gestures.
  - 100 trees, Gini impurity, feature bagging.
- **LSTM** (model.h5):
  - Used for sequential gesture modeling across video frames.
  - Sequence length: 30 frames.
- **Hybrid System**:
  - Combines predictions from both models for higher accuracy and adaptability.

---

## ⚙️ Installation

```bash
# Clone the repository
git clone https://github.com/rupeshbharambe24/Sign-Language-Detection-and-Translation.git
cd Sign-Language-Detection-and-Translation

# Install dependencies
pip install -r requirements.txt
````

> 📝 Make sure your system has a webcam and Python 3.8+.

---

### 📊 Training Models

```bash
# Train Random Forest
python training/train.py --data_path dataset/ --trees 100

# Train LSTM
python training/train.py --data_path dataset/ --epochs 50
```

---

## 📊 Performance Metrics

| Model         | Accuracy | Inference Time |
| ------------- | -------- | -------------- |
| LSTM          | 94.2%    | 18ms           |
| Random Forest | 89.7%    | 8ms            |
| Hybrid        | 96.1%    | 22ms           |

---

---

## ❗ Limitations & Future Work

* Limited to **static hand gestures** for now but with the help of UI, can form sentences or words.
* Only covers the **ISL alphabet** (A–Z) & numbers.
* Plans to:
  * Add **phrase-level** and **dynamic gesture** support.
  * Localize for **multi-language translation**.

---

## 🧾 Dependencies

* Python 3.8+
* OpenCV 4.5.5
* MediaPipe 0.8.11
* TensorFlow 2.7.0
* Scikit-learn 1.0.2
* PyAudio 0.2.11

---

## 👥 Contributors

* **Rupesh Bharambe** – AI/ML, DL, Web Dev, Deployment, etc
* **Harshal More** - AIML, Data Analysis
* **Onkar Kalyankar** - AIML, Data Analysis
* **Aniket Wahul** - Web Developer

---

## 📜 License

This project is licensed under the [MIT License](LICENSE).

---

## 🙏 Acknowledgments

* Google MediaPipe for robust hand tracking
* TensorFlow & Scikit-learn for model building
* OpenCV for real-time video processing
* ASL Dataset providers and open-source communities

---

> 🔁 Feel free to fork, contribute, or customize the system for regional sign languages or mobile deployment. Pull requests are always welcome!

```
