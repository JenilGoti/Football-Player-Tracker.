# ⚽ Football Player Tracker

![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)
![PyTorch](https://img.shields.io/badge/PyTorch-2.0+-ee4c2c.svg)
![YOLOv8](https://img.shields.io/badge/YOLOv8-Ultralytics-purple.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)
![Gradio](https://img.shields.io/badge/Demo-Gradio-orange.svg)

A real-time **Football Player Detection & Tracking** system built with **YOLOv8**, **PyTorch Transfer Learning**, and **ByteTrack**. Upload any football match video and the AI will detect, classify, and track every player, referee, goalkeeper, and ball with unique IDs across all frames.

---

## 🌐 Live Demo

> **Try it here → [https://0da1ed50dc7347a5de.gradio.live](https://0da1ed50dc7347a5de.gradio.live)**

---

## 📸 Project Overview

```
Upload Football Video → YOLOv8 Detection → ByteTrack Tracking → Annotated Output Video
```

| Feature | Detail |
|---|---|
| 🎯 Detection | Players, Ball, Goalkeeper, Referee |
| 🔁 Tracking | Unique ID per player across all frames |
| 🧠 Model | YOLOv8m fine-tuned with Transfer Learning |
| 📦 Dataset | Custom Roboflow football dataset |
| 🚀 Demo | Gradio web app |
| ⚡ Backend | PyTorch + CUDA |

---

## 🧠 How It Works

### Transfer Learning Pipeline

```
YOLOv8m (pretrained on COCO 80 classes)
        ↓
Backbone layers FROZEN  (keeps general features)
        ↓
Detection head FINE-TUNED on football dataset
        ↓
Custom model: detects players, ball, referee, goalkeeper
```

### Tracking Pipeline

```
Frame 1 → Detect players → Assign IDs
Frame 2 → Detect players → Match IDs with ByteTrack
Frame N → Consistent IDs across entire video ✅
```

---

## 📊 Model Performance

| Metric | Score |
|---|---|
| **mAP@50** | **0.84 (84%)** ✅ |
| mAP@50-95 | 0.539 |
| Precision | 95.6% |
| Recall | 78.8% |
| box_loss | 0.9793 |
| cls_loss | 0.4402 |

> Trained for **50 epochs** on Google Colab T4 GPU

---

## 📁 Project Structure

```
Football-Player-Tracker/
│
├── Football_Player_Tracker.ipynb   ← Main Colab notebook
├── README.md                       ← You are here
│
├── football_dataset/               ← Roboflow dataset
│   ├── data.yaml
│   ├── train/
│   │   ├── images/
│   │   └── labels/
│   └── valid/
│       ├── images/
│       └── labels/
│
└── runs/
    └── detect/
        └── football_project/
            └── weights/
                └── best.pt         ← Trained model weights
```

---

## 🚀 Quick Start

### 1. Open in Google Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/JenilGoti/Football-Player-Tracker./blob/main/Football_Player_Tracker.ipynb)

### 2. Install Dependencies

```bash
pip install ultralytics roboflow gradio torch torchvision
```

### 3. Run Detection on a Video

```python
from ultralytics import YOLO

model = YOLO("runs/detect/football_project/weights/best.pt")

model.track(
    source="your_football_video.mp4",
    tracker="bytetrack.yaml",
    save=True,
    conf=0.4
)
```

---

## 🔧 Tech Stack

| Tool | Purpose |
|---|---|
| **PyTorch** | Deep learning framework (backbone engine) |
| **YOLOv8 (Ultralytics)** | Object detection architecture |
| **ByteTrack** | Multi-object tracking algorithm |
| **Roboflow** | Dataset management & export |
| **OpenCV** | Video processing & heatmap generation |
| **Gradio** | Web demo deployment |
| **Google Colab** | Training environment (T4 GPU) |
| **ffmpeg** | Video format conversion |

---

## 📦 Dataset

- **Source:** [Roboflow Universe — Football Player Detection](https://universe.roboflow.com/laurent-pereira-44n5u/football-player-detection-ryyjv)
- **Forked & customized** in personal Roboflow workspace
- **Format:** YOLOv8
- **Split:** 80% Train / 20% Validation
- **Classes:** `player`, `ball`, `goalkeeper`, `referee`

---

## 🗺️ End-to-End Pipeline

```
Phase 1 → Google Colab + T4 GPU setup
Phase 2 → Dataset downloaded from Roboflow
Phase 3 → YOLOv8 trained with PyTorch Transfer Learning
Phase 4 → mAP score evaluated (84% mAP@50)
Phase 5 → Player tracking on video with ByteTrack
Phase 7 → Gradio demo deployed with public link
Phase 8 → Pushed to GitHub
```

---

## 💡 Key Concepts Demonstrated

- ✅ **Transfer Learning** — Froze YOLOv8 backbone, fine-tuned detection head
- ✅ **Custom Dataset Training** — Roboflow pipeline → YOLOv8 format
- ✅ **Multi-Object Tracking** — ByteTrack with consistent player IDs
- ✅ **End-to-End ML Pipeline** — Data → Train → Evaluate → Deploy
- ✅ **Model Deployment** — Gradio web app with public shareable link

---

## 📈 Training Results

```
Validation
─────────────────────────────────────────────────────────
mAP@50:     0.837
mAP@50-95:  0.553
Precision:  0.946
Recall:     0.800
```

---

## 🙌 Acknowledgements

- [Ultralytics YOLOv8](https://github.com/ultralytics/ultralytics)
- [Roboflow Universe](https://universe.roboflow.com)
- [ByteTrack](https://github.com/ifzhang/ByteTrack)
- Dataset by [Laurent Pereira](https://universe.roboflow.com/laurent-pereira-44n5u/football-player-detection-ryyjv)

---

## 👤 Author

**Jenil Goti**
- GitHub: [@JenilGoti](https://github.com/JenilGoti)

---

> ⭐ If you found this project useful, please give it a star!
