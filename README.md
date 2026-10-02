# Concrete Crack Detection | M4U3
Author: Ahmed El Basyouni

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/aalbassiony-png/concrete-crack-detection/blob/main/notebooks/01_crack_detection_training.ipynb)

## Problem and objective
Support initial AECO visual review by locating possible surface cracks in concrete
images. This academic prototype requires human review and does not establish
structural safety, crack width, depth, cause or severity. See docs/problem_statement.md.

## Dataset and classes
One class: 0 = cracks. Source: [Maira on Roboflow Universe](https://universe.roboflow.com/maira-6vdxe/concrete-crack-detection-01ci4).
Fork version 1: 405 images, 324 train (80%), 81 validation (20%), no test split.
Auto-orient; stretch to 640x640; no Roboflow augmentation. Training augmentation
settings are recorded in results/yolov8n_cracks/args.yaml. One polygon annotation
is converted to an enclosing box; the other labels are retained.

Frozen dataset: https://github.com/aalbassiony-png/concrete-crack-detection/releases/download/v1.0/concrete-cracks-v1-yolo11.zip

SHA256: `4f6cf7fb5f8caefd2621fc801a8f337773b08c6c578a10534d222794a4c0faba`

Dataset declares CC BY 4.0. Additional photographs are author-declared originals,
all rights reserved. See LICENSE.md and docs/image_sources.md.

## Latest supplied results
| Precision | Recall | mAP50 | mAP50-95 |
|---|---|---|---|
| 0.9991 | 0.9608 | 0.9811 | 0.7332 |

These are values from the latest supplied backup CSV, not a newly executed
verification by the assistant. Earlier results were P=0.9554, R=0.9608,
mAP50=0.9786, mAP50-95=0.7364. Their discrepancy has not been resolved.
Use the clean notebook to re-evaluate the packaged weight hash.

High validation scores do not demonstrate performance at new sites. The lower
mAP50-95 than mAP50 indicates sensitivity to tighter localisation requirements.
Current new_04 has one visually plausible crack detection at confidence 0.313;
it is not a confirmed current FN. Three current FP and three FN remain pending.

## How to reproduce
1. Repository owner: publish the repository files on public branch main.
2. Upload the provided best.pt as a Release v1.0 asset. Do not commit weights
   or the frozen dataset ZIP into git.
3. Open the Colab badge; choose a T4 GPU if available. CPU inference is supported.
4. Disconnect and delete the runtime; reconnect; Run all with no secrets.
5. Default mode downloads and hashes the dataset and saved trained weights,
   computes metrics, saves ten validation predictions, five new-image outputs,
   an error candidate CSV, and reproduction_run.json under /content/results.
6. Compare freshly computed metrics with the latest backup and investigate
   material discrepancies. Record actual completion time, device and elapsed
   duration only after a successful fresh-session run.
7. Optional: set RUN_FULL_TRAINING=True for a new 30-epoch experiment.

Weights URL: https://github.com/aalbassiony-png/concrete-crack-detection/releases/download/v1.0/best.pt

Weights SHA256: `ef01306429e31ed259def70a3841ab2d54c58254e4f665b17e32c7f2d085f4fd`

## Reproducibility checklist
- Dataset version 1, public frozen URL and checksum recorded.
- Model YOLOv8n, 30 epochs, batch 16, imgsz 640, seed 42.
- Ultralytics 8.3.40; PyYAML 6.0.2.
- Original environment record: docs/environment_and_training.json.
- PyTorch is Colab-provided; every verification records its actual version.
- Fresh-session proof: pending. Expected duration must be measured; no verified
  fresh-run runtime range is claimed. Original historical training was about 4.19 min.

## Evidence and documents
- results/evidence/annotations/: 5 annotation examples.
- results/evidence/validation/: 10 predictions.
- results/evidence/new_images/: 5 predictions and summary CSV.
- results/yolov8n_cracks/: curves, metrics and configuration.
- docs/: problem, classes, historical error review, governance and image rights.
- notebooks/00_baseline_inference.ipynb: generic pretrained inference baseline.
- docs/submission_status.md: requirements still pending.

## PDF pack
Slides (6-8 pages) and mini report (maximum 2 pages) remain pending until current
error review and fresh-session results are verified. Do not treat this package
as a completed final submission yet.
