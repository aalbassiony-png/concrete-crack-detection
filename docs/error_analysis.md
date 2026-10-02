# Error Analysis
Author: Ahmed El Basyouni

## Version Consistency Notice
The latest backup reports different validation metrics and new-image predictions
from the earlier run. The counts and validation examples below are historical,
and must not be represented as verified errors of the packaged current weights.
Run the current notebook error-analysis cells and visually review its candidates.
Three current FP and three confirmed FN examples remain pending.

## Historical Analysis Settings
- Model: YOLOv8n, best.pt
- Validation images: 81
- Labelled crack instances: 51
- Confidence threshold: 0.25
- NMS IoU threshold: 0.70
- Matching IoU threshold: 0.50
- Matching: predictions processed in descending confidence order;
  each annotation can match only one prediction.

At these settings, the comparison found 50 matched detections,
6 unmatched predictions (FP candidates), and 1 unmatched annotation
(FN candidate). These counts describe one operating point and are
separate from the reported Ultralytics validation metrics.

## Historical Three False-Positive Examples

| Image prefix | Observed error | Possible explanation |
|---|---|---|
| 00003 | An additional box overlaps the same crack as a matched detection. | Alternative boxes around the elongated crack may survive NMS. |
| 00018 | A second box covers the same crack already detected. | Different box extents may allow duplicate predictions to survive NMS. |
| 00205 | An additional box covers the crack already identified by a matched prediction. | Uncertain box boundaries and the selected NMS threshold may contribute. |

These are duplicate-detection false positives under one-to-one
matching. They are not examples of predictions on crack-free concrete.
The proposed explanations are hypotheses, not experimentally verified causes.

## Historical False-Negative Review and Current Coverage

### FN 1 — 00103: localisation/matching failure
Two predicted boxes cover visible crack regions, but neither matches
the larger original annotation at IoU >= 0.50. The matching procedure
therefore records one FN and two FP candidates.

This is a localisation or annotation-grouping mismatch, rather than
a complete absence of crack detection. A possible explanation is
inconsistent grouping of nearby cracks into one reference box.

### Reviewed new image — new_04.png (not counted as an FN)
The latest run produced one detection at confidence 0.313 with the box
visually aligned to the vertical crack. The earlier no-detection observation
is superseded. The reason for the discrepancy has not been verified.
Without a ground-truth box, localisation accuracy cannot be quantified.

### Suspected case — 00039
A faint irregular crack-like feature is visible, but its original
annotation file is empty and the model produced no detection.
Image quality prevents confident confirmation. This case is recorded
as a suspected annotation gap and potential model miss, not a
confirmed third FN.

### Requirement status
One validation FN candidate is documented as a localisation/matching failure.
The assignment requirement for three confirmed FN examples remains
incomplete. No third example has been fabricated.

## Additional Image Tests
All targeted test outcomes were retained:
- new_06: 1 detection, confidence approximately 0.900.
- new_07: 1 detection, confidence approximately 0.900.
- new_08: 1 detection, confidence approximately 0.865.
- new_09: 1 detection, confidence approximately 0.926.

These images did not produce complete absence of detection.
The boxes in new_06 and new_09 include substantial background.
Reference boxes are required to quantify their localisation accuracy.

These selected images support qualitative review and do not estimate
overall accuracy. Their sources, redistribution rights, and independence
from the training data must be documented before publication.

## Three Prioritised Data Improvements

1. **Audit labels and standardise box rules.**
   Review all 154 empty-label images across both splits. Start with
   suspected cases such as 00039. Define consistent rules for separate
   cracks, connected branches, and tight boxes. Use a second reviewer
   for ambiguous cases. Publish corrections as a new dataset version
   while preserving the current baseline.

2. **Expand thin and low-contrast crack coverage.**
   Collect at least 50 rights-cleared images with varied lighting,
   distances, and textures. Preserve original resolution and annotate
   all visible cracks. Split by source or capture session to reduce
   leakage. This addresses thin-crack coverage and the low-confidence detection in new_04; it is not evidence of a confirmed current miss.

3. **Add diverse negatives and an independent test set.**
   Collect at least 50 rights-cleared examples of crack-free concrete,
   joints, stains, scratches, and shadows. Verify negative labels
   manually. Establish a test set from separate locations or capture
   sessions to assess future changes.

## Proposed Model Experiment
Compare NMS IoU 0.50 with the current 0.70 to investigate duplicate
detections. Measure both duplicate predictions and missed nearby
cracks. This experiment has not yet been performed.

## Evidence Locations
Paths below are relative to the repository root:
- Error-review figures and candidate CSV: results/evidence/errors/
- Original five new-image predictions: results/evidence/new_images/
- Validation metrics: results/validation_metrics.csv

## Limitations
The dataset is small and has no independent test split.
Empty labels may contain annotation gaps. Visual assessments of
additional images are not a substitute for reference annotations.
Original validation labels were retained unchanged.

The model supports human visual inspection. It does not determine
structural safety, crack severity, or repair requirements.
