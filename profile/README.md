# DL-Volleyball-Analysis | 深度學習排球分析

**基於深度學習的排球比賽分析系統**  
*Volleyball Match Analysis System Based on Deep Learning*

A comprehensive AI-powered system for analyzing volleyball matches, featuring ball tracking, action recognition, and player tracking.

一個綜合性的 AI 排球比賽分析系統，包含球追蹤、動作識別和球員追蹤功能。

---

## Presentation | 專題簡報

[![Canva Presentation](https://img.shields.io/badge/Canva-%E5%B0%88%E9%A1%8C%E7%B0%A1%E5%A0%B1-00C4CC?style=for-the-badge&logo=canva&logoColor=white)](https://www.canva.com/design/DAG7EZ2BhWw/txwh6VE12fYEakm5bF2sdg/view)

[View Full Presentation | 查看完整簡報](https://www.canva.com/design/DAG7EZ2BhWw/txwh6VE12fYEakm5bF2sdg/view)

---

## System Architecture | 系統架構

![System Architecture](system_architecture.png)

The system adopts a **front-end and back-end separation architecture**, with clear module responsibilities:

系統採用**前後端分離架構**，各模組職責明確：

- **Frontend** - React 18 + TypeScript web interface | React 18 + TypeScript 網頁介面
- **Backend** - FastAPI RESTful API + WebSocket | FastAPI RESTful API + WebSocket 即時通訊
- **AI Core** - PyTorch + YOLO deep learning pipeline | PyTorch + YOLO 深度學習管線
- **Database** - SQLite for local, PostgreSQL for production | SQLite 本地端，PostgreSQL 生產環境

---

## AI Processing Pipeline | AI 處理管線

![AI Core](system_architecture_ai_core.png)

### Ball Tracking | 球追蹤

| Specification | Value |
|---------------|-------|
| Model | VballNet (U-Net based) |
| Input | 9-frame grayscale sequence (1, 9, 288, 512) |
| Output | Heatmap with ball location |
| Format | ONNX Runtime |
| Accuracy | 79.5% |

VballNet uses **temporal sequence input** to capture ball motion patterns. A 9-frame buffer captures trajectory information for improved detection accuracy.

VballNet 使用**時間序列輸入**捕捉球的運動模式。9 幀緩衝區捕捉軌跡資訊以提高檢測準確度。

![U-Net Architecture](u-net-architecture.png)

### Action Recognition | 動作識別

| Specification | Value |
|---------------|-------|
| Model | YOLOv11m |
| Classes | 5 (serve, spike, block, receive, set) |
| Dataset | 24,806 images |
| mAP@0.5 | 94.49% |
| Confidence Threshold | ≥60% |

Training configuration: 200 epochs, batch size 12-20, image size 640×640, SGD optimizer.

訓練配置：200 輪，批次大小 12-20，圖像尺寸 640×640，SGD 優化器。

![YOLOv11 Architecture](yolov11_architecture.jpg)

### Player Tracking | 球員追蹤

| Specification | Value |
|---------------|-------|
| Detection Model | YOLOv8 |
| Tracking | Norfair (Euclidean distance) |
| Consistency | 87.6% |
| Confidence Threshold | ≥50% |

Norfair parameters: `distance_threshold=100`, `initialization_delay=3`, `hit_counter_max=15`

---

## Backend Architecture | 後端架構

![Backend](system_architecture_backend.png)

| Component | Technology | Purpose |
|-----------|------------|---------|
| API Framework | FastAPI | RESTful endpoints |
| Real-time | WebSocket | Progress updates |
| Database | SQLite/PostgreSQL | Data persistence |
| Task Queue | Celery + Redis | Background processing |
| Video Streaming | Range requests | Efficient playback |

### API Endpoints | API 端點

```
POST /upload          - Upload video | 上傳影片
POST /analyze/{id}    - Start analysis | 開始分析
GET  /results/{id}    - Get results | 取得結果
GET  /play/{id}       - Stream video | 串流影片
WS   /ws/{task_id}    - Real-time progress | 即時進度
```

---

## Projects | 專案

| Repository | Description | Tech |
|------------|-------------|------|
| [volleyball-analysis-webapp](https://github.com/DL-Volleyball-Analysis/volleyball_analysis_webapp) | Main web application | React + FastAPI |
| [action-recognition-yolov11](https://github.com/DL-Volleyball-Analysis/action-recognition-yolov11) | Action recognition training | YOLOv11 |
| [jersey-number-detection](https://github.com/DL-Volleyball-Analysis/jersey-number-detection) | Jersey number OCR | YOLOv8 |
| [capstone-report](https://github.com/DL-Volleyball-Analysis/capstone-report) | Academic report | LaTeX |

---

## Tech Stack | 技術棧

![Python](https://img.shields.io/badge/Python-3.11-blue?logo=python)
![PyTorch](https://img.shields.io/badge/PyTorch-2.1-red?logo=pytorch)
![React](https://img.shields.io/badge/React-18.2-61DAFB?logo=react)
![FastAPI](https://img.shields.io/badge/FastAPI-0.95-009688?logo=fastapi)
![YOLO](https://img.shields.io/badge/YOLO-v11-00FFFF)
![TypeScript](https://img.shields.io/badge/TypeScript-4.9-blue?logo=typescript)
![TailwindCSS](https://img.shields.io/badge/Tailwind-3.x-38B2AC?logo=tailwindcss)

---

## Performance Summary | 效能總結

| Module | Metric | Value |
|--------|--------|-------|
| Ball Tracking | Accuracy | 79.5% |
| Action Recognition | mAP@0.5 | 94.49% |
| Player Tracking | Consistency | 87.6% |
| Jersey Number OCR | Accuracy | 68.5% |
| Processing Speed | FPS | ~7.91 |
| Test Coverage | Overall | 59% |

---

## Screenshots | 系統截圖

### Landing Page | 首頁
![Landing Page](landing.png)

### Dashboard | 儀表板
![Dashboard](dashboard.png)

### Video Analysis with Play Selector | 影片分析與回合選擇
![Video Analysis](play_sector.png)

### Action Detection | 動作偵測
![Action Boxes](action_boxes.png)

### Player Detection | 球員偵測
![Player Detection](player_detection(boxes).png)

### Player Statistics | 球員統計
![Player Stats](player_stats.png)

---

## System Requirements | 系統需求

| Component | Minimum | Recommended |
|-----------|---------|-------------|
| CPU | Intel i5 | Intel i7+ |
| RAM | 8GB | 16GB |
| GPU | None (CPU mode) | NVIDIA GTX 1060+ |
| Storage | 20GB | 50GB SSD |

---

## Quick Start | 快速開始

```bash
# Clone main repo | 複製主專案
git clone https://github.com/DL-Volleyball-Analysis/volleyball_analysis_webapp.git

# Install dependencies | 安裝依賴
pip install -r requirements.txt
cd frontend && npm install

# Start services | 啟動服務
cd backend && uvicorn main:app --reload  # Backend
cd frontend && npm start                  # Frontend
```

Access | 存取: http://localhost:3000

---

*National Taiwan Ocean University - Department of Computer Science*  
*國立臺灣海洋大學 資訊工程學系*

*Senior Capstone Project 2025 | 專題研究 2025*
