# Future Integration Roadmap

The current repository implements the façade crack detection stage only.

## Planned Next Steps

### 1. Structure
Convert detections into structured outputs such as:
- defect class
- confidence
- pixel area
- severity category
- evidence image reference

### 2. Integrate
Associate structured defect outputs with BIM / IFC / Revit elements using future model-mapping logic.

### 3. Assess
Support persistent condition records and maintenance-oriented decision workflows.

## Example Future Output Schema
```json
{
  "asset_id": "WALL_N_04",
  "defect_type": "crack",
  "confidence": 0.98,
  "severity": "high",
  "pixel_area": 450
}
