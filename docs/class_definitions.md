#  Class Definitions

Defines the façade defect taxonomy used in the dataset and YOLO11 model.

## Current Classes
| Class | Definition | Common Confusions |
|---|---|---|
| crack | linear material fracture in façade surface | wires, joints, shadows |
| efflorescence | white salt deposits caused by moisture migration | glare, paint fading |
| spalling | detached concrete/plaster with material loss | dark stains, shadows |
| wires | visible external cables and service lines | cracks, edges |

## Annotation Principles
- Use tight bounding boxes
- Avoid excessive background
- Split disconnected defects into separate boxes
- Preserve thin-wire continuity where possible

## Version Alignment
Aligned with:
```python
version = project.version(1)
