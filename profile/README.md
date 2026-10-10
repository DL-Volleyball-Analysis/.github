# DL-Volleyball-Analysis | 深度學習排球分析

**基於深度學習的排球比賽分析系統** · *Volleyball Match Analysis System Based on Deep Learning*

Turning one camera's recording of a volleyball match into a reviewable, point-by-point record: the
ball's path, positions in court metres, player actions, every rally and the score. Started as a senior
capstone at National Taiwan Ocean University; the system is being rebuilt around measured accuracy.

把一台攝影機錄下的排球比賽，轉成可以逐分檢討的紀錄：球的路徑、場地公尺座標、球員動作、每一個回合與比分。

[![Website](https://img.shields.io/badge/Website-VolleyVision-0033A0?style=for-the-badge)](https://dl-volleyball-analysis.github.io/volleyvision-website/)
[![Code](https://img.shields.io/badge/Code-volleyball--analysis-24292f?style=for-the-badge&logo=github)](https://github.com/DL-Volleyball-Analysis/volleyball-analysis)
[![Report](https://img.shields.io/badge/Capstone-report-555?style=for-the-badge)](https://github.com/DL-Volleyball-Analysis/capstone-report)

<p align="center">
  <img src="https://raw.githubusercontent.com/DL-Volleyball-Analysis/volleyball-analysis/main/docs/assets/analysis.gif" width="720" alt="Analysed broadcast clip: ball trail, tracked players, court lines and a top-down court map">
  <br><sub>Ball trail, player tracks (tracking ids), detected court and the players on a top-down court map, all
  produced automatically from one broadcast camera.</sub>
</p>

## Repositories | 專案

| Repository | What it holds |
|---|---|
| [volleyball-analysis](https://github.com/DL-Volleyball-Analysis/volleyball-analysis) | all code: the `vball` analysis package, the web app (`webapp/`), training code (`training/`), notebooks, requirements (PRD), specifications (OpenSpec) and measurements |
| [volleyvision-website](https://github.com/DL-Volleyball-Analysis/volleyvision-website) | public landing page |
| [capstone-report](https://github.com/DL-Volleyball-Analysis/capstone-report) | capstone report (LaTeX, Chinese and English); graded version under the `capstone-final` tag |

### Capstone archive (read-only)

The first version of the system, kept with its history. Each README states what it did, its results with
corrections, and where the code lives now.

| Repository | What it was |
|---|---|
| [capstone-webapp](https://github.com/DL-Volleyball-Analysis/capstone-webapp) | first web app (FastAPI + React); rewritten as `volleyball-analysis/webapp` |
| [capstone-action-recognition](https://github.com/DL-Volleyball-Analysis/capstone-action-recognition) | YOLOv11m action recognition; now `training/action-recognition` |
| [capstone-jersey-numbers](https://github.com/DL-Volleyball-Analysis/capstone-jersey-numbers) | YOLOv8 jersey digits; mislabelled training data found, retraining planned |
| [capstone-court-detection](https://github.com/DL-Volleyball-Analysis/capstone-court-detection) | landing and IN/OUT with a hand-marked court; replaced by learned court registration |
| [capstone-prototype](https://github.com/DL-Volleyball-Analysis/capstone-prototype) | early prototype adapted from VolleyVision |

## What is measured | 量測結果

Every number states its kind of evidence. Details: [docs/results](https://github.com/DL-Volleyball-Analysis/volleyball-analysis/tree/main/docs/results).

| Module | Result | Evidence |
|---|---|---|
| Court registration (14 keypoints) | 0.49 m median court-position error on held-out images; wrong courts flagged by a floor-net check | labelled test images |
| Player tracking (YOLO26s + BoT-SORT) | IDF1 0.484, HOTA 0.467 on SportsMOT volleyball | labelled benchmark |
| Ball tracking (VballNet V4c) | 3.08 false jumps per 100 frames, 68.7% of frames detected on 5 broadcast clips | label-free proxy |
| 3D trajectory | 0.05 m median error on a synthetic serve | synthetic data |
| Action recognition (YOLOv11m) | mAP@0.5 0.957 on the test split (same matches as training, so not an unseen-match score) | labelled test split |

| Match review | Tactics board and statistics |
|---|---|
| ![Match review](https://raw.githubusercontent.com/DL-Volleyball-Analysis/volleyball-analysis/main/docs/assets/review-app.jpg) | ![Tactics board and statistics](https://raw.githubusercontent.com/DL-Volleyball-Analysis/volleyball-analysis/main/docs/assets/boards-and-stats.png) |

## Team | 團隊

Liang Yu-Jia 梁祐嘉 (lead), Tsai Pei-Ying 蔡佩穎, Chung Chia-Hsin 鍾佳芯; advisor Professor Ting Pei-Yi 丁培毅.
Department of Computer Science and Engineering, National Taiwan Ocean University.
