# AI-Facade-Inspection
## AI-Enabled Multi-Class Façade Defect Detection for Inspection and Digital Twin Integration

This repository presents the **Detect stage** of an AI-enabled façade inspection workflow developed for the **Final Master Project (FMP)**.

The project uses a **YOLO11-based multi-class object detection pipeline** trained in **Google Colab** using a **Roboflow-managed public dataset** to automatically identify visible façade defects from inspection imagery.

The system currently detects:

- Crack
- Efflorescence
- Spalling
- Exposed wires

The broader project vision supports a full inspection intelligence workflow:

> **Capture → Detect → Structure → Integrate → Assess**

This repository currently focuses on the **detection layer**, providing:

- reproducible notebook training
- validation metrics
- prediction visualizations
- model weights
- error analysis
- deployment-ready repository structure

---

# Project Objective

Façade inspection in existing buildings is often:

- labor intensive
- visually subjective
- difficult to scale
- weakly documented over time

This project explores how **computer vision + object detection** can support a more scalable and evidence-driven façade inspection workflow.

The objective is to automatically detect and localize visible façade defects from images so the outputs can later support:

- condition registers
- BIM elements
- maintenance prioritization
- digital twin environments
- lifecycle decision support

---

# Current Implemented Scope

## Included in this Repository
This version implements:

- Multi-class façade defect detection
- YOLO11 training and validation in Google Colab
- Roboflow dataset integration
- Precision–Recall evaluation
- confusion matrix analysis
- sample predictions on unseen images
- GitHub-hosted reproducibility workflow

## Planned Next Stages
Future work will extend this detector into:

- defect severity scoring
- crack width estimation
- CSV / JSON structured outputs
- BIM element mapping
- Revit / IFC integration
- digital twin synchronization
- maintenance risk ranking

---

# Dataset

## Dataset Source
The façade defect dataset used in this project is publicly available on **Roboflow Universe**.

- **Workspace:** `youniss-workspace-fic2t`
- **Project:** `m10-fmp-g2-facade-detection`
- **Task:** Multi-class object detection
- **Export Format:** YOLO11
- **Version Used:** V1

### Public Link
https://universe.roboflow.com/youniss-workspace-fic2t/m10-fmp-g2-facade-detection

## Dataset Purpose
The dataset was developed to support AI-assisted façade inspection workflows by detecting common visible envelope defects.

It is designed for the **Detect stage** of the wider project pipeline:

> Capture → Detect → Structure → Integrate → Assess

## Defect Classes
The dataset currently includes the following classes:

| Class | Inspection Meaning |
|---|---|
| crack | façade cracks, fractures, and line defects |
| efflorescence | moisture-related salt deposits and white staining |
| spalling | surface material loss and concrete detachment |
| wires | exposed service cables and visible electrical lines |

## Dataset Splits
The dataset follows Roboflow-managed standard splits:

- Training set
- Validation set
- Test set

This supports:

- fair held-out evaluation
- repeatable benchmarking
- class-level performance tracking
- PR curve reproducibility

## Dataset Version Control
The Colab notebook uses:

```python
version = project.version(1)
