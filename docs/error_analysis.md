#  Error Analysis

This document summarizes the major failure modes observed in current model validation.

## Common Failure Patterns
###⚡ Wires
- missed thin cables
- confused with crack lines
- low recall at distance

###  Crack
- confusion with façade joints
- false positives on shadows

###  Efflorescence
- confused with bright paint regions
- weak under glare

###  Spalling
- misses small detached patches
- weak in low-resolution images

## Root Causes
- class imbalance
- insufficient hard examples
- image scale sensitivity
- annotation ambiguity

## Next Actions
- [ ] add more wire samples
- [ ] increase image size
- [ ] upgrade to YOLO11m
- [ ] refine class boundaries
