## 📊 Results Summary

The current baseline **YOLO11 multi-class façade defect detector** demonstrates measurable learning across all four target defect classes, with the strongest performance on **crack detection** and the weakest performance on **thin-object wire detection**.

### Overall Metrics

| Metric | Value |
|---|---:|
| mAP@0.5 | 0.178 |
| mAP@0.5:0.95 | 0.090 |
| Precision | 0.280 |
| Recall | 0.210 |

### Class-wise AP@0.5

| Class | AP |
|---|---:|
| crack | 0.354 |
| efflorescence | 0.148 |
| spalling | 0.155 |
| wires | 0.056 |

### Performance Interpretation
The current model demonstrates the strongest feature learning for **cracks**, benefiting from clearer linear morphology and stronger representation in the dataset.  
The **wires class remains the weakest**, primarily due to:
- thin-object sensitivity
- scale variation
- background clutter
- limited hard negative examples
- lower class balance in the current dataset version

These findings directly inform the next dataset balancing and augmentation strategy for future iterations.
