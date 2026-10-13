# DL-Volleyball-Analysis | 深度學習排球分析

**基於深度學習的排球比賽分析系統** · *Volleyball Match Analysis System Based on Deep Learning*

Turning one camera's recording of a volleyball match into a reviewable, point-by-point record: the
ball's path in 2D and 3D, positions in court metres, player actions and shirt numbers, every rally and the score.
Started as a senior capstone at National Taiwan Ocean University; the system is being rebuilt around measured accuracy.

把一台攝影機錄下的排球比賽，轉成可以逐分檢討的紀錄：球的路徑、場地公尺座標、球員動作、每一個回合與比分。

[![Website](https://img.shields.io/badge/Website-VolleyVision-0033A0?style=for-the-badge)](https://dl-volleyball-analysis.github.io/volleyvision-website/)
[![Code](https://img.shields.io/badge/Code-volleyball--analysis-24292f?style=for-the-badge&logo=github)](https://github.com/DL-Volleyball-Analysis/volleyball-analysis)
[![Report](https://img.shields.io/badge/Capstone-report-555?style=for-the-badge)](https://github.com/DL-Volleyball-Analysis/capstone-report)

<p align="center">
  <img src="https://raw.githubusercontent.com/DL-Volleyball-Analysis/volleyball-analysis/main/docs/assets/analysis.gif" width="720" alt="Analysed fixed end-line clip: court lines fitted to the painted lines, tracked players, ball trail, a top-down court map and a 3D view">
  <br><sub>One fixed camera behind the end line, analysed automatically (GCU vs UCLA): the court fitted to the painted
  lines (black on this multi-sport floor), the players by team, the ball trail, a top-down map and a 3D view.</sub>
</p>

| Basketball lines on the floor | Painted-line court | Broadcast view |
|:---:|:---:|:---:|
| <img src="https://raw.githubusercontent.com/DL-Volleyball-Analysis/volleyball-analysis/main/docs/assets/gallery-basketball-lines.gif" width="250"> | <img src="https://raw.githubusercontent.com/DL-Volleyball-Analysis/volleyball-analysis/main/docs/assets/gallery-court-lines.gif" width="250"> | <img src="https://raw.githubusercontent.com/DL-Volleyball-Analysis/volleyball-analysis/main/docs/assets/gallery-broadcast.gif" width="250"> |

## Repositories | 專案

| Repository | What it holds |
|---|---|
| [volleyball-analysis](https://github.com/DL-Volleyball-Analysis/volleyball-analysis) | all code: the `vball` analysis package, the web app (`webapp/`), training code (`training/`), notebooks, requirements (PRD), specifications (OpenSpec) and measurements |
| [volleyvision-website](https://github.com/DL-Volleyball-Analysis/volleyvision-website) | public landing page |
| [capstone-report](https://github.com/DL-Volleyball-Analysis/capstone-report) | capstone report (LaTeX, Chinese and English) as graded (`capstone-final` tag), with errata and the later work's current results |

### Capstone archive (read-only)

The first version of the system, kept with its history. Each README states what it did, its results with
corrections, and where the code lives now.

| Repository | What it was |
|---|---|
| [capstone-webapp](https://github.com/DL-Volleyball-Analysis/capstone-webapp) | first web app (FastAPI + React); rewritten as `volleyball-analysis/webapp` |
| [capstone-action-recognition](https://github.com/DL-Volleyball-Analysis/capstone-action-recognition) | YOLOv11m action recognition; now `training/action-recognition` |
| [capstone-jersey-numbers](https://github.com/DL-Volleyball-Analysis/capstone-jersey-numbers) | YOLOv8 jersey digits; mislabelled training data found and retrained (now in `volleyball-analysis`) |
| [capstone-court-detection](https://github.com/DL-Volleyball-Analysis/capstone-court-detection) | landing and IN/OUT with a hand-marked court; replaced by learned court registration |
| [capstone-prototype](https://github.com/DL-Volleyball-Analysis/capstone-prototype) | early prototype adapted from VolleyVision |

## What is measured | 量測結果

Every number states its kind of evidence. Details: [docs/results](https://github.com/DL-Volleyball-Analysis/volleyball-analysis/tree/main/docs/results).

| Module | Result | Evidence |
|---|---|---|
| Court registration | 0.10 m median court-position error on held-out broadcast clips, 0.49 m on held-out gym images. Fixed end-line cameras, where both keypoint models fail: the court fitted to the painted lines of an empty-court background plate is right to 2–6 cm on five of six clips (hand-labelled floor points; the sixth is 1.06 m off), and the net tape gives the focal length for 3D | labelled test images; labelled floor points |
| Player tracking (YOLO26s fine-tuned to box players only + BoT-SORT) | IDF1 0.690, precision 0.970 on SportsMOT volleyball (from 0.484 / 0.614) | labelled benchmark |
| Ball detection | WASB fine-tuned on broadcast + gym data: F1 0.942 (10 px) on held-out gym matches, against 0.859 for VballNet V4c and 0.527 for WASB's published weights | labelled test matches |
| 3D trajectory | player-anchored ballistic fit: attack error 0.76 → 0.31 m (median) with realistic detection errors when the toucher is unambiguous; a stress test with twelve players shows when an anchor must be withheld; on fixed end-line clips 45–160 flights per 3 minutes pass the physical checks | synthetic data; system checks |
| Action recognition | per-player classifier weighted by the ball's position: macro F1 0.678 on 16 unseen matches of the Volleyball dataset (capstone detector: 0.303) | labelled benchmark |
| Shirt numbers | digit mAP@0.5 0.824 on teams the model never saw | labelled test split |
| Rally detection | F1 0.742 on two held-out broadcast matches (ball only: 0.423); fixed end-line cameras: a model trained on labels read from the on-screen score reaches F1 0.76 on six clips of other matches and runs in the pipeline | labelled matches |

**Engineering.** Spec-first development (PRD + OpenSpec), one package per concern, CI on Python 3.14 and 3.12 with lint,
types, tests under a coverage gate and dependency audits, pinned dependencies, a model manifest with checksums, Docker
Compose, and decision records; first release [v0.1.0](https://github.com/DL-Volleyball-Analysis/volleyball-analysis/releases/tag/v0.1.0).

| Match review | Tactics board and statistics |
|---|---|
| ![Match review](https://raw.githubusercontent.com/DL-Volleyball-Analysis/volleyball-analysis/main/docs/assets/review-app.jpg) | ![Tactics board and statistics](https://raw.githubusercontent.com/DL-Volleyball-Analysis/volleyball-analysis/main/docs/assets/boards-and-stats.png) |

## Team | 團隊

Liang Yu-Jia 梁祐嘉 (lead), Tsai Pei-Ying 蔡佩穎, Chung Chia-Hsin 鍾佳芯; advisor Professor Ting Pei-Yi 丁培毅.
Department of Computer Science and Engineering, National Taiwan Ocean University.
