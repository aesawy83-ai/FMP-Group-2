# Class Definitions

This document defines the façade defect classes used in the **AI-Facade-Inspection** object detection dataset and model pipeline.

These definitions act as the **annotation standard, model interpretation reference, and evaluation baseline** for all current and future dataset versions.

---

# Purpose

The purpose of this document is to ensure:

* annotation consistency across contributors
* reduced class ambiguity
* reproducible dataset growth
* cleaner error analysis
* more reliable class-wise AP interpretation
* stronger future BIM / digital twin mapping

This is especially important for **multi-class façade defect detection**, where visually similar defects can easily cause label drift.

---

# Current Detection Classes

The current model supports **4 façade defect classes**.

| Class         | Definition                                                | Typical Visual Characteristics                                     | Common Confusions               |
| ------------- | --------------------------------------------------------- | ------------------------------------------------------------------ | ------------------------------- |
| crack         | Linear fracture or separation in façade material          | thin dark lines, branching fractures, diagonal or vertical splits  | wires, joints, shadows          |
| efflorescence | Salt deposit caused by moisture migration                 | white powdery stains, cloudy surface deposits, irregular patches   | paint fading, light reflections |
| spalling      | Loss of surface material or detached concrete/plaster     | chipped edges, exposed substrate, irregular missing surface zones  | shadows, discoloration          |
| wires         | Visible exposed service cables or façade electrical lines | thin elongated cables, bundled wires, dark linear service elements | cracks, window edges            |

---

# Annotation Rules

## 1) Crack

Annotate as **crack** when:

* the defect is a visible fracture in the façade surface
* the line represents material separation
* branching or multiple connected fractures exist

Do **not** label:

* façade joints
* panel seams
* shadow lines
* hanging wires

---

## 2) Efflorescence

Annotate as **efflorescence** when:

* white salt-like deposits are visible
* moisture migration leaves surface residue
* staining is clearly deposit-based rather than paint damage

Do **not** label:

* overexposed highlights
* reflective glare
* white painted regions

---

## 3) Spalling

Annotate as **spalling** when:

* concrete, plaster, or finish layer is visibly detached
* the façade shows missing surface chunks
* edges reveal depth loss or substrate exposure

Do **not** label:

* superficial stains
* discoloration without material loss
* shallow texture changes only

---

## 4) Wires

Annotate as **wires** when:

* service cables are visible externally
* façade-mounted electrical lines are exposed
* bundled or hanging utility wires appear in the image

Do **not** label:

* crack lines
* façade grooves
* railing lines
* window frame edges

---

# Bounding Box Guidance

Use **tight object-level bounding boxes**.

Guidelines:

* include the full visible defect extent
* minimize unnecessary background
* avoid oversized contextual boxes
* use separate boxes for disconnected defects
* preserve thin-wire continuity as much as possible

For cracks:

* prioritize the **full visible fracture path**
* include branching regions if connected

For spalling:

* capture the **entire detached material zone**

---

# Known Ambiguity Zones

The following cases require extra care:

## Crack vs Wires

This is currently the highest-risk confusion pair.

Check:

* does the line follow gravity naturally? → likely wire
* does it branch inside masonry? → likely crack
* is it attached to service fixtures? → wire

## Efflorescence vs Surface Stain

Efflorescence should imply:

* moisture origin
* crystalline or powder-like white deposit
* irregular spread pattern

---

# Why This Matters for Model Quality

Weak class separation directly reduces:

* class-wise AP
* PR curve quality
* recall on difficult images
* transferability to unseen façades

This document should therefore be used as the **single source of truth for all future annotations and dataset revisions**.

---

# Future Extensions

Potential future classes:

* corrosion
* sealant failure
* façade staining
* water ingress marks
* anchor exposure
* delamination

These should only be introduced after sufficient data volume and visual distinctiveness are confirmed.

---

# Versioning Note

This class schema currently aligns with:

```python
version = project.version(1)
```

Any future class expansion must update:

* Roboflow class list
* notebook YAML
* README tables
* error analysis
* benchmark history
