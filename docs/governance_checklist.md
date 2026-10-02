# Governance Checklist
Author: Ahmed El Basyouni

## Purpose and Human Oversight
- [x] Purpose: academic exploration of concrete-crack detection.
- [x] Predictions require human review.
- [x] The model is not authorised for autonomous safety decisions.

## Privacy and Consent
- [x] The training dataset source and declared licence are recorded.
- [ ] Review all images for faces, identifying information, and
      confidential project details before publication.
- [ ] Confirm permission for any privately sourced additional images.
- [ ] Publish only additional images with documented redistribution rights.

## Data Minimisation
- [x] No personal information is required for crack detection.
- [ ] Remove unnecessary personal or confidential content and metadata
      from any additional images before publication.
- [x] Use the frozen dataset release rather than committing the full
      training dataset into the repository.

## Data Rights and Attribution
- [x] Dataset export declares CC BY 4.0.
- [x] Original source:
      https://universe.roboflow.com/maira-6vdxe/concrete-crack-detection-01ci4
- [x] Fork version: 1; 405 images; 324 training / 81 validation.
- [x] Preserve source attribution and record preprocessing and changes,
      including conversion of one polygon annotation to a bounding box.
- [ ] Record source, creator, licence or permission, and any modifications
      for additional images new_01 through new_09.
- [ ] Finalise the project licence statement and document applicable
      third-party software and model terms separately.

## Risks
- [x] False negatives may leave visible cracks unflagged.
- [x] False positives, including duplicate boxes, may increase review
      effort or cause unnecessary follow-up.
- [x] No detection must not be interpreted as proof that a surface is
      crack-free or structurally safe.
- [x] Confidence scores are not measures of structural severity.

## Limitations — When Not to Use
- [x] Small dataset and validation split; no independent test split.
- [x] Possible annotation gaps and inconsistent crack grouping.
- [x] Thin cracks, low contrast, blur, distance, and different surfaces
      may reduce detection performance.
- [x] Bounding boxes do not measure crack width, depth, or progression.
- [x] Do not use for structural certification, repair approval, or
      replacement of a qualified engineer's inspection.

## Reproducibility and Credentials
- [x] Primary dataset download uses a public URL and SHA256 verification.
- [ ] Complete a fresh Colab Run all test without credentials or manual
      image uploads.
- [ ] Inspect notebook cells, outputs, and repository history for API keys
      before submission.

Unchecked items remain pending and must not be described as completed.
