# Class Definitions and Annotation Rules
Author: Ahmed El Basyouni

## Class
- Class ID: 0
- Class name: cracks
- Target: visible surface cracks in concrete.
- Task: object detection using bounding boxes.

A detection identifies an image region containing a possible crack.
It does not establish crack depth, physical width, cause, severity,
or structural safety.

## Current Dataset
Annotations were inherited from the Roboflow source dataset.
One polygon annotation was converted to its enclosing bounding box.
No other labels were changed during this baseline workflow.

Visual review identified possible annotation gaps and inconsistent
grouping of cracks. The following rules are proposed for future
annotation review; they are not claimed to have been applied throughout
the current dataset.

## Proposed Label Rules
1. Draw a tight box around the visible extent of a crack, including
   enough context to identify it while limiting unnecessary background.
2. Use one box for a connected crack and its connected branches.
3. Use separate boxes for clearly disconnected cracks.
4. For cracks extending beyond the image, label only the visible part.
5. Do not label designed joints, shadows, stains, scratches, or surface
   texture as cracks unless visual evidence supports the classification.
6. Refer faint or ambiguous features for a second review.
7. Retain an empty label only after checking that no target crack is visible.

## YOLO Annotation Format
Each bounding-box row contains:
`class_id x_center y_center width height`

Coordinates are normalised to the image dimensions.
For this dataset, class_id is 0.

## Review Examples
- 00103: review whether nearby cracks should be grouped or separated.
- 00039: review the faint crack-like feature and empty annotation.
- new_04: an additional thin-crack example missed by the model.

## Limitations
Bounding boxes contain background and do not describe the exact crack
outline. Pixel-level segmentation would require a separate annotation
and evaluation workflow.
