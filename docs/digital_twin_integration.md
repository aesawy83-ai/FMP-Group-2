# Digital Twin Integration Strategy

---

## Purpose

This repository currently implements the **Detect** stage of the façade inspection workflow using YOLO-based multi-class defect detection.

The wider project vision extends this into a Digital Twin workflow where image-based detections are transformed into **structured, traceable, BIM-linked condition intelligence**.

---

## Target Workflow

```text
Capture → Detect → Structure → Integrate → Assess
```

---

## Workflow Mapping

The conceptual inspection workflow:

```text
Capture → Detect → Structure → Integrate → Assess
```

is implemented as:

```text
Image → YOLO Detection → Structured JSON → BIM / IFC → Digital Twin → Dashboard
```

---

## System Pipeline (see Figure 1)

![System Pipeline](../assets/pipeline_dt.png)

This pipeline transforms inspection imagery into structured, BIM-linked intelligence ready for Digital Twin integration and decision-making.

---

## Integrated System Overview

This system combines three core components:

* The **AI detection pipeline**, which converts inspection images into structured defect data
* The **BIM association logic**, which links defects to physical building elements
* The **Digital Twin condition model**, which tracks asset condition over time

Together, these components form a complete inspection intelligence workflow from detection to lifecycle decision-making.

---

## Digital Twin Role

The Digital Twin layer is responsible for converting façade defect detections into **persistent asset condition records**.

It is not limited to visual detection. Its role is to support:

* BIM-linked defect records
* element-level condition tracking
* evidence-based maintenance prioritisation
* longitudinal façade health monitoring
* lifecycle asset intelligence

---

## Data Flow

```text
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
```

---

## Structured Defect Record

Each detection should be converted into a structured JSON/CSV record.

This structured format enables integration with BIM systems and Digital Twin platforms.

### JSON Example

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
```

---

## BIM Association Logic (see Figure 2)

![BIM Association Logic](../assets/bim_logic_v2.png)

Defects should only be linked to BIM elements when spatial confidence is acceptable.

The system avoids forced BIM association and applies validation-driven decision logic.

### Recommended Statuses

* validated
* candidate
* pending_review
* withheld

### Association Criteria

* camera pose quality
* image-to-model alignment
* nearest façade surface distance
* projected defect location
* manual reviewer confirmation

---

## BIM–Digital Twin Link

BIM provides the spatial and semantic structure of the asset, while the Digital Twin extends this by incorporating **time-based condition data**.

Each defect record is anchored to a BIM element (via IFC GUID or element ID) and updated over time within the Digital Twin condition model.

---

## Revit / IFC Integration

Future implementation may include:

* IFC GUID tagging
* Revit shared parameter updates
* Dynamo / Revit API integration
* external defect registers linked to BIM elements
* clickable evidence links from BIM to inspection images

### Suggested Revit Parameters

* Facade_Condition
* Defect_Count
* Dominant_Defect_Type
* Highest_Severity
* Last_Inspection_Date
* AI_Confidence
* Evidence_Link
* Review_Status

---

## Digital Twin Condition Model (see Figure 3)

![Digital Twin Lifecycle](../assets/dt_lifecycle_v2.png)

---

## Digital Twin State Model

The Digital Twin operates as a **state-based system**, where each inspection represents a new condition state of the asset.

### State Transitions

* **T1** → Detection (initial condition)
* **T2** → Deterioration (severity increase)
* **T3** → Repair and closure

This enables temporal tracking, condition evolution analysis, and lifecycle decision support.

---

## Digital Twin Update Principle

The Digital Twin should be updated through **controlled records**, not uncontrolled model overwrites.

Each inspection creates a new condition state rather than overwriting previous data.

### Example

```text
T1 → Crack detected → Medium severity  
T2 → Crack expanded → High severity  
T3 → Repair completed → Closed  
```

This enables trend analysis, maintenance planning, and lifecycle decision-making.

---

## Safety and Review Gates

This repository is not intended to make standalone structural safety decisions.

Digital Twin updates should be reviewed when:

* detection confidence is low
* image quality is poor
* BIM association is uncertain
* defect class is safety-critical
* severity is high

The system prioritises **reliable decision support over fully automated model updates**.

---

## Included in this Repository

Digital Twin integration strategy documented in:

```text
docs/digital_twin_integration.md
```

---
