# AI-Facade-Inspection
## AI-Enabled Multi-Class Façade Defect Detection for Inspection and Digital Twin Integration

This repository presents the **Detect stage** of an AI-enabled façade inspection workflow developed for the **Final Master Project (FMP)**.

The project uses a **YOLO11-based multi-class object detection pipeline** trained in **Google Colab** using a **Roboflow-managed dataset** to automatically identify visible façade defects from inspection imagery.

The system currently detects:

- Crack
- Efflorescence
- Spalling
- Exposed wires

The broader project vision is to support a full workflow:

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
- weakly documented across time

This project explores how **computer vision + object detection** can support a more scalable and evidence-driven inspection workflow.

The objective is to automatically detect and localize visible façade defects from images so the results can later be linked to:
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

## Source
The dataset is managed using **Roboflow** and exported in **YOLO11 format**.

- Platform: Roboflow
- Format: YOLO11
- Split: Train / Validation / Test
- Export Type: Object Detection

## Defect Classes
The current detector supports **4 façade defect classes**:

| Class | Description |
|---|---|
| crack | visible façade cracking and line fractures |
| efflorescence | salt deposits / moisture-related staining |
| spalling | concrete cover loss / surface material detachment |
| wires | exposed cables or façade service lines |

## Dataset Access
Dataset access is controlled through Roboflow workspace permissions.

If public release is allowed, add the dataset URL here.

```text
Dataset link: [[Insert Roboflow public version link](https://universe.roboflow.com/youniss-workspace-fic2t/m10-fmp-g2-facade-detection)]
