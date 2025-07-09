
# 🧠 Real-Time Concentration Tracker using MediaPipe & OpenCV

This project implements a **real-time facial behavior monitoring system** that evaluates and visualizes a user's **concentration level** using facial landmarks, eye movements, gaze direction, and head posture. Built using **Python**, **MediaPipe**, and **OpenCV**, it provides an interactive interface to help track attention and distraction over time.

---

## 💡 Overview

The Concentration Tracker uses **MediaPipe FaceMesh** to extract facial landmarks and infer important attention-related cues such as:

- **Eye Aspect Ratio (EAR)** for blink detection
- **Iris movement** for gaze tracking
- **Nose position** for head pose estimation
- **A combined heuristic model** to compute concentration level

By aggregating these features, the system provides a smooth, real-time score (0–100%) representing the user's concentration level. It also tracks distraction frequency and alerts when attention drops consistently.

---

## 🎯 Key Features

- 🔍 **Facial Landmark Detection:** Accurate landmark tracking using MediaPipe's FaceMesh with 468 facial points.
- 👁️ **Blink Detection:** Calculates Eye Aspect Ratio (EAR) to detect eye closure and blinks.
- 👀 **Gaze Estimation:** Uses iris coordinates to determine if the user is looking ahead or away.
- 🧭 **Head Pose Scoring:** Detects head orientation based on nose deviation from screen center.
- 📊 **Concentration Scoring:** Computes a real-time weighted concentration score based on gaze, head pose, and blink activity.
- 📉 **Distraction Monitoring:** Increments a distraction counter when attention score drops below threshold.
- ⚙️ **Live Visualization:** Includes a concentration bar, attention status indicator, and distraction alerts overlayed on the video feed.
- 📈 **Smooth Score Tracking:** Uses a history queue to average out the concentration score and reduce jitter.
- 🧪 **Modular Design:** Each component (eye detection, head pose, gaze, scoring) is independently manageable for easy tuning and experimentation.

---

## 🧠 How Concentration is Measured

The system calculates a **concentration score (0–100%)** using the following weighted heuristic:

```
Concentration Score = 0.4 × Gaze Score + 0.4 × Head Pose Score + 0.2 × (1 - Blink Penalty)
```

- **Gaze Score:** 1 if the user is looking forward, else 0
- **Head Pose Score:** 1 if the head is oriented toward the camera, else 0
- **Blink Penalty:** 1 if a blink is detected, else 0

A **score above 40%** indicates attentiveness, while scores below that contribute to the **distraction counter**.

---

## 🧰 Requirements

Ensure you have Python 3.7 or higher. Install the following libraries:

```bash
pip install opencv-python mediapipe numpy
```

---

## 🚀 Getting Started

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/concentration-tracker.git
   cd concentration-tracker
   ```

2. Run the application:
   ```bash
   python main.py
   ```

3. The webcam window will launch with live feedback.

4. Press `q` to exit the window.

---

## 🧪 Applications

This system can be adapted or expanded for:

- 📚 **Online Education:** Monitor student attentiveness during virtual classes
- 👨‍💻 **Workplace Productivity:** Track screen focus during remote work
- 🧑‍🏫 **Tutoring & Assessments:** Detect off-screen distractions
- 🧠 **Cognitive Research:** Analyze user behavior and focus patterns
- 👁️ **Human-Computer Interaction:** Real-time feedback for adaptive systems

---

## 🧑‍💻 Technologies Used

- **Python** – Core programming language
- **MediaPipe** – FaceMesh for landmark extraction
- **OpenCV** – Image processing and rendering
- **NumPy** – Numerical computation and geometry operations

---

## 📌 Notes

- Gaze and head-pose estimation are heuristic and may vary slightly with lighting and camera angle.
- The model does not perform face recognition — it only detects and tracks general facial behaviors.
- This is an on-device solution — no internet or cloud processing is required.

---

## 🤝 Contributions

Contributions and suggestions are welcome! Whether it's improving gaze tracking, adding logging/analytics, or adapting it for mobile/web — feel free to fork the project and raise a pull request.

---


---

## 🙏 Acknowledgments

- [MediaPipe by Google](https://google.github.io/mediapipe/) for enabling high-performance face tracking.
- The open-source community for the foundational tools used in this project.

---

> ✨ “This system aims not just to track where your eyes go — but whether your mind stays.”
