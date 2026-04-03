# Governance Checklist

## Privacy and Consent
- The dataset is restricted to façade condition imagery only.
- No personal identifiable information (PII) is intentionally included.
- Images should be reviewed to remove any unintended sensitive content.

## Data Minimization
- Only imagery relevant to façade crack detection is retained.
- Metadata collection is limited to what supports evaluation and future BIM association.

## Current Technical Limitations
- The current model detects **visible surface cracks only**.
- It does not infer hidden structural deterioration.
- Performance is sensitive to image quality, angle, façade texture, and lighting.

## Risk and Reliability Notes
- False negatives may leave visible cracks undetected.
- False positives may create unnecessary review actions.
- All outputs must support professional inspection, not replace engineering judgment.

## Prototype Deployment Position
- Current use is strictly academic and research-oriented.
- Human validation is mandatory before operational decisions.

## Future Governance Direction
- BIM-linked outputs should include confidence thresholds.
- Low-confidence detections must be flagged for manual review.
- Future deployment should integrate uncertainty-aware decision rules.
