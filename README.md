
# VeinScope – Deep Learning Eye Vein Segmentation System

This repository contains the full pipeline of **VeinScope**, a deep learning-based eye vein analysis system developed during the IIT Mandi GRP Hackathon 2025.

It combines a **Flutter mobile application** with a **deep learning backend** to segment eye veins (specifically scleral and retinal vessels) and extract features that may correlate with systemic health conditions such as diabetes, hypertension, or cardiovascular stress.

---

## 📱 Application Overview

The mobile app (named **Casca**) captures eye images and processes them via two modes:
- **Auto Mode**: Fully automated sclera detection and segmentation
- **Prompt Mode**: User manually selects scleral region using 3–5 points

Both modes communicate with a server hosting the model pipeline for segmentation and health indicator inference.

---

## 🧠 System Architecture

The deep learning pipeline includes:
- **Image classification** using ResNet-18 to filter valid eye/retina images
- **Sclera region detection** using the Segment Anything Model (SAM)
- **Vein enhancement** via green channel extraction and CLAHE
- **Segmentation** using a fine-tuned **nnU-Net** (achieving 63.5% Dice score)
- **Feature extraction** (tortuosity, branching, width, density, etc.)
- **Health indicator mapping** to suggest potential vascular issues

---

## 🧪 Key Features

- Fully automated segmentation from smartphone-captured images
- Support for both retina and sclera vein analysis
- Use of SAM + nnU-Net for precision segmentation
- Feature extraction with visual feedback on vein quality
- Mobile-first interface for quick testing

---

## 🧑‍💻 My Contribution

This was a collaborative hackathon project. My work focused on the **model and backend**, including:
- Building the SAM-based prompt segmentation pipeline
- Training and tuning nnU-Net for vessel segmentation
- Developing image enhancement, data augmentation, and evaluation logic
- Implementing the Flask-based inference server

The app (`app/`) was developed by teammates, and the final repo was structured and cleaned by me.

---

## 📂 Repo Structure

```
VeinScope/
├── app/        # Flutter mobile app (Casca)
└── model/      # DL pipeline: SAM + nnU-Net + Flask server
```

---

## 📈 Results

| Model                  | Dice Score |
|------------------------|------------|
| Vanilla U-Net          | 31.8%      |
| U-Net + ResNet-50      | 33.4%      |
| **nnU-Net (final)**    | **63.5%**  |

---

## 🔧 Backend Server

The Flask-based API (used for inference and image processing) currently runs on a private SSH-accessible GPU server.

🛠️ *Note: Script paths and environment setup are system-specific and will be refactored for public deployment in a future update.*

---

## 📌 Future Work

- Lighter ROI detection models (for on-device inference)
- Eyelash artifact removal using VAE or filtering
- Swin-UNet / Attention UNet exploration
- Clinical validation with hospitals

---

## 🔗 Acknowledgements

- Segment Anything Model (Meta AI) – [arXiv:2304.02643](https://arxiv.org/abs/2304.02643)
- nnU-Net – [Nature Methods](https://www.nature.com/articles/s41592-020-01008-z)
- Flutter & Dart for frontend development

---

## 🚀 Demo (optional)
[![Watch Demo](https://img.youtube.com/vi/4_jvWmj_nAQ/0.jpg)](https://youtu.be/4_jvWmj_nAQ)

---

> 🧠 *Note: This project is for research and screening purposes only. No medical decisions should be based on its output without proper clinical validation.*
