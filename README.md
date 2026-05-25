[README_pj1.md](https://github.com/user-attachments/files/28209839/README_pj1.md)
# 🎭 Emotion Aware Attendance System Using Face Recognition

> An AI-powered attendance management system that combines real-time face recognition with emotion detection — built on Raspberry Pi using Python, OpenCV, and SVM.

![Python](https://img.shields.io/badge/Python-3.9-blue?style=flat-square&logo=python)
![OpenCV](https://img.shields.io/badge/OpenCV-4.x-green?style=flat-square&logo=opencv)
![Platform](https://img.shields.io/badge/Platform-Raspberry%20Pi-red?style=flat-square&logo=raspberrypi)
![License](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)

---

## 📌 Overview

This project presents an **Emotion Aware Face Recognition AI Attendance System** that automates attendance marking while simultaneously capturing the emotional state of each student in real time. It was developed as a B.Tech project at **VIT Bhopal University** (School of Electrical & Electronics Engineering).

The system detects and recognizes faces via webcam, predicts emotions using a pre-trained SVM model, and logs attendance with timestamps and emotion labels into structured Excel/CSV files — eliminating manual attendance entirely.

---

## ✨ Features

- 🔍 **Real-time face detection & recognition** using deep learning embeddings
- 😊 **Emotion detection** — classifies happy, sad, angry, surprise, and neutral
- 📋 **Automated attendance logging** to CSV and Excel (.xlsx) formats
- 📊 **Class Score calculation** — a weighted mood score for the entire class session
- 🖥️ **Live GUI overlay** — bounding boxes and emotion labels on webcam feed
- ⚡ **Optimized for Raspberry Pi** with frame-skipping for lower CPU usage

---

## 🛠️ Tech Stack

| Component | Technology |
|---|---|
| Programming Language | Python 3.9 |
| Face Detection & Recognition | `face_recognition` library (dlib) |
| Emotion Classification | SVM trained on FER2013 dataset |
| Computer Vision | OpenCV |
| Excel Logging | OpenPyXL |
| Hardware | Raspberry Pi + Pi Camera |
| Numerical Processing | NumPy |
| Model Serialization | Joblib |

---

## 📁 Project Structure

```
emotion-attendance-system/
│
├── known_faces/             # Folder with labeled student images (name.jpg)
│   ├── Aryan.jpg
│   ├── Aditya.jpg
│   └── Alok.jpg
│
├── face_recognition_attendance.py   # Main application script
├── emotion_svm.pkl                  # Pre-trained SVM emotion model
│
├── attendence_logs/         # Auto-generated output folder
│   ├── attendence_YYYY-MM-DD.csv
│   └── attendence_YYYY-MM-DD.xlsx
│
└── README.md
```

---

## ⚙️ Installation

### Prerequisites

```bash
# Update system packages
sudo apt update && sudo apt upgrade -y

# Install Python dependencies
pip install opencv-python face_recognition numpy openpyxl joblib scikit-learn
```

> **Note:** Installing `face_recognition` on Raspberry Pi requires `dlib`. This may take a while to compile. Refer to [dlib's official docs](http://dlib.net/) for guidance.

---

## 🚀 Usage

### 1. Add Known Faces

Place labeled images of students inside the `known_faces/` folder. Name each file after the student (e.g., `Aryan.jpg`, `Aditya.jpg`).

### 2. Train the Emotion Model (if not already available)

Train an SVM classifier on the [FER2013 dataset](https://www.kaggle.com/datasets/msambare/fer2013) and save it as `emotion_svm.pkl` using joblib.

### 3. Run the System

```bash
python face_recognition_attendance.py
```

Press `Q` or `Esc` to stop the session. Attendance and emotion logs will be saved automatically.

---

## 📊 How the Class Score Works

The system computes a **weighted mood score** for the class at the end of each session:

```
score = Σ (emotion_weight × count) / total_emotions
```

| Emotion | Weight |
|---|---|
| Happy | 1.0 |
| Surprise | 0.7 |
| Neutral | 0.5 |
| Sad | 0.2 |
| Angry | 0.0 |

**Example:** 10 Happy + 5 Neutral + 3 Surprise →
```
score = (10×1.0 + 5×0.5 + 3×0.7) / 18 = 0.678 → Class Score: 67.8%
```

---

## 📈 Results

| Metric | Value |
|---|---|
| Face Recognition Accuracy | ~92% |
| Emotion Detection Accuracy | ~85% (on FER2013) |
| Robustness | Good under varying lighting; reduced with occlusion or side profiles |

---

## 🔭 Future Scope

- ☁️ Cloud integration for centralized data storage and analytics
- 🧠 Upgrade to CNN / ResNet / Transformer-based emotion models
- 🗣️ Multi-modal analysis (speech tone, body posture)
- 📱 Mobile app for teachers and administrators
- 🔒 Privacy-preserving and secure data handling

---

## 👨‍💻 Authors

| Name | Enrollment No. |
|---|---|
| Aditya Rawat | 24BAC10015 |
| Aryan Saxena | 24BAC10040 |

**Supervisor:** Dr. Anirban Bhowmick, Assistant Professor Senior, SEEE
**Institution:** VIT Bhopal University, Bhopal (M.P.) – 466114

---

## 📚 References

1. Mahor et al., "Face Recognition Techniques", IJCS, 2010.
2. Smith & Lee, "Real-Time Emotion Classification," IEEE Trans. Affective Computing, 2020.
3. Kumar et al., "Hybrid Attendance with Expression Analysis", Springer, 2020.
4. Paul et al., "A Comprehensive Approach to Real-time Attendance Systems," Procedia Computer Science, 2025.
5. Llurba & Palau, "Real-Time Emotion Recognition for Teaching-Learning", Journal of Imaging, 2024.
6. Suhas et al., "Student Attendance with Emotion and Feedback Analysis", Indiana Journal of Multidisciplinary Research, 2024.

---

## 📄 License

This project is submitted in partial fulfillment of the B.Tech degree at VIT Bhopal University. For reuse or collaboration, please contact the authors.
