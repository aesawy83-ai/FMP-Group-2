<p align="center">
  <img src="assets/facade_banner_v2.png" width="100%">
</p>

<p align="center">
  <b>AI-Enabled Multi-Class Façade Defect Detection for AECO Workflows</b>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10+-blue">
  <img src="https://img.shields.io/badge/YOLO-11-success">
  <img src="https://img.shields.io/badge/Roboflow-V1-orange">
  <img src="https://img.shields.io/badge/Colab-T4-yellow">
  <img src="https://img.shields.io/badge/Status-Research%20WIP-purple">
</p>

---

## Introduction

This repository presents the **Detect stage** of an AI-enabled façade inspection workflow developed for a **Master’s Final Project in AI for AECO**. It implements a **YOLO11 multi-class object detection pipeline**, trained and validated in **Google Colab** using a **public Roboflow dataset**, to automatically identify visible façade defects from inspection imagery across four key classes: **Crack, Efflorescence, Spalling, and Exposed Wires**. This computer vision baseline establishes the foundation for future **BIM-linked defect intelligence, Digital Twin integration, and lifecycle-driven asset assessment workflows**.

---

##  End-to-End Project Vision

This repository currently focuses on the **detection layer** of the broader inspection intelligence pipeline:

> **Capture → Detect → Structure → Integrate → Assess**

<p align="center">
  <img src="assets/banner_01.png" width="100%">
</p>

#  Project Objective

Traditional façade inspection is often **manual, labor-intensive, visually subjective, difficult to scale, and weakly documented longitudinally**. This project demonstrates how **computer vision and object detection** can transform the process into a more **scalable, auditable, and evidence-driven workflow**, with a long-term vision of translating detections into **BIM-linked condition intelligence, maintenance prioritization, Digital Twin updates, and lifecycle decision support**.

---

#  Dataset

##  Public Dataset Source

The dataset is publicly available on **Roboflow Universe**.

* **Workspace:** `youniss-workspace-fic2t`
* **Project:** `m10-fmp-g2-facade-detection`
* **Task:** Multi-class object detection
* **Export Format:** YOLO11
* **Version Used:** `V1`

###  Dataset Link

[https://universe.roboflow.com/youniss-workspace-fic2t/m10-fmp-g2-facade-detection](https://universe.roboflow.com/youniss-workspace-fic2t/m10-fmp-g2-facade-detection)

##  Defect Taxonomy

| Class | Inspection Meaning |
|---|---|
| crack | façade cracks, fractures, and line defects |
| efflorescence | moisture-related salt deposits and white staining |
| spalling | surface material loss and concrete detachment |
| wires | exposed service cables and visible electrical lines |

##  Dataset Strategy

The dataset follows standard **train / validation / test** splits to support:

* fair held-out evaluation
* repeatable benchmarking
* class-level AP tracking
* PR curve reproducibility

### Version freeze used in notebook

```python
version = project.version(1)
```
---

# 🤖 Model Architecture

The detector is trained using **Ultralytics YOLO11** in **Google Colab Pro (T4 GPU)**.

##  Training Configuration

| Parameter | Value |
|---|---:|
| Model | YOLO11s |
| Framework | Ultralytics |
| Training Platform | Google Colab |
| GPU | T4 High RAM |
| Epochs | 50 |
| Image Size | 640 |
| Batch Size | 16 |
| Early Stopping | patience = 20 |
| Notebook | `notebooks/FMP_AI_Facade_Inspection.ipynb` |

---

#  Results Summary

| mAP@0.5 | mAP@0.5:0.95 | Precision | Recall | Crack AP | Efflorescence AP | Spalling AP | Wires AP |
|---:|---:|---:|---:|---:|---:|---:|---:|
| **00.18** | **00.09** | **00.28** | **00.21** | **00.354** | **00.148** | **00.155** | **00.056** |

---

# 📈 Evaluation Visual Evidence

## Precision–Recall Curve

![PR Curve](results/curves/PR_curve.png)

## Confusion Matrix

![Confusion Matrix](results/curves/confusion_matrix.png)

## Training Curves

![Training Results](results/curves/results.png)

## F1 Curve

![F1 Curve](results/curves/F1_curve.png)

---

#  Sample Detection Outputs

## Validation Predictions

![Validation 1](results/predictions_val/val_01.jpg)
![Validation 2](results/predictions_val/val_02.jpg)

## Unseen Image Predictions

![Prediction 1](results/predictions_new/new_01.jpg)
![Prediction 2](results/predictions_new/new_03.jpg)

---

#  Reproducibility Workflow (Google Colab)

##  Run Instructions

1. Open notebook: `notebooks/FMP_AI_Facade_Inspection.ipynb`
2. Set runtime → **GPU**
3. Install dependencies:

```python 
!pip install ultralytics roboflow
```

4. Connect dataset:

```python
from roboflow import Roboflow

rf = Roboflow(api_key="YOUR_API_KEY")
project = rf.workspace("youniss-workspace-fic2t").project("m10-fmp-g2-facade-detection")
version = project.version(1)
dataset = version.download("yolov11")
```

5. Run all cells
6. Outputs generated under:

```text
/runs/detect/
```

Generated artifacts:

* `best.pt`
* PR curves
* confusion matrix
* validation predictions
* test predictions
* training curves

---

#  Model Weights

The final trained **YOLO11s multi-class façade defect detector** is available via GitHub Releases.

link: [Download YOLO11s.pt model weights](https://github.com/aesawy83-ai/AI-Facade-Inspection/releases/tag/v1.0)

---

#  Error Analysis

Detailed failure analysis:

`docs/error_analysis.md`

Typical failure patterns:

* thin wire misses
* crack vs stain confusion
* shadow-heavy false positives
* distant spalling misses
* low-light recall degradation

---

# 🎓 Academic Context and Limitations

This repository is a **research and academic prototype**.

Developed as part of a **Master-level Final Project in AI for AECO façade inspection workflows**.

This work combines:

* Computer Vision
* Defect Analytics
* BIM Integration
* Digital Twin Strategy
* Lifecycle Asset Intelligence

Current limitations:

* strongly dependent on dataset quality
* sensitive to camera distance and resolution
* no severity estimation yet
* no BIM element linkage yet
* requires engineering review before use

---

##  Roadmap

### Phase 1 — Detection
- [x] Multi-class YOLO11 baseline
- [x] Roboflow dataset pipeline
- [x] Colab reproducibility
- [x] GitHub documentation system

### Phase 2 — Structuring
- [ ] JSON defect schema
- [ ] severity scoring
- [ ] asset tagging

### Phase 3 — BIM / Digital Twin
- [ ] IFC mapping
- [ ] dashboard visualization
- [ ] lifecycle analytics

---

# 📄 License

**Group_2 License**

---

# 👤 Author

**Group_2**

