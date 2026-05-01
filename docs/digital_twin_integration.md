# 🧠 Digital Twin Integration Strategy

> This document defines the strategy for extending YOLO-based façade defect detection into a BIM-linked Digital Twin workflow.

---

## 🎯 Purpose
This repository currently implements the **Detect stage** of the façade inspection workflow using a YOLO-based multi-class defect detection model.

The wider project vision extends this into a **Digital Twin workflow**, where image-based detections are transformed into **structured, traceable, BIM-linked condition intelligence**.

---

## 🧭 System Workflow Overview

Capture → Detect → Structure → Integrate → Assess
![System Workflow](../assets/system_pipeline.png)
---

## 🏗️ Digital Twin Role
The Digital Twin layer converts façade defect detections into **persistent asset condition records**.

It supports:
- BIM-linked defect records  
- element-level condition tracking  
- evidence-based maintenance prioritisation  
- longitudinal façade health monitoring  
- lifecycle asset intelligence  

---

## 🔄 Data Flow

Inspection Image
    ↓
YOLO Detection
    ↓
Structured Defect Record
    ↓
BIM / IFC Association
    ↓
Digital Twin Update
    ↓
Dashboard & Decisions

---

## 🧾 Structured Defect Record

Each detection should be converted into a structured **JSON or CSV record**.

Example:
{
  "defect_id": "DEF_0001",
  "asset_id": "WALL_N_04",
  "ifc_guid": null,
  "defect_type": "crack",
  "confidence": 0.98,
  "severity": "high",
  "bbox": [120, 85, 460, 220],
  "pixel_area": 450,
  "image_id": "IMG_0234",
  "evidence_link": "results/predictions_new/IMG_0234.jpg",
  "association_status": "pending_review"
}

---

## 🔗 BIM Association Logic

Detection Output
        ↓
Spatial Validation
        ↓
High Confidence → Validated → BIM Linked  
Low Confidence → Pending Review

---

## 🏢 Revit / IFC Integration

Future implementation may include:
- IFC GUID tagging  
- Revit shared parameter updates  
- Dynamo / Revit API integration  
- external defect registers  
- clickable BIM-linked evidence  

---

## 📈 Digital Twin Update Principle

T1 → Crack detected (Medium)  
T2 → Crack expanded (High)  
T3 → Repair completed (Closed)

---

## ⚠️ Safety and Review Gates

Detection → Confidence Check  
High Confidence → Auto Record  
Low Confidence → Manual Review  

The system prioritises reliable, auditable decision support over automation.
