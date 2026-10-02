# Problem Statement and Project Objective
Author: Ahmed El Basyouni

## Problem
Reviewing concrete images for visible surface cracks can be
time-consuming. A computer vision model may support initial
visual inspection by highlighting regions containing possible cracks.

## Objective
Explore YOLOv8n for detecting visible surface cracks in concrete
images and deliver a reproducible workflow that runs in Google Colab.

The intended context is architecture, engineering, construction,
and operations (AECO).

## Workflow
- Prepare and verify the dataset.
- Train YOLOv8n.
- Evaluate performance on the validation split.
- Run inference on new images.
- Review detection errors and propose data improvements.
- Document reproducibility, limitations, and data rights.

## Evaluation and Success Criteria
Evaluate precision, recall, mAP50, and mAP50–95.
Review predictions visually to identify missed cracks,
false detections, and localisation errors.

Successful delivery requires a fresh Colab session to reproduce
the workflow without credentials, with accessible trained weights,
metrics, prediction evidence, and documented limitations.

No numerical performance target was established before training.

## Limitations
This is an academic prototype and requires human review.
Predictions must not be used to determine structural safety,
crack depth, physical width, cause, or severity.
Performance on the validation split does not establish reliability
across other sites, cameras, lighting conditions, or concrete surfaces.
