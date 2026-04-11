# 🏢 AI-Facade-Inspection
## AI-Enabled Multi-Class Façade Defect Detection for Inspection and Digital Twin Integration

> **Final Master Project (FMP) | AI for AECO | Computer Vision | BIM & Digital Twin Workflows**

<p align="center">
  <img src="assets/facade.banner.png" width="100%">
</p>

This repository presents the **Detect stage** of an AI-enabled façade inspection workflow developed for a **Master-level Final Project**.
Using a **YOLO11-based multi-class object detection pipeline** trained in **Google Colab** with a **public Roboflow dataset**, the system automatically detects visible façade defects from inspection imagery.

### ✅ Currently Detected Defect Classes

* **Crack**
* **Efflorescence**
* **Spalling**
* **Exposed wires**

---

## 🔄 End-to-End Project Vision

This repository currently focuses on the **detection layer** of the broader inspection intelligence pipeline:

> **Capture → Detect → Structure → Integrate → Assess**

### Included in this repository

* ✅ Reproducible Google Colab notebook
* ✅ Roboflow dataset integration
* ✅ YOLO11 training + validation
* ✅ PR curves + confusion matrix
* ✅ Sample predictions on unseen images
* ✅ GitHub-ready project structure
* ✅ Error analysis documentation
* ✅ Release-ready model weights

---

# 🎯 Project Objective

Traditional façade inspection is often:

* manual and labor intensive
* visually subjective
* difficult to scale
* weakly documented longitudinally

This project explores how **computer vision and object detection** can transform façade inspection into a more **scalable, auditable, and evidence-driven workflow**.

The long-term goal is to convert image detections into:

* BIM-linked condition records
* maintenance prioritization logic
* digital twin updates
* lifecycle decision support

---

# 🗂️ Dataset

## 📍 Public Dataset Source

The dataset is publicly available on **Roboflow Universe**.

* **Workspace:** `youniss-workspace-fic2t`
* **Project:** `m10-fmp-g2-facade-detection`
* **Task:** Multi-class object detection
* **Export Format:** YOLO11
* **Version Used:** `V1`

### 🔗 Dataset Link

[https://universe.roboflow.com/youniss-workspace-fic2t/m10-fmp-g2-facade-detection](https://universe.roboflow.com/youniss-workspace-fic2t/m10-fmp-g2-facade-detection)

## 🧱 Defect Taxonomy

| Class         | Inspection Meaning                                  |
| ------------- | --------------------------------------------------- |
| crack         | façade cracks, fractures, and line defects          |
| efflorescence | moisture-related salt deposits and white staining   |
| spalling      | surface material loss and concrete detachment       |
| wires         | exposed service cables and visible electrical lines |

## 🧪 Dataset Strategy

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

## ⚙️ Training Configuration

| Parameter         |                                      Value |
| ----------------- | -----------------------------------------: |
| Model             |            YOLO11s *(update final choice)* |
| Framework         |                                Ultralytics |
| Training Platform |                               Google Colab |
| GPU               |                                T4 High RAM |
| Epochs            |                   50 *(update final run)* |
| Image Size        |                   640 *(update final run)* |
| Batch Size        |                                         16 |
| Early Stopping    |                              patience = 20 |
| Notebook          | `notebooks/FMP_AI_Facade_Inspection.ipynb` |

---

# 📊 Results Summary

> Replace with your final metrics from Colab

## 🌍 Overall Metrics

| Metric       | Value |
| ------------ | ----: |
| mAP@0.5      |  0.XX |
| mAP@0.5:0.95 |  0.XX |
| Precision    |  0.XX |
| Recall       |  0.XX |

## 🧩 Class-wise AP@0.5

| Class         |   AP |
| ------------- | ---: |
| crack         | 0.XX |
| efflorescence | 0.XX |
| spalling      | 0.XX |
| wires         | 0.XX |

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

# 🖼️ Sample Detection Outputs

## Validation Predictions

![Validation 1](results/predictions_val/val_01.jpg)
![Validation 2](results/predictions_val/val_02.jpg)

## Unseen Image Predictions

![Prediction 1](results/predictions_new/new_01.jpg)
![Prediction 2](results/predictions_new/new_02.jpg)

---

# 🚀 Reproducibility Workflow (Google Colab)

## ▶️ Run Instructions

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

# 🗃️ Repository Structure

```text
AI-Facade-Inspection/
│
├── README.md
├── requirements.txt
│
├── notebooks/
│   └── FMP_AI_Facade_Inspection.ipynb
│
├── docs/
│   ├── dataset_description.md
│   ├── error_analysis.md
│   └── governance_checklist.md
│
├── results/
│   ├── curves/
│   ├── predictions_val/
│   ├── predictions_new/
│   └── metrics/
│
└── assets/
```

---

# 📦 Model Weights

Add your GitHub Release asset link:

```md
[Download trained model weights](YOUR_RELEASE_LINK_HERE)
```

---

# 🔍 Error Analysis

Detailed failure analysis:

`docs/error_analysis.md`

Typical failure patterns:

* thin wire misses
* crack vs stain confusion
* shadow-heavy false positives
* distant spalling misses
* low-light recall degradation

---

# ⚠️ Limitations

This repository is a **research and academic prototype**.

Current limitations:

* strongly dependent on dataset quality
* sensitive to camera distance and resolution
* no severity estimation yet
* no BIM element linkage yet
* requires engineering review before use

⚠️ **Not intended as a standalone structural safety decision tool.**

---

# 🎓 Academic Context

Developed as part of a **Master-level Final Project in AI for AECO façade inspection workflows**.

This work combines:

* Computer Vision
* Defect Analytics
* BIM Integration
* Digital Twin Strategy
* Lifecycle Asset Intelligence

---

# 🛣️ Future Roadmap

* [ ] improve weak-class recall
* [ ] crack width quantification
* [ ] severity scoring
* [ ] BIM / Revit linking
* [ ] IFC object tagging
* [ ] JSON defect schema
* [ ] digital twin dashboard
* [ ] condition trend analytics

---

# 📄 License

**MIT License**

---

# 👤 Author

**Group_2**

