# 🧠 Digital Twin Integration Strategy

## 🎯 Purpose
This repository currently implements the **Detect stage** of the façade inspection workflow using a YOLO-based multi-class defect detection model.

The wider project vision extends this into a **Digital Twin workflow**, where image-based detections are transformed into **structured, traceable, BIM-linked condition intelligence**.

**Target workflow:**
Capture → Detect → Structure → Integrate → Assess

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
BIM / IFC Element Association
↓
Digital Twin Condition Update
↓
Dashboard / Maintenance Decision

---

## 🧾 Structured Defect Record

Each detection should be converted into a structured **JSON or CSV record**.

### Example:

```json
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
## BIM Association Logic

Defects should only be linked to BIM elements when spatial confidence is acceptable.

Avoid forced or uncertain associations.

Recommended statuses:
validated
candidate
pending_review
withheld
Association may be based on:
camera pose quality
image-to-model alignment
nearest façade surface distance
projected defect location
manual reviewer validation
🏢 Revit / IFC Integration

Future implementation may include:

IFC GUID tagging
Revit shared parameter updates
Dynamo / Revit API integration
external defect registers linked to BIM elements
clickable evidence links from BIM to inspection images
Suggested Revit Parameters:
Facade_Condition
Defect_Count
Dominant_Defect_Type
Highest_Severity
Last_Inspection_Date
AI_Confidence
Evidence_Link
Review_Status
📈 Digital Twin Update Principle

The Digital Twin should be updated through controlled condition records, not direct model overwrites.

Each inspection creates a new condition state:
T1 → Crack detected → Medium severity
T2 → Crack expanded → High severity
T3 → Repair completed → Closed
This enables:

condition trend tracking
maintenance planning
lifecycle decision support
⚠️ Safety and Review Gates

This system supports decision-making but is not intended for autonomous structural decisions.

Review is required when:

detection confidence is low
image quality is poor
BIM association is uncertain
defect class is safety-critical
severity is high

The priority is reliable, auditable decision support, not full automation.

---

## Step 4 — Commit

Scroll down → write:
Add Digital Twin integration strategy documentation

Click:
Commit new file

---

# ✅ Step 5 — Link it in README

Add this line in your README (Docs section):

```md
- [Digital Twin Integration](docs/digital_twin_integration.md)
assets/digital_twin_pipeline.png
