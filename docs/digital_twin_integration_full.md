# 🧠 Digital Twin Integration Strategy

> This document defines the system architecture for extending YOLO-based façade defect detection into a BIM-linked Digital Twin workflow for AECO applications.

---

## 🎯 1. System Purpose

This repository implements the Detect stage of an AI-enabled façade inspection pipeline.

The extended goal is to transform image-based detections into:
- structured defect records  
- BIM-linked condition data  
- Digital Twin updates  
- lifecycle asset intelligence  

---

## 🧭 2. End-to-End Workflow

Capture → Detect → Structure → Coordinate Mapping → Integrate → Digital Twin → Feedback

---

## 🔄 3. Data Flow Architecture

Inspection Image  
↓  
YOLO Detection  
↓  
Structured JSON Output  
↓  
Coordinate Transformation  
↓  
BIM Model (IFC / Revit)  
↓  
Digital Twin Dashboard  
↺  
User Feedback & Validation  

---

## 🧾 4. Structured Defect Data Model

Example JSON:

{
  "defect_id": "DEF_0001",
  "element_id": "FAC-001",
  "ifc_guid": null,
  "defect_type": "crack",
  "confidence": 0.92,
  "severity": "medium",
  "bbox": [120, 340, 80, 60],
  "pixel_area": 480,
  "image_id": "IMG_0234",
  "evidence_link": "results/predictions_new/IMG_0234.jpg",
  "association_status": "pending_review",
  "location": {
    "x": null,
    "y": null,
    "z": null
  }
}

---

## 📐 5. Coordinate Mapping Layer

Converts image detections to real-world coordinates.

Methods:
- homography  
- photogrammetry  
- depth estimation  

---

## 🔗 6. BIM Integration Strategy

Formats:
- IFC  
- Revit  

Data stored as:
- IFC Property Sets  
- Revit parameters  

---

## 🏢 7. BIM Association Logic

Detection → Validation → BIM Link or Review

---

## 📈 8. Digital Twin Update Model

T1 → Medium  
T2 → High  
T3 → Closed  

---

## 📊 9. Digital Twin Dashboard

Functions:
- visualize defects  
- track condition changes  
- support maintenance  

---

## 🔁 10. Feedback Loop

Detection → BIM → Dashboard → User → Update

---

## ⚠️ 11. Safety and Review Gates

High confidence → Auto  
Low confidence → Manual review  

---

## 🏆 12. System Principles

- structured data  
- traceability  
- BIM-first  
- human-in-the-loop  
