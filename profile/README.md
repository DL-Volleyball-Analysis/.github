# DL-Volleyball-Analysis

**基於深度學習的排球比賽分析系統**  
*Volleyball Match Analysis System Based on Deep Learning*

A comprehensive AI-powered system for analyzing volleyball matches, featuring ball tracking, action recognition, and player tracking.

## System Architecture

![System Architecture](system_architecture.png)

### AI Core Processing

![AI Core](system_architecture_ai_core.png)

### Backend Architecture

![Backend](system_architecture_backend.png)

## 🏐 Projects

| Repository | Description |
|------------|-------------|
| [volleyball-analysis-webapp](https://github.com/DL-Volleyball-Analysis/volleyball-analysis-webapp) | Main web application (React + FastAPI) |
| [action-recognition-yolov11](https://github.com/DL-Volleyball-Analysis/action-recognition-yolov11) | YOLOv11 action recognition training |
| [jersey-number-detection](https://github.com/DL-Volleyball-Analysis/jersey-number-detection) | Jersey number OCR detection |
| [capstone-report](https://github.com/DL-Volleyball-Analysis/capstone-report) | Academic report (LaTeX) |

## Tech Stack

![Python](https://img.shields.io/badge/Python-3.11-blue?logo=python)
![PyTorch](https://img.shields.io/badge/PyTorch-2.1-red?logo=pytorch)
![React](https://img.shields.io/badge/React-18.2-61DAFB?logo=react)
![FastAPI](https://img.shields.io/badge/FastAPI-0.95-009688?logo=fastapi)
![YOLO](https://img.shields.io/badge/YOLO-v11-00FFFF)

## Features

- **Ball Tracking** - VballNet (U-Net based) with 79.5% accuracy
- **Action Recognition** - YOLOv11m with 94.49% mAP@0.5
- **Player Tracking** - YOLOv8 + Norfair multi-object tracking
- **Jersey Number OCR** - Automatic jersey number detection

## Screenshots

### Dashboard
![Dashboard](dashboard.png)

### Video Analysis
![Video Analysis](play_sector.png)

---

*National Taiwan Ocean University - Department of Computer Science*  
*Senior Capstone Project 2025*
